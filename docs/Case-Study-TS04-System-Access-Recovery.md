@"

\# Case Study: TS-04 – System Access Recovery



\## Overview

Resolved system lockout and multiple BIOS misconfigurations preventing login and hardware usage.



\---



\## Issues Identified

\- Unknown Windows password

\- Keyboard not functioning

\- USB ports disabled in BIOS

\- Ethernet disabled in BIOS



\---



\## Troubleshooting Steps



\### 1. Access Recovery

\- Booted into recovery mode

\- Replaced utilman.exe with cmd.exe:

ren utilman.exe utilman1.exe

ren cmd.exe utilman.exe



\### 2. Password Reset

control userpasswords2



\### 3. Restore System

\- Reverted utilman changes



\### 4. BIOS Fixes

\- Enabled USB controller

\- Enabled Ethernet adapter



\---



\## Result

\- Successfully restored system access

\- Full hardware functionality recovered



\---



\## Skills Demonstrated

\- Windows recovery environment

\- Password reset techniques

\- BIOS configuration

\- System-level troubleshooting

"@ | Set-Content "Case-Study-TS04-System-Access-Recovery.md"

