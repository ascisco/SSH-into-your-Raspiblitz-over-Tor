

# SSH-into-your-Raspblitz-using-TOR

This guide will instruct you on how to SSH into your Raspiblitz over TOR using an android device.



**Preqeusities:**
- TOR enabled on your Raspiblitz 
- Orbot android app
- An SSH android app (JuiceSSH or Termux)

----------------------------------------------

**Setup SSH Hidden Service**
1. Open the command line terminal on your raspiblitz
2. Open your torrc file
  ```
  sudoedit /etc/tor/torrc
  ```
3. Add the following lines to your torrc file  
  ```
  # SSH Hidden Service
  HiddenServiceDir /mnt/hdd/tor/sshd
  HiddenServiceVersion 3
  HiddenServicePort 22 127.0.0.1:22
  ```
4. Save torrc file and exit back to command line
5. Restart TOR
  ```
  sudo systemctl restart tor
  ```
6. Retrieve your SSH onion address
  ```
  sudo cat /mnt/hdd/tor/sshd/hostname
  ```

----------------------------------------------

**Connect Through Mobile Device**
1. Install and launch Orbot
2. Enable 'VPN mode' and connect to TOR
3. Install and launch your SSH app
4. SSH into your raspiblitz

  For JuiceSSH: Add a new connection
  ```
   - Type: SSH
   - Address: youraddress.onion (from step 6)
   - Identity
      Username: admin
      Password: 'Your Raspiblitz Password A'
   - Port: 22
  ```
  For Termux: Run the following commands
  ```
  pkg install openssh
  ssh admin@youraddress.onion
  ```
5. You should now be connected to your raspiblitz node!

