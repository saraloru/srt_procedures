.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1

.. _start-obs:

Start the observations
======================

$  : commands to insert in a shell

>  : commands to insert in the operatorInput panel


.. |logo| image:: monocle_.png
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check on the monitor


======================

#. Insert your project number

    ``> project=[projectID]``    |logo| :numref:`srt_scheduler`


#. Initial setup

    ``> antennaReset``

    ``> setupCCB`` |logo| :numref:`srt_receivers`


#. Select the active surface shape (Shaped configuration for C-band observations)

    ``> asSetup=S``   |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]`` |logo| :numref:`srt_receivers`

#. Select the Total Power backend

    ``> chooseBackend=BACKENDS/TotalPower`` |logo| :numref:`srt_scheduler`

#. Insert the bandwidth (300, 730, 1250 or 2000 MHz) and choose the sample rate (in MHz) :

    ``> setSection=0,*,[bw],*,*,[sampleRate],*`` |logo| :numref:`srt_genericBackend`

    ``> setSection=1,*,[bw],*,*,[sampleRate],*``

#. Put the antenna at 45 deg of elevation and attenuate the signal in order to obtain values between 750 and 1100 counts (linear range of the backend) :

    ``> goTo=*,45d`` |logo| :numref:`srt_mount_ok`

    ``> getTpi``

    ``> setAttenuation=0,[att]``          with [att] between 0 and 15 dB |logo| :numref:`srt_genericBackend`

    ``> setAttenuation=1,[att]``	with [att] between 0 and 15 dB 

    ``> getTpi``

#. Check the tsys (typical values 35,29 K)

    ``> tsys`` |logo| :numref:`srt_genericBackend`


#. Report the ground temperature, relative humidity, atmospheric pressure, and wind speed :

    ``> wx``


#. Follow the link below to perform the pointing and focus optimization (if not already included in your schedule) :


      :ref:`pointing-focus`


#. Open the calibrationtool client in a terminal to display the pointing and focus plots in real time :

    ``$ calibrationtoolclient MANAGEMENT/CalibrationTool``  |logo| :numref:`srt_calibrationtool`


#. Begin the schedule by indicating the start scan [N] or subscan
 [N_n] in the .scd file :

    ``> startSchedule=[projectID]/[schedulename].scd,[N]`` |logo| :numref:`srt_scheduler`
