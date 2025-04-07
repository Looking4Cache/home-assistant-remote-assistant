# Remote Assistant

Remote Assistant helps you to access your Home Assistant interface from anywhere. Without fixed IP addresses and VPN. An SSH tunnel is created between your local installation and the Remote-RED servers, allowing you to access it with an app from outside your local network.

Remote Assistant is a paid service from Remote-RED, an app that has already helped thousands of Node-RED users to use their dashboard on the go.

It's a lean, simple and affordable solution if you just want to access Home Assistant from the internet. It doesn't have the functionality of the Home Assistant app or Home Assistant Cloud and doesn't aim to.

## Usage

Two components are required to use Remote Assistant: A custom component within Home Assistant that opens the SSH tunnel to the Remote-RED servers and provides you with the access data. The second component required is the Android or iOS app. This accesses the Remote-RED servers via the Internet, which in turn redirect you to your Home Assistant dashboard at home.

## Set up integration in Home Assistant

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=looking4cache&repository=home-assistant-remote-assistant&category=integration)


- The 'Remote Assistant' Custom Component can be installed via HACS. If you have not yet installed HACS, please follow these instructions: [HACS User Documentation](https://hacs.xyz/docs/use/).
- Configure the connection by adding the Remote Assistant integration under 'Settings > Devices and services > Integrations'. Select a server location that is closest to your home. A QR code will be generated in the next step.

## Add connection in the app

- Install the Remote Assistant app on your mobile device:
  - [Apple AppStore](https://apps.apple.com/app/remote-red/id6744168463)
  - [Google PlayStore](http://play.google.com/store/apps/details?id=com.looking4cache.rrha.android)
- On the main page of the app there is the function 'Add Home Assistant instance'. The QR code scanner will open, which requires access to your camera. Simply scan the QR code from the last step and the connection will be established.

## Add another app or reconnect app

- Within Home Assistant, you can open the existing configuration of Remote Assistant under 'Devices and services'.
- Use 'Configure' here to create another QR code.

## Troubleshooting

### Not connected after scanning the QR code

The connection between Home Assistant and the Remote-RED servers is only established as soon as you close the dialog with the QR code. Confirm the dialog with 'OK' and wait a few seconds. The connection should then be possible.

### API error within Home Assistant

The computer on which Home Assistant is installed needs Internet access. If a 'Network Error' or 'API Error' is displayed when connecting to an app, your Home Assistant computer most likely cannot reach the remote RED servers. If you are using a firewall, port 443 (https) and port 22 (ssh) must be allowed outgoing.

## License

This custom component is licensed under the MIT License. See the LICENSE file for details.
