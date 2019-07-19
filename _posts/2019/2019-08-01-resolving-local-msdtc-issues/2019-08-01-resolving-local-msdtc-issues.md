---
title: "Resolving Local MSDTC Issues"
tags: [msdtc,cmd]
description: "If you've ever run into issues locally with MSDCTC, this post may help."
---

<TYPE YO POST HERE, AND DON'T FORGET THE COVER IMAGE!>

```batch
REG QUERY "HKLM\Software\Microsoft\MSDTC\Security" /v NetworkDtcAccess
REG QUERY "HKLM\Software\Microsoft\MSDTC\Security" /v NetworkDtcAccessTransactions
REG QUERY "HKLM\Software\Microsoft\MSDTC\Security" /v NetworkDtcAccessInbound
REG QUERY "HKLM\Software\Microsoft\MSDTC\Security" /v NetworkDtcAccessOutbound
PAUSE

REG ADD "HKLM\Software\Microsoft\MSDTC\Security" /v NetworkDtcAccess /t REG_DWORD /d 1
REG ADD "HKLM\Software\Microsoft\MSDTC\Security" /v NetworkDtcAccessTransactions /t REG_DWORD /d 1
REG ADD "HKLM\Software\Microsoft\MSDTC\Security" /v NetworkDtcAccessInbound /t REG_DWORD /d 1
REG ADD "HKLM\Software\Microsoft\MSDTC\Security" /v NetworkDtcAccessOutbound /t REG_DWORD /d 1
PAUSE

net stop MSDTC
net start MSDTC
PAUSE
```