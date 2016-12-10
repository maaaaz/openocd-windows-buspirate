openocd-windows-buspirate
==========================

Description
-----------
The great `opencd` tool compiled for Windows with **Bus Pirate support**, coming in 2 versions:

* A. The latest `0.10.0` version from the **Gerrit repository**, without SWD transport support
```
> openocd.bat -f interface/buspirate.cfg
Open On-Chip Debugger 0.10.0-dev-00463-g0c2de8b-dirty (2016-12-10-14:57)
Licensed under GNU GPL v2
For bug reports, read
        http://openocd.org/doc/doxygen/bugs.html
Warn : Adapter driver 'buspirate' did not declare which transports it allows; assuming legacy JTAG-only
Info : only one transport option; autoselect 'jtag'
srst_only separate srst_gates_jtag srst_open_drain connect_deassert_srst
Error: You need to specify the serial port!
```

* B. The `0.9.0` with the not-yet-merged [patch](http://openocd.zylin.com/#/c/2444/) providing **SWD transport support**
```
> openocd.bat -f interface/buspirate.cfg -c "transport select swd"
Open On-Chip Debugger 0.9.0 (2016-12-10-16:58)
Licensed under GNU GPL v2
For bug reports, read
        http://openocd.org/doc/doxygen/bugs.html
srst_only separate srst_gates_jtag srst_open_drain connect_deassert_srst
Info : Buspirate SWD mode enabled
swd
Error: You need to specify the serial port!
```


Usage
-----
1. Download the desired archive, with or without SWD support
2. Extract it and run `bin\openocd.bat` (fixing the `scripts` folder path)
3. Profit


Tutorial
--------
In case you want to compile your own version (on Windows/Cygwin or Linux), here is a tutorial to do so:  
1. **Clone**:  
  * A. The Gerrit repository if you want an up-to-date version and no SWD support:  
  `git clone http://openocd.zylin.com/openocd`  
  * B. The Debian repository in the `0.9.0-1` version if you want SWD support:  
  `git clone git://anonscm.debian.org/crosstoolchain/openocd.git && cd openocd/ && git checkout debian/0.9.0-1`  
  
2. Install the **following packages**:  
    `build-essential automake autoconf autogen pkg-config libtool texinfo libusb-dev`  
  
3. **Configure**:  
    * A. Like that for the Gerrit repository  
    `./bootstrap && ./configure --enable-buspirate --enable-maintainer-mode`  
    * B. Like that for the Debian repository  
    `autoreconf --force --install && ./configure --enable-buspirate --enable-maintainer-mode`  
  
4. **Make and install**:  
    `make && make install`  
    
    
Copyright and license
---------------------
* Do not use it for illegal purposes
* I don't own anything on the openocd brand nor am I affiliated with the project
* If you don't trust this compilation: 
  1. Just don't download it.
  2. Compile it yourself with the above tutorial

  
References and cool previous research
-------------------------------------
* http://www.drkns.net/ruxcon-badge-2015-programming/
* https://cybermashup.com/2014/05/01/jtag-debugging-made-easy-with-bus-pirate-and-openocd/
* http://bgamari.github.io/posts/2012-03-28-jtag-over-buspirate.html