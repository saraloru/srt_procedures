.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.



===================
Check during the observations
===================

.. toctree::
   :maxdepth: 1
  

Data quality
------------

#. In the leap0 VNC, go to W3 to check on data quality. Each tab is connected to a cluster node, i.e. a particular 16 MHz sub-band. In each node, go to the data directory:

    ``$ cd /data-001``   for node1

    ``$ cd /data-002``   for node2, etc...


#. In each node, check that the right folders (source and timestamp) are being created and that “dada” files are being written every 10 seconds. If no dada files are being written, there could be something wrong with the IP table.  For example, if one node is malfunctioning (e.g. is turned off) but is listed in the IP table as one would expect, it will cause packet loss or possibly even not write any dada files in the other nodes. In that case, check that all nodes are functioning correctly (see daemons in W1). If the node is definitely not working, you will need to ask a qualified person to look into it [this will involve taking the node out in the IP table before re-starting data acquisition].
      

#. Check for any packet loss with ``dadatest``. Find the last dada file in each folder and check  that no packet loss has occurred so far:

    ``$ dadatest nameoflastdadafile.dada`` 

     The numbers on the left should give you: 0, 2000000, 4000000, 6000000, 8000000, 1000000, 12000000, 14000000, 16000000, 18000000. If not, there has been packet loss and there could be something wrong going on with the cluster. In this case, you can investigate where the packet loss happened using:

    ``$ for i in $(ls *dada); do dadatest $i; done``   (to test all dada files)  

     Occasional packet loss is nothing to worry about. However if the numbers are completely random and the cluster is losing packets in all nodes, we’re in trouble [ask a qualified person to go and manually reset the LEAP switch while data acquisition is  ongoing]. Once that is done, stop data acquisition (with ``Control-C`` and ``./stop.csh``) and re-start with ``./start.csh``. You can then check ``dadatest`` in the newly created folder.

     Note: ``dadatest`` can be done even if we’re not tracking a particular source.

#. Check the data quality with ``digistat``. Type:

    ``$ digistat *dada`` 

     At the prompt, type ``/xs`` or ``/xw`` then ``ENTER`` 


     The curve on the right should be a nice Gaussian. If not, something went wrong with the receiver or with the cluster. Check that we are indeed observing L-band.

     To exit the plotting, just press ``CONTROL-C``.


#. Check the bandpass using ``passband``. Type:

    ``$ passband *dada`` (then ``/xs`` or ``/xw``) 



External client
------------

#. If something goes wrong with the external client (e.g. failing to give you antenna parameters), you should kill (using ``Control-C``) the control.csh code.
 
    Then go see what is wrong with the External Client. If you manage to fix it, re-start: ``./control.csh``.
 
    Failure of the external client does not affect data acquisition with the ROACH while the antenna is tracking. The ROACH keeps recording data. The external client only matters when the antenna is going from TRACKING to SLEWING or from SLEWING to TRACKING.


#. If the external client is not working at all and you need to manually launch data acquisition (i.e. you cannot use the ``./control.csh`` script that is normally used during LEAP to automate data acquisition), you can do the following:

     - at the beginning of the session, set up the ROACH using: ``./control_init.csh`` (W2)
     - Launch the daemons in all 8 nodes (W1)
     - Use ``./start_simple.csh`` to launch data acquisition (instead of ``./start.csh``) (W2)
     - Use ``./stop.csh`` to stop data acquisition without closing the daemons (W2)
     - Use ``./start_simple.csh`` for next source etc. (W2)
     - at the end of the session, use ``./end.csh`` to stop data acquisition and close the daemons (W2)


#. If the external client is working and you are just doing some tests, you can use:
 
     - at the beginning of the session, set up the ROACH using: ``./control_init.csh`` (W2)
     - Launch the daemons in all 8 nodes (W1)
     - Use ``./start.csh`` to launch data acquisition (W2)
     - Use ``./stop.csh`` to stop data acquisition without closing the daemons (W2)
     - Use ``./start.csh`` and ``./stop.csh`` for each source (W2)
     - At the end of the session, use ``./end.csh`` to stop data acquisition and close the daemons (W2)
 
The difference between ``./start.csh`` and ``./start_simple.csh`` is that ``./start_simple.csh`` does not call the external client to get information about the source. If the external client is working, use ``./start.csh`` and the right folders will be automatically created using the name of the source that is being tracked and the most recent timestamp.


Antenna tracking
-------------

#. Antenna monitors

	Check that everything section is green. If a red box appears, put the cursor on it and look at the error message.

	Contact and report the error messages to the responsible of
	the observation (observer friend?).

#. Panels

        * Scheduler : status OK, green

	During the tracking, @ is green while it is red during the slewing of the antenna.

	Check the update of the number of scan/subscan according to your schedule. Scans will be skipped if the target is not visible at the moment of the observations.

	If you realize that the scan/subscan number is frozen or that the tracking @ is red while the antenna is tracking the source, stop the on-going schedule with 

	``> antennaStop``    (in the operatorInput)

	then start again the schedule:

	``> antennaStart=[projectID]/…scd,n``     (with n the number of scan)

     	.. image:: srt_scheduler.png 
	   :align: center

 	* AntennaBoss : status OK, green.
		
     	.. image:: srt_antennaboss.png 
	   :align: center


 	* Mount : READY, READY, OK green (CHECK!!!!) while the antenna is pointing a source.

    	.. image:: srt_mount.png 
	   :align: center

 
 	* MinorServo; tracking @ is green, the status ids OK and green.

    	.. image:: srt_minorservo.png 
	   :align: center


 	* Receivers : status OK, green.

	If the derotator (dewar) is used, check the configuration and status (ready green).

    	.. image:: srt_receivers.png 
	   :align: center


#. Active surface

 	Sometimes, not all of the small squares of the active surface are green. Do not worry for that. Instead, it can be problematic if a large fraction of the active surface becomes red.


	* Check that the state of the active surface corresponds to your choice (shaped, shaped fixed, parabolic, parabolic fixed).


 	* “Ok” should be green during the observations.

    	.. image:: srt_activesurface.png 
	   :align: center


#. Log

 	* The log file (jlog) contains warning and error messages. Warning messages are indicated in yellow while error messages are in red.

 
 	* Check the possible error messages. Try to understand the origin of the problem and to solve it. In case of persistent/complex problem, contact and report the error messages and the associated UT to the responsible of the observation (observer friend?).



    	.. image:: srt_jlog.png 
	   :align: center


#. Calibration tool client


    	.. image:: srt_calibrationtool.png 
	   :align: center


#. Weather parameters

 	 On nuraghe-obs1, activate the meteo client:

	``$ meteoClient``

         If the wind speed exceeds 61 km/h, the antenna must be stowed.

         .. image:: srt_meteo.png 
	    :align: center

	
