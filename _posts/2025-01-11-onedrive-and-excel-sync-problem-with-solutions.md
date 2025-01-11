---
title: First blog pst into
date: 2025-01-05 12:53:05 +/-TTTT
categories: [Blog_Post]
tags: [into]     # TAG names should always be lowercase
description: Short summary of the post.
---

# Kindly please try below suggested actions:
-	Word 2016 co-authoring fails when file is stored on SharePoint 2013
-	Add the following registry key, and then restart Word:
  -	Subkey: HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\FileIO
  - Key: "EnableRealtimeChannel"=dword:00000000
-	"Upload Failed - Locked by another user"
-	Right click OneDrive icon in the taskbar, click Settings.
-	Choose the Office tab
-	Untick the option of “Use Office 2016 to sync Office files that I open”, then click OK.

1. Signout from Excel
2. Settings -> Accounts -> Access Work or School -> Select User and Disconnect -> Click Yes
3. Go to Credential Manager -> Windows Credentials -> Remove All OneDrive Credentials 
4. Go to Regedit -> Computer\HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\Internet\Server Cache

