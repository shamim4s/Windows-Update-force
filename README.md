# Windows-Update-force

#To manually force Windows Update from the command line, you can use PowerShell with administrative privileges. Here are a few methods:

You're running into an execution policy restriction, which is blocking PowerShell from loading the PSWindowsUpdate module. This is a common security feature in Windows.

Here's how to fix it step-by-step:
✅ Step 1: Temporarily Allow Script Execution
Run this in PowerShell as Administrator:

powershell
```
Set-ExecutionPolicy RemoteSigned -Scope Process
```
This allows signed scripts to run only in this PowerShell session (it won't change your system's global settings).

✅ Step 2: Import the Module Again
Now try:

```
Import-Module PSWindowsUpdate
```
You should no longer get the security error.

✅ Step 3: Run the Update Command
Then run:

```
Get-WindowsUpdate -AcceptAll -Install -AutoReboot
```
Or:
```
Install-WindowsUpdate -AcceptAll -AutoReboot
```
Optional: If You Still Have Issues
You can also bypass execution policy just for the command, like this:

```
powershell -ExecutionPolicy Bypass -Command "Import-Module PSWindowsUpdate; Get-WindowsUpdate -AcceptAll -Install -AutoReboot"
```
Let me know if you'd like to wrap all this into a script or a .ps1 file you can run easily next time.


# Final all command 

```
Set-ExecutionPolicy RemoteSigned -Scope Process

Import-Module PSWindowsUpdate

Get-WindowsUpdate -AcceptAll -Install -AutoReboot
```
Optional: If You Still Have Issues
You can also bypass execution policy just for the command, like this:

```
powershell -ExecutionPolicy Bypass -Command "Import-Module PSWindowsUpdate; Get-WindowsUpdate -AcceptAll -Install -AutoReboot"
```
