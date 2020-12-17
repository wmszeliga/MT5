# Running MT5 on a Modern Computer

## History

[MT5](http://web.pdx.edu/%7Emccaf/MT5_970516.zip) is the last in a generation of teleseismic body-wave inversion programs written by Rob McCaffery, Geoffrey Abers, and Peter Zwick. Written in QuickBasic at a time when memory limitations were still a concern, MT5 provides a surprisingly nice and intuitive interface for iteratively solving for the best-fitting double couple focal mechanism or moment tensor from a set of teleseismic body-wave data. Other utilities included in the original software package provide the capability to digitize historical paper recordings and to view and create PostScript plots of your data. The continuing utility of this program can be seen by it's numerous apperances in the reference sections of many current journal articles.
Preparing Your Data

Since MT5 was written at a time before the SAC data format was pervasive, the first step in preparing your data for MT5 typically includes converting from SAC to a format understood by MT5. The perl script SACtoDSN.pl will convert a list of SAC files to a single DSN file capable of being read by the MT5 program mt5inv. The script SACtoDSN.pl requires a number of ancillary perl modules that are available here.
Running MT5

Since MT5 is released as compiled binaries for MS-DOS, one either needs a copy of MS-DOS and an old PC, or an MS-DOS emulator. Fortunately, since many classic computer games were written for the MS-DOS environment, there exists an underground culture devoted to developing and maintaining open-source MS-DOS emulators. One such emulator, [DosBox](https://www.dosbox.com/), is available, pre-compiled, for multiple architectures. Once you have downloaded and installed DosBox, you need to complete a few steps in order to get MT5 up and running.

### Create a directory for MT5.

My typical layout is to create a directory named dos and in this directory, create a subdirectory named mt5. Place all of the MT5 files in the mt5 subdirectory.

### Start DosBox

This is platform specific, so consult the DosBox documentation for your architecture.

### Mount your dos directory

If your DOS directory were located in the directory /home/user/dos, then you would type the following in DosBox

`mount c /home/user/dos`

Then typing

`c:`

would put you in the /user/home/dos directory. Once on the virtual "C" drive in DosBox, you can then type

`cd mt5`

to enter the MT5 directory.

Once you have your seismic data in DSN format and you've successfully started DosBox, you need to preview your data and convert it into the INV format expected by MT5. The program for this is called MT5INT and is part of the MT5 distribution. Consult the [MT5 manual])(http://web.pdx.edu/%7Emccaf/MT5_Manual.zip) for information on using the program MT5INT.

Once you have converted your DSN file to an INV file, you can run MT5 and begin inverting.

## Tips

Memory constraints at the time MT5 was written limit the total number of seismic traces that can be inverted to 50. If your INV file contains more than 50 traces, only the first 50 will be read.
Although undocumented, it appears that the number of P wave phases allowed in one file is 37. If your input data file includes more than 37 P wave phases, MT5 will silently lock-up. Unfortunately, the only recourse is to close DosBox, thus losing any unsaved parameters in MT5.
To overcome some of the memory constraints, MT5 does quite a bit of writting to disk. As such, make sure you're laptop is plugged in, since DosBox burns quite a few CPU cycles doing these disk read/write operations.

## Future

Although development on MT5 stopped in the 1990's, the value of this software is without question. Rumours indicate that a Linux version has been developed, but debugging the code has taken quite a bit of time. For the truely adventurous, a new, free, QuickBasic compiler is available (QB64) for Linux. It should be possible, in theory to re-compile the original QuickBasic source code and possibly remove some of the old limitations. If this sounds like a project you would like to tackle, contact Rob McCaffery.

## Files

Files available in this repository required to prepare your data for MT5 include:

* SACtoDSN.pl
* TauP
* Seed::Response
* Seismogram
