.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  
======================
End of the session
======================

Your observations are now finished, we can stop the schedule and park
the antenna.


On nuraghe-obs1
------------------

#. Close SEADAS 

#. Close the vnc session on seadas


#. Close, in the given order, dfbcontroller, tkds and dfb3

#. Close the vnc session on psrdfb



#. Park the minor servo, active surface and antenna

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
