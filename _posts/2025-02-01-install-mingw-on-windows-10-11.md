---
title: Install MingW on windows 10/11
date: 2025-02-01 11:13:05 +/-TTTT
categories: ["Tech", "Solutions"]
tags: ["MingW", "GCC Compiler", "Windows 11"]     # TAG names should always be lowercase
description: How to install mingw on windows 10 and windows 11
---

1. [Download MingW](/assets/downloads/mingw.exe){:target="_blank" rel="noopener"} and install with the location:
  ```
  C:\MinGW
  ```
2. Click Start or Search on your PC: 
   ```
   About your PC
   ```
3. Go to: 
   ```
   Advanced system settings
   ```
4. On 
   ```
   Advanced Tab
   ```
   Click:
   ```
   Environmental Variables
   ```
5. On The:
  ```
  System Variables
  ```
  Double Click
  ```
  Path
  ```
6. OR
  ```
  Select Path and Click Edit
  ```
7. Clcik New and paste:
  ```
  C:\MinGW\bin
  ``` 
8. Open CMD and type:
  ```
  gcc --version
  ```
9. You will see like this:
  ```
  gcc (MinGW.org GCC-6.3.0-1) 6.3.0
Copyright (C) 2016 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```
That's all!
Enjoy!
