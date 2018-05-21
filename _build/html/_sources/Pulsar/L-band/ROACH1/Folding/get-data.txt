.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  
======================
Getting your data
======================

The data have been written on the nodes of the LEAP cluster (in *.ar
files). You can do a ``psradd`` to add them on each node and copy the
result onto the head node (leap0) in ~/DATA/. Then do a ``psradd -R``
in ~/DATA/ to add the data from all the nodes. 

In the near future, we’ll have a code ready in leap0 (the head node)
in ~/roach/scripts/ that does this, and that can be launched in W1
after the daemons are closed: 

   ``$~/roach/scripts/add.sh``

This data (in .ar format) can then be transferred to *nuraghe-obs1* or a
personal computer using “scp”. In LEAP cluster VNC:

   ``$ scp -r ~/DATA/[today’s date]  [projectID]@nuraghe-obs2:/archive/data/[projectID]/``
