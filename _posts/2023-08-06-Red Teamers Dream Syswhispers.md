---
title: 'Red Teamers Dream Syswhispers'
date: 2023-08-06
permalink: /posts/2023/08/Red-Teamers-Dream-Syswhispers/
tags:
  - syscalls
  - windows 
  - x86/x64
  - security
---

<h1>What are syscalls and what is syswhyspers</h1>
Syscalls are the userlands communication to the kernel to perform a specific task, it's a request from userland to the kernel api to perform the given action. 
In Windows syscalls use the native library (features stored inside ntdll.dll) to send a specific request code to the kernel, dependant on the action to perform. 
The issue with syscalls (not just limited to the windows os) is that they change between versions and updates, this makes them unreliable and a pain to use if you want scalability,
which most programs (especially malware) do.
<h2>What is syswhispers</h2>
<p>Syswhyspers2 aims to streamline this process via making the required syscall codes for different os versions available automatically, whereas syswhyspers og did not.
Even better it utilises something they've called as random syscall jumps, which essentially bypasses hooks placed via AV / EDRs to grab the syscall stub before they are hooked.
Usually, this can be achieved by loading a fresh copy of ntdll.dll from disk. This whole process can be ignoed if using hardcoded syscall values, but this defeats the point of using syswhyspers 
denying yourself the scalability of your malware, it will be limited to the versions specified.</p>


<p>I've already described syscalls in another repository [link](https://github.com/Clydeston/windows-syscalls, "here"), but I had some issues with thread creation (probably the incorrect syscall number although I checked multiple times),
however this issues was solved when using syswhyspers2, creating a thread with zero crashes</p>
