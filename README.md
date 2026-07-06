# Soupa-Swap
A custom-built retro gaming handheld designed from the ground up for modularity, portability, and Hack Club style.

## What is this?

This project is a fully custom gaming console that we designed in CAD and are building ourselves for Hack Club. The handheld uses a Raspberry Pi 3B+, a 7" IPS touch display, detachable wireless controllers, Li-ion batteries, and a modular frame system to create a compact but capable retro gaming device.

What makes this project unique is that we are trying to balance:

- Retro gaming performance (NES through PlayStation 1 era)
- Iconic detachable controllers (inspired by Nintendo Switch)
- Radical customizability (swap the entire shell in under 5 minutes)
- Affordable components (built for ~$150–220 total)
- Compact form factor with 6+ hours of battery life

Instead of buying a commercial handheld, we designed this console ourselves, optimized the bill of materials to reduce costs, and made many CAD revisions to solve mechanical problems like controller pairing, frame rigidity, display integration, and thermal management.

## What makes this project unique

Some notable features include:

### Detachable Game Controls
- Dual detachable wireless controllers (similar to Nintendo Switch Joy-Cons)
- Full analog stick and button layout per controller
- Magnetic snap attachment to the side bezels
- Works independently as separate controllers or attached to the main unit
- Optional: pair external Bluetooth controllers for alternative input

### 5-Minute Modular Frame
- Entire shell swaps in under 5 minutes using only a Phillips screwdriver
- Color-matched bezels, backs, and shoulder buttons
- Inspired by CMF Phone 2 Pro's customizable back panel design
- Print your own color variants and mix-and-match at will

### Hack Club-Themed Launcher
- Switch-like UI built with Pygame (Python)
- Smooth horizontal scrolling tile grid with game icons
- Drop-in game support: add a folder with `game.json` and it appears instantly
- Live reload without rebooting (press F5)
- Full keyboard, D-pad, analog stick, and button support

### Battery-First Design
- 4 × 3.7V 5000mAh cells (20Ah total) for 6–8 hours of gameplay
- Hot-swap battery bays (no tools needed)
- Intelligent power management with BMS protection
- Charging time: ~4 hours on a 5V/2A charger

---

## Planned build volume and specifications

**Form Factor:**
- ~215 mm × 111 mm × 21 mm (handheld, similar to Steam Deck Lite)
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

**Controllers:**
- Dual wireless detachable controllers
- 2 analog axes per controller (full range)
- Magnetic snap attachment
- 12+ hour wireless range via Bluetooth

**Connectivity:**
- Wi-Fi b/g/n (onboard RPi)
- Bluetooth 4.1 LE (controllers + optional external devices)
- 3.5 mm aux jack for headphones
- USB for charging and development

---

## How to Use It

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

