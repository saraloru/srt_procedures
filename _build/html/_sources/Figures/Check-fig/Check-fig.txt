.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1
 
.. _Check-fig:


ACS Command Center
========

       .. _srt_acs:

       .. figure:: srt_acs.png 
	  :align: center
  
          The **ACS** monitor shows the state of the containers related to each DISCOS component.


Active Surface
=========

       .. _srt_activesurface:

       .. figure:: srt_activesurface.png 
	   :align: center

	   This monitor shows the status of the actuators in a graphical representation of the **Active Surface** and its configuration. 


Logging Display
==========

       .. _srt_jlog:

       .. figure:: srt_jlog.png 
	   :align: center

	   The **Logging Display** shows the log messages related to
	   the observation. New messages are shown on top of the
	   previous ones. 


Meteo Client
=========

       .. _srt_meteo:

       .. figure:: srt_meteo.png 
	   :align: center

       The **Meteo Client** window shows the atmospheric temperature
       and the wind parameters (including wind direction) using a
       graphic  interface.




Nuraghe-obs1
========

       .. _srt_vistaglobale:

       .. figure:: srt_vistaglobale.png
	  :align: center

          **Nuraghe-obs1** is the destination for your schedules, and is the machine where you run the system and 
          where you should find the  input terminal and all the monitors.



OperatorInput
========

       .. _srt_operatorinput:

       .. figure:: srt_operatorinput.png 
	   :align: center

           In the **input console** the users can write Nuraghe commands. The prompt is just a sequential number enclosed in <>. 
           If a command is properly read, the system replies repeating the command itself, followed by the operation results 
           (if they are foreseen).


AntennaBoss
========

       .. _srt_antennaboss:

       .. figure:: srt_antennaboss.png 
	   :align: center
          
           The **AntennaBoss** monitor shows the target info, indicating the commanded and actual positions pointed by     
           the antenna. It also gives a feedback on the pointing
           accuracy and on the overall antenna status.


GenericBackend
==========

       .. _srt_genericBackend:

       .. figure:: srt_genericBackend.png 
	   :align: center

	   The monitor **GenericBackend** shows the backend setup parameters related to each section.


Mount
====

       .. _srt_mount_ok:

       .. figure:: srt_mount.png 
	   :align: center

	   Observers must focus only on the **Mount** status and on the online readouts for the Azimuth and Elevation axes, 
           compared to the commanded positions, located in the top left section.


Observatory
========

       .. _srt_observatory:

       .. figure:: srt_observatory.png 
	   :align: center

           The **Observatory** monitor shows the station coordinates and times.



ReceiversBoss
==========

       .. _srt_receivers:

       .. figure:: srt_receivers.png 
	   :align: center

	   The **ReceiverBoss** monitor summarizes the frontend setup parameters. 
           The bottom part is devoted to the derotator (dewar positioner),  when available.

Scheduler
======

        .. _srt_scheduler:

     	.. figure:: srt_scheduler.png 
	   :align: center
          
           The **Scheduler** monitor shows details on the selected data acquisition devices and on the running schedule, if any.


MinorServo
=======

       .. _srt_minorservo:

       .. figure:: srt_minorservo.png 
	   :align: center

	   The **MinorServo** monitor shows the current setup code and the minor servo status and movement.



Calibration tool client
==============

       .. _srt_calibrationtool:

       .. figure:: calibrationtool_cut.png 
	   :align: center

           In the **Calibration tool client** window the subscan
           currently being acquired is shown in real-time (upper
           plot), even if in a low-resoltution. In the lower plot, the
           last completed subscan - in its full sampling - is
           shown. We can read the information about the pointing
           of focus offsets (peakoffsets), the beam size (HPBW), etc.


GenericBackendX
===========

       .. _srt_backendXarcos:

       .. figure:: generic-backend-Xarcos.png 
	   :align: center

           A second **GenericBackend** panel shows the setup
	   parameters of each section of Xarcos.

	   

Primary Control Panel ACU
=================

       .. _srt_ACU_green:

       .. figure:: srt_ACU_green.png 
	   :align: center

           Primary Control Panel ACU. 
