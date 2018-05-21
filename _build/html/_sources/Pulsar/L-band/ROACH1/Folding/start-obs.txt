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

    ``> setupLLP``


#. Select the active surface shape (Parabolic for L and P-band observations) :

    ``> asSetup=P``


#. Insert the Local Oscillator value in MHz (this value may change) :

    ``> setLO=2188``


#. Choose the relevant L-band filter (linear filter for 1300-1800 MHz)

    ``> receiversMode=XXL4``


#. Set the attenuations (to zero) for the 2 polarizations arriving at the Total Power backend (this may change depending on the settings of the new IF distributor).

    ``> setAttenuation=0,0``

    ``> setAttenuation=1,0``

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

    ``$ ./start.csh``

     Data acquisition has now started with the ROACH1. 

#. Immediately launch the control software (in W2) which obtains parameters from the antenna and automatically starts and stops observations, depending on whether the antenna is **TRACKING** or **SLEWING**:

    ``$ ./control.csh``

If necessary, this code can be interrupted (using Control-C) and re-started at any time while the antenna is tracking the same source, without any consequences. 

You should now see: **“no change. keep doing what you’re doing”** while the antenna keeps tracking the same source. If all goes well, you won’t need to do anything else with data acquisition for the remainder of the session. You should however check the control window (W2) once in a while for possible errors (e.g. antenna WARNING). 


