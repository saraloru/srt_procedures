.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1
  
.. _start-CoLTP:

Start the observations
======================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel



.. |logo| image:: monocle_.png 
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|:check on the monitor


#. Insert your project number :

    ``> project=[projectID]``  |logo| :numref:`Fig. %s, <srt_scheduler>` 


#. Initial setup :

    ``> antennaReset``

    ``> setupLLP``  |logo| :numref:`srt_receivers`


#. Select the receiver mode :

    ``> receiversMode=[code]`` where ``[code]`` can be ``XXC1``,
    ``XXC2``, ``XXC3``, ``XXC4``, ``XXC5``, ``XXL1``, ``XXL2``,
    ``XXL3``, ``XXL4``, ``XXL5``.

       - **C** is for **Circular**, **L** for **Linear polarization** ;
       - **1** : all band, 1300-1800 MHz (no filter) ;
       - **2** : 1320-1780 MHz ;
       - **3** : 1350-1450 MHz ;
       - **4** : 1300-1800 MHz (band-pass) ;
       - **5** : 1625-1715 MHz.



#. Select the active surface shape (Parabolic for L-band observations) :

    ``> asSetup=P`` |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz :

    ``> setLO=[freq]`` |logo| :numref:`srt_receivers`

#. Select the Total Power backend :

    ``> chooseBackend=BACKENDS/TotalPower``  |logo| :numref:`srt_scheduler`


#. Insert the bandwidth for the focus selector (always 2000 MHz in L-band) and choose the sample rate (in MHz) :

    ``> setSection=0,*,2000.000000,*,*,[sampleRate],*``  |logo| :numref:`srt_genericBackend`

    ``> setSection=1,*,2000.000000,*,*,[sampleRate],*``  |logo| :numref:`srt_genericBackend`


#. Put the antenna at 45 deg of elevation and attenuate the signal in order to obtain values between 750 and 1100 counts (linear range of the backend) :

    ``> goTo=*,45d`` |logo| :numref:`srt_mount`

    ``> getTpi``

    ``> setAttenuation=0,[att]``	with [att] between 0 and 15 dB |logo| :numref:`srt_genericBackend`

    ``> setAttenuation=1,[att]``	with [att] between 0 and 15 dB |logo| :numref:`srt_genericBackend`

    ``> getTpi``

#. Check the tsys (typical values to be inserted)

    ``> tsys`` |logo| :numref:`srt_genericBackend`

#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[projectID]/[schedulename].scd,[N]`` |logo| :numref:`srt_scheduler`
