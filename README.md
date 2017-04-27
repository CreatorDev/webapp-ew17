![logo](https://static.creatordev.io/logo-md-s.svg)

# Embedded World 2017 - web app

## Overview

This web app works as a proxy and stats collector for other demo components. The demo consists of a pair of conveyor belts moving coloured blocks in a loop, a board detects the colour of blocks and the data is pushed to a cloud application to store the colour and update a multicolour LED bluetooth blub with the last scanned colour.

The webapp works in conjunction with the Creator device server and must be configured with the credentials of a user account to access boards used in the demo. When a coloured block is detected it will be stored in a database so that a graph of detected blocks can be rendered, the webapp also sends back a write request through the Creator device server to a bulb controller application that sets a multicolour LED bulb to match the last detected block. The demo also has a start/stop status that is logged to the database

Other components of the EW17 Creator demo are

* [Ci40 application](https://github.com/CreatorDev/ci40-ew17-uart-to-ds) to receive the detected colour over UART and update an IPSO object with the new colour
* [Clicker application](https://github.com/CreatorDev/clicker-ew-demo) that detects the current block colour and echo the value over UART
* [Ci40 application](https://github.com/CreatorDev/Ci40-ew17-bulb) that receives bulb-colour value changes and issues the corresponding colour change instruction to the bulb over bluetooth
* A python application on a Mediatek 7688 Duo that drives the motors for the conveyor belt when a user presses the stop/start button, or when an inactivity timeout triggers
## Running in docker

* Clone this repository
* `cp config.js.sample config.js`
* Edit config.js file
    * In device server section set url and keys to device server you're suing
    * In database section set URI and database name for your InfluxDB 
    * Set client names as described in comments
    * Set url of host on which app is running. This will be used bu device server to trigger webhooks.
* start the app `docker-compose build && docker-compose up -d`

---

## Help

If you have any problems installing or utilising this project, please look into 
our [Creator Forum](https://forum.creatordev.io). 

Otherwise, If you have come across a nasty bug or would like to suggest new 
features to be added then please go ahead and open an issue or a pull request 
against this repo.

## License

Please see the [license](LICENSE) file for a detailed explanation.

## Contributing

Any Bug fixes and/or feature enhancements are welcome. Please see the 
[contributing](CONTRIBUTING.md) file for a detailed explanation.

--- 