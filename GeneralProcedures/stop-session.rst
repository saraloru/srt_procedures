.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1

.. _stop-session:

End of the session
======================

>  : commands to insert in the operatorInput panel

.. |logo| image:: monocle_.png
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check on the monitor

======================

Your observations are now finished, we can stop the schedule and park
the antenna.

On nuraghe-mng
--------------

.. On nuraghe-obs1 ------------------

1. Stop your schedule :

   ``> stopSchedule``   *interruption of the current subscan*  |logo| :numref:`srt_scheduler`
or
   ``> haltSchedule``    *the schedule stops at the end of the on-going subscan.* 




2. Park the minor servo, active surface and antenna

   ``> goTo=180d,89d`` |logo| :numref:`srt_mount_ok`

   ``> servoPark`` |logo| :numref:`srt_minorservo`

   ``> asPark`` |logo| :numref:`srt_activesurface`

   ``> antennaPark`` |logo| :numref:`srt_mount_ok`



Block the axes of the antenna
------------------------------

Look at the ACU monitor, wait until
**Axis blocked** appears in red. It can take a few minutes after the command
``> antennaPark`` has been given (:numref:`srt_ACU_axisblocked`).

Only at this moment, you can press on the emergency stop button
(:numref:`srt_ACU_redbutton`).

