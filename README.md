

# SSH-into-your-Raspiblitz-over-TOR

This guide will instruct you on how to SSH into your Raspiblitz over TOR using an android device.



**Prerequisites:**
- TOR enabled on your Raspiblitz 
- Tor Android app Orbot
- SSH Android app JuiceSSH

----------------------------------------------

**Setup SSH Hidden Service**
1. Open the command line terminal on your raspiblitz
2. Open your torrc file
  ```
  sudo nano /mnt/hdd/app-data/tor/torrc.d/services
  ```
3. Add the following lines to your torrc file  
  ```
  # Hidden Service for SSH
  HiddenServiceDir /mnt/hdd/tor/sshd
  HiddenServiceVersion 3
  HiddenServicePort 22 127.0.0.1:22
  ```
4. Exit and save the changes to the file.
5. Restart TOR
  ```
  sudo systemctl restart tor
  ```
6. Retrieve your .onion address
  ```
  sudo cat /mnt/hdd/tor/sshd/hostname
  ```

----------------------------------------------

**Connect Through Mobile Device**

For **JuiceSSH**
  1. Open Orbot and enable VPN mode
  2. Connect to TOR
  3. Launch JuiceSSH app
  4. Manage Connections -> New Connection
  ```
   - Nickname: Raspiblitz
   - Type: SSH
   - Address: youraddress.onion (from previous step 6)
   - Identity
      Username: admin
      Password: 'Your Raspiblitz Password A'
   - Port: 22
  ```
  5. Save settings and connect

You should now be connected to your raspiblitz node!

