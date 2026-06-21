## Astrea Hub: A 4-port USB hub shaped like Reinhard's sword from Rezero

## What it is
A bus-powered 4-port USB 2.0 hub on a custom PCB, built around the SL2.1S
hub controller. A single USB-C upstream port connects to your computer and
fans out to four downstream ports: 2× USB-C, 1× USB-A, and 1× Micro-B. The
entire board is cut in the silhouette of the Dragon Sword Reid — the sword
wielded by Reinhard van Astrea in Re:Zero — so the thing sitting on your desk
reads as a sword first and a circuit board second.

It's a fixed-function hardware design: there's no microcontroller and no
firmware anywhere in the project. The SL2.1S handles all of the USB hub logic
internally, which means the board simply works the instant it's plugged in —
nothing to flash, nothing to configure.

What makes it unique: The sword-shaped outline that drew creative elements from
Rezero and the addition of a Micro B port

## What it does / how to use it
- Plug the **upstream USB-C** port into your computer.
- Plug up to **four devices** into the downstream ports (2× USB-C, 1× USB-A,
  1× Micro-B).
- That's the whole setup — **no drivers, no power adapter, no software.** It's
  bus-powered, running entirely off the power from your computer's USB port.
- It's a **USB 2.0** hub, so all four ports share up to 480 Mbps of bandwidth
  and the host port's available current. That makes it perfect for low-power
  peripherals — keyboards, mice, flash drives, game controllers — but it's
  not intended for fast-charging phones or running powered external drives.
- The Micro-B port is a plain downstream data port: its ID pin is left
  unconnected, so it is not an OTG port.

## How it works (the design)
The heart of the board is the **SL2.1S**, a dedicated USB 2.0 hub controller.
It takes the single high-speed data connection coming in from the upstream
USB-C port and splits it into four independent downstream channels, managing
device enumeration and traffic on its own. Because it has a **built-in
oscillator**, the design needs no external crystal — one fewer part to place
and route.

USB-C orientation/role is set with **CC resistors**:
- The **upstream USB-C** port uses **5.1 kΩ pull-downs** on its CC pins, so
  your computer correctly sees the hub as a device.
- The **downstream USB-C** ports use **56 kΩ pull-ups** on their CC pins, so
  they advertise themselves as standard host ports to whatever you connect.

## Specifications
- **Type:** Bus-powered USB 2.0 hub
- **Upstream:** 1× USB-C (to host)
- **Downstream:** 2× USB-C, 1× USB-A, 1× Micro-B
- **Controller:** SL2.1S (internal oscillator, no crystal required)
- **Speed:** USB 2.0, up to 480 Mbps shared across all ports
- **Power:** Bus-powered from the host port; no external supply
- **Board:** Custom sword-shaped PCB, [layers], [dimensions]
- **Firmware:** None — fixed-function hardware

## What's in this repo
- **`pcb/`** — EasyEDA Pro source files and `gerbers.zip` for fabrication
- **`cad/`** — STEP file of the enclosure plus a link to the Onshape design
- **`bom/`** — Bill of Materials in CSV, with part links and a total cost
- **`images/`** — assembled render, PCB top and bottom, and the schematic
- **`zine/`** — the one-page Fallout zine

## Building one yourself
1. Send the gerbers in `pcb/` to a fab house (this was designed for JLCPCB).
   You can either order bare boards and hand-solder, or have them assembled.
2. Source the parts listed in the BOM (designed around LCSC / JLCPCB parts).
3. Reflow or hand-solder the SL2.1S, the connectors, the resistors, and the
   decoupling capacitors. 
4. If using the enclosure: print the case from the CAD files and attach the
   board with screws.
5. Plug the upstream port into a computer and you're done.

## Why I made it
I kept running out of USB ports,
I wanted my first real PCB to be something I'd actually use every day, and I
wanted the challenge of designing a board that wasn't just a rectangle. I used
it to learn the full EasyEDA → JLCPCB pipeline from schematic to fabrication.]
