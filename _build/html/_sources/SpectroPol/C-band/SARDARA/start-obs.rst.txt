.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  
.. _start-SPCSa:

Start the observations
======================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel


#. Insert your project number

    ``> project=[projectID]``

#. Initial setup

    ``> antennaReset``

    ``> setupCCB``


#. Select the active surface shape (Shaped configuration for C-band observations)

    ``> asSetup=S``

#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]``

#. Select and configure the SARDARA backend

    ``> chooseBackend=BACKENDS/Sardara``

    ``> initialize=SC00``


#. Set the different parameters of the backend :

    ``> setSection=[sect],[startFreq],[bw],[num-feed],[polarization],[sampleRate],[bin]``

    with : 

      - ``[sect]``: 0 in full Stokes observations ;
      - ``[startFreq]`` corresponds to the initial frequency in MHz from the LO value ; 
      - ``[bw]`` the bandwidth in MHz ; 
      - ``[num-feed]``: 1 (number of feed in C-band) ;
      - ``[polarization]``: 2 for full Stokes observations ;
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
