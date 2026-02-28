# ⏰ Timer-Based PC Wake-Up System

## 📌 Overview

This repository contains an accessory project that automatically powers on an old desktop computer at a fixed time using a **cheap IKEA digital alarm clock** and a few basic electronic components. The main use case is to reliably wake a Nextcloud server every morning at 6 AM so that the machine can stay powered down the rest of the time.

The target system is an over‑a‑decade‑old PC running Debian 12.6 with Nextcloud. It lacks modern BIOS scheduling features, and continuous operation had caused hardware strain (seized CPU fan, etc.). This project provides a lightweight, hardware‑centric workaround.


---
## 🚀 Problem Statement

Running the server 24/7 on an old office desktop leads to frequent hardware issues. The goal is to:

1. Shutdown the machine automatically when idle overnight,
2. Wake it up reliably at 06:00 each day using the alarm clock signal.

By doing so, the machine avoids unnecessary wear while still being available on a predictable schedule.

---
## ⚙️ System Architecture

### 🔌 Components

- IKEA digital alarm clock (used as a time trigger)
- Timer module / microcontroller (for the shutdown script)
- Relay or transistor interface to short the motherboard’s power‑switch pins
- Basic wiring and power supply for the alarm clock

*(See the project report in `Docs/Project-report.pdf` for full schematics and parts list.)*

### 🧠 Workflow

1. **Midnight Check** – a cron‑job runs at 00:00 which samples CPU usage for two minutes.
   - If average usage < 5 %, the script issues a `shutdown` command.
2. **Alarm Trigger** – when the clock alarm beeps at 06:00, a simple circuit detects the sound.
3. **Power‑on Pulse** – the circuit briefly shorts the motherboard’s PWR pins, simulating a button press.
4. **Alarm Disable** – once the PC’s power LED comes on, the circuit sends a HIGH signal to the clock’s SET line to silence it.


---
## 🛠️ Implementation Notes

- Timer module configured with the alarm clock’s output.
- Custom firmware/programming handles the logic for sensing the beep and driving the relay.
- Relay wired in parallel with the PC power switch headers on the motherboard.
- Extensive cycle testing confirmed consistent operation.

---
## 📊 Testing & Results

| Metric                     | Outcome                         |
|---------------------------|----------------------------------|
| Activation accuracy       | ±1 second around 06:00          |
| Reliability               | Successful over dozens of cycles|
| Shutdown condition        | 2‑min CPU avg < 5 %             |

The system has proved stable in real‑world use over several weeks.

---
## ⚠️ Limitations

- Requires physical access to motherboard headers.
- No battery backup; power loss means manual restart.
- Only a **single daily schedule** is supported at present.
- Resetting or reprogramming the alarm clock requires opening the case.

---
## 🔮 Future Improvements

- Support for multiple wake‑up times.
- A minimal web UI or nextcloud app for configuration.
- Add a small UPS/backup battery for the timer unit.
- Wi‑Fi connectivity for remote management.

---
## 📄 Documentation

See the full project report: [Docs/Project-report.pdf](Docs/Project-report.pdf)

---
## 👨‍💻 Author

Ayushman Sahoo – engineering & innovation enthusiast

*This project is part of my personal portfolio and demonstrates low‑cost automation using legacy hardware.*

---

*Last updated: February 2026*
