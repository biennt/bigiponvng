Welcome

Welcome to F5's SP Hands on Lab (PEM / DNS / CGNAT / AFM / Logging)

This documentation is in support of the UDF lab of the same name.

Overview SP GiLAN Consolidation
-------------------------------

- PEM+AFM+DNS+TrafficSteering
 - Links to content

- Use cases for Multi-Module
  - Mobile / Fixed / University

https://techdocs.f5.com/en-us/bigip-14-1-0/big-ip-policy-enforcement-manager-implementations-14-1-0.html

- Links to F5 Gi-LAN

- This Lab can be used to emulate lots of SP related use-cases. Some outlined below:
      - Video Optimisaiton
      - CGNAT+TCPOpt
      - Subscriber + Application Intelligent Traffic Steering

Getting Started
---------------

Please deploy and start the UDF Lab of the same name. The link for this documentation is in the documentation section of the UDF lab.

.. NOTE::


Prerequisites
-------------

In order to complete this series of training classes you will need to utilize
the provided blueprint for the course session.


UDF Blueprint
-------------

If this is delivered as part of a course, please follow the instructions provided by your lab instructor to access your
lab environment. The lab environment will be delivered  via UDF blueprints to
each student.

.. NOTE:: Please deploy and start your lab as soon as you have access to the class as the lab takes some time to boot all the components.


Lab Topology
------------

The Lab topology layout is shown below:

.. _lab-topology:

|lab_topo1|

The following table lists VLANS, IP Addresses and Credentials for all
components:

.. csv-table:: Lab Network Information
    :header: "Component", "VLAN", "IP Address", "Credentials"
    :widths: 40, 40, 40, 60

    "Linux Jumphost", "Mgmt", "10.1.1.20", ""
    "BIG-IP", "Mgmt", "10.1.1.4", "admin/MandoThis"
    "", "Internal", "10.1.10.5", ""
    "", "External", "10.1.20.5", ""
    "", "Control", "10.1.30.5", ""
    "Client 00", "Mgmt", "10.1.1.9", "udfclient/S3rv1ceP0weR"
    "", "Internal", "10.1.10.25", ""
    "Client 01", "Mgmt", "10.1.1.7", "udfclient/S3rv1ceP0weR"
    "", "Internal", "10.1.10.30", ""
    "ELK Stack", "Mgmt", "10.1.1.5", "ubuntu/default"
    "", "Control", "10.1.30.25", ""

Lab Validation
--------------

Check the F5 components for valid licenses and operation.

Update Admin Password for F5 if required
Article https://support.f5.com/csp/article/K3350


Check the Elasticsearch Host

1. Login via ssh or webshell.
2. Check the following commands screens to validate correct operations.
3. Restart the services as required if failures occur.

.. _EsCheck.png

|EsCheck|

Make sure Elasticsearch is now green

.. _EsStarted.png

|EsStarted|

Next is to confirm Kibana can communicate to ES now.

1.  Check status of Kibana
2.  Restart Kibana if needed
3.  Validate status again = green

.. _KibanaRestartCheck.png

|KibanaRestartCheck|

Once all is confirmed, the lab is ready to be completed.

.. |lab_topo1| image:: /_static/lab_topology.png
   :scale: 80%

.. |EsCheck| image:: /_static/EsCheck.png
    :scale: 100%

.. |EsStarted| image:: /_static/EsStarted.png
   :scale: 100%

.. |KibanaRestartCheck| image:: /_static/KibanaRestartCheck.png
   :scale: 100%