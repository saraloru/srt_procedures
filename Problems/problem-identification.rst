.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

===================
Problem identification
===================

Depending on the problem, you can be able to resolve it.
The first thing is to identify the origin of the error.
Check the presence of error messages on the different monitor panels, the
jlog, ACS and the ACU control panel. 


Monitor panels
=========

Look at the `8 panels <http://discos.readthedocs.io/en/latest/user/srt/source/Appendix_A.html>`_. The error messages usually come out in red.

.. ATTENTION:: **operatorInput**

Check that the command you have insterted is written correctly. If the error is not
related to a typo, try to identify the origin of the problem. Check
the different panels (Scheduler, MinorServo, Receivers, etc...) and the jlog.


.. ATTENTION:: **Scheduler**
 
:ref:`srt-scheduler` when the schedule is not running
correctly. If the Scan/SubScan number is proceeding correctly, the
FAILURE can be associated with skipped scans because of the too high
or too low
elevation of the source (> 85° or < 5°). 

*Solution*: Stop the schedule with  ``> stopSchedule`` and 
check the elevation of the target with `CASTIA <http://www.ira.inaf.it/Observing/castia/site/index.php>`_.
Then start again the schedule with ``>
startSchedule=[projectID]/[schedulename].scd,[N]`` when the target is
visible.


.. ATTENTION:: **Receivers**

If the local oscillator (LO) value is set to 0 on the **Receivers** panel while you have
inserted a correct value (in MHz) on the operatorInput, the LO container is probably
down (check also the operatorInput and jlog errors). Contact the
person in charge of the observations (observer’s friend) to resolve
the problem.



Jlog
====

.. ATTENTION:: **LoggingClient**

Error messages on the LoggingClient appear in red while warning are in
yellow.
If the **Subscan skipped** message appears, the scheduler is skipping
subscans because of a too high or low elevation of the target (see
previous section).




ACU control panel
====

If one or different boxes appear in yellow (warning) or red (error), put the mouse on
the box and read the associated message.


.. ATTENTION:: **Power errors**

In the case of **err_Power_Error** label, look at the jlog window. The
**MAIN POWER ERROR** message should appear, being assigned a CRITICAL
priority. To resolve the problem, give the following commands in the
operatorInput console:

``> antennaReset``

``> antennaTrack``

If the error message is different or the problem still unresolved, contact the person in charge of
the observations (observer’s friend).



Wind velocity
========

.. ATTENTION:: **MeteoClient**

Check regularly the wind velocity using the ``$> meteoClient &`` on
a shell of nuraghe-mng. For observations in K-band, the wind speed
should not exceed 30 km/h (value to be checked) otherwise the pointing
accuracy will probably be lost. :ref:`srt_windspeed`







