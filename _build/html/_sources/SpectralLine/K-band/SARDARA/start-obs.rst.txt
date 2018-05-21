.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  
.. _start-SLKSa:

Start the observations
=======================

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

#. Select and configure the SARDARA backend in K-band

    ``> chooseBackend=BACKENDS/Sardara``

    ``> initialize=[code]``

     with :

       - ``[code]`` = SK00 : central feed only ;
       - ``[code]`` = SK77 : 7 feeds ;
       - ``[code]`` = SK03 : feeds 0 and 3 only ;
       - ``[code]`` = SK06 : feeds 0 and 6 only.


#. Set the different parameters of the backend:

   ``> setSection=[sect],[startFreq],[bw],[num-feed],[polarization],[sampleRate],[bin]``

     with : 

        - ``[sect]`` = 0, 1, 2, 3, 4, 5, 6 in full Stokes observations
          ;
        - ``[sect]`` = 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11,12, 13 in
          non full Stokes observations ;
        - ``[startFreq]`` corresponds to the initial frequency in MHz
          from the LO value ; 
        - ``[bw]`` the bandwidth in MHz ; 
        - ``[num-feed]`` the number of feeds (from 1 to 7) ;
        - ``[polarization]``: the polarization mode ;
        - ``[sampleRate]`` in MHz ;
        - ``[bin]`` the frequency channels (1024, 2048, 4096, 8192, 16384).

    
#. Choose the integration time in ms (e.g. n=10 corresponds to 100 spectra/sec)

   ``> integration=[n]``


#. If you want to use the multi-feed derotator to prevent field rotation during long acquisition, select the derotator configuration :

    ``> derotatorSetConfiguration=[config]``   with ``[config]`` = BSC, CUSTOM or FIXED.

        - BSC is for Best Coverage Space (automatic rotation of the
          dewar in order to best cover the scanned area).

        - CUSTOM : the user has to choose the angle of the dewar axis
          with the y-axis of the scanning frame that will be kept
          during the whole duration of the acquisition :
          ``>  derotatorSetPosition=[ang]d``     with ``[ang]`` the
          dewar angle in degrees.

        - FIXED : the dewar keeps a fixed postion w.r.t the horizon,
          no rotation is applied. To specify a static angle :
          ``>  derotatorSetPosition=[ang]d``     with ``[ang]`` the
          dewar angle in degrees.


    To read back the position of the dewar :

    ``> derotatorGetPosition`` 


#. Attenuate the signal based on the rms range [-128 ;128] and check the value on the interface.

    ``> getrms``  ???

    ``> setAttenuation=[sect],[att]``    with [att] the attenuation from 0 to 15 dB.


#. Check the tsys (typical values)

    ``> tsys``


#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[projectID]/[schedulename].scd,[N]``
