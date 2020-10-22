.. VScodeDemo documentation master file, created by
   sphinx-quickstart on Thu Oct 22 19:40:55 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to my VS Code Demo
==========================

This documentation will show some of the Features of the F5 VScode extension "F5-FAST".

Furthermore it'll show of to do basic AS3 & FAST calls and integration into git.

If you find any issues, or want to include any additional scripts, please send me an email (m.petersen@f5.com) or open a github issue (https://github.com/de1chk1nd/VScodeDemo/).

Finally - big props to Ben Gordon ( https://github.com/DumpySquare ) from whom I "stole" a lot of conetnt and used it in here (and who wrote the F5-FAST extension!!).


.. warning::
   The whole project is currently "work in progress" - documentation and scripts are not yet finished.




Lab Setup - Devices
-------------------

If you want to set up a lab, as used in this documentation (to use the c&p ready scripts), you'll need 3 devices:

* Client with VS Code
* BigIP 1
* BigIP 2

Each device is member of two VLANs: management (10.1.1.0/24); external (10.1.10.0/24)


========  ========  ==========
 Device    IP MGMT   IP Prod
========  ========  ==========
 Client   10.1.1.2  10.1.10.2
 BigIP-1  10.1.1.5  10.1.10.5
 BigIP-2  10.1.1.6  10.1.10.6
========  ========  ==========



.. image:: images/LAB_Design.png
   :width: 800
   :alt: Lab Overview
   :align: center


Why this Blueprint
------------------

I think that using VScode and the F5-FAST extension will help NetOPS to get familiar with DevOPS methodologies - as well as help DevOPS to get familiar with f5 (in an automation fashion-style).

There are many tools (Postman), but as this F5-FAST extension helps to automate things, plus be able to directly connect to your own git repo (VScode feature), I find it very helpfull to get familiar using the F5 Automation Toolchain (ATC).

| 

.. toctree::
   :numbered:
   :maxdepth: 2
   :caption: Contents:

   Introduction <Introduction>
   Basic Set Up <basic>
   AS3 <AS3>
   FAST <FAST>
   RPM Management <rpm>
   VSCode as a API <API>
   Troubleshooting <Troubleshooting>

