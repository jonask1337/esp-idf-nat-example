# ESP-IDF example with WIFI and NAT setup

An example firmware to use the ESP32 as WiFi repeater.

**Requires** this lwIP library with NAT support to be used as ESP-IDF lwIP component: https://github.com/jonask1337/esp-lwip

Use this project if you want to use it with **PlatformIO**: https://github.com/jonask1337/esp-idf-nat-example-pio

Based on: https://github.com/espressif/esp-idf/blob/release/v3.3/examples/wifi/getting_started/softAP/

## Get started
The following are the steps required to run this project on the ESP32 and turn it into a WiFi repeater.
### Step 1 - Setup ESP-IDF
Download and setup the ESP-IDF.

Setup guide for ESP-IDF v3.3: https://docs.espressif.com/projects/esp-idf/en/v3.3/get-started/index.html

Note: The project is tested with ESP-IDF version 3.3. The ESP-IDF v4.x versions are using a different lwIP library version and are therefore currently not working with the lwIP library with NAT.

### Step 2 - Get the lwIP library with NAT
Download the repository of the NAT lwIP library using the follwing command:

`git clone https://github.com/jonask1337/esp-lwip.git`

Note: It is important to clone the repository. If it is only downloaded it will be replaced by the orginal lwIP library during the build.

### Step 3 - Replace original ESP-IDF lwIP library with NAT lwIP library
1. Go to the folder where the ESP-IDF is installed.
2. Rename or delete the *esp-idf/component/lwip/lwip* directory.
3. Copy the lwIP library with NAT repository folder from Step 2 to *esp-idf/component/lwip/*
4. Rename the lwIP library with NAT repository folder from *esp-lwip* to *lwip*.

### Step 4 - Build and flash the esp-idf-nat-example project
1. Configure the esp-idf-nat-example project (see Configuration below)
2. Set the option "Enable copy between Layer2 and Layer3 packets" in the ESP-IDF project configuration.
    1. In the project directory run `make menuconfig` (or `idf.py menuconfig` for cmake).
    2. Go to *Component config -> LWIP* and set "Enable copy between Layer2 and Layer3 packets" option.
3. Build the project and flash it to the ESP32.

A detailed instruction on how to build, configure and flash a ESP-IDF project can also be found the official ESP-IDF guide referenced in Step 1.

## Configuration

In the `main/main.c` file change the values of the *EXAMPLE_ESP_WIFI_SSID* and *EXAMPLE_ESP_WIFI_PASS* defines to the credentials
of the WIFI network the ESP32 should connect to.

With the *ESP_AP_SSID* and *ESP_AP_PASS* defines you can change the credentials of the Access Point created by the ESP32.

By Default the DNS-Server which is offerd to clients connecting to the ESP32 AP is set to 8.8.8.8.
Replace the value of the *MY_DNS_IP_ADDR* with your desired DNS-Server IP address (in hex) if you want to use a different one.


