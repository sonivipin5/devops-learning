# Lab 01 — Machine Inventory (Day 001)

**Objective:** build a one-page inventory of your own computer and be able to explain
every number in it.

**Time:** 30–45 minutes
**Risk level:** 🟢 safe — read-only commands, nothing installed, nothing configured
**Cost:** ₹0 / $0 — everything is local

---

## Requirements

- Windows 11 (works on Windows 10 too)
- Windows Terminal or the VS Code integrated terminal, set to **PowerShell**

---

## Step 1 — Create the output folder

```powershell
New-Item -ItemType Directory -Force -Path "d:\vip\Learn\DevOps\devops-learning\labs\day-001\output" | Out-Null
```

## Step 2 — Collect the raw data

```powershell
$out = "d:\vip\Learn\DevOps\devops-learning\labs\day-001\output"

Get-CimInstance Win32_OperatingSystem |
  Select-Object Caption, Version, OSArchitecture, LastBootUpTime |
  Out-File "$out\os.txt"

Get-CimInstance Win32_Processor |
  Select-Object Name, NumberOfCores, NumberOfLogicalProcessors |
  Out-File "$out\cpu.txt"

(Get-CimInstance Win32_ComputerSystem).TotalPhysicalMemory / 1GB |
  Out-File "$out\ram-gb.txt"

Get-Volume | Where-Object DriveLetter |
  Select-Object DriveLetter, FileSystemType, Size, SizeRemaining |
  Out-File "$out\disks.txt"

(Get-Process).Count |
  Out-File "$out\process-count.txt"

Get-Process | Sort-Object WS -Descending |
  Select-Object -First 5 Name, Id, WS |
  Out-File "$out\top-5-memory.txt"
```

## Step 3 — Verify the files exist

```powershell
Get-ChildItem "d:\vip\Learn\DevOps\devops-learning\labs\day-001\output"
```

You should see six files: `os.txt`, `cpu.txt`, `ram-gb.txt`, `disks.txt`,
`process-count.txt`, `top-5-memory.txt`.

## Step 4 — Write your inventory

Create `d:\vip\Learn\DevOps\devops-learning\labs\day-001\machine-inventory.md` and fill it in.
Use your **own words** in the last column. Write `DOUBT:` if you cannot explain something.

| Field | Your value | What it means (in your own words) |
|---|---|---|
| OS name and version | | |
| Architecture (32/64-bit) | | |
| Last boot time | | |
| CPU model | | |
| Physical cores | | |
| Logical processors | | |
| Total RAM (GB) | | |
| Disk C: total size | | |
| Disk C: free space | | |
| Number of running processes | | |
| Top memory process (name + PID + MB) | | |

## Step 5 — Sanity checks (answer these in the same file)

1. Is `ram-gb.txt` smaller than the "GB" printed on the machine's spec sheet? Why?
2. Are there any duplicate process names in `top-5-memory.txt`? What does that prove?
3. Is `SizeRemaining` smaller than `Size` for every disk? What would it mean if they were equal?
4. How many logical processors do you have per physical core? Is hyper-threading enabled?

---

## Expected result

- `output/` contains 6 non-empty text files
- `machine-inventory.md` is complete with no blank rows
- You can explain, without notes, what each number describes

## Troubleshooting

| Symptom | Fix |
|---|---|
| `Could not find a part of the path` | Step 1 was not run, or the folder name is misspelled |
| `Access denied` | Open Windows Terminal **as Administrator** and retry |
| Command prints nothing | Check spelling of property names; they must exist on the WMI class |
| RAM number looks enormous (e.g. `16700000000`) | You forgot `/ 1GB` |
| `Get-Volume` not recognised | Use `Get-PSDrive -PSProvider FileSystem` instead |

## Cleanup

```powershell
Remove-Item -Recurse -Force "d:\vip\Learn\DevOps\devops-learning\labs\day-001\output"
```

> Deleting output is fine — but keep `machine-inventory.md`. You will compare it against
> your future Linux machine on Day 002+.

---

## Stretch goal (optional)

Repeat the whole lab inside WSL once Ubuntu is installed (Day 002) using these Linux
equivalents, and note the differences:

```bash
cat /etc/os-release     # OS name/version
uname -m                # architecture
nproc                   # logical processors
lscpu                   # CPU details
free -h                 # RAM
df -h                   # disks
ps aux | wc -l          # process count
ps aux --sort=-%mem | head -6   # top memory processes
```
