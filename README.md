# iot
iot devices reverse engineered so you can understand them better

## Zoetouch by 1byone
Amazon link : (https://www.amazon.com/dp/B07FKCGDCH/)

**Description**: This is a bluetooth enabled home body scale with BMI and body fat analysis. The scale has four electrodes that measure impedance. This value is included in the measurment reported via the bluetooth stack. Once the scale is on it is shown on a Bluetooth scan as ```Health Scale```. I have noticed that Bluetooth remains available, only shortly, even after the display turns off. This is not always the case. 

It is possible to read and write to the device (I have not tested writing to it).

Read/Notify (UUID): 0xFFF4 

Write (UUID): 0xFFF1 

### Scale readings via Bluetooth
Struct (can be copied into 010 Editor) (11 bytes total) (ushort=2 bytes):
```c
struct zoetouch_scale {  
    byte      scale_reading_type_identifier;
    ushort    unknown;
    ushort    weight;
    ushort    unknown2;
    ushort    impedence;
    ushort    unknown3;
};
```
I have verifiied values for ```scale_reading_type_identifier``` and ```weight```. 

Example of weight extraction and calculation :

```CF0000B801000000000076```

actual_weight = weight_int * 0.01

```B801``` turns into ```440``` unsiged integer which will give us ```4.4 kg```

If I am not mistaken, it looks like the Android app uses the impedance for calculating the BMI only. Everything else is just formulas using data you input into the app (i.e., height, age etc.).

Default on state:

```CF000000000000000001CE```

