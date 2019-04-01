# Alien Object

### [~$ cd ..](../)

To solve this challenge we were given the following image file :

![cosmos](assets/cosmos.jpg)

We used `exiftool` to find all the image attributes, which gave us the following output :

```
~$ exiftool cosmos.jpg

ExifTool Version Number         : 11.30
File Name                       : cosmos.jpg
Directory                       : .
File Size                       : 8.5 MB
File Modification Date/Time     : 2019:03:15 14:40:52+01:00
File Access Date/Time           : 2019:03:15 14:48:06+01:00
File Inode Change Date/Time     : 2019:03:15 14:45:17+01:00
File Permissions                : rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
DCT Encode Version              : 100
APP14 Flags 0                   : (none)
APP14 Flags 1                   : (none)
Color Transform                 : YCbCr
Exif Byte Order                 : Big-endian (Motorola, MM)
Compression                     : LZW
Photometric Interpretation      : RGB
Camera Model Name               : UEsDBBQAAAAIALiOMk4NBnn9agAAAGgAAAABAAAAZnPPz09R8MpPUlSIzC9VSMsvzUtRKMlIVUjLSUxXVPBILUpVyCxRyCy24uXi5XIODqoO8TBWdvQxNA6t80/yMvYP0Q03CY4vLk1Odi22SAvNMYyMTzPIK3XRNczTDTFJ1XM2KPb1D1asBQBQSwECHwAUAAAACAC4jjJODQZ5/WoAAABoAAAAAQAkAAAAAAAAACAAAAAAAAAAZgoAIAAAAAAAAQAYAG4+r2JOr9QBHHgxf02v1AEceDF/Ta/UAVBLBQYAAAAAAQABAFMAAACJAAAAAAA=
...
```

So we noticed that the `Camera Model Name` was very base64-like. So we tried to decode it using :

```bash
echo "UEsDBBQAAAAIALiOMk4NBnn9agAAAGgAAAABAAAAZnPPz09R8MpPUlSIzC9VSMsvzUtRKMlIVUjLSUxXVPBILUpVyCxRyCy24uXi5XIODqoO8TBWdvQxNA6t80/yMvYP0Q03CY4vLk1Odi22SAvNMYyMTzPIK3XRNczTDTFJ1XM2KPb1D1asBQBQSwECHwAUAAAACAC4jjJODQZ5/WoAAABoAAAAAQAkAAAAAAAAACAAAAAAAAAAZgoAIAAAAAAAAQAYAG4+r2JOr9QBHHgxf02v1AEceDF/Ta/UAVBLBQYAAAAAAQABAFMAAACJAAAAAAA=" | base64 -d > out
```

To know what kind of file we found we did :

```
~$ file out
out: Zip archive data, at least v2.0 to extract
```

This was very promising, we then used `unzip`.

```
unzip out
Archive:  out
  inflating: f
```

Then a simple `cat`.

```
cat f
Good Job! You found the flag! Here it is:

CSR{TH3#AL13U~ObJ3OT-W4S_succEs8fUl1Y_f0nuD-1n-T4e.C0sMOS!}
```

DONE.
