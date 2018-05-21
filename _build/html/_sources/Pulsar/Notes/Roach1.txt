.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

======================
Notes about the ROACH1 backend
======================

The ROACH1 has the capability to process 32 x 16 MHz bands = 512 MHz of bandwidth, therefore the entire L-band and P-bands. It is not adequate for observing in C-band or K-band unless one wants to observe a smaller portion of the total bandwidth. With the current setup of being linked to an 8-node CPU cluster (the “LEAP cluster”), it can only process 8 x 16 MHz bands = 128 MHz of bandwidth. It is therefore adequate for LEAP observations, which observe only a portion of the total L-band, or for the entire P-band. A second ROACH1 board (ROACH1_GPU) will be linked to the SARDARA GPU cluster and will be able to process the entire L-band (512 MHz). 

These instructions are temporary and do not include the use of SEADAS. Since the ROACH1 is not “integrated” into the Nuraghe antenna control system, Nuraghe is used only to point at the sources, while with the use of the externalClient, the ROACH1 has been automated to follow the antenna. To tell Nuraghe to track sources, the user can use manual instructions or load a standard Nuraghe schedule. To tell the ROACH1 to start/stop data acquisition, the user can launch the automated system on the LEAP cluster which follows what the antenna is doing (start of data acquisition when the antenna is TRACKING and stop when the antenna is SLEWING). In case of problems with the externalClient, the start and stop of data acquisition can also be done manually on the LEAP cluster. 

For more information, contact D. Perrodin.

