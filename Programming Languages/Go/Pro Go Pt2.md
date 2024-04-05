Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


35. SportsStore: A Real Application
36. SportsStore: Cart and Database
37. SportsStore: Checkout and Administration
21h 44m remaining
© The Author(s), under exclusive license to APress Media, LLC, part of Springer Nature 2022
A. FreemanPro Go
https://doi.org/10.1007/978-1-4842-7355-5_36
36. SportsStore: Cart and Database
Adam Freeman1  
(1)
London, UK
 
In this chapter, I continue the development of the SportsStore application, adding support for a shopping cart and introducing a database to replace the temporary repository I created in Chapter 35.

TipYou can download the example project for this chapter—and for all the other chapters in this book—from https://github.com/apress/pro-go. See Chapter 2 for how to get help if you have problems running the examples.
Building the Shopping Cart
The SportsStore application is proceeding nicely, but I cannot sell any products unless I implement a shopping cart, which will allow users to gather their selections together before checking out.

Defining the Cart Model and Repository
To define the cart data type, create the sportsstore/store/cart folder and add to it a file named cart.go with the content shown in Listing 36-1.
package cart
import "sportsstore/models"
type CartLine struct {
    models.Product
    Quantity int
}
func (cl *CartLine) GetLineTotal() float64 {
    return cl.Price * float64(cl.Quantity)
}
type Cart interface {
    AddProduct(models.Product)
    GetLines() []*CartLine
    RemoveLineForProduct(id int)
    GetItemCount() int
    GetTotal() float64
    Reset()
}
type BasicCart struct {
    lines []*CartLine
}
func (cart *BasicCart) AddProduct(p models.Product) {
    for _, line := range cart.lines {
        if (line.Product.ID == p.ID) {
            line.Quantity++
            return
        }
    }
    cart.lines = append(cart.lines, &CartLine{
        Product: p, Quantity: 1,
    })
}
func (cart *BasicCart) GetLines() []*CartLine {
    return cart.lines
}
func (cart *BasicCart) RemoveLineForProduct(id int) {
    for index, line := range cart.lines {
        if (line.Product.ID == id) {
            cart.lines = append(cart.lines[0: index], cart.lines[index + 1:]...)
        }
    }
}
func (cart *BasicCart) GetItemCount() (total int) {
    for _, l := range cart.lines {
        total += l.Quantity
    }
    return
}
func (cart *BasicCart) GetTotal() (total float64) {
    for _, line := range cart.lines {
        total += float64(line.Quantity) * line.Product.Price
    }
    return
}
func (cart *BasicCart) Reset() {
    cart.lines = []*CartLine{}
}
Listing 36-1The Contents of the cart.go File in the store/cart Folder
The Cart interface will be provided as a service, and I have defined a BasicCart struct that implements the Cart methods using a slice. To define the service, add a file named cart_service.go to the sportsstore/store/cart folder with the content shown in Listing 36-2.
package cart
import (
    "platform/services"
    "platform/sessions"
    "sportsstore/models"
    "encoding/json"
    "strings"
)
const CART_KEY string = "cart"
func RegisterCartService() {
    services.AddScoped(func(session sessions.Session) Cart {
        lines := []*CartLine {}
        sessionVal := session.GetValue(CART_KEY)
        if strVal, ok := sessionVal.(string); ok {
            json.NewDecoder(strings.NewReader(strVal)).Decode(&lines)
        }
        return &sessionCart{
            BasicCart: &BasicCart{ lines: lines},
            Session: session,
        }
    })
}
type sessionCart struct {
    *BasicCart
    sessions.Session
}
func (sc *sessionCart) AddProduct(p models.Product) {
    sc.BasicCart.AddProduct(p)
    sc.SaveToSession()
}
func (sc *sessionCart) RemoveLineForProduct(id int) {
    sc.BasicCart.RemoveLineForProduct(id)
    sc.SaveToSession()
}
func (sc *sessionCart) SaveToSession() {
    builder := strings.Builder{}
    json.NewEncoder(&builder).Encode(sc.lines)
    sc.Session.SetValue(CART_KEY, builder.String())
}
func (sc *sessionCart) Reset() {
    sc.lines = []*CartLine{}
    sc.SaveToSession()
}
Listing 36-2The Contents of the cart_service.go File in the store/cart Folder
The sessionCart struct responds to changes by adding a JSON representation of its CartLine values to the session. The RegisterCartService function creates a scoped Cart service that creates a sessionCart and populates its lines from the session JSON data.

Creating the Cart Request Handler
Add a file named cart_handler.go to the sportsstore/store folder with the content shown in Listing 36-3.
package store
import (
    "platform/http/actionresults"
    "platform/http/handling"
    "sportsstore/models"
    "sportsstore/store/cart"
)
type CartHandler struct {
    models.Repository
    cart.Cart
    handling.URLGenerator
}
type CartTemplateContext struct {
    cart.Cart
    ProductListUrl string
    CartUrl string
    CheckoutUrl string
    RemoveUrl string
}
func (handler CartHandler) GetCart() actionresults.ActionResult {
    return actionresults.NewTemplateAction("cart.html", CartTemplateContext {
        Cart: handler.Cart,
        ProductListUrl: handler.mustGenerateUrl(ProductHandler.GetProducts, 0, 1),
        RemoveUrl: handler.mustGenerateUrl(CartHandler.PostRemoveFromCart),
    })
}
type CartProductReference struct {
    ID int
}
func (handler CartHandler) PostAddToCart(ref CartProductReference) actionresults.ActionResult {
    p := handler.Repository.GetProduct(ref.ID)
    handler.Cart.AddProduct(p)
    return actionresults.NewRedirectAction(
        handler.mustGenerateUrl(CartHandler.GetCart))
}
func (handler CartHandler) PostRemoveFromCart(ref CartProductReference) actionresults.ActionResult {
    handler.Cart.RemoveLineForProduct(ref.ID)
    return actionresults.NewRedirectAction(
        handler.mustGenerateUrl(CartHandler.GetCart))
}
func (handler CartHandler) mustGenerateUrl(method interface{}, data ...interface{}) string {
    url, err := handler.URLGenerator.GenerateUrl(method, data...)
    if (err != nil) {
        panic(err)
    }
    return url
}
Listing 36-3The Contents of the cart_handler.go File in the store Folder
The GetCart method will render a template that displays the contents of the user’s cart. The PostAddToCart method will be called to add a product to the cart, after which the browser is redirected to the GetCart method. To create the template used by the GetCart method, add a file named cart.html to the templates folder with the content shown in Listing 36-4.
{{ layout "simple_layout.html" }}
{{ $context := . }}
<div class="p-1">
    <h2>Your cart</h2>
    <table class="table table-bordered table-striped">
        <thead>
            <tr>
                <th>Quantity</th><th>Item</th>
                <th class="text-end">Price</th>
                <th class="text-end">Subtotal</th>
                <th />
            </tr>
        </thead>
        <tbody>
            {{ range $context.Cart.GetLines }}
                <tr>
                    <td class="text-start">{{ .Quantity }}</td>
                    <td class="text-start">{{ .Name }}</td>
                    <td class="text-end">{{ printf "$%.2f" .Price }}</td>
                    <td class="text-end">
                        {{ printf "$%.2f" .GetLineTotal }}
                    </td>
                    <td>
                        <form method="POST" action="{{  $context.RemoveUrl }}">
                            <input type="hidden" name="id" value="{{ .ID }}" />
                            <button class="btn btn-sm btn-danger" type="submit">
                                Remove
                            </button>
                        </form>
                    </td>
                </tr>
            {{ end }}
        </tbody>
        <tfoot>
            <tr>
                <td colspan="3" class="text-end">Total:</td>
                <td class="text-end">
                    {{ printf "$%.2f" $context.Cart.GetTotal }}
                </td>
            </tr>
        </tfoot>
    </table>
    <div class="text-center">
        <a class="btn btn-secondary" href="{{ $context.ProductListUrl }}">
            Continue shopping
        </a>
    </div>
</div>
Listing 36-4The Contents of the cart.html File in the templates Folder
This template produces an HTML table with rows for each of the products the user has selected. There is also a button that returns the user to the list of products so that further selections can be made. To create the layout used for this template, add a file named simple_layout.html to the templates folder with the content shown in Listing 36-5.
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>SportsStore</title>
    <link href="/files/bootstrap.min.css" rel="stylesheet" />
</head>
<body>
    <div class="bg-dark text-white p-2">
        <div class="container-fluid">
            <div class="row">
                <div class="col navbar-brand">SPORTS STORE</div>
            </div>
        </div>
    </div>
    {{ body }}
</body>
</html>
Listing 36-5The Contents of the simple_layout.html File in the templates Folder
This layout displays the SportsStore header but does not apply the column layout that is used for the product list.

Adding Products to the Cart
Each product will be displayed with an Add To Cart button that will send a request to the PostAddToCart method created in Listing 36-3. First, add the elements shown in Listing 36-6, which define the button and the form that it submits.
{{ layout "store_layout.html" }}
{{ define "left_column" }}
    {{ $context := . }}
    {{ handler "category" "getbuttons" $context.SelectedCategory}}
{{end}}
{{ define "right_column" }}
    {{ $context := . }}
    {{ range $context.Products }}
        <div class="card card-outline-primary m-1 p-1">
            <div class="bg-faded p-1">
                <h4>
                    {{ .Name }}
                    <span class="badge rounded-pill bg-primary" style="float:right">
                        <small>{{ printf "$%.2f" .Price }}</small>
                    </span>
                </h4>
            </div>
            <div class="card-text p-1">
                <form method="POST" action="{{ $context.AddToCartUrl }}">
                    {{ .Description }}
                    <input type="hidden" name="id" value="{{.ID}}" />
                    <button type="submit"class="btn btn-success btn-sm pull-right"
                        style="float:right">
                            Add To Cart
                    </button>
                </form>
            </div>
        </div>
    {{ end }}
    {{ template "page_buttons.html" $context }}
{{end}}
Listing 36-6Adding a Form in the product_list.html File in the templates Folder
To provide the template with the URL that is used in the form, make the changes shown in Listing 36-7 to its handler.
package store
import (
    "sportsstore/models"
    "platform/http/actionresults"
    "platform/http/handling"
    "math"
)
const pageSize = 4
type ProductHandler struct {
    Repository models.Repository
    URLGenerator handling.URLGenerator
}
type ProductTemplateContext struct {
    Products []models.Product
    Page int
    PageCount int
    PageNumbers []int
    PageUrlFunc func(int) string
    SelectedCategory int
    AddToCartUrl string
}
func (handler ProductHandler) GetProducts(category,
        page int) actionresults.ActionResult {
    prods, total := handler.Repository.GetProductPageCategory(category,
        page, pageSize)
    pageCount := int(math.Ceil(float64(total) / float64(pageSize)))
    return actionresults.NewTemplateAction("product_list.html",
        ProductTemplateContext {
            Products: prods,
            Page: page,
            PageCount: pageCount,
            PageNumbers: handler.generatePageNumbers(pageCount),
            PageUrlFunc: handler.createPageUrlFunction(category),
            SelectedCategory: category,
            AddToCartUrl: mustGenerateUrl(handler.URLGenerator,
                 CartHandler.PostAddToCart),
        })
}
func (handler ProductHandler) createPageUrlFunction(category int) func(int) string {
    return func(page int) string {
        url, _ := handler.URLGenerator.GenerateUrl(ProductHandler.GetProducts,
            category, page)
        return url
    }
}
func (handler ProductHandler) generatePageNumbers(pageCount int) (pages []int) {
    pages = make([]int, pageCount)
    for i := 0; i < pageCount; i++ {
        pages[i] = i + 1
    }
    return
}
func mustGenerateUrl(generator handling.URLGenerator, target interface{}) string {
    url, err := generator.GenerateUrl(target)
    if (err != nil) {
        panic(err)
    }
    return url;
}
Listing 36-7Adding Context Data in the product_handler.go File in the store Folder
The changes add a new property to the context struct used to pass data to the template, allowing the handler to provide a URL that can be used in the HTML form.

Configuring the Application
The final step to get the basic cart feature working is to configure the services, middleware, and handler required for sessions and the cart, as shown in Listing 36-8.
package main
import (
    "sync"
    "platform/http"
    "platform/http/handling"
    "platform/services"
    "platform/pipeline"
    "platform/pipeline/basic"
    "sportsstore/store"
    "sportsstore/models/repo"
    "platform/sessions"
    "sportsstore/store/cart"
)
func registerServices() {
    services.RegisterDefaultServices()
    repo.RegisterMemoryRepoService()
    sessions.RegisterSessionService()
    cart.RegisterCartService()
}
func createPipeline() pipeline.RequestPipeline {
    return pipeline.CreatePipeline(
        &basic.ServicesComponent{},
        &basic.LoggingComponent{},
        &basic.ErrorComponent{},
        &basic.StaticFileComponent{},
        &sessions.SessionComponent{},
        handling.NewRouter(
            handling.HandlerEntry{ "",  store.ProductHandler{}},
            handling.HandlerEntry{ "",  store.CategoryHandler{}},
            handling.HandlerEntry{ "", store.CartHandler{}},
            ).AddMethodAlias("/", store.ProductHandler.GetProducts, 0, 1).
            AddMethodAlias("/products[/]?[A-z0-9]*?",
                store.ProductHandler.GetProducts, 0, 1),
    )
}
func main() {
    registerServices()
    results, err := services.Call(http.Serve, createPipeline())
    if (err == nil) {
        (results[0].(*sync.WaitGroup)).Wait()
    } else {
        panic(err)
    }
}
Listing 36-8Configuring the Application for the Cart in the main.go File in the sportsstore Folder
Compile and execute the project and use a browser to request http://localhost:5000. The products are shown with an Add To Cart button that, when clicked, adds the product to the cart and redirects the browser to display the contents of the cart, as shown in Figure 36-1.

Figure 36-1Creating the store cart
Adding the Cart Summary Widget
Users expect to see a summary of their product selections when they are browsing the list of available products. Add the method shown in Listing 36-9 to the CartHandler request handler.
package store
import (
    "platform/http/actionresults"
    "platform/http/handling"
    "sportsstore/models"
    "sportsstore/store/cart"
)
type CartHandler struct {
    models.Repository
    cart.Cart
    handling.URLGenerator
}
type CartTemplateContext struct {
    cart.Cart
    ProductListUrl string
    CartUrl string
}
func (handler CartHandler) GetCart() actionresults.ActionResult {
    return actionresults.NewTemplateAction("cart.html", CartTemplateContext {
        Cart: handler.Cart,
        ProductListUrl: handler.mustGenerateUrl(ProductHandler.GetProducts, 0, 1),
    })
}
func (handler CartHandler) GetWidget() actionresults.ActionResult {
    return actionresults.NewTemplateAction("cart_widget.html", CartTemplateContext {
        Cart: handler.Cart,
        CartUrl: handler.mustGenerateUrl(CartHandler.GetCart),
    })
}
// ...statements omitted for brevity...
Listing 36-9Adding a Method in the cart_handler.go File in the store Folder
To define the template used by the new method, add a file named cart_widget.html to the templates folder with the content shown in Listing 36-10.
{{ $context := . }}
{{ $count := $context.Cart.GetItemCount }}
    <small class="navbar-text">
        {{ if gt $count 0 }}
            <b>Your cart:</b>
            {{ $count }} item(s)
            {{ printf "$%.2f" $context.Cart.GetTotal }}
        {{ else }}
            <span class="px-2 text-secondary">(empty cart)</span>
        {{ end }}
    </small>
