# RE: [i3wm] Graphical Issues: Giant Grey Bars - VSCode (Obsidian)

Thank you so much for the reply! I appologize for the delayed response.
I removed the file I created and updated the kernel. continued receiving the same issues as seen here:
[quote]

- No buttons or tabs working (e.g., opening/closing files, settings, etc.)
- Constant blinking (blank window → full display)
- Resizing the window: display would not shrink with the window
- [i3] Entering floating mode: resets the display to the correct state only to immediately return to a broken state

[quote]

after hours of more searching (checking dates and versions) I found the intel drivers that were installed and removed them. This fixed my issues.

my current inxi -Fxmprz result
System:
  Kernel: 6.11.0-26-generic arch: x86_64 bits: 64 compiler: gcc v: 13.3.0
  Console: pty pts/1 Distro: Linux Mint 22.1 Xia base: Ubuntu 24.04 noble
Machine:
  Type: Laptop System: Dell product: XPS 9315 v: N/A serial: <superuser required>
  Mobo: Dell model: 0GNN3X v: A03 serial: <superuser required> UEFI: Dell v: 1.28.0
    date: 03/11/2025
Battery:
  ID-1: BAT0 charge: 36.1 Wh (100.0%) condition: 36.1/50.2 Wh (71.8%) volts: 12.5 min: 11.6
    model: BYD DELL G9FHC38 status: full
Memory:
  System RAM: total: 16 GiB available: 15.25 GiB used: 2.31 GiB (15.1%)
  Message: For most reliable report, use superuser + dmidecode.
  Array-1: capacity: 16 GiB slots: 8 modules: 8 EC: None max-module-size: 2 GiB note: est.
  Device-1: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s actual: 5200 MT/s
  Device-2: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s actual: 5200 MT/s
  Device-3: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s actual: 5200 MT/s
  Device-4: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s actual: 5200 MT/s
  Device-5: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s actual: 5200 MT/s
  Device-6: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s actual: 5200 MT/s
  Device-7: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s actual: 5200 MT/s
  Device-8: Motherboard type: LPDDR5 size: 2 GiB speed: spec: 6400 MT/s actual: 5200 MT/s
CPU:
  Info: 10-core (2-mt/8-st) model: 12th Gen Intel Core i7-1250U bits: 64 type: MST AMCP
    arch: Alder Lake rev: 4 cache: L1: 928 KiB L2: 6.5 MiB L3: 12 MiB
  Speed (MHz): avg: 400 min/max: 400/4700:3500 cores: 1: 400 2: 400 3: 400 4: 400 5: 400 6: 400
    7: 400 8: 400 9: 400 10: 400 11: 400 12: 400 bogomips: 45158
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-UP4 GT2 [Iris Xe Graphics] vendor: Dell driver: i915 v: kernel
    arch: Xe bus-ID: 0000:00:02.0
  Display: server: X.org v: 1.21.1.11 with: Xwayland v: 23.2.6 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 tty: 155x40 resolution: 1920x1200
  API: EGL v: 1.5 drivers: iris,swrast platforms: active: gbm,surfaceless,device
    inactive: wayland,x11
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: mesa v: 24.2.8-1ubuntu1~24.04.1
    note: console (EGL sourced) renderer: Mesa Intel Graphics (ADL GT2), llvmpipe (LLVM 19.1.1 256
    bits)
  Info: Tools: api: eglinfo,glxinfo x11: xdriinfo, xdpyinfo, xprop, xrandr
Audio:
  Device-1: Intel Alder Lake Imaging Signal Processor vendor: Dell driver: intel-ipu6
    bus-ID: 0000:00:05.0
  Device-2: Intel Alder Lake Smart Sound Audio vendor: Dell driver: sof-audio-pci-intel-tgl
    bus-ID: 0000:00:1f.3
  API: ALSA v: k6.11.0-26-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active
Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi v: kernel bus-ID: 0000:00:14.3
  IF: wlp0s20f3 state: up mac: <filter>
Bluetooth:
  Device-1: Intel AX211 Bluetooth driver: btusb v: 0.8 type: USB bus-ID: 3-10:5
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 5.3 lmp-v: 12
RAID:
  Hardware-1: Intel Volume Management Device NVMe RAID Controller driver: vmd v: 0.6
    bus-ID: 0000:00:0e.0
Drives:
  Local Storage: total: 476.94 GiB used: 151.12 GiB (31.7%)
  ID-1: /dev/nvme0n1 vendor: Phison model: ESE2A044-512 NVMe 512GB size: 476.94 GiB temp: 28.9 C
Partition:
  ID-1: / size: 467.89 GiB used: 151.08 GiB (32.3%) fs: ext4 dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 45.8 MiB (9.0%) fs: vfat dev: /dev/nvme0n1p1
  ID-3: /home/usr size: 467.89 GiB used: 151.08 GiB (32.3%) fs: ecryptfs source: ERR-102
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 25.0 C mobo: 29.0 C sodimm: 37.0 C
  Fan Speeds (rpm): cpu: 1476
Repos:
  Packages: 2406
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
  Processes: 333 Uptime: 2m Init: systemd target: graphical (5)
  Compilers: gcc: 13.3.0 Shell: Bash v: 5.2.21 inxi: 3.3.38

