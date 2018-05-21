.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  
======================
Roach setup
======================

Initial setup for the LEAP cluster.


In the VNC
----------

#. Open a window (W1) with 8 tabs. Each tab will be connected to each of the 8 cluster nodes and will be used to launch the daemons. In the first tab, type:

    ``$ ssh -X node1``

    ``$ ssh -X node2``   in the second tab, etc... for the 8 tabs.


#. Open a second window (W2) and go to :

    ``$ ~/externalClient/Control/``

     This window will be used to start and stop data acquisition.

#. In W2: type a command here to select L-band (and not P-band):

      **Need to go to SRT to remember what the name of that code
      is**. 
      That code basically changes the IP table so that we are selecting the desired 8 sub-bands.


#. In W2: type a command here to select baseband mode *(little script still to be written)*:

    ``$ ~/roach/scripts/baseband.sh``

#. Open a third window (W3) with 8 tabs (this will be used to look at the results). As before, type ``$ ssh -X node1``, ``$ ssh -X node2``, etc. for each tab. 


