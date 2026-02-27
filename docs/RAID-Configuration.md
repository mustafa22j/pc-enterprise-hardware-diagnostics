# RAID Configuration and Validation Notes

## Purpose
Document common RAID configurations, setup steps, and validation procedures used in hands-on PC troubleshooting labs.

## RAID Concepts (Quick Reference)
- **RAID 0 (Stripe):** Performance, no redundancy (one disk failure = data loss)
- **RAID 1 (Mirror):** Redundancy, usable capacity = 50%
- **RAID 5 (Parity):** Redundancy + capacity efficiency (requires 3+ disks)
- **RAID 10 (1+0):** Performance + redundancy (requires 4+ disks)

## Typical Lab Workflow

### 1) Pre-checks
- Confirm identical or compatible drive types/sizes
- Confirm SATA mode expectations:
  - If using firmware RAID: enable RAID mode in BIOS/UEFI
  - If using OS-level RAID: use AHCI and configure in OS

### 2) Firmware/BIOS RAID (if available)
- Enter RAID configuration utility during boot (vendor dependent)
- Create RAID volume:
  - Select RAID level
  - Select member drives
  - Set stripe size (for RAID 0/5/10)
  - Confirm volume name and capacity
- Save and reboot

### 3) OS Installation / Disk Initialization
- If installing an OS on RAID:
  - Ensure installer recognizes the RAID volume
  - Load RAID drivers if required (vendor dependent)
- If adding RAID volume as a data disk:
  - Initialize disk (GPT recommended for modern systems)
  - Create partition(s) and format (NTFS commonly used in Windows labs)

## Validation Checklist
- RAID volume is visible in:
  - BIOS/RAID utility (healthy state)
  - OS disk management (correct capacity, correct status)
- Read/write test:
  - Create a test folder and move files onto the array
- Reboot test:
  - RAID volume remains present after restart
- Drive failure simulation (if permitted in lab):
  - Confirm degraded state is reported
  - Replace / re-add disk and verify rebuild process

## Common Issues and Fixes
- **Volume missing in OS:** check BIOS mode (UEFI/Legacy), SATA mode (AHCI vs RAID), cabling, and correct controller
- **Wrong capacity shown:** RAID level math error, mixed drive sizes (array uses smallest drive size)
- **Boot failure after RAID change:** OS installed under different controller mode (AHCI↔RAID mismatch)
- **Rebuild not starting:** disk not compatible, not initialized for rebuild, or wrong slot/port

## Notes (Portfolio Value)
RAID work shows practical understanding of:
hardware storage architecture, redundancy trade-offs, BIOS/controller configuration, and verification-driven troubleshooting.
