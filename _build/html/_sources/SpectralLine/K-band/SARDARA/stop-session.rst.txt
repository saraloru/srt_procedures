.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1
  
======================
End of the session
======================

Your observations are now finished, we can stop the schedule and park
the antenna.


On nuraghe-obs1
------------------

1. Stop your schedule :

   ``> stopSchedule``   *interruption of the current subscan*

or

   ``> haltSchedule``    *the schedule stops at the end of the on-going subscan.*




2. Park the minor servo, active surface and antenna

   ``> goTo=180d,89d``

   ``> servoPark``

   ``> asPark``

   ``> antennaPark``



Block the axes of the antenna
--------------------------

Look at the monitor of the antenna and wait until the upper right
panel becomes red. It can take a few minutes after the command
*antennaPark* has been given. 

Only at this moment, you can press on the red button.
