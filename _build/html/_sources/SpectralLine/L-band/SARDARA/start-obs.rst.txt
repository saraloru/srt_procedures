.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  

.. _start-SLLSa:

Start the observations
======================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel


#. Insert your project number

    ``> project=[projectID]``

#. Initial setup

    ``> antennaReset``

    ``> setupLLP``

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


#. Select the active surface shape (Parabolic for L-band observations)

    ``> asSetup=P``


#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]``

#. Select and configure the SARDARA backend in L-band

    ``> chooseBackend=BACKENDS/Sardara``

    ``> initialize=SL00``


#. Set the different parameters of the backend :

    ``> setSection=[sect],[startFreq],[bw],[num-feed],[polarization],[sampleRate],[bin]``

     with : 

       - ``[sect]`` : 0 in full Stokes observations and ``[sect]`` :
         0, 1 in non full-stokes observations ;
       - ``[startFreq]`` corresponds to the initial frequency in MHz from the LO value ; 
       - ``[bw]`` the bandwidth in MHz ; 
       - ``[num-feed]``: the number of feed : 1 in L-band ;
       - ``[polarization]`` = 0 or 1 : Left and Right ; 2 : full Stokes) ;
       - ``[sampleRate]`` in MHz ;
       - ``[bin]`` the frequency channels (1024, 2048, 4096, 8192, 16384).

    
#. Choose the integration time in ms (e.g. n=10 corresponds to 100 spectra/sec)

    ``> integration=[n]``


#. Attenuate the signal based on the rms range [-128 ;128] and check the value on the interface.

    ``> getrms``  ???

    ``> setAttenuation=[sect],[att]``    with [att] the attenuation from 0 to 15 dB.

#. Check the tsys (typical values)

     ``> tsys``

#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

     ``> startSchedule=[projectID]/[schedulename].scd,[N]``
