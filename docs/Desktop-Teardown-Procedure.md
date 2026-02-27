# Desktop Teardown & Rebuild Procedure (Service Workflow)

## Purpose
A safe, repeatable process for disassembling, servicing, and rebuilding desktop PCs while minimizing risk to components and ensuring correct reassembly.

## Safety & Preparation
- Power down and disconnect AC power
- Hold power button to discharge residual power
- Use ESD precautions (wrist strap / grounded surface)
- Prepare a clean workspace and parts tray

## Documentation Before Removal
- Photograph internal layout (cable routing, front-panel connectors)
- Label critical cables if needed:
  - front panel (PWR/RESET/HDD LED)
  - SATA data/power
  - fan headers
  - PCIe power

## Disassembly Steps (High-Level)
1. Remove side panel
2. Disconnect GPU (if present), then remove carefully
3. Remove storage devices (SATA/NVMe) as required
4. Remove RAM (store safely)
5. Disconnect and remove PSU if required
6. Remove CPU cooler (if required) and clean/reapply thermal paste on reassembly
7. Remove motherboard only if necessary (last step)

## Service / Maintenance Tasks
- Clean dust with compressed air (hold fan blades to prevent overspin)
- Inspect for:
  - damaged connectors
  - swollen capacitors
  - loose headers
  - pinched cables
- Verify standoffs match motherboard form factor
- Reseat critical components:
  - RAM
  - GPU
  - SATA/NVMe
  - power connectors

## Reassembly Checklist
- 24-pin ATX and 8-pin CPU power connected
- CPU cooler firmly mounted; fan connected to CPU_FAN header
- RAM seated fully (latches locked)
- GPU seated (if used) + PCIe power connected
- Storage connected and secured
- Case fans connected and oriented for airflow
- Front-panel connectors correctly placed

## Post-Rebuild Verification
- First boot into BIOS/UEFI:
  - confirm CPU/RAM detected
  - confirm storage detected
  - confirm correct boot order
- Boot OS successfully
- Quick functional tests:
  - USB ports
  - network link
  - disk access
  - basic stability (no unexpected shutdowns)

## Notes (Portfolio Value)
This procedure demonstrates technician-level hardware competency:
safe handling, structured disassembly/reassembly, documentation practices, and verification-driven testing.
