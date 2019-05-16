# ESP-IDF example with WIFI and NAT setup

An example firmware to use the ESP32 as WIFI repeater.

**Requires** this lwIP library with NAT support to be used as ESP-IDF lwIP component: https://github.com/jonask1337/esp-lwip

Based on: https://github.com/espressif/esp-idf/blob/release/v3.3/examples/wifi/getting_started/softAP/

## Configuration

In the main/main.c file change the values of the *EXAMPLE_ESP_WIFI_SSID* and *EXAMPLE_ESP_WIFI_PASS* defines to the credentials
of the WIFI network the ESP32 should connect to.

With the *ESP_AP_SSID* and *ESP_AP_PASS* defines you can change the credentials of the Access Point created by the ESP32.

By Default the DNS-Server which is offerd to clients connecting to the ESP32 AP is set to 8.8.8.8.
Replace the value of the *MY_DNS_IP_ADDR* with your desired DNS-Server IP address (in hex) if you want to use a different one.
