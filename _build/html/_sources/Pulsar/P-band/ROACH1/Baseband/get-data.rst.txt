.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


===========
Getting your data
===========

.. toctree::
   :maxdepth: 1
  
The data have been written on the nodes of the LEAP cluster. After the observation run, this baseband data needs to be de-dispersed and folded (it may take a few hours and no other observations with the ROACH1 can take place while the cluster is being used). There are various codes in leap0 (the head node) in ~/roach/scripts/ that do this and that can be launched in W1 after the daemons are closed.


For example for each node, one can launch: 

     ``$~/roach/scripts/dspsr.sh`` (as of October 2017, this code needs to be upgraded; update to follow). The final archive data will be stored on the head node of the LEAP cluster (leap0) in ~/DATA/.


This data (in .ar format) can then be transferred to *nuraghe-obs1* or a
personal computer using “scp”. In LEAP cluster VNC:

     ``$ scp -r ~/DATA/[today’s date]  [projectID]@nuraghe-obs2:/archive/data/[projectID]/``


Go ahead and delete the baseband data on the cluster nodes after all of it has been folded. 

