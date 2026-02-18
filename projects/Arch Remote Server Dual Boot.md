Yes — what you want is actually a **really good architecture** and totally doable.  
You’re basically describing:

- 🎮 Windows = gaming OS on NVMe  
- 🐧 Arch (Omarchy/Hyprland) = dev OS on second drive  
- 🌐 Linux box = always reachable from laptop like a server  

The only real question is **whether you want Arch running at the same time as Windows**, or you’re okay with rebooting.

Because those are **two very different setups**.

---

# 🧠 Option A — Dual boot (simplest, most common)

### How it works
- Windows lives on NVMe
- Arch lives on 200 GB drive
- You pick OS at boot
- Only one runs at a time

### Pros
✔ simple  
✔ zero performance loss  
✔ perfect for gaming  
✔ safest install  
✔ what 90% of Linux users do  

### Cons
❌ Linux box isn’t reachable when booted into Windows  
❌ can’t run both simultaneously  

This is the normal approach.

---

# 🧠 Option B — Always-on Arch “server mode” (what you hinted at)

To do this, you need one of these:

---

## 🟢 Option B1 — Run Arch as a VM inside Windows

### Setup
- Keep Windows as main OS
- Install Arch in a VM using:
  - entity["software","VMware Workstation Player","virtualization software"]  
  - entity["software","VirtualBox","virtualization software"]  
  - or Windows Hyper-V  

Then:
- Start VM on boot
- SSH into it from laptop anytime
- Use it as your Linux dev box

### Pros
✔ both run simultaneously  
✔ laptop can connect anytime  
✔ no rebooting  
✔ safe  
✔ great for dev/server use  

### Cons
❌ Hyprland inside VM is janky  
❌ GPU passthrough is complex  
❌ not ideal if you want the fancy desktop  

👉 This is best if Linux is mainly terminal/dev/server.

---

## 🟢 Option B2 — Arch as main OS, Windows in VM (NOT good for you)

This is what Linux-first users do.

But:
❌ gaming performance tanks  
❌ GPU passthrough is complicated  
❌ not worth it for your goals  

Skip this.

---

## 🟢 Option B3 — Real Arch install + leave it running

This is what you *actually want*, but it requires hardware support.

You’d need:

- Desktop stays powered on
- Boot into Arch normally
- SSH/stream into it remotely
- Reboot into Windows only when gaming

### Pros
✔ full native Arch performance  
✔ real Hyprland  
✔ best dev experience  
✔ easiest remote access  

### Cons
❌ requires reboot to game  
❌ Arch isn’t reachable while in Windows  

This is the **practical power-user setup**.

---

# 🧠 Option C — Dual boot + network dev workflow (my recommendation)

This is the sweet spot.

### Install:
- Windows on NVMe
- Arch on 200 GB drive

### When away from desktop:
Leave desktop booted into Arch

From laptop:
- SSH for coding
- Sunshine for GUI
- Git sync projects

### When home and want to game:
Reboot → Windows → game normally

This gives you:

✔ server-like dev box  
✔ full gaming performance  
✔ simple install  
✔ no virtualization headaches  
✔ future-proof setup  

This is honestly the **cleanest long-term workflow**.

---

# 🧠 How “server-like” you can make it

On Arch you can:

- enable SSH at boot
- auto-start Hyprland
- auto-start Sunshine
- mount your dev folders
- run Docker services
- host Git repos
- run web servers
- access from anywhere via Tailscale

It basically becomes your personal cloud machine.

---

# 🧠 What I’d do in your shoes

Given:
- you’re a dev student
- you want reliability
- you game on Windows
- you like Hyprland

I’d do:

### ✔ Dual boot
### ✔ Arch auto-starts SSH + Sunshine
### ✔ Leave desktop on when away
### ✔ Remote into it from laptop

That’s a legit professional workflow.

---

If you want, next I can give you:

**1️⃣ Safe step-by-step plan to install Arch on that 200 GB drive without breaking Windows**  
**2️⃣ How to make Arch boot straight into Hyprland + SSH + Sunshine automatically**  
**3️⃣ How to make it reachable from outside your home using entity["software","Tailscale","vpn software"]**

Which one do you want first?