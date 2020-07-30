======
cinder
======

.. _cinder_16.0.0.0rc1-107:

16.0.0.0rc1-107
===============

.. _cinder_16.0.0.0rc1-107_New Features:

New Features
------------

.. releasenotes/notes/1884495-173f375dc5274fe6.yaml @ b'c354d5bd04537f7efa6fae2eacf8980cc02bef5f'

- Nimble driver now supports discard.

.. releasenotes/notes/SC-included_domain_ips_ListOpt-61bacddee199ce83.yaml @ b'8a997d88ae2b3c1a925ecd107c50fc3122e05029'

- Added an ``included_domain_ips`` option to the Dell EMC SC driver. This option takes a comma separated list of target IP addresses listed under the fault domains to whitelisted. This option only applies to the ISCSI driver.

.. releasenotes/notes/bp-nfs-volume-encryption-3d8362843caeb39c.yaml @ b'44c7da9a44cc235b514e1b714cc7882683a8491d'

- The NFS driver now supports the creation of encrypted volumes.

.. releasenotes/notes/bp-powerstore-cinder-driver-94f8c7f1371eafe7.yaml @ b'517cb6448b613b888476f5da75ae4ad28f60f744'

- Add Dell EMC PowerStore Storage Driver (iSCSI, FC).

.. releasenotes/notes/healthcheck-449ed4292e6bfa22.yaml @ b'696ef12f4e67582b8345f7ae97b6df550436662d'

- The oslo.middleware /healthcheck is now activated by default in the Cinder
  api-paste.ini. Operators can use it to configure HAproxy or the monitoring
  of Cinder APIs. Edit the ``api-paste.ini`` file and remove any healthcheck
  entries to disable this functionality.

.. releasenotes/notes/hitachi-storage-driver-d38dbd990730388d.yaml @ b'8aaf6a68b38580e26c12ff759ee687a2688b99e4'

- New Cinder Hitachi driver based on REST API for Hitachi VSP storages.

.. releasenotes/notes/pure-storage-revert-snapshot-b7e0ec4f958418c4.yaml @ b'8116de89ea8cc410150b3b9006aaa8d7b0a365fd'

- Add reverting to snapshot support in Pure Storage Cinder driver.


.. _cinder_16.0.0.0rc1-107_Upgrade Notes:

Upgrade Notes
-------------

.. releasenotes/notes/bug-1823200-victoria-ecd2d99c9223d84b.yaml @ b'b2c9592281b24824c2158f91a9295288f41dd81a'

- The fix for `Bug #1823200
  <https://bugs.launchpad.net/cinder/+bug/1823200>`_ requires
  ``os-brick`` version 3.1.0 or greater.

.. releasenotes/notes/fix-host-info-in-volume-details-1759280bd236421e.yaml @ b'9d5c340130ac056e7558468cc61872db65140c9b'

- Due to the fix for `Bug #1740950
  <https://bugs.launchpad.net/cinder/+bug/1740950>`_, the
  ``host_name`` field in any object in the ``attachments``
  array of the volume detail response is populated only when
  the call is made in an administrative context.  Otherwise,
  its value is the JSON ``null`` value.  This is consistent with
  prior API behavior, as it has always been possible for the
  value of that field to be ``null``.

.. releasenotes/notes/ibm-storwize-removehostmappings-e7eeaf898786c6bf.yaml @ b'bdb9e0c5f1a4882960fd1950d4157b0fcb6d2001'

- IBM Spectrum Virtualize Family (previously known as Storwize) driver
  cannot delete volume which has host mapping in some rare cases while
  code_level of IBM Spectrum Virtualize Family storage lower than
  7.7.0.0. Please upgrade to latest code to avoid this kind of issue.


.. _cinder_16.0.0.0rc1-107_Security Issues:

Security Issues
---------------

.. releasenotes/notes/bug-1823200-victoria-ecd2d99c9223d84b.yaml @ b'b2c9592281b24824c2158f91a9295288f41dd81a'

- Dell EMC VxFlex OS driver: This release contains a fix for
  `Bug #1823200 <https://bugs.launchpad.net/cinder/+bug/1823200>`_.
  See `OSSN-0086 <https://wiki.openstack.org/wiki/OSSN/OSSN-0086>`_
  for details.

