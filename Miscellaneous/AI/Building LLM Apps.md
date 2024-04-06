Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


Building LLM Apps
Building LLM Apps: Create Intelligent Apps and Agents with Large Language Models
1 Introduction to Large Language Models
4h 29m remaining
Building LLM Apps: Create Intelligent Apps and Agents with Large Language Models
Welcome to Packt Early Access. We’re giving you an exclusive preview of this book before it goes on sale. It can take many months to write a book, but our authors have cutting-edge information to share with you today. Early Access gives you an insight into the latest developments by making chapter drafts available. The chapters may be a little rough around the edges right now, but our authors will update them over time.You can dip in and out of this book or follow along from start to finish; Early Access is designed to be flexible. We hope you enjoy getting to know more about the process of writing a Packt book.

Chapter 1: Introduction to Large Language Models
Chapter 2: LLMs for AI-powered Applications
Chapter 3: Choosing an LLM for your application
Chapter 4: Prompt Engineering
Chapter 5: Embedding LLMs within your Applications
Chapter 6: Building Conversational applications
Chapter 7: Search and Recommendation engines with LLMs
Chapter 8: LLMs on structured data
Chapter 9: Generating Code and Structured Outputs
Chapter 10: Building multi-modal Agents
Chapter 11: Fine-tuning LLMs
Chapter 12: Responsible AI
Chapter 13: Emerging Trends and Innovations

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


Building LLM Apps: Create Intelligent Apps and Agents with Large Language Models
1 Introduction to Large Language Models
2 LLMs for AI-powered Applications
4h 29m remaining
1 Introduction to Large Language Models
Join our book community on Discord
https://packt.link/EarlyAccessCommunity



Dear reader, welcome to Building Large Language Models application! In this book, we will explore the fascinating world of a new era of application developments, where Large Language Models are the main protagonist.During the last year, we all got to know the power of Generative AI tools such as ChatGPT, Bing Chat, Bard, Dall-E. What mainly impressed us was their stunning capabilities of generating human-like content based on user's request made in natural language. It is in fact their conversational capabilities to make them so easily consumable and, henceforth, popular as soon as they entered the market. Thanks to this phase, we learned to aknowledge the power of Generative AI and its core models: Large Language Models. However, LLMs are more than language generator. They can be also seen as reasoning engines which can become the brains of our intelligent applications. In this book, we will see the theory and practice of how to build LLM-powered applications, addressing a variety of scenarios and showing new components and frameworks that are entering the domain of software development in this new era of AI. The book will start with a first Part where we will introduce the theory behind LLMs, the most promising LLMs in the market right now and the emerging frameworks for LLMs-powered applications. Afterwards, we will move to a hands-on Part where we will implement many applications using various LLMs, addressing different scenarios and real-world problems. Finally, we will conclude the book with a third Part, covering the emerging trends in the field of LLMs, alongside the risk of AI tools and how to mitigate them with Responsible AI practices.So, let’s dive in and start with some definitions of the context we are moving in. This chapter provides an introduction and deep dive into Large Language Models (LLMs), a powerful set of deep learning neural networks that feature the domain of Generative AI.In this chapter, we will cover the following topics:

Understanding of LLMs, their differentiators from classical Machine Learning models and their relevant jargon;
Overview of the most popular LLMs’ architectures
How LLMs are trained and consumed
Base LLMs versus fine-tuned LLMs
By the end of this chapter, you will have the fundamental knowledge of what LLMs are, how they work, and how you can make them more tailored to your applications. This will also pave the way for the concrete usage of LLMs in the hands-on part of this book, where we will see in practice how to embed LLMs within your applications.

Technical requirements
None

What are Large Foundation Models and Large Language Models?
Large language Models (LLMs) are deep-learning-based models that use many parameters to learn from vast amounts of unlabeled texts. They can perform various natural language processing tasks such as recognizing, summarizing, translating, predicting, and generating text.LLMs belong to a wider set of models that feature the artificial intelligence (AI) subfield of generative AI: the Large Foundation Models (LFMs). Henceforth, in the following sections, we will explore the rise and development of LFMs and LLMs, as well as their technical architecture, which is a crucial task to understand their functioning and properly adopt those technologies within your applications.We will start by understanding why LFMs and LLMs differ from traditional AI models and how they represented a paradigm shift in this field. We will then explore the technical functioning of LLMs, how they work, and which are the mechanisms behind their outcomes.

AI Paradigm shift: introduction to Foundation Models
A foundation model refers to a type of pre-trained generative AI model that offers immense versatility by being adaptable for various specific tasks. These models undergo extensive training on vast and diverse datasets, enabling them to grasp general patterns and relationships within the data – not limited to textual, but also covering other data format such as images, audio, video. This initial pre-training phase equips the models with a strong foundational understanding across different domains, laying the groundwork for further fine-tuning.Foundation models are designed with transfer learning in mind, meaning they can effectively apply the knowledge acquired during pre-training to new, related tasks. This transfer of knowledge enhances their adaptability, making them efficient in quickly mastering new tasks with relatively little additional training.One notable characteristic of foundation models is their large architecture, containing millions or even billions of parameters. This extensive scale enables them to capture complex patterns and relationships within the data, contributing to their impressive performance across various tasks.Due to their comprehensive pre-training and transfer learning capabilities, foundation models exhibit strong generalization skills. This means they can perform well across a range of tasks and efficiently adapt to new, unseen data, eliminating the need for training separate models for individual tasks.This paradigm shift in artificial neural network design offers considerable advantages, as foundation models with their diverse training dataset can adapt to different tasks based on users' intent without compromising performance or efficiency. In the past, creating and training distinct neural networks for each task, such as Named Entity Recognition or Sentiment Analysis, would have been necessary, but now, foundation models provide a unified and powerful solution for multiple applications.

 
Figure 1: From task-specific models to general models
Henceforth, when it comes to foundation models focused on language understanding and generation, we talk about LLMs.

 
ss
Figure 2: Features of LLMs
We can then say that an LLM is a type of foundation model specifically designed for natural language processing tasks. These models, such as ChatGPT, BERT, Llama and many others, are trained on vast amounts of text data and can generate human-like text, answer questions, perform translations, and more. Nevertheless, LLMs don’t limit to performing text-related tasks. As we will see throughout the book, those unique models can be seen as reasoning engines, extremely good in common sense reasoning. This means that they can assist us in complex tasks, analytical problem-solving, enhanced connections and insights among pieces of information.In fact, as LLMs mimic the way our brains are made (as we will see in next section), their architectures are featured by connected neurons. Now, human brains have about 100 trillion connections, way more than those within an LLM. Nevertheless, LLMs have proven to be much better at packing a lot of knowledge into those fewer connections than we are.According to Geoffrey Hinton, the godfather of modern neural network AI which is the basis of Large Language Models, it is because backpropagation may be a much much better learning algorithm than what we’ve got.

Definition

Backpropagation is an algorithm used in deep learning to train neural networks. It involves two phases: the forward pass, where data is passed through the network to compute the output, and the backward pass, where errors are propagated backward to update the network's parameters and improve its performance. This iterative process helps the network learn from data and make accurate predictions.

Under the hood of an LLM
Large Language Models are a particular type of Artificial Neural Networks (ANNs), computational models inspired by the structure and functioning of the human brain. They have proven to be highly effective in solving complex problems, particularly in areas like pattern recognition, classification, regression, and decision-making tasks.The basic building block of an artificial neural network is the artificial neuron, also known as a node or unit. These neurons are organized into layers, and the connections between neurons are weighted to represent the strength of the relationship between them. Those weights represent the parameters of the model that will be optimized during the training process.ANNs are, by definition, mathematical models that work with numerical data. Henceforth, when it comes to unstructured, textual data as in the context of LLMs, there are two fundamental activities that are required to prepare data as model input:

Tokenization->it is the process of breaking down a piece of text (a sentence, paragraph, or document) into smaller units called tokens. These tokens can be words, subwords, or even characters, depending on the chosen tokenization scheme or algorithm. The goal of tokenization is to create a structured representation of the text that can be easily processed by machine learning models.

 
Figure 3: Example of tokenization
Embedding->Once the text has been tokenized, each token is converted into a dense numerical vector called an embedding. Embeddings are a way to represent words, subwords, or characters in a continuous vector space. These embeddings are learned during the training of the language model and capture semantic relationships between tokens. The numerical representation allows the model to perform mathematical operations on the tokens and understand the contexst in which they appear.
 
Figure 4: Example of embedding
In summary, tokenization breaks down text into smaller units called tokens, and embeddings convert these tokens into dense numerical vectors. This relationship allows large language models to process and understand textual data in a meaningful and context-aware manner, enabling them to perform a wide range of natural language processing tasks with impressive accuracy.Once we have the vectorized input, we can pass it into the multi-layered neural network. There are three main types of layers:

Input Layer: The first layer of the neural network receives the input data. Each neuron in this layer corresponds to a feature or attribute of the input data.
Hidden Layers: Between the input and output layers, there can be one or more hidden layers. These layers process the input data through a series of mathematical transformations and extract relevant patterns and representations from the data.
Output Layer: The final layer of the neural network produces the desired output, which could be predictions, classifications, or other relevant results depending on the task the neural network is designed for.
 
Figure 5: High-level architecture of a generic Artificial Neural Network
The process of training an artificial neural network involves the process of backpropagation by iteratively adjusting the weights of the connections between neurons based on the training data and the desired outputs. During backpropagation, the network learns by comparing its predictions with the ground truth and minimizing the error or loss between them. The objective of training is to find the optimal set of weights that enables the neural network to make accurate predictions on new, unseen data.Artificial neural networks can vary in architecture, including the number of layers, the number of neurons in each layer, and the connections between them. When it comes to generative AI and LLMs, their remarkable capability of generating text based on our prompts is based on the statistical concept of Bayes’ theorem, which relates the conditional probability of an event based on new evidence with the priori probability of the event.

Definition

Bayes' theorem, named after the Reverend Thomas Bayes, is a fundamental concept in probability theory and statistics. It describes how to update the probability of a hypothesis based on new evidence. Bayes' theorem is particularly useful when we want to make inferences about unknown parameters or events in the presence of uncertainty. According to Bayes’ theorem, given two events A and B, we can define the conditional probability of A given B as:


With:

P(B|A) = probabilty of B occurring given A, also known as likelihood of A given a fixed B.

P(A|B) = probabilty of A occurring given B, also known as posterior probability, also known as posterior probability of A given B.

P(A) and P(B) = probability of observing A or B without any conditions.

Translated into the context of LLMs, we are saying that such a model functions by predicting the next most likely word, given the previous words prompted by the user. But how can LLMs know which is the next most likely word? Well, thanks to the enormous amount of data on which LLMs have been trained on (we will dive deeper into the process of training a LLM in next sections). Based on the training text corpus, the model will be able to identify, given an user’s prompt, the next most likely word or, more generally, text completion.For example, let’s consider the following prompt: “the cat is on the….” and we want the model to complete this sentence. However, the LLM may generate multiple candidate words, and we want to use Bayes' theorem to select the most likely word given the context. Let’s see what are the steps needed:

Prior probability P(A). The prior probability represents the probability of each candidate word being the next word in the context, based on the language model's knowledge learned during training. Let's assume the LLM has three candidate words: "table," "chair," and "roof".
P("table"), P("chain"), and P("roof") are the prior probabilities for each candidate word, based on the language model's knowledge of the frequency of these words in the training data.
Likelihood (P(B|A)). The likelihood represents how well each candidate word fits the context "The cat is on the..." This is the probability of observing the context given each candidate word. The LLM calculates this based on the training data and how often each word appears in similar contexts.
For example, if the LLM has seen many instances of "The cat is on the table," it would assign a high likelihood to "table" as the next word in the given context. Similarly, if it has seen many instances of "The cat is on the chair," it would assign a high likelihood to "chair" as the next word.
P("table" | " The cat is on the..."), P("chair" | " The cat is on the..."), and P("roof" | " The cat is on the...") are the likelihoods for each candidate word given the context.
Posterior Probability (P(A|B)). Using Bayes' theorem, we can calculate the posterior probability for each candidate word based on the prior probability and the likelihood.

Selecting the Most Likely Word. After calculating the posterior probabilities for each candidate word, we choose the word with the highest posterior probability as the most likely next word to complete the sentence.
The LLM uses Bayes' theorem and the probabilities learned during training to generate text that is contextually relevant and meaningful, capturing patterns and associations from the training data to complete sentences in a coherent manner.The following picture illustrates how it translates into the architectural framework of a neural network:

 
Figure 6: Predicting the next most likely word in a Large Language Model.
Overall, Artificial Neural Networks are the core pillars of the development of Generative AI models: thanks to their mechanisms of tokenization, embedding and multiple hidden layers, they can capture complex patterns even in the most unstructured data, such as natural language.However, what we are observing today is a set of models that is demonstrating incredible capabilities that have never been seen before, and this is due to a particular ANNs’ architectural framework, introduced in recent years and main protagonist of Large Language Models’ development. This framework is called Transformer, and we are going to cover it in the following section.

Most popular LLMs transformers-based architectures
Artificial Neural Networks, as we saw in the preceding sections, are at the core of LLMs. Nevertheless, in order to be generative, those ANNs need to be endowed with some peculiar capabilities, such as parallel processing of textual sentences or keeping memory of previous context. These particular capabilities were at the core of generative AI research in the last decades, starting from the 80s and 90s. However, it is only in recent years that the main drawbacks of these early models - such as the capability to text parallel processing or memory management – have been bypassed modern generative AI frameworks, that are called Transformers.In the following sections, we will explore the evolution of generative AI models architecture, from early developments to state-of-the-art transformers. We will start by covering the first generative AI models that paved the way to further research, highlighting their limitations and the approaches to overcome them. We will then explore the introduction of Transformer-based architectures, covering their main components and explaining why they represent the state-of-the-art for Large Language Models.

Early experiments
The very first popular generative AI artificial neural network (ANN) architectures trace back to the 80s and 90s, including:

Recurrent Neural Networks (RNNs). RNNs are a type of ANN designed to handle sequential data. They have recurrent connections that allow information to persist across time steps, making them suitable for tasks like language modelling, machine translation, and text generation. However, RNNs have limitations in capturing long-range dependencies due to the vanishing or exploding gradient problem.

Definition

In ANNs, the gradient is a measure of how much the model's performance would improve if we slightly adjusted its internal parameters (weights). During training, RNNs try to minimize the difference between their predictions and the actual targets by adjusting their weights based on the gradient of the loss function. The problem of vanishing or exploding gradient arises in RNNs during training when the gradients become extremely small or large, respectively. The vanishing gradient problem occurs when the gradient becomes extremely small during training. As a result, the RNN learns very slowly and struggles to capture long-term patterns in the data. Conversely, the exploding gradient problem happens when the gradient becomes extremely large. This leads to unstable training and prevents the RNN from converging to a good solution.

Long Short-Term Memory (LSTM). LSTMs are a variant of RNNs that address the vanishing gradient problem. They introduce gating mechanisms that enable better preservation of important information across longer sequences. LSTMs became popular for various sequential tasks, including text generation, speech recognition, and sentiment analysis.
These architectures were popular and effective for various generative tasks, but they had limitations in handling long-range dependencies, scalability, and overall efficiency, especially when dealing with large-scale natural language processing tasks that would need massive parallel processing.To overcome these limitations, a new framework was introduced: the Transformer. In next section, we are going to see how transformers-based architecture overcome the above limitations and are at the core of modern generative AI LLMs.

Introducing the Transformer architecture
The Transformer architecture is a deep learning model introduced in the paper "Attention Is All You Need" by Vaswani et al. (2017). It revolutionized natural language processing (NLP) and other sequence-to-sequence tasks.The transformer is dispensing with recurrence and convolutions entirely, and relies solely on attention mechanisms to encode and decode sequences.

Definition

In the Transformer architecture, "attention" is a mechanism that enables the model to focus on relevant parts of the input sequence while generating the output. It calculates attention scores between input and output positions, applies softmax to get weights, and takes a weighted sum of the input sequence to obtain context vectors. Attention is crucial for capturing long-range dependencies and relationships between words in the data.

Attnetion layers are responsible for determining the importance of each input token in generating the output. Those answer to the question: “Which part of the input should I focus on?” In order to obtain the self-attention vector for a sentence, the elements we need are “value”, “query”, and “key”. These matrices are used to calculate attention scores between the elements in the input sequence and are the three weight matrices that are learned during the training process (typically initialized with random values)“Query” is used to represent the current focus of the attention mechanism, while “key” is used to determine which parts of the input should be given attention and “value” is used to compute the context vectors. Those matrices are then multiplied and passed through a non-linear transformation (thanks to a softmax function). The output of the self-attention layer represents the input values in a transformed, context-aware manner, which allows the transformer to attend to different parts of the input depending on the task at hand.

 
Figure 7: representation of Query, Key and Value matrices multiplication to obtain the context vector.
From an architectural point of view, the transformer consists of two main components: an encoder and a decoder.

The encoder takes the input sequence and produces a sequence of hidden states, each of which is a weighted sum of all the input embeddings.
The decoder takes the output sequence (shifted right by one position) and produces a sequence of predictions, each of which is a weighted sum of all the encoder hidden states and the previous decoder hidden states.
The following illustration from the original paper shows the transformer architecture:

 
Figure 8: Transformer Architecture from the original paper “Attention is all you need”, showing the Encoder block (left) and the Decoder block (right). https://arxiv.org/abs/1706.03762
Let’s examine each building block, starting from the encoding part:

Input embedding->those are the vector representation of tokenized input text;
Positional encoding-> as the Transformer does not have an inherent sense of word order (unlike RNNs with their sequential nature), positional encodings are added to the input embeddings. These encodings provide information about the positions of words in the input sequence, allowing the model to understand the order of tokens;
Multi-head attention layer-> a mechanism in which multiple self-attention mechanisms operate in parallel on different parts of the input data, producing multiple representations. This allows the Transformer model to attend to different parts of the input data in parallel and aggregate information from multiple perspectives.
Add and Norm layer-> it combines element-wise addition and layer normalization. It adds the output of a layer to the original input and then applies layer normalization to stabilize and accelerate training. This technique helps mitigate gradient-related issues and improves the model's performance on sequential data;
Feed-forward layer-> it is responsible for transforming the normalized output of attention layers into a suitable representation for the final output, using non-linear activation function such as the ReLU.
The decoding part of the Transformer starts with a similar process as the encoding part, where the target sequence (output sequence) undergoes input embedding and positional encoding.

Output embedding (shifted right)-> For the decoder, the target sequence is "shifted right" by one position. This means that at each position, the model tries to predict the token that comes after the token in the original target sequence. This is achieved by removing the last token from the target sequence and padding it with a special start-of-sequence token (start symbol). This way, the decoder learns to generate the correct token based on the preceding context during autoregressive decoding.
Decoders layers->similarly to the encoder block, also here we have positional encoding, multi-head attention, Add&Norm, and feed-forward layers, whose role is the same as above;
Linear and SoftMax->those layers apply, respectively, a linear and non-linear transformation to the output vector. The non-linear transformation (softmax) convey the output vector into a probability distribution, corresponding to a set of candidate word. The word corresponding to the greatest element of the probability vector will be the output of the whole process.
The Transformer architecture paved the way for modern Large Language Models, and it also see many variations with respect to its original framework.Some models use only the encoder part, such as BERT (Bidirectional Encoder Representations from Transformers), which is designed for natural language understanding tasks such as text classification, question answering and sentiment analysis. Other models use only the decoder part, such as GPT-3 (Generative Pre-trained Transformer 3), which is designed for natural language generation tasks such as text completion, summarization and dialogue. Finally, there are models that use both the encoder and the decoder parts, such as T5 (Text-to-Text Transfer Transformer), which is designed for various natural language processing tasks that can be framed as text-to-text transformations, such as translation, paraphrasing and text simplification.Regardless of the variant, the core component of Transformer – the attention mechanism – remain a constant within LLMs architecture, and it also represents the reason why those frameworks gained so much popularity within the context of generative AI and NLP.However, the architectural variant of an LLM is not the only element that features the functioning of that model. This functioning is indeed characterized also by what the model knows, depending on its training dataset, and how well it applies its knowledge upon user’s request, depending on its evaluation metrics.In the next section, we are going to cover both the processes of training and evaluating LLMs, also providing those metrics needed to differentiate among different LLMs and understand which one to use for specific use cases within your applications.

Training and evaluating LLMs
In the preceding sections, we saw how choosing an LLM architecture is a pivotal step in determining its functioning. However, the quality and diversity of the texts depend largely on two factors: the training dataset and the evaluation metric. The training dataset determines what kind of data the LLM learns from and how well it can generalize to new domains and languages. The evaluation metric measures how well the LLM performs on specific tasks and benchmarks, and how it compares to other models and human writers. Therefore, choosing an appropriate training dataset and evaluation metric is crucial for developing and assessing LLMs. In this section, we will discuss some of the challenges and trade-offs involved in selecting and using different training datasets and evaluation metrics for LLMs, as well as some of the recent developments and future directions in this area.

Training a Large Language Model
By definition, Large Language Models are huge, from a double point of view:

Number of parameters: It is a measure of the complexity of the LLM architecture and represents the number of connections among neurons. Complex architectures have tons of layers, each one having multiple neurons, meaning that among layers we will have several connections with associated parameters (or weights).
Training set: It refers to the unlabeled text corpus on which the LLM learns and train its parameter. To give an idea of how big can be such a text corpus for an LLM, let’s consider the OpenAI’s GPT-3 training set:
 
Figure 9: GPT-3 Knowledge base
Considering the assumption:

1 token ~= 4 chars in English
1 token ~= ¾ words
We can conclude that GPT-3 has been trained on around 374 billion words.So generally speaking, LLMs are trained using unsupervised learning on massive datasets, which often consist of billions of sentences collected from diverse sources on the internet. The transformer architecture, with its self-attention mechanism, allows the model to efficiently process long sequences of text and capture intricate dependencies between words. Training such models necessitates vast computational resources, typically employing distributed systems with multiple Graphical Processing Units (GPUs) or Tensor Processing Units (TPUs).

Definition

A tensor is a multi-dimensional array used in mathematics and computer science. It holds numerical data and is fundamental in fields like machine learning.

A Tensor Processing Unit (TPU) is a specialized hardware accelerator created by Google for deep learning tasks. TPUs are optimized for tensor operations, making them highly efficient for training and running neural networks. They offer fast processing while consuming less power, enabling faster model training and inference in data centers.

The training process involves numerous iterations over the dataset, fine-tuning the model's parameters using optimization algorithms backpropagation. Through this process, transformer-based language models acquire a deep understanding of language patterns, semantics, and context, enabling them to excel in a wide range of natural language processing tasks, from text generation to sentiment analysis and machine translation.Below the main steps involved in the training process of a Large Language Model:

Data collection. This is the process of gathering a large amount of text data from various sources, such as the open web, books, news articles, social media, etc. The data should be diverse, high-quality, and representative of the natural language that the LLM will encounter.
Data preprocessing. This is the process of cleaning, filtering, and formatting the data for training. This may include removing duplicates, noise, or sensitive information, splitting the data into sentences or paragraphs, tokenizing the text into subwords or characters, etc.
Model architecture. This is the process of designing the structure and parameters of the LLM. This may include choosing the type of neural network (such as transformer) and its structure (such as decoder only, encoder only or encoder-decoder), the number and size of layers, the attention mechanism, the activation function etc.
Model initialization. This is the process of assigning initial values to the weights and biases of the LLM. This may be done randomly or by using pre-trained weights from another model.
Model training. This is the process of updating the weights and biases of the LLM by feeding it batches of data and computing the loss function. The loss function measures how well the LLM predicts the next token given the previous tokens. The LLM tries to minimize the loss by using an optimization algorithm (such as gradient descent, Adam, etc.) that adjusts the weights and biases in the direction that reduces the loss with the backpropagation mechanism. The model training may take several epochs (iterations over the entire data set) until it converges to a low loss value.
Once we have a trained model, the next and final step is evaluating its performance.

Model evaluation
Evaluating traditional AI models was, in some ways, pretty intuitive. For example, let’s think about an image classification model that have to determines whether the input image represents a dog or a cat. So we train our model on a training dataset with a set of labelled images and, once the model is trained, we test it on unlabeled images. The evaluation metric is simply the percentage of correctly classified images over the total number of images within the test set.When it comes to Large Language Models, the story is a bit different. As those models are trained on unlabeled text and are not task-specific, but rather generic and adaptable given a user’s prompt, traditional evaluation metrics were not suitable anymore. Evaluating an LLM means, among other things, measuring its language fluency, its coherence, its ability to emulate different styles depending on user’s request.Henceforth, a new set of evaluation frameworks urged to be introduced. The following are the most popular frameworks used to evaluate LLMs:

GLUE (General Language Understanding Evaluation) and SuperGLUE-> this benchmark is used to measure the performance of LLMs on various natural language understanding tasks, such as sentiment analysis, natural language inference, question answering, etc. The higher the score on the GLUE benchmark, the better the LLM is at generalizing across different tasks and domains.
It recently evolved into a new benchmark styled after GLUE and called SuperGLUE, that comes with more diffucult tasks. It consists of eight challenging tasks that require more advanced reasoning skills than GLUE, such as natural language inference, question answering, coreference resolution, etc., a broad coverage diagnostic set that tests models on various linguistic capabilities and failure modes, and a leaderboard that ranks models based on their average score across all tasks.
The difference between the GLUE and the SuperGLUE benchmark is that the SuperGLUE benchmark is more challenging and realistic than the GLUE benchmark, as it covers more complex tasks and phenomena, requires models to handle multiple domains and formats, and has higher human performance baselines. The SuperGLUE benchmark is designed to drive research in the development of more general and robust natural language understanding systems.
MMLU (Massive Multitask Language Understanding) ->it is a benchmark that measure the knowledge of an LLM using zero-shot and few-shot settings.

Definition

The concept of zero-shot evaluation is a method of evaluating a language model without any labeled data or fine-tuning. It measures how well the language model can perform a new task by using natural language instructions or examples as prompts, and computing the likelihood of the correct output given the input. It the probability that a trained model will produce a particular set of tokens without needing any labeled training data.

This design adds complexity to the benchmark and aligns it more closely with the way we assess human performance. The benchmark comprises 14,000 multiple-choice questions categorized into 57 groups, spanning STEM, Humanities, Social Sciences, and Other fields. It covers a spectrum of difficulty levels, ranging from basic to advanced professional, assessing both general knowledge and problem-solving skills. The subjects encompass various areas, including traditional ones like mathematics and history, as well as specialized domains like law and ethics. The extensive range of subjects and depth of coverage makes this benchmark valuable for uncovering any gaps in a model's knowledge. Scoring is based on subject-specific accuracy and the average accuracy across all subjects.
HellaSwang->The HellaSwag evaluation framework is a method of evaluating large language models (LLMs) on their ability to generate plausible and commonsense continuations for given contexts. It is based on the HellaSwag dataset, which is a collection of 70,000 multiple-choice questions that cover diverse domains and genres, such as books, movies, recipes, etc. Each question consists of a context (a few sentences that describe a situation or an event) and four possible endings (one correct and three incorrect). The endings are designed to be hard to distinguish for LLMs, as they require world knowledge, common sense reasoning, and linguistic understanding.
TruthfulQA-> it is a benchmark that evaluates a language model's accuracy in generating responses for questions. It includes 817 questions across 38 categories like health, law, finance, and politics. The questions are designed to mimic those that humans might answer incorrectly due to false beliefs or misunderstandings.
A12 Reasoning Challenge (ARC)-> it is a benchmark used to measure LLMs’ reasoning capabilities and to stimulate the development of models that can perform complex Natural Language Understanding (NLU) tasks. It consists of a dataset of 7,787 multiple-choice science questions, assembled to encourage research in advanced question answering. The dataset is divided into an Easy Set and a Challenge Set, where the latter contains only questions that require complex reasoning or additional knowledge to answer correctly. The benchmark also provides a corpus of over 14 million science sentences that can be used as supporting evidence for the questions.
It is important to note that each evaluation framework has a focus on a specific feature. Namely, the GLUE Benchmark focuses on grammar, paraphrasing, text similarity, while MMLU focuses on generalized language understanding among various domains and tasks. Henceforth, while evaluating an LLM, it is important to have a clear understanding of the final goal, so that the most relevant evaluation framework can be used. Alternatively, if the goal is that of having the best of the breed in any task, it is key not to use only one evaluation framework, but rather an average of multiple frameworks.In addition to that, in case no existing LLM is able to tackle your specific use cases, you still have margin to customize those models and make them more tailored towards your application scenarios. In the next section, we are indeed going to cover the existing techniques of LLM customization, from the lightest ones (such as prompt engineering) up to the whole training of an LLM from scratch.

Base models versus customized models
The nice thing about Large Language Models is that they have been trained and ready to use. As we saw in the previous section, training an LLM requires great investment in hardware (GPUs or TPUs) and it might last for months, hardly feasible from individuals. Luckily, pre-trained LLM are generalized enough to be applicable at various tasks, so they can be consumed as they are directly via their REST API (we will dive deeper into model consumption in next chapters). Nevertheless, there might be scenarios where a general-purpose LLM is not enough, since it lacks domain-specific knowledge or doesn’t conform to a particular style and taxonomy of communication. If this is the case, you might want to customize your model.

How to customize your model
There are three main ways to customize your model:

Extending non-parametric knowledge. This allows the model to access external sources of information to integrate its parametric knowledge while responding to user’s query.
Definition

