.. |labmodule| replace:: 1
.. |labnum| replace:: 1
.. |labdot| replace:: |labmodule|\ .\ |labnum|
.. |labund| replace:: |labmodule|\ _\ |labnum|
.. |labname| replace:: Lab\ |labdot|
.. |labnameund| replace:: Lab\ |labund|

Lab |labmodule|\.\ |labnum|\: Initial PEM Setup
-----------------------------------------------

Global PEM Policy
~~~~~~~~~~~~~~~~~

#. Set the Global PEM options.

|PemGlobalOptions|

#. Analytics Enabled
#. Leave External Log publisher blank (This will be used later in this Lab)
#. Enable all other settings

.. NOTE:: These are recommended settings for PoC. THe Terminate session on delete is important as its deletes the Subscriber flows when the sub is removed.


Data Plane Wizard
~~~~~~~~~~~~~~~~~

#. Create the Data plane listeners for PEM.

|DataPlaneWizard|

Click on the + symbol to craete the PEM data listeners for all protocols.

.. NOTE:: This will not use SNAT as there will be a source CGNAT provided by AFM in Lab3 of this module.

Fill out as per below

|DPListenerConfig|

#. Source and Destination all = 0.0.0.0/0
#. All Ports (TCP and UDP)
#. Only Enable on Internal VLAN

.. NOTE:: If you enable the listenders on all VLANs you will create subscribers on the Internet VLAN side as well. There is a profile change to stop this, but best practise is only enable on the Subscrbier VLANs.

Once Complete output should look like below:

|DataPlaneWizOutput|

#. Click into the Pem Profile created

|PemProfile|

.. NOTE:: Set Optimisations both Disabled and None, repectively. These settings are requried for production use, in a PoC or Lab most traffic will be optimisaed and not seen.


Policy and Rule Creation
~~~~~~~~~~~~~~~~~~~~~~~~

#. Create Unknown Subscriber Policy

|CreatePolicy|

#. Create Rule for Logging within the policy.

.. NOTE:: Precedence is reverse order, ie the larger the number the LOWER the Precedence.

.. NOTE:: Leave all Classification filters empty. This will Log all Unknown traffic. If any filter is selected then ONLY that traffic will log.

|LoggingRule|

Example Unknown Policy below with Multiple rules.

|ExampleUnknownPolicy|

#. Configure PEM Profile with the Unknown subsriber policy created. This can also be used as the default policy if unknown is not required.

|GlobalPolicy|

Using this as default Low Precedence Policy.

.. NOTE:: Typically Default policy for all subscribers will include all logging and some global blocking policies.

.. |PemGlobalOptions| image:: /_static/PemGlobalOptions.png
    :scale: 100%

.. |DataPlaneWizard| image:: /_static/DataPlaneWizard.png
    :scale: 100%

.. |DataPlaneWizOutput| image:: /_static/DataPlaneWizOutput.png
    :scale: 100%

.. |DPListenerConfig| image:: /_static/DPListenerConfig.png
    :scale: 100%

.. |PemProfile| image:: /_static/PemProfile.png
    :scale: 100%

.. |CreatePolicy| image:: /_static/CreatePolicy.png
    :scale: 100%

.. |LoggingRule| image:: /_static/LoggingRule.png
    :scale: 100%

.. |ExampleUnknownPolicy| image:: /_static/ExampleUnknownPolicy.png
    :scale: 45%

.. |GlobalPolicy| image:: /_static/GlobalPolicy.png
    :scale: 45%