.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1

.. _pointing-focus:

======================
Pointing and Focus optimization
======================


$  : commands to insert in a shell

>  : commands to insert in the operatorInput panel


.. |logo| image:: monocle_.png
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check on the monitor


======================


Pointing
======

     The pointing optimization depends on the elevation of the sources. It is strongly
     recommended to perform it before observing a source (calibrators
     and target of your schedules). 
     If the target you plan to observe is too weak to present a good S/N,
     select a calibrator bright enough and located close to your
     target (`see the internal report N°27 <http://www.oa-cagliari.inaf.it/area.php?page_id=10&skip=4>`_.)

#. Set the azimuth and elevation offsets to 0 degree.

    ``> azelOffsets=0d,0d``

#. Choose and track a proper calibrator.
    
    ``> track=[name]``  if the calibrator is in the SRT database 
    (e.g. 3c147 => note **c** in lower case)

    otherwise  ``> sidereal=[name],[RA],[Dec],[epoch],[sector]``  

    * ``RA, Dec``: Pay attention to the coordinate formats:
      - decimal degrees, using a **d** suffix, for any coordinate (e.g. 30.00d)
      - sexagesimal degrees, with no suffix, for any coordinate (30:00:00)
      - hh:mm:ss, with a **h** suffix, for longitudes only (02:00:00h).

    * ``epoch``: 1950, 2000 or -1, the last one meaning that the
      provided coordinates are precessed to the observing epoch. 

    * ``sector``: to force the cable wrap sector, if needed. Its value
      can be CW, CCW or neutral. Usually, use *neutral*.

     e.g. ``> sidereal=3c84,03:19:48.16h,41:30:42.1,2000,neutral``
     or   ``> sidereal=3c84,49.951d,41.512d,2000,neutral``


#. Choose the recorder :

    ``> chooseRecorder=MANAGEMENT/CalibrationTool``

#. Open the calibrationtool client in a terminal to display the plots in real time :

    ``$ calibrationtoolclient MANAGEMENT/CalibrationTool``  |logo| :numref:`srt_calibrationtool`

#. Set proper parameters according to your beamsize and coordinate frame in order to perform a correct pointing measurement :

    ``> crossScan=HOR,0.5d,00:00:20``

    * ``HOR`` or ``EQ`` frame: use the same coordinate frame as in the .lis of
      the schedule otherwise the  offsets will be rejected.

    * ``0.5d`` indicates the scan length in degrees (in this example 0.5°)

    * ``00:00:20`` indicates the duration of the scan (in this example: 20 seconds).

    
#. Look at the calibrationtool client to check the pointing offsets.

    Pointing offsets must be less than 1/10 of the beamsize (i.e. about < 0.005
    deg in C-band and < 0.00125 deg in K-band). 


#. If you want to reject the measured offsets :

   ``> azelOffsets=0d,0d``   

   and repeat the pointing scan procedure.


Focus
======

#. Set proper parameters according to your beamsize :

   ``> focusScan=150,00:01:00``

    The first number should be three times the wavelength of
    observation in mm (e.g. in C-Band 3*5cm = 150mm).

#. Look at the calibrationtool client to check the focus measurements.

    The focus is correct if you see a Gaussian with an offset lower
    than a few tenth of  mm with respect to the zero.

#. If you want to reject the updated focus position with: 

   ``> clearServoOffsets``

   and repeat the focus scan procedure.
