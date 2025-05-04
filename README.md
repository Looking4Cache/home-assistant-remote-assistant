# Remote Assistant

Remote Assistant helps you to access your Home Assistant interface from anywhere. Without fixed IP addresses and VPN. An SSH tunnel is created between your local installation and the Remote-RED servers, allowing you to access it with our app from outside your local network.

Remote Assistant is a paid service from Remote-RED, an app that has already helped thousands of Node-RED users to use their dashboard on the go.

It's a lean, simple and affordable solution if you just want to access Home Assistant from the internet. It doesn't have the functionality of the Home Assistant app or Home Assistant Cloud and doesn't aim to.

## Costs

Remote Assistant is financed via InApp purchases. This is only $10 per year, the exact price varies from country to country due to VAT and similar charges. The InApp purchase is only required after some time and then begins with a free trial week.

## Usage

Two components are required to use Remote Assistant: A Custom Component within Home Assistant that opens the SSH tunnel to the Remote-RED servers and provides you with the access data. The second component required is the Android or iOS app. This accesses the Remote-RED servers via the Internet, which in turn redirect you to your Home Assistant dashboard at home.

## Install the Custom Component in Home Assistant

There are sveral ways how to install the Custom Component. Choose the best matching way for you:

### Install via HACS

Installing via HACS is ideal if you already have HACS installed. At the moment Remote Assistant is not in the default reprository, but you can use this button to add this reprository to HACS:

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=looking4cache&repository=home-assistant-remote-assistant&category=integration)

After adding the repository you can search for 'Remote Assistant' and install it throgh HACS. If you have not yet installed HACS, you can follow these instructions: [HACS User Documentation](https://hacs.xyz/docs/use/) or use a alternativ way to install Remote Assistant.

### Install via Installer Addon (for Home Assistant OS/Supervised)

There is a extra Addon to install Remote Assistant and keep it up to date. To install this Addon follow this steps:
- Add the reprository:
  - Use this button to add the reprository (maybe you have to insert your local Home Assistant IP adress)
[![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FLooking4Cache%2Fhome-assistant-remote-assistant-installer)
  - Or add the reprository manually:
    - In Home Assistant, go to 'Settings > Add-ons' and open the 'Add-on Store'.
    - Click on the tree dots on to top right and use 'Repositories' to add https://github.com/Looking4Cache/home-assistant-remote-assistant-installer
- Search for 'Remote Assistant Installer' in the list and install it.
- After installing the Addon, start the Addon.
- The installation of the 'Remote Assistant Custom Component' will be executed automatically. See the protocol for more informations.

The Installer Addon will check every day for new versions of the Remote Assistant Custom Component.

After the installation and update of the Custom Component, a restart of Home Assistant is neccessary. This will be done automatically, but you can disable this in the configuration of the Addon.

### Install via Install script (for Home Assistant Containter/Core)

- Connect to the terminal of your Home Assistant host.
- Home Assistant Containter:
  - Enter the Docker container: ```docker exec -it homeassistant bash```
  - Maybe you must change 'homeassistant' to the name of your container.
- Home Assistant Core:
  - Change to the user that is running Home Assistant.
- Run the installation script: ```curl https://www.remote-red.com/remoteassistantinstall | bash -```
- Restart Home Assistant

Run this script again to update Remote Assistant. This will not happen automatically.

## Configure the Custom Component

Before you can connect the app, you have to configure and start the Custom Component.

- In Home Assistant go to 'Settings > Devices and services > Integrations'.
- Use 'Add integration' and search for 'Remote Assistant'.
- Select a server location. A location matching to your country should be preselected.
- Use 'OK' and wait some seconds.
- A QR code will be generated. You will need this in the next step inside the app.
- Remote Assistant will start serving as soon as this dialog is closed. But wait for that until you scanned the QR Code.

## Add connection in the app

- Install the Remote Assistant app on your mobile device:
  - [Apple AppStore](https://apps.apple.com/app/remote-red/id6744168463)
  - [Google PlayStore](http://play.google.com/store/apps/details?id=com.looking4cache.rrha.android)
- On the main page of the app there is the function 'Add Home Assistant instance'. The QR code scanner will open, which requires access to your camera.
- Simply scan the QR code from 'Configure the Custom Component' step and the connection will be established.

## Add another app or reconnect app

- Within Home Assistant, you can open the existing configuration of Remote Assistant under 'Devices and services'.
- Use 'Configure' here to create another QR code.

## Troubleshooting

### Not connected after scanning the QR code

The connection between Home Assistant and the Remote-RED servers is only established as soon as you close the dialog with the QR code. Confirm the dialog with 'OK' and wait a few seconds. The connection should then be possible.

### API error within Home Assistant

The computer on which Home Assistant is installed needs Internet access. If a 'Network Error' or 'API Error' is displayed when connecting to an app, your Home Assistant computer most likely cannot reach the remote RED servers. If you are using a firewall, port 443 (https) and port 22 (ssh) must be allowed outgoing.

## License

This Custom Component is licensed under the MIT License. See the LICENSE file for details.
