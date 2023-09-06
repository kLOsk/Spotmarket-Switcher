# Victron-ESS, Shelly Plug S, and AVM-Fritz-DECT200-210 Spotmarket-Switcher

Welcome to the Victron-ESS & Shelly Plug S & AVM-Fritz-DECT200-210 Spotmarket-Switcher repository! This software is designed to enhance the functionality of your energy setup by integrating:

- [Victron](https://www.victronenergy.com/) Venus OS Energy Storage Systems
- Shelly products (such as Shelly Plug S or Shelly Plus1PM)
- AVM Fritz!DECT200 and 210 switchable sockets

The primary goal of this software is to empower your system to respond to spot-market electricity prices, allowing it to make intelligent decisions such as battery charging and power activation based on low pricing periods. The expected solar yield will be taken into account via a weather API and battery storage reserved accordingly.

## Data Source

The software currently utilizes EPEX Spot hourly prices provided by three free APIs (Tibber, aWATTar & Entso-E).
The integrated free Entso-E API is providing energy-price-data of the folowing countrys:
Albania (AL), Austria (AT), Belgium (BE), Bosnia and Herz. (BA), Bulgaria (BG), Croatia (HR), Cyprus (CY), Czech Republic (CZ), Denmark (DK), Estonia (EE), Finland (FI), France (FR), Georgia (GE), Germany (DE), Greece (GR), Hungary (HU), Ireland (IE), Italy (IT), Kosovo (XK), Latvia (LV), Lithuania (LT), Luxembourg (LU), Malta (MT), Moldova (MD), Montenegro (ME), Netherlands (NL), North Macedonia (MK), Norway (NO), Poland (PL), Portugal (PT), Romania (RO), Serbia (RS), Slovakia (SK), Slovenia (SI), Spain (ES), Sweden (SE), Switzerland (CH), Turkey (TR), Ukraine (UA), United Kingdom (UK) see [Transparency Entso-E Platform](https://transparency.entsoe.eu/transmission-domain/r2/dayAheadPrices/show). 

![grafik](https://user-images.githubusercontent.com/6513794/224442951-c0155a48-f32b-43f4-8014-d86d60c3b311.png)

## Installation

Setting up the Victron-ESS & Shelly Plug S & AVM-Fritz-DECT200-210 Spotmarket-Switcher is a straightforward process. If you are already running a UNIX-based machine, such as macOS, Linux, or Windows with the Linux subsystem, follow these steps to install the software:


1. Download the install script from the GitHub repository by using [this hyperlink](https://raw.githubusercontent.com/christian1980nrw/Spotmarket-Switcher/main/victron-venus-os-install.sh), or execute the following command in your terminal:
   ```
   wget https://raw.githubusercontent.com/christian1980nrw/Spotmarket-Switcher/main/victron-venus-os-install.sh
   ```

2. Run the installer script with additional options to prepare everything in a subdirectory for your inspection. For example:
   ```
   DESTDIR=/tmp/foo sh victron-venus-os-install.sh
   ```
   If you're using Victron Venus OS, the correct DESTDIR should be `/` (the root directory). Feel free to explore the installed files in `/tmp/foo`.

Please note that while this software is currently optimized for the Venus OS, it can be adapted to other setups, such as controlling household devices via IP switches. Future development might enhance compatibility with other systems.

### Access to Venus OS

For instructions on accessing the Venus OS, please refer to [https://www.victronenergy.com/live/ccgx:root_access](https://www.victronenergy.com/live/ccgx:root_access).

### Execution of the Install Script

- If you're using Victron Venus OS:
  - Execute `victron-venus-os-install.sh` to download and install the Spotmarket-Switcher.
  - Edit the variables with a text editor in`/data/etc/Spotmarket-Switcher/controller.sh`.
  - Set up an ESS charge schedule (refer to the screenshot provided). In the example, the battery charges at night up to 50% if activated. Remember to deactivate it after creation. Verify that the system time (as shown in the screenshot) is accurate.
![grafik](https://user-images.githubusercontent.com/6513794/206877184-b8bf0752-b5d5-4c1b-af15-800b6499cfc7.png)

- If you're using another OS:
  - Copy the shell script (`controller.sh`) to a custom location and adjust the variables according to your needs.
  - Create a crontab or another scheduling method to run this script at the start of each hour.
  - Sample Crontab:
      Use the following crontab entry to execute the control script every hour:
      Open your terminal and enter `crontab -e`, then insert the following line:
      ```
      0 * * * * /path/to/controller.sh
      ```

### Support and Contribution

If you find this project valuable, please consider sponsoring and supporting further development through these links:
- [Revolut](https://revolut.me/christqki2)
- [PayPal](https://paypal.me/christian1980nrw)

Additionally, if you're in Germany and interested in switching to a dynamic electricity tariff, you can support the project by signing up using this [Tibber (referral link)](https://invite.tibber.com/ojgfbx2e). Both you and the project will receive a 50 euro bonus for hardware. Please note that a smart meter or a Pulse-IR is required for an hourly tariff (https://tibber.com/de/store/produkt/pulse-ir) .

If you need a natural gas tariff or prefer a classic electricity tariff, you can still support the project [Octopus Energy (referral link)](https://share.octopusenergy.de/glass-raven-58) .
You receive a 50 euro bonus for yourself and also for the project.
Octopus has the advantage that the contracts usually only have a monthly term. They are ideal, for example, for pausing a tariff based on stock exchange prices.

## Disclaimer

This computer program is provided "as is," and the user assumes full risk when using it. The author makes no representations or warranties regarding the accuracy, reliability, completeness, or suitability of the program for any specific purpose. The author shall not be liable for any damages arising from the use or inability to use the program, including but not limited to direct, indirect, incidental, special, or consequential damages.
