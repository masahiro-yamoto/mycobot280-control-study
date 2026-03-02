# myCobot 280 (Raspberry Pi Version) Control Study

## Purpose

This repository documents my learning process and experimental development while controlling the myCobot 280 (Raspberry Pi version) using Python.

The primary objective of this project is to understand low-level hardware communication and establish reliable robotic arm control through direct Python-based serial communication.

---

## Hardware Configuration

- myCobot 280 (Raspberry Pi version)
- Raspberry Pi onboard control
- Python 3
- pymycobot library
- UART serial communication (/dev/ttyAMA0)
- Baud rate: 1000000

---

## Project Goals

- Establish stable UART communication
- Execute joint angle control via Python
- Understand serial communication parameters (port and baud rate)
- Build a foundation for structured motion control experiments

---

## Technical Progress

### Serial Communication Debugging

During initial testing, the robot did not respond despite successful script execution.

Investigation revealed a baud rate mismatch:

- 115200 baud → No response
- 1000000 baud → Successful communication

After correcting the baud rate to 1000000, the robot executed motion commands successfully.

This marked the first successful hardware control via direct Python-based UART communication.

---

## Working Example

```python
from pymycobot.mycobot import MyCobot
import time

mc = MyCobot("/dev/ttyAMA0", 1000000)

mc.send_angles([0, 20, 0, 0, 0, 0], 50)
time.sleep(3)
