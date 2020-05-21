.. |labmodule| replace:: 1
.. |labnum| replace:: 1
.. |labdot| replace:: |labmodule|\ .\ |labnum|
.. |labund| replace:: |labmodule|\ _\ |labnum|
.. |labname| replace:: Lab\ |labdot|
.. |labnameund| replace:: Lab\ |labund|

Lab |labmodule|\.\ |labnum|\: Provision and Base Setup
-------------------------------------------------------

Configuration of the following items in order:

#. Checked Provisioned Modules refelcts the below image (DNS / PEM / AFM and AVR).

|prov_image|

.. NOTE:: CGNAT is NOT provisioned in this case as it is now part of AFM. This provisioning is for CGNAT standalone.

#. Create Vlans. 

|VlanCreationExternal|

.. NOTE:: Use advanced settings and set External to Destination DAG. This pins return traffic back from Internet to the correct TMM

|VlanCreationInternal|

.. NOTE:: Use advanced settings and set Internal to Source DAG. This pins traffic flows to the correct TMM per subscriber

|VlanCreationControl|

.. NOTE:: Use advanced settings and set Control to Default DAG. Default DAG is required for any control plane services (DHCP/RADIUS/Gx/Gy to function correctly.)

#. Create SELF-IP's as per table below:

.. csv-table:: Self IP Network Information
    :header: "VLAN", "IP Address", "Mask"
    :widths: 40, 40, 40

    "Internal", "10.1.10.5", "255.255.255.0"
    "External", "10.1.20.5", "255.255.255.0"
    "Control", "10.1.30.5", "255.255.255.0"

|self_ip|


#. Create Default route as per table below:

.. csv-table:: IP Route Network Information
    :header: "Destination", "IP Address"
    :widths: 40, 40

    "Default", "10.1.20.1"

|routes|

#. Setup Logging Profiles.

The logging uses a cascading approach:

    Log publisher
        |
        ------------>> Format Log (Splunk)
                            |   
                            --------------->> HSL Destination
                                                    |
                                                    ---------->> Logging Pool

So we work backwards to achieve this starting at the Logging Pools

#.  Create Logging Pools for each of the functions, in this case PEM , DNS , and AFM

|LoggingPoolCreation|

with the following Node Members

.. csv-table:: Logging Pool Information
    :header: "Node IP", "Port", "Function"
    :widths: 40, 40, 40

    "10.1.30.25", "5514", "PEM"
    "10.1.30.25", "5515", "DNS"
    "10.1.30.25", "5516", "AFM"

Create System Log Destinations for HSL 

|HSLLogDest|

Do this for each of the Pools created before DNS and AFM.

Now create the Format Destination for each HSL (Splunk format)

.. NOTE:: ELK can use Splunk formats for HSL

|HSLLogDest|

All Destinations created. Now create the publishers

|ElkPub|

.. NOTE:: Make sure to select the format destination (HSL destination will work, without formatting for ELK)

Create all three module publishers, these will be used later for logging externally.

|ElkAllPub|

.. |prov_image| image:: /_static/prov_image.png
    :scale: 45%

.. |VlanCreationExternal| image:: /_static/VlanCreationExternal.png
    :scale: 100%

.. |VlanCreationInternal| image:: /_static/VlanCreationInternal.png
    :scale: 100%

.. |VlanCreationControl| image:: /_static/VlanCreationControl.png
    :scale: 100%

.. |self_ip| image:: /_static/self_ip.png
    :scale: 45%

.. |routes| image:: /_static/routes.png
    :scale: 45%

.. |LoggingPoolCreation| image:: /_static/LoggingPoolCreation.png
    :scale: 100%

.. |HSLLogDest| image:: /_static/HSLLogDest.png
    :scale: 100%

.. |ElkPub| image:: /_static/ElkPub.png
    :scale: 100%

.. |ElkAllPub| image:: /_static/ElkAllPub.png
    :scale: 100%

