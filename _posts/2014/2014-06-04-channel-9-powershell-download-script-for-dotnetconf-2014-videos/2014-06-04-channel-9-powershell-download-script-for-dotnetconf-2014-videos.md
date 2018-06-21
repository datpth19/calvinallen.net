---
title: "Channel 9 PowerShell Download Script for dotNetConf 2014 Videos"
tags: [channel9,dotnetconf,powershell]
redirect_from:
  - /archive/2014/06/04/channel-9-powershell-download-script-for-dotnetconf-2014-videos
---

Based on my previous script of a nearly identical title, this script will snag the 2014 dotNetConf videos (high quality MP4s) from Channel 9.

Change the `$baseLocation` to a folder of your choosing, and let it go.

```powershell
$baseLocation = "V:\Coding\Channel 9\dotNetConf 2014\"

$rssFeed = New-Object -TypeName XML
$rss = (New-Object System.Net.WebClient).DownloadString("http://s.ch9.ms/Events/dotnetConf/2014/RSS/mp4high")

$rssFeed.LoadXml($rss)

$itemCount = $rssFeed.rss.channel.item.Count

for($i = 0; $i -lt $itemCount; $i++) {
     $fileCount = $i + 1
     Write-Progress -Activity "Downloading Recordings..." -Status "Processing file $fileCount of $itemCount" -PercentComplete (($i/$itemCount)*100)

     $item = $rssFeed.rss.channel.item[$i]

     $fileExtension = $item.enclosure.url.Substring($item.enclosure.url.lastIndexOf('.'), $item.enclosure.url.length - $item.enclosure.url.lastIndexOf('.'))

     $cleanFileName = [RegEx]::Replace($item.title, "[{0}]" -f ([RegEx]::Escape([String][System.IO.Path]::GetInvalidFileNameChars())), '') 

     $downloadTo = $baseLocation+$cleanFileName+$fileExtension

     If(!(Test-Path $downloadTo)) {
          (New-Object System.Net.WebClient).DownloadFile($item.enclosure.url, $downloadTo)
     }
}
```