<a href={{ $context.CartUrl }}
        class="btn btn-sm btn-secondary navbar-btn">
    <i class="fa fa-shopping-cart"></i>
</a>
Listing 36-10The Contents of the cart_widget.html File in the templates Folder
Invoking the Handler and Adding the CSS Icon Stylesheet
Listing 36-10 invokes the GetWidget method to insert the cart widget into the layout. The cart widget template requires a shopping cart icon, which is provided by the excellent Font Awesome package. In Chapter 35, I copied the Bootstrap CSS file so that it can be served using the static file features provided by the web platform, but multiple files are required for the Font Awesome package, so Listing 36-11 adds a link element with a URL for a content distribution network. (This means that you will have to be online to see the icons. See https://fontawesome.com for details of how to download the files, which can be installed in the sportsstore/files folder.)
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>SportsStore</title>
    <link href="/files/bootstrap.min.css" rel="stylesheet" />
    <link rel="stylesheet"
href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css"  />
</head>
<body>
    <div class="bg-dark text-white p-2">
        <div class="container-fluid">
            <div class="row">
                <div class="col navbar-brand">SPORTS STORE</div>
                <div class="col-6 navbar-text text-end">
                    {{ handler "cart" "getwidget" }}
                </div>
            </div>
        </div>
    </div>
    <div class="row m-1 p-1">
        <div id="sidebar" class="col-3">
            {{ template "left_column" . }}
        </div>
        <div class="col-9">
            {{ template "right_column" . }}
        </div>
    </div>
</body>
</html>
Listing 36-11Adding a Stylesheet Link in the store_layout.html File in the templates Folder
Compile and execute the project, and you will see the widget displayed in the page header. The widget will indicate that the cart is empty. Click one of the Add To Cart buttons and then click the Continue Shopping button to see the effect of the product selection reflected, shown in Figure 36-2.

Figure 36-2Displaying a cart widget
Using a Database Repository
Most of the basic features are in place, and it is time to retire the temporary repository I created in Chapter 35 and replace it with one that uses a persistent database. I am going to use SQLite. Use a command prompt to run the command shown in Listing 36-12 in the sportsstore folder to download and install the SQLite driver, which also includes the SQLite runtime.
go get modernc.org/sqlite
Listing 36-12Installing the SQLite Driver and Database Package
Creating the Repository Types
Add a file named sql_repo.go to the models/repo folder with the content shown in Listing 36-13, which defines the basic types for the SQL repository.
package repo
import (
    "database/sql"
    "platform/config"
    "platform/logging"
    "context"
)
type SqlRepository struct {
    config.Configuration
    logging.Logger
    Commands SqlCommands
    *sql.DB
    context.Context
}
type SqlCommands struct {
    Init,
    Seed,
    GetProduct,
    GetProducts,
    GetCategories,
    GetPage,
    GetPageCount,
    GetCategoryPage,
    GetCategoryPageCount *sql.Stmt
}
Listing 36-13The Contents of the sql_repo.go File in the models/repo Folder
The SqlRepository struct will be used to implement the Repository interface and will be provided to the rest of the application as a service. This struct defines a *sql.DB field that provides access to the database and a Commands field, which is a collection of *sql.Stmt fields that will be populated with the prepared statements required to implement the features of the Repository interface.

Opening the Database and Loading the SQL Commands
In Chapter 26, I defined SQL commands as Go strings. In real projects, I prefer to define SQL commands in text files with a .sql file extension, which means that my editor can perform syntax checking. This means I need to open a database and then locate and process the SQL files that correspond to the fields defined by the SqlCommands struct defined in Listing 36-13. Add a file named sql_loader.go to the models/repo folder with the content shown in Listing 36-14.
package repo
import (
    "os"
    "database/sql"
    "reflect"
    "platform/config"
    "platform/logging"
    _ "modernc.org/sqlite"
)
func openDB(config config.Configuration, logger logging.Logger) (db *sql.DB,
        commands *SqlCommands, needInit bool) {
    driver := config.GetStringDefault("sql:driver_name", "sqlite")
    connectionStr, found := config.GetString("sql:connection_str")
    if !found {
        logger.Panic("Cannot read SQL connection string from config")
        return
    }
    if _, err := os.Stat(connectionStr); os.IsNotExist(err) {
        needInit = true
    }
    var err error
    if db, err = sql.Open(driver, connectionStr); err == nil {
        commands = loadCommands(db, config, logger)
    } else {
        logger.Panic(err.Error())
    }
    return
}
func loadCommands(db *sql.DB, config config.Configuration,
        logger logging.Logger) (commands *SqlCommands)  {
    commands = &SqlCommands {}
    commandVal := reflect.ValueOf(commands).Elem()
    commandType := reflect.TypeOf(commands).Elem()
    for i := 0; i < commandType.NumField(); i++ {
        commandName := commandType.Field(i).Name
        logger.Debugf("Loading SQL command: %v", commandName)
        stmt := prepareCommand(db, commandName, config, logger)
        commandVal.Field(i).Set(reflect.ValueOf(stmt))
    }
    return commands
}
func prepareCommand(db *sql.DB, command string, config config.Configuration,
        logger logging.Logger) *sql.Stmt {
    filename, found := config.GetString("sql:commands:" + command)
    if !found {
        logger.Panicf("Config does not contain location for SQL command: %v",
            command)
    }
    data, err := os.ReadFile(filename)
    if err != nil {
        logger.Panicf("Cannot read SQL command file: %v", filename)
    }
    statement, err := db.Prepare(string(data))
    if (err != nil) {
        logger.Panicf(err.Error())
    }
    return statement
}
Listing 36-14The Contents of the sql_loader.go File in the models/repo Folder
The openDB function reads the database driver name and connection string from the configuration system and opens the database before calling the loadCommands function. The loadCommands function uses reflection to get a list of the fields defined by the SqlCommands struct and calls the prepareCommand for each one. The prepareCommand function gets the name of the file that contains the SQL for the command from the configuration system, reads the contents of the file, and creates a prepared statement, which is assigned to the SqlCommands field.

Defining the Seed and Initialization Statements
For each feature required by the Repository interface, I need to define a SQL file that contains the query and define a Go method that will execute it. I am going to start with the Seed and Init commands. The Seed command is required by the Repository interface, but the Init function is specific to the SqlRepository struct and will be used to create the database schema. Add a file named sql_initseed.go to the models/repo folder with the contents shown in Listing 36-15.

Notice that all the queries used by the repository use the methods that accept a context.Context argument (ExecContext, QueryContext, etc.). The platform created in Chapters 32–34 passes Context values to middleware components and request handlers, so I have used them when querying the database.
package repo
func (repo *SqlRepository) Init() {
    if _, err := repo.Commands.Init.ExecContext(repo.Context); err != nil {
        repo.Logger.Panic("Cannot exec init command")
    }
}
func (repo *SqlRepository) Seed() {
    if _, err := repo.Commands.Seed.ExecContext(repo.Context); err != nil {
        repo.Logger.Panic("Cannot exec seed command")
    }
}
Listing 36-15The Contents of the sql_initseed.go File in the models/repo Folder
To create the SQL commands these methods use, create the sportsstore/sql folder and add to it a file named init_db.sql with the content shown in Listing 36-16.
DROP TABLE IF EXISTS Products;
DROP TABLE IF EXISTS Categories;
CREATE TABLE IF NOT EXISTS Categories (
    Id INTEGER NOT NULL PRIMARY KEY,        Name TEXT
);
CREATE TABLE IF NOT EXISTS Products (
    Id INTEGER NOT NULL PRIMARY KEY,
    Name TEXT, Description TEXT,
    Category INTEGER, Price decimal(8, 2),
    CONSTRAINT CatRef FOREIGN KEY(Category) REFERENCES Categories (Id)
);
Listing 36-16The Contents of the init_db.sql File in the sql Folder
This file contains statements that drop and re-create Categories and Products tables. Add a file named seed_db.sql to the sportsstore/sql folder with the content shown in Listing 36-17.
INSERT INTO Categories(Id, Name) VALUES
        (1, "Watersports"), (2, "Soccer"), (3, "Chess");
INSERT INTO Products(Id, Name, Description, Category, Price) VALUES
        (1, "Kayak", "A boat for one person", 1, 275),
        (2, "Lifejacket", "Protective and fashionable", 1, 48.95),
        (3, "Soccer Ball", "FIFA-approved size and weight", 2, 19.50),
        (4, "Corner Flags", "Give your playing field a professional touch", 2, 34.95),
        (5, "Stadium", "Flat-packed 35,000-seat stadium", 2, 79500),
        (6, "Thinking Cap", "Improve brain efficiency by 75%", 3, 16),
        (7, "Unsteady Chair", "Secretly give your opponent a disadvantage", 3, 29.95),
        (8, "Human Chess Board", "A fun game for the family", 3, 75),
        (9, "Bling-Bling King", "Gold-plated, diamond-studded King", 3, 1200);
Listing 36-17The Contents of the seed_db.sql File in the sql Folder
The file contains INSERT statements that create three categories and nine products, using values that will be familiar to anyone who has read any of my other books.

Defining the Basic Queries
To complete the repository, I have to work through the methods required by the Repository interface, defining a Go implementation of that method and the SQL query that it will use. Add a file named sql_basic_methods.go to the models/repo folder with the content shown in Listing 36-18.
package repo
import "sportsstore/models"
func (repo *SqlRepository) GetProduct(id int) (p models.Product) {
    row := repo.Commands.GetProduct.QueryRowContext(repo.Context, id)
    if row.Err() == nil {
        var err error
        if p, err = scanProduct(row); err != nil {
            repo.Logger.Panicf("Cannot scan data: %v", err.Error())
        }
    } else {
        repo.Logger.Panicf("Cannot exec GetProduct command: %v", row.Err().Error())
    }
    return
}
func (repo *SqlRepository) GetProducts() (results []models.Product) {
    rows, err := repo.Commands.GetProducts.QueryContext(repo.Context)
    if err == nil {
        if results, err = scanProducts(rows); err != nil {
            repo.Logger.Panicf("Cannot scan data: %v", err.Error())
            return
        }
    } else {
        repo.Logger.Panicf("Cannot exec GetProducts command: %v", err)
    }
    return
}
func (repo *SqlRepository) GetCategories() []models.Category {
    results := make([]models.Category, 0, 10)
    rows, err := repo.Commands.GetCategories.QueryContext(repo.Context)
    if err == nil {
        for rows.Next() {
            c := models.Category{}
            if err := rows.Scan(&c.ID, &c.CategoryName); err != nil {
                repo.Logger.Panicf("Cannot scan data: %v", err.Error())
            }
            results = append(results, c)
        }
    } else {
        repo.Logger.Panicf("Cannot exec GetCategories command: %v", err)
    }
    return results
}
Listing 36-18The Contents of the sql_basic_methods.go File in the models/repo Folder
Listing 36-18 implements the GetProduct, GetProducts, and GetCategories methods. To define the functions that scan Product values from the SQL results, add a file named sql_scan.go to the models/repo folder with the content shown in Listing 36-19.
package repo
import (
    "database/sql"
    "sportsstore/models"
)
func scanProducts(rows *sql.Rows) (products []models.Product, err error) {
    products = make([]models.Product, 0, 10)
    for rows.Next() {
        p := models.Product{ Category: &models.Category{}}
        err = rows.Scan(&p.ID, &p.Name, &p.Description, &p.Price,
            &p.Category.ID, &p.Category.CategoryName)
        if (err == nil) {
            products = append(products, p)
        } else {
            return
        }
    }
    return
}
func scanProduct(row *sql.Row) (p models.Product, err error) {
    p = models.Product{ Category: &models.Category{}}
    err = row.Scan(&p.ID, &p.Name, &p.Description, &p.Price, &p.Category.ID,
        &p.Category.CategoryName)
    return p, err
}
Listing 36-19The Contents of the sql_scan.go File in the models/repo Folder
The scanProducts function scans values when there are multiple rows, while the scanProduct function does the same thing for results with a single row.

Defining the SQL Files for the Basic Queries
Now comes the process of defining the SQL files for each query. Add a file named get_product.sql to the sportsstore/sql folder with the content shown in Listing 36-20.
SELECT Products.Id, Products.Name, Products.Description, Products.Price,
    Categories.Id, Categories.Name
FROM Products, Categories
WHERE Products.Category = Categories.Id
AND Products.Id = ?
Listing 36-20The Contents of the get_product.sql File in the sql Folder
This query produces a single row containing the details for a product with a specified Id. Add a file named get_products.sql to the sportsstore/sql folder with the content shown in Listing 36-21.
SELECT Products.Id, Products.Name, Products.Description, Products.Price,
    Categories.Id, Categories.Name
FROM Products, Categories
WHERE Products.Category = Categories.Id
ORDER BY Products.Id
Listing 36-21The Contents of the get_products.sql File in the sql Folder
This query produces rows for all the products in the database. Next, add a file named get_categories.sql to the sportsstore/sql folder with the content shown in Listing 36-22.
SELECT Categories.Id, Categories.Name
FROM Categories ORDER BY Categories.Id
Listing 36-22The Contents of the get_categories.sql File in the sql Folder
This query selects all of the rows in the Categories folder.

Defining the Paged Queries
The methods for paged data are more complex because they have to perform one query for a page of data and query one to get the total number of available results. Add a file named sql_page_methods.go to the sportsstore/models/repo folder with the content shown in Listing 36-23.
package repo
import "sportsstore/models"
func (repo *SqlRepository) GetProductPage(page,
        pageSize int) (products []models.Product, totalAvailable int) {
    rows, err := repo.Commands.GetPage.QueryContext(repo.Context,
        pageSize, (pageSize * page) - pageSize)
    if err == nil {
        if products, err = scanProducts(rows); err != nil {
            repo.Logger.Panicf("Cannot scan data: %v", err.Error())
            return
        }
    } else {
        repo.Logger.Panicf("Cannot exec GetProductPage command: %v", err)
        return
    }
    row := repo.Commands.GetPageCount.QueryRowContext(repo.Context)
    if row.Err() == nil {
        if err := row.Scan(&totalAvailable); err != nil {
            repo.Logger.Panicf("Cannot scan data: %v", err.Error())
        }
    } else {
        repo.Logger.Panicf("Cannot exec GetPageCount command: %v", row.Err().Error())
    }
    return
}
func (repo *SqlRepository) GetProductPageCategory(categoryId int, page,
        pageSize int) (products []models.Product, totalAvailable int) {
    if (categoryId == 0) {
        return repo.GetProductPage(page, pageSize)
    }
    rows, err := repo.Commands.GetCategoryPage.QueryContext(repo.Context, categoryId,
        pageSize, (pageSize * page) - pageSize)
    if err == nil {
        if products, err = scanProducts(rows); err != nil {
            repo.Logger.Panicf("Cannot scan data: %v", err.Error())
            return
        }
    } else {
        repo.Logger.Panicf("Cannot exec GetProductPage command: %v", err)
        return
    }
    row := repo.Commands.GetCategoryPageCount.QueryRowContext(repo.Context,
        categoryId)
    if row.Err() == nil {
        if err := row.Scan(&totalAvailable); err != nil {
            repo.Logger.Panicf("Cannot scan data: %v", err.Error())
        }
    } else {
        repo.Logger.Panicf("Cannot exec GetCategoryPageCount command: %v",
            row.Err().Error())
    }
    return
}
Listing 36-23The Contents of the sql_page_methods.go File in the models/repo Folder
To define the main SQL query used by the GetProductPage method, add a file named get_product_page.sql to the sportsstore/sql folder with the content shown in Listing 36-24.
SELECT Products.Id, Products.Name, Products.Description, Products.Price,
    Categories.Id, Categories.Name
FROM Products, Categories
WHERE Products.Category = Categories.Id
ORDER BY Products.Id
LIMIT ? OFFSET ?
Listing 36-24The Contents of the get_product_page.sql File in the sql Folder
To define the query used to get the total number of products in the database, add a file named get_page_count.sql to the sportsstore/sql folder with the content shown in Listing 36-25.
SELECT COUNT (Products.Id)
FROM Products, Categories
WHERE Products.Category = Categories.Id;
Listing 36-25The Contents of the get_page_count.sql File in the sql Folder
To define the main query used by the GetProductPageCategory method, add a file named get_category_product_page.sql to the sportsstore/sql folder with the content shown in Listing 36-26.
SELECT Products.Id, Products.Name, Products.Description, Products.Price,
    Categories.Id, Categories.Name
FROM Products, Categories
WHERE Products.Category = Categories.Id AND        Products.Category = ?
ORDER BY Products.Id
LIMIT ? OFFSET ?
Listing 36-26The Contents of the get_category_product_page.sql File in the sql Folder
To define the query that determines how many products are in a specific category, add a file named get_category_product_page_count.sql to the sportsstore/sql folder with the content shown in Listing 36-27.
SELECT COUNT (Products.Id)
FROM Products, Categories
WHERE Products.Category = Categories.Id AND Products.Category = ?
Listing 36-27The Contents of the get_category_product_page_count.sql File in the sql Folder
Defining the SQL Repository Service
To define the function that will register the repository service, add a file named sql_service.go to the sportssstore/models/repo folder with the content shown in Listing 36-28.
package repo
import (
    "sync"
    "context"
    "database/sql"
    "platform/services"
    "platform/config"
    "platform/logging"
    "sportsstore/models"
)
func RegisterSqlRepositoryService() {
    var db *sql.DB
    var commands *SqlCommands
    var needInit bool
    loadOnce := sync.Once {}
    resetOnce := sync.Once {}
    services.AddScoped(func (ctx context.Context, config config.Configuration,
            logger logging.Logger) models.Repository {
        loadOnce.Do(func () {
            db, commands, needInit = openDB(config, logger)
        })
        repo := &SqlRepository{
            Configuration: config,
            Logger: logger,
            Commands: *commands,
            DB: db,
            Context: ctx,
        }
        resetOnce.Do(func() {
            if needInit || config.GetBoolDefault("sql:always_reset", true) {
                repo.Init()
                repo.Seed()
            }
        })
        return repo
    })
}
Listing 36-28The Contents of the sql_service.go File in the models/repo Folder
The database is opened the first time a dependency on the Repository interface is resolved so that the commands are prepared only once. A configuration setting specifies whether the database should be reset every time the application starts, which is useful during development, and this is done by executing the Init method, followed by the Seed method.

Configuring the Application to Use the SQL Repository
Listing 36-29 defines the configuration settings that specify the locations of the SQL files. The code that loads these files will panic if these files cannot be loaded, so it is important to ensure that the paths specified match those used to create the files.
{
    "logging" : {
        "level": "debug"
    },
    "files": {
        "path": "files"
    },
    "templates": {
        "path": "templates/*.html",
        "reload": true
    },
    "sessions": {
        "key": "MY_SESSION_KEY",
        "cyclekey": true
    },
    "sql": {
        "connection_str": "store.db",
        "always_reset": true,
        "commands": {
            "Init":                 "sql/init_db.sql",
            "Seed":                 "sql/seed_db.sql",
            "GetProduct":           "sql/get_product.sql",
            "GetProducts":          "sql/get_products.sql",
            "GetCategories":        "sql/get_categories.sql",
            "GetPage":              "sql/get_product_page.sql",
            "GetPageCount":         "sql/get_page_count.sql",
            "GetCategoryPage":      "sql/get_category_product_page.sql",
            "GetCategoryPageCount": "sql/get_category_product_page_count.sql"
        }
    }
}
Listing 36-29Defining Configuration Settings in the config.json File in the sportsstore Folder
The final change is to register the SQL repository so that it is used to resolve dependencies on the Repository interface and comment out the statement that registered the temporary repository, as shown in Listing 36-30.
...
func registerServices() {
    services.RegisterDefaultServices()
    //repo.RegisterMemoryRepoService()
    repo.RegisterSqlRepositoryService()
    sessions.RegisterSessionService()
    cart.RegisterCartService()
}
...
Listing 36-30Changing the Repository Service in the main.go File in the sportsstore Folder
Compile and execute the project and use a browser to request http://localhost:5000, and you will see data that is read from the database, as shown in Figure 36-3.

Figure 36-3Using data from the database
Summary
In this chapter, I continued the development of the SportsStore application by adding support for the shopping cart and replacing the temporary repository with one that uses a SQL database. I continue the development of the SportsStore application in the next chapter.


Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


36. SportsStore: Cart and Database
37. SportsStore: Checkout and Administration
38. SportsStore: Finishing and Deployment
21h 44m remaining
© The Author(s), under exclusive license to APress Media, LLC, part of Springer Nature 2022
A. FreemanPro Go
https://doi.org/10.1007/978-1-4842-7355-5_37
37. SportsStore: Checkout and Administration
Adam Freeman1  
(1)
London, UK
 
In this chapter, I continue the development of the SportsStore application by adding a checkout process and starting work on the administration features.

TipYou can download the example project for this chapter—and for all the other chapters in this book—from https://github.com/apress/pro-go. See Chapter 2 for how to get help if you have problems running the examples.
Creating the Checkout Process
To complete the store experience, I need to let the user check out and complete an order. In this section, I will extend the data model to describe shipping details and create handlers to capture those details and use them to store an order in the database. Most e-commerce sites would not simply stop there, of course, and I have not provided support for processing credit cards or other forms of payment. But I want to keep things focused on Go, so a simple database entry will do.

Defining the Model
To define the type that will represent a user’s shipping details and product selections, add a file named order.go to the models folder with the content shown in Listing 37-1.
package models
type Order struct {
    ID int
    ShippingDetails
    Products []ProductSelection
    Shipped bool
}
type ShippingDetails struct {
    Name string `validation:"required"`
    StreetAddr string `validation:"required"`
    City string `validation:"required"`
    State string `validation:"required"`
    Zip string `validation:"required"`
    Country string `validation:"required"`
}
type ProductSelection struct{
    Quantity int
    Product
}
Listing 37-1The Contents of the order.go File in the models Folder
The Order type defines a ShippingDetails field, which will be used to represent the customer’s shipping details and which has been defined with struct tags for the platform validation feature. There is also a Products field, which will be used to store the products and quantities the customer has ordered.

Extending the Repository
The next step is to extend the repository so that it can be used to store and retrieve orders. Add the methods shown in Listing 37-2 to the repository.go file in the sportsstore/models folder.
package models
type Repository interface {
    GetProduct(id int) Product
    GetProducts() []Product
    GetProductPage(page, pageSize int) (products []Product, totalAvailable int)
    GetProductPageCategory(categoryId int, page, pageSize int) (products []Product,
        totalAvailable int)
    GetCategories() []Category
    GetOrder(id int) Order
    GetOrders() []Order
    SaveOrder(*Order)
    Seed()
}
Listing 37-2Adding Interface Methods in the repository.go File in the models Folder
Listing 37-3 shows the changes required to the SQL file that which create new tables for storing order data.
DROP TABLE IF EXISTS OrderLines;
DROP TABLE IF EXISTS Orders;
DROP TABLE IF EXISTS Products;
DROP TABLE IF EXISTS Categories;
CREATE TABLE IF NOT EXISTS Categories (
    Id INTEGER NOT NULL PRIMARY KEY,        Name TEXT
);
CREATE TABLE IF NOT EXISTS Products (
    Id INTEGER NOT NULL PRIMARY KEY,
    Name TEXT, Description TEXT,
    Category INTEGER, Price decimal(8, 2),
    CONSTRAINT CatRef FOREIGN KEY(Category) REFERENCES Categories (Id)
);
CREATE TABLE IF NOT EXISTS OrderLines (
    Id INTEGER NOT NULL PRIMARY KEY,
    OrderId INT, ProductId INT, Quantity INT,
    CONSTRAINT OrderRef FOREIGN KEY(ProductId) REFERENCES Products (Id)
    CONSTRAINT OrderRef FOREIGN KEY(OrderId) REFERENCES Orders (Id)
);
CREATE TABLE IF NOT EXISTS Orders (
    Id INTEGER NOT NULL PRIMARY KEY,
    Name TEXT NOT NULL,
    StreetAddr TEXT NOT NULL,
    City TEXT NOT NULL,
    Zip TEXT NOT NULL,
    Country TEXT NOT NULL,
    Shipped BOOLEAN
);
Listing 37-3Adding Tables in the init_db.sql File in the sql Folder
To define some seed data, add the statements shown in Listing 37-4 to the seed_db.sql file in the sportsstore/sql folder.
INSERT INTO Categories(Id, Name) VALUES
        (1, "Watersports"), (2, "Soccer"), (3, "Chess");
INSERT INTO Products(Id, Name, Description, Category, Price) VALUES
        (1, "Kayak", "A boat for one person", 1, 275),
        (2, "Lifejacket", "Protective and fashionable", 1, 48.95),
        (3, "Soccer Ball", "FIFA-approved size and weight", 2, 19.50),
        (4, "Corner Flags", "Give your playing field a professional touch", 2, 34.95),
        (5, "Stadium", "Flat-packed 35,000-seat stadium", 2, 79500),
        (6, "Thinking Cap", "Improve brain efficiency by 75%", 3, 16),
        (7, "Unsteady Chair", "Secretly give your opponent a disadvantage", 3, 29.95),
        (8, "Human Chess Board", "A fun game for the family", 3, 75),
        (9, "Bling-Bling King", "Gold-plated, diamond-studded King", 3, 1200);
INSERT INTO Orders(Id, Name, StreetAddr, City, Zip, Country, Shipped) VALUES
        (1, "Alice", "123 Main St", "New Town", "12345", "USA", false),
        (2, "Bob", "The Grange", "Upton", "UP12 6YT", "UK", false);
INSERT INTO OrderLines(Id, OrderId, ProductId, Quantity) VALUES
        (1, 1, 1, 1), (2, 1, 2, 2), (3, 1, 8, 1), (4, 2, 5, 2);
Listing 37-4Adding Seed Data in the seed_db.sql File in the sql Folder
Disabling the Temporary Repository
The temporary repository created in Chapter 35 no longer defines all the methods specified by the Repository interface. In a real project, I typically switch back to the memory repository when adding a new feature, like orders, and then switch back to SQL once I understand what is required. But, for this project, I am simply going to comment out the code that creates the memory-based service, as shown in Listing 37-5, so that it doesn’t cause a compiler error.
package repo
import (
//    "platform/services"
    "sportsstore/models"
    "math"
)
// func RegisterMemoryRepoService() {
//     services.AddSingleton(func() models.Repository {
//         repo := &MemoryRepo{}
//         repo.Seed()
//         return repo
//     })
// }
type MemoryRepo struct {
    products []models.Product
    categories []models.Category
}
// ...other statements omitted for brevity...
Listing 37-5Commenting Code in the memory_repo.go File in the models/repo Folder
Defining the Repository Methods and Commands
The next step is to define and implement the new Repository methods and the SQL files on which they will rely. Listing 37-6 adds new commands to the struct used to load SQL files for the database.
package repo
import (
    "database/sql"
    "platform/config"
    "platform/logging"
    "context"
)
type SqlRepository struct {
    config.Configuration
    logging.Logger
    Commands SqlCommands
    *sql.DB
    context.Context
}
type SqlCommands struct {
    Init,
    Seed,
    GetProduct,
    GetProducts,
    GetCategories,
    GetPage,
    GetPageCount,
    GetCategoryPage,
    GetCategoryPageCount,
    GetOrder,
    GetOrderLines,
    GetOrders,
    GetOrdersLines,
    SaveOrder,
    SaveOrderLine *sql.Stmt
}
Listing 37-6Adding Commands in the sql_repo.go File in the models/repo Folder
Defining the SQL Files
Add a file named get_order.sql to the sportsstore/sql folder with the content shown in Listing 37-7.
SELECT Orders.Id, Orders.Name, Orders.StreetAddr, Orders.City, Orders.Zip,
    Orders.Country, Orders.Shipped
FROM Orders
WHERE Orders.Id = ?
Listing 37-7The Contents of the get_order.sql File in the sql Folder
This query retrieves the details of an order. To define the query that will get details of the products that were ordered, add a file named get_order_lines.sql to the sportsstore/sql folder with the content shown in Listing 37-8.
SELECT OrderLines.Quantity, Products.Id, Products.Name, Products.Description,
    Products.Price, Categories.Id, Categories.Name
FROM Orders, OrderLines, Products, Categories
WHERE Orders.Id = OrderLines.OrderId
    AND OrderLines.ProductId = Products.Id
    AND Products.Category = Categories.Id
    AND Orders.Id = ?
ORDER BY Products.Id
Listing 37-8The Contents of the get_order_lines.sql File in the sql Folder
To define the query that will get all the orders in the database, add a file named get_orders.sql to the sportsstore/sql folder with the content shown in Listing 37-9.
SELECT Orders.Id, Orders.Name, Orders.StreetAddr, Orders.City, Orders.Zip, Orders.Country, Orders.Shipped
FROM Orders
ORDER BY Orders.Shipped, Orders.Id
Listing 37-9The Contents of the get_orders.sql Folder in the sql Folder
To define the query that will get all the product details associated with all orders, add a file named get_orders_lines.sql to the sportsstore/sql folder with the content shown in Listing 37-10.
SELECT Orders.Id, OrderLines.Quantity, Products.Id, Products.Name,
    Products.Description, Products.Price, Categories.Id, Categories.Name
FROM Orders, OrderLines, Products, Categories
WHERE Orders.Id = OrderLines.OrderId
    AND OrderLines.ProductId = Products.Id
    AND Products.Category = Categories.Id
ORDER BY Orders.Id
Listing 37-10The Contents of the get_orders_lines.sql File in the sql Folder
To define the statement that will store an order, add a file named save_order.sql to the sportsstore/sql folder with the content shown in Listing 37-11.
INSERT INTO Orders(Name, StreetAddr, City, Zip, Country, Shipped)
VALUES (?, ?, ?, ?, ?, ?)
Listing 37-11The Contents of the save_order.sql File in the sql Folder
To define the statement that will store details of a product selection associated with an order, add a file named save_order_line.sql to the sportsstore/sql folder with the content shown in Listing 37-12.
INSERT INTO OrderLines(OrderId, ProductId, Quantity)
VALUES (?, ?, ?)
Listing 37-12The Contents of the save_order_line.sql File in the sql Folder
Listing 37-13 adds configuration settings for the new SQL files.
...
"sql": {
    "connection_str": "store.db",
    "always_reset": true,
    "commands": {
        "Init":                 "sql/init_db.sql",
        "Seed":                 "sql/seed_db.sql",
        "GetProduct":           "sql/get_product.sql",
        "GetProducts":          "sql/get_products.sql",
        "GetCategories":        "sql/get_categories.sql",
        "GetPage":              "sql/get_product_page.sql",
        "GetPageCount":         "sql/get_page_count.sql",
        "GetCategoryPage":      "sql/get_category_product_page.sql",
        "GetCategoryPageCount": "sql/get_category_product_page_count.sql",
        "GetOrder": "sql/get_order.sql",
        "GetOrderLines": "sql/get_order_lines.sql",
        "GetOrders": "sql/get_orders.sql",
        "GetOrdersLines": "sql/get_orders_lines.sql",
        "SaveOrder": "sql/save_order.sql",
        "SaveOrderLine": "sql/save_order_line.sql"
    }
}
...
Listing 37-13Adding Configuration Settings in the config.json File in the sportsstore Folder
Implementing the Repository Methods
Add a file named sql_orders_one.go to the sportsstore/models/repo folder with the content shown in Listing 37-14.
package repo
import "sportsstore/models"
func (repo *SqlRepository) GetOrder(id int) (order models.Order) {
    order = models.Order { Products: []models.ProductSelection {}}
    row := repo.Commands.GetOrder.QueryRowContext(repo.Context, id)
    if row.Err() == nil {
        err := row.Scan(&order.ID, &order.Name, &order.StreetAddr, &order.City,
            &order.Zip, &order.Country, &order.Shipped)
        if (err != nil) {
            repo.Logger.Panicf("Cannot scan order data: %v", err.Error())
            return
        }
        lineRows, err := repo.Commands.GetOrderLines.QueryContext(repo.Context, id)
        if (err == nil) {
            for lineRows.Next() {
                ps := models.ProductSelection {
                    Product: models.Product{ Category: &models.Category{}},
                }
                err = lineRows.Scan(&ps.Quantity, &ps.Product.ID, &ps.Product.Name,
                    &ps.Product.Description,&ps.Product.Price,
                    &ps.Product.Category.ID, &ps.Product.Category.CategoryName)
                if err == nil {
                    order.Products = append(order.Products, ps)
                } else {
                    repo.Logger.Panicf("Cannot scan order line data: %v",
                        err.Error())
                }
            }
        } else {
            repo.Logger.Panicf("Cannot exec GetOrderLines command: %v", err.Error())
        }
    } else {
        repo.Logger.Panicf("Cannot exec GetOrder command: %v", row.Err().Error())
    }
    return
}
Listing 37-14The Contents of the sql_orders_one.go File in the models/repo Folder
This method queries the database for an order and then queries again for details of the product selections associated with that order. Next, add a file named sql_orders_all.go in the sportsstore/models/repo folder with the content shown in Listing 37-15.
package repo
import "sportsstore/models"
func (repo *SqlRepository) GetOrders() []models.Order {
    orderMap := make(map[int]*models.Order, 10)
    orderRows, err := repo.Commands.GetOrders.QueryContext(repo.Context)
    if err != nil {
        repo.Logger.Panicf("Cannot exec GetOrders command: %v", err.Error())
    }
    for orderRows.Next() {
        order := models.Order { Products: []models.ProductSelection {}}
        err := orderRows.Scan(&order.ID, &order.Name, &order.StreetAddr, &order.City,
            &order.Zip, &order.Country, &order.Shipped)
        if (err != nil) {
            repo.Logger.Panicf("Cannot scan order data: %v", err.Error())
            return  []models.Order {}
        }
        orderMap[order.ID] = &order
    }
    lineRows, err := repo.Commands.GetOrdersLines.QueryContext(repo.Context)
    if (err != nil) {
        repo.Logger.Panicf("Cannot exec GetOrdersLines command: %v", err.Error())
    }
    for lineRows.Next() {
        var order_id int
        ps := models.ProductSelection {
            Product: models.Product{ Category: &models.Category{} },
        }
        err = lineRows.Scan(&order_id, &ps.Quantity, &ps.Product.ID,
            &ps.Product.Name, &ps.Product.Description, &ps.Product.Price,
            &ps.Product.Category.ID, &ps.Product.Category.CategoryName)
        if err == nil {
            orderMap[order_id].Products = append(orderMap[order_id].Products, ps)
        } else {
            repo.Logger.Panicf("Cannot scan order line data: %v", err.Error())
        }
    }
    orders := make([]models.Order, 0, len(orderMap))
    for _, o := range orderMap {
        orders = append(orders, *o)
    }
    return orders
}
Listing 37-15The Contents of the sql_orders_all.go File in the models/repo Folder
This method queries the database for all the orders and their related product selections. To implement the final method, add a file named sql_orders_save.go to the sportsstore/models/repo folder with the content shown in Listing 37-16.
package repo
import "sportsstore/models"
func (repo *SqlRepository) SaveOrder(order *models.Order) {
    tx, err := repo.DB.Begin()
    if err != nil {
        repo.Logger.Panicf("Cannot create transaction: %v", err.Error())
        return
    }
    result, err :=  tx.StmtContext(repo.Context,
        repo.Commands.SaveOrder).Exec(order.Name, order.StreetAddr, order.City,
            order.Zip, order.Country, order.Shipped)
    if err != nil {
        repo.Logger.Panicf("Cannot exec SaveOrder command: %v", err.Error())
        tx.Rollback()
        return
    }
    id, err := result.LastInsertId()
    if err != nil {
        repo.Logger.Panicf("Cannot get inserted ID: %v", err.Error())
        tx.Rollback()
        return
    }
    statement := tx.StmtContext(repo.Context, repo.Commands.SaveOrderLine)
    for _, sel := range order.Products {
        _, err := statement.Exec(id, sel.Product.ID, sel.Quantity)
        if err != nil {
            repo.Logger.Panicf("Cannot exec SaveOrderLine command: %v", err.Error())
            tx.Rollback()
            return
        }
    }
    err = tx.Commit()
    if err != nil {
        repo.Logger.Panicf("Transaction cannot be committed: %v", err.Error())
        err = tx.Rollback()
        if err != nil {
            repo.Logger.Panicf("Transaction cannot be rolled back: %v", err.Error())
        }
    }
    order.ID = int(id)
}
Listing 37-16The Contents of the sql_orders_save.go File in the models/repo Folder
This method uses a transaction to ensure that a new order and its related product selections are added to the database. If the transaction fails, then the changes are rolled back.

Creating the Request Handler and Templates
The next step is to define the request handler that will allow the user to provide their shipping details and check out. As noted at the start of this chapter, storing the order will complete the checkout process, although real online stores would prompt the user to provide payment. Add a file named order_handler.go to the sportsstore/store folder with the content shown in Listing 37-17.
package store
import (
    "encoding/json"
    "platform/http/actionresults"
    "platform/http/handling"
    "platform/sessions"
    "platform/validation"
    "sportsstore/models"
    "sportsstore/store/cart"
    "strings"
)
type OrderHandler struct {
    cart.Cart
    sessions.Session
    Repository models.Repository
    URLGenerator handling.URLGenerator
    validation.Validator
}
type OrderTemplateContext struct {
    models.ShippingDetails
    ValidationErrors [][]string
    CancelUrl string
}
func (handler OrderHandler) GetCheckout() actionresults.ActionResult {
    context := OrderTemplateContext {}
    jsonData := handler.Session.GetValueDefault("checkout_details", "")
    if jsonData != nil {
        json.NewDecoder(strings.NewReader(jsonData.(string))).Decode(&context)
    }
    context.CancelUrl = mustGenerateUrl(handler.URLGenerator, CartHandler.GetCart)
    return actionresults.NewTemplateAction("checkout.html", context)
}
func (handler OrderHandler) PostCheckout(details models.ShippingDetails) actionresults.ActionResult {
    valid, errors := handler.Validator.Validate(details)
    if (!valid) {
        ctx := OrderTemplateContext {
            ShippingDetails: details,
            ValidationErrors: [][]string {},
        }
        for _, err := range errors {
            ctx.ValidationErrors = append(ctx.ValidationErrors,
                []string { err.FieldName, err.Error.Error()})
        }
        builder := strings.Builder{}
        json.NewEncoder(&builder).Encode(ctx)
        handler.Session.SetValue("checkout_details", builder.String())
        redirectUrl := mustGenerateUrl(handler.URLGenerator,
            OrderHandler.GetCheckout)
        return actionresults.NewRedirectAction(redirectUrl)
    } else {
        handler.Session.SetValue("checkout_details", "")
    }
    order := models.Order {
        ShippingDetails: details,
        Products: []models.ProductSelection {},
    }
    for _, cl := range handler.Cart.GetLines() {
        order.Products = append(order.Products, models.ProductSelection {
            Quantity: cl.Quantity,
            Product: cl.Product,
        })
    }
    handler.Repository.SaveOrder(&order)
    handler.Cart.Reset()
    targetUrl, _ := handler.URLGenerator.GenerateUrl(OrderHandler.GetSummary,
        order.ID)
    return actionresults.NewRedirectAction(targetUrl)
}
func (handler OrderHandler) GetSummary(id int) actionresults.ActionResult {
    targetUrl, _ := handler.URLGenerator.GenerateUrl(ProductHandler.GetProducts,
        0, 1)
    return actionresults.NewTemplateAction("checkout_summary.html", struct {
        ID int
        TargetUrl string
    }{ ID: id, TargetUrl: targetUrl})
}
Listing 37-17The Contents of the order_handler.go File in the store Folder
This handler defines three methods. The GetCheckout method will display an HTML form that allows the user to enter their shipping details and will display any validation errors from previous attempts to check out.

The PostCheckout method is the target of the form rendered by the GetCheckout method. This method validates the data supplied by the user, and if there are errors, it redirects the browser back to the GetCheckout method. I use the session to pass data from the PostCheckout method to the GetCheckout method, encoding and decoding the data as JSON so it can be stored in the session cookie.

If there are no validation errors, the PostCheckout method creates an Order, using the shipping details provided by the user and the product details obtained from the Cart, which the handler obtains as a service. The Order is stored using the repository, and the browser is redirected to the GetSummary method, which renders a template that displays a summary.

To create the template for the shipping details, add a file named checkout.html to the sportsstore/templates folder with the content shown in Listing 37-18.
{{ layout "simple_layout.html" }}
{{ $context := .}}
{{ $details := .ShippingDetails }}
<div class="p-2">
    <h2>Check out now</h2>
    Please enter your details, and we'll ship your goods right away!
</div>
{{ if gt (len $context.ValidationErrors) 0}}
    <ul class="text-danger mt-3">
        {{ range $context.ValidationErrors }}
            <li>
                {{ index . 0 }}: {{ index . 1 }}
            </li>
        {{ end }}
    </ul>
{{ end }}
<form method="POST" class="p-2">
    <h3>Ship to</h3>
    <div class="form-group">
        <label class="form-label">Name:</label>
        <input name="name" class="form-control" value="{{ $details.Name }}" />
    </div>
    <div class="form-group">
        <label>Street Address:</label>
        <input name="streetaddr" class="form-control"
            value="{{ $details.StreetAddr }}" />
    </div>
    <div class="form-group">
        <label>City:</label>
        <input name="city" class="form-control" value="{{ $details.City }}" />
    </div>
    <div class="form-group">
        <label>State:</label>
        <input name="state" class="form-control" value="{{ $details.State }}" />
    </div>
    <div class="form-group">
        <label>Zip:</label>
        <input name="zip" class="form-control" value="{{ $details.Zip }}" />
    </div>
    <div class="form-group">
        <label>Country:</label>
        <input name="country" class="form-control" value="{{ $details.Country }}" />
    </div>
    <div class="text-center py-1">
        <a class="btn btn-secondary m-1" href="{{ $context.CancelUrl }}">Cancel</a>
        <button class="btn btn-primary m-1" type="submit">Submit</button>
    </div>
</form>
Listing 37-18The Contents of the checkout.html File in the templates Folder
To create the template that is displayed at the end of the checkout process, add a file named checkout_summary.html to the sportsstore/templates folder with the content shown in Listing 37-19.
{{ layout "simple_layout.html" }}
{{ $context := . }}
<div class="text-center m-3">
    <h2>Thanks!</h2>
    <p>Thanks for placing order #{{ $context.ID }} </p>
    <p>We'll ship your goods as soon as possible.</p>
    <a class="btn btn-primary" href="{{ $context.TargetUrl }}">
        Return to Store
    </a>
</div>
Listing 37-19The Contents of the checkout_summary.html File in the templates Folder
This template includes a link that will return the user to the list of products. The PostCheckout method resets the user’s cart, allowing the user to start the shopping process again.

Integrating the Checkout Process
To allow the user to start the checkout process from the cart summary, make the changes shown in Listing 37-20.
...
func (handler CartHandler) GetCart() actionresults.ActionResult {
    return actionresults.NewTemplateAction("cart.html", CartTemplateContext {
        Cart: handler.Cart,
        ProductListUrl: handler.mustGenerateUrl(ProductHandler.GetProducts, 0, 1),
        RemoveUrl: handler.mustGenerateUrl(CartHandler.PostRemoveFromCart),
        CheckoutUrl: handler.mustGenerateUrl(OrderHandler.GetCheckout),
    })
}
...
Listing 37-20Adding a Context Property in the cart_handler.go File in the store Folder
This change sets the value of the context property to give the template a URL for targeting the checkout handler. Listing 37-21 adds the link that uses the URL.
...
<div class="text-center">
    <a class="btn btn-primary" href="{{ $context.ProductListUrl }}">
        Continue shopping
    </a>
    <a class="btn btn-danger" href="{{ $context.CheckoutUrl }}">Checkout</a>
</div>
...
Listing 37-21Adding an Element in the cart.html File in the templates Folder
Registering the Request Handler
Listing 37-22 registers the request handler so that it can receive requests.
...
func createPipeline() pipeline.RequestPipeline {
    return pipeline.CreatePipeline(
        &basic.ServicesComponent{},
        &basic.LoggingComponent{},
        &basic.ErrorComponent{},
        &basic.StaticFileComponent{},
        &sessions.SessionComponent{},
        handling.NewRouter(
            handling.HandlerEntry{ "",  store.ProductHandler{}},
            handling.HandlerEntry{ "",  store.CategoryHandler{}},
            handling.HandlerEntry{ "", store.CartHandler{}},
            handling.HandlerEntry{ "", store.OrderHandler{}},
        ).AddMethodAlias("/", store.ProductHandler.GetProducts, 0, 1).
            AddMethodAlias("/products[/]?[A-z0-9]*?",
                store.ProductHandler.GetProducts, 0, 1),
    )
}
...
Listing 37-22Registering a New Handler in the main.go File in the sportsstore Folder
Compile and execute the project and use a browser to request http://localhost:5000. Add products to the cart and click the Checkout button, which will present you with the form shown in Figure 37-1.

Figure 37-1The checkout process
Creating Administration Features
The SportsStore application has a basic product listing and checkout process, and now it is time to create administration features. I am going to start with some basic templates and handlers that produce placeholder content.

Create the sportsstore/admin folder and add to it a file named main_handler.go with the content shown in Listing 37-23.
package admin
import (
    "platform/http/actionresults"
    "platform/http/handling"
)
var sectionNames = []string { "Products", "Categories", "Orders", "Database"}
type AdminHandler struct {
    handling.URLGenerator
}
type AdminTemplateContext struct {
    Sections []string
    ActiveSection string
    SectionUrlFunc func(string) string
}
func (handler AdminHandler) GetSection(section string) actionresults.ActionResult {
    return actionresults.NewTemplateAction("admin.html", AdminTemplateContext {
        Sections: sectionNames,
        ActiveSection: section,
        SectionUrlFunc: func(sec string) string {
            sectionUrl, _ := handler.GenerateUrl(AdminHandler.GetSection, sec)
            return sectionUrl
        },
    })
}
Listing 37-23The Contents of the main_handler.go File in the admin Folder
The purpose of this handler is to display a template for the overall administration features, with buttons to move between different sections of functionality. Add a file named admin.html to the sportsstore/templates folder with the content shown in Listing 37-24.
{{ $context := . }}
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>SportsStore</title>
    <link href="/files/bootstrap.min.css" rel="stylesheet" />
</head>
<body>
    <div class="bg-info text-white p-2">
        <div class="container-fluid">
            <div class="row">
                <div class="col navbar-brand">SPORTS STORE Administration</div>
            </div>
        </div>
    </div>
    <div class="row m-1 p-1">
        <div id="sidebar" class="col-3">
            <div class="d-grid gap-2">
                {{ range $context.Sections }}
                    <a href="{{ call $context.SectionUrlFunc . }}"
                        {{ if eq . $context.ActiveSection }}
                            class="btn btn-info">
                        {{ else }}
                            class="btn btn-outline-info">
                        {{ end }}
                        {{ . }}
                    </a>
                {{ end }}
            </div>
        </div>
        <div class="col-9">
            {{ if eq $context.ActiveSection ""}}
                <h6 class="p-2">
                    Welcome to the SportsStore Administration Features
                </h6>
            {{ else }}
                {{ handler $context.ActiveSection "getdata" }}
            {{ end }}
        </div>
    </div>
</body>
</html>
Listing 37-24The Contents of the admin.html File in the templates Folder
This template uses a different color scheme to denote the administration features and displays a two-column layout with section buttons on one side and the selected administration function on the other. The selected feature is displayed using the handler function.

Add a file named products_handler.go to the sportsstore/admin folder with the content shown in Listing 37-25.
package admin
type ProductsHandler struct {}
func (handler ProductsHandler) GetData() string {
    return "This is the products handler"
}
Listing 37-25The Contents of the products_handler.go File in the admin Folder
Add a file named categories_handler.go to the sportsstore/admin folder with the content shown in Listing 37-26.
package admin
type CategoriesHandler struct {}
func (handler CategoriesHandler) GetData() string {
    return "This is the categories handler"
}
Listing 37-26The Contents of the categories_handler.go File in the admin Folder
Add a file named orders_handler.go to the sportsstore/admin folder with the content shown in Listing 37-27.
package admin
type OrdersHandler struct {}
func (handler OrdersHandler) GetData() string {
    return "This is the orders handler"
}
Listing 37-27The Contents of the orders_handler.go File in the admin Folder
To complete the set of handlers, add a file named database_handler.go to the sportsstore/admin folder with the content shown in Listing 37-28.
package admin
type DatabaseHandler struct {}
func (handler DatabaseHandler) GetData() string {
    return "This is the database handler"
}
Listing 37-28The Contents of the database_handler.go File in the admin Folder
I will add access controls for the administration features in Chapter 38, but for now, I am going to register the new handlers so they can be accessed by anyone, as shown in Listing 37-29.
package main
import (
    "sync"
    "platform/http"
    "platform/http/handling"
    "platform/services"
    "platform/pipeline"
    "platform/pipeline/basic"
    "sportsstore/store"
    "sportsstore/models/repo"
    "platform/sessions"
    "sportsstore/store/cart"
    "sportsstore/admin"
)
func registerServices() {
    services.RegisterDefaultServices()
    //repo.RegisterMemoryRepoService()
    repo.RegisterSqlRepositoryService()
    sessions.RegisterSessionService()
    cart.RegisterCartService()
}
func createPipeline() pipeline.RequestPipeline {
    return pipeline.CreatePipeline(
        &basic.ServicesComponent{},
        &basic.LoggingComponent{},
        &basic.ErrorComponent{},
        &basic.StaticFileComponent{},
        &sessions.SessionComponent{},
        handling.NewRouter(
            handling.HandlerEntry{ "",  store.ProductHandler{}},
            handling.HandlerEntry{ "",  store.CategoryHandler{}},
            handling.HandlerEntry{ "", store.CartHandler{}},
            handling.HandlerEntry{ "", store.OrderHandler{}},
            handling.HandlerEntry{ "admin", admin.AdminHandler{}},
            handling.HandlerEntry{ "admin", admin.ProductsHandler{}},
            handling.HandlerEntry{ "admin", admin.CategoriesHandler{}},
            handling.HandlerEntry{ "admin", admin.OrdersHandler{}},
            handling.HandlerEntry{ "admin", admin.DatabaseHandler{}},
            ).AddMethodAlias("/", store.ProductHandler.GetProducts, 0, 1).
AddMethodAlias("/products[/]?[A-z0-9]*?", store.ProductHandler.GetProducts, 0, 1).
                AddMethodAlias("/admin[/]?", admin.AdminHandler.GetSection, ""),
    )
}
func main() {
    registerServices()
    results, err := services.Call(http.Serve, createPipeline())
    if (err == nil) {
        (results[0].(*sync.WaitGroup)).Wait()
    } else {
        panic(err)
    }
}
Listing 37-29Registering the Administration Handlers in the main.go File in the sportsstore Folder
Compile and execute the project and use a browser to request http://localhost:5000/admin, which will produce the response in Figure 37-2. Clicking the navigation buttons in the left column invokes different handlers in the right column.

Figure 37-2Starting work on the administration features
Creating the Product Administration Feature
The product administration feature will allow new products to be added to the store and existing products to be modified. For simplicity, I am not going to allow products to be deleted from the database, which has been created with foreign key relationships between tables.

Extending the Repository
The first step is to extend the repository so that I can make changes to the database. Listing 37-30 adds a new method to the Repository interface.
package models
type Repository interface {
    GetProduct(id int) Product
    GetProducts() []Product
    SaveProduct(*Product)
    GetProductPage(page, pageSize int) (products []Product, totalAvailable int)
    GetProductPageCategory(categoryId int, page, pageSize int) (products []Product,
        totalAvailable int)
    GetCategories() []Category
    GetOrder(id int) Order
    GetOrders() []Order
    SaveOrder(*Order)
    Seed()
}
Listing 37-30Defining a Method in the repository.go File in the models Folder
To define the SQL that will be used to store new products, add a file named save_product.sql to the sportsstore/sql folder with the content shown in Listing 37-31.
INSERT INTO Products(Name, Description, Category, Price)
VALUES (?, ?, ?, ?)
Listing 37-31The Contents of the save_product.sql File in the sql Folder
To define the SQL that will be used to modify existing products, add a file named update_product.sql to the sportsstore/sql folder with the content shown in Listing 37-32.
UPDATE Products
SET Name = ?, Description = ?, Category = ?, Price =?
WHERE Id == ?
Listing 37-32The Contents of the update_product.sql File in the sql Folder
Listing 37-33 adds new commands that will provide access to the SQL files for modifying product data.
package repo
import (
    "database/sql"
    "platform/config"
    "platform/logging"
    "context"
)
type SqlRepository struct {
    config.Configuration
    logging.Logger
    Commands SqlCommands
    *sql.DB
    context.Context
}
type SqlCommands struct {
    Init,
    Seed,
    GetProduct,
    GetProducts,
    GetCategories,
    GetPage,
    GetPageCount,
    GetCategoryPage,
    GetCategoryPageCount,
    GetOrder,
    GetOrderLines,
    GetOrders,
    GetOrdersLines,
    SaveOrder,
    SaveOrderLine,
    SaveProduct,
    UpdateProduct *sql.Stmt
}
Listing 37-33Adding Commands in the sql_repo.go File in the models/repo Folder
Listing 37-34 adds the configuration settings that specify the location of the SQL files for the new commands.
...
"sql": {
    "connection_str": "store.db",
    "always_reset": true,
    "commands": {
        "Init":                 "sql/init_db.sql",
        "Seed":                 "sql/seed_db.sql",
        "GetProduct":           "sql/get_product.sql",
        "GetProducts":          "sql/get_products.sql",
        "GetCategories":        "sql/get_categories.sql",
        "GetPage":              "sql/get_product_page.sql",
        "GetPageCount":         "sql/get_page_count.sql",
        "GetCategoryPage":      "sql/get_category_product_page.sql",
        "GetCategoryPageCount": "sql/get_category_product_page_count.sql",
        "GetOrder":             "sql/get_order.sql",
        "GetOrderLines":        "sql/get_order_lines.sql",
        "GetOrders":            "sql/get_orders.sql",
        "GetOrdersLines":       "sql/get_orders_lines.sql",
        "SaveOrder":            "sql/save_order.sql",
        "SaveOrderLine":        "sql/save_order_line.sql",
        "SaveProduct":          "sql/save_product.sql",
        "UpdateProduct":        "sql/update_product.sql"
    }
}
...
Listing 37-34Adding Configuration Settings in the config.json File in the sportsstore Folder
To use the SQL commands to implement the repository method, add a file named sql_products_save.go to the sportsstore/models/repo folder with the content shown in Listing 37-35.
package repo
import "sportsstore/models"
func (repo *SqlRepository) SaveProduct(p *models.Product) {
    if (p.ID == 0) {
        result, err := repo.Commands.SaveProduct.ExecContext(repo.Context, p.Name,
            p.Description, p.Category.ID, p.Price)
        if err == nil {
            id, err := result.LastInsertId()
            if err == nil {
                p.ID = int(id)
                return
            } else {
                repo.Logger.Panicf("Cannot get inserted ID: %v", err.Error())
            }
        } else {
            repo.Logger.Panicf("Cannot exec SaveProduct command: %v", err.Error())
        }
    } else {
        result, err := repo.Commands.UpdateProduct.ExecContext(repo.Context, p.Name,
            p.Description, p.Category.ID, p.Price, p.ID)
        if err == nil {
            affected, err := result.RowsAffected()
            if err == nil && affected != 1 {
                repo.Logger.Panicf("Got unexpected rows affected: %v", affected)
            } else if err != nil {
                repo.Logger.Panicf("Cannot get rows affected: %v", err)
            }
        } else {
            repo.Logger.Panicf("Cannot exec Update command: %v", err.Error())
        }
    }
}
Listing 37-35The Contents of the sql_products_save.go File in the models/repo Folder
If the ID property of the Product received by this method is zero, then the data is added to the database; otherwise, an update is performed.

Implementing the Products Request Handler
The next step is to remove the placeholder response from the request handler and add the real functionality that will allow the administrator to see and edit the Product data. Replace the contents of the products_handler.go file in the sportsstore/admin folder with the content shown in Listing 37-36. (Make sure you edit the file in the admin folder and not the one in the store folder with a similar name.)
package admin
import (
    "sportsstore/models"
    "platform/http/actionresults"
    "platform/http/handling"
    "platform/sessions"
)
type ProductsHandler struct {
    models.Repository
    handling.URLGenerator
    sessions.Session
}
type ProductTemplateContext struct {
    Products []models.Product
    EditId int
    EditUrl string
    SaveUrl string
}
const PRODUCT_EDIT_KEY string = "product_edit"
func (handler ProductsHandler) GetData() actionresults.ActionResult {
    return actionresults.NewTemplateAction("admin_products.html",
            ProductTemplateContext {
        Products: handler.GetProducts(),
        EditId: handler.Session.GetValueDefault(PRODUCT_EDIT_KEY, 0).(int),
        EditUrl: mustGenerateUrl(handler.URLGenerator,
             ProductsHandler.PostProductEdit),
        SaveUrl: mustGenerateUrl(handler.URLGenerator,
             ProductsHandler.PostProductSave),
    })
}
type EditReference struct {
    ID int
}
func (handler ProductsHandler) PostProductEdit(ref EditReference) actionresults.ActionResult {
    handler.Session.SetValue(PRODUCT_EDIT_KEY, ref.ID)
    return actionresults.NewRedirectAction(mustGenerateUrl(handler.URLGenerator,
         AdminHandler.GetSection, "Products"))
}
type ProductSaveReference struct {
    Id int
    Name, Description string
    Category int
    Price float64
}
func (handler ProductsHandler) PostProductSave(
        p ProductSaveReference) actionresults.ActionResult {
    handler.Repository.SaveProduct(&models.Product{
        ID: p.Id, Name: p.Name, Description: p.Description,
        Category: &models.Category{ ID: p.Category },
        Price: p.Price,
    })
    handler.Session.SetValue(PRODUCT_EDIT_KEY, 0)
    return actionresults.NewRedirectAction(mustGenerateUrl(handler.URLGenerator,
        AdminHandler.GetSection, "Products"))
}
func mustGenerateUrl(gen handling.URLGenerator, target interface{},
        data ...interface{}) string {
    url, err := gen.GenerateUrl(target, data...)
    if (err != nil) {
        panic(err)
    }
    return url
}
Listing 37-36Adding Features in the products_handler.go File in the admin Folder
The GetData method renders a template named admin_products.html with context data that contains the Product values in the database, an int value used to denote the ID of the Product the user wants to edit, and URLs that are used for navigation. To create the template, add a file named admin_products.html to the sportsstore/templates folder with the content shown in Listing 37-37.
{{ $context := . }}
<table class="table table-sm table-striped table-bordered">
    <thead>
        <tr>
            <th>ID</th><th>Name</th><th>Description</th>
            <th>Category</th><th class="text-end">Price</th><th></th>
        </tr>
    </thead>
    <tbody>
        {{ range $context.Products }}
            {{ if ne $context.EditId .ID}}
                <tr>
                    <td>{{ .ID }}</td>
                    <td>{{ .Name }}</td>
                    <td>
                        <span class="d-inline-block text-truncate"
                            style="max-width: 200px;">
                               {{ .Description }}
                        </span>
                    </td>
                    <td>{{ .CategoryName }}</td>
                    <td class="text-end">{{ printf "$%.2f" .Price }}</td>
                    <td class="text-center">
                        <form method="POST" action="{{ $context.EditUrl }}">
                            <input type="hidden" name="id" value="{{ .ID }}" />
                            <button class="btn btn-sm btn-warning" type="submit">
                                Edit
                            </button>
                        </form>
                    </td>
                </tr>
            {{ else }}
                <tr>
                    <form method="POST" action="{{ $context.SaveUrl }}" >
                        <input type="hidden" name="id" value="{{ .ID }}" />
                        <td>
                            <input class="form-control" disabled value="{{.ID}}"
                                size="3"/>
                        </td>
                        <td><input name="name" class="form-control" size=12
                            value="{{ .Name }}" /></td>
                        <td><input name="description" class="form-control"
                             size=15 value="{{ .Description }}" /></td>
                        <td>{{ handler "categories" "getselect" .Category.ID }}</td>
                        <td><input name="price" class="form-control text-end"
                            size=7 value="{{ .Price }}"/></td>
                        <td>
                            <button class="btn btn-sm btn-danger" type="submit">
                                Save
                            </button>
                        </td>
                    </form>
                </tr>
            {{ end }}
        {{ end }}
    </tbody>
    {{ if eq $context.EditId 0}}
        <tfoot>
            <tr><td colspan="6" class="text-center">Add New Product</td></tr>
            <tr>
                <form method="POST" action="{{ $context.SaveUrl }}" >
                    <td>-</td>
                    <td><input name="name" class="form-control" size=12 /></td>
                    <td><input name="description" class="form-control"
                        size=15 /></td>
                    <td>{{ handler "categories" "getselect" 0 }}</td>
                    <td><input name="price" class="form-control" size=7 /></td>
                    <td>
                        <button class="btn btn-sm btn-danger" type="submit">
                            Save
                        </button>
                    </td>
                </form>
            </tr>
        </tfoot>
    {{ end }}
</table>
Listing 37-37The Contents of the admin_products.html File in the templates Folder
This template produces an HTML template that contains all of the products, along with an inline editor for modifying existing products and another for creating new products. Both tasks require a select element that allows the user to choose a category, which is generated by invoking a method defined by the CategoriesHandler. Listing 37-38 adds this method to the request handler.
package admin
import (
    "platform/http/actionresults"
    "sportsstore/models"
)
type CategoriesHandler struct {
    models.Repository
}
func (handler CategoriesHandler) GetData() string {
    return "This is the categories handler"
}
func (handler CategoriesHandler) GetSelect(current int) actionresults.ActionResult {
    return actionresults.NewTemplateAction("select_category.html", struct {
        Current int
        Categories []models.Category
    }{ Current: current, Categories: handler.GetCategories()})
}
Listing 37-38Adding Support for a Select Element in the categories_handler.go File in the admin Folder
To define the template used by the GetSelect method, add a file named select_category.html to the sportsstore/templates folder with the content shown in Listing 37-39.
{{ $context := . }}
<select class="form-select" name="category" value="{{ $context.Current }}">
    <option value="0">Select a category</option>
    {{ range $context.Categories }}
        <option value="{{.ID}}" {{ if eq $context.Current .ID }}selected{{end}}>
            {{.CategoryName}}
        </option>
    {{ end }}
</select>
Listing 37-39The Contents of the select_category.html File in the templates Folder
Compile and execute the project, use a browser to request http://localhost:5000/admin, and click the Products button. You will see the list of products, which has been read from the database. Click one of the Edit buttons to select a product for editing, enter new values into the form fields, and click the Submit button to save the changes to the database, also shown in Figure 37-3.

Figure 37-3Editing a product
NoteThe SportsStore application is configured to reset the database each time it is started, which means that any changes you make to the database will be discarded. I disable this feature when preparing the application for deployment in Chapter 38.
When no product is selected for editing, a form at the bottom of the table can be used to create new products in the database, as shown in Figure 37-4.

Figure 37-4Adding a product
Creating the Categories Administration Feature
I am going to apply the basic pattern established in the previous section to implement the other administration features.

Extending the Repository
Listing 37-40 adds a method to the Repository interface that will store a Category.
package models
type Repository interface {
    GetProduct(id int) Product
    GetProducts() []Product
    SaveProduct(*Product)
    GetProductPage(page, pageSize int) (products []Product, totalAvailable int)
    GetProductPageCategory(categoryId int, page, pageSize int) (products []Product,
        totalAvailable int)
    GetCategories() []Category
    SaveCategory(*Category)
    GetOrder(id int) Order
    GetOrders() []Order
    SaveOrder(*Order)
    Seed()
}
Listing 37-40Adding a Method in the repository.go File in the models Folder
To define the SQL that will be used to store new categories in the database, add a file named save_category.sql to the sportsstore/sql folder with the content shown in Listing 37-41.
INSERT INTO Categories(Name) VALUES (?)
Listing 37-41The Contents of the save_category.sql File in the sql Folder
To define the SQL that will be used to modify existing categories, add a file named update_category.sql to the sportsstore/sql folder with the content shown in Listing 37-42.
UPDATE Categories SET Name = ? WHERE Id == ?
Listing 37-42The Contents of the update_category.sql File in the sql Folder
Listing 37-43 adds new commands that will provide access to the SQL files.
...
type SqlCommands struct {
    Init,
    Seed,
    GetProduct,
    GetProducts,
    GetCategories,
    GetPage,
    GetPageCount,
    GetCategoryPage,
    GetCategoryPageCount,
    GetOrder,
    GetOrderLines,
    GetOrders,
    GetOrdersLines,
    SaveOrder,
    SaveOrderLine,
    SaveProduct,
    UpdateProduct,
    SaveCategory,
    UpdateCategory *sql.Stmt
}
...
Listing 37-43Adding Commands in the sql_repo.go File in the models/repo Folder
Listing 37-44 adds the configuration settings that specify the location of the SQL files for the new commands.
...
"sql": {
    "connection_str": "store.db",
    "always_reset": true,
    "commands": {
        "Init":                 "sql/init_db.sql",
        "Seed":                 "sql/seed_db.sql",
        "GetProduct":           "sql/get_product.sql",
        "GetProducts":          "sql/get_products.sql",
        "GetCategories":        "sql/get_categories.sql",
        "GetPage":              "sql/get_product_page.sql",
        "GetPageCount":         "sql/get_page_count.sql",
        "GetCategoryPage":      "sql/get_category_product_page.sql",
        "GetCategoryPageCount": "sql/get_category_product_page_count.sql",
        "GetOrder":             "sql/get_order.sql",
        "GetOrderLines":        "sql/get_order_lines.sql",
        "GetOrders":            "sql/get_orders.sql",
        "GetOrdersLines":       "sql/get_orders_lines.sql",
        "SaveOrder":            "sql/save_order.sql",
        "SaveOrderLine":        "sql/save_order_line.sql",
        "SaveProduct":          "sql/save_product.sql",
        "UpdateProduct":        "sql/update_product.sql",
        "SaveCategory":         "sql/save_category.sql",
        "UpdateCategory":       "sql/update_category.sql"
    }
}
...
Listing 37-44Adding Configuration Settings in the config.json File in the sportsstore Folder
To implement the new interface method, add a file named sql_category_save.go to the sportsstore/models/repo folder with the content shown in Listing 37-45.
package repo
import "sportsstore/models"
func (repo *SqlRepository) SaveCategory(c *models.Category) {
    if (c.ID == 0) {
        result, err := repo.Commands.SaveCategory.ExecContext(repo.Context,
            c.CategoryName)
        if err == nil {
            id, err := result.LastInsertId()
            if err == nil {
                c.ID = int(id)
                return
            } else {
                repo.Logger.Panicf("Cannot get inserted ID: %v", err.Error())
            }
        } else {
            repo.Logger.Panicf("Cannot exec SaveCategory command: %v", err.Error())
        }
    } else {
        result, err := repo.Commands.UpdateCategory.ExecContext(repo.Context,
            c.CategoryName, c.ID)
        if err == nil {
            affected, err := result.RowsAffected()
            if err == nil && affected != 1 {
                repo.Logger.Panicf("Got unexpected rows affected: %v", affected)
            } else if err != nil {
                repo.Logger.Panicf("Cannot get rows affected: %v", err)
            }
        } else {
            repo.Logger.Panicf("Cannot exec UpdateCategory command: %v", err.Error())
        }
    }
}
Listing 37-45The Contents of the sql_category_save.go File in the models/repo Folder
If the ID property of the Category received by this method is zero, then the data is added to the database; otherwise, an update is performed.

Implementing the Category Request Handler
Replace the contents of the categories_handler.go file in the sportsstore/admin folder with the code shown in Listing 37-46.
package admin
import (
    "sportsstore/models"
    "platform/http/actionresults"
    "platform/http/handling"
    "platform/sessions"
)
type CategoriesHandler struct {
    models.Repository
    handling.URLGenerator
    sessions.Session
}
type CategoryTemplateContext struct {
    Categories []models.Category
    EditId int
    EditUrl string
    SaveUrl string
}
const CATEGORY_EDIT_KEY string = "category_edit"
func (handler CategoriesHandler) GetData() actionresults.ActionResult {
    return actionresults.NewTemplateAction("admin_categories.html",
        CategoryTemplateContext {
            Categories: handler.Repository.GetCategories(),
            EditId: handler.Session.GetValueDefault(CATEGORY_EDIT_KEY, 0).(int),
            EditUrl: mustGenerateUrl(handler.URLGenerator,
                 CategoriesHandler.PostCategoryEdit),
            SaveUrl: mustGenerateUrl(handler.URLGenerator,
                 CategoriesHandler.PostCategorySave),
        })
}
func (handler CategoriesHandler) PostCategoryEdit(ref EditReference) actionresults.ActionResult {
    handler.Session.SetValue(CATEGORY_EDIT_KEY, ref.ID)
    return actionresults.NewRedirectAction(mustGenerateUrl(handler.URLGenerator,
         AdminHandler.GetSection, "Categories"))
}
func (handler CategoriesHandler) PostCategorySave(
        c models.Category) actionresults.ActionResult {
    handler.Repository.SaveCategory(&c)
    handler.Session.SetValue(CATEGORY_EDIT_KEY, 0)
    return actionresults.NewRedirectAction(mustGenerateUrl(handler.URLGenerator,
        AdminHandler.GetSection, "Categories"))
}
func (handler CategoriesHandler) GetSelect(current int) actionresults.ActionResult {
    return actionresults.NewTemplateAction("select_category.html", struct {
        Current int
        Categories []models.Category
    }{ Current: current, Categories: handler.GetCategories()})
}
Listing 37-46Replacing the Contents of the categories_handler.go File in the admin Folder
To define the template used by this handler, add a file named admin_categories.html to the sportsstore/templates folder with the content shown in Listing 37-47.
{{ $context := . }}
<table class="table table-sm table-striped table-bordered">
    <thead><tr><th>ID</th><th>Name</th><th></th></tr></thead>
    <tbody>
        {{ range $context.Categories }}
            {{ if ne $context.EditId .ID}}
                <tr>
                    <td>{{ .ID }}</td>
                    <td>{{ .CategoryName }}</td>
                    <td class="text-center">
                        <form method="POST" action="{{ $context.EditUrl }}">
                            <input type="hidden" name="id" value="{{ .ID }}" />
                            <button class="btn btn-sm btn-warning" type="submit">
                                Edit
                            </button>
                        </form>
                    </td>
                </tr>
            {{ else }}
                <tr>
                    <form method="POST" action="{{ $context.SaveUrl }}" >
                        <input type="hidden" name="id" value="{{ .ID }}" />
                        <td>
                            <input class="form-control" disabled
                                value="{{.ID}}" size="3"/>
                        </td>
                        <td><input name="categoryname" class="form-control" size=12
                            value="{{ .CategoryName }}" /></td>
                    <td class="text-center">
                            <button class="btn btn-sm btn-danger" type="submit">
                                Save
                            </button>
                        </td>
                    </form>
                </tr>
            {{end }}
        {{ end }}
    </tbody>
    {{ if eq $context.EditId 0}}
        <tfoot>
            <tr><td colspan="6" class="text-center">Add New Category</td></tr>
            <tr>
                <form method="POST" action="{{ $context.SaveUrl }}" >
                    <td>-</td>
                    <td><input name="categoryname" class="form-control"
                        size=12 /></td>
                    <td class="text-center">
                        <button class="btn btn-sm btn-danger" type="submit">
                            Save
                        </button>
                    </td>
                </form>
            </tr>
        </tfoot>
    {{ end }}
</table>
Listing 37-47The Contents of the admin_categories.html File in the templates Folder
Compile and execute the project, use a browser to request http://localhost:5000/admin, and click the Categories button. You will see the list of categories, which has been read from the database, and can edit and create categories, as shown in Figure 37-5.

Figure 37-5Managing categories
Summary
In this chapter, I continued the development of the SportsStore application by adding a checkout process and starting work on the administration features. In the next chapter, I complete those features, add support for access control, and prepare the application for deployment.


Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


37. SportsStore: Checkout and Administration
38. SportsStore: Finishing and Deployment
Back Matter
21h 44m remaining
© The Author(s), under exclusive license to APress Media, LLC, part of Springer Nature 2022
A. FreemanPro Go
https://doi.org/10.1007/978-1-4842-7355-5_38
38. SportsStore: Finishing and Deployment
Adam Freeman1  
(1)
London, UK
 
In this chapter, I complete the development of the SportsStore application and prepare it for deployment.

TipYou can download the example project for this chapter—and for all the other chapters in this book—from https://github.com/apress/pro-go. See Chapter 2 for how to get help if you have problems running the examples.
Completing the Administration Features
Two of the four administration sections defined in Chapter 37 are not yet implemented. I define both of these features at the same time in this section, reflecting the fact that they are simpler than the product and category features.

Extending the Repository
Two new repository methods are required to complete the administration features, as shown in Listing 38-1.
package models
type Repository interface {
    GetProduct(id int) Product
    GetProducts() []Product
    SaveProduct(*Product)
    GetProductPage(page, pageSize int) (products []Product, totalAvailable int)
    GetProductPageCategory(categoryId int, page, pageSize int) (products []Product,
        totalAvailable int)
    GetCategories() []Category
    SaveCategory(*Category)
    GetOrder(id int) []Order
    GetOrders() Order
    SaveOrder(*Order)
    SetOrderShipped(*Order)
    Seed()
    Init()
}
Listing 38-1Adding an Interface in the repository.go File in the models Folder
The SetOrderShipped method will be used to update an existing Order to indicate when it has been shipped. The Init method corresponds to a method name already defined by the SQL implementation of the interface and will be used to allow the administrator to prepare the database for first use after it has been deployed.

To define the SQL that will be used to update existing orders, add a file named update_order.sql to the sportsstore/sql folder with the content shown in Listing 38-2.
UPDATE Orders SET Shipped = ? WHERE Id == ?
Listing 38-2The Contents of the update_order.sql File in the sql Folder
Listing 38-3 adds a new command so that the SQL defined in Listing 38-2 can be accessed in the same way as the other SQL statements.
...
type SqlCommands struct {
    Init,
    Seed,
    GetProduct,
    GetProducts,
    GetCategories,
    GetPage,
    GetPageCount,
    GetCategoryPage,
    GetCategoryPageCount,
    GetOrder,
    GetOrderLines,
    GetOrders,
    GetOrdersLines,
    SaveOrder,
    SaveOrderLine,
    UpdateOrder,
    SaveProduct,
    UpdateProduct,
    SaveCategory,
    UpdateCategory *sql.Stmt
}
...
Listing 38-3Adding a New Command in the sql_repo.go File in the models/repo Folder
Listing 38-4 adds a configuration setting that specifies the location of the SQL required for the new command.
...
"sql": {
    "connection_str": "store.db",
    "always_reset": true,
    "commands": {
        "Init": "sql/init_db.sql",
        "Seed": "sql/seed_db.sql",
        "GetProduct": "sql/get_product.sql",
        "GetProducts": "sql/get_products.sql",
        "GetCategories": "sql/get_categories.sql",
        "GetPage": "sql/get_product_page.sql",
        "GetPageCount": "sql/get_page_count.sql",
        "GetCategoryPage": "sql/get_category_product_page.sql",
        "GetCategoryPageCount": "sql/get_category_product_page_count.sql",
        "GetOrder": "sql/get_order.sql",
        "GetOrderLines": "sql/get_order_lines.sql",
        "GetOrders": "sql/get_orders.sql",
        "GetOrdersLines": "sql/get_orders_lines.sql",
        "SaveOrder": "sql/save_order.sql",
        "SaveOrderLine": "sql/save_order_line.sql",
        "SaveProduct":          "sql/save_product.sql",
        "UpdateProduct":        "sql/update_product.sql",
        "SaveCategory":         "sql/save_category.sql",
        "UpdateCategory":       "sql/update_category.sql",
        "UpdateOrder":          "sql/update_order.sql"
    }
}
...
Listing 38-4Adding a Configuration Setting in the config.json File in the sportsstore Folder
To implement the repository method, add a file named sql_order_update.go in the sportsstore/models/repo folder with the content shown in Listing 38-5.
package repo
import "sportsstore/models"
func (repo *SqlRepository) SetOrderShipped(o *models.Order) {
    result, err := repo.Commands.UpdateOrder.ExecContext(repo.Context,
        o.Shipped, o.ID)
    if err == nil {
        rows, err :=result.RowsAffected()
        if err != nil {
            repo.Logger.Panicf("Cannot get updated ID: %v", err.Error())
        } else if rows != 1 {
            repo.Logger.Panicf("Got unexpected rows affected: %v", rows)
        }
    } else {
        repo.Logger.Panicf("Cannot exec UpdateOrder command: %v", err.Error())
    }
}
Listing 38-5The Contents of the sql_order_update.go File in the models/repo Folder
Implementing the Request Handlers
To add support for managing orders, replace the content of the orders_handler.go file in the sportsstore/admin folder with the content shown in Listing 38-6.
package admin
import (
    "platform/http/actionresults"
    "platform/http/handling"
    "sportsstore/models"
)
type OrdersHandler struct {
    models.Repository
    handling.URLGenerator
}
func (handler OrdersHandler) GetData() actionresults.ActionResult {
    return actionresults.NewTemplateAction("admin_orders.html", struct {
        Orders []models.Order
         CallbackUrl string
    }{
        Orders: handler.Repository.GetOrders(),
        CallbackUrl: mustGenerateUrl(handler.URLGenerator,
            OrdersHandler.PostOrderToggle),
    })
}
func (handler OrdersHandler) PostOrderToggle(ref EditReference) actionresults.ActionResult {
    order := handler.Repository.GetOrder(ref.ID)
    order.Shipped = !order.Shipped
    handler.Repository.SetOrderShipped(&order)
    return actionresults.NewRedirectAction(mustGenerateUrl(handler.URLGenerator,
        AdminHandler.GetSection, "Orders"))
}
Listing 38-6The New Contents of the orders_handler.go File in the admin Folder
The only change that will be allowed on orders is to change the value of the Shipped field, indicating that the order has been dispatched. Replace the content of the database_handler.go file with the content shown in Listing 38-7.
package admin
import (
    "platform/http/actionresults"
    "platform/http/handling"
    "sportsstore/models"
)
type DatabaseHandler struct {
    models.Repository
    handling.URLGenerator
}
func (handler DatabaseHandler) GetData() actionresults.ActionResult {
    return actionresults.NewTemplateAction("admin_database.html", struct {
        InitUrl, SeedUrl string
    }{
        InitUrl: mustGenerateUrl(handler.URLGenerator,
            DatabaseHandler.PostDatabaseInit),
        SeedUrl: mustGenerateUrl(handler.URLGenerator,
           DatabaseHandler.PostDatabaseSeed),
    })
}
func (handler DatabaseHandler) PostDatabaseInit() actionresults.ActionResult {
    handler.Repository.Init()
    return actionresults.NewRedirectAction(mustGenerateUrl(handler.URLGenerator,
        AdminHandler.GetSection, "Database"))
}
func (handler DatabaseHandler) PostDatabaseSeed() actionresults.ActionResult {
    handler.Repository.Seed()
    return actionresults.NewRedirectAction(mustGenerateUrl(handler.URLGenerator,
        AdminHandler.GetSection, "Database"))
}
Listing 38-7The New Contents of the database_handler.go File in the admin Folder
There are handler methods for each of the operations that can be performed on the database, which will allow the administrator to jump-start the application after the application has been prepared for deployment later in this chapter.

Creating the Templates
To create the template used to manage orders, add a file named admin_orders.html to the sportsstore/templates folder with the content shown in Listing 38-8.
{{ $context := .}}
<table class="table table-sm table-striped table-bordered">
    <tr><th>ID</th><th>Name</th><th>Address</th><th/></tr>
    <tbody>
        {{ range $context.Orders }}
            <tr>
                <td>{{ .ID }}</td>
                <td>{{ .Name }}</td>
                <td>{{ .StreetAddr }}, {{ .City }}, {{ .State }},
                     {{ .Country }}, {{ .Zip }}</td>
                <td>
                    <form method="POST" action="{{$context.CallbackUrl}}">
                        <input type="hidden" name="id" value="{{.ID}}" />
                        {{ if .Shipped }}
                            <button class="btn-btn-sm btn-warning" type="submit">
                                Ship Order
                            </button>
                        {{ else }}
                            <button class="btn-btn-sm btn-danger" type="submit">
                                Mark Unshipped
                            </button>
                        {{ end }}
                    </form>
                </td>
            </tr>
            <tr><th colspan="2"/><th>Quantity</th><th>Product</th></tr>
            {{ range .Products }}
                <tr>
                    <td colspan="2"/>
                    <td>{{ .Quantity }}</td>
                    <td>{{ .Product.Name }}</td>
                </tr>
            {{ end }}
        {{ end }}
    </tbody>
</table>
Listing 38-8The Contents of the admin_orders.html File in the templates Folder
The template displays the orders in a table, along with details of the products that each contains. To create the template used to manage the database, add a file named admin_database.html to the sportsstore/templates folder with the content shown in Listing 38-9.
{{ $context := . }}
<form method="POST">
    <button class="btn btn-danger m-3 p-2" type="submit"
            formaction="{{ $context.InitUrl}}">
        Initialize Database
    </button>
    <button class="btn btn-warning m-3 p-2" type="submit"
            formaction="{{ $context.SeedUrl}}">
        Seed Database
    </button>
</form>
Listing 38-9The Contents of the admin_database.html File in the templates Folder
Compile and execute the project, use a browser to request http://localhost:5000/admin, and click the Orders button to see the orders in the database and change their shipping status, as shown in Figure 38-1. Click the Database button, and you will be able to reset and seed the database, also shown in Figure 38-1.

Figure 38-1Completing the administration features
Restricting Access to the Administration Features
Granting open access to the administration features simplifies development but should never be allowed in production. Now that the administration features are complete, it is time to make sure they are available only to authorized users.

Creating the User Store and Request Handler
As I explained previously, I do not implement a real authentication system, which is difficult to do securely and is beyond the scope of this book. Instead, I am going to follow a similar approach to the one I took with the platform project and rely on hardwired credentials to authenticate a user. Create the sportsstore/admin/auth folder and add to it a file named user_store.go with the content shown in Listing 38-10.
package auth
import (
    "platform/services"
    "platform/authorization/identity"
    "strings"
)
func RegisterUserStoreService() {
    err := services.AddSingleton(func () identity.UserStore {
        return &userStore{}
    })
    if (err != nil) {
        panic(err)
    }
}
var users = map[int]identity.User {
    1: identity.NewBasicUser(1, "Alice", "Administrator"),
}
type userStore struct {}
func (store *userStore) GetUserByID(id int) (identity.User, bool) {
    user, found := users[id]
    return user, found
}
func (store *userStore) GetUserByName(name string) (identity.User, bool) {
    for _, user := range users {
        if strings.EqualFold(user.GetDisplayName(), name) {
            return user, true
        }
    }
    return nil, false
}
Listing 38-10The Contents of the user_store.go File in the admin/auth Folder
To create the handler for authentication requests, add a file named auth_handler.go to the sportsstore/admin folder with the content shown in Listing 38-11.
package admin
import (
    "platform/authorization/identity"
    "platform/http/actionresults"
    "platform/http/handling"
    "platform/sessions"
)
type AuthenticationHandler struct {
    identity.User
    identity.SignInManager
    identity.UserStore
    sessions.Session
    handling.URLGenerator
}
const SIGNIN_MSG_KEY string = "signin_message"
func (handler AuthenticationHandler) GetSignIn() actionresults.ActionResult {
    message := handler.Session.GetValueDefault(SIGNIN_MSG_KEY, "").(string)
    return actionresults.NewTemplateAction("signin.html", message)
}
type Credentials struct {
    Username string
    Password string
}
func (handler AuthenticationHandler) PostSignIn(creds Credentials) actionresults.ActionResult {
    if creds.Password == "mysecret" {
        user, ok := handler.UserStore.GetUserByName(creds.Username)
        if (ok) {
            handler.Session.SetValue(SIGNIN_MSG_KEY, "")
            handler.SignInManager.SignIn(user)
            return actionresults.NewRedirectAction("/admin/section/")
        }
    }
    handler.Session.SetValue(SIGNIN_MSG_KEY, "Access Denied")
    return actionresults.NewRedirectAction(mustGenerateUrl(handler.URLGenerator,
        AuthenticationHandler.GetSignIn))
}
func (handler AuthenticationHandler) PostSignOut(creds Credentials) actionresults.ActionResult {
        handler.SignInManager.SignOut(handler.User)
    return actionresults.NewRedirectAction("/")
}
Listing 38-11The Contents of the auth_handler.go File in the admin Folder
The GetSignIn method renders a template that will prompt the user for their credentials and displays a message that is stored in the session. The PostSignIn method receives the credentials from the form and either signs the user into the application or adds a message to the session and redirects the browser so the user can try again.

To create the template to let users sign into the application, add a file named signin.html to the sportsstore/templates folder with the content shown in Listing 38-12.
{{ layout "simple_layout.html" }}
{{ if ne . "" }}
    <h3 class="text-danger p-2">{{ . }}</h3>
{{ end }}
<form method="POST" class="m-2">
    <div class="form-group">
        <label>Username:</label>
        <input class="form-control"  name="username" />
    </div>
    <div class="form-group">
        <label>Password:</label>
        <input class="form-control" name="password" type="password" />
    </div>
    <div class="my-2">
        <button class="btn btn-secondary" type="submit">Sign In</button>
    </div>
</form>
Listing 38-12The Contents of the signin.html File in the templates Folder
This template prompts the user for their account name and password, which is posted back to the request handler.

To allow the user to sign out of the application, add a file named signout_handler.go to the sportsstore/admin folder with the content shown in Listing 38-13.
package admin
import (
          "platform/authorization/identity"
          "platform/http/actionresults"
    "platform/http/handling"
)
type SignOutHandler struct {
    identity.User
    handling.URLGenerator
}
func (handler SignOutHandler) GetUserWidget() actionresults.ActionResult {
        return actionresults.NewTemplateAction("user_widget.html", struct {
            identity.User
            SignoutUrl string}{
                handler.User,
                mustGenerateUrl(handler.URLGenerator,
                    AuthenticationHandler.PostSignOut),
            })
    }
Listing 38-13The Contents of the signout_handler.go File in the admin Folder
To create the template that will let the user sign out, add a file named user_widget.html to the sportsstore/templates folder with the content shown in Listing 38-14.
{{ $context := . }}
{{ if $context.User.IsAuthenticated }}
    <form method="POST" action="{{$context.SignoutUrl}}">
        <button class="btn btn-sm btn-outline-secondary text-white" type="submit">
            Sign Out
        </button>
    </form>
{{ end }}
Listing 38-14The Contents of the user_widget.html File in the templates Folder
Listing 38-15 adds the user widget to the layout used for the administration features.
...
<div class="bg-info text-white p-2">
    <div class="container-fluid">
        <div class="row">
            <div class="col navbar-brand">SPORTS STORE Administration</div>
            <div class="col-6 navbar-text text-end">
                {{ handler "signout" "getuserwidget" }}
            </div>
        </div>
    </div>
</div>
...
Listing 38-15Adding a Widget in the admin.html File in the templates Folder
Configuring the Application
Listing 38-16 adds a configuration setting that specifies a URL that will be used when a request is made for a restricted URL, which provides a more useful alternative to returning a status code.
{
    "logging" : {
        "level": "debug"
    },
    "files": {
        "path": "files"
    },
    "templates": {
        "path": "templates/*.html",
        "reload": true
    },
    "sessions": {
        "key": "MY_SESSION_KEY",
        "cyclekey": true
    },
    "sql": {
         // ...setting omitted for brevity...
    },
    "authorization": {
        "failUrl": "/signin"
    }
}
Listing 38-16Adding a Configuration Setting in the config.json File in the sportsstore Folder
The specified URL will prompt the user for their credentials. Listing 38-17 reconfigures the request pipeline so the administration features are protected.
package main
import (
    "sync"
    "platform/http"
    "platform/http/handling"
    "platform/services"
    "platform/pipeline"
    "platform/pipeline/basic"
    "sportsstore/store"
    "sportsstore/models/repo"
    "platform/sessions"
    "sportsstore/store/cart"
    "sportsstore/admin"
    "platform/authorization"
    "sportsstore/admin/auth"
)
func registerServices() {
    services.RegisterDefaultServices()
    //repo.RegisterMemoryRepoService()
    repo.RegisterSqlRepositoryService()
    sessions.RegisterSessionService()
    cart.RegisterCartService()
    authorization.RegisterDefaultSignInService()
    authorization.RegisterDefaultUserService()
    auth.RegisterUserStoreService()
}
func createPipeline() pipeline.RequestPipeline {
    return pipeline.CreatePipeline(
        &basic.ServicesComponent{},
        &basic.LoggingComponent{},
        &basic.ErrorComponent{},
        &basic.StaticFileComponent{},
        &sessions.SessionComponent{},
        authorization.NewAuthComponent(
            "admin",
            authorization.NewRoleCondition("Administrator"),
            admin.AdminHandler{},
            admin.ProductsHandler{},
            admin.CategoriesHandler{},
            admin.OrdersHandler{},
            admin.DatabaseHandler{},
            admin.SignOutHandler{},
        ).AddFallback("/admin/section/", "^/admin[/]?$"),
        handling.NewRouter(
            handling.HandlerEntry{ "",  store.ProductHandler{}},
            handling.HandlerEntry{ "",  store.CategoryHandler{}},
            handling.HandlerEntry{ "", store.CartHandler{}},
            handling.HandlerEntry{ "", store.OrderHandler{}},
            // handling.HandlerEntry{ "admin", admin.AdminHandler{}},
            // handling.HandlerEntry{ "admin", admin.ProductsHandler{}},
            // handling.HandlerEntry{ "admin", admin.CategoriesHandler{}},
            // handling.HandlerEntry{ "admin", admin.OrdersHandler{}},
            // handling.HandlerEntry{ "admin", admin.DatabaseHandler{}},
            handling.HandlerEntry{ "", admin.AuthenticationHandler{}},
        ).AddMethodAlias("/", store.ProductHandler.GetProducts, 0, 1).
            AddMethodAlias("/products[/]?[A-z0-9]*?",
                store.ProductHandler.GetProducts, 0, 1),    )
}
func main() {
    registerServices()
    results, err := services.Call(http.Serve, createPipeline())
    if (err == nil) {
        (results[0].(*sync.WaitGroup)).Wait()
    } else {
        panic(err)
    }
}
Listing 38-17Configuring the Application in the main.go File in the sportsstore Folder
Compile and execute the application and use a browser to request http://localhost:5000/admin. When prompted, authenticate as user alice with password mysecret, and you will be granted access to the administration features, as shown in Figure 38-2.

Figure 38-2Signing into the application
Creating a Web Service
The final feature I am going to add is a simple web service, just to show how it can be done. I am not going to use authorization to protect the web service, which can be a complex process that depends on the type of clients expected to require access. This means that any user will be able to modify the database. If you are deploying a real web service, then you can use cookies in much the same way as I have done in this example. If your clients don’t support cookies, then JSON Web Tokens (JWTs) can be used, as described at https://jwt.io.

To create the web service, add a file named rest_handler.go to the sportsstore/store folder with the content shown in Listing 38-18.
package store
import (
    "sportsstore/models"
    "platform/http/actionresults"
    "net/http"
)
type StatusCodeResult struct {
    code int
}
func (action *StatusCodeResult) Execute(ctx *actionresults.ActionContext) error {
    ctx.ResponseWriter.WriteHeader(action.code)
    return nil
}
type RestHandler struct {
    Repository models.Repository
}
func (h RestHandler) GetProduct(id int) actionresults.ActionResult {
    return actionresults.NewJsonAction(h.Repository.GetProduct(id))
}
func (h RestHandler) GetProducts() actionresults.ActionResult {
    return actionresults.NewJsonAction(h.Repository.GetProducts())
}
type ProductReference struct {
    models.Product
    CategoryID int
}
func (h RestHandler) PostProduct(p ProductReference) actionresults.ActionResult {
    if p.ID == 0 {
        return actionresults.NewJsonAction(h.processData(p))
    } else {
        return &StatusCodeResult{ http.StatusBadRequest }
    }
}
func (h RestHandler) PutProduct(p ProductReference) actionresults.ActionResult {
    if p.ID > 0 {
        return actionresults.NewJsonAction(h.processData(p))
    } else {
        return &StatusCodeResult{ http.StatusBadRequest }
    }
}
func (h RestHandler) processData(p ProductReference) models.Product {
    product := p.Product
    product.Category = &models.Category {
        ID: p.CategoryID,
    }
    h.Repository.SaveProduct(&product)
    return h.Repository.GetProduct(product.ID)
}
Listing 38-18The Contents of the rest_handler.go File in the store Folder
The StatusCodeResult struct is an action result that sends an HTTP status code, which is useful for web services. The request handler defines methods that allow one product and all products to be retrieved using GET requests, new products to be created using POST requests, and existing products to be modified using PUT requests. Listing 38-19 registers the new handler with a prefix of /api.
...
handling.NewRouter(
     handling.HandlerEntry{ "",  store.ProductHandler{}},
     handling.HandlerEntry{ "",  store.CategoryHandler{}},
     handling.HandlerEntry{ "", store.CartHandler{}},
     handling.HandlerEntry{ "", store.OrderHandler{}},
     handling.HandlerEntry{ "", admin.AuthenticationHandler{}},
     handling.HandlerEntry{ "api", store.RestHandler{}},
).AddMethodAlias("/", store.ProductHandler.GetProducts, 0, 1).
    AddMethodAlias("/products[/]?[A-z0-9]*?",
    store.ProductHandler.GetProducts, 0, 1),
...
Listing 38-19Registering a Handler in the main.go File in the sportsstore Folder
Compile and execute the project. Open a new command prompt and execute the command shown in Listing 38-20 to add a new product to the database.
curl --header "Content-Type: application/json" --request POST --data '{"name" : "Jet Engine","description": "Paddling is hard work", "price":650, "categoryid":1}' http://localhost:5000/api/product
Listing 38-20Adding a New Product
If you are using Windows, open a new PowerShell window and run the command shown in Listing 38-21.
Invoke-RestMethod http://localhost:5000/api/product -Method POST -Body  (@{ Name="Jet Engine"; Description="Paddling is hard work"; Price=650; CategoryId=1 } | ConvertTo-Json) -ContentType "application/json"
Listing 38-21Adding a New Product in Windows
To see the effect of the change, run the command shown in Listing 38-22.
curl http://localhost:5000/api/product/10
Listing 38-22Requesting Data
If you are using Windows, run the command shown in Listing 38-23 in a PowerShell window.
Invoke-RestMethod http://localhost:5000/api/product/10
Listing 38-23Requesting Data in Windows
You can also use a browser to see the effect of the change. Request http://localhost:5000/admin. Authenticate as the user alice with the password mysecret and click the Products button. The last table row will contain the product created using the web service, as shown in Figure 38-3.

Figure 38-3Checking the effect of a database change
Preparing for Deployment
In this section, I will prepare the SportsStore application and create a container that can be deployed into production. This isn’t the only way that a Go application can be deployed, but I picked Docker containers because they are widely used and because they suit web applications. This is not a complete guide to deployment, but it will give you a sense of the process to prepare an application.

Installing the Certificates
The first step is to add the certificates that will be used for HTTPS. As explained in Chapter 24, you can create a self-signed certificate if you don’t have a real certificate available, or you can use the certificate files from the GitHub repository for this book (which contain a self-signed certificate that I created).

Configuring the Application
The most important change is to change the application configuration to disable features that are convenient during development but that should not be used in deployment, as well as to enable HTTPS, as shown in Listing 38-24.
{
    "logging" : {
        "level": "information"
    },
    "files": {
        "path": "files"
    },
    "templates": {
        "path": "templates/*.html",
        "reload": false
    },
    "sessions": {
        "key": "MY_SESSION_KEY",
        "cyclekey": false
    },
    "sql": {
        "connection_str": "store.db",
        "always_reset": false,
        "commands": {
            "Init": "sql/init_db.sql",
            "Seed": "sql/seed_db.sql",
            "GetProduct": "sql/get_product.sql",
            "GetProducts": "sql/get_products.sql",
            "GetCategories": "sql/get_categories.sql",
            "GetPage": "sql/get_product_page.sql",
            "GetPageCount": "sql/get_page_count.sql",
            "GetCategoryPage": "sql/get_category_product_page.sql",
            "GetCategoryPageCount": "sql/get_category_product_page_count.sql",
            "GetOrder": "sql/get_order.sql",
            "GetOrderLines": "sql/get_order_lines.sql",
            "GetOrders": "sql/get_orders.sql",
            "GetOrdersLines": "sql/get_orders_lines.sql",
            "SaveOrder": "sql/save_order.sql",
            "SaveOrderLine": "sql/save_order_line.sql",
            "SaveProduct":          "sql/save_product.sql",
            "UpdateProduct":        "sql/update_product.sql",
            "SaveCategory":         "sql/save_category.sql",
            "UpdateCategory":       "sql/update_category.sql",
            "UpdateOrder":          "sql/update_order.sql"
        }
    },
    "authorization": {
        "failUrl": "/signin"
    },
    "http": {
        "enableHttp": false,
        "enableHttps": true,
        "httpsPort": 5500,
        "httpsCert": "certificate.cer",
        "httpsKey": "certificate.key"
    }
}
Listing 38-24Changing Settings in the config.json File in the sportsstore Folder
Make sure that the values you specify for the httpsCert and httpsKey properties match the names of your certificate files and that the certificate files are in the sportsstore folder.

Building the Application
Docker containers run Linux. If you are running Windows, you must select Linux as the build target by running the commands shown in Listing 38-25 in a PowerShell window to configure the Go build tools. This isn’t required if you are running Linux.
$Env:GOOS = "linux"; $Env:GOARCH = "amd64"
Listing 38-25Setting Linux as the Build Target
Run the command shown in Listing 38-26 in the sportsstore folder to build the application.
go build
Listing 38-26Building the Application
NoteIf you are a Windows user, you can return to a normal Windows build with the following command: $Env:GOOS = "windows"; $Env:GOARCH = "amd64". But don’t run this command until you have completed the deployment process.
Installing Docker Desktop
Go to docker.com and download and install the Docker Desktop package. Follow the installation process, reboot your machine, and run the command shown in Listing 38-27 to check that Docker has been installed and is in your path. (The Docker installation process seems to change often, which is why I am not being more specific about the process.)

NoteYou will have to create an account on docker.com to download the installer.
docker --version
Listing 38-27Checking the Docker Desktop Installation
Creating the Docker Configuration Files
To create the Docker configuration for the application, create a file named Dockerfile in the sportsstore folder with the content shown in Listing 38-28.
FROM alpine:latest
COPY sportsstore /app/
COPY templates /app/templates
COPY sql/* /app/sql/
COPY files/* /app/files/
COPY config.json /app/
COPY certificate.* /app/
EXPOSE 5500
WORKDIR /app
ENTRYPOINT ["./sportsstore"]
Listing 38-28The Contents of the Dockerfile in the sportsstore Folder
These instructions copy the application and its supporting files into a Docker image and configure its execution. The next step is to create an image using the instructions defined in Listing 38-28. Run the command shown in Listing 38-29 in the sportsstore folder to create a Docker image.
docker build  --tag go_sportsstore .
Listing 38-29Creating an Image
Ensure that you have stopped all other instances of the application and run the command shown in Listing 38-30 to create a new container from the image and execute it.
docker run -p 5500:5500 go_sportsstore
Listing 38-30Creating and Starting a Container
Give the container a moment to start and then use a browser to request https://localhost:5500, which will produce the response shown in Figure 38-4. If you have used a self-signed certificate, then you may have to pass through a security warning.

Figure 38-4Running the application in a container
The application is now ready for deployment. To stop the container—and any other container that is running—run the command shown in Listing 38-31.
docker kill $(docker ps -q)
Listing 38-31Stopping Containers
Summary
In this chapter, I completed the SportsStore application by finishing the administration features, configuring authorization, and creating a basic web service, before preparing the application for deployment using a Docker container.

That’s all I have to teach you about Go. I can only hope that you have enjoyed reading this book as much as I enjoyed writing it, and I wish you every success in your Go projects.


Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


38. SportsStore: Finishing and Deployment
Back Matter
21h 44m remaining
Index
A
Address operator
append function
Arithmetic operators
Arithmetic overflow
Arrays
comparing
defining
enumerating
index notation
literal syntax
multi-dimensional arrays
pointers, to
types compiler inference
values
Arrow expressions
B
Benchmarking
Blank identifier
Boolean data types
C
cap function
Channels
arrow expressions
buffering
closing
coordinating
enumerating
receiving
results
select statements
sending
types
unidirectional
Character data types
close function
Closures
Constant values
untyped constants
Contexts
databases
Converting types
explicit conversions
formatting strings
math package
parsing integers
parsing strings
copy function
D
Databases
closing
contexts
DB struct
drivers, listing
opening
queries
results
multiple rows
scanning
single row
statements
placeholders
prepared statements
transactions
committing
rollback
starting
using
Data types
bool
byte
complex64
complex128
float32
float64
int
run
string
uint
Debugging
breakpoint
commands
debugging in editor
Delve debugger
dlv Command
defer keyword
delete function
Dependency injection
dlv Command
Docker
Documentation, code
do...while loops
Durations
methods
parsing
E
Empty interface
Enumerating sequences, range keyword
Errata, reporting
error interface
Errors
channels
convenience functions
defer keyword
error interface
ignoring errors
panic function
panicking
recoverable
recover function
recovering from panics
reporting
unrecoverable
Explicit type conversion
F
File paths
Files
closing
common file locations
creating
directories
file paths
files and directories
File struct
reading
convenience function
decoding JSON
seeking
standard error
standard input
standard output
temporary files
writing
convenience function
File struct
seeking
File struct
Floating-point data types
Flow control
completion statements
do...while loops
else clauses
else if clauses
if statement
initialization statements
label statements
for loops
scope
switch statements
fall through
type switching
syntax restrictions
fmt package
for loop
completion statements
do...while loops
initialization statements
range keyword
Formatting strings
Formatting verbs
func keyword
Functions
closures
defer keywords
defining
func keyword
literal syntax
parameters
omitting names
omitting types
pointers
variadic
results
multiple
named
using as arguments
using as results
Function types
aliases
closures
comparisons
defining
parameters
results
G
go build command
go clean command
go command
unit testing
arguments
go doc command
go fmt command
go get command
go install Command
go keyword
go mod Command
Goroutines
channels
conditions
creating
deferring execution
go keyword
mutual exclusion, read-write
Once struct
pausing
pausing execution
results
timed notifications
go run command
go vet command
H
HTTP
cookies
form data
POST requests
requests
Client struct
convenience functions
cookies
forms
redirections
Request struct
Response struct
ResponseWriter interface
server
certificates
content type sniffing
convenience responses
creating
dynamic content
files
HTTPS
JSON data
processing requests
routing
static content
TLS
URL struct
I
if statement
initialization statement
scope
import keyword
import statement
Initialization statement
Integer data types
interface keyword
Interfaces
comparing
defining
dynamic types
empty interface
implementing
static types
type assertions
using
iota keyword
J, K
JSON
decoding
arrays
interfaces
maps
numbers
structs
Unmarshaler interface
encoding
arrays
data type mappings
interfaces
maps
Marshaler interface
slices
structs
struct tags
NewDecoder function
NewEncoder function
L
Label statements
len function
Linter
configuration
disabling rules
installing
revive
using
Listings
Literal values, examples
Localization
Logging, log package
M
Maps
checking for items
delete function
enumerating
literal syntax
removing items
types
Math
functions
math/rand package
random numbers
ranges
seeding
shuffling slices
math package
math/rand package
Methods
defining
overloading
parameters
receiver
receivers, pointers
results
for type aliases
Module
creating
go.mod file
Mutual exclusion
N
new function
O
Operators
arithmetic
arithmetic overflow
comparison, pointers
decrement
equality
increment
logical
remainder operator
ternary
os package
P, Q
Package declaration
package keyword
Packages
access control
blank identifier
creating
initialization functions
name conflicts
aliases
dot imports
third part packages
using
panic function
Pipes
Pointers
address operator
comparing
defining
following
method receivers
pointer arithmetic
structs
zero values
R
Random numbers
range keyword
Ranges
Readers
buffering
Closer interface
pipes
Reader interface
Read method
scanning
specialized implementations
utility functions
recover function
Reflection
database results
reflected types
basic features
identifying
kinds of type
reflected values
basic features
comparing
converting
creating
obtaining
setting
types
arrays
channels
functions
interfaces
maps
methods
pointers
slices
structs
values
arrays
channels
functions
interfaces
maps
methods
pointers
slices
structs
reflect package
Regular expressions
compiling patterns
finding strings
matching
matching strings
replacing strings
splitting strings
subexpressions
RESTful web service
Runes
changing case
from string
S
Scope
select statements
timeouts
Semicolons in code files
Short variable declaration syntax
Slices
appending to
capacity allocating
comparing
copying elements
creating from arrays
creating from other slices
deleting elements
enumerating
ranges
reflect package
shuffling
sorting
custom types
searching
sort package
types
underlying arrays
sort package
SportsStore
access control
action results
administration
authorization
cart
checkout
configuration
CSS
database
data model
dependency injection
deployment
Docker
filtering
HTML responses
logging
middleware components
pagination
pipeline
request handlers
services
sessions
URL generation
validation
web service
Standard error
Standard input
Standard output
String data type
Strings
building strings
byte content
case changes
character content
comparing
concatenating
converting case
enumerating
finding substrings
formatting
fmt package
precision
width
formatting verbs
parsing
regular expressions
replacing characters
rune content
scanning
splitting
trimming
Structs
address operator
anonymous structs
arrays
classes
comparing
constructor functions
converting
defining
embedded fields
fields embedded
maps
new function
pointers
slices
tags
values
zero-values
switch statement
fall through
T
Templates
actions
blocks
conditions
data values
enumerating
executing
formatting values
functions
loading patterns
nested templates
result encoding
slices
variables
whitespace
Ternary comparisons
Times and dates
durations
formatting
layout constants
manipulating
parsing from strings
representing
types
TLS
Type aliases
Type assertions testing
Type composition
base type
constructor functions
embedded fields
interfaces
dynamic types
promotion
ambiguity
restrictions
type chains
U
Unicode
Unit testing
go command
managing execution
mock types
package statement
running
skipping
test files
test functions
T struct
Untyped constants, iota
V
Variables
blank identifier
defining
redefining
short syntax
var keyword
Variable scope
W, X, Y, Z
Wait groups
Writers
buffering
Closer interface
pipes
scanning
specialized implementations
utility functions
Writer interface
Write method

Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue

