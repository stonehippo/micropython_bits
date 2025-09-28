# Boot.py stuff

## Simple WiFi startup
On boards that support Wifi, it can be handy to define a helper to get WiFi connected. Here's what I put into the `boot.py` on my ESP32, ESP8266, and Pico W boards:

```python
import network
def wifi_up(ssid, password, hostname=None):
    global wlan
    if hostname:
        network.hostname(hostname)
    wlan = network.WLAN(network.STA_IF)
    if not wlan.isconnected():
        print("connecting to WiFi…")
        wlan.active(True)
        wlan.connect(ssid, password)
        while not wlan.isconnected():
            pass
    print(f"Hostname: {network.hostname()}\nIP config: {wlan.ipconfig('addr4')}")
```

This can be called from the REPL like this:

```python
wifi_up("ssid", "password")
```

If you also want to set a hostname—useful if the board's MicroPython LWIP has mDNS configured so you can reach it with something like "mpy-esp32.local")—you can do that, too:

```python
wifi_up("ssid", "password", "hostname")
```
