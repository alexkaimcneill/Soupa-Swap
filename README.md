# Soupa-Swap
A custom-built retro gaming machine.

## What is this?

This project is a fully custom gaming console, It uses a Raspberry Pi 3B+, a 7" IPS touch display, keyboard, Li-ion batteries, and a modular frame system to create a compact but capable retro gaming device.


## What makes this project unique

Some notable features include:

### Bluetooth and wired functionality
This allows for enjoyment no matter where its taken and all thats required is a keyboard or wireless controller

5-Minute Modular Frame
- Entire shell swaps in under 5 minutes using only a Phillips screwdriver
- Color-matched bezels, backs, and shoulder buttons
- Inspired by CMF Phone 2 Pro's customizable back panel design
- Print your own color variants and mix-and-match at will

Custom Launcher UI
- Switch-like UI built with Pygame (Python)
- Smooth horizontal scrolling tile grid with game icons
- Live reload without rebooting (press F5)

Large Battery Life
- 4 × 3.7V 5000mAh cells (20Ah total) for 6–8 hours of gameplay
- Hot-swap battery bays (no tools needed)
- Intelligent power management with BMS protection
- Charging time: ~4 hours on a 5V/2A charger

---
Parts

**Form Factor:**
- ~215 mm × 111 mm × 21 mm
- ~450–500 g with batteries and controllers

**Display:**
- 7" IPS LCD, 1024×600 resolution
- Capacitive touch support
- Outdoor viewable brightness

**Compute:**
- Raspberry Pi 3B+ (4× ARM Cortex-A53 @ 1.4 GHz, 1 GB RAM)
- 32–128 GB microSD card (64+ GB recommended)

**Power:**
- 4 × 3.7V 5000mAh Li-ion cells (20Ah total)
- 5V buck converter regulated supply
- 6–8 hour battery life (mixed retro gaming)


**Connectivity:**
- Wi-Fi b/g/n (onboard RPi)
- Bluetooth 4.1 LE (controllers + optional external devices)
- 3.5 mm aux jack for headphones
- USB for charging and development

---

## How to Use It

Plug in or connect a keyboard/controller and enjoy


### Software & Launcher

The **SwitchPi Launcher** is a fullscreen Pygame application that boots on startup:

```bash
python3 launcher.py
```

**Adding Games:**

Create a folder in `games/` with a `game.json` file:

```json
{
  "title": "Pokemon Fire Red",
  "command": "mgba /home/pi/roms/firered.gba",
  "icon": "icon.png"
}
```

Supported emulators:
- **NES/SNES:** Nestopia, Snes9x
- **Game Boy / Color:** mgba, Gambatte
- **Genesis:** Genesis Plus GX
- **Arcade:** MAME, FinalBurn
- **N64:** Mupen64Plus (light games only)
- **PlayStation 1:** Mednafen
- **Multi-system:** RetroArch

The launcher auto-detects new games on boot or after pressing F5.

### Controller Usage


**Navigation:**
- D-pad or Left Analog: scroll left/right through games
- A button: select and launch a game
- B button: back / menu
- Pair secondary controllers via Bluetooth for multiplayer (if supported by emulator)


---

## Why We Made It

We made this project because we wanted to build a gaming handheld that was:

**More modular than commercial options:**
We were inspired by framework laptops, we wanted a console that could do something similar


Lack of good modern hardware to play retro games so we built our own



How to make


First, obtain the materials


**Cost-effective:**
Commercial gaming handhelds cost $400–600. Our BOM is ~$150–220 because we're willing to do the assembly work ourselves and use open-source software.

---

## Tech Stack

### Hardware
- **Compute:** Raspberry Pi 3B+
- **Display:** 7" IPS LCD, 1024×600, capacitive touch
- **Power:** 4 × 3.7V 5000mAh Li-ion cells, BMS, 5V buck converter, audio amp
- **Controllers:** Dual wireless Bluetooth controllers with analog sticks and buttons
- **Frame:** Aluminum + PETG composite, modular design
- **I/O:** USB hub, 3.5 mm audio jack, Micro USB charging

### Software
- **OS:** Raspberry Pi OS Lite (Bookworm, headless)
- **Launcher:** Custom Pygame application (Python 3.11+)
- **Emulators:** RetroArch, mgba, Nestopia, Snes9x, etc. (drop-in via game.json)
- **Wireless:** bluez (Bluetooth stack for RPi)
- **CAD:** Onshape, FreeCAD, CadQuery

---

## Bill of Materials

| Component | Qty | Cost (USD) | Notes |
|-----------|-----|-----------|-------|
| Raspberry Pi 3B+ | 1 | $60 | Used acceptable |
| 7" IPS LCD 1024×600 | 1 | $25 | Huaqiangbei market common |
| 3.7V 5000mAh Li-ion cells | 4 | $18 | 18650 or similar format |
| BMS + charger board | 1 | $1 | Generic module |

