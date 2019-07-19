---
title: "Launch GitKraken Using a PowerShell Alias"
tags: [gitkraken,powershell]
description: "I usually have a powershell window open to an active projects folder, and sometimes I just want to fire off GitKraken at that same folder, from the PowerShell window."
---

<TYPE YO POST HERE, AND DON'T FORGET THE COVER IMAGE!>

```powershell
Function Launch-GitKraken {
  Start-Process -FilePath "C:\Users\$env:UserName\AppData\Local\gitkraken\update.exe" -ArgumentList "--processStart=gitkraken.exe","--process-start-args=`"-p `"$(Get-Location)`"`""
}

Set-Alias -Name "gitkraken" -Value Launch-GitKraken -Force
```