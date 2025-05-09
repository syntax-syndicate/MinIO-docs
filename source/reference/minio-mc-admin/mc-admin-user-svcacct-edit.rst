.. _minio-mc-admin-svcacct-edit:

==============================
``mc admin user svcacct edit``
==============================

.. default-domain:: minio

.. contents:: Table of Contents
   :local:
   :depth: 2

.. mc:: mc admin user svcacct edit

.. important::

   This command has been replaced and will be deprecated in a future MinIO Client release.

   As of MinIO Client RELEASE.2024-10-08T09-37-26Z, use the :mc:`mc admin accesskey edit` command to modify access keys for built-in MinIO IDP users.

   To modify access keys for AD/LDAP users, use the :mc:`mc idp ldap accesskey edit` command.

Syntax
------

.. start-mc-admin-svcacct-edit-desc

The :mc-cmd:`mc admin user svcacct edit` command modifies the configuration of an access key associated to the specified user.

.. end-mc-admin-svcacct-edit-desc

.. tab-set::

   .. tab-item:: EXAMPLE

      The following command applies a new policy and secret key to the ``myuserserviceaccount`` access key on the ``myminio`` deployment:

      .. code-block:: shell  
         :class: copyable 

         mc admin user svcacct edit                                             \  
                               --secret-key "myuserserviceaccountnewsecretkey"  \     
                               --policy "/path/to/new/policy.json"              \  
                               myminio myuserserviceaccount

   .. tab-item:: SYNTAX

      The command has the following syntax: 
  
      .. code-block:: shell  
         :class: copyable 

         mc [GLOBALFLAGS] admin user svcacct edit            \  
                                             [--secret-key]  \  
                                             [--policy]      \  
                                             ALIAS           \  
                                             SERVICEACCOUNT 

      .. include:: /includes/common-minio-mc.rst
         :start-after: start-minio-syntax
         :end-before: end-minio-syntax


Parameters
~~~~~~~~~~

.. mc-cmd:: ALIAS
   :required:

   The :mc-cmd:`alias <mc alias>` of the MinIO deployment.

.. mc-cmd:: SERVICEACCOUNT
   :required:

   The service account to modify.

.. mc-cmd:: --description
   :optional:

   .. versionadded:: RELEASE.2023-05-18T16-59-00Z

   Add a description for the service account.
   For example, you might specify the reason the service account exists.

.. mc-cmd:: --expiry
   :optional:

   .. versionadded:: RELEASE.2023-05-30T22-41-38Z

   Set an expiration date for the service account.
   The date must be in the future, you may not set an expiration date that has already passed.

   Allowed date and time formats:

   - ``2023-06-24``
   - ``2023-06-24T10:00``
   - ``2023-06-24T10:00:00``
   - ``2023-06-24T10:00:00Z``
   - ``2023-06-24T10:00:00-07:00``

.. mc-cmd:: --name
   :optional:

   .. versionadded:: RELEASE.2023-05-18T16-59-00Z

   Add a human-readable name for the service account.

.. mc-cmd:: --policy
   :optional:

   The path to a :ref:`policy document <minio-policy>` to attach to the new access key, with a maximum size of 2048 characters.
   The attached policy cannot grant access to any action or resource not explicitly allowed by the parent user's policies.

   The new policy overwrites any previously attached policy.

.. mc-cmd:: --secret-key
   :optional:

   The secret key to associate with the new access key.
   Overwrites the previous secret key.
   Applications using the access keys *must* update to use the new credentials to continue performing operations.


Global Flags
~~~~~~~~~~~~

.. include:: /includes/common-minio-mc.rst
   :start-after: start-minio-mc-globals
   :end-before: end-minio-mc-globals


Behavior
--------

S3 Compatibility
~~~~~~~~~~~~~~~~

.. include:: /includes/common-minio-mc.rst
   :start-after: start-minio-mc-s3-compatibility
   :end-before: end-minio-mc-s3-compatibility
