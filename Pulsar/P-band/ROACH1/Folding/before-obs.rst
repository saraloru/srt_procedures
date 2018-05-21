.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1

**Notes :** The following instructions are for observing at P-band (305-410 MHz) with the ROACH1 in real-time folding mode. The total observed bandwidth is 128 MHz and includes the whole P-band. 


======================
Before observing
======================

Some checks need to be performed before starting the observations.


On nuraghe-mng
------------------

  Check that :

   - all of the 31 containers are active on ACS ;
   - the active surface is green on AS ;
   - the jlog is open in order to track possible error messages ;
   - the interface of the Meteo client is open to check the wind velocity in real time (< 60 km/h).


On nuraghe-obs1
------------------


1. Check the presence of the 8 panels : 

    - operatorInput
    - AntennaBoss
    - GenericBackend
    - Mount
    - Observatory
    - Receivers
    - Scheduler
    - MinorServo

2. Upload your shedules and check them :

   *From your computer:*

    ``$ scp  [schedules] observer@nuraghe-obs1:/archive/schedules/[projectID]``

   *On nuraghe-obs1:*

    ``$ cd /archive/schedules/[projectID]``

    ``$ scheduleChecker [schedulename.scd]``


3. Log on to the LEAP cluster :

    ``$ ssh -X user@leap0``     *ask for password*


4. Launch a VNC session once logged on to leap0 :

    ``leap0: $ vncserver &``

5. Go back to nuraghe-obs1 and open the leap0 VNC session using
**VNCViewer** or **TigerVNC** and selecting **leap0:1**  *(ask for
password)*.