Large Language Models exhibit two types of knowledge: parametrc and non-parametric. The parametric knowledge is the one embedded in the LLM’s parametes, deriving from the unlabelled text corpora during the training phase. On the other hand, non-parametric knowledge is the one we can “attach” to the model via embedded documentation. Non-parametric knowledge doesn’t change the structure of the model, but rather allows it to navigate throught external documentation to be used as relevant context to answer user’s query.

This might involve connecting the model to web sources (like Wikipedia) or internal documentations with domain-specific knowledge. The connection of the LLM towards external sources is called plug-in, and we will be discussing it more deeply in the hands-on section of this book.

Few-shot learning. In this type of model customization, the LLM is given with a metaprompt with small number of examples (typically between 3 and 5) of each new task it is asked to perform. The model must use its prior knowledge to generalize from these examples to perform the task.

Definition

A metaprompt is a message or instruction that can be used to improve the performance of LLMs on new tasks with few examples. 

Fine tuning. The fine-tuning process involves using smaller, task-specific datasets to customize the foundation models for particular applications.
This approach differs to the first ones because, with fine tuning, the parameters of the pre-trained model are altered and optimized toward the specific task. This is done by training the model on a smaller labelled dataset that is specific to the new task. The key idea behind fine tuning is to leverage the knowledge learned from the pre-trained model and fine-tune it to the new task, rather than training a model from scratch.

 
Figure 10s
In the preceding picture, you can see a schema on how fine-tuning works on OpenAI pre-built models. The idea is that you have available a pre-trained model with general-purpose weights or parameters. Then, you feed your model with custom data, typically in the form of “key-value” prompts and completions.

{"prompt": "<prompt text>", "completion": "<ideal generated text>"}
{"prompt": "<prompt text>", "completion": "<ideal generated text>"}
{"prompt": "<prompt text>", "completion": "<ideal generated text>"}
...
Once the training is done, you will have a customized model that is particularly performing for a given task, for example classification of your company’s documentations.The nice thing about fine-tuning is that you can make pre-built models tailored to your use cases, without the need to re-train them from scratch, yet leveraging smaller training datasets and hence less training time and compute. At the same time, the model keeps its generative power and accuracy learnt via the original training, the one occurred to the massive dataset.In Chapter 11, we will focus on fine-tuning your model in Python so that you can test it for your own task.On top of the above techniques, there is a fouth one, which is the most “drastic”. It consists of training from scratch an LLM, which you might want to either build on your own, or initializing from a pre-built architecture. We will see how to onboard this approach in the final chapters.

Summary
In this chapter, we explored the field of Large Language Models, with a technical deep dive into their architecture, functioning and training process. We saw the most prominent architectures such as the transformer-based frameworks, how the training process works and different ways to customize your own LLM.We now have the foundation to understand what LLMs are. In next chapter, we will see to use them and, more specifically, how to build intelligent applications with them.

References
Attention is all you need: 1706.03762.pdf (arxiv.org)
Possible End of Humanity from AI? Geoffrey Hinton at MIT Technology Review's EmTech Digital: https://www.youtube.com/watch?v=sitHS6UDMJc&t=594s&ab_channel=JosephRaczynski
GlueBenchmark: https://gluebenchmark.com/
TruthfulQA: https://paperswithcode.com/dataset/truthfulqa
Hugging Face Open LLM Leaderboard: https://huggingface.co/spaces/optimum/llm-perf-leaderboard
Think you have Solved Question Answering? Try ARC, the AI2 Reasoning Challenge: https://arxiv.org/abs/1803.05457

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


1 Introduction to Large Language Models
2 LLMs for AI-powered Applications
3 Choosing an LLM for your application
3h 51m remaining
2 LLMs for AI-powered Applications
Join our book community on Discord
https://packt.link/EarlyAccessCommunity



In chapter 1, we introduced Large Language Models as powerful foundation models with generative capabilities as well as powerful common-sense reasoning. Now the next question is: how should I do with those models?In this chapter, we are going to see how LLMs are revolutionizing the world of software development, leading to a new era of AI-powered applications. By the end of this chapter, you will have a clearer picture of how LLMs can be embedded in different applications scenarios, thanks to new AI orchestrators frameworks that are populating the market of AI development.

Technical requirements
None.

How LLMs are changing software development
Large Language Models have proven to have extraordinary capabilities: from natural language tasks (summarization, named entity recognition, classification) to text generation, from common-sense reasoning to brainstorming skills.However, LLMs are not just incredible by themselves. Large Language Models and, generally speaking, Large Foundation Models (LFMs) are revolutionizing software development by serving as platforms for building powerful applications. In fact, as we saw in chapter 1, the paradigm shift Now the story is different. Instead of starting from scratch, developers can make API calls to a hosted version of an LLM, with the option of customizing it for their specific needs as we saw in the previous chapter. This shift allows teams to incorporate the power of AI more easily and efficiently into their applications, similar to the transition from single-purpose computing to time-sharing in the past. But how does it mean, in concrete, to incorporate LLMs within applications?There are two main aspects to consider when incorporating Large Language Models (LLMs) within applications:

Technical Aspect, which covers the how. Integrating LLMs into applications involves embedding them through REST API calls and managing them with AI orchestrators. This means setting up architectural components that allow seamless communication with the LLMs via API calls. Additionally, using AI orchestrators helps to efficiently manage and coordinate the LLMs' functionality within the application;
Conceptual Aspect, which covers the what. LLMs bring a plethora of new capabilities that can be harnessed within applications. These capabilities will be explored in detail in Part 2 of this book. One way to view LLMs' impact is by considering them as a new category of software, often referred to as Copilot. This categorization highlights the significant assistance and collaboration provided by LLMs in enhancing application functionalities.
We will dwelve into the technical aspect in next paragraph, while next section will cover this brand-new category of software.

The Copilot System
The Copilot system is a new category of software that serves as an expert helper to users trying to accomplish complex tasks. This concept was coined by Microsoft and already introduce into its applications, such as M365 Copilot or the new Bing, now powered by GPT-4. With the same framework and orchestration, developers can now build their own copilots to embed within their applications.But what exactly is a copilot?As the name suggests, copilots are meant to be AI assistant that work side-by-side with users and support them in various activities, from information retrieval to blog writing and posting, from ideas brainstorming to code review and generation.Below some peculiar features of copilots:

A copilot is powered by LLMs or, more generally, LFMs, meaning that these re the reasoning engines that make the copilot “intelligent”. This reasoning engine is one of its components, but not the only one. A copilot also relies on other technologies, such as apps, data sources, and user interfaces, to provide a useful and engaging experience for users.

 
Figure 1: Copilot is powered by LLM
A copilot is designed to have a conversational user interface, allowing users to interact with it using natural language. This reduces or even eliminates the knowledge gap between complex systems which need domain-specific taxonomy (for example, querying tabular data needs the knowledge of programming languages such as T-SQL) and users.

 
Figure 2: An example of conversational UI.
A copilot has a scope. It means that it is grounded to domain-specific data, so that it is entitled to answer only within the perimeter of the application or domain.
Definition

Grounding is the process of using large language models (LLMs) with information that is use-case specific, relevant, and not available as part of the LLM’s trained knowledge. It is crucial for ensuring the quality, accuracy and relevance of the output.

Grounding also helps Copilot to be restricted or scoped to application-specific data, so that it can support only within the boundaries of the provided knowledge base.

Being restricted and scoped also means that the information that is used to ground the LLMs is not stored or used to train the LLMs. The LLMs are trained on a large corpus of public information, but they are not updated or fine-tuned with your data. The information that is used to ground the LLMs is only provided as an input to the LLMs along with your prompt, and it is not retained or shared with anyone else.

For example, let’s consider once again our Grocery Copilot As fun as it can be, we cannot provide users with a copilot they can use planning their summer trip (it would be like providing users with a ChatGPT-like tool at our own hosting cost!); on the contrary, we want the copilot to be grounded to our application database, so that it can respond only if the answer is pertinent with the domain-specific context.

 
Figure 3: Example of grounding a Copilot
The copilot's capabilities can be extended by skills, which can be code or calls to other models. In fact, the LLM (our reasoning engine) might have two kind of limitations:
Limited parametric knowledge. This is due to the knowledge base cutoff date that is a physiological feature of LLM. In fact, their training dataset will always be “outdated”, not in line with the current news. This can be overcome by adding non-parametric knowledge with grounding, as previously seen.
Lack of executive power. This means that LLMs by themselves are not empowered to make actions. Let’s consider for example the well-known ChatGPT: if we ask it to generate a LinkedIn post about productivity tips, we will then need to copy and paste it in our LinkedIn profile as ChatGPT is not able to do so by itself. That is the reason why we need plug-ins. Plug-ins are LLMs’ connector towards the external world that not only serve as input sources to extend LLMs’ non-parametric knowledge (for example, to allow web search), but also as output sources so that the copilot can actually execute actions. For example, with a LinkedIn plug-in, our copilot powered by an LLM will be not only able to generate the post, but also to post it online.
 
Figure 4: Example of Wikipedia and LinkedIn plug-ins.
Note that natural language is not only the way we interact with copilots or, more generally, with LLMs. It is also a crucial component of the backend logic of our LLM-powered applications, within the context of prompt engineering.

Definition

Prompt engineering is the process of designing and optimizing prompts to large language models (LLMs) for a wide variety of applications and research topics. Prompts are short pieces of text that are used to guide the LLM’s output. Prompt engineering skills help to better understand the capabilities and limitations of LLMs.

Prompt engineering involves selecting the right words, phrases, symbols, and formats that elicit the desired response from the LLM. Prompt engineering also involves using other controls, such as parameters, examples, or data sources, to influence the LLM’s behavior. Prompt engineering is an art and a science that requires creativity and attention to detail.

In fact, Andrej Karpathy, the previously Director of AI at Tesla, and returned to OpenAI in February 2023, twitted that “English is the hottest new programming language”.We will dive deeper into the concept of prompt engineering in Chapter 4, while in next paragraph we are going to focus on the emerging AI orchestrators.

How to embed LLMs into applications: introducing AI orchestrators
In the previour paragraph, we saw that there are two main aspects to consider when incorporating Large Language Models within applications: a technical aspect and a conceptual aspect. While we can explain the conceptual aspect with the brand-new category of software called Copilot, in this paragraph we are going to further explore how to technically embed and orchestrate LLMs within our applications.From one side, the paradigm shift of foundation models implies a great simplification in the domain of AI-powered applications: from producing models, now the trend is consuming models. On the other side, many roadblocks might arise in developing with this new kind of AI, since there are LLMs-related components that are brand-new and never been managed before within an application lifecycle.The main components are:

Models. The model is simply the type of LLM we decide to embed in our application. There are two main categories of models:
Proprietary LLMs->models that are owned by specific companies or organizations. Examples include GPT-3 and GPT-4 developed by OpenAI or Bard, developed by Google. As their source code and architecture is not available, those models cannot be re-trained from scratch on custom data, yet they can be fine-tuned if needed.
Open-source->models with code and architecture freely available and distributed, hence they can also be trained from scratch on custom data. Examples include Falcon LLM, developed by Abu Dhabi’s Technology Innovation Institute (TII), or LLaMA, developed by Meta.
We will dive deeper into the main set of LLMs available today in next chapter.

Memory. LLM applications commonly use a conversational interface, which requires the ability to refer back to earlier information within the conversation. This is achieved through a "memory" system that allows the application to store and retrieve past interactions. Note that past interactions could also constitute an additional non-parametric knowledge to be added to the model. To achieve that, it is important to store all the past conversations – properly embedded – into the VectorDB which is at the core of applications data.

Definition

A VectorDB is a type of database that stores and retrieves information based on vectorized embeddings, the numerical representations that capture the meaning and context of text. By using VectorDB, you can perform semantic search and retrieval based on the similarity of meanings rather than keywords. VectorDB can also help LLMs generate more relevant and coherent text by providing contextual understanding and enriching generation results. Some examples of vectorDB are Chroma, FAISS, Elastic Search, Milvus, Pinecone, Qdrant, and Weaviate.

Plug-ins. They can be seen as additional modules or components that can be integrated into the LLM to extend its functionality or adapt it to specific tasks and applications. These plug-ins act as add-ons, enhancing the capabilities of the LLM beyond its core language generation or comprehension abilities.
The idea behind plug-ins is to make LLMs more versatile and adaptable, allowing developers and users to customize the behavior of the language model for their specific needs. Plug-ins can be created to perform various tasks, and they can be seamlessly incorporated into the LLM's architecture.
Prompts. This is probably the most interesting and pivotal component of an LLM-powered application. We’ve already quoted, in the previous section, Andrej Karpathy’s adfirmation that “English is the hottest new programming language”.
“Frontend”, or what the user sees. A “prompt” refer to the input to the model. It is the way the user interact with the application, asking things in natural language;
“Bakcend”, or what the user does not see. Natural Language not only is the way to interact, as an user, with the front-end, but also is it the way we “program” the backend. In fact, on top of the user’s prompt, there are many natural language instructions, or meta-promts, that we give to the model so that it can properly address user’s query. Meta-prompts are meant to instruct the model to act as it is meant to. For example, if we want to limit our application to answer only to questions related to the documentatios we provided in the VectorDB, we will specify in our meta-promts to the model: “Answer only if the question is related to the provided documentation”.
The following is an illustration of the main components of an LLM-powered application:

 
Figure 5: High-level architecture of LLM-powered applications
As you can see from the picture above, the core of the high-level architecture is the AI orchestrator. With AI orchestrator, we refer to lightweight libraries which make it easier to embed and orchestrate LLMs within applications.Since LLMs got viral by the end of 2022, many libraries started arising in the market. In next sections, we are going to focus on three of them: LangChain, Semantic Kernel and HayStack.

LangChain
LangChain was launched as an open-source project by Harrison Chase, in October 2022. It can be used both in Python and JS/TS. LangChain is a framework for developing applications powered by language models, making them data-aware (with grounding) and agentic – that means, able to interact with external environments.LangChain provides modular abstractions for the components necessary to work with language models that we previously mentioned, such as prompts, memory and plug-ins. Alongside those components, LangChain also offer pre-built chains, that are structured contatenations of components. Those chains can be pre-built for specific use cases or also be customized.Overall, LangChain has the following core modules:

Models. These are the Large Language Models or Large Foundation Models that will be the engine of the application. LangChain supports proprietary models, such as those available in OpenAI and Azure OpenAI, and open-source models consumable from the Hugging Face Hub.
Definition

Hugging Face is a company and a community that builds and shares state-of-the-art models and tools for natural language processing and other machine learning domains. It developed the Hugging Face Hub, a platform where people can create, discover, and collaborate on machine learning models and LLMs, datasets, and demos. Hugging Face Hub hosts over 120k models, 20k datasets, and 50k demos in various domains and tasks, such as audio, vision, and language.

Alongside with models, LangChain also offers many prompts-related components that make it easier to manage the prompt flow.

Data connections. These refer to the building blocks needed to retrieve the additional non-parametric knowledge we want to provide the model with. Examples of data connetctions are document loaders or text embedding models.
Memory. It allows the application to keep references to user’s interactions, both in the short and long-term. It is typically based on vectorized embeddings stored into a VectorDB.
Chains. These are predetermined sequences of actions and calls to LLMs that make it easier to build complex applications that require chaining LLMs with each other or with other components. An example of chain might be: take the user query, chunk it into smaller pieces, embed those chunks, search for similar embeddings in a VectorDB, use the top three most similar chunks in the VectorDB as context to provide the answer, generate the answer.
Agents. Agents are entities that drive decision-making within LLMs-powered applications. They have access to a suite of tools and can decide which tool to call based on the user input and the context. Agents are dynamic and adaptive, meaning that they can change or adjust their actions based on the situation or the goal.
In Part 2 of this book, we will go throught a series of hands-on applications, all LangChain based. Henceforth, starting from Chapter 4 we will focus much deeper into LangChain components and overall frameworks.

HayStack
Haystack is a Python-based framework developed by deepset, a startup founded in 2018 in Berlin by Milos Rusic, Malte Pietsch, Timo Möller. Deepset provides developers with the tools to build Natural Language Processing (NLP)-based application, and with the introduction of Haystack they are making it to the next level.Haystack has the following core components:

Nodes. These are components that perform a specific task or function, such as a retriever, a reader, a generator, a summarizer, etc. Nodes can be LLMs or other utilities that interact with LLMs or other resources. Among LLMs, Haystack supports proprietary models, such as those available in OpenAI and Azure OpenAI, and open-source models consumable from the Hugging Face Hub.
Pipelines. These are sequences of calls to nodes that perform natural language tasks or interact with other resources. Pipelines can be querying pipelines or indexing pipelines, depending on whether they perform searches on a set of documents or prepare documents for search. Pipelines are predetermined and hardcoded, meaning that they do not change or adapt based on the user input or the context.
Agent. This is an entity that uses LLMs to generate accurate responses to complex queries. An agent has access to a set of tools, which can be pipelines or nodes, and it can decide which tool to call based on the user input and the context. An agent is dynamic and adaptive, meaning that it can change or adjust its actions based on the situation or the goal.
Tools. There are functions that an agent can call to perform natural language tasks or interact with other resources. Tools can be pipelines or nodes that are available to the agent and they can be grouped into toolkits, which are sets of tools that can accomplish specific objectives.
DocumentStores. Those are backends that store and retrieve documents for search. DocumentStores can be based on different technologies, also including VectorDB (such as FAISS, Milvus, or Elasticsearch).
A nice thing about HayStack is that you can deploy it as a REST API and be consumed directly

Semantic Kernel
Semantic Kernel is the third open-shource SDK we are going to explore in this chapter. It’s been developed by Microsoft, originally in C# and now available also in Python.This framework takes its name over the concept of “kernel” that, generally speaking, refers to the core or essence of a system. In the context of this framework, a kernel is meant to act as the engine that addresses user’s input by chaining and concatenating a series of components into pipelines, encouraging function composition.

Definition

In mathematics, function composition is a way to combine two functions to create a new function. The idea is to use the output of one function as the input to another function, forming a chain of functions. The composition of two functions f and g is denoted as (f o g), where the function g is applied first, followed by the function f->(f o g)(x) = f(g(x)).

Function composition in computer science is a powerful concept that allows for the creation of more sophisticated and reusable code by combining smaller functions into larger ones. It enhances modularity and code organization, making programs easier to read and maintain.

Semantic Kernel has the following main components:

Models. These are the Large Language Models or Large Foundation Models that will be the engine of the application. Semantic Kernel supports proprietary models, such as those available in OpenAI and Azure OpenAI, and open-source models consumable from the Hugging Face Hub.
Memory. It allows the application to keep references to user’s interactions, both in the short and long-term. Within the framework of Semantic Kernel, memories can be accessed in three ways:
Key-value pairs-> it consists in saving environment variables that store simple information, such as names or dates.
Local-storage->it consists in saving information to a file that can be retrieved by its filename, such as a CSV or JSON file.
Semantic memory search-> it is similar to LangChain’s and HayStack’s memory, as it uses embeddings to represent and search for text information based on its meaning.
Functions. Functions can be seen as skills that mix LLM prompts and code, with the goal of making user’s asks interpretable and actionable. There are two types of functions:
Semantic functions-> it is basically a templated prompt, which is a natural language query that specifies the input and output format for the LLM, also incorporating prompt configuration, which sets the parameters for the LLM.
Native functions->those refer to the native computer code that can route the intent captured by the semantic function and permorm the related task.
To make an example, a semantic function could ask the LLM to write a short paragraph about AI, while a native function could actually post it on social media like LinkedIn.

Plug-ins. Those are connectors towards external sources or system that are meant to provide additional information or the ability to perform autonomous actions. Semantic Kernel offers out-of-the-box plug-ins, such as the Microsoft Graph Connector kit, but you can build your custom plug-in by leveraging functions (both native and semantic, or a mix of the two).
Planner. As LLMs can be see as reasoning engine, they can also be leveraged to auto-create chains or pipelines to address new user’s needs. This goal is achieved with a planner, which is a function that takes as input a user’s task and produces the set of actions, plug-ins and functions needed to achieve the goal.
Below an illustration of the anatomy of Semantic Kernel:

 
Figure 6: Anatomy of Semantic Kernel. Source: https://learn.microsoft.com/en-us/semantic-kernel/overview/
Overall, the three frameworks offer, more or less, similar core components, sometimes called with a different taxonomy, yet covering all the blocks illustrated within the concept of copilot system. So a natural question might be: “which one should I use to build my LLM-powered application?” Well, as it might seem elusive, there is no right or wrong answer! All the three are extremely valid. However, there are some features that might be more relevant for specific use cases or developer’s preference. Below some criteria you might want to consider:

The programming language you are comfortable with or prefer to use. Different frameworks may support different programming languages or have different levels of compatibility or integration with them. For example, Semantic Kernel supports C#, Python, and Java, while LangChain and Haystack are mainly based on Python (even thought LangChain also introduced JS/TS support). You may want to choose a framework that matches your existing skills or preferences, or that allows you to use the language that is most suitable for your application domain or environment.
The type and complexity of the natural language tasks you want to perform or support. Different frameworks may have different capabilities or features for handling various natural language tasks, such as summarization, generation, translation, reasoning, etc. For example, LangChain and Haystack provide utilities and components for orchestrating and executing natural language tasks, while Semantic Kernel allows you to use natural language semantic functions to invoke LLMs and services. You may want to choose a framework that offers the functionality and flexibility you need or want for your application goals or scenarios.
The level of customization and control you need or want over the LLMs and their parameters or options. Different frameworks may have different ways of accessing, configuring, and fine-tuning the LLMs and their parameters or options, such as model selection, prompt design, inference speed, output format, etc. For example, Semantic Kernel provides connectors that make it easy to add memories and models to your AI app, while LangChain and Haystack allow you to plug in different components for document store, retriever, reader, generator, summarizer, and evaluator. You may want to choose a framework that gives you the level of customization and control you need or want over the LLMs and their parameters or options.
The availability and quality of the documentation, tutorials, examples, and community support for the framework. Different frameworks may have different levels of documentation, tutorials, examples, and community support that can help you learn, use, and troubleshoot the framework. For example, Semantic Kernel has a website with documentation, tutorials, examples, and a Discord community; LangChain has a GitHub repository with documentation, examples, and issues; Haystack has a website with documentation, tutorials, demos, blog posts, and a Slack community. You may want to choose a framework that has the availability and quality of the documentation, tutorials, examples, and community support that can help you get started and solve problems with the framework.
Feature	LangChain	HayStack	Semantic Kernel
LLM support	Proprietary and Open-source	Proprietary and Open-source	Proprietary and Open-source
Supported Languages	Python and JS/TS	Python	C#, Java and Python
Process orchestration	Chains	Pipelines of nodes	Pipelines of functions
Deployment	No REST API	REST API	No REST API
Memory	Key-value paris, local storage, semantic memory search (embeddings)	Embeddings	Embeddings
Summary
In this chapter, we dwelved into the new way of developing applications that LLMs have been paving, introducing the concept of copilot and encouraging the emerging of new AI orchestrators. Among those, we focused on three projects - LangChain, HayStack and Semantic Kernel – and we examined their features, main components and some criteria to decide which one to pick.Once decided the AI orchestrator, another pivotal step is to decide which LLM(s) we want to embed into our applications. In next Chapter, we are going to see the most prominent LLMs in the market today – both proprietary and open-source – and understand some decision criteria to pick the proper models with respect to the application use cases.

References
https://github.com/langchain-ai/langchain
https://learn.microsoft.com/en-us/semantic-kernel/get-started/supported-languages
https://build.microsoft.com/en-US/sessions/bb8f9d99-0c47-404f-8212-a85fffd3a59d?source=/speakers/ef864919-5fd1-4215-b611-61035a19db6b
https://www.youtube.com/watch?v=E5g20qmeKpg

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


2 LLMs for AI-powered Applications
3 Choosing an LLM for your application
4 Prompt Engineering
3h 32m remaining
3 Choosing an LLM for your application
Join our book community on Discord
https://packt.link/EarlyAccessCommunity



In last chapter, we saw how pivotal is to properly orchestrate LLMs and their components within applications. The next key decision is which LLMs to actually use. In fact, we saw that not all LLMs are created equal. Different LLMs may have different architectures, sizes, training data, capabilities, and limitations. Choosing the right LLM for your application is not a trivial decision, as it can have a significant impact on the performance, quality, and cost of your solution.In this chapter, we will guide you through the process of choosing the right LLM for your application. We will cover the following topics:

Overview of the most promising LLMs in the market
Main criteria and tools to use when comparing LLMs
Trade-offs between size and performance
By the end of this chapter, you should have a clear understanding of how to choose the right LLM for your application and how to use it effectively and responsibly.

Technical requirements
None.

Most promising LLMs in the market
The last few months have witnessed an unprecedented surge in the research and development of LLMs. Several new models have been released or announced by different organizations, each with its own features and capabilities. Some of these models are the largest and most advanced ever created, surpassing the previous state-of-the-art by orders of magnitude. Others are lighter yet more specialized on specific tasks.In this chapter, we will review some of the most promising LLMs in the market as of 2023. We will introduce their background, key findings, and main techniques. We will also compare their performance, strengths, and limitations on various benchmarks and tasks. We will also discuss their potential applications, challenges, and implications for the future of AI and society.

Proprietary models
Proprietary LLMs are developed and owned by private companies, and they are not disclosed with code. They are also typically subject to a fee for consumption.Proprietary models offer a series of advantages, including better support and maintenance as well as sagety and alignment. They also tend to outperform open-source model in terms of generalization, because of their complexity and training datasets. On the other hand, they are “black box”, meaning that owners do not disclose the source code to developers. Plus, they are typically subject to a fee of usage.In next sections, we will cover three of the most popular proprietary LLMs in the market, as for August 2023.

GPT-4
Released in March 2023, GPT-4 is, at the time of writing (December 2023), the latest model developed by OpenAI, as well as the top performer in the market right now.It belongs to the class of Generative Pretrained Transformer (GPT), a decoder-only transforber-based architecture introduced by OpenAI in 2018 with the paper “Language Models are Few-Shot Learners”.GPT-4, as the previous models in the GPT-series, has been trained on both publicly available and OpenAI licensed dataset (OpenAI didn’t disclose the exact composition of the training set). Additionally, to make the model more aligned with user’s intent, the training process also involved a Reinforcement Learning with Human Feedback (RLHF) training.

Definition

Reinforcement Learning with Human Feedback (RLHF) is a technique aims at using human feedbacks as an evaluating metric for LLMs’ generated output, and then using that feedback to further optimize the model. There are two main steps to achieve that goal:

(1) Training a reward model based on human preferences.

(2) Optimizing the LLM with respect to the reward model. This step is done via Reinforcement Learning, is a type of machine learning paradigm where an agent learns to make decisions by interacting with an environment. The agent receives feedback in the form of rewards or penalties based on its actions, and its goal is to maximize the cumulative reward over time by continuously adapting its behavior through trial and error.

With RLHF, thanks to the reward model the LLM is able to learn from human preferences and be more aligned with users’ intents.

GPT-4 demostrated outstanding capabilities in common sense reasoning and analytical skills. It has been benchmarked with state-of-the-art (SOTA) systems, including the MMLU we covered in Chapter 1. On MMLU, GPT-4 outperformed previous models not only in English, but also in other languages.Below an illustration that shows GPT-4 performance on MMLU:

 
Figure 1: GPT-4 3-shot accuracy on MMLU across languages. Source: https://openai.com/research/gpt-4
In addition to MMLU, GPT-4 has been benchmarked on a variety of SOTA systems and acadeimc exams, as you can see from the following picture:

 
Figure 2: GPT performance on academic and professional exams. Source: https://arxiv.org/pdf/2303.08774.pdf
Note: in the above graph you can see two versions of GPT-4: vision and no vision. This is because GPT-4 is a multi-modal models, meaning that it can take as input also images, in addition to text. However, in this chapter we will benchmarking only its textual capabilities.Another great improvement of GPT-4 with respect to its predecessors (GPT-3.5 and GPT-3) is its noticeable reduction in the risk of hallucination.

Definition

Hallucination is a term that describes a phenomenon where large language models (LLMs) generate text that is incorrect, nonsensical, or not real, but appears to be plausible or coherent. For example, an LLM may hallucinate a fact that contradicts the source or the common knowledge, or a name that does not exist, or a sentence that does not make sense.

Hallucination can happen because LLMs are not databases or search engines that store or retrieve factual information. Rather, they are statistical models that learn from massive amounts of text data and produce outputs based on the patterns and probabilities they have learned. However, these patterns and probabilities may not reflect the truth or the reality, as the data may be incomplete, noisy, or biased. Moreover, LLMs have limited contextual understanding and memory, as they can only process a certain number of tokens at a time and abstract them into latent representations. Therefore, LLMs may generate text that is not supported by any data or logic, but is the most likely or correlated from the prompt.

In fact, even thought it is still not 100% reliable, it made great improvements with TruthfulQA benchmarks, which tests the model’s ability to separate fact from incorrect statements (we covered TruthfulQA benchmarks in Chapter 1, under the section “Model evaluation”).Below you can see an illustration that compares GPT-4 results in TruthfulQA benchmark with those of GPT-3.5 (the model behind OpenAI’s ChatGPT) and Anthropic-LM (we will cover this latter model in next sections).

 
Figure 3: Models comparison in TruthfulQA benchmark. Source: https://openai.com/research/gpt-4.
Finally, with GPT-4 OpenAI made an additional effor to make it safer and more aligned, engaging from the beginning a team of over 50 experts in domains like AI alignment risks, privacy, cybersecurity and similar, with the goal of undertanding the extend of the risk of such a powerful model and how to prevent them.

