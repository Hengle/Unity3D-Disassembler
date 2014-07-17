Unity3D-Deompiler
=================

Some classes written(pretty badly) in C# that can be used to decompile/unpack .unity3d files.

###Usage Example
```javascript
    Unpacker unpacker = new Unpacker("Direcory pointing to file");
    unpacker.Unpack();
```
=================
###Data Types

Type | Size | Range | Note |
------------ | -------------| ------------- | ------------- |
int | 4 bytes | -2147483648 to 2147483647 | Not really sure if signed or not |
string | N/A | N/A | Null terminated |

=================
###Info
This section will be giving you the info about .unity3d files header and other stuffs and thing.
>Some of the info might not be 100% true.

.unity3d files content are compressed using the [LZMA](http://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Markov_chain_algorithm) compression algorithm. You can get the latest SDK [here](http://www.7-zip.org/sdk.html).

####Compressed File Header

Here is an example of a compressed unity3d file's header. 
######HEX VIEW
```
55 6E 69 74 79 57 65 62 00 00 00 00 03 33 2E 78 2E 78 00 34 2E 32 2E 31 66 34 00 00 24 E5 0B
00 00 00 3C 00 00 00 01 00 00 00 01 00 24 E4 CF 00 73 5C A0 00 24 E5 0B 00 00 02 38 00
```

######TEXT VIEW
```
U n i t y W e b . . . . . 3 . x . x . 4 . 2 . 1 f 4 . . $ å . . . . < . . . . . . . . . $ ä 
Ï . s \ . $ å . . . . 8 .
```

The first 8 bytes, "55 6E 69 74 79 57 65 62 *00*", of the header is a string, "UnityWeb". I guess we will call it the .unity3d file signature. 

The next 4 bytes, "00 00 00 03" bytes is an int, '3'. Still  not really sure about it, maybe its the build number? But it seems to be a static value.

The next 5 bytes, "33 2E 78 2E 78 *00*", of the header is a string, "3.x.x". It is the Unity Webplayer minium requirement?

=================
###TODO List
- [ ] Clean the code.
- [ ] Add repacking function.
- [ ] Add output log file.
