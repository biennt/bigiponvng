.. |labmodule| replace:: 1
.. |labnum| replace:: 3
.. |labdot| replace:: |labmodule|\ .\ |labnum|
.. |labund| replace:: |labmodule|\ _\ |labnum|
.. |labname| replace:: Lab\ |labdot|
.. |labnameund| replace:: Lab\ |labund|

Lab |labmodule|\.\ |labnum|\: CGNAT within AFM
----------------------------------------------

NAPT Configuration
~~~~~~~~~~~~~~~~~~

#. Create subscriber NAPT configuration (This can be used for NAPT / PBA or DNAT), in the Network Address Translation >> Source Translation section

|CreateNAPT|

.. NOTE:: This lab will use the additional IP's assigned to the External interface as /32 to provide the NAPT pool (This is different to the old CGNAT standalone method)

Config should like similar to below

|SubNAPTConfig|

.. NOTE:: Exgress interface needs to be set and PAT Mode to the CGNAT algorithm required.

Address Translation Policy
~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Create Subscriber NAT Policy. In the example it is created for the entire Subscriber subnet (10.1.20.0/24) , a policy per subsciber will be created in a later lab.

|CreateNATPolicy|

This is the finished policy below:

|ExampleNATPolicy|

#. Now the policy is assigned in the Security section of the PEM VS created in Lab 1.

|AssignNATPolicy|

.. NOTE:: This needs to be done across all PEM VS, otherwise any VS without the flows will fail..

Quick Check to validate policy is assigned is to check the Security section SourceNAT policy, the VS context were NOT there in creation.

|CheckNATPolicy|


.. NOTE:: Quick check from here into the RDP of client 1 and run the network_script.sh. From here you should be able check via the browser.

|SimpleGiCheck|

.. |CreateNAPT| image:: /_static/CreateNAPT.png
    :scale: 100%

.. |SubNAPTConfig| image:: /_static/SubNAPTConfig.png
    :scale: 100%

.. |CreateNATPolicy| image:: /_static/CreateNATPolicy.png
    :scale: 45%

.. |ExampleNATPolicy| image:: /_static/ExampleNATPolicy.png
    :scale: 50%
   
.. |AssignNATPolicy| image:: /_static/AssignNATPolicy.png
    :scale: 50%

.. |CheckNATPolicy| image:: /_static/CheckNATPolicy.png
    :scale: 50%

.. |SimpleGiCheck| image:: /_static/SimpleGiCheck.png
    :scale: 50%