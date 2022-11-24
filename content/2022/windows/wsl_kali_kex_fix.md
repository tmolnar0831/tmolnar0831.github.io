Title: Fixing the "Error connecting..." issue in Kali KeX on WSL
Date: 2022-11-24 09:00
Modified: 2022-11-24 10:00
Category: Windows
Tags: windows, wsl, howto, kali, kex
Slug: fixing-kali-kex
Authors: Tamas Molnar

Requirements:

1. Kali distro is installed
1. KeX is installed
1. Kali is WSL version 2
1. Coffee is ready for consumption

Time to time the Kali desktop on WSL stops working and spits out the following message:

```
Error connecting to the KeX server.
Please try "kex start" to start the service.
If the server fails to start, please try "kex kill" or restart your WSL2 session and try again.
```

Certainly the "solution" from the error message does not work.

In my case the socket for the VNC server "stuck" and it causes the isse, so my solution is:


In the **Kali terminal**:
```
sudo rm -rf /tmp/.X1-lock
```

Then in **PowerShell** I shut down every running instance:
```
wsl --shutdown
```

After it starting a Kali will be able to start the TigerVNC server and the connection will work. Just use

```
kex
```

If you have a comment or other opinion, visit [Tom's IT Cafe Discord Server](https://discord.gg/YbSYGsQYES) and share it!