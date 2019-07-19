---
title: "Creating a Self-Signed Wildcard Certificate for Local Development"
tags: [powershell,iis]
description: "If you're developing on Windows and using IIS, and need to create a self-signed, wildcard, TLS/SSL certificate - this post will show you how with some easy to use PowerShell"
---

<TYPE YO POST HERE, AND DON'T FORGET THE COVER IMAGE!>

```powershell
New-SelfSignedCertificate 
	-Subject *.localhost.com 
	-DnsName *.localhost.com 
	-CertStoreLocation Cert:\LocalMachine\My 
	-NotAfter (Get-Date).AddYears(10) 
	-FriendlyName "Localhost Wildcard"
```

Then, take the cert and move it to Trusted Root in certmgr.msc