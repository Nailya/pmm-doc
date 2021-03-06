--------------------------------------------------------------------------------
Adding a ProxySQL host
--------------------------------------------------------------------------------

.. _pmm-admin.add-proxysql-metrics:

`Adding ProxySQL metrics service <client-proxysql-metrics.html#pmm-admin-add-proxysql-metrics>`_
=================================================================================================

Use the |opt.proxysql-metrics| alias 
to enable |proxysql| performance metrics monitoring.

.. _pmm-admin.add-proxysql-metrics.usage:

.. rubric:: USAGE

.. _code.pmm-admin.add-proxysql-metrics:

.. include:: ../.res/code/pmm-admin.add.proxysql-metrics.txt

where username and password are credentials for the monitored MongoDB access,
which will be used locally on the database host. Additionally, two positional
arguments can be appended to the command line flags: a service name to be used
by PMM, and a service address. If not specified, they are substituted
automatically as ``<node>-proxysql`` and ``127.0.0.1:3306``.

The output of this command may look as follows:

  .. code-block:: bash

     # pmm-admin add proxysql --username=admin --password=admin
     ProxySQL Service added.
     Service ID  : /service_id/f69df379-6584-4db5-a896-f35ae8c97573
     Service name: ubuntu-proxysql

Beside positional arguments shown above you can specify service name and
service address with the following flags: ``--service-name``, ``--host`` (the
hostname or IP address of the service), and ``--port`` (the port number of the
service). If both flag and positional argument are present, flag gains higher
priority. Here is the previous example modified to use these flags::

     pmm-admin add proxysql --username=pmm --password=pmm --service-name=my-new-proxysql --host=127.0.0.1 --port=3306 

.. only:: showhidden

	.. _pmm-admin.add-proxysql-metrics.options:

	.. rubric:: OPTIONS

	The following option can be used with the |opt.proxysql-metrics| alias:

	|opt.dsn|
	  Specify the ProxySQL connection DSN.
	  By default, it is ``stats:stats@tcp(localhost:6032)/``.
	
	You can also use
	:ref:`global options that apply to any other command
	<pmm-admin.options>`,
	as well as
	:ref:`options that apply to adding services in general
	<pmm-admin.add-options>`.

	For more information, run
	|pmm-admin.add|
	|opt.proxysql-metrics|
	|opt.help|.

	.. seealso::

	   Default ports
	      :ref:`Ports <Ports>` in :ref:`pmm.glossary-terminology-reference`


.. include:: ../.res/replace.txt
