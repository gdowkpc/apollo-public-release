# Set up Apollo on a Raspberry Pi

**Build 93 · Bootstrap R5 — test release.** Final hardware testing is still in progress. R5 fixes the installation error in R3 and R4; Build 93 and Node Agent 51 are unchanged.

You'll need a Raspberry Pi 4 Model B or Raspberry Pi 5 Model B, a fresh microSD card, power supply, an RTL2832U USB receiver and antenna, and a computer on the same network. This guide uses your computer to set up the Pi; a monitor and keyboard for the Pi are optional.

## 1. Prepare the microSD card

**If R3 or R4 stopped during installation:** keep that card intact for diagnosis and use a different freshly imaged card. Do not rerun the installer on the partially installed card.

Install [Raspberry Pi Imager](https://www.raspberrypi.com/software/) on your computer and insert the new card.

In Imager:

- Choose your board (**Raspberry Pi 4** or **Raspberry Pi 5**) and **Raspberry Pi OS (64-bit)**, based on Debian 13 (Trixie). The 32-bit OS and Bookworm are not supported by this installer.
- Select your new microSD card. Writing the image erases that card.
- Set the hostname to **apollo-pi** and username to **pi**. Choose a password for the Pi.
- Enter your Wi-Fi details, or plan to connect an Ethernet cable.
- Enable **SSH** with password authentication.
- Write the image and wait for verification to finish.

## 2. Start the Pi

With the Pi powered off, insert the prepared card. Connect the receiver, antenna and Ethernet cable if using one, then turn on the power. Allow a few minutes for the first boot.

On your computer, open **Terminal** (Windows Terminal on Windows) and run:

```text
ssh pi@apollo-pi.local
```

Accept the connection prompt and enter the Pi password you chose in Imager. Nothing appears while you type the password; that is normal.

## 3. Install Apollo

On [Apollo Downloads](https://www.repeaterbook.com/apollo/downloads/), the Raspberry Pi installer is **Bootstrap R5**. Copy this whole block into your connected Pi terminal to download, verify and run it:

```bash
base=https://github.com/gdowkpc/apollo-public-release/releases/download
curl --fail --location --proto '=https' --tlsv1.2 \
  "$base/pi-bootstrap-v1.0.0-beta1-r5/apollo-pi-bootstrap-beta1-r5.sh" \
  --output apollo.sh &&
printf '%s  %s\n' \
  6d0f474d1c570fe7a52113ad1431aac56b5e0ee1de53cb5d67bd573848c97503 \
  apollo.sh | sha256sum --check --strict &&
sudo bash ./apollo.sh
```

Enter your **Pi password** if asked. Wait for the installer to finish and show the instructions for opening Apollo.

## 4. Open Apollo

Open a **second terminal on your computer**. Copy and run the SSH command printed by the installer. It looks like this, with your Pi's hostname in place of `PRINTED-HOSTNAME`:

```text
ssh -N -T -L 17882:127.0.0.1:17882 pi@PRINTED-HOSTNAME.local
```

Enter your Pi password and leave that terminal open. It may appear idle; it is keeping the connection open.

On the same computer, open [Apollo](http://127.0.0.1:17882/) in your browser. If using a browser directly on the Pi, open that address without the SSH command.

## 5. Connect and start receiving

1. **Connect to RepeaterBook:** enter your RepeaterBook username and password, then select **Sign in and connect this node**.
2. **Receiver Location:** place the map marker at the receiver's location and select **Confirm Location**. If you use **Use My Location**, check that it points to the Pi, not your computer.
3. **SDR Scan Plan:** choose the bands or frequency ranges to scan and review the gain and reference settings.
4. Save the plan and select **Start Receiver**. Apollo opens **Dashboard/Live**.

Enter your RepeaterBook password only in Apollo's sign-in screen. Apollo stores the device connection securely; you do not need to copy any credentials.

[Release details and checksums](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-bootstrap-v1.0.0-beta1-r5)
