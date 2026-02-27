# Windows Forced Logoff / Shutdown Timer — Troubleshooting Case Study

## Symptom
After logging into Windows, a warning appears indicating an imminent sign-out/shutdown with a countdown. The system logs off automatically unless interrupted.

## Initial Hypothesis
Because the issue occurs after login (not in BIOS), the root cause is likely:
- a scheduled shutdown command,
- a startup item triggering `shutdown.exe`,
- a task in Task Scheduler,
- or a script/policy applied at logon.

## Investigation Workflow

### 1) Confirm it is not hardware
- System remains stable in BIOS/UEFI with no power loss
- No thermal or SMART alerts observed during basic checks

### 2) Abort the shutdown to buy time
Use:
- `shutdown -a`

If this stops the countdown, it confirms a shutdown/logoff command is being triggered by software.

### 3) Identify the trigger source
Check these locations in order:

#### A) Startup folders
- User Startup:
  - `%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup`
- All Users Startup:
  - `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup`

Look for:
- shortcuts calling `shutdown.exe`
- batch files or scripts
- unknown executables

#### B) Task Scheduler
- Search Task Scheduler Library for tasks running:
  - “At log on”
  - “At startup”
- Inspect “Actions” tab for:
  - `shutdown.exe /s`
  - `shutdown.exe /l`
  - `/t` timers

#### C) Registry Run Keys (startup persistence)
- `HKCU:\Software\Microsoft\Windows\CurrentVersion\Run`
- `HKLM:\Software\Microsoft\Windows\CurrentVersion\Run`

#### D) Group Policy (if domain-joined)
- Logon scripts
- Restricted policies triggering logoff

## Action Taken (Typical Fix Pattern)
- Remove the startup shortcut/script responsible for calling shutdown/logoff
- Disable or delete scheduled task if task-based
- Reboot and verify the issue no longer triggers

## Verification
- Multiple logins without countdown
- Restart and cold boot tests
- Confirm no “shutdown” actions remain in startup/task locations

## Notes (Portfolio Value)
This case demonstrates structured Windows troubleshooting:
symptom isolation, command-line mitigation, persistence hunting (Startup/Tasks/Run keys), and verification testing.
