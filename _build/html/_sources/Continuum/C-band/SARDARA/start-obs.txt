.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.



.. toctree::
   :maxdepth: 1
  
.. _start-CoCSa:

Start the observations
======================


$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel



.. |logo| image:: monocle_.png 
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check on the monitor


======================
 


#. Insert your project number :

    ``> project=[projectID]`` |logo| :numref:`srt_scheduler`

#. Initial setup :

    ``> antennaReset``

    ``> setupCCB`` |logo| :numref:`srt_receivers`

#. Select the active surface shape (Shaped configuration for C-band observations) :

    ``> asSetup=S`` |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz :

    ``> setLO=[freq]`` |logo| :numref:`srt_receivers`

#. Select and configure the SARDARA backend :

    ``> chooseBackend=BACKENDS/Sardara`` |logo| :numref:`srt_scheduler`

    ``> initialize=SC00``

#. Set the different parameters of the backend :

    ``> setSection=[sect],[startFreq],[bw],[num-feed],[polarization],[sampleRate],[bin]`` |logo| :numref:`srt_genericBackend`

    with : 

      - ``[sect]``: 0 in full-stokes observations and ``[sect]``: 0, 1 in non full-stokes observations ;
      - ``[startFreq]`` corresponds to the initial frequency in MHz from the LO value ; 
      - ``[bw]`` the bandwidth in MHz ; 
      - ``[num-feed]``: 1 (number of feed in C-band) ;
      - ``[polarization]`` = 0 or 1 : Left and Right ; 2 : full Stokes) ;
      - ``[sampleRate]`` in MHz ;
      - ``[bin]`` the frequency channels (1024, 2048, 4096, 8192, 16384).

#. Choose the integration time in ms (e.g. n=10 corresponds to 100 spectra/sec) :

     ``> integration=[n]``

#. Attenuate the signal based on the rms range [-128 ;128] and check the value on the interface :

     ``> getrms``  **(ASK A. MELIS)**

     ``> setAttenuation=[sect],[att]``    with [att] the attenuation from 0 to 15 dB.  |logo| :numref:`srt_genericBackend`

#. Check the tsys (typical values to be inserted) :

     ``> tsys`` |logo| :numref:`srt_genericBackend`

#. Report the ground temperature, relative humidity, atmospheric pressure, and wind speed :

     ``> wx``

#. Follow the link below to perform the pointing and focus optimization (if not already included in your schedule) :

       :ref:`pointing-focus`

#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

      ``> startSchedule=[projectID]/[schedulename].scd,[N]``  |logo| :numref:`srt_scheduler`
