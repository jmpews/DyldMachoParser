## DyldMachoParser

**Macho Parser Base on dyld.**


## How to use it ?

`DYLD_IN_PROCESS` mean runtime.

#### 0x1 Modify CMakelists.txt

```
ADD_DEFINITIONS(-DDYLD_IN_PROCESS=1)
ADD_DEFINITIONS(-DTARGET_OS_IOS=1)
```

#### 0x2 Cmake with command line

```
cmake .. -DDYLD_IN_PROCESS=1 -DTARGET_OS_IOS=1
```
