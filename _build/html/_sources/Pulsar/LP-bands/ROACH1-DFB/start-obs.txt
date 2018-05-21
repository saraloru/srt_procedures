.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  

Start the observations
======================

$ : commands to insert in a shell   
 

In the operatorInput panel
---------------------


#. Insert your project number :

    ``> project=[projectID]``


#. Initial setup :

    ``> antennaReset``

    ``> setupPLP``


#. Select the active surface shape (Parabolic for L and P-band observations) :

    ``> asSetup=P``


#. Insert the Local Oscillator value in MHz (this value may change) :

    ``> setLO=2188``


#. Choose the relevant L-band filter (linear filter for 1300-1800 MHz)

    ``> receiversMode=L3L2``


#. Set the attenuations for the 2x2 polarizations arriving at the Total Power backend (this may change depending on the settings of the new IF distributor).

    ``> setAttenuation=0,15``

    ``> setAttenuation=1,15``

    ``> setAttenuation=2,0``

    ``> setAttenuation=3,0``

#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[projectID]/[schedulename].scd,[N_n]``

If your schedule is LST-based (like for LEAP schedules), the antenna points to the relevant source as soon as you launch the schedule, even before the designated start time of observations (but you can start data acquisition with the ROACH1 at a later time). Check on the monitor each time that the antenna is pointing at and **TRACKING** the right source. 



On the LEAP cluster (using VNC):
--------------------------

Before starting data acquisition, do the following:

#. W2: initial setup in Control directory:

    ``$ ./control_init.sh`` 

#. W1: in each of the 8 tabs, launch the daemons:

    ``$ ~/roach/scripts/daemon.sh``

#. When the antenna is tracking the first source and you are ready to start data acquisition, go to W2 and type:

    ``$ ./start.csh``  Data acquisition has now started with the ROACH1. 

#. Immediately launch the control software (in W2) which obtains parameters from the antenna and automatically starts and stops observations, depending on whether the antenna is **TRACKING** or **SLEWING**:

    ``$ ./control.csh``

If necessary, this code can be interrupted (using Control-C) and re-started at any time while the antenna is tracking the same source, without any consequences. 

You should now see: **“no change. keep doing what you’re doing”** while the antenna keeps tracking the same source. If all goes well, you won’t need to do anything else with data acquisition for the remainder of the session. You should however check the control window (W2) once in a while for possible errors (e.g. antenna WARNING). 


To use the DFB in parallel with the ROACH1:
-----------------------------------

To use the DFB in parallel with the ROACH, we use "DFBController" in PASSIVE mode. DO NOT LAUNCH SEADAS, as this will interrupt the Nuraghe schedule.

In the LEAP cluster VNC, open another window and go to :

     ``~/externalClient/LeapDFBSockets/``

     and type: 

     ``$ ./simple_server``

This will allow the DFB to check the antenna parameters of the antenna (written on the LEAP cluster) and acquire data when the tracked source is a pulsar.

After having prepared the ROACH1 for LEAP observations and launched
"./simple_server", you are ready to set up the DFB.


#. Make sure the DFB is turned on (large button at the back) and make sure the cables connected to the DFB are the right ones (DFB3 & DFB4 for L-band, and DFB1 & DFB2 for P-band). 

#. In the “PULSAR” tab, open a terminal and connect to the DFB:

     ``ssh –X corr@psrdfb``    **ask for the password**

#. Check that the DFB clock is correctly synchronized by typing: 

     ``atdc`` and press ``enter``

     Check that the clock is synchronized and that the Tick phase is a
     small number in ns (less than a few hundreds). If the clock needs
     to be re-synchronized, follow `these instructions <http://www.jb.man.ac.uk/~pulsar/observing/DFB.pdf>`_ at pag. 53.


#. Launch **dfbcontroller**:

     ``/home/corr/software/seadas/bin/dfbcontroller``


#. Input these parameters in the dfbcontroller interface:

     - Config: pdfb4_512_1024_1024
     - Subint time (s): 30.0
     - Frequency (MHz): 1548
     - Inverted: no
     - Write file: yes
     - Control mode: change from DIRECT to PASSIVE


6. At the correct time, launch the Nuraghe schedule + start the ROACH
observing. The DFB observing will follow automatically.


7. Throughout the observing session, check that the DFB temperatures
don’t go above 70 degrees. If the temperatures are exceedingly high,
you will need to turn off the DFB for at least half an hour.


8. To end DFB observing, simply change the ``Control mode`` from PASSIVE to DIRECT. Then close the DFB windows.

 

