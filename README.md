# PSENrd 3.1 live and RevPi Connect 4

<div style="display: flex; flex-direction: column; align-items: center;">
    <a href="https://www.pilz.com" rel="nofollow">
        <img src="/img/pilz-logo.png" alt="Pilz Logo">
    </a><br/>
</div>

## Exclusion of Liability

We have taken great care in compiling our application note. It contains information about our company and our products. All statements are made in accordance with the current status of technology and to the best of our knowledge and belief.
While every effort has been made to ensure the information provided is accurate, we cannot accept liability for the accuracy and entirety of the information provided, except in the case of gross negligence. In particular, all information on applicable standards, safety-related classifications and time characteristics should be viewed as provisional. In particular it should be noted that statements do not have the legal quality of assurances or assured properties.
We are grateful for any feedback on the contents.<br/>
May 2026<br/>
All rights to this publication are reserved by Pilz GmbH & Co. KG.
We reserve the right to amend specifications without prior notice. Copies may be made for the user’s internal purposes.
The names of products, goods and technologies used in this manual are trademarks of the respective companies. Please note the current information about the products, their licenses and registered trademarks in the documents listed in [Useful documentation](#1-useful-documentation).<br/>

## Industrial Security

To secure plants, systems, machines and networks against cyberthreats it is necessary to implement (and continuously maintain) an overall &#128279;[Industrial Security concept](https://www.pilz.com/en-INT/products/industrial-security) that is state of the art.
Perform a risk assessment in accordance with VDI/VDE 2182 or IEC 62443-3-2 and plan the security measures with care. If necessary, seek advice from<br/>
&#128279;[Pilz Customer Support](https://www.pilz.com/en-INT/support/technical-support).<br/>

## Definition of Symbols

Information that is particularly important is identified as follows:<br/>

>[!Caution]
>Advises about risks or negative outcomes of certain actions.

>[!Important]
>Key information users need to know to achieve their goal.

>[!Tip]
>Helpful advice for doing things better or more easily.

>[!Note]
>Useful information that users should know, even when skimming content.

## Contents and Setup steps

1.  [Useful documentation and Links to Third-Party Websites](#1-useful-documentation-and-links-to-third-party-websites)<br/>
1.1 [Documentation form Pilz GmbH & Co. KG](#11-documentation-from-pilz-gmbh--co-kg)<br/>
1.2 [Documentation from Kunbus GmbH](#12-documentation-from-kunbus-gmbh)<br/>
2.  [Hardware and software used](#2-hardware-and-software-used)<br/>
2.1 [Pilz products](#21-pilz-products)<br/>
2.2 [Kunbus products](#22-kunbus-products)<br/>
2.3 [Third-party products](#23-third-party-products)<br/>
2.4 [Structure of the application (schematic)](#24-structure-of-the-application-schematic)<br/>
3.  [Preface](#3-preface)<br/>
4.  [Application description](#4-application-description)<br/>
5.  [First steps to start RevPi Connect 4](#5-first-steps-to-start-revpi-connect-4)<br/>
5.1 [Password](#51-password)<br/>
5.2 [Instructions for changing the keyboard settings](#52-instructions-for-changing-the-keyboard-settings)<br/>
5.3 [Automated Installation and Configuration](#53-automated-installation-and-configuration)<br/>
5.4 [Update System packages](#54-update-system-packages)<br/>
5.5 [Using the Firewall](#55-using-the-firewall)<br/>
6.  [Install Mosquitto and Mosquitto-Clients](#6-install-mosquitto-and-mosquitto-clients)<br/>
6.1 [Create certificates (optional)](#61-create-certificates-optional)<br/>
6.2 [Create users and passwords for accessing to the broker ](#62-create-users-and-passwords-for-accessing-to-the-broker)<br/>
6.3 [Create an ACL (Access control list)](#63-create-an-acl-access-control-list)<br/>
6.4 [Configurate Mosquitto Broker](#64-configurate-mosquitto-broker)<br/>
6.5 [Start mosquitto service](#65-start-mosquitto-service)<br/>
7.  [Setup and Configuration NTP Server](#7-setup-and-configuration-ntp-server)<br/>
8.  [WiFi Configuration with guaranteed wpa2 support](#8-wifi-configuration-with-guaranteed-wpa2-support)<br/>
8.1 [Install dnsmasq](#81-install-dnsmasq)<br/>
8.2 [Set up WiFi connection](#82-set-up-wifi-conncetion)<br/>
8.3 [Set up WiFi and BT](#83-set-up-cockpit-revpi-connect-4-wifi-and-bt)<br/>
9.  [Testing of Data exchange](#9-testing-of-data-exchange)<br/>
10. [Integration of a python program](#10-integration-of-a-python-program)<br/>
10.1 [Work with USB-Stick](#101-work-with-usb-stick)<br/>
10.2 [Install additional Python packages and graphical packages](#102-install-additional-python-packages-and-graphical-packages)<br/>
10.3 [Start the GUI in the graphical interface](#103-start-the-gui-in-the-graphical-interface)<br/>
11. [Work with remote desktop connection (RDP)](#11-work-with-remote-desktop-connection-rdp)<br/>
11.1 [Create a new network IP-Address](#111-create-a-new-network-ip-address)<br/>
11.2 [Install xrdp and xorg xrdp](#112-install-xrdp-and-xorg-xrdp)<br/>
11.3 [Using the remote desktop connection](#113-using-the-remotedesktop-connection)<br/>
12. [License Information](#12-license-information)<br/>

## 1. Useful documentation and Links to Third-Party Websites

Reading the documentations listed below is necessary for understanding this Application.<br/>
The availability of the software used, and its safe handling are also presupposed for the user.<br/>
<br/>
The scenario described below illustrates a possible application example for using the Pilz product PSENrd 3.1 live in conjunction with third-party system. For further information on the third-party system, please refer to the documentation provided by the respective manufacturer. The links provided refer to external third-party content. The respective provider is solely responsible for the content, timeliness, and availability of that content.

### 1.1 Documentation from Pilz GmbH & Co. KG

|Nr.| Discription | Part number/ Download|
|---| ------------| ---------------------|
| 1 | Pilz international website, download section | &#128279;[www.pilz.com >EN Support >Downloads](https://www.pilz.com/en-INT/support/downloads)<br/>&#128279;[www.pilz.com > DE Support > Downloads](https://www.pilz.com/de-INT/support/downloads)<br/> |
| 2 | Operating manual of PSEN rd3.1 live| The documentation is currently still being prepared and will be made available at a later date. We will inform you as soon as it is available. |

### 1.2 Documentation from Kunbus GmbH
|Nr.| Discription | Part number/ Download|
|---| ------------| ---------------------|
| 1 | Product Description of RevPi Connect 4 |&#128279;[www.revolutionpi.com >EN](https://revolutionpi.com/en/docs/revpi-connect-4)<br/>&#128279;[www.revolutionpi.com >DE](https://revolutionpi.com/de/docs/revpi-connect-4)<br/> |

<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 RevPi Connect 4_en_docs_.png and RevPi Connect 4_de_docs.png -->

## 2. Hardware and software used

### 2.1 Pilz products

|Nr.| Discription | Order number| Version| Quantity|
|---| ------------|-------------| -------| --------|
| 1 | PSENrd      | 6B000017    |  3.1   |    1    |
| 2 | PSEN op cable axial M12 5-pole, 3m| 630310 | - | 1 |

### 2.2 Kunbus products

|Nr.| Discription | Order number| Version| Quantity|
|---| ------------|-------------| -------| --------|
| 1 | RevPi Connect 4| 100380   |  4     |    1    |

> [!IMPORTANT]
> We only use the RevPi Connect 4 (100380) here for the application with WiFi network. Because the RevPi Connect 4 (100380) has a WiFi antenna connection.<br/> 

### 2.3 Third-party Equipment

|Nr.| Discription | Order number| Version| Quantity|
|---| ------------|-------------| -------| --------|
| 1 |   Monitor   |      -      |    -   |    1    |
| 2 |   Keyboard  |      -      |    -   |    1    |
| 3 |   Mouse     |      -      |    -   |    1    |
| 4 | Micro-HDMI adapter |  -   |    -   |    1    |
| 5 | HDMI cable for the Monitor| -  | - |    1    |
| 6 | Antenna (optional)|   -   |    -   |    1    |
| 7 | Ethernet cable |      -   |    -   |    1    |

### 2.4 Structure of the application (schematic)

<div style="display: flex; flex-direction: column; align-items: center;">
        <img src="/img/RevPI4_and_PSENrd3_1_live.png" alt="Structure of the application (schematic)" width="800">
    </a><br/>
</div>

## 3. Preface

This application basically describes the commissioning process of a PSENrd 3.1 with an RevPi Connect 4. Both devices communicate with each other using MQTT.
Data is sent from the PSENrd 3.1 to the internal access point of the RevPi Connect 4. This data is sent to the Python program provided and processed there.<br/>
The basic procedure for successful basic configuration is shown here step-by-step, mostly using command lines. The operating system used is Debain GNU/Linux 12 (bookworm-arm64.img). &#128279;[www.revolutionpi.com >Operating System-Images](https://revolutionpi.com/en/docs/revpi-bookworm)<br/> 

<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 -> revolutionpi.com_en_docs_revpi_bookworm.png -->

> [!IMPORTANT]
> This document only describes the procedure for using the RevPi Connect 4 (100380) and PSENrd 3.1 (6B000017) and does not constitute technical documentation on the general use of the operating system Linux and the program language Python. The operating system and the programming language are basic requirements for this application.

## 4. Application description

The example here shows people counting to determine whether one or more people are present in a monitored area.<br/>

There are several requirements for the realization of this application:<br/>

+ Data transmission takes place via MQTT.<br/>
+ Evaluation of the sensor data in the RevPi Connect 4 in real time.<br/>
+ Recording of personal data in a specific area.<br/>
+ All persons detected by the PSENrd 3.1 sensor are recorded and processed by the RevPi Connect 4.<br/>

Non-functional requirements:<br/>

+ Stability and reliability of the system.<br/>
+ Simple setup and handling of the operating system on the RevPi Connect 4.<br/>

The structure of the system and components is based on:<br/>
[2.4 Structure of the application (schematic)](#24-structure-of-the-application-schematic)<br/>

## 5. First Steps to start RevPi Connect 4

### 5.1 Password 

> [!Important]
> Depending on how this network access is secured, strangers may also be able to log into the device and gain access to data and all functions. Therefore, always choose a
<ins>"strong"</ins> password and work in "headless" mode, i.e. only access the network from devices that you know. Unknown devices could, for example, log keystrokes and thus spy on your login data. 

+ First of all, connect the RevPi Connect 4 to a monitor. A micro HDMI is available on the RevPi Connect 4.<br/>
+ Connect a keyboard via the RevPi Connect 4 USB ports.<br/>
+ Start the RevPi Connect 4 with the 24VDC supply. The RevPi Connect 4 then boots up.<br/>
+ Open the Cockpit. Please follow for this topic the instructions Configuration with Cockpit &#128279;[Configuration with Cockpit](https://revolutionpi.com/en/docs/cockpit)<br/>
+ Follow the instructions under accounts and password managemant &#128279;[Accounts and Password Management](https://revolutionpi.com/en/docs/cockpit#accounts)<br/>
+ Follow the instructions under changing password &#128279;[Changing Password](https://revolutionpi.com/en/knowledge/login-via-terminal#change-pswd)<br/>

<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 -> revolutionpi.com_en_docs_cockpit.png -->
<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 -> revolutionpi.com_en_docs_cockpit_accounts.png -->
<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 -> revolutionpi.com_en_knowledge_login_via_terminal_change_pswd.png -->

> [!Tip]
> When you enter password, the letters and special characters are not displayed.

> [!Tip]
> The letter l (small L) can easily be confused with the number 1 (one). Make sure you use the correct character.<br/>

### 5.2 Instructions for changing the keyboard settings

+ Open the Cockpit.
+ Configure under regional settings your time zone.

> [!Tip]
> On the English keyboard, the character - (hyphen) corresponds to the character ? (question mark). Make sure you take this into account when entering.

> [!Tip]
> Try whether the setting has worked. for example press Y or Z.

### 5.3 Automated Installation and Configuration

> [!Tip]
> Connect your RevPi Connect 4 to the Internet for the first time via the Ethernet interface. Please use the right Ethernet port.

+ Open the Cockpit.
+ Under Tools you can open Terminal.
+ In the next steps, the work will be done in the terminal.


As an alternative to manually performing the steps described in this document, an installation script is available. This script automates the installation of all required packages as well as the configuration of the necessary services and components.<br/>
To do this, use the “Installation_and_Configuration_Script.sh” script. You find the Script in the table. Please follow the instructions in the script. These are commented out with a hashtag "#".<br/>

+ Once you have finished making changes to the script. For example place the script in your home directory in your Linux system. Follow the instructions under [10.1 Work with USB-Stick](#101-work-with-usb-stick) and replace the file name there as appropraite. Start at the point "Insert your USB stick into one of the two USB ports. Check the name of the USB with the command:"

+ Go to the folder where your script is located.
+ run the following command:
```
chmod +x Installation_and_Configuration_Script.sh
```
```
sudo ./Installation_and_Configuration_Script.sh
```
+ It will take about 10 minutes for the script to complete the installations and configurations.

+ Once the script is finished, you no longer need to perform the following steps. This script handled them automatically. The remaining steps are important only for verification purposes.

### 5.4 Update System packages

+ Follow the instructions under Firmware Updates for Expansion Modules &#128279;[Firmware Updates for Expansion Modules](https://revolutionpi.com/en/docs/firmware-updates)

<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 ->  revolutionpi.com_en_docs_firmware_Update.png-->

### 5.5 Using the Firewall 

+ Follow the instructions under Firewall &#128279;[Firewall](https://revolutionpi.com/en/knowledge/firewall)

<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 ->  revolutionpi.com_en_docs_firewall.png-->

## 6. Install Mosquitto and Mosquitto-Clients
<!--[Text for Mosquitto and mqtt here]-->
+ Install Mosquitto and Mosquitto-Clients:
```
sudo apt-get install mosquitto mosquitto-clients
```
### 6.1 Create certificates (optional)

> [!Tip]
> This step is required only when using self-signed certificates.

+ Install OpenSSL:
```
sudo apt-get install openssl
```
1. Create a folder on your broker/server for example in your home directory in which you save the Certificates:<br/>
```
mkdir certs
```
```
cd certs
```
2. Create a private key:
```
openssl genrsa -out server.key 2048
```
> [!Note]
> create a private RSA-key with 2048 bit.

3. Create certificate signing request (CSR):
```
openssl req -new -key server.key -out server.csr
```
> [!Note]
> You will be asked for information such as country, organization, common name (IP address).

4. Create self-signed certificate: 
```
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
```
Creates a certificate that is valid for 365 days.

### 6.2 Create users and passwords for accessing to the broker 
```
sudo mosquitto_passwd -c /etc/mosquitto/passwd PSENrd3_sensor
```
```
sudo mosquitto_passwd -b /etc/mosquitto/passwd PSENrd3_admin <password for that user>
```
```
sudo mosquitto_passwd -b /etc/mosquitto/passwd PSENrd3_consumer <password for that user>
```
> [!Tip]
> We recommend using the suggested usernames. The less-than signs and greater-than signs, "<>" do not need to be written.

> [!Note]
> -c: create a new password file (overwrites an existing file).<br/>
  -b: sets the user and password directly in the command (password in plain text)

> [!Important]
> If you use other usernames, please customize the usernames in the step [6.3 Create an ACL list](#63-create-an-acl-access-control-list)

### 6.3 Create an ACL (Access control list)

1. Create an ACL-File:<br/>
```
sudo nano /etc/mosquitto/aclfile
```
2. Write the ACL-Rules in the ACL-File:
```
# PSENrd3_sensor: Read (commands, config, details, positionData); Write (details, positionData, handoff)
user PSENrd3_sensor
topic read /PSENrd3/+/commands
topic read /PSENrd3/+/handoff
topic read /PSENrd3/+/config
topic read /PSENrd3/+/details
topic read /PSENrd3/+/positionData
topic write /PSENrd3/+/details
topic write /PSENrd3/+/positionData
topic write /PSENrd3/+/handoff

# PSENrd3_admin: Read (commands, config, details, positionData); Write (commands, config)
user PSENrd3_admin
topic read /PSENrd3/+/commands
topic read /PSENrd3/+/config
topic read /PSENrd3/+/details
topic read /PSENrd3/+/positionData
topic write /PSENrd3/+/commands
topic write /PSENrd3/+/config

# PSENrd3_consumer: Read (details, positionData)
user PSENrd3_consumer
topic read /PSENrd3/+/details
topic read /PSENrd3/+/positionData
```
> [!Important]
> If you used another usernames, please customize the usernames in the ACL-File.

### 6.4 Configurate Mosquitto Broker

1. Open the mosquitto config-file:<br/>
```
sudo nano /etc/mosquitto/mosquitto.conf
```
2. Add the following lines:<br/>
```
listener 8883

cafile </path/to/certs>/ca.crt
certfile </path/to/certs>/server.crt
keyfile </path/to/certs>/server.key

require_certificate false
use_identity_as_username false
allow_anonymous false

password_file /etc/mosquitto/passwd
acl_file /etc/mosquitto/aclfile
```
> [!Important]
> Make sure that you enter the correct path to the <ins>certs</ins> folder where the certificates can be found.<br/>
> **cafile </path/to/certs>/ca.crt**, this configuration line is only used if an existing certificate is available.

> [!Tip]
> The less-than signs and greater-than signs, "<>" do not need to be written.

### 6.5 Start mosquitto service
```
sudo systemctl start mosquitto
```
```
sudo systemctl enable mosquitto
```
```
sudo systemctl status mosquitto
```
> [!Note]
> If the mosquitto service shows an error on starting then it could be that you should make sure that the certificates have the correct authorizations and are readable for the Mosquitto service. To do that you can try:

> [!Important]
> You do not need the first command line if you are using a self-signed CA-Certifcate.
```
sudo chown mosquitto:mosquitto </path/to/certs>/ca.crt
```
```
sudo chown mosquitto:mosquitto </path/to/certs>/server.crt
```
```
sudo chown mosquitto:mosquitto </path/to/certs>/server.key
```
```
sudo systemctl restart mosquitto
```
> [!Tip]
> The less-than signs and greater-than signs, "<>" do not need to be written.

## 7. Setup and Configuration NTP Server

+ Follow the instructions under NTP &#128279;[Network Time Protocol](https://revolutionpi.com/en/knowledge/ntp)

<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 ->  revolutionpi.com_en_doc_ntp.png-->

## 8. WiFi configuration with guaranteed WPA2 support

### 8.1 Install dnsmasq

+ To enable the automatic connection of WiFi devices, we need the dnsmasq package, which acts as a DHCP server.

Install package:
```
sudo apt install dnsmasq
```
>[!Tip]
> Confirm with Y key.

+ Open the configuration file: 
```
sudo nano /etc/dnsmasq.conf
```
+ Add the following example configuration in this file: (scroll all the way down with the down button)
```
interface=wlan0
dhcp-range=192.168.0.50,192.168.0.150,12h
```
+ Save the config.file and exit to start dnsmasq:
```
sudo systemctl restart dnsmasq
```
```
sudo systemctl enable dnsmasq
```
+ Control the dnsmasq.service via status:
```
sudo systemctl status dnsmasq
```
+ The status shows you that the dnsmasq service is active.

### 8.2 Set up WiFi Connection 

>[!Important]
>To use a secure WLAN network, please install the hostapd package. This is required to use the WPA2 security protocol. The procedure is explained in detail in the following section.

+ Install packages:
```
sudo apt update
```
```
sudo apt upgrade
```
```
sudo apt install hostapd
```
hostapd is a package that allows you to create a router in your RevPi Connect 4 to later ensure the WPA2 protocol. <br/>

+ Create a configuration file:
```
sudo nano /etc/hostapd/hostapd.conf
```
+ Please write the following settings in this file:
```
interface=wlan0
driver=nl80211
ssid=<YourNetworkName>
hw_mode=g
channel=6
wmm_enabled=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=<YourPassword>
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

ap_max_inactivity=5
disassoc_low_ack=1
```
> [!Tip]
> The less-than signs and greater-than signs, "<>" do not need to be written.

>[!Note]
>In your application, make sure that the settings for commissioning are sufficiently secure (security).<br/>

+ Save the file an exit the file.

>[!Note]
>After installation, the hostapd service is hidden by default on many systems. This prevents the access point from being started accidentally before network configuration is complete. Before putting the system into operation, the service must therefore first be unhidden and then.

+ Please unmask the hostapd service using the following command:
```
sudo systemctl unmask hostapd 
```
+ Enable the hostapd service with: 
```
sudo systemctl enable hostapd
```
+ Start the hostapd service:
```
sudo systemctl start hostapd
```
+ Control the status of hostapd:
```
sudo systemctl status hostapd
```
+ Create a new file for the Configuration of wlan0:
```
sudo nano /etc/network/interfaces.d/wlan0
```
+ Please write the following settings in this new file:<br/> (The following settings are an example, please use your IP addresses)
```
auto wlan0
iface wlan0 inet static
    address 192.168.0.1
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
```    
+ Save the file an exit the file.<br/>

The next step is to create a new file in the NetworkManager folder. Please follow the instructions.

>[!Note]
>The 99-unmanaged-devices.conf file is used to configure certain network devices so that they are ignored by NetworkManager. This setting forces the use of the WPA2 security protocol.

+ Create the following configuration file:
```
sudo nano /etc/NetworkManager/conf.d/99-unmanaged-devices.conf
```
+ Please write the following settings in this file:
```
[keyfile]
unmanaged-devices=interface-name:wlan0

[device]
wifi.scan-rand-mac-address=no
```
+ Save the file an exit the file.

+ Please restart the NetworkManager:
```
sudo systemctl restart NetworkManager.service
```
+ Control the status of the NetworkManager to see if it is activated.
```
sudo systemctl status NetworkManager.service
```
>[!Note]
>The WPA2 security protocol is now guaranteed to be used.

### 8.3 Set up Cockpit-RevPi Connect 4 WiFi and BT

Please follow for this topic the instructions Configuration Wifi and BT. &#128279;[Set up WiFi and BT](https://revolutionpi.com/en/docs/revpi-connect-4#wlan-bt)

<!--screenshot unter PSENrd_3 -> Documents -> Screenshot_GitHub_Appl_with_RevPi4 ->  revolutionpi.com_en_docs_wlan_bt.png-->

>[!Tip]
>When you connect the WiFi the first time, please control in your Network Manager "sudo nmtui" whether the RevPi Connect 4 find your desired WiFi. This Tip belongs to the subitem [5.3 Update System packages](#53-update-system-packages).

>[!Tip]
>Use a WiFi endpoint device, e.g. a smartphone, and check whether you can see the new WiFi connection in your WiFi settings. Click on it and connect and see if you are then in the WiFi. You can see this by the checkmark and the WiFi icon.

## 9. Testing of Data exchange 

<!--[!Important]
>Before you start exchaning data, please read or note the operating manual.
-->

+ You can start by checking whether you can connect the RevPi Connect 4 system to the PSENrd 3.1. First restart the RevPi Connect 4:
```
sudo reboot
```
>[!Tip]
>General tip, restarting the system is very important for many new installations. Restart the RevPi Connect 4 from time to time.

>[!Tip]
>Again, remember the synchronization time of the NTP service.

+ The tail -f command is used to display the last lines of a file in real time. If you use it with Mosquitto, you can monitor the log file of the Mosquitto broker to see current activities and messages.
```
sudo tail -f /var/log/mosquitto/mosquitto.log
```
+ You can find for example the information in the table:

New client connection from IP-Address: Portnumber as ID (p2, c1, k120).

+ The next step is to press Ctrl + C to exit the currently running command or process and return to the command line to enter new commands.
+ We need the first test whether the sensor sends data to the RevPi Connect 4.
```
mosquitto_sub -p 8883 -h <IP-Address> --cafile </path/to/certs>/server.crt> -t '/PSENrd3/<ID OF YOUR SENSOR>/positionData' -u <username> -P <password> 
```
>[!Important]
>If you already have an existing certificate, please replace "sever.crt" to "ca.crt" and specify the path to "ca.crt".

>[!Tip]
>Use your wlan0 IP-Address for this command.

>[!Tip]
>For the Path to your CA file, use your lines from the point [6.4 Configurate Mosquitto Broker](#64-configurate-mosquitto-broker).

>[!Tip]
>You will find the 12-digit ID on the back of the sensor (The Mac-Adress without colon and capital letters).

>[!Tip]
>Use for username and password your settings from point [6.2 Create users and passwords for accessing to the broker](#62-create-users-and-passwords-for-accessing-to-the-broker).

> [!Tip]
> The less-than signs and greater-than signs, "<>" do not need to be written.

+  Position data should then gradually appear on your shell.

## 10. Integration of a python program   

>[!Note]
>The follow description shows how to get a possible python program into an IndustrialPI 4. The possible procedure for a Python program is described in detail.
<!--
>[!Note]
>We greate a graphical python program for this application. This graphical Python program displays recognized people and counts them. The program can be found in the table at the top of this repository.-->
 
### 10.1 Work with USB-stick

>[!Important]
>Make sure that the USB stick comes from a trustworthy source and has not been used before on potentially compromised systems. The stick should be checked or reformatted before use to ensure maximum security.
<!--
>[!Note]
>The follow description shows how to copy the Python program from the GitHub repository (https://github.com/PilzDE/PSENrd3.1_live_and_RevPi_Connect_4) of your workstation notebook to any USB stick and then integrate it into your RevPi Connect 4 system. Please copy the raw file of the Python program from the GitHub repository Samples and insert it into a suitable tool. Save the file and copy the program to your USB stick.-->

+ Python is already available on this oparting system. You can view the current Python version with the following command:
```
python3 --version
```
+ Create a new folder for your python-program for example in your home directory:
```
mkdir ~/my_python_program
```
+ Insert your USB stick into one of the two USB ports. Check the name of the USB with the command:
```
lsblk
```
>[!Tip]
>In the last column of this table you will see the name of the mount point for your USB device, e.g. /media/usb.

+ Create a folder for your USB Devices under the media directory: 
```
sudo mkdir /media/usb
```
+ Mount the example USB into your system:
```
sudo mount /dev/sda1 /media/usb
```
<!--Hier wird später das Sample erläutert.Das "possible_python_program.py ist ein Beipsiel-->
+ Copy the supplied program in this new folder for example from a stick:
```
sudo cp /media/usb/possible_python_program.py /home/pi/my_python_program
```
+ After you have copied your program you could umount the USB stick:
```
sudo umount /dev/sda1
```
The next step is to change the correct mac-address and path.<br/>
+ Open the python program:
```
sudo nano /home/pi/my_python_program/possible_python_program.py
```
+ Change the mac-address where the "XXXXXXXXXXXX" are located.

>[!Tip]
>You will find the 12-digit Mac address on the back of the sensor.

+ Change the path of your certificates markes with "/XXX/XXX/XXX/XXX" as well.

+ Save the file and exit.

### 10.2 Install additional Python packages and graphical packages  
For the possible python program you need a Python package for installation for execution.<br/>
+ Install tkinter:
```
sudo apt-get install python3-tk
```
+ Install matplotlib:
```
sudo apt-get install python3-matplotlib
```
>[!Tip]
>Confirm both installations with Y.

Several steps are required for the graphical interface.

+ Open the file bash.bashrc:
```
sudo nano /etc/bash.bashrc
```
+ Write the line "export DISPLAY=:0.0" at the bottom after the content of this file.<br/>
```
export DISPLAY=:0.0
```
+ Save the file and exit.
+ Restart this file:
```
source /etc/bash.bashrc
```
+ Control whether the $DISPLAY varibale is set correctly:
```
echo $DISPLAY
```
+ This Commando should return :0.0.

+ Next step is to install the so called x Sever for the graphical window of your Linux system.
```
sudo apt update
```
```
sudo apt upgrade
```
```
sudo apt install xorg
```
>[!Tip]
>Requests that are answered with y or n must continue with y. Press q if when asked.

### 10.3 Start the GUI in the graphical interface
+ Start the graphical interface with:
```
startx
```
+ There will open a new window with a new commando line. Now you can use a mouse in this shell. Click behind the Commoando line.
+ Change at first your keyboard language again. For example Germany (de):
```
setxkbmap de
```
>[!Tip]
>Try whether the setting has worked. For example press Y or Z.

Enlarge the display:<br/>
+ Held down with the ctrl key and right mouse button, a menu with unicode fonts will appear.
+ Navigate with the mouse to your desired font size.<br/>(Hold down the ctrl key and the right mouse button the whole time.)

+ Change into the directory: 
```
cd /home/pi/my_python_program
```
+ Execute the python program:
```
python3 possible_python_program.py
```
<!--+ You should now see a yellow GUI with a gray range area showing whether your sensor is connected. You have a counter in the yellow area.-->

## 11. Work with remote desktop connection (RDP)

In this discription, you will use the system via remotedesktop at your workstation with an Ethernet connection. The Requirement for this is that you need a terminal program for example PuTTY. The Remotdesktop- Connection is available on a Windows PC by default.<br/>
>[!Important]
>Observe the specifications of commissioning (security) for your application, in particular the removal of the separation of networks with defferent IP addresses. 

### 11.1 Create a new Network IP-Address

First of all, you need a new Network IP-Address for the Remotedesktop Connection. For example change the third number in your IP-Address, as before. The reason in this case is, if you have the IP-Address in the same network the WLAN connection will be interrupt between PSENrd 3.1 and IndustrialPI 4.<br/> 

+ Please use the Network Manager:
```
sudo nmtui
```
+ Select the option edit a connection.
+ In this case select under Ethernet the first wired connection.
+ Enter the automatic behind the IPv4 configuration and select manual.
+ One line will show up for the new IP-Address.
+ Please enter your Ethernet IP-Address in this line. For example 192.168.1.109/24.
+ Then you can click OK in the right corner.
+ Reboot the system:
```
sudo reboot
```

### 11.2 Install xrdp and xorg xrdp

+ Install the packages xrdp and xorg xrdp:
```
sudo apt install xrdp xorgxrdp
```
+ Reboot the system:
```
sudo reboot
```
<!--
>[!Tip]
>Integrate the Port Number 3389/tcp in the rules list of ufw. The Port number is the typical standard Port number of the RDP (Remote Desktop Protokoll) from Windows.
 ```
 sudo ufw allow 3389/tcp
 ```
-->
### 11.3 Using the Remotedesktop-Connection

Connect the IndustrialPI 4 to your laptop via Ethernet cable. Then search for the Remote Desktop Connection in your search bar in your operating system.<br/>
+ A small Window with an input line opens. 
+ Please enter your Ethernet IP-Address there.
+ An identity question is displayed.
>[!Important]
>In your application, make sure that the settings for commissioning are sufficiently secure (security).
+ Please click Yes.
+ After that a login query will open.
+ Please enter your username and your password of your IndustrialPI 4.
+ Now the graphical desktop opens directly.
+ If you want to use the python program you need a different display number.
+ You can find this number in a file it names "xrdp-sesman.log". 
```
sudo nano /var/log/xrdp-sesman.log
```
+ In the fourth line you will find the IP address of your PC. At the bottom of this file you will find the display number, in this case the number 10 is available.
+ Exit this file with ctrl + X.
+ Change the DISPLAY number:
```
export DISPLAY=:10.0
```
+ Control the change with:
```
echo $DISPLAY
```
Now you can start the python program on the remote desktop connection.<br/>

## 12. License Information

>[!Note]
>This Documentation is licensed under the CC-BY-ND-4.0.txt- see the LICENSE file for details. Here you will find a short description about the LICENSE &#128279;(https://creativecommons.org/licenses/by-nd/4.0/).
>Furthermore, the code snippets and the "Installation_and_Configuration_Script.sh" are subject to the LICENSE CC0-1.0.txt- see the LICENSE file for details. Here you will find a short description about the LICENSE &#128279;(https://creativecommons.org/publicdomain/zero/1.0/).

Copyright (c) 2025 Pilz GmbH & Co. KG<br/>