**Attach the controllers:**
1. Align each controller's magnetic snap connector with the side bezels
2. Snap firmly into place (they'll click when seated)
3. Both controllers are now paired and ready to use

**Navigation:**
- D-pad or Left Analog: scroll left/right through games
- A button: select and launch a game
- B button: back / menu
- Pair secondary controllers via Bluetooth for multiplayer (if supported by emulator)

**Detach the controllers:**
1. Press the release tabs on each controller
2. Slide the controller away from the bezel
3. Controllers remain paired via Bluetooth for independent use

---

## Why We Made It

We made this project because we wanted to build a gaming handheld that was:

**More modular than commercial options:**
Most gaming handhelds are sealed boxes. We wanted something where every component—frame, buttons, bezels, and controllers—could be swapped or customized in minutes.

**Capable of retro gaming:**
The RPi 3B+ is perfectly suited for NES through PlayStation 1 era games. We wanted to optimize for that sweet spot rather than try to chase modern AAA performance on underpowered hardware.

**An educational challenge:**
This project pushed us to learn:
- Mechanical design and CAD (Onshape, FreeCAD)
- 3D printing constraints and material selection
- Power management and battery sizing
- Embedded systems integration (RPi + display + touch + audio)
- Wireless controller pairing and management
- UI/UX design for a retro aesthetic with modern responsiveness

**A platform for experimentation:**
We wanted room to iterate and add features:
- Custom game metadata and achievements
- Multiple launcher themes
- Advanced emulator configurations
- Network play for multiplayer games
- Save state management

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
| Raspberry Pi 3B+ | 1 | $35–40 | Used acceptable |
| 7" IPS LCD 1024×600 | 1 | $40–60 | Huaqiangbei market common |
| Wireless controllers (pair) | 1 | $30–50 | Bluetooth capable |
| 3.7V 5000mAh Li-ion cells | 4 | $20–30 | 18650 or similar format |
| BMS + charger board | 1 | $10–15 | Generic module |
| 5V buck converter | 1 | $5–10 | Input 7–24V |
| Audio amplifier (3W) | 1 | $5–10 | Stereo capable |
| PETG filament (kg) | 0.5–1.0 | $15–25 | Multiple color variants |
| Aluminum/PETG frame parts | — | $10–20 | 3D printed + fasteners |
| USB hub (5-port, powered) | 1 | $10–15 | Cable routing |
| Cables, connectors, fasteners | — | $15–25 | M3/M5 screws, wire, etc. |
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

## Calibration and Testing

After assembly:

1. **Mechanical verification:**
   - Attach and detach the controllers 5 times
   - Verify the magnetic snap is secure
   - Ensure controllers don't rattle

2. **Display and touch:**
   - Boot the RPi
   - Tap the four corners of the touch screen
   - Verify the launcher responds

3. **Controller input:**
   - Navigate the launcher menu using the D-pad
   - Test all buttons and analog sticks
   - Launch a game and verify input works in-game

4. **Audio:**
   - Play a game with sound
   - Confirm audio comes from the built-in speaker
   - Test the 3.5 mm jack with headphones

5. **Battery life:**
   - Play a demanding game (e.g., a fast SNES title)
   - Monitor battery voltage over 1–2 hours
   - Expected runtime: 6–8 hours on full 4-pack

6. **Wireless connectivity:**
   - Detach a controller and move 10 meters away
   - Verify input still responds (Bluetooth range test)
   - Re-attach and verify pairing persists

---

## Recommended First Games

**Test with quick, lightweight games:**
- Kirby's Dream Land (Game Boy) — simple, short levels
- Super Mario Bros (NES) — iconic, low resource usage
- Sonic the Hedgehog (Genesis) — fast paced, good for battery drain test

**Mainstream favorites:**
- The Legend of Zelda: A Link to the Past (SNES)
- Final Fantasy III / VI (SNES)
- Castlevania IV (SNES)
- Street Fighter II (Arcade)
- Pac-Man (Arcade)

**PS1 titles (if your RPi can handle them):**
- Crash Bandicoot
- Spyro the Dragon
- Metal Gear Solid (may struggle; test first)

---

## Maintenance and Care

**Daily use:**
- Gently handle the wireless controllers to avoid drops
- Keep the controllers charged when not in use
- Avoid dropping the main unit (PETG is durable but not indestructible)

**Controller maintenance:**
- Clean the analog sticks with a dry cloth
- Re-pair controllers if they become unresponsive
- Charge controllers every 2–3 days for extended play sessions

**Long-term:**
- Store batteries in a cool, dry place when not in use
- Top-charge the batteries every 2–3 months to maintain health
- Keep the device away from direct sunlight to prevent warping

**Customization maintenance:**
- If you swap frame colors, check that all buttons and bezels align
- Clean the screw holes on new frame pieces before installing
- Verify the back panel isn't warped before the final screw-down

---

## Troubleshooting

**Controllers don't pair:**
- Ensure Bluetooth is enabled on the RPi: `bluetoothctl show`
- Put controllers in pairing mode (consult controller manual)
- Try forgetting and re-pairing: `bluetoothctl forget [MAC_ADDRESS]`

**Display shows nothing on boot:**
- Verify USB power is connected (measure 5V across the power rails)
- Check that the USB-to-display adapter is firmly seated
- Try booting without the display connected; if the RPi LED blinks, the compute is working

**Launcher crashes or won't start:**
- SSH in and run `python3 launcher.py` to see error messages
- Verify pygame is installed: `pip install pygame`
- Check that the games folder exists: `mkdir -p games/`

**Button input not working:**
- Test keyboard input (arrow keys) first—if those work, the launcher is running
- Verify the controller is still paired: `bluetoothctl info [MAC_ADDRESS]`
- Re-pair the controller if needed

**Battery drains very fast:**
- RPi 3B+ idles at ~0.5A; a single 5Ah pack gives ~10 hours idle
- During gameplay: expect 1–2A draw depending on emulator
- All 4 packs should give 6–8 hours of continuous play
- Wi-Fi and Bluetooth consume extra power when enabled

**Touch screen is unresponsive:**
- Ensure the display is powered (check 5V supply)
- Verify the USB touch interface is connected
- Try recalibrating if available on your display model

---

## Safety Notes

- **Controller safety:** Wireless controllers have small button components. Not suitable for young children unsupervised.
- **Battery safety:** Li-ion cells can overheat if short-circuited. Use only the provided BMS and charger.
- **Electrical:** Verify all grounding connections. Never modify the power circuitry while the device is powered.
- **Thermal:** The RPi 3B+ can get warm under heavy load. Ensure airflow around the back of the device.
- **Drop protection:** PETG is durable but not unbreakable. Avoid hard impacts on the display or corners.

---

## Community & Contribution

Have ideas for improvements? Found a bug?

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

Common contribution areas:
- **CAD improvements:** New color variants, ergonomic tweaks, printability optimizations
- **Launcher features:** Custom themes, additional game metadata, performance tuning
- **Emulator integration:** New console support, configuration guides
- **Documentation:** Build videos, troubleshooting guides, game recommendations

---

## Credits & Inspiration

**Hardware Design:**
- Nintendo Switch (detachable controllers, modular ethos)
- Steam Deck Lite (form factor, display choice)
- Lenovo Legion Go (tablet-style handheld)
- CMF Phone 2 Pro (5-minute customizable design)

**Software:**
- Hack Club (theming, community)
- RetroArch (emulation ecosystem)
- Pygame (launcher framework)
- Raspberry Pi community

**Components sourced at:**
- Huaqiangbei Electronics Market, Shenzhen
- AliExpress, Taobao

---

## License

- **Software** (launcher, scripts): MIT License
- **Hardware** (CAD, schematics): CC BY-SA 4.0 (share-alike)

Feel free to modify and remix — just credit the original design.

---

**Happy retro gaming!** 🎮

*Soupa-Swap: The handheld console you built yourself.*
