## What you need to know to get started with ctypesgen

### Requirements

ctypesgen is available via git: https://github.com/davidjamesca/

Only 2 requirements:

  * Python, at least version 2.4
  * A C pre-compiler, if you have a C compiler installed such as GCC you already have one

#### Linux or Mac

It's easy to set up on Linux or Mac because you can use gcc.

#### Windows

Windows does not ship a compiler/pre-processor with the operating system so one needs to be installed. For example, http://www.mingw.org

Assuming mingw32 has been installed in the default location, open a command prompt and issue:

    path %SystemDrive%\MinGW\bin;%PATH%
    ctypesgen.py -a -l MYLIB - o pyMYLIB.py MYLIB.h


Where MYLIB.dll is the name of the name of the dll of interest and MYLIB.h is the main header include file.

NOTE the "-a" flag, this ensures macros etc. that are present in include files that MYLIB.h include are included in pyMYLIB.py.


Alternatively gcc does not need to be in the path:

    ctypesgen.py -a --cpp="%SystemDrive%\MinGW\bin\gcc.exe -E" -l MYLIB - o pyMYLIB.py MYLIB.h


The --cpp flag could also be used to call the Microsoft Visual Studio compiler cl.exe.

#### C Pre Processors

gnu gcc is known to work.

Microsoft Visual C++ VS .net 2003 is known to *fail*. Should be able to setup path with:

    REM VS C++ 6.0
    call "C:\Program Files\DevStudio\VC\bin\VCVARS32.BAT"

    REM VS C++ .NET 2003
    call "C:\Program Files\Microsoft Visual Studio\VC98\Bin\VCVARS32.BAT"


Then use --cpp="cl -E" or --cpp="cl -EP"

Pure Python processor would be a nice addition but at the moment there does not appear to be one, possible research items:
  * http://www.atrandomresearch.com/pyembc/
  * http://code.google.com/p/preprocess/

See [[Hacking-Tips|Hacking-Tips]] for modifying ctypesgen and testing information.