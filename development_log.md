# Development Log

## 2026-02-28

### Environment
- Mac (VSCode practice completed on 2026-02-23)
- myCobot 280 Raspberry Pi version
- GitHub repository created

### Today's Progress
- Repository initialized

### Next Step
- Install required Python libraries
- Test basic angle control

## 2026-03-02

### Environment
- myCobot 280 Raspberry Pi version  
- Linux (MATE Desktop Environment)  
- Python 3  
- pymycobot library  

### Today's Progress
- Opened MATE Terminal and verified Python installation  
- Confirmed pymycobot library installation  
- Checked available serial ports using `ls /dev/tty*`  
- Identified `/dev/ttyAMA0` as the primary UART port  
- Executed initial Python angle control script  

### Issue Encountered
The robot did not move despite:
- Successful Python script execution  
- No error messages  
- Servo motors powered ON  

### Root Cause Analysis
Observed initialization log from myBlockly:

## 2026-03-03

### Environment
- myCobot 280 Raspberry Pi version  
- Linux (MATE Desktop Environment)  
- Python 3  
- pymycobot library  

### Today's Objective
Improve code structure by introducing parameterized functions and loop-based motion control.

### Implementation

#### 1. Parameterized Motion Functions

Refactored motion control into reusable functions:

- Implemented `home(speed)`
- Implemented `pose1(speed)`

Speed is now passed as an argument instead of being hardcoded.

Example:

```python
def home(speed):
    mc.send_angles([0, 0, 0, 0, 0, 0], speed)
    time.sleep(3)

## 2026-03-03

### Environment
- myCobot 280 Raspberry Pi version  
- Linux (MATE Desktop Environment)  
- Python 3  
- pymycobot library  

---

### Today's Objective
Verify coordinate-based motion control using `send_coords()` and investigate the robot's coordinate system in order to draw shapes on a vertical surface.

---

### Implementation

#### 1. Base Coordinate Confirmation

Confirmed the Cartesian coordinates corresponding to the initial joint angles.

The following joint configuration:

```python
angles = [0, 0, 0, 0, 0, 0]
```

corresponded to the Cartesian position:

```python
coords = [45.4, -63.4, 412.3, -90.43, 0.7, -90.0]
```

This coordinate was used as the **base position for motion testing**.

---

#### 2. Coordinate Motion Verification

Tested whether the robot moves correctly when small changes are applied to the coordinate values.

Example test code:

```python
base = [45.4, -63.4, 412.3, -90.43, 0.7, -90.0]

mc.send_coords(base, 30, 1)
time.sleep(2)

test = [45.4, -53.4, 412.3, -90.43, 0.7, -90.0]  # Y +10
mc.send_coords(test, 30, 1)
```

Initial attempts suggested no motion, but further observation showed that **small coordinate changes did produce movement**.

---

#### 3. Coordinate Direction Investigation

Additional experiments were conducted by adjusting the Y coordinate.

Example values tested:

```
Y = -163
Y = -63
Y = -48
```

From these tests, it was observed that:

- Motion toward the **wall direction corresponds to the negative Y axis**.

This helped clarify the orientation of the robot's coordinate system.

---

#### 4. Attempt to Draw an L Shape

An attempt was made to draw an **L-shaped trajectory on a vertical surface**.

The idea was to:

1. Move in one direction to form the vertical segment
2. Move in another direction to form the horizontal segment

However, the trajectory did not form a proper L shape due to **insufficient calibration of the drawing base coordinate**.

---

### Result

The L-shape drawing was not successfully achieved, but the following were confirmed:

- The robot can be controlled using Cartesian coordinates with `send_coords()`.
- Small coordinate adjustments produce corresponding physical movements.
- The wall-facing direction corresponds to negative Y movement.

---

### Next Steps

- Redefine the drawing base coordinate.
- Establish a stable **drawing reference position (DRAW = BASE)**.
- Calibrate axis directions more precisely before implementing trajectory generation.