Definition

Alignment is a term that describes the degree to which large language models (LLMs) behave in ways that are useful and harmless for their human users. For example, an LLM may be aligned if it generates text that is accurate, relevant, coherent, and respectful. An LLM may be misaligned if it generates text that is false, misleading, harmful, or offensive.

Thanks to this analysis, further data have been collected and used while training the GPT-4, to mitigate its potential risks, resulting in a reduced risk compared to its predecessor GPT-3.5.

PaLM 2
PaLM 2 is a large language model developed by Google that aims to improve the state of the art in natural language understanding and generation. PaLM 2 stands for Pathways Language Model 2, and it builds on the previous version of PaLM that was released in 2022.

Definition

With the term Pathways, Google refer to the new way of thinking about AI that consists of having one single model to address multiple task. As we saw in chapter 1, the AI “generalization” is a paradigm shift that lead to the evolution, in recent years, of the Foundation models, alongside the Large Language Models we are covering in this book.

PaLM 2 was trained on around 100 spoken languages and over 20 programming languages.The model was perfectioned by merging three disting areas of development in the field of Large Language Models, that cover the topic, respectively, of optimized compute, high-quality training dataset and state-of-the-art architecture. By doing so, Google was able to come up with a model that have the following features:

Compute-optimal scaling. PaLM 2 uses a technique called compute-optimal scaling, which balances the model size and the training data size in proportion to each other. This makes PaLM 2 more efficient and faster than its predecessor PaLM, with fewer parameters and lower serving cost.
Improved dataset mixture. PaLM 2 is trained on a diverse and multilingual corpus of text, which includes hundreds of human and programming languages, mathematical equations, scientific papers, and web pages. This gives PaLM 2 a broader knowledge base and better performance on multilingual tasks, such as translation, cross-lingual transfer, and language proficiency.
On top of that, Google also put a lot of effort in improving PaLM 2 capabilities in its toxicity classification capabilities, adding a built-in control over toxic generation.
Updated model architecture and objective. PaLM 2 has an improved architecture that made it possible to train it on a variety of tasks simultaneously. This allowed the model to learn different aspects of language from different data sources, as well as learn general and transferable skills that can be applied to new tasks.
Overall, PaLM-2 is capable of performing advanced reasoning, coding, and mathematics tasks that require logic, common sense, and creativity. A peculiarity of PaLM-2 is its capability at solving mathematical task. In fact, Google evaluated PaLM-2 across three main evaluation benchmarks focused on maths:

MATH->a test containing 12.500 problems from high-school competitions in 7 maths subject areas.
GSM8K->a dataset of 8.500 grade school math problems.
MGSM->a multilingual version of GSM8K.
Results were stunning, with PaLM-2 surpassing not only state-of-the-art LLMs, such as the GPT-4, but also mathematical fine-tuned, vertical versions of LLMs, such as Minerva (a fine-tuned version of PaLM developed by Google in June 2022).

 
Figure 4: Evaluation results on MATH, GSM8K, and MGSM. Source: https://ai.google/static/documents/palm2techreport.pdf
Google is already powering its products with PaLM 2, including Google Workspace (for example, email summarization in Gmail and content generation in Docs) and Bard (an AI assistant, similar to OpenAI’s ChatGPT).As of today, you can consume PaLM 2 via API, yet you first need to enroll the waitlist at https://makersuite.google.com/waitlist to get access to it. Alternatively, you can try PaLM directly with a chat interface via Bard.

CLAUDE 2
CLAUDE 2, which stands for Constitutional Large-scale Alignment via User Data and Expertise, is an LLM developed by Anthropic, a research company founded by former OpenAI researchers and focused on AI safety and alignment. It was announced in July 2023.CLAUDE 2 is a transformer-based LLM that has been trained on a mix of publicly available information from the internet and proprietary data, via unsupervised learning, Reinforcement Learning with Human Feedback (RLHF) and Constitutional AI.This latter – Constitutional AI (CAI) - is a real peculiarity of CLAUDE. In fact, Anthropic put extraordinary attention into CLAUDE 2 alignment with safety principles. More specifically, Anthropic developed this unique technique called Constitutional AI (CAI), disclosed in December 2022 in the paper “Constitutional AI: Harmlessness from AI Feedback”. Constitutional AI involves using a set of principles to guide the model’s behavior and outputs, rather than relying on human feedback or data alone. The principles are derived from various sources, such as the UN Declaration of Human Rights, trust and safety best practices, principles proposed by other AI research labs, non-western perspectives, and empirical research.Constitutional AI aims to make the model more safe and aligned with human values and intentions, by avoiding toxic or discriminatory outputs, avoiding helping a human engage in illegal or unethical activities, and broadly creating an AI system that is helpful, honest, and harmless.Constitutional AI uses the principles in two stages of the training process:

First, the model is trained to critique and revise its own responses using the principles and a few examples.
Second, the model is trained via reinforcement learning, but rather than using human feedback, it uses AI-generated feedback based on the principles to choose the more harmless output.
The following illustration shows the training process according to CAI technique:

 
Figure 5: CLAUDE’s training process according to CAI technique. Source: https://arxiv.org/abs/2212.08073
Another peculiarity of CLAUDE 2 is the context length, that reaches the 100k tokens. This means that users can input longer prompts, namely pages of technical documentations or even a book, which do not need to be embedded. Plus, the model can also generates longer output compared to other LLMs.Finally, CLAUDE 2 demontrates relevant capabilities also when working with code, scoring 71.2% on the HumanEval benchmark.

Definition

HumanEval is a benchmark for evaluating the code generation ability of large language models (LLMs). It consists of 164 human-crafted coding problems in Python, each with a prompt, a solution, and a test suite. The problems cover various topics, such as data structures, algorithms, logic, math, and string manipulation. The benchmark can be used to measure the functional correctness, syntactic validity, and semantic coherence of the LLM’s outputs.

Overall, CLAUDE 2 is a very interesting model and competitor of GPT-4 to pay attention to. It can be consumed via REST API or directly via Anthropic beta chat experience (limited for US and UK users as for August 2023).

GPT-4	PaLM 2	CLAUDE 2
Company or institution	OpenAI	Google	Anthropic
First release	March 2023	July 2023	July 2023
Architecture	Transformer-based, decoder only	Transformer-based, decoder-only	Transformer-based
Sizes and variants	
Parameters not officially specified.Two context-length variants:

GPT-4 8K tokens
GPT-4 32K tokens
Four sizes, from smallest to largest: Gecko, Otter, Bison and Unicorn. Further details about the number of parameters are not officially specified.	Not officially specified
How to use	REST API at OpenAI developer platforms.Using OpenAI Playground at https://platform.openai.com/playground	REST API after compiling the form at https://makersuite.google.com/waitlist Using Google Bard at https://bard.google.com/	REST API after compiling the form at https://www.anthropic.com/claude
Open-source models
In addition to proprietary models, there is a huge market of open-source LLMs available today. The advantage of an open-source models is that, by definition, developers have full visibility and access to the source code. In the context of LLMs, this implies:

Major control over the architecture, meaning that you can also modify it in the local version you are going to use within your project. This also implies not being prone to potential updates to the source code made by models’ owners.
Possibility to train your model from scratch, on top of the classical fine-tuning, which is also available for proprietary models.
Free to use, meaning that you won’t incur in any charge while using those LLMs, differently from the proprietary ones that have a pay-per-use pricing.
To compare open-source models, throughout this book we will refer to the independent Hugging Face Open LLM leaderboard, a project that aims at evaluating and comparing the performance of LLMs on various NLU tasks. The project is hosted on Hugging Face Spaces, a platform for creating and sharing machine learning applications.The Open LLM leaderboard uses four main evaluation benchmarks, that we have covered in Chapter 1, under the “Model Evaluation” paragraph:

AI2 Reasoning Challenge (ARC)->grade-school science questions and complex NLU tasks.
HellaSwag->commonsense reasoning.
MMLU->various domains tasks including maths, computer science, law.
TruthfulQA->evaluation of how truthful is the model when generating answers.
Even though those are just a subsample of the plethora of LLMs’ benchmarks, we will stick to this leaderboard as a reference evaluation framework as it being widely adopted.

LlaMA-2
LLaMA-2 is a new family of models developed by Meta and unveiled to the public on 18 July, open-source and for free (its first version originally limited to researchers). It is an auto-regressive model with an optimized, decoder-only transformer architecture.

Definition

The concept of auto-regressive in the context of transformers refers to the fact that the model predicts the next token in the sequence, conditioned on all the previous tokens. This is done by masking the future tokens in the input, so that the model can only attend to the past tokens. For example, if the input sequence is “The sky is blue”, the model would predict “The” first, then “sky”, then “is”, and finally “blue”, using a mask to hide the tokens that come after each prediction.

LlaMA-2 models come in three sizes: 7, 13, and 70 billion parameters. All the version have been trained on 2 trillion tokens and have a context lengths of 4092 tokens.On top of that, all model sizes come with a “chat” version, called LlaMA-2-chat. LlaMA-2-chat was developed with a fine-tuning process that consisted into two main steps:

Supervised fine-tuning. This step involves fine-tuning the model on publicly available instruction datasets and over 1 million human annotations, to make them more helpful and safe for conversational use cases. The fine-tuning process uses a selected list of prompts to guide the model outputs, and a loss function that encourages diversity and relevance (that’s the reason why it is “supervised”).
Reinforcement Learning with Human Feedback (RLHF). As we saw while introducing GPT-4, RFHF is a technique aims at using human feedbacks as an evaluating metric for LLMs’ generated output, and then using that feedback to further optimize the model.
Below an illustration of how the training process of LlaMA work:

 
Figure 6: Two-steps fine-tuning to obtain LlaMA 2-chat. Source: https://ai.meta.com/resources/models-and-libraries/llama/
To access the model, you need to submit a request on Meta’s website (the form is available at https://ai.meta.com/resources/models-and-libraries/llama-downloads/). Once submitted, you will receive an email with the GitHub repo where you will be able to download the following assets:

Model code
Model Weights
README (User Guide)
Responsible Use Guide
License
Acceptable Use Policy
Model Card
Falcon LLM
Falcon LLM is a representation of a new trend of LLMs, consisting on building lighter models (with fewer parameters) focusing rather on the quality of the training dataset. Indeed, it is a matter of fact that complex models like GPT-4 with trillion of parameters are extremely heavy, both in the training phase and inference phase. This implies the need for high and expensive computational power (GPU and TPU-powered) as well as long training time.Falcon LLM, is an open-source model launched by Abu Dhabi’s Technology Innovation Institute (TII) in May 2023. It is an auto-regressive, decoder-only transformer, trained on 1 trillion tokens and has 40 billion parameters (even though it has also been released a lighter version with 7 billion parameters). Similarly to what we saw for LlaMA, also Falcon LLM comes with a fine-tuned variant, called “instruct”, which is tailored towards following user’s instructions.

Definition

Instruct models are specialized for short-form instruction following. Instruction following is a task where the model has to execute a natural language command or query, such as “write a haiku about cats” or “tell me the weather in Paris”. The “instruct” fine-tuned models are trained on a large dataset of instructions and their corresponding outputs, such as the Stanford Alpaca dataset.

According to the Open LLM leaderboard, since its launch Falcon LLM has been among the first positions globally, second only to some versions of LlaMA.So the question might be: how can a model with “only” 40 billion parameters perform so well? In fact, the answer is in the quality of the dataset.Falcon was developed using specialized tools and incorporates a unique data pipeline capable of extracting valuable content from web data. The pipeline was designed to extract high-quality content by employing extensive filtering and deduplication techniques.The resulting dataset, called RefinedWeb, has been released by TII under the Apache-2.0 license and can be found at https://huggingface.co/datasets/tiiuae/falcon-refinedweb.By combining superior data quality with these optimizations, Falcon achieves remarkable performance while utilizing around 75% of the training compute budget of the GPT-3 and 80% of PaLM-62B’s.

MPT
The third and last open-source model series we are going to cover is MosaciML Pretrainer Transformer (MPT), developed by MosaicML, a company that provides a platform for training and deploying LLMs. The first version with 7 billion parameters, MPT-7B, was launched in May 2023, alongside some fine-tuned variants (as we saw for the LlaMA series):

MPT-7B-Instruct. A model for short-form instruction following.
MPT-7B-Chat. A chatbot-like model for dialogue generation.
MPT-7B-StoryWriter-65k+. A model designed to read and write stories with super long context lengths, with a context length of 65k tokens. This noticeable length of tokens is achieved thanks to the replacing of positional embedding swith Attention with Linear Biases (ALiBI).
Definition

Attention with Linear Biases (ALiBI) was introduced by Press et al. (2021) in their paper "Train Short, Test Long: Attention with Linear Biases Enables Input Length Extrapolation". It is a positioning method that allows Transformer language models to consume, at inference time, sequences which are longer than the ones they were trained on, due to extrapolation.

ALiBi does this without using actual position embeddings. Instead, it biases query-key attention scores with a penalty that is proportional to their distance. This means that words that are close-by have higher attention values than words that are far away, which reflects the intuition that nearby words are more relevant than distant words.

Then, in June 2023 a new, more complex version with 30 billion parameters was launched: MPT-30B. This latest version has been trained on an initial chunk of 1 trillion tokens with 2k-long sequences, and then an additional 50 billion chunk of tokens with 8k-long sequence. The 8k tokens-long context window allows the model to handle 8k tokens context when consumed, longer than LlaMA or Falcon LLM (around 4k tokens).As per MPT-7B, also this version will offer the two fine-tuned variants of MPT-30B-instruct and MPT-30B-chat.According to MPT-30B original paper, the model is already outperforming OpenAI’s GPT-3, and it is competitive with the aforementioned open-source models, LlaMA and Falcon LLM.Below you can see performance comparison among the three open-source models in different domains:

 
Figure 7: Domains-specific performance benchmark among MPT, LlaMA and Falcon LLM, in different model sizes. Source: https://www.mosaicml.com/blog/mpt-30b
LlaMA	Falcon LLM	MPT
Company or institution	Meta	Technology Innovation Institute (TII)	MosaicML
First release	July 2023	May 2023	May 2023
Architecture	Auto-regressive transformer, decoder-only	Auto-regressive transformer, decoder-only	Transformer, decoder only
Sizes and variants	Three sizes: 7B, 13B and 70B, alongside with fine-tuned version (chat).	Two sizes: 7B, and 40B, alongside with fine-tuned version (instruct)	Two sizes: 7B, and 30B, alongside with fine-tuned version (chat and instruct)
Licenses	A custom commercial license is available at: https://ai.meta.com/resources/models-and-libraries/llama-downloads/	Commercial Apache 2.0 licensed	Commercial Apache 2.0 licensed
How to use	
Submit request form at https://ai.meta.com/resources/models-and-libraries/llama-downloads/ and download the GitHub repo.

Also available in Hugging Face Hub.

Download or Hugging Face Hub Inference API/Endpoint.	Download or Hugging Face Hub Inference API/Endpoint.
Beyond Language Models
Insofar, we have only be covering language-specific foundation models, as it also being the focus of this book. Nevertheless, in the context of AI-powered applications, it is worth mentioning that there are additional foundation models that can handle data different from text, that can be embedded and orchestrated.Below you can find a sample of Large Foundation Models available in the market today:

Whisper. It is is a general-purpose speech recognition model developed by OpenAI that can transcribe and translate speech in multiple languages. It is trained on a large dataset of diverse audio and is also a multitasking model that can perform multilingual speech recognition, speech translation, spoken language identification, and voice activity detection.
Midjourney. Developed by the homonymous independent research lab, Midjourney is based on a Transformer sequence-to-sequence model that takes text prompts and outputs a set of four images that match the prompts. Midjourney is designed to be a tool for artists and creative professionals, who can use it for rapid prototyping of artistic concepts, inspiration, or experimentation.
DALL-E. Similarly to the previous one, DALL-E, developed by OpenAI, generates images from natural language descriptions, using a 12-billion parameter version of GPT-3 trained on a dataset of text-image pairs.
The idea is that we can combine and orchestrate multiple LFMs within our applications to achieve extraordinary results. For example, lets say we want to write a review about an interview with a young chef and post it on Instagram. The involved models might be the following:

Whisper->it will convert the interview audio into a transcript.
An LLM, such as Falcon-7B-instruct, with a web plug-in->it will extrapolate the name of the young chef and search it in the internet to retrieve the biography.
An LLM, such as LlaMA->it will process the transcript and generate a review with an Instagram post-like style. We can ask the same model also to generate a prompt that will ask the following model to generate a picture based on the post content.
Dall-E->it will generate an image based on the prompt generated by the LLM.
We will then provide our LFMs-flow with an Instagram plug-in so that the application is able to post the whole review, including the illustration, on our profile.Finally, there are emerging LFMs that are meant to be multi-modal, meaning that they can handle multiple data-format with just one architecture. An example is the GPT-4 itself. Below you can see some illustrations from OpenAI early experiments with GPT-4 visual:

 
Figure 8: Early experiments with GPT-4 visuals.
 
Figure 9: Early experiments with GPT-4 visuals.
 
Figure 10: Early experiments with GPT-4 visuals.
GPT-4 is just one example of Large Multimodal Models (LMMs), and it is representativeof the trend that we will probably going to witness in next years.

A decision framework to pick the right LLM
In previous paragraphs, we covered some of the most promising Large Language Models available in the market today. Now the question is: which one should I use within my applications?The truth is that there is no a straightforward answer to this question. There are many factors to consider when choosing a large language model (LLM) for your application. Those factors also need to be declined in two scenarios: proprietary and open-source LLMs.Below you can find some factors and trade-offs you might want to consider while choosing your LLMs:

Size and performance. We saw that complex models (that means, with high number of parameters) tend to have better performance, especially in terms of parametric knowledge and generalization capabilities. Nevertheless, the larger the model, the more computation and memory it requires to process the input and generate the output. Which can result in higher latency and, as we will see, in higher costs.
Cost and hosting strategy. When incorporating LLMs within our applications, there are two type of costs we have to have in mind:
Cost for model consumption->it refers to the fee we pay to consume the model. Proprietary models like GPT-4 or CLAUDE 2 require a fee, which is typically proportional to the number of tokens processed. On the other hand, open-source models like LlaMA or Falcon LLM are free to use.
Cost for model hosting->it refers to your hosting strategy. Typically, proprietary models are hosted in private or public hyperscaler, so that they can be consumed via REST API and you don’t have to worry about the underlying infrastructure (for example, GPT-4 is hosted in a super-computer built in Microsoft Azure cloud). With open-source models, we typically need to provide our own infrastructure, since those models can be downloaded locally. Of course, the larger the model, the more powerful the computational power needed.

Note

In the context of open-source model, another option to consume those models is that of using the Hugging Face Inference API. The free version allow you to test and evaluate, with a limited rate, all the available LLMs on a shared infrastructure hosted on Hugging Face. For production use cases, Hugging Face also offers the Inference Endpoints, so that you can easily deploy your LLMs on a dedicated and fully managed infrastructure, with the possibility to configure parameters like region, compute power and security level to accommodate your constraints in terms of latency, throughput and compliance.

Pricing for the Inference Endpoint is publicly available at https://huggingface.co/docs/inference-endpoints/pricing.

Customization. This might be a requirement you want to evaluate before deciding which model to adopt. In fact, not all models are equally flexible in terms of customization. When we talk about customization, we refer to two activities:
Fine-tuning->this is the process of slightly adjusting LLMs’ parameter to better fit into a domain. All open-source models can be fine-tuned. When it comes to proprietary models, not all LLMs can be fine-tuned: for example, OpenAI’s GPT-3.5 can be fine-tuned, while the current version of GPT-4 (as of August 2023) cannot.
Henceforth, it is important to understand whether you will need fine-tuning in your application and decide accordingly.
Training from scratch->if you really want an LLM which is super-specific about your domain knowledge, you might want to retrain the model from scratch. To train an LLM from scratch, without having to re-invent an architecture, you can download open-source LLMs and simply re-train them on custom datasets. Of course, this implies we have access to the source code, which is not the case when we work with proprietary LLMs.
Domain specific capabilities. We saw that the most popular way of evaluating LLMs’ performance is that of averaging different benchmarks across domains. However, there are benchmarks that are tailored towards specific capabilities: if MMLU measure LLMs’ generalized culture and common sense reasoning, TruthfulQA is more concerned around LLMs’ alignment, while HumanEval is tailored towards LLMs’ coding capabilities.
Henceforth, if you have a tailored use case in mind, you might want to use a model that is top performer in one specific benchmark, rather than top performer, on average, across all benchmark. Namely, you might pick CLAUDE 2 if you are looking for exceptional coding capabilities, or PaLM 2 if analytical reasoning is what you are looking for. On the other hand, if you need a model which encompass all the above capabilities, GPT-4 might be the right choice for you.
Note

If you are looking for LLMs that are extremely specific, there is a plethora of models that have been trained on domain-specific technical documentations. For example, at the beginning of 2023, the Stanford Center for Research on Foundation Models (CRFM) and MosaicML announced the release of BioMedLM, a decoder-only transformer-based LLM with 2.7 billion parameters, trained on biomedical abstracts and papers.

Another example is BloombergGPT, a 50 billion parameter LLM specialized for the financial domain developed by Bloomberg and trained on a 363 billion token dataset based on Bloomberg’s extensive data sources, perhaps the largest domain-specific dataset yet, augmented with 345 billion tokens from general purpose datasets.

Picking a domain-specific model is also a way to make some savings in terms of model complexity. The thing is, it might be sufficient for you a relatevily small model (for example, a LlaMA-7B-instruct) if you need to use it for a specific use case, which comes with all the benefits in terms of cost and performance.Note that the the above decision factors are not meant to be an exhaustive guide to decide which models to embed within applications. Nevertheless, those are useful elements of reflection while setting up your application flow, so that you can determine which are your requirements and then shortlist those LLMs that are more suitable for your goals.

Summary
This chapter covered some of the most promising Large Language Models in the market. It first differentiated between proprietary and open-source models, with all the related pros and cons. It then offered a deep dive into the architecture and technical features of GPT-4, PaLM-2, CLAUDE 2, LlaMA-2, Falcon LLM and MPT, with the addition of a section covering some Large Multimodal Models (LMMs).Finally, it provided a light framework to help developers deciding which LLMs to pick while building AI-powered applications.Starting from next chapter, we will begin Part 2 of this book, where we will start working hands-on with LLMs within applications.

References
https://cdn.openai.com/papers/gpt-4.pdf
https://arxiv.org/pdf/2108.12409.pdf
arxiv.org/pdf/2303.08774.pdf
https://arxiv.org/abs/2212.08073
https://huggingface.co/docs/inference-endpoints/index
https://huggingface.co/docs/inference-endpoints/pricing
https://huggingface.co/stanford-crfm/BioMedLM
https://ai.google/static/documents/palm2techreport.pdf
https://arxiv.org/abs/2206.14858

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
4 Prompt Engineering
Join our book community on Discord
https://packt.link/EarlyAccessCommunity



In Chapter 2, we introduced the concept of prompt engineering as the process of designing and optimizing prompts – the text inputs that guides the behaviour of a large language model - to LLMs for a wide variety of applications and research topics.Since prompts have a massive impact on LLMs performance, prompt engineering is a crucial activity while designing LLM-powered applications. In fact, there are several techniques that can be implemented to not only to refine your LLM’s responses, but also to reduce risks associated with hallucination and biases.In this chapter, we are going to cover the emerging techniques in the field of prompt engineering, starting from basic approaches up to advanced frameworks. More specifically, we will go through the following topics:

Introduction to prompt engineering
Basic principles of prompt engineering
Advanced techniques of prompt engineering
Mitigation of risks and hallucinations with prompt engineering
Handling prompt injections
By the end of this chapter, you will have the foundations to build functional and solid prompts for your LLM-powered applications, which will also be relevant in the upcoming chapters.

Technical requirements
OpenAI account and API.
Python 3.7.1 or later version.
What is prompt engineering?
A prompt is a text input that guides the behaviour of an LLM to generate a text output.Prompt engineering is the process of designing effective prompts that elicit high-quality and relevant outputs from LLMs. Prompt engineering requires creativity, understanding of the LLM, and precision.

 
Figure 1: Example of prompts engineering to specialize LLMs.
Principles of prompt engineering
Ww

Clear Instructions
The principle of giving clear instructions is to provide the model with enough information and guidance to perform the task correctly and efficiently. Clear instructions should include the following elements:

The goal or objective of the task, such as “write a poem” or “summarize an article”.
The format or structure of the expected output, such as “use four lines with rhyming words” or “use bullet points with no more than 10 words each”.
The constraints or limitations of the task, such as “do not use any profanity” or “do not copy any text from the source”.
The context or background of the task, such as “the poem is about autumn” or “the article is from a scientific journal”.
Let’s say, for example, that we want our model to fetch any kind of instructions from text and return to us a tutorial in a bullet list. Plus, if there are no instructions in the provided text, the model should inform us about that. As first thing, we need to initialize our model. For this purpose, we are going to leverage OpenAI’s GPT-3.5-turbo model.

response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": instructions},
    ]
)
As you can see, the chat model comes with a system message (or metaprompt) where we can put our instructions. Then, it takes the user’s query (in this case, the text instructions).For this scenarios, I set the two variables system_message and instructions as follows:

system_message = """
You are an AI assistant that helps human by generating tutorials given a text.
You will be provided with a text. If the text contains any kind of istructions on how to proceed with something, generate a tutorial in a bullet list.
Otherwise, inform the user that the text does not contain any instructions.
Text: 
"""
instructions = """
To prepare the known sauce from Genova, Italy, you can start by toasting the pine nuts to then coarsely 
chop them in a kitchen mortar together with basil and garlic. Then, add half of the oil in the kitchen mortar and season with salt and pepper.
Finally, transfer the pesto to a bowl and stir in the grated Parmesan cheese.
"""
Now let’s test our model:

print(response['choices'][0]['message']['content'])
Output:

Sure, I can generate a tutorial based on the given text. Here's a bullet list on how to prepare the Genovese pesto sauce:
- Toast the pine nuts on a pan until they are slightly browned.
- Coarsely chop the toasted pine nuts, along with basil leaves and garlic cloves, using a kitchen mortar.
- Add half of the olive oil into the kitchen mortar, and season the mixture with salt and pepper.
- Grind the mixture until it becomes a smooth paste.
- Transfer the pesto to a bowl, and stir in the grated Parmesan cheese.
- You can add more olive oil to achieve the desired consistency for the sauce.
- Your Genovese pesto sauce is now ready. It can be served with pasta, vegetables, or as a dip for bread. Enjoy!
Note that, if we pass the model another text which does not contain any instructions, it will be able to respond as we instructed it:

response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": 'the sun is shining and dogs are running on the beach.'},
    ]
)
#print(response)
print(response['choices'][0]['message']['content'])
Output:

As there are no instructions provided in the text you have given me, it is not possible to create a tutorial. May I have a different text to work with?
By giving clear instructions, you can help the model understand what you want it to do and how you want it to do it. This can improve the quality and relevance of the model’s output, and reduce the need for further revisions or corrections.However, sometimes there are scenarios where clarity is not enough. We might need to infer the way of thinking of our LLM to make it more robust with respect to its task. In next section, we are going to examine one of this techniques, very useful in case of complext tasks to accomplish.

Split complex tasks into subtasks
Prompt engineering is a technique that involves designing effective inputs for large language models (LLMs) to perform various tasks. Sometimes, the tasks are too complex or ambiguous for a single prompt to handle, and it is better to split them into simpler subtasks that can be solved by different prompts. Here are some examples of splitting complex tasks into subtasks:

Text summarization: A complex task that involves generating a concise and accurate summary of a long text. This task can be split into subtasks such as:
Extracting the main points or keywords from the text.
Rewriting the main points or keywords in a coherent and fluent way.
Trimming the summary to fit a desired length or format.
Machine translation: A complex task that involves translating a text from one language to another. This task can be split into subtasks such as:
Detecting the source language of the text.
Converting the text into an intermediate representation that preserves the meaning and structure of the original text.
Generating the text in the target language from the intermediate representation.
Poem generation: A creative task that involves producing a poem that follows a certain style, theme, or mood. This task can be split into subtasks such as:
Choosing a poetic form (such as sonnet, haiku, limerick, etc.) and a rhyme scheme (such as ABAB, AABB, ABCB, etc.) for the poem.
Generating a title and a topic for the poem based on the user’s input or preference.
Generating the lines or verses of the poem that match the chosen form, rhyme scheme, and topic.
Refining and polishing the poem to ensure coherence, fluency, and originality.
Code generation: A technical task that involves producing a code snippet that performs a specific function or task. This task can be split into subtasks such as:
Choosing a programming language (such as Python, Java, C++, etc.) and a framework or library (such as TensorFlow, PyTorch, React, etc.) for the code.
Generating a function name and a list of parameters and return values for the code based on the user’s input or specification.
Generating the body of the function that implements the logic and functionality of the code.
Adding comments and documentation to explain the code and its usage.
Let’s consider the following example in Python, leveraging OpenAI’s GPT-3.5-turbo model:

import os
import openai
openai.api_key = os.environment[“OPENAI_API_KEY”]
response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": article},
    ]
)
Let’s set both the system_message and article variables as follows (you can find the entire scripts at the book’s GitHub repository):

system_message = """
You are an AI assistant that summarize articles. 
To complete this task, do the following subtasks:
Read the provided article context comprehensively and identified the main topic and key points
Generated a paragraph summary of the current article context that captures the essential information and conveys the main idea
Print each step of the proces.
Article:
"""
article = """
Recurrent neural networks, long short-term memory and gated recurrent neural networks
in particular, […]
"""
To see the output, you can run the following code:

