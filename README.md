## Tango server for automatic Rigaku Crysalis .par file correction (ts-crysalispar)
Are you working with Rigaku's Crysalis at the synchrotron facility? 
Probably you are aware of the problem of the instrumental files which contain the full geometry of the instrument.

This Tango Server watches for changes in the file system uaing the predefined properties:

    CalibFilePattern	"enst"
    WatchPath	["/gpfs/current", "/gpfs/commissioning"]

If the a .par file appears starting with __enst__, it is considered to be an instrumental calibration file, and its information is extracted.

For each of the new .par files which carry no calibration file information, the files are adjusted to latest saved calibration is injected.
Since there are not so many .par files in an experiment, I use lock file creation as a mechanism to prevent accidental .par file overwriting. 

## Installation
I provide the .xmi (XML) file for POGO of Tango Controls and the source code.

It depends on the following python modules:

    pip install pytango watchdog

 