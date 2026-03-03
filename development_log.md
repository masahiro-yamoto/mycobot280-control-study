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