print(response['choices'][0]['message']['content'])
Output:

Summary: 
The article discusses the use of recurrent neural networks, specifically long short-term memory and gated recurrent neural networks, in sequence modeling and transduction problems. These models have achieved great success but are limited by their inherently sequential nature. Attention mechanisms have become popular in addressing this issue but are usually used in conjunction with recurrent networks. The authors propose the Transformer, an architecture that relies solely on attention mechanisms instead of recurrence. The Transformer allows for greater parallelization and can achieve state-of-the-art results in machine translation after only twelve hours of training on eight GPUs. 
Steps:
1. The article discusses the success and limitations of recurrent neural networks in sequence modeling and transduction problems. 
2. Attention mechanisms have become popular in addressing the limitations of recurrence but are usually used alongside recurrent networks. 
3. The authors propose the Transformer, a model architecture that relies solely on attention mechanisms and allows for greater parallelization. 
4. The Transformer can achieve state-of-the-art results in machine translation after only twelve hours of training on eight GPUs.
As you can see, the model was able to produce a high-quality summary based on the key topics extracted (and displayed) from the given article.Splitting complex tasks into easier sub-tasks is a powerful technique, nevertheless it does not address one of the main risks of LLM-generated content, that is, having a wrong output. In next two sections, we are going to see some techniques that are mainly aimed at addressing this risk.

Ask for justification
LLMs are built in such a way that they predict the next token based on the previous ones without looking back at their generations. This might lead the model to output wrong content to the user, yet in a very convincing way. If the LLM-powered application does not provide specific reference to that response, it might be hard to validate the ground truth behind it.Henceforth, specifying in the prompt to support the LLM’s answer with some reflections and justification could prompt the model to recover from its actions. Furthermore, asking for justification might be useful also in case of answers that are right, but simply we don’t know the LLM thought process behind it. For example, let’s say we want our LLM to solve riddles. To do so, we can instruct it as follows:

system_message = """
You are an AI assistant specialized in solving riddles.
Given a riddle, solve it the best you can.
Provide a clear justification of your answer and the reasoning behind it.
Riddle:
"""
As you can see, I’ve specified in the metaprompt to the LLM to justify its answer and also socializing its reasoning. Let’s see how it works:

riddle = """
What has a face and two hands, but no arms or legs?
"""
response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", 
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": riddle},
    ]
)
#print(response)
print(response['choices'][0]['message']['content'])
Output:

The answer to this riddle is a clock. 
A clock has a face with numbers and two hands (the hour and minute hand), which rotate around the center of the clock to show the time. Although it doesn't have any arms or legs like humans do, it still has the ability to measure time, which is important in our daily lives. 
Hence, a clock is the correct answer to this riddle.
Justifications are a great tool to make your model more reliable and robust, since they “force” it to re-think about its output, as well as providing us with a view of how the reasoning was set to solve the problem. With a similar approach, we could also intervene at different prompts level to improve our LLM’s performance. For example, we might discover that the model is systematically tackling a mathematical problem in the wrong way, henceforth we might want to suggest the right approach directly at the metaprompt level. Another example might be that of asking the model to generate multiple outputs – along with their justifications – to evaluate different reasoning techniques and prompt the best one in the metaprompt.In next section, we are going to focus on one of this example, more specifically the possibility of generating multiple outputs and then picking the most likely one.

Generate many outputs, then use the model to pick the best one
As we saw in the previous section, LLMs are built in such a way that they predict the next token based on the previous ones without looking back at their generations. If this is the case, if one sampled token is the wrong one (in other words, if the model is unlucky), the LLM will keep generating wrong tokens and, henceforth, wrong content. Now, the bad news is that, unlike humans, LLMs cannot recover from errors on their own. It means that, if we ask them, they aknowledge the error, but we need to explicitly prompt them to think about that.One way to overcome this limitation is that of broadening the space of probabilities of picking the right token. Rather than generating just one response, we can prompt the model to generate multiple response, and then picking the one which is most suitable for the user’s query. This splits the job into two sub-jobs for our LLM:

Generating multiple responses to user’s query;
Comparing those responses and picking the best one, according to some criteria we can specify in the metaprompt.
Let’s see an example, following up with the riddles examined in the previous section.

system_message = """
You are an AI assistant specialized in solving riddles.
Given a riddle, you have to generate three answers to the riddle.
For each answer, be specific about the reasoning you made.
Then, among the three answer, select the one which is most plausible given the riddle.
Riddle:
"""
riddle = """
What has a face and two hands, but no arms or legs?
"""
In this case, I’ve prompted the model to generate three answers to the riddle, then to give me the most likely, justifying why. Let’s see the result:

response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": riddle},
    ]
)
#print(response)
print(response['choices'][0]['message']['content'])
Output:

Answer 1: A clock. A clock has a face with numbers and two hands to show minutes and hours. It does not have arms or legs because it is an object, and it does not have intrinsic limbs.
Answer 2: A watch. Similar to a clock, a watch also has a face with numbers and two hands to indicate the time. Although it is usually worn on a person's wrist, it does not have arms or legs.
Answer 3: A wall. While this answer may be less obvious, a wall does, in a way, have a face and two hands. The face is its outer surface, and the hands are the clock that usually hangs on the wall. 
Among the three answers, the most plausible one is answer 1: a clock. The riddle distinctly mentions "two hands" and it's logical to associate hands with those that are found in clocks to indicate time.
As aforementioned, forcing the model to tackle a problem with different approaches is a way to collect multiple samples of reasonings, which might serve as further instructions in the metaprompt. For example, if we want the model to always propose us something which is not the most straightforward solution to a problem – in other words, if we want it to “think differently” – we might force it to solve a problem in N ways and then use the most creative reasoning as framework in the metaprompt.The last element we are going to examine is the overall structure we want to give to our metaprompt. In fact, in previous examples, we saw a sample system message with some statements and instructions. In next section, we will see how the order and “strength” of those statements and instructions is not an invariant.

Repeat instructions at the end
Large Language Models tend not to process the metaprompt attributing the same weight or imprortance to all the sections. In fact, in his blog post “Large Language Model Prompt Engineering for Complex Summarization”, Microsoft’s Software Engineer John Stewart found out some interesting outcomes from arranging prompt sections. More specifically, after several experimentations, he found that repeating the main instruction at the end of the prompt can help the model to overcome its inner recency bias.

Definition

Recency bias is the tendency of large language models to give more weight to the information that appears near the end of a prompt, and ignore or forget the information that appears earlier. This can lead to inaccurate or inconsistent responses that do not take into account the whole context of the task. For example, if the prompt is a long conversation between two people, the model may only focus on the last few messages and disregard the previous ones.

One possible way to overcome recency bias is to break down the task into smaller steps or subtasks, and provide feedback or guidance along the way. This can help the model focus on each step and avoid getting lost in irrelevant details. We’ve covered this technique in the previous section about splitting complex tasks into easier subtasks.Another way to overcome recency bias with prompt engineering techniques is to repeat the instructions or the main goal of the task at the end of the prompt. This can help remind the model of what it is supposed to do and what kind of response it should generate. For instance, let’s say we want our model to output the sentiment of a whole chat history between an AI agent and the user. We want to make sure that the model will output the sentiment in lower cap and without punctuation. Let’s consider the following example (the conversation is truncated, you can find the whole code at the book’s GitHub repository).

system_message = """
You are a sentiment analyzer. You classify conversations into three categories: positive, negative or neutral.
Return only the sentiment, in lower cap and without punctuation.
Conversation:
"""
conversation = """
Customer: Hi, I need some help with my order.
AI agent: Hello, welcome to our online store. I'm an AI agent and I'm here to assist you. 
Customer: I ordered a pair of shoes yesterday, but I haven't received a confirmation email yet. Can you check the status of my order?
[…]
"""
In this case, the key instruction is that of having as output only the sentiment in lower cap and without punctuation. In this scenario, we have key instruction before the conversation, and the output looks like so:

response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": conversation},
    ]
)
#print(response)
print(response['choices'][0]['message']['content'])
Output:

Neutral
The model didn’t follow the instruction of having only lower letters. Let’s try to repeat the instruction also at the end of the prompt:

system_message = f"""
You are a sentiment analyzer. You classify conversations into three categories: positive, negative or neutral.
Return only the sentiment, in lower cap and without punctuation.
Conversation:
{conversation}
Remember to return only the sentiment, in lower cap and without punctuation
"""
The output looks like the following:

response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "user", "content": system_message},
    ]
)
#print(response)
print(response['choices'][0]['message']['content'])
Output:

neutral
As you can see, now the model was able to output exactly the output we desired. This approach is particularly useful whenever we have a conversation history to keep storing in the context window. If this is the case, having the main instructions at the beginning might induce the model not to have them in mind once it also goes through the whole history, hence reducing their strength.

Use delimiters
The last principle to be covered is related to the format we want to give to our meta prompt. This helps our LLM to better understand its intents as well as making relations among sections and paragraphs. To achieve this, we can use delimiters within our prompt. A delimiter can by any sequence of characters or symbols that is clearly mapping a schema rather than a concept. For example, we can consider delimiters the following sequences:

>>>>
====
------
####
` ` ` ` `
And so on. Let’s consider, for example, a meta prompt that aims at instructing the model to translate user’s tasks into Python code, providing also an example to do so.

system_message = """
You are a Python expert that produces python code as per user's request.
===>START EXAMPLE
---User Query---
Give me a function to print a string of text.
---User Output---
Below you can find the described function:
```def my_print(text):
     return print(text)
