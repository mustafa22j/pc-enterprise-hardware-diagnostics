# BIOS / POST Troubleshooting Workflow

## Purpose
A repeatable workflow for diagnosing systems that fail to boot reliably (no display, no POST, boot loops, incorrect boot device, unstable startup).

## Tools Used
- BIOS/UEFI setup utility
- Hardware isolation testing (minimum boot configuration)
- Memory reseat / single-stick testing
- Storage detection (SATA/NVMe presence)
- Visual inspection (cables, seating, damage)
- Basic indicators (fans, LEDs, beep codes where applicable)

## Common Symptoms Observed
- Powers on but no display / no POST
- Repeated reboot cycle (boot loop)
- “No boot device” / incorrect boot order
- Random freezes during boot
- Incorrect time/date (possible CMOS battery issue)

## Diagnostic Workflow

### 1) Confirm power and basic signs of life
- Verify power cable and PSU switch (desktop)
- Confirm fans spin and motherboard LEDs are active
- Reseat power connectors:
  - 24-pin ATX
  - 8-pin CPU EPS
  - GPU power (if present)

### 2) Reduce to minimum boot configuration
Boot with only:
- CPU + cooler
- 1 RAM stick
- Boot drive (or no drive if testing POST only)
- Integrated graphics (remove discrete GPU if possible)

This helps isolate failures caused by peripherals or expansion cards.

### 3) Memory isolation
- Reseat RAM
- Test **one stick at a time** in the recommended slot
- Swap slots if needed
- If POST succeeds with one stick but not another, suspect a bad module or slot

### 4) Storage detection and boot chain
- Confirm the drive appears in BIOS/UEFI
- Validate boot mode:
  - UEFI vs Legacy/CSM
- Confirm correct boot order / boot entry
- If drive is not detected:
  - reseat SATA/NVMe
  - try different SATA port / cable
  - verify power to the drive

### 5) BIOS settings sanity check
- Load BIOS defaults (“Optimized Defaults”)
- Confirm:
  - Date/time
  - Boot order
  - SATA mode (AHCI/RAID) matches OS installation expectation

### 6) CMOS reset if configuration is suspected
- Clear CMOS using motherboard jumper (desktop) or BIOS reset method
- If time/date resets repeatedly after shutdown, consider CMOS battery replacement

## Fix / Resolution Patterns
- Incorrect boot order → corrected boot entry
- Loose RAM / power connectors → reseated
- Misconfigured UEFI/Legacy settings → aligned with OS boot mode
- Storage not detected → cable/port reseat or replacement
- Persistent no-POST after isolation → suspected board/CPU/PSU issue based on elimination

## Verification
- Stable POST and entry into BIOS
- Correct boot device consistently selected
- Successful OS boot multiple times (cold boot + restart)
- BIOS settings persist after shutdown

## Notes (Portfolio Value)
This workflow demonstrates structured troubleshooting:
symptom → isolate → test → adjust → verify, using minimum-configuration testing to identify root cause efficiently.