.. releasenotes/notes/fix-host-info-in-volume-details-1759280bd236421e.yaml @ b'9d5c340130ac056e7558468cc61872db65140c9b'

- It was possible under certain circumstances for the host name
  of an instance to be leaked in the volume detail response.  This
  has been fixed in the current release.  The ``host_name`` field
  in any object in the ``attachments`` array of the volume
  detail response is populated only when the call is made in an
  administrative context.  Otherwise, its value is the JSON ``null``
  value.


.. _cinder_16.0.0.0rc1-107_Bug Fixes:

Bug Fixes
---------

.. releasenotes/notes/bug-1823200-victoria-ecd2d99c9223d84b.yaml @ b'b2c9592281b24824c2158f91a9295288f41dd81a'

- `Bug #1823200 <https://bugs.launchpad.net/cinder/+bug/1823200>`_:
  This release contains an updated Dell EMC VxFlex OS driver.  It must
  be used with ``os-brick`` version 3.1.0 or greater and requires that
  a new configuration file be deployed on compute nodes, cinder nodes,
  and anywhere you would perform a volume attachment in your deployment.
  See the `Dell EMC VxFlex OS (ScaleIO) Storage driver
  <https://docs.openstack.org/cinder/latest/configuration/block-storage/drivers/dell-emc-vxflex-driver.html>`_
  documentation for details about the configuration file, and see
  `OSSN-0086 <https://wiki.openstack.org/wiki/OSSN/OSSN-0086>`_ for
  more information about the security vulnerability.

.. releasenotes/notes/bug-1828386-fix-retype-rbd-backend.yaml @ b'0d22547fd246be4b09536c2da633af421e9c7df0'

