## Astrea Hub: A 4-port USB hub shaped like Reinhard's sword from Rezero

## What it is
A bus-powered 4-port USB 2.0 hub on a custom PCB, built around the SL2.1S
hub controller. A single USB-C upstream port connects to your computer and
fans out to four downstream ports: 2× USB-C, 1× USB-A, and 1× Micro-B. The
entire board is cut in the silhouette of the Dragon Sword Reid, the sword
wielded by Reinhard van Astrea in ReZero so the thing sitting on your desk
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
- It's a **USB 2.0** hub, so all four ports share up to 480 Mbps of bandwidth
  and the host port's available current. 
- The Micro-B port is a plain downstream data port: its ID pin is left
  unconnected, so it is not an OTG port.

## How it works (the design)
The heart of the board is the **SL2.1S**, a dedicated USB 2.0 hub controller.
It takes the single high-speed data connection coming in from the upstream
USB-C port and splits it into four independent downstream channels, managing
device enumeration and traffic on its own. Because it has a **built-in
oscillator**, the design needs no external crystal which is one fewer part to place
and route.

## Specifications
- **Type:** Bus-powered USB 2.0 hub
- **Upstream:** 1× USB-C (to host)
- **Downstream:** 2× USB-C, 1× USB-A, 1× Micro-B
- **Controller:** SL2.1S (internal oscillator, no additional clock required)
- **Speed:** USB 2.0, up to 480 Mbps shared across all ports (must be tested upon build)
- **Power:** Bus-powered from the host port; no external supply needed
- **Board:** Reinhard-inspired sword-shaped PCB

## Assembly
1. Download CAD files from onshape and the gerber zip.
   - View the onshape link to the project here: https://cad.onshape.com/documents/7c607c3ebfcfa0479c0bf52b/w/723ed4fde2646e4e640c2162/e/bc4f0acb96e833c6c127c953?renderMode=0&uiState=6a3731a90b13741097a9af9d
2. Purchase the parts from the BOM or select alternatives. (Screws must be exact identicals in dimensions)
3. Order the PCB from JLCPCB (or your prefferred vendor) using the gerber file attached
4. Print the case enclosure that houses the PCB and components
5. Attach, assemble, and solder the parts to the PCB as it looks according to the Onshape CAD
6. Insert heat inserts into their respective mounting holes, place PCB, then screw in the screws
7. Repeat step 6 for the case
Build Finished, sweeet


## Why I made it
I kept running out of USB ports,
I wanted my first real PCB to be something I'd actually use every day, and I
wanted the challenge of designing a board that wasn't just a rectangle.

<img width="1545" height="1999" alt="AstreaHub" src="https://github.com/user-attachments/assets/c24e96c5-19bf-4e04-82fe-4ff2324dedcc" />
<img width="2160" height="518" alt="Top PCB 3D View" src="https://github.com/user-attachments/assets/e3b158be-0fab-4bdd-ab22-5dcea93875a2" />
<img width="1187" height="627" alt="image" src="https://github.com/user-attachments/assets/f608fb9c-2477-435f-8b56-9ce629248620" />


