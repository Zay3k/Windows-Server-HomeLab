# Ticket #001 - No Internet Connectivity

## User
Michael (Front Desk)

###### Priority: High

## Issue
User reports that the computer shows Wi-Fi connected, but no internet access. Outlook and web browsing are not working.

---

## Initial Assessment
- Confirmed issue is isolated to one device
- Other devices on same network have internet access
- Suspected DHCP or network adapter issue

---

## Troubleshooting Steps

### 1. Checked IP Configuration
Ran:

ipconfig


Observed:
- IPv4 Address: 169.254.x.x (APIPA address)
- No default gateway assigned

**Conclusion:** Device failed to obtain IP from DHCP server.

---

### 2. Restarted Network Adapter
- Disabled Wi-Fi adapter
- Waited several seconds
- Re-enabled adapter

**Result:** Issue persisted

---

### 3. Attempted IP Renewal
Ran:

ipconfig /release ipconfig /renew


**Result:**
- Unable to contact DHCP server
- No valid IP assigned

---

### 4. Checked Device Manager
- Opened Device Manager → Network Adapters
- Found Intel Wi-Fi Adapter with warning icon

**Conclusion:** Possible driver corruption or adapter malfunction

---

### 5. Updated Driver
- Attempted automatic driver update
- Windows confirmed latest driver already installed

**Result:** Issue not resolved

---

### 6. Reinstalled Network Adapter
- Uninstalled Wi-Fi adapter in Device Manager
- Selected “Remove driver software”
- Restarted system

Windows automatically reinstalled network adapter on reboot.

---

## Resolution
- Wi-Fi adapter successfully reinstalled
- Device obtained valid IP address (192.168.1.x range)
- Internet connectivity restored

---

## Outcome
- Outlook working
- Web browsing restored
- No further issues reported

---

## Root Cause
Corrupted network adapter driver / network stack failure

---

## Notes / Lessons Learned
- 169.254.x.x indicates DHCP failure (APIPA address)
- Reinstalling network adapter is an effective fix for driver-related network issues
- Device Manager is critical for hardware-level troubleshooting
