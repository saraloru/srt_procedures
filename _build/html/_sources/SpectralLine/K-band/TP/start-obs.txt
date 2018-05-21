.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1
  

Start the observations
======================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel


#. Insert your project number

    ``> project=[projectID]``

#. Initial setup

    ``> antennaReset``

    ``> setupKKG``


#. Select the active surface shape (Shaped configuration for K-band observations)

    ``> asSetup=S``

#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]``

#. Select the Total Power backend

    ``> chooseBackend=BACKENDS/TotalPower`` 

#. For each section [sect], insert the bandwidth ([bw]=300, 730, 1250 or 2000 MHz) and the sample rate (in MHz) :

    ``> setSection=[sect],*, [bw],*,*,[sampleRate],*``

   Reminder : in K-band there are 7 feeds, so 14 sections with [sect]=0,1,2,3,4,5,6,7,8,9,10,11,12,13.


#. If you want to use the multi-feed derotator to prevent field rotation during long acquisition, select the derotator configuration :

    ``> derotatorSetConfiguration=[config]``   with [config]=BSC, CUSTOM or FIXED


    - BSC is for Best Coverage Space (automatic rotation of the dewar in order to best cover the scanned area).

    - CUSTOM : the user has to choose the angle of the dewar axis with
     the y-axis of the scanning frame that will be kept during the
     whole duration of the acquisition :

    ``>  derotatorSetPosition=[ang]d``     with [ang] the dewar angle in degrees


    - FIXED : the dewar keeps a fixed postion w.r.t the horizon, no rotation is applied. To specify a static angle :

    ``>  derotatorSetPosition=[ang]d``     with [ang] the dewar angle in degrees

   To read back the position of the dewar :

    ``> derotatorGetPosition`` 


#. Put the antenna at 45 deg of elevation and attenuate the signal for
 the 14 sections [sect] in order to obtain values between 750 and 1100
 counts (linear range of the backend) :

     ``> goTo=*,45d``

     ``> getTpi``

     ``> setAttenuation=[sect],[att]``	with [att] between 0 and 15 dB

     ``> getTpi``


#. Check the tsys (typical values)

    ``> tsys``

#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[projectID]/[schedulename].scd,[N]``
