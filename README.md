# ChrondOS11 – Windows on Chromebook Hardware

The idea behind ChrondOS11 is simple:

> Make Microsoft Windows run as smoothly and reliably as possible on Chromebooks with MrChromebox firmware.

This involves two main challenges:

- **Hardware compatibility** – getting Windows to work properly with Chromebook hardware  
- **Storage reliability** – making Windows behave well on low-end eMMC storage

---

## MCFS – eMMC-Tuned Filesystem Concept

Many Chromebooks use cheap eMMC storage, and NTFS is not designed with this in mind. It can cause heavy, bursty read/write patterns that wear out eMMC quickly or lead to corruption.

To address this, ChrondOS11 explores a filesystem concept called **MCFS (MC FileSystem)**.

### What MCFS aims to be

MCFS is envisioned as an NTFS-like, eMMC-aware filesystem that:

- spreads out writes instead of hammering the same cells  
- turns short, intense I/O bursts into more even, consistent access  
- is more forgiving on low-end eMMC devices  
- reduces the risk of “self-destructing” installs after only a few boots  

Right now, MCFS is a **design and research idea**, not an implemented filesystem.

---

## Boot Concept

Windows normally only boots from NTFS.  
The long-term idea is:

- Use a small **NTFS boot partition**  
- Have the bootloader load **MCFS drivers**  
- Then mount and run Windows from an **MCFS main partition**

As of April 16, 2026, **MCFS drivers do not exist**.  
This is a future goal for contributors with filesystem and driver experience.

---

## Status

- Concept: defined at a high level  
- Filesystem: not implemented  
- Drivers: not implemented  
- Research and design: in progress  

If you’re interested in storage, filesystems, Windows internals, or Chromebook hardware, contributions and ideas are welcome.
