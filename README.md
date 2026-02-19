⏰ Timer-Based PC Wake-Up System
📌 Overview

A hardware-based system designed to automatically power on a desktop computer at a predefined time using a IKEA Digital Alarm clock.

This project is an accessory to my Nextcloud cloud storage server, running on an old PC, to turn it on everyday at 6 AM.

🚀 Problem Statement

I have made my own cloud storage server using nextcloud and debian 12.6. It runs on a very old (11+ years) PC which doesn't have any modern BIOS features. As it is very old office desktop and not a server, it is not meant to run 24/7 for weeks at a time. This overuse has resulted in a seized CPU fan and a lot of headache.

This project, or sub-project, is to turn the server ON everyday at 6 AM using basic components and a cheap digital alarm clock.

⚙️ System Architecture

Working Principle:
A custom script checks the CPU usage for 2 mins at 12 AM everyday. If the Avg. CPU usage for 2 mins is less than 5%, meaning no background job is being performed, the script shuts down the server.

Then, to wake the PC up, I am made a simple circuit to check when the alarm beeps and then short the PWR Pins in the motherboard for few seconds untill the PC is on. Then it turns off the alarm by giving the SET button a HIGH signal when the PC case LED turns on.

🧩 Components Used



🖼️ System Diagram



🛠️ Implementation

Configured timer module

Programmed trigger condition

Connected relay across motherboard power switch pins

Tested over multiple cycles

📊 Testing & Results

Successful activation at scheduled time

Accuracy within ±1 second

Reliable over multiple test cycles

⚠️ Limitations

Requires motherboard access

No battery backup

Single schedule support

🔮 Future Improvements

Multiple schedules

Web interface

Battery backup

WiFi-based configuration

📄 Full Documentation
Detailed documentation available in:
[Full Project Report](./Docs/Project report.odt)

👨‍💻 Author

Ayushman Sahoo
Engineering & Innovation Portfolio
