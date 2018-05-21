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

    ``> setupLLP``


#. Select the receiver Mode :

    ``> receiversMode=[mode]``

     - with receiversMode=XXC1;
            receiversMode=XXC2;
            receiversMode=XXC3;
            receiversMode=XXC4;
            receiversMode=XXC5;
            receiversMode=XXL1;
            receiversMode=XXL2;
            receiversMode=XXL3;
            receiversMode=XXL4;
            receiversMode=XXL5.

     Note that C is for *Circular*, L for *Linear polarization* and
     1 : all band, 1300-1800 MHz (no filter);
     2 : 1320-1780 MHz;
     3 : 1350-1450 MHz;
     4 : 1300-1800 MHz (band-pass);
     5 : 1625-1715 MHz.


#. Select the active surface shape (Parabolic for L-band observations)

    ``> asSetup=P``

#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]``

#. Select the Total Power backend

    ``> chooseBackend=BACKENDS/TotalPower``


#. Insert the bandwidth for the focus selector (always 2000 MHz in L-band) and choose the sample rate (in MHz) :

    ``> setSection=0,*,2000.000000,*,*,[sampleRate],*``

    ``> setSection=1,*,2000.000000,*,*,[sampleRate],*``


#. Put the antenna at 45 deg of elevation and attenuate the signal in order to obtain values between 750 and 1100 counts (linear range of the backend) :

    ``> goTo=*,45d``

    ``> getTpi``

    ``> setAttenuation=0,[att]``	with [att] between 0 and 15 dB

    ``> setAttenuation=1,[att]``	with [att] between 0 and 15 dB

    ``> getTpi``

#. Check the tsys (typical values)

    ``> tsys``

#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[projectID]/[schedulename].scd,[N]``
