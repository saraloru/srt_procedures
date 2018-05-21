.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1

.. _check-obs:

Checks during the observations
==============================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel

.. |logo| image:: monocle_.png 
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check on the monitor

==============================


.. On nuraghe-obs2 ---------------

.. #. Check that the data are correctly written in your project section :

..    $ cd /archive/data/[projectID]/``   


.. #. Look at the Quick-look of the data :

..    $ idl``             

..    IDL> .r fitslook``

..    IDL> fitslook``
	
.. Note that the subscans are shown with a short delay in the
.. quick-look plots with respect to the real observations.



On nuraghe-mng
--------------

#. Check that the data are correctly written in your project section (Maintenance) :

    ``$ cd /archive/data/Maintenance/yyyymmdd``   


#. Look at the Quick-look of the data :

      TBD (tool M. Bachetti)


#. **jlog**

     The logging display shows warning and error messages. Warning
     messages are indicated in yellow while error messages are in red
     |logo| :numref:`srt_jlog`.

     Check the possible error messages. Try to understand the origin
     of the problem and to solve it. In case of persistent/complex
     problem, contact and report the error messages and the associated
     UT to the responsible of the observation. 


#. **Meteo client**

     Check the wind speed on the Meteo client. If it exceeds 60 km/h,
     the antenna is automatically stowed. For observations in K-band,
     the wind speed should not exceed 30 km/h (value to be checked)
     otherwise the pointing accuracy will probably be lost. |logo| :numref:`srt_windspeed`

  
     .. On nuraghe-obs1 --------------

#. **Scheduler**

     Check the status of the Scheduler is OK (green).
     During the tracking, @ is green while it is red during the
     slewing of the antenna. |logo| :numref:`srt_scheduler`

     Check the update of the number of scan/subscan according to your
     schedule (.scd). Scans will be skipped if the target is not
     visible at the moment of the observations.

     If you realize that the scan/subscan number is frozen or that the
     tracking is red while the antenna is tracking the source, stop
     the on-going schedule with:

     ``> stopSchedule``    (in the operatorInput)

     then start again the schedule:

     ``> startSchedule=[projectID]/…scd,n``    (with n the number of scan)


#. **MinorServo**

     Check the status and the tracking are green |logo| :numref:`srt_minorservo`.


#. **ReceiverBoss**

     Check the status is OK (green). If the derotator (dewar) is used,
     check the configuration and status (ready green). |logo|
     :numref:`srt_receivers`


#. **AntennaBoss**

     Check the status is OK (green), the coordinates of the source and
     the beam size value are correct (FWHM in degrees). 
     The tracking @ is green when the source is correctly pointed
     (within 1/10 of the beam), while a red circle appears when the
     telescope is in slewing. |logo| :numref:`srt_antennaboss`
  

#. **Mount**

     Check the commanded azimuth and elevation of the antenna and
     its real position (in blue). The status must be green. 
     |logo| :numref:`srt_mount`


#. **Active surface**

     Check that the state of the active surface corresponds to your
     choice (shaped, shaped fixed, parabolic, parabolic fixed). |logo|
     :numref:`srt_activesurface`

     "OK" should be green during the observations. 

     Sometimes, not all of the small squares of the active surface are
     green. Do not worry for that if they are spread randomly. Instead, it can be problematic if a
     large fraction (a whole sector) of the active surface becomes
     red, in particular in K-band (see |logo|
     :numref:`srt_AS-fraction-red`).
     Contact the responsible of the observation (observer friend).


Primary Control Panel ACU
---------------------

Check that everything appears in green (see |logo|
:numref:`srt_ACU_green`). 
If a red box appears, put the cursor
on it and look at the error message.

Contact and report the error messages to the responsible of the observation (observer friend).





	
