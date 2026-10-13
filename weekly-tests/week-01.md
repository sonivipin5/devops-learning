# Week 1 — Plan and Assessment

**Week:** 1 of Level 1 (Foundations)
**Dates:** 2026-10-13 → 2026-10-19

## 1. Main objective

Build a solid mental model of **what a computer and operating system are**, then get a
**working Linux environment** (Ubuntu via WSL) on my Windows machine, and use it
confidently for basic navigation.

## 2. Daily topics (planned — may shift by one day if a topic needs more time)

| Day | Topic |
|---|---|
| 1 | Computer fundamentals and operating systems |
| 2 | Windows vs Linux; the boot process; installing Ubuntu via WSL |
| 3 | Linux architecture, distributions, terminal and shell basics |
| 4 | Command practice: navigation, files, directories, pipes, redirection |
| 5 | Troubleshooting day: permissions, "command not found", PATH, disk/memory checks |
| 6 | Weekly practical lab: build a "system report" script that works on Linux |
| 7 | Revision + interview preparation + weekly test |

## 3. Practical work

- Day 1 lab: machine inventory on Windows
- Day 2 lab: WSL + Ubuntu install and verification
- Day 3–4 labs: Linux file system exploration
- Day 6 lab: a reusable `system-report.sh` script

## 4. Expected skills by end of week

- Explain OS, kernel, shell, process, service, VM vs container
- Open a Linux shell and move around the file system without help
- Read `ls -l`, `df -h`, `free -h`, `ps aux` output correctly
- Create, move, copy, delete, and inspect files
- Use pipes and redirection
- Explain two differences between Windows and Linux that matter in DevOps

## 5. Weekly project / lab

`system-report.sh` — a Bash script that prints OS name, kernel version, CPU count, RAM,
disk usage, logged-in users, and top 5 processes by memory, with headers and error
handling. Idempotent and safe to run repeatedly.

## 6. Interview topics to revise

Operating systems · Linux architecture · shell vs kernel · process vs service ·
file system basics · Linux vs Windows differences.

## 7. Weekly assessment criteria

| Criterion | Weight | Pass bar |
|---|---|---|
| Conceptual understanding (Q&A) | 30% | Explain all core concepts in own words |
| Command fluency (practical) | 30% | Complete a file-system task unaided |
| Troubleshooting scenario | 20% | Follow a sensible diagnostic path |
| Weekly lab delivered | 20% | Script runs correctly and handles an error case |

**Pass mark:** 70% overall, with at least 60% in the practical section.
If below the pass mark, the weak topic is revised and re-tested — the roadmap does not
advance until the fundamentals are solid.

---

## Weekly Test — Week 1

_Not yet taken. To be filled in after Day 7._

| Section | Max | Score |
|---|---|---|
| Conceptual | 30 | |
| Practical commands | 30 | |
| Troubleshooting scenario | 20 | |
| Weekly lab | 20 | |
| **Total** | **100** | |
