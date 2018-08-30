======
cinder
======

.. _cinder_13.0.0.0rc2:

13.0.0.0rc2
===========

.. _cinder_13.0.0.0rc2_Security Issues:

Security Issues
---------------

.. releasenotes/notes/bug-1784871-7f67402eb13abca7.yaml @ b'3a39d09166bf6d1c7d2bae63caf3e2a954328862'

- Removed the ability to create volumes in a ScaleIO Storage Pool
  that has zero-padding disabled.
  A new configuration option had been added to override this new
  behavior and allow volume creation, but should not be enabled if
  multiple tenants will utilize volumes from a shared Storage Pool.

