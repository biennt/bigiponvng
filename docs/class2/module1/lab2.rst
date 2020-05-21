.. |labmodule| replace:: 1
.. |labnum| replace:: 2
.. |labdot| replace:: |labmodule|\ .\ |labnum|
.. |labund| replace:: |labmodule|\ _\ |labnum|
.. |labname| replace:: Lab\ |labdot|
.. |labnameund| replace:: Lab\ |labund|

Lab |labmodule|\.\ |labnum|\: DNS
---------------------------------

DNS Pools
~~~~~~~~~

#. Create DNS Pools for external servers for DNS (Google in this case)

|CreateDNSPool|

DNS Cache
~~~~~~~~~

#. Create DNS Cache as Resolver

|CreateDNSCache|

.. NOTE:: Keep this as defaults, and resovler settings. For PRODUCTION use these will need to be tuned.

DNS Profile
~~~~~~~~~~~

#. Create DNS profile for the DNS listeners, reference the DNSCache created in previous step.

|CreateDNSProfile|

.. NOTE:: key component of this profile is the Cache enabled. This assists subscribers QoE and is an important feature we can use.

DNS Listeners
~~~~~~~~~~~~~

#. Create the listeners and configure the DNS profile, and pools created before.

|CreateDNSListener|

.. |CreateDNSCache| image:: /_static/CreateDNSCache.png
    :scale: 100%

.. |CreateDNSProfile| image:: /_static/CreateDNSProfile.png
    :scale: 100%

.. |CreateDNSPool| image:: /_static/CreateDNSPool.png
    :scale: 100%

.. |CreateDNSListener| image:: /_static/CreateDNSListener.png
    :scale: 100%
   