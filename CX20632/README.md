**Update: April 12, 2020**

CX20632 is supported by AppleALC (Credit to Halelluja12 & frankiezdh) since v1.4.2

Pull [#457](https://github.com/acidanthera/AppleALC/pull/457) layout-id 28

Pull [#459](https://github.com/acidanthera/AppleALC/pull/459) layout-id 23


Update: December 02, 2018

I tried to add CX20632 support to AppleALC but failed.

My HP EliteDesk 800 G3 DM is gone so I didn't have chance to do more tests.

Below are the informations you might need:

### Dump & Verbit

Verbs from Linux Codec Dump File: codec_dump.txt

Codec: Conexant CX20632   Address: 0   DevID: 351359128 (0x14f15098)
<br />
\----------------

```
   Jack   Color  Description                  Node     PinDefault   c  d  e  f   Modified Verbs
--------------------------------------------------------------------------------------------------------
Unknown Unknown  Other at Ext N/A            24 0x18   0x40f001f0   f0 01 f0 40 01871cf0 01871d00 01871ef0 01871f40
    1/8   Black  HP Out at Ext Front         25 0x19   0x02211040   40 10 21 02 01971c40 01971d10 01971e21 01971f01
    1/8   Black  Mic at Ext Front            26 0x1a   0x02a11020   20 10 a1 02 01a71c20 01a71d10 01a71ea1 01a71f01
Unknown Unknown  Other at Ext N/A            27 0x1b   0x40f001f0   f0 01 f0 40 01b71c30 01b71d00 01b71ef0 01b71f40
    1/8   Black  HP Out at Ext Front         28 0x1c   0x022110d0   d0 10 21 02 01c71cd0 01c71d10 01c71e21 01c71f01
Unknown Unknown  Other at Ext N/A            29 0x1d   0x40f001f0   f0 01 f0 40 01d71c50 01d71d00 01d71ef0 01d71f40
Unknown Unknown  Other at Ext N/A            30 0x1e   0x40f001f0   f0 01 f0 40 01e71c60 01e71d00 01e71ef0 01e71f40
 Analog Unknown  Speaker at Int Front        31 0x1f   0x92170110   10 01 17 92 01f71c10 01f71d00 01f71e17 01f71f91
Unknown Unknown  Other at Ext N/A            32 0x20   0x40f001f0   f0 01 f0 40 02071c70 02071d00 02071ef0 02071f40
Unknown Unknown  Other at Ext N/A            33 0x21   0x40f001f0   f0 01 f0 40 02171c80 02171d00 02171ef0 02171f40
Unknown Unknown  Other at Ext N/A            38 0x26   0x40f001f0   f0 01 f0 40 02671c90 02671d00 02671ef0 02671f40
--------------------------------------------------------------------------------------------------------
```

### Revise
Replace f0 01 f0 40 with f0 00 00 40 to disable unused ports
```
   Jack   Color  Description                  Node     PinDefault   c  d  e  f   Modified Verbs
--------------------------------------------------------------------------------------------------------
Unknown Unknown  Other at Ext N/A            24 0x18   0x40f001f0   f0 00 00 40 01871cf0 01871d00 01871e00 01871f40
    1/8   Black  HP Out at Ext Front         25 0x19   0x02211040   50 10 2b 02 01971c50 01971d10 01971e2b 01971f02
    1/8   Black  Mic at Ext Front            26 0x1a   0x02a11020   20 10 ab 02 01a71c20 01a71d10 01a71eab 01a71f02
Unknown Unknown  Other at Ext N/A            27 0x1b   0x40f001f0   f0 00 00 40 01b71cf0 01b71d00 01b71e00 01b71f40
    1/8   Black  HP Out at Ext Front         28 0x1c   0x022110d0   50 10 21 02 01c71c50 01c71d10 01c71e21 01c71f02
Unknown Unknown  Other at Ext N/A            29 0x1d   0x40f001f0   f0 00 00 40 01d71cf0 01d71d00 01d71e00 01d71f40
Unknown Unknown  Other at Ext N/A            30 0x1e   0x40f001f0   f0 00 00 40 01e71cf0 01e71d00 01e71e00 01e71f40
 Analog Unknown  Speaker at Int Front        31 0x1f   0x92170110   40 01 17 90 01f71c40 01f71d01 01f71e17 01f71f90
Unknown Unknown  Other at Ext N/A            32 0x20   0x40f001f0   f0 00 00 40 02071cf0 02071d00 02071e00 02071f40
Unknown Unknown  Other at Ext N/A            33 0x21   0x40f001f0   f0 00 00 40 02171cf0 02171d00 02171e00 02171f40
Unknown Unknown  Other at Ext N/A            38 0x26   0x40f001f0   f0 00 00 40 02671cf0 02671d00 02671e00 02671f40
--------------------------------------------------------------------------------------------------------
```

### PathMap
| Node | Dec | Device Name | Path |
| ---- | ---- | ---- | ---- |
| 0x19 | 25 | HP Out at Ext Front	| 25->17 |
| 0x1a | 26	| Mic at Ext Front | 20->26 |
| 0x1c | 28	| HP Out at Ext Front	| 28->23 |
| 0x1a | 31 | Speaker at Int Front | 31->16 |
