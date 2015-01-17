# LW12 API Description

## Get Status
### Command
    EF 01 77
### Response
    [0] 66
    [1] 01
    [2] PowerOff
    [3] Mode
    [4] ModeRun
    [5] ModeSpeed
    [6] Red
    [7] Green
    [8] Blue
    [9] 01
    [10] 99
    
### Example
    echo -ne '\xEF\x01\x77' | nc -w3 -i1 192.168.178.49 5577 | hexdump -C
    00000000  66 01 23 26 21 0a 85 00  00 01 99                 |f.#A!...)..|
    
    [0] 66
    [1] 01
    [2] PowerOff 23 = 35(23) - 35 = 0(On)
    [3] Prog 26 = 38(26) - 36 = 2(Red gradual change)
    [4] ProgRun 21 = 33(21) - 32 = 1(Running)
    [5] Speed 0a = 32 - 10(0a) = 22(Speed 22)
    [6] Red f8
    [7] Green ef
    [8] Blue 29
    [9] 01
    [10] 99
 
## Power On
### Command
    CC 23 33
### Example
    echo -ne '\xCC\x23\x33' | nc -w3 192.168.178.49 5577

## Power Off
### Command
    CC 24 33
### Example
    echo -ne '\xCC\x24\x33' | nc -w3 192.168.178.49 5577

## Set RGB Color
### Command 56 [HEXRGB] AA

## Set Program
### Command
    BB [PRG] [SPEED] 44
    PRG:
        1: Seven color cross fade
        2: Red gradual change

## Program On
### Command
    CC 21 33

## Program Off
### Command
    CC 20 33  
