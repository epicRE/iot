## Decoding and talking to a bluetooth LED light strip

LED lights are now available with bluetooth communications. After decoding the protocol, it is possible to talk to the device using your own bluetooth stick.

The model is : [https://play.google.com/store/apps/details?id=shy.smartled](https://play.google.com/store/apps/details?id=shy.smartled)

The following GATT characteristic UUIDs are available:

```
UUID_RW          = "0000fff3-0000-1000-8000-00805f9b34fb"
```

|method | hex (int) values| notes|
|---|---|---|
|lights on/off|  ||
| | 7E (126) ||
| | 04 (4) ||
| | 04 (4)||
| | 01 (x) |Set x to 0x01 for lights on and Set x to 0x00 for lights off |
| | 00 (0) ||
| | 01 (x) |Set x to 0x01 for lights on and Set x to 0x00 for lights off |
| | FF (-1) ||
| | 00 (0) ||
| | EF (-17) ||

|lights off |lights on|
|---|---|
|7E0404000000FF00EF| 7E0404010001FF00EF |


