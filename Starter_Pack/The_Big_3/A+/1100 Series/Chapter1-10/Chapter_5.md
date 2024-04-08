- **Firmware:**
  - Define and explain the function of firmware, UEFI, BIOS, CMOS, ROM.
  - Distinguish among various system setup utility options.
  - Troubleshoot using the power-on self-test (POST).
  - Maintain BIOS/UEFI settings.

- **Introduction to Communication with Peripherals:**
  - Discusses the necessity of peripherals for a computer and their connection to the CPU via controller chips.

- **The Evolution of Chipsets:**
  - Describes the transition from individual controller chips to chipsets, focusing on the Intel 430VX chipset and the integration of northbridge and southbridge chips.
  - Explains the modern concept of the Platform Controller Hub (PCH) and its role in connecting devices via the data bus.

- **Talking to the Keyboard:**
  - Explores the interaction between the CPU and the keyboard controller, illustrating how commands are sent and received.
  - Discusses the role of device drivers and their importance in enabling communication between the CPU and peripherals.

- **ROM:**
  - Introduces read-only memory (ROM) chips and their function in storing firmware.
  - Focuses on flash ROM chips as the standard for storing firmware on modern motherboards.

- **UEFI:**
  - Introduces the Unified Extensible Firmware Interface (UEFI) as a modern firmware standard replacing BIOS.
  - Explains the role of UEFI in configuring system utilities, device drivers, and boot support.

- **BIOS:**
  - Provides a historical perspective on BIOS (basic input/output system) and its transition to UEFI.
  - Notes the continued use of the term BIOS interchangeably with UEFI in common language.

- **CMOS and the System Setup Utility:**
  - Discusses the necessity of complementary metal-oxide semiconductor (CMOS) for storing system configuration data.
  - Introduces the system setup utility for accessing and modifying CMOS data.

- **Touring the System Setup Utility:**
  - Provides an overview of the graphical and text-based interfaces of the system setup utility.
  - Covers various tabs and options within the utility, including Main, Ai Tweaker, Advanced, Boot, and Tool tabs.

- **Accessing System Setup:**
  - Offers guidance on accessing the system setup utility during the boot process, highlighting common keys such as delete and f2.

- **Noteworthy BIOS/UEFI Security Settings:**
  - Mentions security features found in BIOS/UEFI settings, including administrator/user passwords, hard drive passwords, and Secure Boot.

- **Boot Options**
  - Your computer's ability to prioritize bootable devices is crucial for system startup.
  - The Boot tab in the system setup utility allows you to set boot options, including USB device boot support.

- **USB Permissions**
  - Enabling booting from USB drives poses security risks, as unauthorized devices could introduce malware.
  - In high-security environments, USB ports are often disabled to mitigate this risk.

- **Fan Considerations**
  - Desktop systems require efficient cooling, typically achieved through multiple fans.
  - System setup utilities offer fan settings to control fan speed and temperature management.

- **Trusted Platform Module (TPM)**
  - TPM serves as a secure cryptoprocessor for storing secure keys used by various software.
  - System setup utilities contain options to enable/disable TPM, which is crucial for operations like disk encryption.

- **Secure Boot**
  - Secure Boot ensures that only trusted firmware and software are loaded during system startup, minimizing malware risks.
  - Signed code with digital signatures is required for Secure Boot verification.

- **Exiting and Saving BIOS/UEFI Settings**
  - System setup utilities provide options to save or discard changes made to settings.
  - Users can create and save customized settings profiles for specific performance or energy use requirements.

- **Power-On Self-Test (POST)**
  - POST is a diagnostic program initiated during system startup to check hardware functionality.
  - POST communicates errors through beep codes or text messages, aiding in troubleshooting.

- **POST Cards**
  - POST cards help identify hardware issues causing system startup failures by monitoring the POST process.

- **The Boot Process**
  - BIOS and UEFI manage the boot process differently, with UEFI systems directly loading the operating system boot loader.

- **Care and Feeding of BIOS/UEFI**
  - Making changes to system setup settings should be done cautiously, with documentation of original settings and changes made.

- **Default/Optimized Settings**
  - System setup utilities offer options like Load Default Settings and OS Optimized Defaults.
  - Default settings reset everything to simple configurations, while Optimized settings maximize system speed and stability.

- **Clearing CMOS**
  - Clearing CMOS resets system settings back to factory defaults, useful for resolving system startup issues caused by misconfigurations.
  - Most motherboards feature CLRTC wires or a CMOS clear button for resetting CMOS settings.

- **Losing CMOS RTC Settings**
  - CMOS RAM requires a continuous trickle charge from a CMOS battery to retain settings.
  - Various factors like hardware changes or electrical surges can lead to the loss of CMOS data.
  - Symptoms of lost CMOS data include CMOS configuration mismatch, date/time errors, and BIOS resets.
  - To replace the CMOS battery, gently pry it out with a screwdriver and ensure the replacement has the same voltage and amperage.

- **Flashing the ROM**
  - Flash ROM chips can be reprogrammed to update BIOS firmware, adding support for new technologies or enhancing security.
  - BIOS flashing utilities typically involve running a program from a removable disk containing the updated BIOS file.
  - Flashing BIOS carries the risk of bricking the computer if the process fails, so backups are essential.
  - Some motherboards offer Windows-based flash ROM update utilities or direct internet access for firmware updates.
  - BIOS updates should only be performed when necessary, as a failed update can cause irreparable damage to the system.