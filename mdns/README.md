# mDNS

MicroPython firmware for Wifi-enabled boards use LWIP and _sometimes_ enables mDNS for local name resolution. For example, the ESP32 build does this, but the ESP8266 build does not.

If you need mDNS on a MicroPython board, here are some options:

- https://github.com/cbrand/micropython-mdns - a complete implementation of mDNS. It's a bit heavy and won't work on the smaller microcontrollers like ESP8266.
- https://github.com/nickovs/slimDNS - a very lightweight solution for advertising a hostname over mDNS. Works will even on small microcontrollers, but has limited functionality (and could use refactoring to make it an MP module)
