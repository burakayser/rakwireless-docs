---
rak_img: /assets/images/wisduo/rak3272s-breakout-board/overview/RAK3272S_Breakout_home.png
rak_desc: Contains instructions and tutorials in installing and deploying your RAK3272S Breakout Board. Instructions are written in a detailed and step-by-step manner for an easier experience in setting up your LoRaWAN Module. 
prev: ../Overview/
next: ../AT-Command-Manual/
tags:
  - wisduo
  - quickstart
  - RAK3272S Breakout Board
---

# RAK3272S Quick Start Guide

This guide covers the following topics:

- [TheThingsNetwork Guide](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#connecting-to-the-things-network-ttn) - How to login, register new accounts and create new applications on TTN.
- [RAK3272S TTN OTAA Guide](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#ttn-otaa-device-registration) - How to add OTAA device on TTN and what AT commands to use on RAK3272S OTAA activation.
- [RAK3272S TTN ABP Guide](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#ttn-abp-device-registration) - How to add ABP device on TTN and what AT commands to use on RAK3272S ABP activation.
- [Chirpstack Guide](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#connecting-with-chirpstack) - How to create new applications on Chirpstack. 
- [RAK3272S Chirpstack OTAA Guide](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#chirpstack-otaa-device-registration) - How to add OTAA device to Chirpstack and what AT commands to use on RAK3272S OTAA activation.
- [RAK3272S Chirpstack ABP Guide](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#chirpstack-abp-device-registration) - How to add ABP device on Chirpstack and what AT commands to use on RAK3272S ABP activation.
- [LoRa P2P](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#lora-p2p-mode) - Point to point communication between two RAK3272S Breakout Boards.
- [Updating RAK3272S Breakout Board  FW](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#upgrading-the-firmware) - Procedures on how to update RAK3272S Breakout Board firmware.

## Prerequisites

### What Do You Need?

Before going through the step in the installation guide of the RAK3272S Breakout Board, make sure to prepare the necessary items listed below:

#### Hardware Tools

1. RAK3272S Breakout Board
2. RAKDAP1 Flash and Debug Tool (or any USB-Serial Adapter)
3. Jumper Wires
4. Windows/Mac OS/Linux Computer with USB port
5. USB cable


#### Software Tools
1. [RAK Serial Port Tool](https://downloads.rakwireless.com/en/LoRa/Tools)


#### List of Acronyms

| Acronym | Definition                                       |
| ------- | ------------------------------------------------ |
| DFU     | Device Firmware Upgrade                          |
| JTAG    | Joint Test Action Group                          |
| LoRa    | Long Range                                       |
| OTAA    | Over-The-Air-Activation                          |
| ABP     | Activation-By-Personalization (ABP)              |
| TTN     | The Things Network                               |
| DEVEUI  | Device EUI (Extended Unique Identification)      |
| APPEUI  | Application EUI (Extended Unique Identification) |
| APPKEY  | Application Key                                  |
| DEVADDR | Device Address                                   |
| NWKSKEY | Network Session Key                              |
| APPSKEY | Application Session Key                          |
| P2P     | Point-to-Point                                   |


## Product Configuration

### Interfacing with RAK3272S Breakout Board

The RAK3272S can be interface via UART. The UART serial communication is exposed on the **LPUART1 port**, through **Pin 7 (TX2)** and **Pin 8 (RX2)**. The default parameters of the UART2 communication are **9600 / 8-N-1**. The firmware upgrade is also possible through this port. To get familiar with the pin distribution of this module and find a schematic circuit of a reference application, refer to the [RAK3272S  Breakout Board Datasheet](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Datasheet/#rak3272s-breakout-board-datasheet).

#### Connect to the RAK3272S Breakout Board

1. Connect the RAK3272S Breakout Board to the [RAKDAP1](https://store.rakwireless.com/collections/hardware-tools/products/daplink-tool) or any USB-Serial adapter with 3.3&nbsp;V voltage supply, as shown in Figure 1.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/rak3272srakdap1.png"
  width="65%"
  caption="RAK3272S Breakout Board to USB-Serial Connection"
/>

2. Any serial communication tool can be used; but, it is recommended to use the [RAK Serial Port Tool](https://downloads.rakwireless.com/en/LoRa/Tools).

3. Configure the serial communication tool by selecting the proper port detected by the computer and configure the link as follows: 

 * Baud Rate: **9600 baud**
 * Data Bits: **8 bits**
 * Stop Bits: **1 stop bit**
 * Parity: **NONE**

#### Configuring RAK3272S Breakout Board

To enable the RAK3272S Breakout Board as a LoRa P2P board or a LoRaWAN end-device, the board must be configured and parameters must be set by sending AT commands.

The first step is to connect the RAK3272S Breakout Board to the USB port of a computer, as described in the previous section. Using a serial communication tool, you can now send commands to the RAK3272S. For example, sending the `AT` will display `OK`. For the details of all supported AT commands, refer to [AT Commands for RAK3272S](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/AT-Command-Manual/).


### Connecting to The Things Network (TTN)

In this section, a quick tutorial guide will show how to connect the RAK3272S Breakout Board to TTN platform. 

:::tip 📝 NOTE:

In this guide, you need to have a working gateway that is connected to TTN or have a coverage of TTN community network.

:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/4.ttn-context.png"
  width="95%"
  caption="RAK3272S in the context of the TTN"
/>

As shown in Figure 2, The Things Stack (TTN V3) is an open-source LoRaWAN Network Server suitable for global, geo-distributed public and private deployments as well as for small, local networks. The architecture follows the LoRaWAN Network Reference Model for standards compliance and interoperability. This project is actively maintained by [The Things Industries](https://www.thethingsindustries.com/).

LoRaWAN is a protocol for low-power wide-area networks. It allows for large scale Internet of Things deployments where low-powered devices efficiently communicate with Internet-connected applications over long-range wireless connections.

The RAK3272S Breakout Board can be part of this ecosystem as a device, and the objective of this section is to demonstrate how simple it is to send data to The Things Stack using the LoRaWAN protocol. To achieve this, the RAK3272S Breakout Board must be located inside the coverage of a LoRaWAN gateway connected to The Things Stack server. 

#### Registration to TTN and Creating LoRaWAN Applications

1. The first step is to go to [The Things Network platform](https://console.cloud.thethings.network/) and select a cluster, as shown in Figure 3.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_1.png"
  width="100%"
  caption="Selecting Cluster in TTN V3"
/>

2. You can use the same login credentials on the TTN V2 if you have one. If you have no account yet, you need to create one.

To register as a new user to TTN, click on **Login with The Things ID** then select **register** on the next page, as shown in Figures 4 and 5.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_2.png"
  width="100%"
  caption="Login using TTN account"
/>

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_3.png"
  width="100%"
  caption="Registration of new account"
/>

3. You should now be on the step of creating your TTN account. Fill all the necessary details and activate your account.

4. After creating an account, login into the platform using your username/email and password, then click **Submit**, as shown in Figure 6.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_4.png"
  width="100%"
  caption="Logging in to TTN platform"
/>

5. Click **Authorize** to proceed.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_5.png"
  width="100%"
  caption="Authorization to TTN"
/>

6. Now that you are logged in to the platform, the next step is to create an application. Click **Create an application**.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_6.png"
  width="100%"
  caption="Creating TTN application for your LoRaWAN devices"
/>

7. To have an application registered, input first the specific details and necessary information about your application, then click **Create application**.
 
<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_7.png"
  width="100%"
  caption="Details of the TTN application"
/>

8. If you have no error on the previous step, you should now be on the application console page. The next step is to add end-devices to your TTN application.

LoRaWAN specifications enforce that each end-device has to be personalized and activated. There are two options in registering devices depending on the activation mode selected. Activation can be done either via Over-The-Air-Activation (OTAA) or Activation-By-Personalization (ABP).

#### TTN OTAA Device Registration

1. Go to your application console to register a device. To start adding an OTAA end-device, click **+ Add end device**, as shown in Figure 10.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_8.png"
  width="100%"
  caption="Add end device"
/>

1. To register the board, click first **Manually**, then configure the activation method by selecting **Over the air activation (OTAA)** and compatible **LoRaWAN version**. After that, click **Start** button, as shown in Figures 11 and 12.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_9.png"
  width="100%"
  caption="Manually register device to TTN"
/>

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_10.png"
  width="100%"
  caption="Device activation configuration"
/>

3. Then you need to put a unique **End device ID** and EUIs (**DevEUI** and **AppEUI**), as shown in Figure 13. Check if your board has a DevEUI on sticker or QR that you can scan, then use this as the device unique DevEUI.

Optionally, you can add a more descriptive **End device name** and **End device description** about your device.

4. After putting all the details, click **Network layer settings** to proceed on the next step.

:::tip 📝 NOTE:

It is advisable to use a meaningful End device ID, End device name, and End device description that will match your device purpose. The End device ID `rak-device` is for illustration purpose only.

:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_11.png"
  width="100%"
  caption="OTAA Device Information"
/>

5. Next step is to setup **Frequency plan**, compatible **Regional Parameter version**, and **LoRaWAN class** supported. Then you can click **Join settings**.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_12.png"
  width="100%"
  caption="OTAA Configuration"
/>

6. The last step in the registration of a new OTAA end-device is the configuration of the **AppKey**. To get the AppKey, you must click the **generate button**. Then you need to click **Add end device** to finish your new device registration.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_13.png"
  width="100%"
  caption="OTAA AppKey generation and device registration"
/>

7. You should now be able to see the device on the TTN console after you fully registered your device, as shown in Figure 16.

:::tip 📝 NOTE:

- The **AppEUI**, **DevEUI**, and **AppKey** are the parameters that you will need to activate your LoRaWAN end-device via OTAA. The **AppKey** is hidden by default for security reasons, but you can easily show it by clicking the show button. You can also copy the parameters quickly using the copy button.
- The three OTAA parameters on the TTN device console are MSB by default. 
- These parameters are always accessible on the device console page as shown in Figure 16.
:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_14.png"
  width="100%"
  caption="OTAA device successfully registered to TTN"
/>


#### OTAA Configuration for TTN

The RAK3272S Breakout Board supports a series of AT commands to configure its internal parameters and control the functionalities of the board. 

1. To set up the RAK3272S Breakout Board to join the TTN using OTAA, start by connecting the RAK3272S Breakout Board to the Computer (see Figure 1) and open the RAK Serial Port Tool. Select the right COM port and set the baud rate to 9600.

It is recommended to start by testing the serial communication and verify that the current configuration is working by sending these two AT commands:

```
AT
```

```
ATE
```

`ATE` will echo the commands you input to the board, which is useful for tracking the commands and troubleshooting.

You will receive `OK` when you input the two commands. After setting `ATE`, you can now see all the commands you input together with the replies. Try again `AT` and you should see it on the terminal followed by `OK`, as shown in Figure 17.

:::tip 📝 NOTE:

If you haven't received an `OK` or any reply, you need to check if the wiring of your UART lines is correct and if the baud is correctly configured to 9600. Also, you can check if the device is powered correctly. If you are getting power from USB port, ensure that you have a good USB cable.
:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/atstart.png"
  width="90%"
  caption="at+version command response"
/>


2. The next step is to configure the OTAA LoRaWAN parameters in RAK3272S: 

- LoRa work mode: **LoRaWAN**
- LoRaWAN join mode: **OTAA**
- LoRaWAN class: **Class A**
- LoRaWAN region: **EU868** 

Set the work mode to LoRaWAN.

```
AT+NWM=1
```

Set the LoRaWAN activation to OTAA.

```
AT+NJM=1
```

Set the LoRaWAN class to Class A.

```
AT+CLASS=A
```

Set the frequency/region to EU868.

```
AT+BAND=4
```

:::tip 📝 NOTE:

Depending on the Regional Band you selected, you might need to configure the sub-band of your RAK3272S to match the gateway and LoRaWAN network server. This is specially important on Regional Bands like US915, AU915, and CN470.

To configure the masking of channels for the sub-bands, you can use the [AT+MASK command](https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3272S-Breakout-Board/AT-Command-Manual/#at-mask) that can be found on the AT Commands Manual.

To illustrate, you can use use sub-band 2 by sending the command `AT+MASK=0002`.
:::

**List of band parameter options**

| Code     | Regional Band |
| -------- | ------------- |
| 0        | EU433         |
| 1        | CN470         |
| 2        | RU864         |
| 3        | IN865         |
| 4        | EU868         |
| 5        | US915         |
| 6        | AU915         |
| 7        | KR920         |
| 8 or 8-1 | AS923-1       |
| 8-2      | AS923-2       |
| 8-3      | AS923-3       |
| 8-4      | AS923-4       |


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/otaaconfig.png"
  width="90%"
  caption="Configuring LoRa Parameters"
/>


3. After configuration of the LoRaWAN parameters, the next step is to setup the EUIs and key. You need the use the values from the TTN console. 


- Device EUI: **1133557799224466**
- Application EUI: **1000000000000009**
- Application Key: **04FA4E626EF5CF227C969601176275C2**

Set the Device EUI.

```
AT+DEVEUI=1133557799224466
```

Set the Application EUI.

```
AT+APPEUI=1000000000000009
```

Set the Application Key.

```
AT+APPKEY=04FA4E626EF5CF227C969601176275C2
```

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/otaaeuis.png"
  width="90%"
  caption="Configuring LoRa Parameters"
/>

4. After EUI and keys configuration, the device can now join the network and send payload.

```
AT+JOIN=1:0:10:8
```

Join command format: **`AT+JOIN=w:x:y:z`**

| Parameter | Description                                                  |
| --------- | ------------------------------------------------------------ |
| w         | Join command - 1: joining, 0: stop joining.                  |
| x         | Auto-join config - 1: auto-join on power up, 0: no auto-join |
| y         | Reattempt interval in seconds (7-255) - 8 is default.        |
| z         | Number of join attempts (0-255) - 0 is default.              |

5. After 5 or 6 seconds, if the request is successfully received by a LoRa gateway, then you should see `+EVT:JOINED` status reply, as shown in Figure 20.

:::tip 📝 NOTE:

- If the OTAA device join failed, you need to check if your device is within reach of a working LoRaWAN gateway that is configured to connect to TTN. It is also important to check that all your OTAA parameters (DEVEUI, APPEUI, and APPKEY) are correct by using `AT+DEVEUI=?`, `AT+APPEUI=?`, and `AT+APPKEY=?` commands. Lastly, ensure that the antenna of your device is properly connected.

- After checking all the things above, try to join again. 
:::

6. With the end-device properly activated, you can now try to send some payload after successful join.

```
AT+SEND=2:12345678
```

7. Send command format: **`AT+SEND=<port>:<payload>`**

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/otaajoin.png"
  width="90%"
  caption="OTAA Test Sample Data Sent via RAK Serial Port Tool"
/>

8. You can see the data sent by the RAK3272S Breakout Board on the TTN device console *Live data* section. Also, the *Last seen* info should be few seconds or minutes ago.


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/otaasend.png"
  width="100%"
  caption="OTAA Test Sample Data Sent Viewed in TTN"
/>


#### TTN ABP Device Registration

1. To register an ABP device, you need to go to your application console and select the application where you want your device to be added.

2. Then click **+ Add end device**, as shown in Figure 22.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_8.png"
  width="100%"
  caption="Adding ABP Device"
/>

3. To register the board, click first **Manually** then configure the activation method by selecting **Activation by personalization (ABP)**, compatible **LoRaWAN version**, and click **Start** button, as shown in Figures 23 and 24.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_9.png"
  width="100%"
  caption="Manually register device to TTN"
/>

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_1_abp.png"
  width="100%"
  caption="Selecting ABP and LoRaWAN version"
/>

4. At this step, you need to put a unique **End device ID** and **DevEUI**, as shown in Figure 25. Check if your board has a DevEUI on sticker or QR that you can scan then use this as the device unique DevEUI.

Optionally, you can add a more descriptive **End device name** and **End device description** about your device.

5. After putting all the details, click **Network layer settings** to proceed on the next step.

:::tip 📝 NOTE:

It is advisable to use a meaningful End device ID, End device name, and End device description that will match your device purpose. The End device ID `rak-device-abp` is for illustration purpose only.

:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_2_abp.png"
  width="100%"
  caption="ABP Device Information"
/>

6. Next step is to setup **Frequency plan**, compatible **Regional Parameter version**, and **LoRaWAN class** supported. In an ABP device, you also need to generate **Device Address** and **NwkSKey** (Network Session Keys). Then you can click **Application layers settings**

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_3_abp.png"
  width="100%"
  caption="ABP Device Configuration"
/>

7. The last step in the registration of a new ABP end-device is the configuration of the **AppSKey**. To get the AppSKey, you must click the **generate button**. Then you need to click **Add end device** to finish your new device registration.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_4_abp.png"
  width="100%"
  caption="ABP AppSKey generation and device registration"
/>

8. You should now be able to see the device on the TTN console after you fully registered your device, as shown in Figure 28.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/image_5_abp.png"
  width="100%"
  caption="ABP device successfully registered to TTN"
/>

#### ABP Configuration for TTN

1. To set up the RAK3272S Breakout Board to join the TTN using ABP, start by connecting the RAK3272S Breakout Board to the Computer (see Figure 1) and open the RAK Serial Port Tool. Select the right COM port and set baud rate to 9600.

It is recommended to start by testing the serial communication and verify the current configuration is working by sending these two AT commands:

```
AT
```

```
ATE
```

`ATE` will echo the commands you input to the board, which is useful for tracking the commands and troubleshooting.

You will receive `OK` when you input the two commands. After setting `ATE`, you can now see all the commands you input together with the replies. Try again AT and you should see it on the terminal followed by `OK`, as shown in Figure 17.

:::tip 📝 NOTE:

If you haven't received an `OK` or any reply, you need to check if the wiring of your UART lines is correct and if the baud is correctly configured to 9600. Also you can check if the device is powered correctly. If you are getting power from USB port, ensure that you have a good USB cable.
:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/atstart.png"
  width="90%"
  caption="at+version command response"
/>


2. The next step is to configure the ABP LoRaWAN parameters in RAK3272S: 

- LoRa work mode: **LoRaWAN**
- LoRaWAN join mode: **ABP**
- LoRaWAN class: **Class A**
- LoRaWAN region: **EU868** 

Set the work mode to LoRaWAN.

```
AT+NWM=1
```

Set the LoRaWAN activation to ABP.

```
AT+NJM=0
```

Set the LoRaWAN class to Class A.

```
AT+CLASS=A
```

Set the frequency/region to EU868.

```
AT+BAND=4
```

:::tip 📝 NOTE:

Depending on the Regional Band you selected, you might need to configure the sub-band of your RAK3272S to match the gateway and LoRaWAN network server. This is specially important on Regional Bands like US915, AU915, and CN470.

To configure the masking of channels for the sub-bands, you can use the [AT+MASK command that can be found on the AT Commands Manual](https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3272S-Breakout-Board/AT-Command-Manual/#at-mask).

To illustrate, you can use use sub-band 2 by sending the command `AT+MASK=0002`.
:::

**List of band parameter options**

| Code     | Regional Band |
| -------- | ------------- |
| 0        | EU433         |
| 1        | CN470         |
| 2        | RU864         |
| 3        | IN865         |
| 4        | EU868         |
| 5        | US915         |
| 6        | AU915         |
| 7        | KR920         |
| 8 or 8-1 | AS923-1       |
| 8-2      | AS923-2       |
| 8-3      | AS923-3       |
| 8-4      | AS923-4       |


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/abpconfig.png"
  width="90%"
  caption="Configuring LoRa Parameters"
/>

3. After configuration of the LoRaWAN parameters, the next step is to setup the device address and sessions keys. You need the use the values from the TTN console. 

- Device Address: **260BDE80**
- Application Session Key: **A585903A949C2B2D44B55E99E94CB533**
- Network Session Key: **433C7A924F7F6947778FE821525F183A**

Set the Device Address.

```
AT+DEVADDR=260BDE80
```

Set the Application Session Key.

```
AT+APPSKEY=A585903A949C2B2D44B55E99E94CB533
```

Set the Network Session Key.

```
AT+NWKSKEY=433C7A924F7F6947778FE821525F183A
```

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/abpeuis.png"
  width="90%"
  caption="Configuring LoRa Parameters"
/>

4. After EUI and keys configuration, the device can now join the network and send some payload.

```
AT+JOIN=1:0:8:0
```

Join command format: **`AT+JOIN=w:x:y:z`**

| Parameter | Description                                                 |
| --------- | ----------------------------------------------------------- |
| w         | Join command - 1: joining, 0: stop joining.                 |
| x         | Auto-join config - 1: auto-join on powerup, 0: no auto-join |
| y         | Reattempt interval in seconds (7-255) - 8 is default.       |
| z         | Number of join attempts (0-255) - 0 is default.             |


5. With the end-device properly activated, you can now try to send some payload after successful join.

```
AT+SEND=3:12341234
```

Send command format: **`AT+SEND=<port>:<payload>`**

:::tip 📝 NOTE:

- If your LoRaWAN payload didn't reach the TTN, check if your device is within reach of a working LoRaWAN gateway that is configured to connect to TTN. It is also important to check that all your ABP parameters (DEVADDR, APPSKEY, and NWKSKEY) are correct by using `AT+DEVADDR=?`, `AT+APPSKEY=?`, and `AT+NWKSKEY=?` commands. Lastly, ensure that the antenna of your device is properly connected.

- After checking all the things above, try to send LoRaWAN payloads again. 
:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/abpjoin.png"
  width="90%"
  caption="ABP Test Sample Data Sent via RAK Serial Port Tool"
/>

6. You can see the data sent by the RAK3272S Breakout Board on the TTN device console *Live data* section and the *Last seen* info should be a few seconds ago.


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/abpsend.png"
  width="100%"
  caption="OTAA Test Sample Data Sent Viewed in TTN"
/>

### Connecting with ChirpStack

In this section, it shows how to connect the RAK3272S Breakout Board to the ChirpStack platform.


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/23.chirpstack-platform.png"
  width="60%"
  caption="RAK3272S Module in the Context of the ChirpStack Platform"
/>

The ChirpStack or previously known as LoRaServer project provides open-source components for building LoRaWAN networks. Like the case of TTN, the RAK3272S Breakout Board is located in the periphery and will transmit the data to the backend servers through a LoRa gateway. Learn more about [ChirpStack](https://www.chirpstack.io/).

:::tip 📝 NOTE:

It is assumed that you are using RAK Gateway and its built-in ChirpStack. Also, the gateway with the ChirpStack must be configured successfully. For further information, check the RAK documents.

:::

* In summary, these are the requirements: 

  1. Have ChirpStack online gateway, the frequency band of the nodes should be consistent with the frequency band of the gateway in use.
      *	[Connect the Gateway with Chirpstack](/Product-Categories/WisGate/RAK7243/Quickstart/#connect-the-gateway-with-chirpstack)
  2.	The RAK Serial Port Tool provided by RAK
  3.	RAK3272S Breakout Board

:::tip 📝 NOTE:
The frequency band used in the demonstration is EU868. Use a high-frequency version of RAK3272S. The product number should be “**RAK3172 (H)**”.
:::



#### Create a New Application

1. Login to the ChirpStack server using your account and password.

2. Go to the Application section, as shown in the Figure 35.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/24.chirpstack.png"
  width="100%"
  caption="Application Section"
/>

3. By default, you should create a new application, although you can reuse the existing ones. For this setup, create a new Application by clicking on the “**CREATE**” button, and fill the required parameters, as shown in the Figures 36 and 37.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/25.new-application.png"
  width="100%"
  caption="Creating a New Application"
/>


* For this setup, create an Application named “**rak_node_test**”.

ChirpStack LoraServer supports multiple system configurations, with only one by default. 

* **Service profile**: Field is to select the system profile.
* **Payload codec**: It is the parsing method for selecting load data such as parsing LPP format data.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/26.filling-parameters.png"
  width="100%"
  caption="Filling Parameters of an Application"
/>

<b>Register a New Device</b>

1. Choose the **Application** created in the previous step, then select the **DEVICES** tab, as shown in Figures 38 and 39.

2. Once done, click “**+ CREATE**”.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/27.application-available.png"
  width="100%"
  caption="List of Applications Created"
/>


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/28.application-page.png"
  width="100%"
  caption="Device Tab of an Application"
/>

3. Once inside of the DEVICE tab, create a new device (LoRaWAN node) by clicking on the “**+ CREATE**” button. 

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/29.adding-node.png"
  width="100%"
  caption="Add a New Device"
/>

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/30.new-device-registration.png"
  width="100%"
  caption="Chirpstack Adding Node into the RAK3272S Module"
/>


6. Once the node is created, fill-in the necessary data. You can generate a Device EUI automatically by clicking the following icon, or you can write a correct Device EUI in the edit box.

Fill the parameters requested:

* **Device name and Device description**: These are descriptive texts about your device. 

* **Device EUI**: This interface allows you to generate a Device EUI automatically by clicking the generate icon. You can also add a specific Device EUI directly in the form. 

* **Device Profile**: 
  * If you want to join in OTAA mode, select “**DeviceProfile_OTAA**”.
  * If you want to join in ABP mode, select “**DeviceProfile_ABP**”.

:::tip 📝 NOTE:
- Device profiles **DeviceProfile_OTAA** and **DeviceProfile_ABP** are only available if you are using the built-in Chirpstack LoRaWAN Server of RAK Gateways.
- If you have your own Chirpstack installation, you can set up the device profile with `LoRaWAN MAC version 1.0.3` and `LoRaWAN Regional Parameters revision B` to make it compatible with RAK3272S.
:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/31.adding-parameters.png"
  width="100%"
  caption="Generate a New Device EUI "
/>

#### Chirpstack OTAA Device Registration

1. If you have selected “**DeviceProfile_OTAA**”, as shown in Figure 43, then after the device is created, an Application Key must be also created for this device. 

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/32.otaa.png"
  width="100%"
  caption="Chirpstack OTAA Activation"
/>

2. A previously created Application Key can be entered here, or a new one can be generated automatically by clicking the icon highlighted in red in Figure 44.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/33.otaa-set-device-keys.png"
  width="100%"
  caption="Chirpstack OTAA Set Application Keys"
/>

3. Once the Application Key is added in the form, the process can be finalized by clicking on the “**SET DEVICE-KEYS**” button. 

* As shown in Figure 45, a new device should be listed in the DEVICES tab. The most important parameters, such as the Device EUI are shown in the summary.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/34.set-device-eui.png"
  width="100%"
  caption="Chirpstack OTAA List of Device in the Device Tab"
/>

4. To end the process, it is a good practice to review that the Application Key is properly associated with this device. The Application Key can be verified in the **KEYS(OTAA)** tab, as shown in Figure 46.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/35.application-key.png"
  width="100%"
  caption="Application Key Associated with the New Device"
/>

:::tip 📝 NOTE:

Standard OTAA mode requires the **Device EUI**, **Application Key**, and **Application EUI**, but in the ChirpStack’s implementation, only the Device EUI and the Application Key are mandatory. The Application EUI is not required and not recorded in the Application tab. Nevertheless, you can reuse the Device EUI as the Application EUI during the configuration in the side of the node. 

:::

#### OTAA Configuration for Chirpstack

The RAK3272S Breakout Board supports a series of AT commands to configure its internal parameters and control the functionalities of the board. 

1. To set up the RAK3272S Breakout Board to join the Chirpstack using OTAA, start by connecting the RAK3272S Breakout Board to the Computer (see Figure 1) and open the RAK Serial Port Tool. Select the right COM port and set baud rate to 9600.

It is recommended to start by testing the serial communication and verify that the current configuration is working by sending these two AT commands:

```
AT
```

```
ATE
```

`ATE` will echo the commands you input to the board which is useful for tracking the commands and troubleshooting.

You will receive `OK` when you input the two commands. After setting `ATE`, you can now see all the commands you input together with the replies. Try again `AT` and you should see it on the terminal followed by `OK`, as shown in Figure 47.

:::tip 📝 NOTE:

If do not receive an `OK` or any reply, you need to check if the wiring of your UART lines is correct and if the baud is correctly configured to 9600. Also you can check if the device is powered correctly. If you are getting power from USB port, ensure that you have a good USB cable.
:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/atstart.png"
  width="90%"
  caption="at+version command response"
/>

2. The next step is to configure the OTAA LoRaWAN parameters in RAK3272S: 

- LoRa work mode: **LoRaWAN**
- LoRaWAN join mode: **OTAA**
- LoRaWAN class: **Class A**
- LoRaWAN region: **EU868** 

Set the work mode to LoRaWAN.

```
AT+NWM=1
```

Set the LoRaWAN activation to OTAA.

```
AT+NJM=1
```

Set the LoRaWAN class to Class A.

```
AT+CLASS=A
```

Set the frequency/region to EU868.

```
AT+BAND=4
```

:::tip 📝 NOTE:

- Depending on the Regional Band you selected, you might need to configure the sub-band of your RAK3272S to match the gateway and LoRaWAN network server. This is specially important on Regional Bands like US915, AU915, and CN470.

- To configure the masking of channels for the sub-bands, you can use the [AT+MASK command that can be found on the AT Commands Manual](https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3272S-Breakout-Board/AT-Command-Manual/#at-mask).

- To illustrate, you can use use sub-band 2 by sending the command `AT+MASK=0002`.
:::

**List of band parameter options**

| Code     | Regional Band |
| -------- | ------------- |
| 0        | EU433         |
| 1        | CN470         |
| 2        | RU864         |
| 3        | IN865         |
| 4        | EU868         |
| 5        | US915         |
| 6        | AU915         |
| 7        | KR920         |
| 8 or 8-1 | AS923-1       |
| 8-2      | AS923-2       |
| 8-3      | AS923-3       |
| 8-4      | AS923-4       |


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/otaaconfig.png"
  width="90%"
  caption="Configuring LoRa Parameters"
/>


3. After configuration of the LoRaWAN parameters, the next step is to setup the DevEUI and AppKey. You need the use the values from the Chirpstack device console. 

:::tip 📝 NOTE:
The Application EUI parameter is not required in the ChirpStack platform; therefore, it possible to use the same id as the Device EUI. 
::: 

- Device EUI: **5E9D1E0857CF25F1**
- Application EUI: **5E9D1E0857CF25F1**
- Application Key: **F921D50CD7D02EE3C5E6142154F274B2**


Set the Device EUI.

```
AT+DEVEUI=5E9D1E0857CF25F1
```

Set the Application EUI.

```
AT+APPEUI=5E9D1E0857CF25F1
```

Set the Application Key.

```
AT+APPKEY=F921D50CD7D02EE3C5E6142154F274B2
```

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/chirp_otaa_eui.png"
  width="90%"
  caption="Configuring LoRa Parameters"
/>

4. After EUI and key configuration, the device can now join the network and send some payload.

```
AT+JOIN=1:0:10:8
```

Join command format: **`AT+JOIN=w:x:y:z`**

| Parameter | Description                                                 |
| --------- | ----------------------------------------------------------- |
| w         | Join command - 1: joining, 0: stop joining.                 |
| x         | Auto-join config - 1: auto-join on powerup, 0: no auto-join |
| y         | Reattempt interval in seconds (7-255) - 8 is default.       |
| z         | Number of join attempts (0-255) - 0 is default.             |


5. After 5 or 6 seconds, if the request is successfully received by a LoRa gateway, then you should see JOINED status reply.

:::tip 📝 NOTE:

- If the OTAA device join failed, you need to check if your device is within reach of a working LoRaWAN gateway that is configured to connect to Chirpstack. It is also important to check that all your OTAA parameters (DEVEUI and APPKEY) are correct by using `AT+DEVEUI=?` and `AT+APPKEY=?` commands. Lastly, ensure that the antenna of your device is properly connected.

- After checking all the things above, try to join again. 
:::

6. With the end-device properly activated, you can now try to send some payload after successful join.

```
AT+SEND=2:12345678
```

Send command format: **`AT+SEND=<port>:<payload>`**

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/chirp_otaa_send.png"
  width="90%"
  caption="OTAA Test Sample Data Sent via RAK Serial Port Tool"
/>

7. On the ChirpStack platform, you should see the join and uplink messages in the LORAWAN FRAMES tab as shown in Figure 51. By convention, messages sent from nodes to gateways are considered as **Uplinks** while messages sent by gateways to nodes are considered as **Downlinks**. 


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/41.message-received.png"
  width="100%"
  caption="Chirpstack Data Received Preview"
/>

#### Chirpstack ABP Device Registration

1. During the registration of a new device, if you select “**DeviceProfile_ABP**”, as shown in Figure 52, then the ChirpStack platform will assume that this device will join to the LoRaWAN network using the ABP mode. 


:::tip 📝 NOTE:

Check “**Disable counting frame verification**”. During the test, when the board is restarted, the frame counting number will be also be restarted from zero. This would cause a synchronization problem with the ChirpStack server treating it as a replay attack. For the testing purpose, it is safe to disable this feature, but remember to activate it in a production environment.

:::


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/42.configuring-device-abp.png"
  width="100%"
  caption="ChirpStack Console, Configuring a Device"
/>


2. After selecting the ABP mode, the following parameters appear in the Activation tab, then you can see that there are some parameters for ABP in the **“ACTIVATION”** item:

  *	**Device address**
  *	**Network Session Key**
  *	**Application Session Key**

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/43.abp-activation-parameters.png"
  width="100%"
  caption="Chirpstack ABP Activation Parameters Needed"
/>

3. The parameters can be generated as random numbers by the platform or can be set with user values. Once these parameters are filled properly, the process is completed by clicking on the “**ACTIVATE DEVICE**” button.


#### ABP Configuration for Chirpstack

1. To set up the RAK3272S Breakout Board to join the Chirpstack using ABP, start by connecting the RAK3272S Breakout Board to the Computer (see Figure 1) and open the RAK Serial Port Tool. Select the right COM port and set baud rate to 9600.

It is recommended to start by testing the serial communication and verify that the current configuration is working by sending these two AT commands:

```
AT
```

```
ATE
```

`ATE` will echo the commands you input to the board which is useful for tracking the commands and troubleshooting.

You will receive `OK` when you input the two commands. After setting `ATE`, you can now see all the commands you input together with the replies. Try again `AT` and you should see it on the terminal followed by `OK`, as shown in Figure 54.

:::tip 📝 NOTE:

If do not receive an `OK` or any reply, you need to check if the wiring of your UART lines is correct and if the baud is correctly configured to 9600. Also you can check if the device is powered correctly. If you are getting power from USB port, ensure that you have a good USB cable.
:::

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/atstart.png"
  width="90%"
  caption="at+version command response"
/>


2. The next step is to configure the ABP LoRaWAN parameters in RAK3272S: 

- LoRa work mode: **LoRaWAN**
- LoRaWAN join mode: **ABP**
- LoRaWAN class: **Class A**
- LoRaWAN region: **EU868** 

Set the work mode to LoRaWAN. It can be set to P2P as well, but by default, the device is in LoRaWAN mode.

```
AT+NWM=1
```

Set the LoRaWAN activation to ABP.

```
AT+NJM=0
```

Set the LoRaWAN class to Class A.

```
AT+CLASS=A
```

Set the frequency/region to EU868.

```
AT+BAND=4
```

:::tip 📝 NOTE:

Depending on the Regional Band you selected, you might need to configure the sub-band of your RAK3272S to match the gateway and LoRaWAN network server. This is specially important on Regional Bands like US915, AU915, and CN470.

To configure the masking of channels for the sub-bands, you can use the [AT+MASK command](https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3272S-Breakout-Board/AT-Command-Manual/#at-mask) that can be found on the AT Commands Manual.

To illustrate, you can use use sub-band 2 by sending the command `AT+MASK=0002`.
:::

**List of band parameter options**

| Code     | Regional Band |
| -------- | ------------- |
| 0        | EU433         |
| 1        | CN470         |
| 2        | RU864         |
| 3        | IN865         |
| 4        | EU868         |
| 5        | US915         |
| 6        | AU915         |
| 7        | KR920         |
| 8 or 8-1 | AS923-1       |
| 8-2      | AS923-2       |
| 8-3      | AS923-3       |
| 8-4      | AS923-4       |


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/abpconfig.png"
  width="90%"
  caption="Configuring LoRa Parameters"
/>

3. After configuration of the LoRaWAN parameters, the next step is to setup the device address and session keys. You need to use the values from the TTN device console. 

- Device Address: **26011AF9**
- Application Session Key: **4D42EC5CAF97F03D833CDAf5003F69E1**
- Network Session Key: **C280CB8D1DF688BC18601A97025C5488**


Set the Device Address.

```
AT+DEVADDR=26011AF9
```

Set the Application Session Key.

```
AT+APPSKEY=4D42EC5CAF97F03D833CDAf5003F69E1
```

Set the Network Session Key.

```
AT+NWKSKEY=C280CB8D1DF688BC18601A97025C5488
```

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/chirp_abp_key.png"
  width="90%"
  caption="Configuring LoRa Parameters"
/>

4. After EUI and keys configuration, the device can now join the network and send some payload.

```
AT+JOIN=1:0:10:8
```

Join command format: **`AT+JOIN=w:x:y:z`**

| Parameter | Description                                                 |
| --------- | ----------------------------------------------------------- |
| w         | Join command - 1: joining, 0: stop joining.                 |
| x         | Auto-join config - 1: auto-join on powerup, 0: no auto-join |
| y         | Reattempt interval in seconds (7-255) - 8 is default.       |
| z         | Number of join attempts (0-255) - 0 is default.             |

5. After 5 or 6 seconds, if the request is successfully received by a LoRa gateway, then you should see JOINED status reply.

You can now try to send some payload after successful join.

```
AT+SEND=2:12341234
```
Send command format: **`AT+SEND=<port>:<payload>`**

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/chirp_abp_send.png"
  width="90%"
  caption="ABP Test Sample Data Sent via RAK Serial Port Tool"
/>


### LoRa P2P Mode

This section will show you how to set up and connect two RAK3272S units to work in the LoRa P2P mode. The configuration of the RAK3272S units is done by connecting the two boards to a general-purpose computer using a USB-UART converter. The setup of each RAK3272S can be done separately, but testing the LoRa P2P mode will require having both units connected simultaneously. This could be done by having one computer with two USB ports or two computers with one USB port each.

It is recommended to start by testing the serial communication and verify the current configuration is working by sending these two AT commands:

```
AT
```

```
ATE
```

`ATE` will echo the commands you input to the board which is useful for tracking the commands and troubleshooting.

You will receive `OK` when you input the two commands. After setting `ATE`, you can now see all the commands you input together with the replies.

Try again `AT` and you should see it on the terminal followed by `OK`.


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/atstart.png"
  width="90%"
  caption="at+version command response"
/>

1. To setup the RAK3272S to work in LoRa P2P mode, you need to input the work mode command on both RAK3272S Breakout Board.

```
AT+NWM=0
```

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/p2pworkmode.png"
  width="90%"
  caption="P2P Mode"
/>

:::tip 📝 NOTE:

You might need to input `ATE` command again to ensure that your succeeding commands on P2P mode echo on the terminal.

:::

For this P2P setup, the LoRa parameters are the following:

- Link frequency: **868000000&nbsp;Hz**
- Spreading factor: **7**
- Bandwidth: **125&nbsp;kHz**
- Coding Rate: 0 = **4/5**
- Preamble Length: **10**
- Power: **14&nbsp;dBm**

2. Input the P2P setup on both RAK3272S Breakout Board. The parameters should be exactly the same on the two boards. 

```
AT+P2P=868000000:7:125:0:10:14
```

:::tip 📝 NOTE:

Refer to the [P2P Mode](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/AT-Command-Manual/) section of the AT command documentation to learn more about the definition of the parameters used.

:::


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/p2psetup.png"
  width="90%"
  caption="Configuring P2P in both RAK3272S Breakout Board"
/>


2. To set one module as receiver (RX), you need set the value of P2P receive command to 65535.

```
AT+PRECV=65535 
```

:::tip 📝 NOTE:

- If `AT+PRECV` value is set to 65534, the device will continuously listen to P2P LoRa TX packets without any timeout. This is the same as setting the device in RX mode.
- If `AT+PRECV` value is set to 65535, the device will listen to P2P TX without a timeout. But it will stop listening once a P2P LoRa packet is received to save power.
- If `AT+PRECV` value is 0, the device will stop listening to P2P TX data. The device is in TX mode.

:::

With one board configured as RX, the other device will be the TX.

3. You can now try to send a P2P payload.

```
AT+PSEND=11223344
```

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/p2p_txrx.png"
  width="90%"
  caption="Configuring P2P in both RAK3272S Breakout Board"
/>


## Miscellaneous

### Upgrading the Firmware

If you want to upgrade the latest version firmware of the module, you can follow this section. The latest firmware can be found in the software section of [RAK3272S Datasheet](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Datasheet/#firmware-os).

#### Firmware Upgrade Through UART2

##### Minimum Hardware and Software Requirements

Refer to the table for the minimum hardware and software required to perform the firmware upgrade via UART2.

| Hardware/Software | Requirement                                   |
| ----------------- | --------------------------------------------- |
| Computer          | A Windows/Ubuntu/Mac computer                 |
| Firmware File     | Bin firmware file downloaded from the website |
| Others            | A USB to TTL module                           |

##### Firmware Upgrade Procedure

Execute the following procedure to upgrade the firmware in Device Firmware Upgrade (DFU) mode through the USB interface.


1.	Download the latest application firmware of the RAK3172.

    - [RAK3272S Datasheet](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Datasheet/#firmware-os)

2.	Download the RAK Device Firmware Upgrade (DFU) tool.
    - [RAK Device Firmware Upgrade (DFU) Tool](https://downloads.rakwireless.com/LoRa/Tools/RAK_Device_Firmware_Upgrade_tool/)

3.	Connect the RAK3272S Breakout Board to the computer via USB-Serial adapter. Refer to [Figure 1](/Product-Categories/WisDuo/RAK3272S-Breakout-Board/Quickstart/#connect-to-the-rak3172-evaluation-board).

4.	Open the Device Firmware Upgrade tool. Select the serial port and baud rate (9600) of the board and click the "Select Port" button.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/56.device-firmware.png"
  width="80%"
  caption="Device Firmware Upgrade Tool"
/>

5.	Select the application firmware file of the board with the suffix "**.bin**".

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/57.select-firmware.png"
  width="80%"
  caption="Select Firmware"
/>

6.	Click the "**Upgrade**" button to upgrade the device. After the upgrade is complete, the RAK3272S Breakout Board will be ready to work with the new firmware.

<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/58.firmware-upgrading.png"
  width="80%"
  caption="Firmware Upgrading"
/>


<rk-img
  src="/assets/images/wisduo/rak3272s-breakout-board/quickstart/59.upgrade-success.png"
  width="80%"
  caption="Upgrade Successful"
/>





