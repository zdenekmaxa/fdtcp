## fdtcp project, fdtcplib - Python wrapper for FDT Java.

Provides fdtd daemon, fdtcp client program. Supports third-party transfers,
authentication in the CMS (Compact Muon Solenoid) Grid environment via Grid
Map Files.

Run py.test unittests from fdtcplib directory.

Unittets depend on Python Mock, psutil and FDT Java available in
    `../fdtjava/fdt.jar` and bash wrappers (e.g. `wrapper_kill.sh`)
    
Production installation takes configuration values from `/etc/fdtcp/*`,
configuration files are installed from conf files from this directory.