- Fix the bug that a volume retyped from
  other volume type to replicated or
  multiattach type cannot be enabled replicated
  or multiattach in rbd driver. (Bug #1828386)

.. releasenotes/notes/bug-1859652-netapp-fix-retype-attached-volume-to-solidfire-1933f03673ff078d.yaml @ b'ca475a3dad993624920d2bcbe65bf98162f32e2f'

- Fixed `bug #1859652 <https://bugs.launchpad.net/cinder/+bug/1859652>`_
  to allow retyping an attached volume to SolidFire.

.. releasenotes/notes/bug-1869746-cross-project-incremental-backup-error.yaml @ b'8ebeafcbbafb700052f3abfc1f7ba004269a92e8'

- Cinder no longer allows an incremental backup to be
  created while having the parent backup in another
  project.

.. releasenotes/notes/bug-1874134-netapp-ONTAP-fix-max-resize-size-ad2d88da8721560e.yaml @ b'510613e135b639776246d46c3d7977208d0fbfd8'

- Fix bug `#1874134 <https://bugs.launchpad.net/cinder/+bug/1874134>`_,
  allowing an iSCSI or FCP volume to be extended to a size up to 16TB
  regardless of its original size, even if it's attached to an instance.

.. releasenotes/notes/bug-1875570-nfs-image-volume-cache-c45e840a6ec2a702.yaml @ b'f690327b55cac79540c9bb7b10c390b73aa3fc62'

- `Bug #1875570 <https://bugs.launchpad.net/cinder/+bug/1875570>`_:
  Fixed issue with NFS backend where the image-volume cache was
  never used to create a volume, even when the cache was enabled.

.. releasenotes/notes/bug-1879578-volume_type-regression-de82f4152c7b2f77.yaml @ b'674c8e7286999bb6408291de1dc6395aac2b04b1'

- `Bug #1879578 <https://bugs.launchpad.net/cinder/+bug/1879578>`_:
  A regression in the Train release caused Cinder to assign the default
  volume type too aggressively when a volume type was not specified in
  a volume-create request.  As a result, some alternative methods of
  specifying the volume type were ignored and the default type (either
  configured by the operator or the system default) would be assigned.
  
  This release restores the intended behavior, which is described as
  follows:
  
  If a ``volume_type`` is not specified when a volume is created, Cinder
  tries to infer the volume type from other information in the
  volume-create request:
  
  * if a ``source_volid`` is supplied in the request, the volume type
    is inferred from the source volume's volume type
  * if a ``snapshot_id`` is supplied in the request, the volume type
    is inferred from the volume type associated with the snapshot
  * if an ``imageRef`` is supplied in the request, and the image has
    a ``cinder_img_volume_type`` image property, the volume type is
    inferred from the value of that image property
  
  Otherwise, the volume type is the default volume type configured by
  the operator, and if no volume type is so configured, the volume type
  is the system default volume type, namely, ``__DEFAULT__``.
  
  When a volume type is specified explicitly in a volume-create call, Cinder
  will use the specified type.  If the specified type cannot be assigned due
  to a conflict with other parameters in the volume-create call, however, the
  call will result in a 400 (Bad Request) response.

.. releasenotes/notes/bug-1886222-nfs-snapshot-82b5519175c48a6f.yaml @ b'11b5c9d97bd69f9e8b5db0d32bfe257063170155'

- `Bug #1886222 <https://bugs.launchpad.net/cinder/+bug/1886222>`_:
  Fixed an issue with creating a snapshot on an NFS backend
  if the snapshot name is not specified.

.. releasenotes/notes/cleanup-rbd-temp-file-during-convert-fail-3848e9dbe7e15fc6.yaml @ b'7c95f3969f4c0df5f818f96cb662dddc17a8dd6f'

- `Bug #1873738 <https://bugs.launchpad.net/cinder/+bug/1873738>`_: RBD Driver:
  Added cleanup for residue destination file if the copy image to encrypted volume
  operation fails.

.. releasenotes/notes/fix-3par-live-migration-0065bd2626fdb4a1.yaml @ b'fc51678298a38dcd94bcfe92c590b38fdb7193e4'

- Fix HPE 3PAR driver issue where volumes that were live migrated to it would
  end up being inaccessible.  We would no longer be able to use the volume
  for any operation, such as attach, detach, delete, snapshot, etc.
  (bug 1697422)

.. releasenotes/notes/fix-3par-migrate-rename-662d984e070a1de2.yaml @ b'd8062063a35ab2307edbe36826f350f2767ea08d'

- Fix the HPE 3PAR driver's attempt to rename the backend volume after
  it was migrated. If the original volume resides on the same 3PAR backend
  then the pre and post migration volume names are swapped. Otherwise, the
  newly migrated volume is renamed to match the original name.
  (bug 1858119)

.. releasenotes/notes/fix-host-info-in-volume-details-1759280bd236421e.yaml @ b'9d5c340130ac056e7558468cc61872db65140c9b'

- `Bug #1740950 <https://bugs.launchpad.net/cinder/+bug/1740950>`_:
  the ``host_name`` field in any object in the ``attachments`` array
  of the volume detail response is populated only when the call is
  made in an administrative context.  Otherwise, its value is the
  JSON ``null`` value.

.. releasenotes/notes/fix-kaminario-unique_fqdn_network-ecde36f614c30733.yaml @ b'53504f82a53146151935e6aac301a41e2b387623'

- Fix ``unique_fqdn_network`` configuration option for the Kaminario driver,
  as it was being ignored when defined in the driver section, which used to
  work.
  (Bug #1886042).

.. releasenotes/notes/netapp-ontap-fix-detach-multiattach-d99d33dff2fefb4c.yaml @ b'e27d83f4d03a89d982aebbb3fb8a8d1adafbdfc5'

- NetApp ONTAP: Fixes `bug 1839384
  <https://bugs.launchpad.net/cinder/+bug/1839384>`__ Detaching any instance
  from multiattached volume terminates connection. Now the connection is
  terminated only if there're no other instances using the same initiator.

.. releasenotes/notes/powermax-bug-1875478-8c9072ad9a87b83d.yaml @ b'03f5dce3329f2ec3b3fa49b9ad68ffa1d1f27eb9'

- PowerMax Driver - Concurrent live migrations can sometimes fail when one
  thread deletes a storage group that another thread may need.


.. _cinder_16.0.0.0rc1-107_Other Notes:

Other Notes
-----------

.. releasenotes/notes/powermax-91-to-92-endpoints-bb467c8aca0165dd.yaml @ b'd592b2ad0d4eeab2fbbf25427d63b80fd0c5d72b'

- PowerMax driver - the minimum version of Unisphere for PowerMax required
  for Victoria is 9.2, so all the latest 92 REST endpoints will be used.

