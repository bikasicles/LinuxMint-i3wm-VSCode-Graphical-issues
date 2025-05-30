# [i3wm] Graphical Issues: Giant Grey Bars — VSCode (Obsidian)

## Problem Overview

These issues can occur in:
- [i3]
- [cinnamon]
- [both]

### Steps to Reproduce

1. Restart
2. Login
3. Open VSCode  
   - [i3]: via Rofi  
   - [cinnamon]: via 'start' menu or terminal
4. Once VSCode opens, the graphical issues start.

### Observed Issues

I was successfully using VSCode one night. The next morning, VSCode had the following problems:
- No buttons or tabs working (e.g., opening/closing files, settings, etc.)
- Constant blinking (blank window → full display)
- Resizing the window: display would not shrink with the window
- [i3] Entering floating mode: resets the display to the correct state only to immediately return to a broken state

---

Without investigation, I reinstalled VSCode, updated/upgraded, and rebooted.  
Issues persisted. Decided I'd fix it later.

Continued using the laptop regularly (not using VSCode).  
Found that Obsidian was having very similar issues to VSCode.  
Assumed the issues persisted within i3 and desktop applications.

Tested both VSCode and Obsidian in Cinnamon — issues persisted.

Switching back to i3, I assumed it might be GPU drivers or compositor (compton) issues.  
After significant Googling, I came across this post:  
https://www.reddit.com/r/i3wm/comments/uns7de/graphics_glitches_in_i3/  
Followed the solution in the comments by the OP.

**Result:**  
- Fixed Obsidian.
- VSCode still has major issues:
  - Giant grey bars flickering horizontally
  - Text vanishes based on mouse movement
  - Occasionally, color of text flickers

Now focused more on drivers; turned to reading bug forums for my version of Mesa.  
This is the closest bug report I could find for my issue:  
https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1806232

After hours of searching, I've met my match.

---

## Environment

<details>
<summary><code>inxi -Fxmprz</code> result (click to expand)</summary>
   
