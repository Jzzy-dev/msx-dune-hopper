# msx-dune-hopper
A race against time and obstables, on the road and...

<img width="960" height="720" alt="image" src="https://github.com/user-attachments/assets/bd501b1b-2cef-4d73-8797-cdbe12f8e61f" />

by Jzzy & Claude - 2026
File: DuneHopper.rom  (128KB ASCII16 megaROM, needs MSX2 with 128KB VRAM)
Running it
openMSX : openmsx -machine <any MSX2> -cart DuneHopper.rom -romtype ASCII16 WebMSX / blueMSX / flash carts: select mapper "ASCII16" if not auto-detected. Works with the free C-BIOS as well as real MSX2 BIOS.
Controls
Cursor keys or joystick (port 1) : steer SPACE / UP / fire button          : accelerate DOWN                              : brake
Rules
Race against the clock. Each checkpoint gate adds 20 seconds.
Logs on the track are ramps: hit them to jump (+100) and fly over rocks.
Rocks, trees, signs and gate posts make you crash (lost time).
Collect stars (+500). Leftover time at the finish is paid out x100.
Three courses: MEADOW, DESERT, TUNDRA (they loop, score keeps counting).
Going off the dirt track slows you down.
Every now and then something falls out of the sky: UFO, rocket, meteorite, jumbo jet, dragon, satellite, flying e-car, giant phone, retro computer or a grand piano. Watch its shadow, steer around it (+300) - or jump it. Things fall more often on later courses.
Building from source
python3 gen.py            (generates graphics, tables and tracks into build/) sjasmplus main.asm        (writes build/dunehop.rom)
Tech notes
Screen 5, double-buffered pages 0/1. Road rows are pre-rendered in VRAM page 2 and only the edges that move are re-copied with VDP commands; page 3 holds a clean background used to erase objects. Road stripes scroll via palette rotation at 60/50 Hz. Scaled roadside objects are LMMM blits from a pre-scaled sheet; the buggy is 8 hardware sprites (mode 2) plus a jump shadow. The horizon band scrolls sideways through curves (parallax). Falling objects are streamed from ROM into a VRAM slot just before they appear. All graphics, tracks, font and code are original.
