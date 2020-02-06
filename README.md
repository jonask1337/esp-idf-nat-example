# ESP-IDF example with WIFI and NAT setup

An example firmware to use the ESP32 as WiFi repeater.

**Requires** this lwIP library with NAT support to be used as ESP-IDF lwIP component: https://github.com/martin-ger/esp-lwip

Based on: https://github.com/espressif/esp-idf/blob/release/v3.3/examples/wifi/getting_started/softAP/

![NAT-Setup (4)](https://user-images.githubusercontent.com/6740386/72107648-085e4a80-3332-11ea-95a7-e2269adb37dd.png)
Example network setup using ESP32 as WiFi repeater. The diagram was created with [Draw.io](https://www.draw.io/).
## Get started
The following are the steps required to run this project on the ESP32 and turn it into a WiFi repeater.
### Step 1 - Setup ESP-IDF
Download and setup the ESP-IDF.

### Step 2 - Get the lwIP library with NAT
Download the repository of the NAT lwIP library using the follwing command:

`git clone https://github.com/martin-ger/esp-lwip.git`

Note: It is important to clone the repository. If it is only downloaded it will be replaced by the orginal lwIP library during the build.

### Step 3 - Replace original ESP-IDF lwIP library with NAT lwIP library
1. Go to the folder where the ESP-IDF is installed.
2. Rename or delete the *esp-idf/component/lwip/lwip* directory.
3. Move the lwIP library with NAT repository folder from Step 2 to *esp-idf/component/lwip/*
4. Rename the lwIP library with NAT repository folder from *esp-lwip* to *lwip*.

### Step 4 - Build and flash the esp-idf-nat-example project
1. Configure and set the option "Enable copy between Layer2 and Layer3 packets" in the ESP-IDF project configuration.
    1. In the project directory run `make menuconfig` (or `idf.py menuconfig` for cmake).
    2. Go to *Component config -> LWIP* and set "Enable copy between Layer2 and Layer3 packets" option.
    3. Go to *Example config* and set SSID and Password of both, the uplink STA interface and the SoftAP.
2. Build the project and flash it to the ESP32.

A detailed instruction on how to build, configure and flash a ESP-IDF project can also be found the official ESP-IDF guide.

## DNS
By Default the DNS-Server which is offerd to clients connecting to the ESP32 AP is set to 8.8.8.8.
Replace the value of the *MY_DNS_IP_ADDR* with your desired DNS-Server IP address (in hex) if you want to use a different one.


