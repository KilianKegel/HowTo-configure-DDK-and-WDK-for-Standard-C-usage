# HowTo-configure-DDK-and-WDK-for-Standard-C-usage

HowTo make free of charge Microsoft command line build environments usable for ANSI-C-Programming

* ALL STATEMENTS WITHOUT GUARANTEE
* AT YOUR OWN RISK ONLY

## WDK 7.1.0

1. get .ISO image from http://download.microsoft.com/download/4/a/2/4a25c7d5-efbe-4182-b6a9-ae6850409a78/grmwdk_en_7600_1.iso
2. install to `C:\WinDDK\7600.16385.1`

### configure for 32Bit build environment
`C:\WinDDK\7600.16385.1\LAUNCH32.BAT`
```bat
@echo off
set DDKROOTDIR=c:\winddk\7600.16385.1\
set BASEDIR=%DDKROOTDIR%
set PATH=%DDKROOTDIR%bin\x86\x86;%PATH%
set INCLUDE=%DDKROOTDIR%INC\CRT;%DDKROOTDIR%INC\API
set LIB=%DDKROOTDIR%LIB\CRT\i386;%DDKROOTDIR%LIB\WIN7\i386;
cmd /k title 32-Bit Standard C Build environment
```

### configure for 64Bit build environment
`C:\WinDDK\7600.16385.1\LAUNCH64.BAT`
```bat
@echo off
set DDKROOTDIR=c:\winddk\7600.16385.1\
set BASEDIR=%DDKROOTDIR%
set PATH=%DDKROOTDIR%\bin\x86\amd64;%PATH%
set INCLUDE=%DDKROOTDIR%\INC\CRT;%DDKROOTDIR%\INC\API
set LIB=%DDKROOTDIR%\LIB\CRT\AMD64;%DDKROOTDIR%\LIB\WIN7\AMD64;
cmd /k title 64-Bit Standard C Build environment
```


## EWDK for Windows 10, version 1703

1. get `EnterpriseWDK_rs2_release_15063_20170317-1834.zip` archive from https://go.microsoft.com/fwlink/p/?LinkID=846038
2. extract archive to `C:\EWDK1703`

### configure for 32Bit build environment
`C:\EWDK1703\launch32.bat`
```bat
@echo off
set DDKROOTDIR=C:\EWDK1703\
set VCINSTALLDIR=%DDKROOTDIR%Program Files\Microsoft Visual Studio 14.0\VC\
set VS140COMNTOOLS=%VCINSTALLDIR%\..\Common7\Tools\
set INCLUDE=%DDKROOTDIR%Program Files\Windows Kits\10\Include\10.0.15063.0\ucrt\
set INCLUDE=%INCLUDE%;%DDKROOTDIR%Program Files\Microsoft Visual Studio 14.0\VC\include\
set INCLUDE=%INCLUDE%;%DDKROOTDIR%Program Files\Windows Kits\10\Include\10.0.15063.0\um\
set INCLUDE=%INCLUDE%;%DDKROOTDIR%Program Files\Windows Kits\10\Include\10.0.15063.0\shared;
set LIB=%DDKROOTDIR%Program Files\Microsoft Visual Studio 14.0\VC\lib\;%DDKROOTDIR%Program Files\Windows Kits\10\Lib\10.0.15063.0\um\x86\;%DDKROOTDIR%Program Files\Windows Kits\10\Lib\10.0.15063.0\ucrt\x86\
call LaunchBuildEnv.cmd x86
cmd /k title 32-Bit Standard C Build environment
```

### configure for 64Bit build environment
`C:\EWDK1703\launch64.bat`
```bat
@echo off
set DDKROOTDIR=C:\EWDK1703\
set VCINSTALLDIR=%DDKROOTDIR%Program Files\Microsoft Visual Studio 14.0\VC\
set VS140COMNTOOLS=%VCINSTALLDIR%\..\Common7\Tools\
set INCLUDE=%DDKROOTDIR%Program Files\Windows Kits\10\Include\10.0.15063.0\ucrt\
set INCLUDE=%INCLUDE%;%DDKROOTDIR%Program Files\Microsoft Visual Studio 14.0\VC\include\
set INCLUDE=%INCLUDE%;%DDKROOTDIR%Program Files\Windows Kits\10\Include\10.0.15063.0\um\
set INCLUDE=%INCLUDE%;%DDKROOTDIR%Program Files\Windows Kits\10\Include\10.0.15063.0\shared;
set LIB=%DDKROOTDIR%Program Files\Microsoft Visual Studio 14.0\VC\lib\amd64\;%DDKROOTDIR%Program Files\Windows Kits\10\Lib\10.0.15063.0\um\x64\;%DDKROOTDIR%Program Files\Windows Kits\10\Lib\10.0.15063.0\ucrt\x64\
call LaunchBuildEnv.cmd amd64
cmd /k title 64-Bit Standard C Build environment
```