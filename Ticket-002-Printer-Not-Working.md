# Ticket #002 - Printer not working 

## Category 
Printer Support

## Environment 
Windows 11, Network printer, Single user affected

## User
Sara (Human Resources)

###### Priority: Medium

## Status 
Resolved

## Issue
User reports documents remain stuck in the print queue. Other employees are able to print to the same printer without issue.

---

## Initial Assessment
- Confirmed issue is isolated to one workstation
- Printer is powered on
- No paper jams or hardware errors observed
- Other users can successfully print
- Suspected printer configuration issue

---

## Troubleshooting Steps

### 1. Verified printer status 
Opened: 

Settings > Bluetooth & devices > Printers and scanners

Observed:
- Printer listed correctly
- Printer status displayed offline 

**Conclusion:** Issue appears to be local workstation

---

### 2. Restarted Printer Spooler Service 
Opened: 
services.msc

Located: 
Print spooler

##### Actions performed:
Stopped service
Started service

##### Result: Printer came online but print jobs still stuck.

---

### 3. Cleared print queue
Stopped print spooler service

Navigated to C:\Windows\System32\spool\PRINTERS

Deleted all pending print jobs

Restarted Print spool service

##### Result: Queue successfully cleared

---

### 4. Removed and reinstalled printer
Opened:
Settings > Bluetooth & devices > Printers & scanners

Removed affected printer
Selected:
Add printer
- Windows rediscoverd the printer and installed it successfully

### 5.
Printed a windows test page.

**Result:**
Test page printed successfully 
User successsfully printed a word document

**Resolution:** 
Restarted printer spool service
Cleared corrupted print queue
Removed and reinstalled network printer
Verified successful test print

---

## Outcome
Printer functioning normally
User able to print documents
No additional issues reported

---

## Root Cause
A corrupted print job caused the Print Spooler to get stuck, preventing jobs from being processed.

---

## Notes / Lessons Learned
Always verify whether the issue affects one or multiple users
Restarting the print spooler is one of the first troubleshooting steps for print related issues 
Clearing the print queue resolves many spooler related problems
If issues persist after clearing the queue, removing and reinstalling the printer can resolve corrupter printer configurations
Testing with a windows test page confirms both printer communication and driver functionality

## Commands / Tools Used

* services.msc
* Print Management
* Settings → Printers & Scanners
* Windows Print Spooler
* Windows Test Page
* File Explorer