```
<===END EXAMPLE
"""
query = "generate a python function to calculate the nth Fibonacci number"
Let’s see how it works:

response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": query},
    ]
)
#print(response)
print(response['choices'][0]['message']['content'])
Output:

 
Figure 2: Sample output of a model using delimiters in the system message.
As you can see, it also printed the code in backsticks as showed within the system message.All the principles examined up to this point are general rules that can make your LLM-powered application more robust. In next sections, we are going to see some advanced techniques for prompt engineering that address the way the model reason and think to the answer, before providing it to the final user.

Advanced techniques
In previous sections, we covered some basics techniques of prompt engineering. Those techniques should be kept in mind regardless of the type of application your are developing, since are general best practices that improve your LLM performance anyway.On the other hand, there are some advanced techniques which might be implemented for specific scenarios, that we are going to cover in the upcoming sections.

Few-shot approach
In their paper “Language Models are Few-Shot Learners”, the authors demonstrate that GPT-3 can achieve strong performance on many NLP tasks in a few-shot setting. This means that for all tasks, GPT-3 is applied without any fine-tuning, with tasks and few-shot demonstrations specified purely via text interaction with the model.This is an example and evidence of how the concept of few-shot learning – which means, providing the models with examples of how we would like it to respond – is a powerful techniques that enables models’ customization without interfering with their overall architecture.For example, let’s say we want our model to generate a tagline for a new product line of climbing shoes we’ve just coined – Elevation Embrace. We have an idea of how the tagline should be like – concise and direct. We could explain it to the model in plain text, however it might be more effective simply to provide it with some examples of similar projects.Let’s see an implementation with code:

system_message = """
You are an AI marketing assistant. You help users to create taglines for new product names.
Given a product name, produce a tagline similar to the following examples:
Peak Pursuit - Conquer Heights with Comfort
Summit Steps - Your Partner for Every Ascent
Crag Conquerors - Step Up, Stand Tal
Product name:
"""
product_name = 'Elevation Embrace'
Let’s see how our model will handle this request:

response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": product_name},
    ]
)
#print(response)
print(response['choices'][0]['message']['content'])
Output:

Tagline idea: Embrace the Heights with Confidence.
As you can see, it maintained the style, length and also writing convetion of the provided taglines. This is extremely useful when you want your model to follow examples you already have, such as fixed templates.Note that few shot learning, most of the time, is powerful enough to customize a model even if extremely specialized scenarios, where we could think about fine tuning as the proper tool. In fact, a proper few shot learning could be as effective as a fine tuning process.For example, let’s say we want to specialize a model for sentiment analysis. To do so, we provide it with a series of examples of texts with different sentiments, alongside the output we would like – positive or negative. Note that this set of examples is nothing but a small training set for a supervised learning tasks: the only difference from fine tuning is that we are not updating the model’s parameters.To provide you with a concrete representation of what said above, let’s provide our model with just two examples for each label:

system_message = """
You are a binary classifier for sentiment analysis.
Given a text, based on its sentiment you classify it into one of two categories: positive or negative.
You can use the following texts as examples:
Text: "I love this product! It's fantastic and works perfectly."
Positive
Text: "I'm really disappointed with the quality of the food."
Negative
Text: "This is the best day of my life!"
Positive
Text: "I can't stand the noise in this restaurant."
Negative
ONLY return the sentiment as output (without punctuation).
Text:
"""
To test our classifier, I’ve used the IMDB of movies’ reviewes available on Kaggle at https://www.kaggle.com/datasets/yasserh/imdb-movie-ratings-sentiment-analysis/code.

import numpy as np
import pandas as pd
df = pd .read_csv('movie.csv', encoding='utf-8')
df['label'] = df['label'].replace({0: 'Negative', 1: 'Positive'})
df.head()
As you can see, the dataset contains many movies’ reviews along with their associated sentiment – positive or negative. Now, we want to test the performance of our model over a sample of 10 observations of this dataset.

df = df.sample(n=10, random_state=42)
def process_text(text):
    response = openai.ChatCompletion.create(
        engine="gpt-35-turbo", 
        messages=[
            {"role": "system", "content": system_message},
            {"role": "user", "content": text},
        ]
    )
    return response['choices'][0]['message']['content']
df['predicted'] = df['text'].apply(process_text)
print(df)
Output:

 
Figure 3: Output of a GPT-3.5 model with few shot examples.
As you can see, the model was able to correctly classify all the reviews, without even fine tuning!This is just an example of what you can achieve – in terms of model specialization – with the technique of few shot learning.

Chain of Thoughts
Introduced in the paper “Chain-of-Thought Prompting Elicits Reasoning in Large Language Models” by Wei et al., Chain of thought (CoT) is a technique that enables complex reasoning capabilities through intermediate reasoning steps. It also encourages the model to explain its reasoning, “forcing” it not to be too fact and risking to give the wrong response (as we saw in previous sections).Let’s say that we want to prompt our LLM to solve first-degree equations. To do so, we are going to provide it with a generic reasoning list that it might want to follow:

system_message = """
To solve a generic first-degree equation, follow these steps:
1. **Identify the Equation:** Start by identifying the equation you want to solve. It should be in the form of "ax + b = c," where 'a' is the coefficient of the variable, 'x' is the variable, 'b' is a constant, and 'c' is another constant.
2. **Isolate the Variable:** Your goal is to isolate the variable 'x' on one side of the equation. To do this, perform the following steps:
   
   a. **Add or Subtract Constants:** Add or subtract 'b' from both sides of the equation to move constants to one side.
   
   b. **Divide by the Coefficient:** Divide both sides by 'a' to isolate 'x'. If 'a' is zero, the equation may not have a unique solution.
3. **Simplify:** Simplify both sides of the equation as much as possible.
4. **Solve for 'x':** Once 'x' is isolated on one side, you have the solution. It will be in the form of 'x = value.'
5. **Check Your Solution:** Plug the found value of 'x' back into the original equation to ensure it satisfies the equation. If it does, you've found the correct solution.
6. **Express the Solution:** Write down the solution in a clear and concise form.
7. **Consider Special Cases:** Be aware of special cases where there may be no solution or infinitely many solutions, especially if 'a' equals zero.
Equation:
"""
Let’s see how it works:

equation = "3x + 5 = 11"
response = openai.ChatCompletion.create(
    engine="gpt-35-turbo", # engine = "deployment_name".
    messages=[
        {"role": "system", "content": system_message},
        {"role": "user", "content": equation},
    ]
)
#print(response)
print(response['choices'][0]['message']['content'])
Output:

 
Figure 4: Output of the model solving an equation with CoT approach.
Note that you can also combine combine it with few-shot prompting to get better results on more complex tasks that require reasoning before responding. With CoT, we are prompting the model to generate intermediate reasoning steps. This is also a component of another reasoning technique that we are going to examine in next section.

ReAct
Introduced in the paper “ReAct: Synergizing Reasoning and Acting in Language Models” by Yao et al., ReAct (Reason and Act) is a general paradigm that combines reasoning and acting with large language models. ReAct prompts the language model to generate verbal reasoning traces and actions for a task, and also receives observations from external sources such as web search or databases. This allows the language model to perform dynamic reasoning, and quickly adapt its acting plan based on external information. For example, you can prompt the language model to answer a question by first reasoning about the question, then performing an action to send a query to the web, then receiving an observation from the search results, and then continuing with this thought, action, observation loop until it reaches a conclusion.The difference between chain of thought and ReAct approaches is that chain of thought prompts the language model to generate intermediate reasoning steps for a task, while ReAct prompts the language model to generate intermediate reasoning steps, actions, and observations for a task. Note that the “action” phase is generally related to the possibility for our LLM to interact with external tools, such as the web search.For example, let’s say we want to ask our model some up-to-date information about the upcoming Olympics game. To do so, we are going to build a smart LangChain Agent (as described in Chapter 2). I won’t dive deeper into each component of the following code, since next Chapter will be entirely focused on LangChain and its main components.

import os
from dotenv import load_dotenv
from langchain import SerpAPIWrapper
from langchain.agents import AgentType, initialize_agent
from langchain.chat_models import ChatOpenAI
from langchain.tools import BaseTool, StructuredTool, Tool, tool
from langchain.schema import HumanMessage
model = ChatOpenAI(
    model_name='gpt-35-turbo'
)
load_dotenv()
key = os.environ["SERPAPI_API_KEY"]
search = SerpAPIWrapper()
tools = [
    Tool.from_function(
        func=search.run,
        name="Search",
        description="useful for when you need to answer questions about current events"
    )
    ]
agent_executor = initialize_agent(tools, model, agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION, verbose=True)
As you can see, for this purpose I’ve used a pre-built agent type available in LangChain, called ZERO_SHOT_REACT_DESCRIPTION. It comes with a pre-compiled prompt that follows the ReAct approach. Let’s inspect that:

print(agent_executor.agent.llm_chain.prompt.template)
Output:

Answer the following questions as best you can. You have access to the following tools:
Search: useful for when you need to answer questions about current events
Use the following format:
Question: the input question you must answer
Thought: you should always think about what to do
Action: the action to take, should be one of [Search]
Action Input: the input to the action
Observation: the result of the action
... (this Thought/Action/Action Input/Observation can repeat N times)
Thought: I now know the final answer
Final Answer: the final answer to the original input question
Begin!
Question: {input}
Thought:{agent_scratchpad}
Let’s now test our agent asking something about the upcoming Olympics games:


Output:

‘Matteo Zurloni is one of the Italian male climbers who has secured a spot at the Paris 2024 Olympics, but a comprehensive list of Italian male climbers for the Olympics is not readily available.’
At the time of this question (7th of October 2023), the answer is definitely correct. Note how the model went through several iterations of Observation/Thought/Action, until it reached the final conclusion. This is a great example of how prompting a model to think step by step and explicit each step of the reasoning makes it “wiser” and cautious before answering. It is also a great technique to prevent hallucination.Overall, prompt engineering is a powerful discipline, still in its emerging phase yet already widely adopted within LLM-powered applications. In next Chapters, we are going to see concrete applications of this techniques.

Summary
In this chapter, we covered many aspects of the activity of prompt engineering, a core step in the context of improving the performance of LLMs within your application, as well as custimizing it depending on the scenario.We started with an introduction to the concept of prompt engineering and why it is important, to then move towards the basic principles – including clear instructions, asking for justification etc.Then, we moved towards more advanced techniques, which are meant to shape the reasoning approach of our LLM: few-shot learning, CoT and ReAct.Prompt engineering is an emerging discipline which is paving the way for a new category of applications, infused with LLMs. In next chapters, we will see those techniques in action building real-world applications using LLMs.

References
ReAct approach. https://arxiv.org/abs/2210.03629
Chain of Thoughts approach. https://arxiv.org/abs/2201.11903
What is prompt engineering. https://www.mckinsey.com/featured-insights/mckinsey-explainers/what-is-prompt-engineering
Prompt engineering techniques. https://blog.mrsharm.com/prompt-engineering-guide/
Prompt engineering principles. https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/advanced-prompt-engineering?pivots=programming-language-chat-completions
Recency bias. https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/advanced-prompt-engineering?pivots=programming-language-chat-completions#repeat-instructions-at-the-end
Large Language Model Prompt Engineering for Complex Summarization. https://devblogs.microsoft.com/ise/2023/06/27/gpt-summary-prompt-engineering/
Language Models are Few-Shot Learners. https://arxiv.org/pdf/2005.14165.pdf
IMDB dataset. https://www.kaggle.com/datasets/yasserh/imdb-movie-ratings-sentiment-analysis/code
ReAct. https://arxiv.org/abs/2210.03629
Chain of Thoughts. https://arxiv.org/abs/2201.11903

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

back
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


4 Prompt Engineering
5 Embedding LLMs within your Applications
6 Building Conversational applications
2h 36m remaining
5 Embedding LLMs within your Applications
Join our book community on Discord
https://packt.link/EarlyAccessCommunity



This chapter opens Part 2 of the book, and it will kickstart the hands-on sections. In this chapter, we will cover the following topics:

Deep dive into LangChain and how to use it
Calling open-source LLM API into code via Hugging Face Hub
Managing prompt engineering
By the end of this chapter, you will have the technical foundations to start developing your LLM-powered applications using LangChain and open-source Hugging-Face models.

Technical requirements
To complete the hands-on sections of this chapter, the following pre-requisites are needed:

Hugging Face account and user access token.
OpenAI account and user access token.
Python 3.7.1 or later version.
Python packages. Make sure to have the following Python packages installed: langchain, python-dotenv, huggingface_hub. Those can be easily installed via pip install in your terminal.

Getting started with LangChain
As introduced in Chapter 2, LangChain is a lightweight framework meant to make it easier to integrate and orchestrate LLMs’ and their components within applications. It is mainly Python based, yet it recently extended its support to JavaScript and TypeScript.In addition to Large Language Models integration (which we will cover in the upcoming dedicated paragraph), we saw that LangChain offer the following main components:

Models and prompt templates
Data Connections
Memory
Chains
Agents
 
Figure 1: LangChain’s components.
Next sections will be a deep dive for each of these components.

Models and Prompts
LangChain offers more than 50 integrations towards third-party vendor and platforms, including OpenAI, Azure OpenAI, Databricks and MosaicML, as well as the integration with Hugging Face Hub and the world of open-source LLMs. In Part 2 of this book, we will be trying various LLMs, both proprietary and open-source, leveraging those LangChain’s integrations.Just to provide an example, let’s see how easy is to consume the OpenAI GPT-3 model (you can retrieve your OpenAI API key at https://platform.openai.com/account/api-keys):

from langchain.llms import OpenAI
llm = OpenAI(openai_api_key="your-api-key")
print(llm('tell me a joke'))
Output:

Q: What did one plate say to the other plate?
A: Dinner's on me!
Note that, by default, the module OpenAI use the GPT-3 (or text-davinci-003) as base model. You can specify the model you want to use by passing the model’s name as a parameter.As said, we will dive deeper into LLM’s in next paragraph; henceforth, let’s focus on prompts.There are two main components related to LLM’s prompts and prompts’ design/engineering:

Prompt templates. A prompt template is a component that defines how to generate a prompt for a language model. It can include variables, placeholders, prefixes, suffixes, and other elements that can be customized according to the data and the task.
For example, suppose you want to use a language model to generate translation from one language to another. You can use a prompt template like this:

Sentence: {sentence}
Translation in {language}:
The {sentence} is a variable that will be replaced by the actual text. The Translation in {language}: is a prefix that indicates the task and the expected output format.You can easily implement this template as follows:

from langchain import PromptTemplate
template = """Sentence: {sentence}
Translation in {language}:"""
prompt = PromptTemplate(template=template, input_variables=["sentence", "language"])
print(prompt.format(sentence = "the cat is on the table", language = "spanish"))
Output:

Sentence: the cat is on the table
Translation in spanish:
Generally speaking, prompt templates tend to be agnostic with respect to the LLM you might decide to use, and it is adaptable to both completion and chat models.

Definition

A completion model is a type of LLM that takes a text input and generates a text output, called a completion. The completion model tries to continue the prompt in a coherent and relevant way, according to the task and the data it was trained on. For example, a completion model can generate summaries, translations, stories, code, lyrics, and more, depending on the prompt.

A chat model is a special kind of completion model that is designed to generate conversational responses. A chat model takes a list of messages as input, where each message has a role (either system, user, or assistant) and content. The chat model tries to generate a new message for the assistant role, based on the previous messages and the system instruction.

The main difference between completion and chat models is that completion models expect a single text input as prompt, while chat models expect a list of messages as input.

Example selector. An example selector is a component in LangChain that allows you to choose which examples to include in a prompt for a language model. A prompt is a text input that guides the language model to produce a desired output. Examples are pairs of inputs and outputs that demonstrate the task and the format of the output. 
The idea recalls the concept of few-shot learning we covered in chapter 1.
LangChain offers the Example Selector class called BaseExampleSelector that you can import and modify as you whish. You can find the API reference at https://python.langchain.com/docs/modules/model_io/prompts/example_selectors/.
Data connections
Data connections refer to the building blocks needed to retrieve the additional non-parametric knowledge we want to provide the model with. The idea is that of covering the typical flow of incorporating user-specific data into applications that made of five main blocks, as illustrated in the following picture:

 
Figure 2: Incorporating user-specific knowledge into LLMs. Source: https://python.langchain.com/docs/modules/data_connection/
Those blocks are addressed with the following LangChain tools:

Document loaders. They are in charge of loading documents from different sources such as CSV, File Directory, HTML, JOSN, Markdown and PDF. Document loaders expose a .load method for loading data as documents from a configured source. The output is a Document object that contains a piece of text and associated metadata.
For example, let’s consider a sample CSV file to be loaded (you can find the whole code in the book GitHub repo at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications)
from langchain.document_loaders.csv_loader import CSVLoader
loader = CSVLoader(file_path='sample.csv')
data = loader.load()
print(data)
Output:

[Document(page_content='Name: John\nAge: 25\nCity: New York', metadata={'source': 'sample.csv', 'row': 0}), Document(page_content='Name: Emily\nAge: 28\nCity: Los Angeles', metadata={'source': 'sample.csv', 'row': 1}), Document(page_content='Name: Michael\nAge: 22\nCity: Chicago', metadata={'source': 'sample.csv', 'row': 2})]
Document transformers. After importing your documents, it's common to modify them to better match your needs. A basic instance of this is breaking down a lengthy document into smaller chunks that fit your model's context window. Within LangChain, there are various pre-built document transformers available called Text splitters. The idea of Text splitters is to make it easier to split documents into chunks that are semantically related, so that we do not lose context or relevant information.
With Text splitters, you can decide how to split the text (for example, by character, heading, token…) and how to measure the length of the chunk (for example, by number of characters).
For example, let’s split a document using the RecursiveCharacterTextSplitter module, that operates at character level. For this purpose, we will be using a .txt file about mountains (you can find the whole code in the book GitHub repo at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications).
with open('mountain.txt') as f:
    mountain = f.read()
from langchain.text_splitter import RecursiveCharacterTextSplitter
text_splitter = RecursiveCharacterTextSplitter(
    chunk_size = 100,
    chunk_overlap  = 20,
    length_function = len
)
texts = text_splitter.create_documents([mountain])
print(texts[0])
print(texts[1])
print(texts[2])
Output:
page_content="Amidst the serene landscape, towering mountains stand as majestic guardians of nature's beauty." metadata={}
page_content='The crisp mountain air carries whispers of tranquility, while the rustling leaves compose a' metadata={}
Text embedding models. In chapter 1, section “Under the hood of an LLM”, we introduced the concept of embedding as are a way to represent words, subwords, or characters in a continuous vector space.
Embeddings are the key step to incorporate non-parametric knowledge into LLMs. In fact, once properly stored into a VectorDB (which will be covered in next section), they become the non-parametric knowledge against which we can measure the distance of user’s query.
To get started with embedding, you will need an embedding model:
Then, LangChain offer the Embedding class with two main modules, that address the embedding of, respectively, the non-parametric knowledge (multiple input text) and the user query (single input text).
For example, let’s consider the embeddings using the OpenAI embedding model text-embedding-ada-002 (for more details about OpenAI embedding models, you can refer to the official documentation at https://platform.openai.com/docs/guides/embeddings/what-are-embeddings)
from langchain.embeddings import OpenAIEmbeddings
from dotenv import load_dotenv
load_dotenv()
os.environ["OPENAI_API_KEY"]
embeddings_model = OpenAIEmbeddings(model ='text-embedding-ada-002' )
embeddings = embeddings_model.embed_documents(
    [
        "Good morning!",
        "Oh, hello!",
        "I want to report an accident",
        "Sorry to hear that. May I ask your name?",
        "Sure, Mario Rossi."
    ]
)
print("Embed documents:")
print(f"Number of vector: {len(embeddings)}; Dimension of each vector: {len(embeddings[0])}")
embedded_query = embeddings_model.embed_query("What was the name mentioned in the conversation?")
print("Embed query:")
print(f"Dimension of the vector: {len(embedded_query)}")
print(f"Sample of the first 5 elements of the vector: {embedded_query[:5]}")
Output:

Embed documents:
Number of vector: 5; Dimension of each vector: 1536
Embed query:
Dimension of the vector: 1536
Sample of the first 5 elements of the vector: [0.00538721214979887, -0.0005941778072156012, 0.03892524912953377, -0.002979141427204013, -0.008912666700780392]
Once we have both documents and query embedded, the next step will be that of computing the similarity between the two elements and retrieve the most suitable information from the documents embedding. We will see the details of this passage when talking about Vector stores.
Vector stores. A vector store (or VectorDB) is a type of database that can store and search over unstructured data, such as text, images, audio, or video, by using embeddings. By using embeddings, vector stores can perform fast and accurate similarity search, which means finding the most relevant data for a given query.
Definition

Similarity is a measure of how close or related two vectors are in a vector space. In the context of Large Language Models, vectors are numerical representations of sentences, words or documents that capture their semantic meaning, and the distance between those vector should be representative of their semantic similarity.

There are different ways to measure similarity between vectors, and while working with LLMs, one of the most popular measure in use is the cosine similarity.

This is the cosine of the angle between two vectors in a multidimensional space. It is computed as the dot product of the vectors divided by the product of their lengths. Cosine similarity is insensitive to scale and location, and it ranges from -1 to 1, where 1 means identical, 0 means orthogonal, and -1 means opposite.

The following is an illustration of the typical flow while using a vector store.

 
Figure 3: Sample architecture of vector store. Source: https://python.langchain.com/docs/modules/data_connection/vectorstores/
LangChain offers more than 40 integrations towards 3 party vector stores. Some examples are FAISS, ElasticSearch, MongoDB Atlas, and Azure Search. For an exhaustive list and descriptions of all the integrations, you can check the official documentation at https://python.langchain.com/docs/integrations/vectorstores/.
To make an example, let’s leverage the Facebook AI Similarity Search (FAISS) vectore store, which has been developed by Meta AI research for efficient similarity search and clustering of dense vectors. We are going to leverage the same dialogue.txt file saved in the previous section.
from langchain.document_loaders import TextLoader
from langchain.embeddings.openai import OpenAIEmbeddings
from langchain.text_splitter import CharacterTextSplitter
from langchain.vectorstores import FAISS
from dotenv import load_dotenv
load_dotenv()
os.environ["OPENAI_API_KEY"]
# Load the document, split it into chunks, embed each chunk and load it into the vector store.
raw_documents = TextLoader('dialogue.txt').load()
text_splitter = CharacterTextSplitter(chunk_size=50, chunk_overlap=0, separator = "\n",)
documents = text_splitter.split_documents(raw_documents)
db = FAISS.from_documents(documents, OpenAIEmbeddings())
Now that we’ve embedded and saved the non-parametric knowledge, let’s also embed user’s query so that it can be used to search the most similar text chunk using cosine similarity as a measure.

query = "What is the reason for calling?"
docs = db.similarity_search(query)
print(docs[0].page_content)
Output:

I want to report an accident
As you can see, the output is the piece of text that is more likely to contain the answer to the question. In an end-to-end scenario, it will be used as context to the LLM to generate a conversational response.

Retrievers. A retriever is a component in Langchain that can return documents relevant to an unstructured query, such as a natural language question or a keyword. A retriever does not need to store the documents itself, but only to retrieve them from a source. A retriever can use different methods to find the relevant documents, such as keyword matching, semantic search, or ranking algorithms
The difference between a retriever and a vector store is that a retriever is more general and flexible than a vector store. A retriever can use any method to find relevant documents, while a vector store relies on embeddings and similarity metrics. A retriever can also use different sources of documents, such as web pages, databases, or files, while a vector store needs to store the data itself.
However, a vector store can also be used as the backbone of a retriever, if the data is embedded and indexed by a vector store. In that case, the retriever can use the vector store to perform similarity search over the embedded data and return the most relevant documents. This is one of the main types of retrievers in Langchain, called a vector store retriever.
For example, let’s consider the FAISS vector store we previously initialized and “mount” a retriever on top of that.
from langchain.chains import RetrievalQA
from langchain.llms import OpenAI
retriever = db.as_retriever()
qa = RetrievalQA.from_chain_type(llm=OpenAI(), chain_type="stuff", retriever=retriever)
query = "What was the reason of the call?"
qa.run(query)
Output:

' The reason for the call was to report an accident.'
Overall, data connections modules offer a plethora of integrations and pre-built templates that make it easier to manage the flow of your LLM-powered application. We will see some concrete applications of these building blocks in the upcoming chapters, while in next section we are going to deep dive into another of the LangChain’s main components.

Memory
In the context of LLM-powered applications, memory allows the application to keep references to user’s interactions, both in the short and long-term. LangChain offers several modules for designing your memory system within your applications, enabling it with both reading and writing skills.The first step to do with your memory system is that of actually store your human interactions somewhere. To do so, you can leverage more than x built-in memory integrations with 3rd party provider, including Redis, Cassandra, Postgres.Then, when it comes to define how to query your memory system, there are varioys memory types you can leverage:

Conversation buffer memory. This is the “plain vanilla” memory type available in LangChain. It allows you to store your chat messages and extract them in a variable.
Conversation buffer window memory. It is identical to the previous one, with the only difference of allowing for a sliding window over only K interactions, so that you can manage longer chat history over time.
Entity memory. Entity memory is a feature of Langchain that allows the language model to remember given facts about specific entities in a conversation. An entity is a person, place, thing, or concept that can be identified and distinguished from others. For example, in the sentence “Deven & Sam are working on a hackathon in Italy”, Deven and Sam are entities (person), as well as hackathon (thing) and Italy (place).
Entity memory works by extracting information on entities from the input text using a LLM. It then builds up its knowledge about that entity over time by storing the extracted facts in a memory store. The memory store can be accessed and updated by the language model whenever it needs to recall or learn new information about an entity.
Conversation Knowledge Graph memory. This type of memory uses a knowledge graph to recreate memory.
Definition

A knowledge graph is a way of representing and organizing knowledge in a graph structure, where nodes are entities and edges are relationships between them. A knowledge graph can store and integrate data from various sources, and encode the semantics and context of the data. A knowledge graph can also support various tasks, such as search, question answering, reasoning, and generation.

Another example of a knowledge graph is DBpedia, which is a community project that extracts structured data from Wikipedia and makes it available on the web. DBpedia covers topics such as geography, music, sports, films, and more, and provides links to other datasets like GeoNames and WordNet.

You can use this type of memory to save the input and output of each conversation turn as knowledge triplets, such as (subject, predicate, object), and then use them to generate relevant and consistent responses based on the current context. You can also query the knowledge graph to get the current entities or the history of the conversation.

Conversation summary memory. When it comes to longer conversations to be stored, this type of memory can be very useful, since it takes creates a summary of the conversation over time (leveraging an LLM).
Conversation summary buffer memory. This type of memory combines the ideas behind Buffer Memory and Conversation Summary Memory. It keeps a buffer of recent interactions in memory, but rather than just completely flushing old interactions (as occurs for the conversation buffer memory) it compiles them into a summary and uses both.
Conversation token buffer memory. It is similar to the previous one, with the difference that, to determine when to start summarizing the interactions, this type of memory use token lengths rather than the number of interactions (as occurs in summary buffer memory).
Vector store-backed memory. This type of memory leverages the concepts of embeddings and vectore stores previously covered. It is different from all the previous memories since it stores interactions as vectors, and then retrieve the top-K most similar texts every time it is queried, using a retriever.
LangChain provides specific modules for each of the those memory types. Let’s consider an example with the Conversation summary memory, where we will also need an LLM to generate the summary of the interactions.

from langchain.memory import ConversationSummaryMemory, ChatMessageHistory
from langchain.llms import OpenAI
memory = ConversationSummaryMemory(llm=OpenAI(temperature=0))
memory.save_context({"input": "hi, I'm looking for some ideas to write an essay in AI"}, {"output": "hello, what about writing on LLMs?"})
memory.load_memory_variables({})
Output:

{'history': '\nThe human asked for ideas to write an essay in AI and the AI suggested writing on LLMs.'}
As you can see, the memory summarized the conversation leveraging the OpenAI LLM we initialized.There is no recipe to define which memory to use within your applications, however there are some scenarios that might be particularly suitable for specific memories. For example, a knowledge graph memory is useful for applications that need to access information from a large and diverse corpus of data and generate responses based on semantic relationships, while a Conversation summary buffer memory could be suitable for creating conversational agents that can maintain a coherent and consistent context over multiple turns, while also being able to compress and summarize the previous dialogue history.

Chains
Chains are predetermined sequences of actions and calls to LLMs that make it easier to build complex applications that require combining LLMs with each other or with other components. LangChain offer four main type of chain to get started with:

LLMChain. This is the most common type of chain. It consists of a PromptTemplate, an LLM, and an optional output parser.
Definition

An output parser is a component that helps structure language model responses. It is a class that implements two main methods: get_format_instructions and parse. The get_format_instructions method returns a string containing instructions for how the output of a language model should be formatted. The parse method takes in a string (assumed to be the response from a language model) and parses it into some structure, such as a dictionary, a list, or a custom object.

This chain takes multiple input variables, uses the PromptTemplate to format them into a prompt, passes it to the model, and then uses the OutputParser (if provided) to parse the output of the LLM into a final format. For example, let’s retrieve the prompt template we built in the previous section.

from langchain import PromptTemplate
template = """Sentence: {sentence}
Translation in {language}:"""
prompt = PromptTemplate(template=template, input_variables=["sentence", "language"])
Now let’s put it into an LLMChain.

from langchain import OpenAI, LLMChain
llm = OpenAI(temperature=0)
llm_chain = LLMChain(prompt=prompt, llm=llm)
llm_chain.predict(sentence="the cat is on the table", language="spanish")
Output:

' El gato está en la mesa.'
RouterChain. This is a type of chain that allows you to route the input variables to different chains based on some conditions. You can specify the conditions as functions or expressions that return a boolean value. You can also specify the default chain to use if none of the conditions are met.
For example, you can use this chain to create a chatbot that can handle different types of requests, such as booking a restaurant reservation or planning an itinerary. To achieve this goal, you might want to differentiate two different prompts, depending on the type of query the user will make:
itinerary_template = """You are a vacation itinerary assistant. \
You help customers finding the best destinations and itinerary. \
You help customer screating an optimized itinerary based on their preferences.
Here is a question:
{input}"""
restaurant_template = """You are a restaurant booking assitant. \
You check with customers number of guests and food preferences. \
You pay attention whether there are special conditions to take into account.
Here is a question:
{input}"""
Thanks to the RouterChain, we can build a chain which is able to activate a different prompt depending on the user’s query. I won’t post the whole code here (you can find the notebook at the book’s GitHub at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications), but you can see a sample output of how the chain react to two different user’s query:

print(chain.run("I'm planning a trip from Milan to Venice by car. What can I visit in between?"))
Output:

> Entering new MultiPromptChain chain...
itinerary: {'input': "I'm planning a trip from Milan to Venice by car. What attractions can I visit in between?"}
> Finished chain.
Answer: 
There are many attractions that you can visit while traveling from Milan to Venice by car. Some of the most popular attractions include Lake Como, Verona, the Dolomites, and the picturesque towns of Bergamo and Brescia. You can also visit the stunning UNESCO World Heritage Sites in Mantua and Ferrara. Additionally, you can explore some of the local wineries and sample some of the wines of the region.
And with a second query:

print(chain.run("I want to book a table for tonight"))
Output:

> Entering new MultiPromptChain chain...
restaurant: {'input': 'I want to book a table for tonight'}
> Finished chain.
. How many people are in your party?
Hi there! How many people are in your party for tonight's reservation?
SequentialChain. This is a type of chain that allows you to execute multiple chains in a sequence. You can specify the order of the chains and how they pass their outputs to the next chain. The simplest module of sequential chain, namely, takes by default the output of one chain as the input of the next chain, however you can also use a more complex module to have more flexibility to set input and output among chains.
As an example, let’s consider an AI system that is meant to first generate a joke on a given topic, and then translate it in another language. To do so, we will first create two chains as follows:

from langchain.llms import OpenAI
from langchain.chains import LLMChain
from langchain.prompts import PromptTemplate
# This is an LLMChain to write a synopsis given a title of a play.
llm = OpenAI(temperature=.7)
template = """You are a comedian. Generate a joke on the following {topic}
Joke:"""
prompt_template = PromptTemplate(input_variables=["topic"], template=template)
joke_chain = LLMChain(llm=llm, prompt=prompt_template)
template = """You are translator. Given a text input, translate it to {language}
Translation:"""
prompt_template = PromptTemplate(input_variables=["language"], template=template)
translator_chain = LLMChain(llm=llm, prompt=prompt_template)
Now, let’s combine them using the SimpleSequentialChain module:

# This is the overall chain where we run these two chains in sequence.
from langchain.chains import SimpleSequentialChain
overall_chain = SimpleSequentialChain(chains=[joke_chain, translator_chain], verbose=True)
translated_joke = overall_chain.run("Cats and Dogs")
Output:

> Entering new SimpleSequentialChain chain...
Why did the cat cross the road? To prove to the dog that it could be done!
 ¿Por qué cruzó el gato la carretera? ¡Para demostrarle al perro que se podía hacer!
> Finished chain.
TransformationChain. This is a type of chain that allows you to transform the input variables or the output of another chain using some functions or expressions. You can specify the transformation as a function that takes the input or output as an argument and returns a new value, as well as specifying the output format of the chain.
For example, let’s say we want to summarize a text, but before that we want to rename one of the protagonist of the story (a cat) as “Silvester the Cat”. As a sample text, I asked Bing Chat to generate a story about Cats and Dogs (you can find the whole .txt fine at the GitHub repository of this book).
from langchain.chains import TransformChain, LLMChain, SimpleSequentialChain
from langchain.llms import OpenAI
from langchain.prompts import PromptTemplate
transform_chain = TransformChain(
    input_variables=["text"], output_variables=["output_text"], transform=rename_cat
)
template = """Summarize this text:
{output_text}
Summary:"""
prompt = PromptTemplate(input_variables=["output_text"], template=template)
llm_chain = LLMChain(llm=OpenAI(), prompt=prompt)
sequential_chain = SimpleSequentialChain(chains=[transform_chain, llm_chain])
sequential_chain.run(cats_and_dogs)
As you can see, we’ve combined with a sequential chain a simple chain and a transformation chain, where we set as transformation function the rename_cat function (you can see the whole code at the GitHub repo).The output is the following:

" Silvester the Cat and a dog lived together but did not get along. Silvester the Cat played a prank on the dog which made him angry. When their owner found them fighting, she scolded them and made them apologize. After that, they became friends and learned to respect each other's differences and appreciate each other's strengths."
Overall, Langchain chains are a powerful way to combine different language models and tasks into a single workflow. Chains are flexible, scalable, and easy to use, and they enable users to leverage the power of language models for various purposes and domains. Starting from the next chapter, we are going to see chains in action in concrete use cases, but before getting there, we need to cover the last component of LangChain: Agents.

Agents
Agents are entities that drive decision-making within LLMs-powered applications. They have access to a suite of tools and can decide which tool to call based on the user input and the context. Agents are dynamic and adaptive, meaning that they can change or adjust their actions based on the situation or the goal: in fact, while in a chain the sequence of actions is hardcoded, in agents the LLM is used as the reasoning engine with the goal of planning and executing the right actions in the right order.A core concept while talking about agents is that of tools. In fact, an agent might be good at planning all the right actions to fulfill user’s query, but what if it cannot actually executing them, since it is missing information or executive power? For example, imagine I want to build an agent which is capable of answering my questions searching in the web. By itself, the agent has no access to the Web, so I need to provide it with this tool. I will do so by using the SerpApi (the Google Search API) integration provided by LangChain (you can retrieve your API key at https://serpapi.com/dashboard). Let’s see it in Python:

from langchain import SerpAPIWrapper
from langchain.agents import AgentType, initialize_agent
from langchain.llms import OpenAI
from langchain.tools import BaseTool, StructuredTool, Tool, tool
import os
from dotenv import load_dotenv
load_dotenv()
os.environ["SERPAPI_API_KEY"]
search = SerpAPIWrapper()
tools = [Tool.from_function(
        func=search.run,
        name="Search",
        description="useful for when you need to answer questions about current events"
    )]
agent = initialize_agent(tools, llm = OpenAI(), agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION, verbose=True)
agent.run("When was Avatar 2 released?")
Output:

> Entering new AgentExecutor chain...
 I need to find out when Avatar 2 was released.
Action: Search
Action Input: "Avatar 2 release date"
Observation: December 16, 2022
Thought: I now know the final answer.
Final Answer: Avatar 2 was released on December 16, 2022.
> Finished chain.
'Avatar 2 was released on December 16, 2022.'
Note that, while initializing my agent, I set agent type as ZERO_SHOT_REACT_DESCRIPTION. This is one of the configurations we can pick and, specifically, it configures the agent to decide which tool to pick based solely on the tool’s description with a ReAct approach.

Definition

The ReAct approach is a way of using large language models (LLMs) to solve various language reasoning and decision making tasks. It was introduced in the paper “ReAct: Synergizing Reasoning and Acting in Language Models” by Shunyu Yao et al., back to October 2022.

The ReAct approach prompts LLMs to generate both verbal reasoning traces and text actions in an interleaved manner, allowing for greater synergy between the two. Reasoning traces help the model to plan, track, and update its actions, as well as handle exceptions. Actions allow the model to interact with external sources, such as knowledge bases or environments, to gather additional information.

On top of this configuration, LangChain offers also the following types of agents:

Structured input ReAct. This is an agent type that uses the ReAct framework to generate natural language responses based on structured input data. The agent can handle different types of input data, such as tables, lists, or key-value pairs. The agent uses a language model and a prompt to generate responses that are informative, concise, and coherent.
OpenAI Functions. This is an agent type that uses the OpenAI Functions API to access various language models and tools from OpenAI. The agent can use different functions, such as GPT-3, Codex, DALL-E, CLIP, or ImageGPT. The agent uses a language model and a prompt to generate requests to the OpenAI Functions API and parse the responses.
Conversational. This is an agent type that uses a language model to engage in natural language conversations with the user. The agent can handle different types of conversational tasks, such as chit-chat, question answering, or task completion. The agent uses a language model and a prompt to generate responses that are relevant, fluent, and engaging.
Self ask with search. This is an agent type that uses a language model to generate questions for itself and then search for answers on the web. The agent can use this technique to learn new information or test its own knowledge. 
ReAct document store. This is an agent type that uses the ReAct framework to generate natural language responses based on documents stored in a database. The agent can handle different types of documents, such as news articles, blog posts, or research papers.
Plan-and-execute agents. This is an experimental agent type that uses a language model to choose a sequence of actions to take based on the user’s input and a goal. The agent can use different tools or models to execute the actions it chooses. The agent uses a language model and a prompt to generate plans and actions, and then uses an AgentExecutor to run them.
LangChain agents are pivotal whenever you want to let your LLMs interact with the external world. Plus, it is interesting to see how agents leverage LLMs not only to retrieve and generate responses, but also as reasoning engines to plan an optimized sequence of actions.Together with all the LangChain components covered in this paragraph, agents can be the core of LLM-powered applications, we we will see in next chapters.In next section, we are going to shift towards the world of open-source LLMs, introducing the Hugging Face Hub and its native integration with LangChain.

Start working with LLMs via Hugging Face Hub
Now that we got familiar with LangChain components, it is time to start using our LLMs. If you want to use open-source LLMs, leveraging the Hugging Face Hub integration is extremely versatile. In fact, with just one access token you can leverage all the open-source LLMs available in Hugging Face’s repos. As it being a non-production scenario, I will be using the free Inference API, however if you are meant to build production-ready applications, you can easily scale to the Inference Endpoint, which grants you a dedicated and fully managed infrastructure to host and consume your LLMs.So let’s see how to start integrating LangChain with Hugging Face Hub.

Create an Hugging Face user access token
To access the free Inference API, you will need an user access token, the credential thal allows you to run the service. Below you can find the steps to activate the user access token:

Create an Hugging Face account. You can create an Hugging Face account for free at https://huggingface.co/join.

 
Figure 4: Hugging Face registration page. Source: https://huggingface.co/join.
Retrieve your user access token. Once you have your account, go to the upper-right corner of your profile and go you can go under Settings>Access Tokens. From that tab, you will be able to copy your secret token and use it to access Hugging Face models.

 
Figure 5: Retrieving access tokens from Hugging Face account. Source: https://huggingface.co/settings/tokens
Set permissions. Access tokens enable users, applications and notebooks to perform specific actions based on their assigned roles. There are two available roles:
Readallows tokens to provide read access to repositories you have permission to read. This includes public and private repositories owned by you or your organization. This role is suitable for tasks like downloading private models or inference.
Writein addition to read access, tokens with this role grant write access to repositories where you have writing privileges. This token is useful for activities like training models or updating model cards.
In our series of use cases, we will keep a write permission on our token.

Managing your user access token. Within your profile, you can create and manage multiple access tokens, so that you can also differentiate permissions. To create a new token, you can click on the New token button:
 
Figure 6: Creating a new token.
Finally, at any time you can delete or refresh your token under the button Manage:

 
Figure 7: Managing tokens.
It is important not to leak your token, and a good practice is to periodically regenerate it.

Storing your secrets in a .env file
With our user access token generated in the previous section, we have a first secret to be managed.

Definition

Secrets are data that need to be protected from unauthorized access, such as passwords, tokens, keys, and credentials. Secrets are used to authenticate and authorize requests to API endpoints, as well as to encrypt and decrypt sensitive data.

Throughout this hands-on Part of the book, we will keep all our secrets within a .env file.Storing Python secrets in an .env file is a common practice to enhance security and maintainability in projects. To do this, create a file named .env in your project directory and list your sensitive information as key-value pairs: in our scenario, we will have HUGGINGFACEHUB_API_TOKEN=”your_user_access_token”. This file should be added to your project's .gitignore to prevent accidental exposure. To access these secrets in your Python code, use the python-dotenv library to load the .env file's values as environment variables. You can easily install it in your terminal via pip install python-dotenv.This approach keeps sensitive data separate from your codebase and helps ensure that confidential information remains confidential throughout development and deployment processes.Below you can see an example on how to retrieve your access token as set it as an environmental varialbe:

import os
from dotenv import load_dotenv
load_dotenv()
os.environ["HUGGINGFACEHUB_API_TOKEN"]
Note that, by default, load_dotenv will look for the .env file in the current working directory, however you can also specifi the path where your secrets’ file is leaving:

from dotenv import load_dotenv
from pathlib import Path
dotenv_path = Path('path/to/.env')
load_dotenv(dotenv_path=dotenv_path)
Start using open-source LLMs
Now that we all the ingredients to start coding, it is time to try out some open-source LLMs.The nice thing about the Hugging Face Hub integration is that you can navigate on its portal and decide, within the model catalog, what to use. Models are also clustered per category (Computer Vision, Natural Language Processing, Audio…) and, within each category, per capabilities (within NLP, we have summarization, classification, Q&A…).Since we are interested in LLMs, we will focus on text generation category. For this first experiment, let’s try Falson LLM-7B.

from langchain import HuggingFaceHub
repo_id = "tiiuae/falcon-7b-instruct"  
llm = HuggingFaceHub(
    repo_id=repo_id, model_kwargs={"temperature": 0.5, "max_length": 1000}
)
print(llm("what was the first disney movie?"))
Output:

The first Disney movie was 'Snow White and the Seven Dwarfs'
As you can see, with just few lines of code, we integrated an LLM from the Hugging Face Hub. With analogous code, you can test and consume all the LLMs available in the Hub.Note that, throughout this book, we will leveraging specific models for each application, both proprietary and open-source. However, the idea is that you can use the model you prefer by simply initializing it as the main LLM and run the code as it is, simply changing the LangChain LLM integration. This is one of the main advantages of LLM-powered applications, since you don’t have to change the whole code to adapt to different LLMs.

Summary
In this chapter, we dove deeper into the fundamentals of LangChain, since it will be the AI orchestrator used in the upcoming chapters: we got familiar with LangChain components such as memory, agents, chains and prompt templates.We also covered how to start integrating LangChain with Hugging Face Hub and its model catalog, how to use the available LLMs and start embedding them into your code.From now on, we will see a series of concrete end-to-end use cases, starting from a Semantic Q&A Search app that we are going to develop in the next chapter.

References
https://python.langchain.com/docs/integrations/llms/openai
https://python.langchain.com/docs/modules/model_io/prompts/prompt_templates/
https://python.langchain.com/docs/integrations/vectorstores/
https://faiss.ai/
https://python.langchain.com/docs/modules/chains/
https://arxiv.org/abs/2210.03629
https://python.langchain.com/docs/modules/agents/agent_types/
https://huggingface.co/docs

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


5 Embedding LLMs within your Applications
6 Building Conversational applications
7 Search and Recommendation engines with LLMs
2h 3m remaining
6 Building Conversational applications
Join our book community on Discord
https://packt.link/EarlyAccessCommunity



With this chapter, we embark the hands-on section of this book with a first concrete implementation of LLM-powered applications. Throughout this chapter, we will cover a step by step implementation of a conversational application, using LangChain and its components. The main steps will be the following:

Configuring the schema of a simple chatbot
Adding the memory component
Adding non-parametric knowledge
Adding tools and make the chatbot “agentic”
By the end of this chapter, you will be able to set up your own conversational application project with just few lines of code.

Technical requirements
Hugging Face account and user access token.
OpenAI account and user access token.
Python 3.7.1 or later version.
Python packages. Make sure to have the following Python packages installed: langchain, python-dotenv, huggingface_hub, streamlit, openai. Those can be easily installed via pip install in your terminal.
Getting started with conversational applications
A conversational application is a type of software that can interact with users using natural language. It can be used for various purposes, such as providing information, assistance, entertainment, or transactions. Generally speaking, a conversational application can use different modes of communication, such as text, voice, graphics, or even touch. A conversational application can also use different platforms, such as messaging apps, websites, mobile devices, or smart speakers.Today, conversational applications are getting to the next level thanks to Large Language Models. In fact, not only LLMs provides a new level of natural language interactions, but also they can power an applications in making reasonings on the best responses given user’s preferences. As we saw in previous chapters, LLMs can leverage their parametric knowledge, but also enriched with non-parametric knowledge, thanks to embeddings and plug-ins. Finally, LLMs are also able to keep track of the conversation thanks to different types of memories.

 
Figure 1: Sample architecture of a conversational bot.
Throughout this chapter, we will build from scratch a text conversational application that is able to help users to plan their vacations. We will call this app GlobeBotter.We will add incremental layers of complexity to make the app as enjoyable as possible for the end user.So let’s start with the basics behind a conversational app architecture.

Plain vanilla bot
To start with, let’s initialize our LLM and set the schema for our bot. The schema refers to the type of messages the bot is able to receive. In our case, we will have three type of messages:

System messagethe instructions we give the bot so that it behave as a travel assistant.
AI Messagethe message generated by the LLM
Human Messagethe user’s query
Let’s start with a simple configuration:

from langchain.schema import (
    AIMessage,
    HumanMessage,
    SystemMessage
)
from langchain.chains import LLMChain, ConversationChain  
from langchain.chat_models import ChatOpenAI
from langchain.chat_models import ChatOpenAI
chat = ChatOpenAI()
messages = [
    SystemMessage(content="You are a helpful assistant that help the user to plan an optimized itinerary."),
    HumanMessage(content="I'm going to Rome for 2 days, what can I visit?")
We can then save and print the output as follows:

output = chat(messages)
print(output.content)
Output:

 
Figure 2: Sample output of a plain vanilla travel bot.
As you can see, the model was pretty good at generating an itinerary in Rome with only one piece of information from our side, being the number of day.However, we might want to keep interacting with the bot, so that we can further optimize the itinerary, providing further information about our preferences and habits. To achieve that, we need to add memory to our bot.

Adding Memory
As it being a conversational bot with relatively short messages, in this scenario a ConversationBufferMemory could be suitable. To make the configuration easier, let’s also initialize a ConversationChain to combine the LLM and the memory components.Let’s first initialize our memory and chain (I’m keeping verbose = True so that you can see the bot keeping trace of previous messages):

from langchain.memory import ConversationBufferMemory
from langchain.chains import ConversationChain  
memory = ConversationBufferMemory()
conversation = ConversationChain(
    llm=chat, verbose=True, memory=memory
)
Great, now let’s have some interactions with our bot:

conversation.run("Hi there!")
Output:

> Entering new ConversationChain chain...
Prompt after formatting:
The following is a friendly conversation between a human and an AI. The AI is talkative and provides lots of specific details from its context. If the AI does not know the answer to a question, it truthfully says it does not know.
Current conversation:
Human: Hi there!
AI:
> Finished chain.
'Hello! How can I assist you today?'
Input:

conversation.run("what is the most iconic place in Rome?")
Output:

> Entering new ConversationChain chain...
Prompt after formatting:
The following is a friendly conversation between a human and an AI. The AI is talkative and provides lots of specific details from its context. If the AI does not know the answer to a question, it truthfully says it does not know.
Current conversation:
Human: Hi there!
AI: Hello! How can I assist you today?
Human: what is the most iconic place in Rome?
AI:
> Finished chain.
'The most iconic place in Rome is probably the Colosseum. It is a magnificent amphitheater that was built in the first century AD and is one of the most recognizable symbols of ancient Rome. The Colosseum was used for gladiatorial contests, public spectacles, and other events. Today, it is a major tourist attraction and a UNESCO World Heritage site.'
As you can see from the chain, it is keeping track of the previous interactions. Let’s challenge it and ask something related to the previous context:

conversation.run("What kind of other events?")
Output:

> Entering new ConversationChain chain...
Prompt after formatting:
The following is a friendly conversation between a human and an AI. The AI is talkative and provides lots of specific details from its context. If the AI does not know the answer to a question, it truthfully says it does not know.
Current conversation:
Human: Hi there!
AI: Hello! How can I assist you today?
Human: what is the most iconic place in Rome?
AI: The most iconic place in Rome is probably the Colosseum. It is a magnificent amphitheater that was built in the first century AD and is one of the most recognizable symbols of ancient Rome. The Colosseum was used for gladiatorial contests, public spectacles, and other events. Today, it is a major tourist attraction and a UNESCO World Heritage site.
Human: What kind of other events?
AI:
> Finished chain.
'Other events that took place at the Colosseum include mock sea battles, animal hunts, and reenactments of famous battles. The Colosseum was also used for executions and religious ceremonies. It was a versatile venue that could accommodate a variety of events and entertainments.'
The bot was pretty able to understand that our request was related to its previous answer. We can also retrieve the messages history with the memory.load_memory_variables() method (you can see the full output in the GitHub repository).Output:

{'history': 'Human: Hi there!\nAI: Hello! How can I assist you today?\nHuman: what is the most iconic place in Rome?....
Rather than running the conversation.run method at every interaction, I’ve coded a while cycle to make it interactive. The following is a snapshot of the whole conversation (you can find it at the book GitHub repository at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications).

while True:
    query = input('you: ')
    if query == 'q':
        break
    output = conversation({"question": query})
    print('User: ', query)
    print('AI system: ', output['text'])
Output:

 
Figure 3: Sample conversation with travel AI assistant.
Adding non-parametric knowledge
Imagine that you also want your GlobeBotter to have access to exclusive documentations about itineraries, that are not part of its parametric knowledge. To do so, we can either embed the documentation in a VectorDB, or directly use a retriever to do the job. In this case, we will use a vector store-backed retriever using the a particular chain, ConversationalRetrievalChain. This type of chain leverage a retriever over the provided knowledge base keeping the chat history, which can be passed as a parameter using the desired type of memory previously seen.With this goal in mind, we will use a sample Italy travel guide PDF downloaded from https://www.minube.net/guides/italy. The following Python code shows how to initialize all the ingredients we need, that are:

Document Loadersince the document is in PDF format, we will use PyPDFLoader.
Text splitterwe will use a RecursiveCharacterTextSplitter, which splits text by recursively look at characters to find one that works.
Vector storewe will use the FAISS vectorDB.
Memorywe will use a ConversationBufferMemory.
LLMswe will use the gpt-3.5-turbo model for conversations.
Embeddingswe will use the text-embedding-ada-002.
from langchain.llms import OpenAI
from langchain.chat_models import ChatOpenAI
from langchain.embeddings.openai import OpenAIEmbeddings
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain.vectorstores import FAISS
from langchain.document_loaders import PyPDFLoader
from langchain.chains import ConversationalRetrievalChain
from langchain.memory import ConversationBufferMemory
text_splitter = RecursiveCharacterTextSplitter(
            chunk_size=1500,
            chunk_overlap=200
        )
raw_documents = PyPDFLoader('italy_travel.pdf').load()
documents = text_splitter.split_documents(raw_documents)
db = FAISS.from_documents(documents, OpenAIEmbeddings())
memory = ConversationBufferMemory(
            memory_key='chat_history',
            return_messages=True
        )
llm = ChatOpenAI()
Let’s now interact with the chain:

qa_chain = ConversationalRetrievalChain.from_llm(llm, retriever=db.as_retriever(), memory=memory, verbose=True)
qa_chain.run({'question':'Give me some review about the Pantheon'})
Output (I’m reporting a truncated version. You can see the whole output at the book’s GitHub repo at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications):

> Entering new StuffDocumentsChain chain...
> Entering new LLMChain chain...
Prompt after formatting:
System: Use the following pieces of context to answer the users question. 
If you don't know the answer, just say that you don't know, don't try to make up an answer.
----------------
cafes in the square. The most famous are the Quadri and
Florian. 
Piazza San Marco, 
Venice
4
Historical Monuments
Pantheon
 
Miskita:
 
"Angelic and non-human design," was how
Michelangelo described the Pantheon 14 centuries after its
construction. The highlights are the gigantic dome, the upper
eye, the sheer size of the place, and the harmony of the
whole building. We visited with a Roman guide which is
...
> Finished chain.
'Miskita:\n"Angelic and non-human design," was how Michelangelo described the Pantheon 14 centuries after its construction. The highlights
Note that, by default, the ConversationalRetrievalChain use a prompt template called CONDENSE_QUESTION_PROMPT, which aims at condensing the last user’s query with the chat history, so that it results as just one query to the retriever.If you want to pass a custom prompt, you can do so using the condense_question_prompt parameter in the ConversationalRetrievalChain.from_llm module.Even though the bot was able to provide an answer based on the documentation, we still have a limitation. In fact, with such a configuration, our GlobeBotter will only look at the provided documentation, but what if we want it to be able also to use its parametric knowledge? For example, we might want the bot to be able to understand whether it could integrated with provided documentations or simply answer “freely”. To do so, we need to make our GlobeBotter agentic.To do so, we will use two main components:

create_retriever_toolthis method create a custom tool which act as a retriever for an agent.
create_conversational_retrieval_agentthis method initialize a conversational agent which is configured to work with retrievers and chat models.
The following code illustrates hwo to initialize the agent:

from langchain.agents.agent_toolkits import create_retriever_tool
tool = create_retriever_tool(
    db.as_retriever(), 
    "italy_travel",
    "Searches and returns documents regarding Italy."
)
tools = [tool]
memory = ConversationBufferMemory(
            memory_key='chat_history',
            return_messages=True
        )
from langchain.agents.agent_toolkits import create_conversational_retrieval_agent
from langchain.chat_models import ChatOpenAI
llm = ChatOpenAI(temperature = 0)
agent_executor = create_conversational_retrieval_agent(llm, tools, memory_key='chat_history', verbose=True)
Great, now let’s see the thought process of the agent with two different questions (I will report only the chain of thoughts and truncate the output, but you can find the whole code at the GitHub repo).

agent_executor({"input": "Tell me something about Pantheon"})
Output:

> Entering new AgentExecutor chain...
Invoking: `italy_travel` with `Pantheon`
[Document(page_content='cafes in the square. The most famous are the Quadri and\nFlorian. […]
> Finished chain.
Let’s now try with a question not related to the document:

output = agent_executor({"input": "what can I visit in India in 3 days?"})
Output:

> Entering new AgentExecutor chain...
In India, there are numerous incredible places to visit, each with its own unique attractions and cultural experiences. While three days is a relatively short time to explore such a vast and diverse country, here are a few suggestions for places you can visit:
1. Delhi: Start your trip in the capital city of India, Delhi. […]
> Finished chain.
As you can see, when I asked the agent something about Italy, it immediately invoked the provided document, while this latter was ignored in the last question.The last thing we want to add to our GlobeBotter is the capability to navigate the web, since, as travelers, we want to have up-to-date information about the country we are traveling to.Let’s implement it with LangChain’s tools.

Adding external tools
The tool we are going to add here is the Google SerpAPI tool, so that our bot will be able to navigate the internet. Since we don’t want our GlobeBotter to be focused only to the web, we will add the SerpAPI tool to the previous one, so that the agent will be able to pick the most useful tool to answer the question – or rather using no tool since not necessary.Let’s initialize our tools and agent:

from langchain import SerpAPIWrapper
import os
from dotenv import load_dotenv
load_dotenv()
os.environ["SERPAPI_API_KEY"]
search = SerpAPIWrapper()
tools = [
    Tool.from_function(
        func=search.run,
        name="Search",
        description="useful for when you need to answer questions about current events"
    ),
    create_retriever_tool(
        db.as_retriever(), 
        "italy_travel",
        "Searches and returns documents regarding Italy."
    )
    ]
agent_executor = create_conversational_retrieval_agent(llm, tools, memory_key='chat_history', verbose=True)
Great, now let’s test it with three different questions (also here, the output will be truncated):

“What can I visit in India in 3 days?”
> Entering new AgentExecutor chain...
India is a vast and diverse country with numerous attractions to explore. While it may be challenging to cover all the highlights in just three days, here are some popular destinations that you can consider visiting:
1. Delhi: Start your trip in the capital city of India, Delhi. […]
> Finished chain.
“What is the current weather in Delhi?” (note how the agent is invoking the search tool)
> Entering new AgentExecutor chain...
Invoking: `Search` with `{'query': 'current weather in Delhi'}`
Current Weather · 95°F Mostly sunny · RealFeel® 105°. Very Hot. RealFeel Guide. Very Hot. 101° to 107°. Caution advised. Danger of dehydration, heat stroke, heat ...The current weather in Delhi is 95°F (35°C) with mostly sunny conditions. The RealFeel® temperature is 105°F (41°C), indicating that it feels very hot. Caution is advised as there is a danger of dehydration, heat stroke, and heat-related issues. It is important to stay hydrated and take necessary precautions if you are in Delhi or planning to visit.
> Finished chain.
“I'm travelling to Italy, can you give me some suggestions of the main attractions?” (note how the agent is invoking the document retriever)
> Entering new AgentExecutor chain...
Invoking: `italy_travel` with `{'query': 'main attractions in Italy'}`
[Document(page_content='ITALY\nMINUBE TRAVEL GUIDE\nThe best must-see places for your travels, […]
Here are some suggestions for main attractions in Italy:
1. Parco Sempione, Milan: This is one of the most important parks in Milan. It offers a green space in the city where you can relax, workout, or take a leisurely walk. […]
> Finished chain.
Overall, our GlobeBotter is now able to provide up-to-date information as well as retrieving specific knowledge from curated documentation.Next step will be that of building a front-end. We will do so building a webapp using Streamlit.

Front-end with Streamlit
Streamlit is a Python library that allows you to create and share web apps. It is designed to be easy and fast to use, without requiring any front-end experience or knowledge. You can write your app in pure Python, using simple commands to add widgets, charts, tables, and other elements.In addition to its native capabilities, in July 2023 Streamlit announced an initial integration and future plans with LangChains. At the core of this initial integration there is the ambition of making it easier to build GUI for conversational applications, as well as showing all the streps LangChain’s agents take before producing the final response.To achieve this goal, the main module that Streamlit introduced is the Streamlit callback handler. This module provides a class called StreamlitCallbackHandler that implements the BaseCallbackHandler interface from LangChain. This class can handle various events that occur during the execution of a LangChain pipeline, such as tool start, tool end, tool error, LLM token, agent action, agent finish, etc. The class can also create and update Streamlit elements such as containers, expanders, text, progress bars, etc. to display the output of the pipeline in a user-friendly way. You can use the streamlit callback handler to create Streamlit apps that showcase the capabilities of LangChain and interact with the user through natural language. For example, you can create an app that takes a user prompt and runs it through an agent that uses different tools and models to generate a response. You can use the streamlit callback handler to show the agent’s thought process and the results of each tool in real time. To start building your application, you need to create a .py file to run in your terminal via streamlit run file.py. In our case, the file will be named globebotter.py.Those are the main building blocks of the application:

Setting the configuration of the webpage:
import streamlit as st
st.set_page_config(page_title="GlobeBotter", page_icon=" ")
st.header('  Welcome to Globebotter, your travel assistant with Internet access. What are you planning for your next trip?')
Initializing the LangChain components we need as backbone. The code is the same as the one in the previous section, so I will share here only the initialization code, without all the preliminary steps:
search = SerpAPIWrapper()
text_splitter = RecursiveCharacterTextSplitter(
            chunk_size=1500,
            chunk_overlap=200
        )
raw_documents = PyPDFLoader('italy_travel.pdf').load()
documents = text_splitter.split_documents(raw_documents)
db = FAISS.from_documents(documents, OpenAIEmbeddings())
memory = ConversationBufferMemory(
    return_messages=True, 
    memory_key="chat_history", 
    output_key="output"
)
llm = ChatOpenAI()
tools = [
    Tool.from_function(
        func=search.run,
        name="Search",
        description="useful for when you need to answer questions about current events"
    ),
    create_retriever_tool(
        db.as_retriever(), 
        "italy_travel",
        "Searches and returns documents regarding Italy."
    )
    ]
agent = create_conversational_retrieval_agent(llm, tools, memory_key='chat_history', verbose=True)
Setting the input box for the user with a placeholder question:
user_query = st.text_input(
    "**Where are you planning your next vacation?**",
    placeholder="Ask me anything!"
)
Setting the Streamlit’s session states. Session state is a way to share variables between reruns, for each user session. In addition to the ability to store and persist state, Streamlit also exposes the ability to manipulate state using Callbacks. Session state also persists across apps inside a multipage app. You can use the Session State API to initialize, read, update, and delete variables in the session state. In the case of our Globebotter, we want two main states: messages and memory.
if "messages" not in st.session_state:
    st.session_state["messages"] = [{"role": "assistant", "content": "How can I help you?"}]
if "memory" not in st.session_state:
    st.session_state['memory'] = memory
Making sure to display the whole conversation. To do so, I created a for loop that iterates over the list of messages stored in st.session_state[“messages”]. For each message, it creates a Streamlit element called st.chat_message that displays a chat message in a nice format.
for msg in st.session_state["messages"]:
    st.chat_message(msg["role"]).write(msg["content"])
Configuring the AI assistant to respond given a user’s query. In this first example, we will keep the whole chain visible and printed to the screen.
if user_query:
    st.session_state.messages.append({"role": "user", "content": user_query})
    st.chat_message("user").write(user_query)
    with st.chat_message("assistant"):
        st_cb = StreamlitCallbackHandler(st.container())
        response = agent(user_query, callbacks=[st_cb])
        st.session_state.messages.append({"role": "assistant", "content": response})
        st.write(response)
Finally, adding a button to clear the history of the conversation and start from scratch:
if st.sidebar.button("Reset chat history"):
    st.session_state.messages = []
The final product looks as follows:

 
Figure 4: Front-end of Globebotter with Streamlit.
From the expander, we can see that the agent used the Search tool (provided with the SerpAPI). We can also expand chat_history or intermediate_steps as follows:

 
Figure 5: Example of Streamlit expander.
Of course, we can also decide to only show the output rather than the whole chain of thoughts, by specifying in the code to return only response[‘output’].You can see the whole code in the book GitHub repository at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications.

Summary
In this chapter, we approached the end-to-end implementation of a conversational application, leveraging LangChain’s modules and progressively adding layers of complexity. We started with a plain vanilla chatbot with no memory, to then move towards more complex system with the ability to keep trace of past interaction. We’ve also seen how to add non-parametric knowledge to our application with external tools, making it more “agentic” so that it is able to determine which tool to use, depending on user’s query. Finally, we introduced Streamlit as front-end framework to build the webapp for our Globebotter.In next chapter, we will focus on a more specific domain where LLMs are adding values and demonstrating emerging behaviours, that is the one of recommendation systems.

References
https://github.com/shashankdeshpande/langchain-chatbot/blob/master/pages/2_%E2%AD%90_context_aware_chatbot.py
https://www.minube.net/guides/italy

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


6 Building Conversational applications
7 Search and Recommendation engines with LLMs
8 LLMs on structured data
1h 39m remaining
7 Search and Recommendation engines with LLMs
Join our book community on Discord
https://packt.link/EarlyAccessCommunity



In this chapter, we covered the core steps to build conversational applications. We started with a plain vanilla chatbot to then add more complext components, such as memory, non-parametric knowledge and external tools. All of this was made straightforward with the pre-built components of LangChain, as well as Streamlit for UI rendering.Even though conversational applications are often seen as the “confort zone” of generative AI and LLMs. Nevertheless, those models embrace a wider spectrum of applications. In this chapter, we are going to cover how LLMs can enhance recommendion systems, using both embeddings and generative models.Throughout this chapter we will cover the following topics:

Definition and evolutions of recommendation systems
How generative AI is impacting this field of research
Building recommendation systems with LangChain
By the end of this chapter, you will be able to create your own recommendation application leverage state-of-the-art Large Language Models using LangChain as framework.

Technical requirements
Hugging Face account and user access token.
OpenAI account and user access token.
Python 3.7.1 or later version.
Python packages. Make sure to have the following Python packages installed: langchain, python-dotenv, huggingface_hub, streamlit, lancedb. Those can be easily installed via pip install in your terminal.
Introduction to recommendation systems
A recommendation system is a computer program that recommends items for users of digital platforms such as e-commerce websites and social networks. It uses large data sets to develop models of users’ likes and interests, and then recommends similar or recommended items to individual users.There are different types of recommendation systems, depending on the methods and data they use. Some of the common types are:

Collaborative filtering: This type of recommendation system uses the ratings or feedback of other users who have similar preferences to the target user. It assumes that users who liked similar items in the past will like similar items in the future. For example, if user A and user B both liked movies X and Y, then the algorithm may recommend movie Z to user A if user B also liked it.
Collaborative filtering can be further divided into two subtypes: user-based and item-based:
User-based collaborative filtering finds similar users to the target user and recommends items that they liked.
Item-based collaborative filtering finds similar items to the ones that the target user liked and recommends them
Content-based filtering: This type of recommendation system uses the features or attributes of the items themselves to recommend items that are similar to the ones that the target user has liked or interacted with before. It assumes that users who liked certain features of an item will like other items with similar features. For example, if user A liked movie X, which is a comedy with actor Y, then the algorithm may recommend movie Z, which is also a comedy with actor Y.
Hybrid filtering: This type of recommendation system combines both collaborative and content-based filtering methods to overcome some of their limitations and provide more accurate and diverse recommendations. For example, YouTube uses hybrid filtering to recommend videos based on both the ratings and views of other users who have watched similar videos, and the features and categories of the videos themselves.
Knowledge-based filtering: This type of recommendation system uses explicit knowledge or rules about the domain and the user’s needs or preferences to recommend items that satisfy certain criteria or constraints. It does not rely on ratings or feedback from other users, but rather on the user’s input or query. For example, if user A wants to buy a laptop with certain specifications and budget, then the algorithm may recommend a laptop that satisfies those criteria. Knowledge-based recommender systems work well when there is no or little rating history available, or when the items are complex and customizable.
Existing recommendation systems
Modern recommendation systems uses Machine Learning (ML) techniques to make better predictions about user’s preferences, based on the available data that can come from:

User behavior datainsights about user interaction with a product. This data can be acquired from factors like user ratings, clicks, and purchase records.
User demographic data refers to personal information about users, including details like age, educational background, income level, and geographical location.
Product attribute data involves information about the characteristics of a product, such as the genre for books, cast for movies, or cuisine for food."
As of today, some of the most popular ML rechniques are K-nearest neighbors, dimensionality reduction and Neural networks.

K-Nearest Neighbors
K-nearest neighbor (KNN) is a machine learning algorithm that can be used for both classification and regression problems. It works by finding the k closest data points to a new data point and using their labels or values to make a prediction. KNN is based on the assumption that similar data points are likely to have similar labels or values.KNN can be applied to recommendation systems in the context of collaborative filtering, both user-based and content-based:User-based KNN is a type of collaborative filtering, which uses the ratings or feedback of other users who have similar tastes or preferences to the target user. For example, if user A and user B both liked movies X and Y, then the algorithm may recommend movie Z to user A if user B also liked it. User-based KNN works by finding the k most similar users to the target user based on their ratings, and then taking the weighted average of their ratings for the items that the target user has not rated yet.Item-based KNN is another type of collaborative filtering, which uses the attributes or features of the items to recommend similar items to the target user. For example, if user A liked movie X, which is a comedy with actor Y, then the algorithm may recommend movie Z, which is also a comedy with actor Y. Item-based KNN works by finding the k most similar items to the items that the target user has rated, and then taking the weighted average of their ratings for the items that the target user has not rated yet.K-Nearest Neighbors (KNN) is a popular technique in recommendation systems, but it has some pitfalls:

Scalability. KNN can become computationally expensive and slow when dealing with large datasets, as it requires calculating distances between all pairs of items or users.
Cold Start Problem. KNN struggles with new items or users that have limited or no interaction history, as it relies on finding neighbors based on historical data.
Data Sparsity. KNN performance can degrade in sparse datasets where there are many missing values, making it challenging to find meaningful neighbors.
Feature Relevance. KNN treats all features equally and assumes that all features contribute equally to similarity calculations. This may not hold true in scenarios where some features are more relevant than others.
Choice of K. Selecting the appropriate value of K (number of neighbors) can be subjective and impact the quality of recommendations. A small K may result in noise, while a large K may lead to overly broad recommendations.
To address these pitfalls, techniques like distance weighting, dimensionality reduction, and hybrid methods (combining KNN with other recommendation techniques) have been explored. Additionally, further techniques are widely used in the file of recommendation systems, such as matrix factorization.

Matrix factorization
Matrix factorization is a technique used in recommendation systems to analyze and predict user preferences or behaviors based on historical data. It involves decomposing a large matrix into two or more smaller matrices to uncover latent features that contribute to the observed data patterns and address the so-called“curse of dimensionality”.

Definition

The curse of dimensionality refers to challenges that arise when dealing with high-dimensional data. It leads to increased complexity, sparse data, and difficulties in analysis and modeling due to the exponential growth of data requirements and potential overfitting.

In the context of recommendation systems, this technique is employed to predict missing values in the user-item interaction matrix, which represents users' interactions with various items (such as movies, products, or books).Let’s consider the following example. Imagine you have a matrix where rows represent users, columns represent movies, and the cells contain ratings (from 1 as lowest to 5 as highest). However, not all users have rated all movies, resulting in a matrix with many missing entries:

Movie 1	Movie 2	Movie 3	Movie 4
User 1	4	-	5	-
User 2	-	3	-	2
User 3	5	4	-	3
Matrix factorization aims to break down this matrix into two matrices: one for users and another for movies, with a reduced number of dimensions (latent factors). These latent factors could represent attributes like genre preferences or specific movie characteristics. By multiplying these matrices, you can predict the missing ratings and recommend movies that the users might enjoy.There are different algorithms for matrix factorization, among which:

Singular Value Decomposition (SVD). It decomposes a matrix into three separate matrices, where the middle matrix contains singular values that represent the importance of different components in the data. It's widely used in data compression, dimensionality reduction, and collaborative filtering in recommendation systems.
Principal Component Analysis (PCA). PCA is a technique to reduce the dimensionality of data by transforming it into a new coordinate system aligned with the principal components. These components capture the most significant variability in the data, allowing for efficient analysis and visualization.
Non-Negative Matrix Factorization (NMF). NMF decomposes a matrix into two matrices with non-negative values. It's often used for topic modeling, image processing, and feature extraction, where the components represent non-negative attributes.
In the context of recommendation system, probably the most popular technique is SVD, so let’s use this one to go on with our example. We will use the Python numpy module to apply SVD as follows:

import numpy as np
# Your user-movie rating matrix (replace with your actual data)
user_movie_matrix = np.array([
    [4, 0, 5, 0],
    [0, 3, 0, 2],
    [5, 4, 0, 3]
])
# Apply SVD
U, s, V = np.linalg.svd(user_movie_matrix, full_matrices=False)
# Number of latent factors (you can choose this based on your preference)
num_latent_factors = 2
# Reconstruct the original matrix using the selected latent factors
reconstructed_matrix = U[:, :num_latent_factors] @ np.diag(s[:num_latent_factors]) @ V[:num_latent_factors, :]
# Replace negative values with 0
reconstructed_matrix = np.maximum(reconstructed_matrix, 0)
print("Reconstructed Matrix:")
print(reconstructed_matrix)
Output:

Reconstructed Matrix:
[[4.2972542  0.         4.71897811 0.        ]
 [1.08572801 2.27604748 0.         1.64449028]
 [4.44777253 4.36821972 0.52207171 3.18082082]]
In this example, the U matrix contains user-related information, the s matrix contains the singular values, and the V matrix contains movie-related information. By selecting a certain number of latent factors (num_latent_factors), you can reconstruct the original matrix with reduced dimensions, while setting the full_matrices=False parameter in the np.linalg.svd function ensures that the decomposed matrices are truncated to have dimensions consistent with the selected number of latent factors.These predicted ratings can then be used to recommend movies with higher predicted ratings to users. Matrix factorization enables recommendation systems to uncover hidden patterns in user preferences and make personalized recommendations based on those patterns.Matrix factorization has been a widely used technique in recommendation systems, but it has some pitfalls (some similar to the KNN’s technique):

Cold Start Problem. Similar to KNN, matrix factorization struggles with new items or users that have limited or no interaction history. Since it relies on historical data, it can't effectively provide recommendations for new items or users.
Data Sparsity. As the number of users and items grows, the user-item interaction matrix becomes increasingly sparse, leading to challenges in accurately predicting missing values.
Scalability. For large datasets, performing matrix factorization can be computationally expensive and time-consuming.
Limited Context. Matrix factorization typically only considers user-item interactions, ignoring contextual information like time, location, or additional user attributes.
Henceforth, Neural networks (NNs) have been explored as an alternative to mitigate these pitfalls in recent years.

Neural Networks
Neural networks are used in recommendation systems to improve the accuracy and personalization of recommendations by learning intricate patterns from data. Here's how neural networks are commonly applied in this context:

Collaborative Filtering with Neural Networks. Neural networks can model user-item interactions by embedding users and items into continuous vector spaces. These embeddings capture latent features that represent user preferences and item characteristics. Neural collaborative filtering models combine these embeddings with neural network architectures to predict ratings or interactions between users and items.
Content-Based Recommendations. In content-based recommendation, neural networks can learn representations of item content, such as text, images, or audio. These representations capture item characteristics and user preferences. Neural networks like Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs) are used to process and learn from item content, enabling personalized content-based recommendations.
Sequential Models. In scenarios where user interactions have a temporal sequence, such as clickstreams or browsing history, recurrent neural networks (RNNs) or variants like Long Short-Term Memory (LSTM) networks can capture temporal dependencies in the user behavior and make sequential recommendations.
Autoencoders and Variational Autoencoders (VAEs). Autoencoders and VAEs can be used to learn low-dimensional representations of users and items.
Definition

Autoencoders are a type of neural network architecture used for unsupervised learning and dimensionality reduction. They consist of an encoder and a decoder. The encoder maps the input data into a lower-dimensional latent space representation, while the decoder attempts to reconstruct the original input data from the encoded representation.

Variational Autoencoders are an extension of traditional autoencoders that introduce probabilistic elements. VAEs not only learn to encode the input data into a latent space but also model the distribution of this latent space using probabilistic methods. This allows for the generation of new data samples from the learned latent space. VAEs are used for generative tasks like image synthesis, anomaly detection, and data imputation.

In both autoencoders and variational autoencoders, the idea is to learn a compressed and meaningful representation of the input data in the latent space, which can be useful for various tasks including feature extraction, data generation, and dimensionality reduction.

These representations can then be used to make recommendations by identifying similar users and items in the latent space.
Side Information Integration. Neural networks can incorporate additional user and item attributes, such as demographic information, location, or social connections, to improve recommendations by learning from diverse data sources.
Deep Reinforcement Learning. In certain scenarios, deep reinforcement learning can be used to optimize recommendations over time, learning from user feedback to suggest actions that maximize long-term rewards.
Neural networks offer flexibility and the ability to capture complex patterns in data, making them well-suited for recommendation systems. However, they also require careful design, training, and tuning to achieve optimal performance.However, neural networks also bring their own challenges, including increased complexity, training requirements, and potential overfitting. Selecting appropriate architectures, handling large datasets, and tuning hyperparameters are essential to effectively use NNs in recommendation systems. Even though relevant advancements have been made in recent years, the aforementioned techniques still suffer from some pitfalls, first one being their being task-specific. For example, a rating-prediction recommendation system will not be able to tackle a task where we need to recommend the top k items that are likely matching user’s taste. Actually, if we extend this limitation to other “pre-LLMs” AI solutions, we might see some similarities: it is indeed the task-specific situation that Large Languare Models and, more generally, Large Foundation Models are revolutionizing, being highly generalized and adaptable to various tasks, depending on user’s prompts and instructions.Henceforth, several researches in the field of recommendation systems are experimenting to what extent LLMs can enhance the current models. In the following paragraphs, we will cover the theory behind these new approaches referring to recent papers and blogs about this emerging domain.

How LLMs are changing recommendation systems
We saw in previous chapters how LLMs can be customized in three main ways: pre-training, fine-tuning and prompting. According to to the paper “Recommender systems in the Era of Large Language Models (LLMs)” from Wenqi Fan et al., these are also the ways you can tailor an LLM to be a recommender system.

Pre-training. Pre-training LLMs for recommender systems is an important step to enable LLMs to acquire extensive world knowledge and user preferences, and to adapt to different recommendation tasks with zero or few shots.

Note

An example of a recommendation system LLM is P5, introduced by Shijie Gang et al. in their paper “Recommendation as Language Processing (RLP): A Unified Pretrain, Personalized Prompt & Predict Paradigm (P5)”.

P5 is a unified text-to-text paradigm for building recommender systems using large language models (LLMs). It stands for Pretrain, Personalized Prompt & Predict Paradigm and consists of three steps:

Pretrain. A foundation language model based on T5 architecture is pretrained on a large-scale web corpus and fine-tuned on recommendation tasks.

Personalized Prompt. A personalized prompt is generated for each user based on their behavior data and contextual features.

Predict. The personalized prompt is fed into the pretrained language model to generate recommendations.

P5 is based on the idea that LLMs can encode extensive world knowledge and user preferences, and can be adapted to different recommendation tasks with zero or few shots.

Fine-tuning. Training an LLM from scratch is a highly computational-intensive activity. An alternative and less intrusive approach to customize an LLM for recommendation systems might be fine-tuning.
More specifically, the authors of the paper review two main strategies for fine-tuning LLMs:

Full-model fine-tuningit involves changing the entire model weights based on task-specific recommendation datasets.
Parameter-efficient fine-tuningit aims to change only a small part of weights or develop trainable adapters to fit specific tasks.
Prompting. The third and “lightest” way of tailoring LLMs to be recommender systems is prompting. According to the authors, there are three main techniques for prompting LLMs:
Conventional promptingit aims to unify downstream tasks into language generation tasks by designing text templates or providing a few input-output examples.
In-context learningit enables LLMs to learn new tasks based on contextual information without fine-tuning.
Chain-of-thoughtit enhances the reasoning abilities of LLMs by providing multiple demonstrations to describe the chain of thought as examples within the prompt. The authors also discuss the advantages and challenges of each technique, and provide some examples of existing methods that adopt them.
Regardless of the typology, prompting is the fastest way to test whether an general-purpose LLM can tackle recommendations systems’ tasks.
The application of LLMs within the recommendation system domain is undoubtfully raising interest in the research field, and there are already some interesting evicences and results as seen above. In next section, we are going to implement our own recommendation application using the prompting approach and leveraging the capabilities of LangChain as AI orchestrator.

Implementing an LLM-powered recommendation system
Now that we have covered some theory about recommendation systems and emerging research on how LLMs can enhance them, let’s start building our recommendation app, which will be a movie recommender system called MovieHarbor. The goal will be to make it as general as possible, meaning that we want our app to be able to address various recommendations tasks with a conversational interface. The scenario we are going to simulate will be that of the so called “cold-start”, that means the first interaction of an user with the recommendation system, so that we do not have user’s preference history. On the other hand, we will leverage a movie database with textual description.With this purpose, we will use the “Movie recommendation data” dataset, available on Kaggle at https://www.kaggle.com/datasets/rohan4050/movie-recommendation-data.The idea is that of having a dataset with a textual description of each movie (alongside information such as rating and movie title) so that we can get the embeddings of that text. So let’s start building our MovieHarbor application.Data PreprocessingIn order to apply LLMs to our dataset, we first need to preprocess it. The initial dataset included several columns, however the ones we are interested in are the following:

Genresa list of applicable genre for the movie.
Titlemovie’s title
Overviewtextual description of the plot.
Vote_averagerating from 1 to 10 for a given movie
Vote_countnumber of votes for a given movie.
I won’t report here the whole code (you can find it in the GitHub repo of this book at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications), however I will share the main steps if data preprocessing:

Formatting the genres column into a numpy array, which is easier to handle rather than the original dictionary format in the dataset.
import pandas as pd
import ast
# Convert string representation of dictionaries to actual dictionaries
md['genres'] = md['genres'].apply(ast.literal_eval)
# Transforming the 'genres' column
md['genres'] = md['genres'].apply(lambda x: [genre['name'] for genre in x])
Merging the vote_average and vote_count columns into a single column, which is the weighted rated with respect to the number of votes. I’ve also limited the rows to the 95th percentile of the number of votes, so that we can get rid of minimum vote count to prevent skewed results.
# Calculate weighted rate (IMDb formula)
def calculate_weighted_rate(vote_average, vote_count, min_vote_count=10):
    return (vote_count / (vote_count + min_vote_count)) * vote_average + (min_vote_count / (vote_count + min_vote_count)) * 5.0
# Minimum vote count to prevent skewed results
vote_counts = md[md['vote_count'].notnull()]['vote_count'].astype('int')
min_vote_count = vote_counts.quantile(0.95)
# Create a new column 'weighted_rate'
md['weighted_rate'] = md.apply(lambda row: calculate_weighted_rate(row['vote_average'], row['vote_count'], min_vote_count), axis=1)
Creating a new column called combined_info where we are going to merge all the elements that will be provided as context to the LLMs. Those elements are movie title, overview, genres and ratings.
md_final['combined_info'] = md_final.apply(lambda row: f"Title: {row['title']}. Overview: {row['overview']} Genres: {', '.join(row['genres'])}. Rating: {row['weighted_rate']}", axis=1)
Tokenizing the movie combined_info so that we will get better results while embedding:
import pandas as pd
import tiktoken
import os
import openai
openai.api_key = os.environ["OPENAI_API_KEY"]
from openai.embeddings_utils import get_embedding
embedding_encoding = "cl100k_base"  # this the encoding for text-embedding-ada-002
max_tokens = 8000  # the maximum for text-embedding-ada-002 is 8191
encoding = tiktoken.get_encoding(embedding_encoding)
# omit reviews that are too long to embed
md_final["n_tokens"] = md_final.combined_info.apply(lambda x: len(encoding.encode(x)))
md_final = md_final[md_final.n_tokens <= max_tokens]
Definition

Cl100k_base is the name of a tokenizer that is used by OpenAI’s embeddings API. A tokenizer is a tool that splits a text string into smaller units called tokens, which can then be processed by a neural network. Different tokenizers have different rules and vocabularies for how to split the text and what tokens to use.

The cl100k_base tokenizer is based on the Byte Pair Encoding (BPE) algorithm, which learns a vocabulary of subword units from a large corpus of text. The cl100k_base tokenizer has a vocabulary of 100,000 tokens, which are mostly common words and word pieces, but also include some special tokens for punctuation, formatting, and control. The cl100k_base tokenizer can handle texts in multiple languages and domains, and can encode up to 8,191 tokens per input.

Embedding the text with text-embedding-ada-002:
md_final["vector"] = md_final.overview.apply(lambda x: get_embedding(x, engine=embedding_model))
After changing some columns names and dropping unnecessary columns, the final dataset looks as follow:

 
Figure 1: Sample of the final movies dataset.
Let’s have a look at a random row for text:

md['text'][0]
Output:

'Title: GoldenEye. Overview: James Bond must unmask the mysterious head of the Janus Syndicate and prevent the leader from utilizing the GoldenEye weapons system to inflict devastating revenge on Britain. Genres: Adventure, Action, Thriller. Rating: 6.173464373464373'
Great, now that we have our final dataset, we need to store it into a VectorDB. For this purpose, we are going to leverage LanceDB, an open-source database for vector-search built with persistent storage, which greatly simplifies retrieval, filtering and management of embeddings, which also offers a native integration with LangChain. You can easily install LanceDB via pip install lancedb.

import lancedb
uri = "data/sample-lancedb"
db = lancedb.connect(uri)
table = db.create_table("movies", md)
Now that we have all our ingredients, we can start working with those embeddings and start building our recommendarion system. We will start with a simple task in a cold start scenario, adding progressive layers of complexity with LangChain components. Afterwards, we will also try a content-based scenario to challenge our LLMs with diverse tasks.

Cold Start
In previous sections, we saw how the cold start scenario – that means, interacting with an user for the first time without its backstory- often represents a problem to face for recommendation systems. By definition, the less information we have about a user, the harder is it to match its preferences.In this section, we are going to simulate a cold start scenario with LangChain and OpenAI’s LLMs with the following high-level architecture:

 
Figure 2: High-level architecture of recommendation system in a cold start scenario.
In the previous section, we’ve already saved our embeddings in LanceDB. Now, we are going to build a LangChain RetrievalQA using the vector store as retriever, so that it returns the top k most similar movies upon user’s query, using cosine similarity as distance metric (which is the default).
So let’s start building the chain using only the movie overview as information input:

from langchain.embeddings import OpenAIEmbeddings
from langchain.vectorstores import LanceDB
os.environ["OPENAI_API_KEY"]
embeddings = OpenAIEmbeddings()
docsearch = LanceDB(connection = table, embedding = embeddings)
query = "I'm looking for an animated action movie. What could you suggest to me?"
docs = docsearch.similarity_search(query)
docs
Output (I will display a truncated version of the output, showing only the first out of four document sources):

[Document(page_content='Title: Hitman: Agent 47. Overview: An assassin teams up with a woman to help her find her father and uncover the mysteries of her ancestry. Genres: Action, Crime, Thriller. Rating: 5.365800865800866', metadata={'genres': array(['Action', 'Crime', 'Thriller'], dtype=object), 'title': 'Hitman: Agent 47', 'overview': 'An assassin teams up with a woman to help her find her father and uncover the mysteries of her ancestry.', 'weighted_rate': 5.365800865800866, 'n_tokens': 52, 'vector': array([-0.00566491, -0.01658553, […]
As you can see, alongside each Document, all variables are reported as metadata, plus it is also reported the distance as score. The lower the distance, the more the proximity between user’s query and movie’s text embedding.Once gathered the most similar documents, we want a conversational response. For this goal, in addition to the embedding models, we will also use OpenAI’s completion model GPT-3 and combine it in a LangChain retrieval chain, called RetrievalQA.

qa = RetrievalQA.from_chain_type(llm=OpenAI(), chain_type="stuff", retriever=docsearch.as_retriever(), return_source_documents=True)
query = "I'm looking for an animated action movie. What could you suggest to me?"
result = qa({"query": query})
result[‘result’]
Output:

' I would suggest Transformers. It is an animated action movie with genres of Adventure, Science Fiction, and Action, and a rating of 6.'
Since we set the return_source_documents=True parameter, we can also retrieve the documents sources:

result['source_documents'][0]
Output:

Document(page_content='Title: Hitman: Agent 47. Overview: An assassin teams up with a woman to help her find her father and uncover the mysteries of her ancestry. Genres: Action, Crime, Thriller. Rating: 5.365800865800866', metadata={'genres': array(['Action', 'Crime', 'Thriller'], dtype=object), 'title': 'Hitman: Agent 47', 'overview': 'An assassin teams up with a woman to help her find her father and uncover the mysteries of her ancestry.', 'weighted_rate': 5.365800865800866, 'n_tokens': 52, 'vector': array([-0.00566491, -0.01658553, -0.02255735, ..., -0.01242317,
       -0.01303058, -0.00709073], dtype=float32), '_distance': 0.42414575815200806})
Note that the first document reported is not the one the model suggested. This occurred probably because because of the rating, which is lower than Transformers (that was only the third result. This is a great example of how the LLM was able to consider multiple factors, on top of similarity, to suggest the movie to the user.The model was able to generate a conversational answer, however it is still using only a part of the available information – the textual overview. What if we want our MovieHarbor to also leverage the other variables? To do, we can approach the task in two ways:

The “filter” way. This approach consist of adding as kwargs to our retriever some filters, which might be required by the application to the user before responding. Those questions might be, for example, the genre of a movie.
For example, let’s say we want to provide results including only those movies tagged as comedy among their genres. You can achieve this result with the following code:
df_filtered = md[md['genres'].apply(lambda x: 'Comedy' in x)]
qa = RetrievalQA.from_chain_type(llm=OpenAI(), chain_type="stuff", 
    retriever=docsearch.as_retriever(search_kwargs={'data': df_filtered}), return_source_documents=True)
query = "I'm looking for a movie with animals and an adventurous plot."
result = qa({"query": query})
The filter can also operates at metadata level, as shown in the following example, where we want to filter only results with rating above 7:

qa = RetrievalQA.from_chain_type(llm=OpenAI(), chain_type="stuff", 
    retriever=docsearch.as_retriever(search_kwargs={'filter': {weighted_rate__gt:7}}), return_source_documents=True)
The “agentic” way. This is probably the most innovative way to approach the problem. Making our chain agentic means converting the retriever to a tool that the agent can leverage if needed, in all its aspects – including the additional variables. By doing so, it would be sufficient for the user to provide its preferences in natural language so that the agent can retrieve the most promising recommendation.
Let’s see how to implement it with code, asking specifically for an action movie (so filtering on the genre variable):
from langchain.agents.agent_toolkits import create_retriever_tool
from langchain.agents.agent_toolkits import create_conversational_retrieval_agent
from langchain.chat_models import ChatOpenAI
llm = ChatOpenAI(temperature = 0)
retriever = docsearch.as_retriever(return_source_documents = True)
tool = create_retriever_tool(
    retriever, 
    "movies",
    "Searches and returns recommendations about movies."
)
tools = [tool]
agent_executor = create_conversational_retrieval_agent(llm, tools, verbose=True)
result = agent_executor({"input": "suggest me some action movies"})
Let’s see a glimpse of the chain of thoughts and the output produced (always based on the four most similar movies according to cosine similarity).

> Entering new AgentExecutor chain...
Invoking: `movies` with `{'genre': 'action'}`
[Document(page_content='The action continues from [REC], […] 
Here are some action movies that you might enjoy:
1. [REC]² - The action continues from [REC], with a medical officer and a SWAT team sent into a sealed-off apartment to control the situation. It is a thriller/horror movie.
2. The Boondock Saints - Twin brothers Conner and Murphy take swift retribution into their own hands to rid Boston of criminals. It is an action/thriller/crime movie.
3. The Gamers - Four clueless players are sent on a quest to rescue a princess and must navigate dangerous forests, ancient ruins, and more. It is an action/comedy/thriller/foreign movie.
4. Atlas Shrugged Part III: Who is John Galt? - In a collapsing economy, one man has the answer while others try to control or save him. It is a drama/science fiction/mystery movie.
Please note that these recommendations are based on the genre "action" and may vary in terms of availability and personal preferences.
> Finished chain.
Finally, we might also want to make our application more tailored towards its goal of being a recommender system. To do so, we need to do some prompt engineering.

Note

One of the advantages of using LangChain’s pre-built components, such as the RetrievalQA chain, is that they come with a pre-configured, well-curated prompt template. Before overriding the existing prompt, it’s a good practice to inspect it, so that you can also see which are the variables (within {}) that are already expectd from the component.

To explore the existing prompt, you can run the following code:

print(qa.combine_documents_chain.llm_chain.prompt.template)
Output:

Use the following pieces of context to answer the question at the end. If you don't know the answer, just say that you don't know, don't try to make up an answer.
{context}
Question: {question}
Helpful Answer:
Let’s say, for example, that we want our system to return three suggestions for each user’s request, with a short description of the plot and the reason why the user might like it. Below a sample prompt that could match this goal:

from langchain.prompts import PromptTemplate
template = """You are a movie recommender system that help users to find movies that match their preferences. 
Use the following pieces of context to answer the question at the end. 
For each question, suggest three movies, with a short description of the plot and the reason why the user migth like it.
If you don't know the answer, just say that you don't know, don't try to make up an answer.
{context}
Question: {question}
Your response:"""
PROMPT = PromptTemplate(
    template=template, input_variables=["context", "question"])
Now we need to pass it into our chain:

PROMPT = PromptTemplate(
    template=template, input_variables=["context", "question"])
chain_type_kwargs = {"prompt": PROMPT}
qa = RetrievalQA.from_chain_type(llm=OpenAI(), 
    chain_type="stuff", 
    retriever=docsearch.as_retriever(),
    return_source_documents=True, 
    chain_type_kwargs=chain_type_kwargs)
query = "I'm looking for a funny action movie, any suggestion?"
result = qa({'query':query})
print(result['result'])
Output:

1. A Good Day to Die Hard: An action-packed comedy directed by John Moore, this movie follows Iconoclastic, take-no-prisoners cop John McClane as he travels to Moscow to help his wayward son Jack. With the Russian underworld in pursuit, and battling a countdown to war, the two McClanes discover that their opposing methods make them unstoppable heroes.
2. The Hidden: An alien is on the run in America and uses the bodies of anyone in its way as a hiding place. With lots of innocent people dying in the chase, this action-packed horror movie is sure to keep you laughing.
3. District B13: Set in the ghettos of Paris in 2010, this action-packed science fiction movie follows an undercover cop and ex-thug as they try to infiltrate a gang in order to defuse a neutron bomb. A thrilling comedy that will keep you laughing.
Another thing that we might want to implement in our prompt is the information gathered with the conversational preliminary questions that we might want to set as welcome page. For example, before letting the user input its natural language question, we might want to ask it its age, gender and favourite movie genre. To do so, we can insert in our prompt a section where we can format the input variables with those shared by the user, and then combine this prompt chunk in the final prompt we are going to pass to the chain.Below you can find an example (for simplicity, we are going to set the variables without asking the user):

from langchain.prompts import PromptTemplate
template_prefix = """You are a movie recommender system that help users to find movies that match their preferences. 
Use the following pieces of context to answer the question at the end. 
If you don't know the answer, just say that you don't know, don't try to make up an answer.
{context}"""
user_info = """This is what we know about the user, and you can use this information to better tune your research:
Age: {age}
Gender: {gender}"""
template_suffix= """Question: {question}
Your response:"""
user_info = user_info.format(age = 18, gender = 'female')
COMBINED_PROMPT = template_prefix +'\n'+ user_info +'\n'+ template_suffix
print(COMBINED_PROMPT)
Output:

You are a movie recommender system that help users to find movies that match their preferences. 
Use the following pieces of context to answer the question at the end. 
If you don't know the answer, just say that you don't know, don't try to make up an answer.
{context}
This is what we know about the user, and you can use this information to better tune your research:
Age: 18
Gender: female
Question: {question}
Your response:
Now let’s format the prompt and pass it into our chain:

PROMPT = PromptTemplate(
    template=COMBINED_PROMPT, input_variables=["context", "question"])
chain_type_kwargs = {"prompt": PROMPT}
qa = RetrievalQA.from_chain_type(llm=OpenAI(), 
    chain_type="stuff", 
    retriever=docsearch.as_retriever(),
    return_source_documents=True, 
    chain_type_kwargs=chain_type_kwargs)
result = qa({'query':query})
result['result']
Output:

' Sure, I can suggest some action movies for you. Here are a few examples: A Good Day to Die Hard, Goldfinger, Ong Bak 2, and The Raid 2. All of these movies have high ratings and feature thrilling action elements. I hope you find something that you enjoy!'
As you can see, the system took into account the user’s information provided. When we will build the front-end of MovieHarbor, we will make those information dynamic as a preliminary questionnaire proposed to the user.

Recomender Syster
In the previous section, we covered the cold start scenario where the system knew nothing about the user. Sometimes, recommender systems already have some backstory about users, and it is extremely useful to embed this knowledge in our application. Let’s imagine, for example, to have a users database where the system has stored all the refistered user’s information (such as age, gender, country etc.) as well as the movies the user’s already watched alongside its rating. To do so, we will need to set a custom prompt that is able to retrieve this information from a source. For simplicity, we will create a sample dataset with users’ information with just two records, corresponding to two users. Each user will exhibit the following variables: username, age, gender, and a dictionary containing movies already watched alongside with the rating they gave to them.The high-level architecture is the following:

 
Figure 3: High-level architecture of a content-based recommendation system.
Below you can see the code to create the dataset:

import pandas as pd
data = {
    "username": ["Alice", "Bob"],
    "age": [25, 32],
    "gender": ["F", "M"],
    "movies": [
        [("Transformers: The Last Knight", 7), ("Pokémon: Spell of the Unknown", 5)],
        [("Bon Cop Bad Cop 2", 8), ("Goon: Last of the Enforcers", 9)]
    ]
}
# Convert the "movies" column into dictionaries
for i, row_movies in enumerate(data["movies"]):
    movie_dict = {}
    for movie, rating in row_movies:
        movie_dict[movie] = rating
    data["movies"][i] = movie_dict
# Create a pandas DataFrame
df = pd.DataFrame(data)
df.head()
Output:

 
Figure 4: Sample users dataset.
What we want to do now is applying the same logic of the prompt of the cold start with the formatting with varialbels. The difference here is that, rather than asking the user to provide the value for those variables, we will directly collect them from our user dataset. Henceforth, once defined our prompt chunks:

template_prefix = """You are a movie recommender system that help users to find movies that match their preferences. 
Use the following pieces of context to answer the question at the end. 
If you don't know the answer, just say that you don't know, don't try to make up an answer.
{context}"""
user_info = """This is what we know about the user, and you can use this information to better tune your research:
Age: {age}
Gender: {gender}
Movies already seen alongside with rating: {movies}"""
template_suffix= """Question: {question}
Your response:"""
We will format the user_info chunk as follows (assuming that the user interacting with the system is ‘Alice’):

age = df.loc[df['username']=='Alice']['age'][0]
gender = df.loc[df['username']=='Alice']['gender'][0]
movies = ''
# Iterate over the dictionary and output movie name and rating
for movie, rating in df['movies'][0].items():
    output_string = f"Movie: {movie}, Rating: {rating}" + "\n"
    movies+=output_string
    #print(output_string)
user_info = user_info.format(age = age, gender = gender, movies = movies)
COMBINED_PROMPT = template_prefix +'\n'+ user_info +'\n'+ template_suffix
print(COMBINED_PROMPT)
Output:

You are a movie recommender system that help users to find movies that match their preferences. 
Use the following pieces of context to answer the question at the end. 
If you don't know the answer, just say that you don't know, don't try to make up an answer.
{context}
This is what we know about the user, and you can use this information to better tune your research:
Age: 25
Gender: F
Movies already seen alongside with rating: Movie: Transformers: The Last Knight, Rating: 7
Movie: Pokémon: Spell of the Unknown, Rating: 5
Question: {question}
Your response:
Let’s now use this prompt within our chain:

PROMPT = PromptTemplate(
    template=COMBINED_PROMPT, input_variables=["context", "question"])
chain_type_kwargs = {"prompt": PROMPT}
qa = RetrievalQA.from_chain_type(llm=OpenAI(), 
    chain_type="stuff", 
    retriever=docsearch.as_retriever(),
    return_source_documents=True, 
    chain_type_kwargs=chain_type_kwargs)
query = "Can you suggest me some action movie based on my background?"
result = qa({'query':query})
result['result']
Output:

" Based on your age, gender, and the movies you've already seen, I would suggest the following action movies: The Raid 2 (Action, Crime, Thriller; Rating: 6.71), Ong Bak 2 (Adventure, Action, Thriller; Rating: 5.24), Hitman: Agent 47 (Action, Crime, Thriller; Rating: 5.37), and Kingsman: The Secret Service (Crime, Comedy, Action, Adventure; Rating: 7.43)."
'
Note that, in this scenario, we used as dataset a simple pandas dataframe. In production scenarios, a best practice for storing variables related to a task to be addressed (such as a recommendation task) is that of using a feature store.Feature stores are data systems that are designed to support machine learning workflows. They allow data teams to store, manage, and access features that are used for training and deploying machine learning models.Furthermore, LangChain offers native integrations towards some of the most popular features stores:

Feast it is an open-source feature store for machine learning. It allows teams to define, manage, discover, and serve features. Feast supports batch and streaming data sources and integrates with various data processing and storage systems. Feast uses BigQuery for offline features and BigTable or Redis for online features.
Tectonit is a managed feature platform that provides a complete solution for building, deploying, and using features for machine learning. Tecton allows users to define features in code, version control them, and deploy them to production with best practices. Furthermore, it integrates with existing data infrastructure and ML platforms like SageMaker and Kubeflow, and it uses Spark for feature transformations and DynamoDB for online feature serving.
Featureformit is a virtual feature store that transforms existing data infrastructure into a feature store. Featureform allows users to create, store, and access features using standard feature definitions and a Python SDK. It orchestrates and manages the data pipelines required for feature engineering and materialization, and it is compatible with a wide range of data systems, such as Snowflake, Redis, Spark, and Cassandra.
AzureML Managed Feature Storeit is a new type of workspace that lets users discover, create, and operationalize features. This service integrates with existing data stores, feature pipelines, and ML platforms like Azure Databricks and Kubeflow. Plus, it uses SQL, PySpark, SnowPark, or Python for feature transformations and Parquet/S3 or Cosmos DB for feature storage.
You can read more about LangChain’s integration with features stores from the official documentation at https://python.langchain.com/docs/modules/model_io/prompts/prompt_templates/connecting_to_a_feature_store.

Front-end with Streamlit
Now that we have seen the logic behind an LLM-powered recommendation system, it is now time to give a GUI to our MovieHarbor. To do so, we will once again leverage Streamlit, and we will assume the cold start scenario. As always, you can find the whole Python code in the GitHub book repository at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications.As per the Globebotter application, also in this case you need to create a .py file to run in your terminal via streamlit run file.py. In our case, the file will be named movieharbor.py.Below you can find the main steps to build the front end:

Configuring the application webpage:
import streamlit as st
st.set_page_config(page_title="GlobeBotter", page_icon=" ")
st.header('  Welcome to MovieHarbor, your favourite movie recommender')
Importing the credentials and establishing the connection towards LanceDB:
load_dotenv()
#os.environ["HUGGINGFACEHUB_API_TOKEN"]
openai_api_key = os.environ['OPENAI_API_KEY']
embeddings = OpenAIEmbeddings()
uri = "data/sample-lancedb"
db = lancedb.connect(uri)
table = db.open_table('movies')
docsearch = LanceDB(connection = table, embedding = embeddings)
# Import the movie dataset
md = pd.read_pickle('movies.pkl')
Creating some widgets for the user to define its features and movies preferences:
# Create a sidebar for user input
st.sidebar.title("Movie Recommendation System")
st.sidebar.markdown("Please enter your details and preferences below:")
# Ask the user for age, gender and favourite movie genre
age = st.sidebar.slider("What is your age?", 1, 100, 25)
gender = st.sidebar.radio("What is your gender?", ("Male", "Female", "Other"))
genre = st.sidebar.selectbox("What is your favourite movie genre?", md.explode('genres')["genres"].unique())
# Filter the movies based on the user input
df_filtered = md[md['genres'].apply(lambda x: genre in x)]
Defining the parametrized prompt chunks:
template_prefix = """You are a movie recommender system that help users to find movies that match their preferences. 
Use the following pieces of context to answer the question at the end. 
If you don't know the answer, just say that you don't know, don't try to make up an answer.
{context}"""
user_info = """This is what we know about the user, and you can use this information to better tune your research:
Age: {age}
Gender: {gender}"""
template_suffix= """Question: {question}
Your response:"""
user_info = user_info.format(age = age, gender = gender)
COMBINED_PROMPT = template_prefix +'\n'+ user_info +'\n'+ template_suffix
print(COMBINED_PROMPT)
Setting up the RetrievalQA chain:
#setting up the chain
qa = RetrievalQA.from_chain_type(llm=OpenAI(), chain_type="stuff", 
    retriever=docsearch.as_retriever(search_kwargs={'data': df_filtered}), return_source_documents=True)
Inserting the search bar for the user:
query = st.text_input('Enter your question:', placeholder = 'What action movies do you suggest?')
if query:
    result = qa({"query": query})
    st.write(result['result'])
And that’s it! You can see the final result running in your terminal streamlit run movieharbor.py. It looks like the following:

 
Figure 5: Sample front-end for Movieharbor with Streamlit.
S you can see, in just few lines of code we were able to set up a webapp for our MovieHarbor. Starting from this template, you can customize your layout with Streamlit’s components, as well as make it tailored also to content-based scenarios. Plus, you can customize your prompts in such a way that the recommender acts as you prefer.

Summary
In this chapter, we explored how LLMs could change the way we approach a recommendation system task. We started from the analysis of the current strategies and algorithms to build recommendation applications, differentiating among various scenarios (collaborative-filtering, content-based, cold start…) as well as different techniques (K-Nearest Neighbors, Matrix factorization and Neural Networks).We then moved to the new, emerging research of how to apply the power of LLMs to this field, and explored the various experiments that have been done in recent months. Leveraging this evidences, we built a movies recommender applications powered by LLMs, using LangChain as AI orchestrator and Streamlit as front-end, showing how LLMs can revolutionize this fiend thanks to their reasoning capabilities as well as generalization.This was just one example of how LLMs not only can open new frontiers, but also can they enhance existing fields of research.In next chapter, we will see what

References
https://arxiv.org/abs/2203.13366
https://python.langchain.com/docs/modules/model_io/prompts/prompt_templates/connecting_to_a_feature_store
https://docs.feast.dev/
https://www.tecton.ai/
https://www.featureform.com/
https://learn.microsoft.com/en-us/azure/machine-learning/concept-what-is-managed-feature-store?view=azureml-api-2

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


7 Search and Recommendation engines with LLMs
8 LLMs on structured data
59m remaining
8 LLMs on structured data
Join our book community on Discord
https://packt.link/EarlyAccessCommunity



In this chapter, we are going to cover yet another great capabilities of Large Language Models: the ability to handle structured, tabular data. We will see how, thanks to plug-ins and an agentic approach, we can use LLMs as a natural language interface between us and our structured data, reducing the gap between the business user and the structured information.During this chapter, we will cover the following topics:

Introduction to the main structured data systems
Using tools and plug-ins to connect LLMs to tabular data
Building a Database copilot with LangChain
By the end of this chapter, you will be able to build your own natural language interface towards your data estate, also combining unstructured with structured sources.

Technical requirements
Hugging Face account and user access token.
OpenAI account and user access token.
Python 3.7.1 or later version.
Python packages. Make sure to have the following Python packages installed: langchain, python-dotenv, huggingface_hub, streamlit, sqlite3. Those can be easily installed via pip install in your terminal.
What are structured data?
In previous chapters, we focused on how Large Language Models can handle textual data. In fact, those models are, as the name suggests, “language” models, meaning that they have been trained and are able to handle unstructured, text data.Nevertheless, unstructured data only refers to a portion of the overall data realm that applications can handle. Generally, data can be categorized into three types:Certainly! Here are definitions and examples of unstructured, structured, and semi-structured data:

Unstructured Data refers to data that doesn't have a specific or predefined format. It lacks a consistent structure, making it challenging to organize and analyze using traditional databases. Examples of unstructured data include:
Text documents: Emails, social media posts, articles, and reports.
Multimedia: Images, videos, audio recordings.
Natural language text: Chat logs, transcriptions of spoken conversations.
Binary data: Files without a specific data format, such as proprietary file formats.
Structured Datathis type of data is organized and formatted with a clear structure, typically into rows and columns. It follows a fixed schema, making it easy to store, retrieve, and analyze using relational databases. Examples of structured data include:
Relational databases: Data stored in tables with predefined columns and data types.
Spreadsheets: Data organized in rows and columns in software like Microsoft Excel.
Sensor data: Recorded measurements like temperature, pressure, and time in a structured format.
Financial data: Transaction records, balance sheets, and income statements.
Semi-Structured Datait falls between the two categories. While it doesn't adhere to a rigid structure like structured data, it has some level of organization and may contain tags or other markers that provide context. Examples of semi-structured data include:
XML (eXtensible Markup Language) files: They use tags to structure data, but the specific tags and their arrangement can vary.
JSON (JavaScript Object Notation): Used for data interchange and allows for nested structures and key-value pairs.
NoSQL databases: Storing data in a format that doesn't require a fixed schema, allowing for flexibility.
In summary, unstructured data lacks a defined format, structured data follows a strict format, and semi-structured data has some level of structure but is more flexible than structured data. The distinction between these types of data is important as it impacts how they are stored, processed, and analyzed in various applications.However, regardless of its nature, querying structured data involves using a query language or methods specific to that database technology. For example, for SQL Databases, the Structured Query Language (SQL) is used to interact with relational databases. Henceforth, to extract data from tables, you need to know this specific language.But what if we want to ask questions in natural language to our structured data? And what if our application could provide us not only with a sterile numeric answer, but rather with a conversational answer which also gives us context about the number?This is exactly what we will try to achieve in next sections with our LLM-powered applications. More specifically, we are going build something that we’ve already defined in Chapter 2: a copilot. Since we are going to mount our copilot ti a relational database, we will name our application DBCopilot.But what if we want to ask questions in natural language to our structured data? And what if our application could provide us not only with a sterile numeric answer, but rather with a conversational answer which also gives us context about the number?This is exactly what we will try to achieve in next sections with our LLM-powered applications. More specifically, we are going build something that we’ve already defined in Chapter 2: a copilot. Since we are going to mount our copilot ti a relational DataBase, we will name our application DBCopilot.

Relational database and Chinook.db
The concept of relational databases was first proposed by E.F. Codd, an IBM researcher, in 1970. He defined the rules and principles of the relational model, which aimed to provide a simple and consistent way of accessing and manipulating data. He also introduced the Structured Query Language (SQL), which became the standard language for querying and manipulating relational databases.Relational databases became widely used in various domains and applications, such as e-commerce, inventory management, payroll, customer relationship management (CRM), and business intelligence (BI).In this section, we are going to cover the main aspects of a relational database. Then, we will start working with the sample database we will use in our DBCopilot, the Chinook database. We will inspect this database and explore how to connect to remote tables using Python.

Introduction to relational database
A relational database is a type of database that stores and organizes data in structured tables with rows and columns. Each row represents a record, and each column represents a field or attribute. The relationships between tables are established through keys, primarily the primary key and foreign key. This allows for efficient querying and manipulation of data using structured query language (SQL).These databases are commonly used for various applications like websites, business management systems, and more, due to their ability to manage structured data effectively.To have a better understanding of relational databases, let’s consider an example of a database of a library. We'll have two tables: one for books and another for authors. The relationship between them will be established using primary and foreign keys.

 
Figure 1: Example of relationship between two tables in a database.
In this example, the "Authors" table contains information about authors, including their ID, name, and birth year. The "Books" table includes details about books, including the book's ID, title, and a foreign key "AuthorID" that references the corresponding author in the "Authors" table (with AuthorID as primary key).

Definition

A primary key is like the unique fingerprint of each record in a table. It's a special column that holds a value that's distinct for each row in that table. Think of it as the "identity" of a record. Having a primary key is important because it guarantees that no two records in the same table will share the same key. This uniqueness makes it easy to locate, modify, and manage individual records in the table.

A foreign key is a bridge between two tables. It's a column in one table that references the primary key column in another table. This reference creates a link between the data in the two tables, establishing a relationship. The purpose of the foreign key is to maintain data consistency and integrity across related tables. It ensures that if a change is made in the primary key table, the related data in the other table remains accurate. By using foreign keys, you can retrieve information from multiple tables that are connected, enabling you to understand how different pieces of data are related to each other.

This way, you can use SQL queries to retrieve information like finding all books written by a specific author or the birth year of an author based on the book they wrote. The relational structure allows for efficient management and retrieval of data in a structured manner.Some of the main database systems in the market include:

SQL (Structured Query Language) databases: These are relational database management systems (RDBMS) that use SQL for data manipulation and querying. Examples include MySQL, PostgreSQL, and Microsoft SQL Server.
Oracle Database: A widely-used RDBMS that offers advanced features and scalability for large-scale applications.
SQLite: A self-contained, serverless, and zero-configuration SQL database engine commonly used in embedded systems and mobile applications.
IBM Db2: A family of data management products, including relational database servers, developed by IBM.
Amazon Web Services (AWS) RDS: A managed relational database service offered by Amazon, providing options for various databases like MySQL, PostgreSQL, SQL Server, and more.
Google Cloud SQL: A managed database service by Google Cloud Platform, supporting MySQL, PostgreSQL, and SQL Server.
Redis: An open-source, in-memory data structure store that can be used as a database, cache, and message broker.
In next sections, we are going to use SQLite database, which also offers a seamless integration with Python with the module sqlite3, that you can easily install via pip install sqlite3.

Overview of the Chinook database
The chinook database is a sample database that can be used for learning and practicing SQL. It is based on a fictional digital media store, and contains data about artists, albums, tracks, customers, invoices, and more. The chinook database is available for various database management systems, such as SQL Server, Oracle, MySQL, PostgreSQL, SQLite, and DB2. Below some features of this database:

It uses real data from an iTunes library, which makes it more realistic and interesting.
It has a clear and simple data model, which makes it easy to understand and query.
It covers more features of SQL, such as subqueries, joins, views, triggers, etc.
It is compatible with multiple database servers, which makes it more versatile and portable.
You can find the configuration instructions at https://database.guide/2-sample-databases-sqlite/.Below you can see an illustration of the relationship among database’s tables:

 
Figure 2: Diagram of Chinook Database. Source: https://github.com/arjunchndr/Analyzing-Chinook-Database-using-SQL-and-Python.
As you can see, there are 11 tables, all related among each others with primary and foreign keys. In the upcoming paragraph, we will see how LLMs will be cabaple to districate among those tables, capturing their relationships and gathering relevant information. But before jumping to LLMs, let’s first inspect a bit more the Chinook database by setting up the connection with Python.

How to work with relational database in Python
To work with relational databases in Python, you need to use a library that can connect to the database and execute SQL queries.

SQLAlchemy: This is an open-source SQL toolkit and object-relational mapper (ORM) for Python. It allows you to create, read, update and delete data from relational databases using Python objects and methods. It supports many database engines, such as SQLite, MySQL, PostgreSQL, Oracle, and more.
psycopg: This is a popular database connector for PostgreSQL. It enables you to execute SQL queries and access PostgreSQL features from Python. It is fast, reliable, and thread-safe.
MySQLdb: This is a database connector for MySQL. It allows you to interact with MySQL databases from Python using the DB-API 2.0 specification. It is one of the oldest and most widely used Python libraries for MySQL, but its development is mostly frozen.
cx_Oracle: This is a database connector for Oracle Database. It enables you to connect to Oracle databases and use SQL and PL/SQL features from Python. It supports advanced features such as object types, LOBs, arrays, and more.
Since we are going to work with SQLite, we will use the sqlite3 module, that you can easily install via pip install sqlite3.You can use sqlite3 to create, query, update, and delete data from SQLite databases in your Python programs.Some of the features of sqlite3 are:

It follows the DB-API 2.0 specification, which defines a standard interface for Python database access modules.
It supports transactions, which allow you to execute multiple SQL statements as a single unit of work and roll back in case of errors.
It allows you to use Python objects as parameters and results for SQL queries, using various adapters and converters.
It supports user-defined functions, aggregates, collations, and authorizers, which enable you to extend the functionality of SQLite with Python code.
It has a built-in row factory, which returns query results as named tuples or dictionaries instead of plain tuples.
Let’s see an example of this connection using our Chinook database, which I’ve downloaded locally from the GitHub repo at https://github.com/lerocha/chinook-database.

import sqlite3
import pandas as pd
## creating a connection
database = 'chinook.db'
conn = sqlite3.connect(database)
## importing tables 
tables = pd.read_sql("""SELECT name, type
                        FROM sqlite_master
                        WHERE type IN ("table” conn)
Output:

 
Figure 3: List of tables within the Chinook database.
We can also inpsect the single table to gather some relevant data. For example, let’s say we want to see the top five countries per albums sales:

pd.read_sql("""
SELECT c.country AS Country, SUM(i.total) AS Sales
FROM customer c
JOIN invoice i ON c.customer_id = i.customer_id
GROUP BY Country
ORDER BY Sales DESC
LIMIT 5;
""", conn)
Output:

 
Figure 4: Top 5 countries with highest sales.
Finally, we can also use the Python library matplotlib to create useful diagrams about the database’s statistics:

import matplotlib.pyplot as plt
# Define the SQL query
sql = """
SELECT g.Name AS Genre, COUNT(t.track_id) AS Tracks
FROM genre g
JOIN track t ON g.genre_id = t.genre_id
GROUP BY Genre
ORDER BY Tracks DESC;
"""
# Read the data into a dataframe
data = pd.read_sql(sql, conn)
# Plot the data as a bar chart
plt.bar(data.Genre, data.Tracks)
plt.title("Number of Tracks by Genre")
plt.xlabel("Genre")
plt.ylabel("Tracks")
plt.xticks(rotation=90)
plt.show()
Output:

 
Figure 5: Number of tracks by genre.
As you can see, in order to gather relevant information from our database, we used the syntax of SQL language. Our goal is that of gathering information simply asking in natural language, and we are going to do so starting from next paragraph.

Implementing the DBCopilot with LangChain
LangChain agents and SQL Agent
In Chapter 4, we introduced the concept of LangChain agents, defining them as entities that drive decision-making within LLMs-powered applications. Agents have access to a suite of tools and can decide which tool to call based on the user input and the context. Agents are dynamic and adaptive, meaning that they can change or adjust their actions based on the situation or the goal.In this chapter, we will see agents in action, using the following LangChain’s componnts:

An agent designed to interact with relational databasescreate_sql_agent
A toolkit to provide the agent with the required non-parametric knowledgeSQLDatabaseToolkit
A Large Language Models to act as the reasoning engine behind the agent, as well as the generative engine to produce conversational resultsOpenAI
To start with our implementation, let’s first initialize all the components and establish the connection to the Chinook database, using the LangChain component SQLDatabase (which uses SQLAlchemy under the hood).

from langchain.agents import create_sql_agent
from langchain.agents.agent_toolkits import SQLDatabaseToolkit
from langchain.sql_database import SQLDatabase
from langchain.llms.openai import OpenAI
from langchain.agents import AgentExecutor
from langchain.agents.agent_types import AgentType
from langchain.chat_models import ChatOpenAI
llm = OpenAI()
db = SQLDatabase.from_uri('sqlite:///chinook.db')
toolkit = SQLDatabaseToolkit(db=db, llm=llm)
agent_executor = create_sql_agent(
    llm=llm,
    toolkit=toolkit,
    verbose=True,
    agent_type=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
)
Before running the agent, let’s first inspect what are its available tools:

[tool.name for tool in toolkit.get_tools()]
Output:

['sql_db_query', 'sql_db_schema', 'sql_db_list_tables', 'sql_db_query_checker']
Those tools have the following capabilities:

sql_db_query it takes as input a detailed and correct SQL query, and it outputs a result from the database. If the query is not correct, an error message will be returned.
sql_db_schema it takes as input a comma-separated list of tables, and it outputs the schema and sample rows for those tables.
sql_db_list_tables it takes as input a an empty string, and it outputs a comma separated list of tables in the database.
sql_db_query_checkerthis tool double checks if the query is correct before executing it.
Let’s now execute our agent with a simple query to describe the playlisttrack table:

agent_executor.run("Describe the playlisttrack table")
Output:

> Entering new AgentExecutor chain...
Action: sql_db_list_tables
Action Input: 
Observation: album, artist, customer, employee, genre, invoice, invoice_line, media_type, playlist, playlist_track, track
Thought: The table I need is playlist_track
Action: sql_db_schema
Action Input: playlist_track
Observation: 
CREATE TABLE playlist_track (
    playlist_id INTEGER NOT NULL, 
    track_id INTEGER NOT NULL, 
    PRIMARY KEY (playlist_id, track_id), 
    FOREIGN KEY(track_id) REFERENCES track (track_id), 
    FOREIGN KEY(playlist_id) REFERENCES playlist (playlist_id)
)
/*
3 rows from playlist_track table:
playlist_id track_id
1   3402
1   3389
1   3390
*/
Thought: I now know the final answer
Final Answer: The playlist_track table contains the playlist_id and track_id columns. It has a primary key of playlist_id and track_id. There is also a foreign key reference to the track and playlist tables. Sample rows include (1, 3402), (1, 3389), and (1, 3390).
> Finished chain.
'The playlist_track table contains the playlist_id and track_id columns. It has a primary key of playlist_id and track_id. There is also a foreign key reference to the track and playlist tables. Sample rows include (1, 3402), (1, 3389), and (1, 3390).'
As you can see, with a simple question in natural language, our agent was able to understand its semantic, translate it into a SQL query, extract the relevant information and use them as context to generate the response.But how was it able to do all of that? Under the hood, the SQL agent comes with a default prompt template which make it tailored to this type of activity.
Let’s wee the default template of the LangChain component:

print(agent_executor.agent.llm_chain.prompt.template)
Output:

You are an agent designed to interact with a SQL database.
Given an input question, create a syntactically correct sqlite query to run, then look at the results of the query and return the answer.
Unless the user specifies a specific number of examples they wish to obtain, always limit your query to at most 10 results.
You can order the results by a relevant column to return the most interesting examples in the database.
Never query for all the columns from a specific table, only ask for the relevant columns given the question.
You have access to tools for interacting with the database.
Only use the below tools. Only use the information returned by the below tools to construct your final answer.
You MUST double check your query before executing it. If you get an error while executing a query, rewrite the query and try again.
DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database.
If the question does not seem related to the database, just return "I don't know" as the answer.
sql_db_query: Input to this tool is a detailed and correct SQL query, output is a result from the database. If the query is not correct, an error message will be returned. If an error is returned, rewrite the query, check the query, and try again. If you encounter an issue with Unknown column 'xxxx' in 'field list', using sql_db_schema to query the correct table fields.
sql_db_schema: Input to this tool is a comma-separated list of tables, output is the schema and sample rows for those tables. Be sure that the tables actually exist by calling sql_db_list_tables first! Example Input: 'table1, table2, table3'
sql_db_list_tables: Input is an empty string, output is a comma separated list of tables in the database.
sql_db_query_checker: Use this tool to double check if your query is correct before executing it. Always use this tool before executing a query with sql_db_query!
Use the following format:
Question: the input question you must answer
Thought: you should always think about what to do
Action: the action to take, should be one of [sql_db_query, sql_db_schema, sql_db_list_tables, sql_db_query_checker]
Action Input: the input to the action
...
Question: {input}
Thought: I should look at the tables in the database to see what I can query.  Then I should query the schema of the most relevant tables.
{agent_scratchpad}
Thanks to this prompt template, the agent is able to use the proper tools and generate a SQL query, without modifying the underlying database (you can see the explicit rule not to run any DML statements.

Definition

DML stands for Data Manipulation Language, which is a class of SQL statements that are used to query, edit, add and delete row-level data from database tables or views. The main DML statements are:

SELECT: Used to retrieve data from one or more tables or views based on specified criteria.

INSERT: Used to insert new data records or rows into a table.

UPDATE: Used to modify the values of existing data records or rows in a table.

DELETE: Used to remove one or more data records or rows from a table.

MERGE: Used to combine the data from two tables into one based on a common column.

DML statements are used to store, modify, retrieve, delete and update data in a database.

We can also see how the agent is able to correlate more than one table within the database:

agent_executor.run('what is the total number of tracks and the average length of tracks by genre?')
From the first lines of the chain, you can see that the actino input invokes two tables: track and genre:

> Entering new AgentExecutor chain...
Action: sql_db_list_tables
Action Input:
Observation: album, artist, customer, employee, genre, invoice, invoice_line, media_type, playlist, playlist_track, track
Thought: I should look at the schema of the track and genre tables.
Action: sql_db_schema
Action Input: track, genre
[…]
Below the output:

'The top 10 genres by track count and average track length are Rock (1297 tracks with an average length of 283910.04 ms), Latin (579 tracks with an average length of 232859.26 ms), Metal (374 tracks with an average length of 309749.44 ms), Alternative & Punk (332 tracks with an average length of 234353.85 ms), Jazz (130 tracks with an average length of 291755.38 ms), TV Shows (93 tracks with an average length of 2145041.02 ms), Blues (81 tracks with an average length of 270359.78 ms), Classical (74 tracks with an average length of 293867.57 ms), Drama (64 tracks with an average length of 2575283.78 ms), and R&B/Soul (61 tracks with an average length of 220066.85 ms).'
Now the question is: are we sure that we are getting the proper result? A nice way to double check it would be to print the SQL query that the agent ran against the database. To do so, we can modify the default prompt to ask the agent to explicitly show us the reasoning behind its result.

Prompt Engineering
As we saw in the previous chapter, LangChain pre-built agents and chains come with default prompts, which make it easier to tailor them towards their goals. Nevertheless, we can customize that prompt and pass it as a paramenter to our component. For example, let’s say that we want our SQL agent to print the SQL query it used to return the result.First of all, we have to understand which kind of prompt chunks the SQL Agent is able to take as parameters. To do so, we can simply inspect the object running create_sql_agent?.

 
Figure 6: Screenshot of the description of the SQL agent.
The Agent takes a prompt prefix and a format instruction, that are merged and constitutes the default prompt we inspected in the previous section. To make our agent more self-explanatory, we will create two variables, prompt_prefix and prompt_format_instructions, that will be passed as parameters and that slightly modify the default prompt as follows (you can find the whole prompts in the GitHub repo at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications):

In the prompt_prefix, we will add the following line of instruction:
As part of your final answer, ALWAYS include an explanation of how to got to the final answer, including the SQL query you run. Include the explanation and the SQL query in the section that starts with "Explanation:".
In the prompt_format_instructions, we will add the following example of explanation using few-shot learning:
Explanation:
<===Beging of an Example of Explanation:
I joined the invoices and customers tables on the customer_id column, which is the common key between them. This will allowed me to access the Total and Country columns from both tables. Then I grouped the records by the country column and calculate the sum of the Total column for each country, ordered them in descending order and limited the SELECT to the top 5.
```sql
SELECT c.country AS Country, SUM(i.total) AS Sales
FROM customer c
JOIN invoice i ON c.customer_id = i.customer_id
GROUP BY Country
ORDER BY Sales DESC
LIMIT 5;
```sql
===>End of an Example of Explanation
Now let’s pass those prompt chunks as parameters to our agent and print the result (I will omit here the whole chain, but you can see it in the notebook of this chapter).

agent_executor = create_sql_agent(
    prefix=prompt_prefix,
    format_instructions = prompt_format_instructions,
    llm=llm,
    toolkit=toolkit,
    verbose=True,
    top_k=10
)
result = agent_executor.run("What are the top 5 best-selling albums and their artists?")
print(result)
Output:

The top 5 best-selling albums and their artists are 'A Matter of Life and Death' by Iron Maiden, 'BBC Sessions [Disc 1] [live]' by Led Zeppelin, 'MK III The Final Concerts [Disc 1]' by Deep Purple, 'Garage Inc. (Disc 1)' by Metallica and 'Achtung Baby' by U2.
Explanation: I joined the album and invoice tables on the album_id column and joined the album and artist tables on the artist_id column. This allowed me to access the title and artist columns from the album table and the total column from the invoice table. Then I grouped the records by the artist column and calculated the sum of the Total column for each artist, ordered them in descending order and limited the SELECT to the top 5.
```sql
SELECT al.title AS Album, ar.name AS Artist, SUM(i.total) AS Sales
FROM album al
JOIN invoice i ON al.album_id = i.invoice_id
JOIN artist ar ON al.artist_id = ar.artist_id
GROUP BY ar.name
ORDER BY Sales
Great! Now in our result we have a clear explanation of the thought process as well as the printed query our agent made for us. This is already extremely useful, but we want to bring it to the next level: we want our DBCopilot to also be able to generate graphs and save results in our local file system. To achieve this goal, we need to add tools to our agent, and we are going to do so in the next section.