Dupont wires 
| Cables, connectors, fasteners | — | $0 | Owned|
| **Total** | — | **~$150–220** | DIY assembly |

---

## Build Instructions

### 1. Prepare the Display and Battery Packs

**Display:**
- Verify the 7" LCD boots and responds to touch
- Test with RPi before integration
- Plan cable routing to the RPi's micro USB ports

**Battery Packs:**
- Install 4 × 3.7V cells into plastic holders
- Wire in parallel using the BMS module
- Verify voltage output: 3.6–4.2V on a single pack, ~3.7V nominal
- Test the charger circuit before integrating

**Controllers:**
- Charge both wireless controllers fully before pairing
- Verify Bluetooth connectivity with the RPi
- Test button input and analog stick responsiveness

### 2. Assemble the PETG Chassis

**3D Print the following parts:**
- Base frame (lower half)
- Top bezel with screen opening
- Side bezels (left and right)
- Shoulder button holders
- D-pad housing
- Back panel (removable for customization)
- Controller mounting brackets

**Print settings:**
- 0.2 mm layer height
- 20% infill (gyroid or honeycomb)
- No supports for most parts
- Print time: 20–30 hours total

**Assembly:**
- Snap all frame pieces together (no glue needed if tolerances are tight)
- Insert shoulder buttons and D-pad into slots
- Verify the touch screen bezel opening aligns
- Leave the back panel loose until the electronics are installed

### 3. Integrate the Electronics

**Mount the Raspberry Pi:**
- Use M2.5 standoffs to secure the RPi to a mounting plate
- Position it near the battery bays for short power cables
- Leave USB/Micro USB ports accessible

**Connect the display:**
- Plug the display's power cable into RPi USB
- Wire the display's touch interface to the RPi's I2C pins (if separate from USB)
- Route the display FPC cable carefully to avoid pinching

**Wire the power distribution:**
- 4 × Li-ion cells → BMS module
- BMS output → 5V buck converter
- Buck converter → RPi Micro USB (or GPIO 5V + GND)
- Buck converter → Display power rail
- Buck converter → Audio amplifier

**Audio system:**
- Connect audio amplifier to RPi's 3.5 mm jack (or GPIO PWM)
- Mount small speaker inside the bottom enclosure
- Route audio cables away from power lines

**Pair the wireless controllers:**
```bash
# SSH into the RPi
ssh pi@raspberrypi.local

# Launch Bluetooth pairing
bluetoothctl
> scan on
> pair [MAC_ADDRESS]
> trust [MAC_ADDRESS]
> connect [MAC_ADDRESS]
```

### 4. Battery Integration

**Install battery bays:**
- Slot the 4 × 3.7V cell groups into the designated battery compartments
- Wire all 4 in parallel to the BMS
- Verify voltage output: ~3.7V nominal

**Test under load:**
- Boot the RPi and display
- Monitor battery voltage while running a game
- Expect ~0.5A idle draw, ~1.5A during gameplay

### 5. Mount Controllers and Fit the Frame

**Attach controller brackets:**
- Snap the magnetic mounting brackets onto each side bezel
- Attach the wireless controllers to the brackets
- Verify the controllers don't interfere with gameplay

**Close the housing:**
- Snap all frame pieces into their final positions
- Align the back panel with the main chassis
- Screw down the 4 frame attachment points using a Phillips screwdriver (no power tools needed)
- Verify the display is flush and touch points align

**Test the modular swap:**
- Remove the 4 screws
- Slide off the frame panel
- Verify the internal components remain in place
- Slide on a different color variant
- Re-screw and verify alignment

### 6. Software Setup

**Flash the SD card:**
```bash
# On a Linux/Mac computer
sudo dd if=raspios-lite-arm64.img of=/dev/sdX bs=4M
# X = your SD card (e.g., sdc, sdd)
```

**Boot and configure:**
```bash
# SSH into the RPi (default user: pi, password: raspberry)
ssh pi@raspberrypi.local

# Update and install dependencies
sudo apt update && sudo apt upgrade -y
sudo apt install -y python3-pip git bluetooth bluez

# Install launcher dependencies
pip install pygame

# Clone the launcher repository
git clone https://github.com/yourusername/switchpi.git
cd switchpi
```

**Add your games:**
```bash
mkdir -p games/my_first_game
cat > games/my_first_game/game.json << EOF
{
  "title": "My Game",
  "command": "mgba /path/to/rom.gba",
  "icon": "icon.png"
}
EOF
```

**Boot the launcher:**
```bash
python3 launcher.py
```

For automatic startup on boot, create a systemd service:
```bash
sudo cp launcher.service /etc/systemd/system/
sudo systemctl enable launcher.service
sudo systemctl start launcher.service
```

---


---
Credits


*Soupa-Swap: The handheld console you built yourself.*
