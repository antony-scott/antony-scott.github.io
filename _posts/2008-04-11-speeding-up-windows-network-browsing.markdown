---
layout:     post
title:      Speeding up Windows network browsing
date:       2008-04-11
categories: Windows,Networking
---
I have always used the `\\MACHINENAME` way of traversing my local network. Slowness is just something I assumed came as part of the deal with windows networking, until I did a quick google and found out that windows will look for any shared printers and scheduled tasks. Personally, I don't want this as I have a networked printer with a built-in server, and I use remote desktop to manage any scheduled tasks. So, I've now turned those options off and my network browsing is instantaneous!

I cannot remember where I found the registry way of doing it, but you basically you need to delete a couple of entries here

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\RemoteComputer\NameSpace`

There are two entries

| Key | Use |
|--|--|
| `{2227A280-3AEA-1069-A2DE-08002B30309D}` | Look for printers |
| `{D6277990-4C6A-11CF-8D87-00AA0060F5BF}` | Look for scheduled tasks |

I have removed both, but it\'s up to you to decide which you need, if any.