Adding further tools
In order to make our DBCopilot more versatile, there are two further capabilities we need to add:

PythonREPLTool. This tools allows you to interact with the Python programming language using natural language. You can use this tool to write, run, and debug Python code without having to use a script file or an IDE. You can also use this tool to access and manipulate various Python modules, libraries, and data structures.
Definition

REPL is an acronym for Read-Eval-Print Loop, which is a term that describes an interactive shell or environment that allows you to execute code and see the results immediately. REPL is a common feature of many programming languages, such as Python, Ruby, Lisp, and more.

In the context of LangChain, REPL is a feature that allows you to interact with LangChain agents and tools using natural language. You can use REPL in LangChain to test, debug, or experiment with different agents and tools without having to write and run a script file. You can also use REPL in LangChain to access and manipulate various data sources, such as databases, APIs, web pages, and more.

We will need this tool to produce the matplotlib graphs from the SQL query’s results.

FileManagementToolkit. This is a set of tools, or toolkit, that allows you to interact with the file system of your computer or device using natural language. You can use this toolkit to perform various operations on files and directories, such as creating, deleting, renaming, copying, moving, searching, reading, writing, and more. You can also use this toolkit to access and manipulate the metadata and attributes of files and directories, such as name, size, type, date, permissions, and more.
We will need this toolkit to save the graphs generated by our agent in our working directory.So the first thing that we have to do, is defining the list of tools for our agent:

from langchain.tools.python.tool import PythonREPLTool
from langchain.python import PythonREPL
from langchain.agents.agent_toolkits import FileManagementToolkit
working_directory  = os.getcwd()
tools = FileManagementToolkit(
    root_dir=str(working_directory),
    selected_tools=["read_file", "write_file", "list_directory"],).get_tools()
tools.append(
    PythonREPLTool())
tools.extend(SQLDatabaseToolkit(db=db, llm=llm).get_tools())
In order to leverage that heterogeneous set of tools – SQL Database, Python REPL and File Management – we cannot work anymore with the SQL Database-specific agent, since its default configurations are meant to only accept SQL-relatent contents. Henceforth, we need to setup an agnostic agent which is able to use all the tools that we provide it with. For this purpose, we are going to use the STRUCTURED_CHAT_ZERO_SHOT_REACT_DESCRIPTION agent type, which is able to use a multi-tools input.Let’s first start with initializing the agent and asking it to produce a bar chart and save it in the current working directory for the top 5 countries for sales (note that for this purpose, I’ve used a chat model as best suited for the type of agent in use):

from langchain.chat_models import ChatOpenAI
model = ChatOpenAI()
agent = initialize_agent(
    tools, model, agent= AgentType.STRUCTURED_CHAT_ZERO_SHOT_REACT_DESCRIPTION, verbose=True
)
agent.run("generate a matplotlib bar chart of the top 5 countries for sales from the chinook database. Save the output in the current working directory as figure.png")
Output (I will report here just the main actions of the chain, you can see the whole code at the GitHub repo of the book).

