.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

===================
Identification of the problems
===================

Depending on the problem, you can be able to resolve it.
The first thing is to identify the origin of the error.

Check the presence of error messages on the different panels, the jlog
and ACS.


Panels
=====

The error messages usually come out in red.

* **Scheduler**

The Status is indicated in FAILURE when the schedule is not running
correctly. If the Scan/SubScan number is proceeding correctly, the
FAILURE can be associated with skipped scans because of the too high
elevation of the source (> 85°). 

**Solution**: stop the schedule with  ``> stopSchedule`` and 
check the elevation of the target with `CASTIA <http://www.ira.inaf.it/Observing/castia/site/index.php>`_.
Then start again the schedule with ``> startSchedule=[projectID]/[schedulename].scd,[N]`` when the target is visible.


Jlog
====


ACS
====


MeteoClient
========

On a shell of nuraghe-mng, check that wind velocity does not
exceed 60 km/h (indicated with the red horizontal line).

``$> meteoClient &``

If the wind speed is beyond this limit, stop immediately the
observations and park the antenna (link). 



===================
Unresolved problems
===================

If you do not find the origin of the problem or the problem is too
complex to be resolved, please contact the person in charge of the
observations (observer's friend).



