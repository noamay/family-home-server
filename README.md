
# My Home Server

This is my smart home setup for home automation, media server and NAS.

In my opinion - the best way to monitor my services is Docker-Compose.

## [Home Assistant](https://github.com/noamay/FamilyHomeServer/tree/master/homeassistant)

My home automation heart is [Home Assistant](https://www.home-assistant.io/).
Home assistant is an open source platform that combines a variety of smart home devices and features into a single platform.
#### Docker-Compose Configuration:
```yaml
version: '3'
services:
  homeassistant:
    container_name: home-assistant
    image: homeassistant/home-assistant:stable
    volumes:
      - /PATH_TO_YOUR_CONFIG:/config
    environment:
      - TZ=${TimeZone}
    restart: always
    network_mode: host
```
#### Devices And Integrations Table
|Device|Control Method|Controller|Integration|Feedback|
|----|----|----|----|----|
|[RF-433 Light Switches](https://www.aliexpress.com/item/4000049296138.html)|RF-433|[Broadlink RM Pro](https://www.aliexpress.com/item/4000286121299.html)|[Broadlink](https://www.home-assistant.io/integrations/broadlink/)|No|
|Air Conditioner|IR Control|[Broadlink RM Pro](https://www.aliexpress.com/item/4000286121299.html)|[Broadlink](https://www.home-assistant.io/integrations/broadlink/)|On/Off Only from Magnetic Sensor|
|[Magnetic Sensor](https://www.aliexpress.com/item/32991903307.html) - Air-Con Feedback|ZigBee|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|
|[Temperature Sensor](https://www.aliexpress.com/item/32990414707.html)|ZigBee|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|
|Simple Light Strip|ZigBee - [Xiaomi Smart Plug](https://www.aliexpress.com/item/32826132697.html)|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|On/Off|
|Philips Hue Light Bulbs|ZigBee|Philips Hue Hub|[Philips Hue](https://www.home-assistant.io/integrations/hue/)|Yes
|Television|IR Control|[Broadlink RM Pro](https://www.aliexpress.com/item/4000286121299.html)|[Broadlink](https://www.home-assistant.io/integrations/broadlink/)|No|
|[Hallway Motion Detector](https://www.aliexpress.com/item/32975225751.html)| ZigBee|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|
|[ZigBee Smart Button](https://www.aliexpress.com/item/1000008298004.html)|ZigBee|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|
|[Blinds Motor](https://www.aliexpress.com/item/32837172974.html)|RF-433|[Broadlink RM Pro](https://www.aliexpress.com/item/4000286121299.html)|[Broadlink](https://www.home-assistant.io/integrations/broadlink/)|No|
|Brother Printer|WiFi|WiFi Router|[Brother Printer](https://www.home-assistant.io/integrations/brother/)|
|Xiaomi Mibox|WiFi|WiFi|[Google Cast](https://www.home-assistant.io/integrations/cast/) (TODO ADB)|Yes|
|iRobot Roomba|WiFi|WiFi|[iRobot](https://www.home-assistant.io/integrations/roomba/)|Yes|
|Ikea TRADFRI Bulbs|ZigBee|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|Yes|
|[Broadlink A1 Multi Sensor](https://www.aliexpress.com/item/32869635529.html)|WiFi|WiFi Router|[Broadlink](https://www.home-assistant.io/integrations/broadlink/)|
|Ikea TRADFRI Smart Button|ZigBee|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|
|[Xiaomi Aqara Double Switch](https://www.aliexpress.com/item/4000463350744.html)|ZigBee|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|
|[Switcher](https://switcher.co.il/%d7%97%d7%a0%d7%95%d7%aa/) - Boiler Switch|WiFi|WiFi Router|[Switcher_KIS](https://www.home-assistant.io/integrations/switcher_kis/)|Yes|
|Television|IR Control| [Broadlink RM Mini](https://www.aliexpress.com/item/32907686132.html)|[Broadlink](https://www.home-assistant.io/integrations/broadlink/)|No|
|Air Conditioner|IR Control| [Broadlink RM Mini](https://www.aliexpress.com/item/32907686132.html)|[Broadlink](https://www.home-assistant.io/integrations/broadlink/)|No|
|[Magnetic Sensor](https://www.aliexpress.com/item/32991903307.html) - Air-Con Feedback|ZigBee|[CC2531](https://www.aliexpress.com/item/4000059514865.html)|[MQTT](https://www.home-assistant.io/integrations/mqtt/)|
|[YeeLight Lightstrip](https://www.aliexpress.com/item/32943265653.html)|WiFi|WiFi Router|[YeeLight](https://www.home-assistant.io/integrations/yeelight/)|Yes|

Some of my devices can't send a status feedback, I'd strongly recommend to avoid these devices.
For example - I'd use a ZigBee/WiFi wall switches - but those require an extra neutral line at the socket.
#### Other Integrations:
* Plex - Some data from the Plex Media Server(Such as active viewers count)
* Glances - Displays the server's vital signs.
* Dark Sky - Weather Data.
* SmartIR - Allows to use any IR controller and sensors to create a climate controller.
* Telegram Bot - Allows my server to interact with users via Telegram.
* Speed Test - Monitor my internet speed test.
* Google Home - via Nabu Casa paid subscription(this isn't the only method, but it's the easiest method and you get a chance to support the home assistant community)
---

## License
[MIT](https://choosealicense.com/licenses/mit/)