> Entering new AgentExecutor chain...
Action:
```
{
  "action": "sql_db_query",
  "action_input": "SELECT billing_country as Country, SUM(total) as Sales FROM invoices GROUP BY billing_country ORDER BY Sales DESC LIMIT 5"
}
```
[…]
Observation: [('USA', 10405.889999999912), ('Canada', 5489.549999999994), ('Brazil', 4058.999999999997), ('France', 3972.869999999995), ('Germany', 3441.2399999999925)]
[…]
We have successfully retrieved the top 5 countries for sales. We can now use matplotlib to create a bar chart.
Action:
```
{
  "action": "Python_REPL",
  "action_input": "import matplotlib.pyplot as plt\nsales_data = [('USA', 10405.89), ('Canada', 5489.55), ('Brazil', 4059.0), ('France', 3972.87), ('Germany', 3441.24)]\n\nx = [item[0] for item in sales_data]\ny = [item[1] for item in sales_data]\nplt.bar(x, y)\nplt.xlabel('Country')\nplt.ylabel('Sales')\nplt.title('Top 5 Countries for Sales')\nplt.show()"
}
```
[…]
> Finished chain.
'Here is the bar chart of the top 5 countries for sales from the Chinook database. It has been saved as figure.png in the current working directory. '
 
Figure 7: Bar chart of top 5 countries by sales.
Great! The agent was able to first invoke the SQL tool to retrieve the relevant information, then it used the Python tool to generate the matplotlib bar chart. Then, it used the File system tool to save the result as PNG.Also in this case, we can modify the prompt of the agent. For example, we might want the agent to provide an explanation not only of the SQL query, but also of the Python code. To do so, we need to define a prompt_prefix and prompt_format_instructionsvariables to be passed as kgwargs to the agent as follows:

prompt_prefix = “”” Your prefix here
“””
prompt_format_instructions= “””
Your instructions here.
“””
agent = initialize_agent(tools, model, agent=AgentType.STRUCTURED_CHAT_ZERO_SHOT_REACT_DESCRIPTION, verbose = True,
                         agent_kwargs={
                            'prefix':prompt_prefix,
                            'format_instructions': prompt_format_instructions })
Thanks to LangChain’s tools components, we were able to extend our DBCopilot capabilities and make it more versatile, depending upon user’s query.With the same logic, we can tailor our agents to any domain, adding or removing tools so that we can control its perimeter of actions. Plus, thanks to the prompt customization, we can always refine the behind logic to make it more customized.

Front-end with Streamlit
Now that we have seen the logic behind an LLM-powered DBCopilot, it is now time to give a GUI to our applicatino. To do so, we will once again leverage Streamlit. As always, you can find the whole Python code in the GitHub book repository at https://github.com/PacktPublishing/Building-Large-Language-Model-Applications.As per the previous sections, also in this case you need to create a .py file to run in your terminal via streamlit run file.py. In our case, the file will be named dbcopilot.py.Below the main steps to setup the front-end:

Configuring the application webpage:
import streamlit as st
st.set_page_config(page_title="DBCopilot", page_icon="")
st.header(' Welcome to DBCopilot, your copilot for structured databases.')
Importing the credentials and establishing the connection towards the Chinook database:
load_dotenv()
#os.environ["HUGGINGFACEHUB_API_TOKEN"]
openai_api_key = os.environ['OPENAI_API_KEY']
db = SQLDatabase.from_uri('sqlite:///chinook.db')
Initializing the Large Language Model and the toolkit:
llm = OpenAI()
toolkit = SQLDatabaseToolkit(db=db, llm=llm)
Initializing the agent using the prompt variables defined in the previous sections:
agent_executor = create_sql_agent(
    prefix=prompt_prefix,
    format_instructions = prompt_format_instructions,
    llm=llm,
    toolkit=toolkit,
    verbose=True,
    top_k=10
)
Defining Streamlit’s session states to make it conversational and memory-aware:
if "messages" not in st.session_state or st.sidebar.button("Clear message history"):
    st.session_state["messages"] = [{"role": "assistant", "content": "How can I help you?"}]
for msg in st.session_state.messages:
    st.chat_message(msg["role"]).write(msg["content"])
Finally, defining the logic of the application whenever an user makes a query:
if user_query:
    st.session_state.messages.append({"role": "user", "content": user_query})
    st.chat_message("user").write(user_query)
    with st.chat_message("assistant"):
        st_cb = StreamlitCallbackHandler(st.container())
        response = agent_executor.run(user_query, callbacks = [st_cb])
        st.session_state.messages.append({"role": "assistant", "content": response})
        st.write(response)
You can run your application in the terminal with the streamlit run copilot.py command. The final webpage looks as follows:

 
Figure 8: Screenshot of the frontend of DBCopilot.
Thanks to the StreamlitCallbackHandler module, we can also expand each action the agent took, for example:

 
Figure 9: Illustration of agent’s actions during the chain.
With just few lines of code, we were able to setup a simple front-end for our DBCopilot with a conversational user interface.

Summary
In this chapter, we saw how Large Language Models are not only capable of interacting with textual, unstructured data, but also with structured and numeric data. This is made possible because of two main elements: the natural capabilities of LLMs and, more generally, LFMs to understand a promblem’s statement, planning a resolution and acting as reasoning engines; and a set of tools that extend LLMs’ capabilities with domain-specific skills. In this case, we mainly relied upon LangChain’s SQL Database toolkit, which connect the agent to a SQL Database with a curated prompt. Furthermore, we extended the agent’s capabilities even further, making it able to generate matplotlib graphs with the Python REPL tool, and save the output in our local file system with the File Management tool.In next chapter, we are going to delve even deeper into the analytical capabilities of LLMs. More specifically, we are going to cover their capabilities of working with code.

References
Chinook Database. https://github.com/lerocha/chinook-database/tree/master/ChinookDatabase/DataSources
LangChain File system tool. https://python.langchain.com/docs/integrations/tools/filesystem
LangChain Python REPL tool. https://python.langchain.com/docs/integrations/toolkits/python

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

