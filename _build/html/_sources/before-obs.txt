.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1
  
.. _before-obs:

======================
Important checks
======================

Some checks need to be performed before starting the observations.


On nuraghe-mng
------------------

Check that :
   - all of the **32 containers** are active on ACS (MNG virtual desktop) (:numref:`srt_acs`);
   - the **active surface** is green on the AS virtual desktop (:numref:`srt_activesurface`);
   - the log client **jlog** is open in order to track possible error
     messages (:numref:`srt_jlog`). In case it is not open, type ``$
     jlog &`` on a shell;
   - the interface of the **Meteo client** is open to check the wind
     velocity in real time (< 60 km/h) (:numref:`srt_meteo`). If it is
     close, type ``$ meteoClient &`` on a shell.



.. On nuraghe-obs1 ------------------


Check the presence of the 8 panels (:numref:`srt_vistaglobale`): 
   - **operatorInput** (:numref:`srt_operatorinput`)
   - **AntennaBoss** (:numref:`srt_antennaboss`)
   - **GenericBackend** (:numref:`srt_genericBackend`)
   - **Mount** (:numref:`srt_mount_ok`)
   - **Observatory** (:numref:`srt_observatory`)
   - **Receivers** (:numref:`srt_receivers`)
   - **Scheduler** (:numref:`srt_scheduler`)
   - **MinorServo** (:numref:`srt_minorservo`)


**Upload your shedules (.scd, .lis, .bck and .cfg files) and check them:**

   *From your computer:*

   ``$ scp  [schedulename.*] gavino@nuraghe-mng:/archive/schedules/[projectID]``

   *On nuraghe-mng:*

   ``$ cd /archive/schedules/[projectID]``

   ``$ scheduleChecker [schedulename.scd]``


.. Upload your shedules (.scd, .lis, .bck and .cfg files) and check them :

..   *From your computer:*

..   $ scp  [schedulename.*] observer@nuraghe-obs1:/archive/schedules/[projectID]``

..   *On nuraghe-obs1:*

..   $ cd /archive/schedules/[projectID]``

..   $ scheduleChecker [schedulename.scd]``
