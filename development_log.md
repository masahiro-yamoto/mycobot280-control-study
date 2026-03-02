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
