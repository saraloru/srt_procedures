.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  

.. _start-PuCDF:

Start the observations
======================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel



On seadas
----------

Place your observing files in corr@seadas as follows:

   - your seadas setup file(s) in folder:    corr@seadas:/home/corr/setup/[your project code]

   - your seadas schedule file(s) in folder: corr@seadas:/home/corr/scheds/[your project code]



On nuraghe-obs1
------------------

#. Insert your project number

    ``> project=[projectID]``

#. Initial setup

    ``> antennaReset``

    ``> setupCCB``

    ``> goTo=*,81.9d``


#. On a terminal open a vnc session for corr@seadas:

    ``$ vncviewer seadas:1``

#. If this fails, start a new vnc session on corr@seadas. 

#. Type password at prompt. 



#. On another workspace, open a new terminal and start a vnc session for corr@psrdfb:

    ``$ vncviewer psrdfb:2``

#. If this fails, start a new vnc session on corr@psrdfb. 

#. Type password at prompt. 


In the vnc session corr@seadas
----------------------------------

#. Open a terminal and start SEADAS

    ``$ seadas``

#. In the log frame of seadas main window check that SEADAS connects to nuraghe

#. Click on the red label at the top right corner of the Antenna and Pointing Management frame.

#. Check that the clicked label becomes green and dislpays the word "ENABLED"


In the vnc session corr@psrdfb
----------------------------------

#. Open a terminal and check the system clock is working properly (time properly synchronized, tick phase ~ 100 ns, positive or negative) by typing

    ``$ atdc``

#. Open a new terminal and start DFBCONTROLLER

    ``$ /home/corr/software/seadas/bin/dfbcontroller``

#. In DFBCONTROLLER window, check that the colored label at the right of the
  "tkds" label is green and displays the word "CONNECTED". If not, click on it.


Inside SEADAS window
------------------------

#. Verify and adjust attenuation levels

#. Select "Schedule" in the "Session mode" combo box

#. Click "View obs list". A window named "Observations List" pops up

#. Click "View schedule". A window named "Schedule Manager" pops up

#. Click "Load sched" in "Schedule Manager" window. A system window pops up for browsing system directories and selecting the schedule file

#. In "Schedule manager" window select schedule lines to be done - mouse left click on each single line - or click button "Select all" for loading the entire schedule in the "Observations List" window

#. If necessary, rearrange the order of the observations in the "Observations List" window  - left button click == cut line ; mid button click == paste line

#. Click "Observe"
