CLI Commands
============

oro:api:cache:clear
-------------------

This command command clears Data API cache.

Usually you need to run this command when you add a new entity to ``Resources/config/oro/api.yml`` or you add a new processor that changes a list of available through Data API resources.

.. code:: bash

    php bin/console oro:api:cache:clear

oro:api:doc:cache:clear
-----------------------

This command allows to clear or warm-up API documentation cache.

If this command is launched without parameters it warm-ups all API documentation caches:

.. code:: bash

    php bin/console oro:api:doc:cache:clear

Also you can use ``--no-warmup`` option if you need to clear the cache, but do not need to warm-up it:

.. code:: bash

    php bin/console oro:api:doc:cache:clear --no-warmup

To work only with the specified `API documentation views <https://github.com/nelmio/NelmioApiDocBundle/blob/master/Resources/doc/multiple-api-doc.rst>`__ use ``--view`` option:

.. code:: bash

    php bin/console oro:api:doc:cache:clear --view=rest_json_api

oro:api:dump
------------

This command shows all resources accessible through Data API.

Run this command without parameters to see all available resources:

.. code:: bash

    php bin/console oro:api:dump

or specify the ``request-type`` option if you need to know resources for a particular request type:

.. code:: bash

    php bin/console oro:api:dump --request-type=rest --request-type=json_api

Also the ``sub-resources`` option can be used to show all available sub-resources:

.. code:: bash

    php bin/console oro:api:dump --sub-resources

If you are interested in information about a concrete entity, you can specify entity class or entity alias as an argument:

.. code:: bash

    php bin/console oro:api:dump "Oro\Bundle\UserBundle\Entity\User" --sub-resources

or

.. code:: bash

    php bin/console oro:api:dump users --sub-resources

In additional you can use this command to get all entities that are not accessible through Data API. Use ``--not-accessible`` option for this:

.. code:: bash

    php bin/console oro:api:dump --not-accessible

oro:api:debug
-------------

This command shows details about registered Data API actions and processors.

If you want to know all actions run this command without parameters:

.. code:: bash

    php bin/console oro:api:debug

If you want to know which processors are registered for a particular action run this command with the action name as an argument:

.. code:: bash

    php bin/console oro:api:debug get_list

The ``request-type`` option can be used to see the processors which will be executed for a particular request type:

.. code:: bash

    php bin/console oro:api:debug get_list --request-type=rest --request-type=json_api

oro:api:config:dump
-------------------

This command shows configuration for a particular entity.

Run this command and specify entity class or entity alias as an argument:

.. code:: bash

    php bin/console oro:api:config:dump "Oro\Bundle\UserBundle\Entity\User"

or

.. code:: bash

    php bin/console oro:api:config:dump users

If you want to see the configuration that is used for a particular action you can use the ``action`` option (please note that the default value for this option is ``get``):

.. code:: bash

    php bin/console oro:api:config:dump users --action=update

To see the configuration for a particular request type you can use the ``request-type`` option:

.. code:: bash

    php bin/console oro:api:config:dump users --request-type=rest --request-type=json_api

The ``section`` option can be used to see a configuration of an entity when it is referenced by another entity:

.. code:: bash

    php bin/console oro:api:config:dump addresses --section=relations

By default no extra configuration data are added into output, but they can be added with the ``--extra`` option. The value for ``extra`` option can be: actions, definition, filters, sorters, descriptions or the full name of a class implements `ConfigExtraInterface <https://github.com/oroinc/platform/tree/master/src/Oro/Bundle/ApiBundle/Config/ConfigExtraInterface.php>`__, e.g.

.. code:: bash

    php bin/console oro:api:config:dump users --extra=filters --extra=sorters

to see human-readable representation of an entity and its fields

.. code:: bash

    php bin/console oro:api:config:dump users --extra=descriptions

or if a new extra section was added just pass the FQCN of a ConfigExtra

.. code:: bash

    php bin/console oro:api:config:dump users --extra="Acme\Bundle\AcmeBundle\Config\AcmeConfigExtra"

or it's also possible to pass multiple options

.. code:: bash

    php bin/console oro:api:config:dump users --extra=sorters --extra=descriptions --extra=filters --extra="Acme\Bundle\AcmeBundle\Config\AcmeConfigExtra"

oro:api:metadata:dump
---------------------

This command shows metadata for a particular entity.

To see metadata run this command and specify entity class or entity alias as an argument:

.. code:: bash

    php bin/console oro:api:metadata:dump "Oro\Bundle\UserBundle\Entity\User"

or

.. code:: bash

    php bin/console oro:api:metadata:dump users

If you want to see entity metadata that is used for a particular action you can use the ``action`` option (please note that the default value for this option is ``get``):

.. code:: bash

    php bin/console oro:api:metadata:dump users --action=update

If you want to see entity metadata that is used for a particular request type you can use the ``request-type`` option:

.. code:: bash

    php bin/console oro:api:metadata:dump users --request-type=rest --request-type=json_api

oro:api:config:dump-reference
-----------------------------

This command shows the structure of ``Resources/config/oro/api.yml``.

.. code:: bash

    php bin/console oro:api:config:dump-reference
