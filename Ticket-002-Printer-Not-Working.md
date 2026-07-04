# Ticket #002 - Network Printer Not Printing

## User
Sarah (Human Resources)

## Category
Printer Support

## Environment
- Operating System: Windows 11
- Device Type: Desktop
- Network: Corporate Wi-Fi
- Printer Type: Network Printer
- Affected Users: Single user

## Priority
Medium

## Status
Resolved

---

## Issue

User reports that documents are stuck in the print queue and are not printing.

Other employees are able to print successfully to the same network printer.

---

## Initial Assessment

- Issue isolated to one workstation
- Printer is powered on and reachable on the network
- No paper jams or hardware errors reported
- Other users can print without issue
- Suspected local Print Spooler or driver issue

---

## Troubleshooting Steps

### 1. Verified Printer Status

- Checked Printers & Scanners in Windows Settings
- Confirmed printer was listed and installed correctly
- Status showed "Ready"

**Result:**
- Printer was reachable and online

---

### 2. Restarted Print Spooler Service

- Opened services.msc
- Located Print Spooler service
- Restarted service

**Result:**
- Print queue temporarily resumed but jobs remained stuck

---

### 3. Cleared Print Queue

- Stopped Print Spooler service
- Navigated to:
  C:\Windows\System32\spool\PRINTERS
- Deleted all stuck print jobs
- Restarted Print Spooler service

**Result:**
- Print queue successfully cleared

---

### 4. Reinstalled Printer

- Removed printer from Settings → Printers & Scanners
- Re-added network printer
- Windows automatically installed correct driver

**Result:**
- Printer reconnected successfully

---

### 5. Test Print

- Printed Windows Test Page

**Result:**
- Test page printed successfully
- User confirmed Word and PDF printing working

---

## Resolution

- Restarted Print Spooler service
- Cleared corrupted print queue
- Removed and reinstalled printer
- Verified functionality with test print

---

## Outcome

- Printing restored for user
- No further issues reported
- System operating normally

---

## Root Cause

A corrupted print job in the local Print Spooler caused the print queue to become stuck, preventing new print jobs from being processed.

---

## Notes / Lessons Learned

- Print issues affecting only one user typically indicate a local issue (driver/spooler)
- Restarting Print Spooler is a key first step in troubleshooting print problems
- Clearing the spool folder resolves stuck print jobs
- Reinstalling the printer can resolve driver-related corruption
- Always confirm scope before escalating (single user vs multiple users)

---

## Commands / Tools Used

- services.msc
- Settings → Printers & Scanners
- File Explorer (spool folder path)
- Windows Test Page
* File Explorer
