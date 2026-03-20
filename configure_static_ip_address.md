**IMPORTANT NOTE**\
The `ip address add` command is to temporarily set an IP address on a network interface.\
This means the result of `ip address add` command, and also the results of other `ip` commands are non-persistent. They will be lost after the system is rebooted.\

Please use **nmcli** or **nmtui** to make the network configuration persistent!

- To configure a static IP address on "Wired connection 1" with IP address of 192.168.56.11/24:
  ```
  sudo nmcli connection modify "Wired connection 1" ipv4.method manual ipv4.address 192.168.56.11/24
  ```
- To apply new changes, bring the connection down and up:
  ```
  sudo nmcli connection down "Wired connection 1"
  sudo nmcli connection up "Wired connection 1"
  ```
- To verify:
  ```
  nmcli
  nmcli device status
  nmcli device show
  nmcli connection show
  ```