```
System:
  Kernel: 6.8.0-60-generic arch: x86_64 bits: 64 compiler: gcc v: 13.3.0
  Desktop: i3 v: 4.23 Distro: Linux Mint 22.1 Xia base: Ubuntu 24.04 noble
Machine:
  Type: Laptop System: Dell product: XPS 9315 v: N/A
    serial: <superuser required>
  Mobo: Dell model: 0GNN3X v: A03 serial: <superuser required> UEFI: Dell
    v: 1.28.0 date: 03/11/2025
Battery:
  ID-1: BAT0 charge: 13.4 Wh (35.3%) condition: 38.0/50.2 Wh (75.6%)
    volts: 11.1 min: 11.6 model: BYD DELL G9FHC38 status: discharging
Memory:
  System RAM: total: 16 GiB available: 15.25 GiB used: 2.6 GiB (17.1%)
  Message: For most reliable report, use superuser + dmidecode.
  Array-1: capacity: 16 GiB slots: 8 modules: 8 EC: None
    max-module-size: 2 GiB note: est.
  Device-1: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s
    actual: 5200 MT/s
  Device-2: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s
    actual: 5200 MT/s
  Device-3: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s
    actual: 5200 MT/s
  Device-4: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s
    actual: 5200 MT/s
  Device-5: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s
    actual: 5200 MT/s
  Device-6: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s
    actual: 5200 MT/s
  Device-7: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s
    actual: 5200 MT/s
  Device-8: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s
    actual: 5200 MT/s
CPU:
  Info: 10-core (2-mt/8-st) model: 12th Gen Intel Core i7-1250U bits: 64
    type: MST AMCP arch: Alder Lake rev: 4 cache: L1: 928 KiB L2: 6.5 MiB
    L3: 12 MiB
  Speed (MHz): avg: 1202 high: 3292 min/max: 400/4700:3500 cores: 1: 400
    2: 400 3: 2688 4: 400 5: 2004 6: 400 7: 400 8: 3292 9: 400 10: 400 11: 3244
    12: 400 bogomips: 45158
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-UP4 GT2 [Iris Xe Graphics] vendor: Dell
    driver: i915 v: kernel arch: Gen-12.2 bus-ID: 0000:00:02.0
  Display: x11 server: X.Org v: 21.1.11 with: Xwayland v: 23.2.6 driver: X:
    loaded: intel unloaded: modesetting dri: iris gpu: i915
    resolution: 1920x1200~60Hz
  API: EGL v: 1.5 drivers: iris,swrast platforms:
    active: gbm,x11,surfaceless,device inactive: wayland
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: intel mesa
    v: 24.2.8-1ubuntu1~24.04.1 glx-v: 1.4 direct-render: yes renderer: Mesa
    Intel Graphics (ADL GT2)
Audio:
  Device-1: Intel Alder Lake Imaging Signal Processor vendor: Dell
    driver: intel-ipu6 bus-ID: 0000:00:05.0
  Device-2: Intel Alder Lake Smart Sound Audio vendor: Dell
    driver: sof-audio-pci-intel-tgl bus-ID: 0000:00:1f.3
  API: ALSA v: k6.8.0-60-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active
Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 0000:00:14.3
  IF: wlp0s20f3 state: up mac: <filter>
Bluetooth:
  Device-1: Intel AX211 Bluetooth driver: btusb v: 0.8 type: USB
    bus-ID: 3-10:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 5.3
    lmp-v: 12
RAID:
  Hardware-1: Intel Volume Management Device NVMe RAID Controller driver: vmd
    v: 0.6 bus-ID: 0000:00:0e.0
Drives:
  Local Storage: total: 476.94 GiB used: 143.63 GiB (30.1%)
  ID-1: /dev/nvme0n1 vendor: Phison model: ESE2A044-512 NVMe 512GB
    size: 476.94 GiB temp: 25.9 C
Partition:
  ID-1: / size: 467.89 GiB used: 143.58 GiB (30.7%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 45.8 MiB (9.0%) fs: vfat
    dev: /dev/nvme0n1p1
  ID-3: /home/user size: 467.89 GiB used: 143.58 GiB (30.7%) fs: ecryptfs
    source: ERR-102
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 48.0 C mobo: 26.0 C sodimm: SODIMM C
  Fan Speeds (rpm): cpu: 0
Repos:
  Packages: 2350
  No active apt repos in: /etc/apt/sources.list
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list
    1: deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list
    1: deb https://mirrors.xmission.com/linuxmint xia main upstream import backport
    2: deb http://mirrors.xmission.com/ubuntu noble main restricted universe multiverse
    3: deb http://mirrors.xmission.com/ubuntu noble-updates main restricted universe multiverse
    4: deb http://mirrors.xmission.com/ubuntu noble-backports main restricted universe multiverse
    5: deb http://security.ubuntu.com/ubuntu/ noble-security main restricted universe multiverse
  Active apt repos in: /etc/apt/sources.list.d/spotify.list
    1: deb https://repository.spotify.com stable non-free
  Active apt repos in: /etc/apt/sources.list.d/vscode.list
    1: deb [arch=amd64,arm64,armhf] https://packages.microsoft.com/repos/code stable main
  Active apt repos in: /etc/apt/sources.list.d/protonvpn-stable.sources
    1: deb https://repo.protonvpn.com/debian stable main
Info:
  Processes: 377 Uptime: 1h 26m Init: systemd target: graphical (5)
  Compilers: gcc: 13.3.0 Shell: Bash v: 5.2.21 inxi: 3.3.34
...
```
</details>

---

## Screenshots

![Graphical Issue Example](Screenshots/graphical%20issue%201.png)
![Graphical Issue Example](Screenshots/graphical%20issue%202.png)

---

## Expectation

Looking for help resolving the graphical issues for VSCode and future applications.

> **Note:**  
> - This is my first help post — if I am missing anything please let me know!  
> - I am still new to Linux and i3wm; please be kind.
