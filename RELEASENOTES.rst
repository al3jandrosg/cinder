======
cinder
======

.. _cinder_16.0.0.0rc1-158:

16.0.0.0rc1-158
===============

.. _cinder_16.0.0.0rc1-158_New Features:

New Features
------------

.. releasenotes/notes/1884495-173f375dc5274fe6.yaml @ b'c354d5bd04537f7efa6fae2eacf8980cc02bef5f'

- Nimble driver now supports discard.

.. releasenotes/notes/1885946-17bc5c3dc0535044.yaml @ b'437a9674ec7cec160c7a93229bfb40ac461395d1'

- Add Multi-attach feature in Nimble driver.

.. releasenotes/notes/SC-included_domain_ips_ListOpt-61bacddee199ce83.yaml @ b'8a997d88ae2b3c1a925ecd107c50fc3122e05029'

- Added an ``included_domain_ips`` option to the Dell EMC SC driver. This option takes a comma separated list of target IP addresses listed under the fault domains to whitelisted. This option only applies to the ISCSI driver.

.. releasenotes/notes/add-cluster-name-to-volume-details-ce01dd828faafcde.yaml @ b'c5e15b38693a27a6ec510107027f3b52839bffc3'

- Added new APIs on microversion 3.61  to show ``cluster_name`` attribute in
  the response body of volume details for admin.

.. releasenotes/notes/backup_max_operations-27753c748ba1dc1a.yaml @ b'30c2289c9b0456d3783f01e3d65985ed1b09976a'

- We can now limit the number of concurrent backup/restore operations that a
  Cinder backup service can perform using the ``backup_max_operations``
  configuration option.

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

.. releasenotes/notes/powermax-auto-migration-5cc57773c23fef02.yaml @ b'197e024747ca04daeb35a9eaa9f1350089211ea3'

- This PowerMax driver moves the legacy shared volume from the masking
  view structure in Ocata and prior releases (when SMI-S was supported) to
  staging masking view(s) in Pike and later releases (U4P REST).
  In Ocata, the live migration process shared the storage group,
  containing the volume, among the different compute nodes. In Pike,
  we changed the masking view structure to facilitate a cleaner live
  migration process where only the intended volume is migrated without
  exposing other volumes in the storage group. The staging storage group
  and masking views facilitate a seamless live migration operation in
  upgraded releases.

.. releasenotes/notes/powermax-failover-abilities-1fa0a23128f1c00b.yaml @ b'1a4ec30e0be996a218132a4396c33fe936aa3fbb'

- PowerMax for Cinder driver now supports the ability to transition to a
  new primary array as part of the failover process if the existing
  primary array is deemed unrecoverable.

.. releasenotes/notes/powermax-load-balance-9cd152e53ecb34fd.yaml @ b'55042c357e16ccba4fd4084b5c47f05bc2300bc0'

- PowerMax for Cinder driver now supports Port Group and Port load
  balancing when attaching Nova Compute instances to volumes on the
  backend PowerMax.

.. releasenotes/notes/pure-storage-revert-snapshot-b7e0ec4f958418c4.yaml @ b'8116de89ea8cc410150b3b9006aaa8d7b0a365fd'

- Add reverting to snapshot support in Pure Storage Cinder driver.

.. releasenotes/notes/support-modern-compression-9984f77bb12e97e0.yaml @ b'6527ab9aeb39d1a741cb8a5e0954f23c945ff348'

- Added support to cinder backup for use of the Zstandard compression
  algorithm.  To use it, set the ``backup_compression_algorithm`` to
  ``zstd`` in the cinder configuration file.  (The default value for
  this option is ``zlib``.)


.. _cinder_16.0.0.0rc1-158_Upgrade Notes:

Upgrade Notes
-------------

.. releasenotes/notes/1885946-17bc5c3dc0535044.yaml @ b'437a9674ec7cec160c7a93229bfb40ac461395d1'

- Nimble specific extra-spec nimble:multi-initiator is removed.
  Common extra-spec multiattach is added.

.. releasenotes/notes/allow-deleting-__DEFAULT__-type-d35dfb5d89760b9b.yaml @ b'e5d842eb1be8026451edeb16e849b53b3bf6ef7a'

- The ``default_volume_type`` configuration option is now required
  to have a value.  The default value is ``__DEFAULT__``, so you
  should see no change in behavior whether or not you have set a
  value for ``default_volume_type``.  See
  `Bug #1886632 <https://bugs.launchpad.net/cinder/+bug/1886632>`_
  for more information about this change.

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

.. releasenotes/notes/increase_glance_num_retries-66b455a0729c4535.yaml @ b'da5a27f7b38708ea7e4e8877a1f247833224a518'

- The default value of the configuration option, ``glance_num_retries``,
  has been changed to 3 in this release. Its former value was 0.
  The option controls how many times to retry a Glance API call
  in response to a HTTP connection failure, timeout or ServiceUnavailable status.
  By this change, Cinder can be more resilient to temporary failure and continue
  the request if a retry succeeds.

.. releasenotes/notes/remove-cinder-manage-shell-6d6f42e5a4ee8c5c.yaml @ b'e89dfb0eab9f19a9d305fd35e8e1d1a3d193ced3'

- The "cinder-manage shell" set of commands has been removed.

.. releasenotes/notes/remove-rbd_keyring_conf-2d54a4de634c255c.yaml @ b'2aef694a87c6c038a50b2562a29aece3d7064f85'

- RBD driver: the ``rbd_keyring_conf`` configuration option, which
  was deprecated in the Ussuri release, has been removed.  If it is
  present in a configuration file, its value will silently be
  ignored.  For more information, see `OSSN-0085
  <https://wiki.openstack.org/wiki/OSSN/OSSN-0085>`_:
  Cinder configuration option can leak secret key from Ceph backend.

.. releasenotes/notes/vxflexos-powerflex-rebrand-37dfe2b82d35b6a2.yaml @ b'db4c1ec55a5dd46a133833bc5377ea3e9f714716'

- Dell EMC VxFlex OS has been rebranded to PowerFlex. The driver
  ``cinder.volume.drivers.dell_emc.vxflexos.driver.VxFlexOSDriver``
  has been renamed to
  ``cinder.volume.drivers.dell_emc.powerflex.driver.PowerFlexDriver``.
  Although in this release the volume manager will recognize the old
  driver name, that functionality will be removed in the Wallaby
  release, and thus we recommend that you update the driver name in
  ``cinder.conf`` at your earliest convenience.
  
  Existing vxFlex OS configuration options will continue to work in this
  release, but this functionality will be removed in the Wallaby release.
  Thus all driver configuration options that start with ``vxflexos``
  should be updated to ``powerflex`` in your ``cinder.conf`` as soon
  as possible.
  
  Before the Rocky release, this driver was named
  ``cinder.volume.drivers.dell_emc.scaleio.driver.ScaleIODriver``.
  That name was deprecated in the Rocky release.  In this release,
  the pre-Rocky name for this driver is no longer recognized and
  support for configuration options beginning with ``sio`` has been
  removed.
  
  The online documentation has been updated to reflect these changes.


.. _cinder_16.0.0.0rc1-158_Deprecation Notes:

Deprecation Notes
-----------------

.. releasenotes/notes/deprecate-tsm-backup-driver-8be0c78ec1a9d6dc.yaml @ b'e6795b8906854f2e39492dede6fb2a595917612b'

- Cinder TSM Backup Driver is deprecated and will be removed in Wallaby
  release.


.. _cinder_16.0.0.0rc1-158_Security Issues:

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


.. _cinder_16.0.0.0rc1-158_Bug Fixes:

Bug Fixes
---------

.. releasenotes/notes/allow-deleting-__DEFAULT__-type-d35dfb5d89760b9b.yaml @ b'e5d842eb1be8026451edeb16e849b53b3bf6ef7a'

- `Bug #1886632 <https://bugs.launchpad.net/cinder/+bug/1886632>`_:
  The system defined ``__DEFAULT__`` volume type is now treated as
  a regular volume-type and may be updated or deleted.  Since the
  configured ``default_volume_type`` cannot be deleted, however,
  the ``__DEFAULT__`` volume type may not be deleted if it is the
  value of that configuration option.

.. releasenotes/notes/brocade_looup_fail_get_client-179151d449a34aa4.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1888550 <https://bugs.launchpad.net/cinder/+bug/1888550>`_:
  Fix `UnboundLocalError` on the Brocade lookup driver on southbound client
  creation failure during the device mapping retrieval.

.. releasenotes/notes/brocade_py3-15647dbe3981d44b.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1888548 <https://bugs.launchpad.net/cinder/+bug/1888548>`_:
  Add Python 3 support to the Brocade Zone Manager driver.

.. releasenotes/notes/brocade_rest_client-202cfd474c96d3fe.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1866860 <https://bugs.launchpad.net/cinder/+bug/1866860>`_:
  Fix `AttributeError` on the Brocade ZM driver when using setting REST_HTTP
  or REST_HTTPS as the fc_southbound_protocol option and an exception is
  raised by the client.

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

.. releasenotes/notes/bug-1828386-fix-retype-rbd-backend.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1828386 <https://bugs.launchpad.net/cinder/+bug/1828386>`_:
  Fix the bug that a volume retyped from
  another volume type to a replicated or
  multiattach type cannot have replication
  or multiattach enabled in rbd driver.

.. releasenotes/notes/bug-1859652-netapp-fix-retype-attached-volume-to-solidfire-1933f03673ff078d.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1859652 <https://bugs.launchpad.net/cinder/+bug/1859652>`_:
  Fix to allow retyping an attached volume to SolidFire.

.. releasenotes/notes/bug-1869746-cross-project-incremental-backup-error.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1869746 <https://bugs.launchpad.net/cinder/+bug/1869746>`_:
  Cinder no longer allows an incremental backup to be
  created while having the parent backup in another
  project.

.. releasenotes/notes/bug-1874134-netapp-ONTAP-fix-max-resize-size-ad2d88da8721560e.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1874134 <https://bugs.launchpad.net/cinder/+bug/1874134>`_:
  Fix for NetApp ONTAP driver allowing an iSCSI or FCP volume to be
  extended to a size up to 16TB regardless of its original size, even
  if it's attached to an instance.

.. releasenotes/notes/bug-1874541-netapp-fix-update-cluster-status-8331655904fb4fed.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1874541 <https://bugs.launchpad.net/cinder/+bug/1874541>`_:
  Fix a ZeroDivisionError when the SolidFire driver tried
  to update cluster capabilities.

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

.. releasenotes/notes/cleanup-rbd-temp-file-during-convert-fail-3848e9dbe7e15fc6.yaml @ b'7c95f3969f4c0df5f818f96cb662dddc17a8dd6f'

- `Bug #1873738 <https://bugs.launchpad.net/cinder/+bug/1873738>`_: RBD Driver:
  Added cleanup for residue destination file if the copy image to encrypted volume
  operation fails.

.. releasenotes/notes/fix-3par-live-migration-0065bd2626fdb4a1.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1697422 <https://bugs.launchpad.net/cinder/+bug/1697422>`_:
  Fix HPE 3PAR driver issue where volumes that were live migrated to it would
  end up being inaccessible.  We would no longer be able to use the volume
  for any operation, such as attach, detach, delete, snapshot, etc.

.. releasenotes/notes/fix-3par-migrate-rename-662d984e070a1de2.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1858119 <https://bugs.launchpad.net/cinder/+bug/1858119>`_:
  Fix the HPE 3PAR driver's attempt to rename the backend volume after
  it was migrated. If the original volume resides on the same 3PAR backend
  then the pre and post migration volume names are swapped. Otherwise, the
  newly migrated volume is renamed to match the original name.

.. releasenotes/notes/fix-groups-actions-in-a-a-mode-5d554b30a26da22c.yaml @ b'7d211d6221ec17544984f0c33e11c3428e50aa3b'

- Fixed volume group action in Active/Active HA deployment:
  
  * Update group
    (`#1876133 <https://bugs.launchpad.net/cinder/+bug/1876133>`_)
  
  * Create group from group snapshot
    (`#1867906 <https://bugs.launchpad.net/cinder/+bug/1867906>`_)

.. releasenotes/notes/fix-host-info-in-volume-details-1759280bd236421e.yaml @ b'9d5c340130ac056e7558468cc61872db65140c9b'

- `Bug #1740950 <https://bugs.launchpad.net/cinder/+bug/1740950>`_:
  the ``host_name`` field in any object in the ``attachments`` array
  of the volume detail response is populated only when the call is
  made in an administrative context.  Otherwise, its value is the
  JSON ``null`` value.

.. releasenotes/notes/fix-kaminario-unique_fqdn_network-ecde36f614c30733.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1886042 <https://bugs.launchpad.net/cinder/+bug/1886042>`_:
  Fix ``unique_fqdn_network`` configuration option for the Kaminario driver,
  as it was being ignored when defined in the driver section, which used to
  work.

.. releasenotes/notes/fix-leave-mapped-volume-ef0bd683d415f7b1.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1880971 <https://bugs.launchpad.net/cinder/+bug/1880971>`_:
  Fix leaving mapped volumes on offline volume migration and revert to
  snapshot operations failure.

.. releasenotes/notes/fix-show-transfer-for-non-admins-be001d79975b325d.yaml @ b'1f733cdf2dcf014b4391ebd733693d3cbcb1f848'

- `Bug #1884268 <https://bugs.launchpad.net/cinder/+bug/1884268>`_:
  Fixed issue where non-admin users could not show a volume transfer by name.

.. releasenotes/notes/netapp-ontap-fix-detach-multiattach-d99d33dff2fefb4c.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1839384 <https://bugs.launchpad.net/cinder/+bug/1839384>`_:
  NetApp ONTAP: Detaching any instance
  from multiattached volume terminates connection. Now the connection is
  terminated only if there're no other instances using the same initiator.

.. releasenotes/notes/powermax-bug-1875478-8c9072ad9a87b83d.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1875478 <https://bugs.launchpad.net/cinder/+bug/1875478>`_:
  PowerMax Driver - Concurrent live migrations can sometimes fail when one
  thread deletes a storage group that another thread may need.

.. releasenotes/notes/revert-snapshot-non-admin-8485be55060eab0d.yaml @ b'e0498078373376c08d99801be3b3f852b0de4f2f'

- `Bug #1889758 <https://bugs.launchpad.net/cinder/+bug/1889758>`_:
  Fix revert to snapshot not working for non admin users when using the
  snapshot's name.


.. _cinder_16.0.0.0rc1-158_Other Notes:

Other Notes
-----------

.. releasenotes/notes/allow-deleting-__DEFAULT__-type-d35dfb5d89760b9b.yaml @ b'e5d842eb1be8026451edeb16e849b53b3bf6ef7a'

- Beginning with the Train release, untyped volumes (that is, volumes with
  no volume-type) have been disallowed.  To facilitate this, a
  ``__DEFAULT__`` volume-type was included as part of the Train database
  migration.  In this release, handling of the default volume-type has been
  improved:
  
  * The ``default_volume_type`` configuration option is required to have a
    value.  The default value is ``__DEFAULT__``.
  * A request to delete the currently configured ``default_volume_type``
    will fail.  (You can delete that volume-type, but you cannot do it
    while it is the value of the configuration option.)
  * There must always be at least one volume-type defined in a Cinder
    installation.  This is enforced by the type-delete call.
  * If the ``default_volume_type`` is misconfigured (that is, if the value
    refers to a non-existent volume-type), requests that rely on the
    default volume-type (for example, a volume-create request that does
    not specify a volume-type) will result in a HTTP 500 response.

.. releasenotes/notes/powermax-91-to-92-endpoints-bb467c8aca0165dd.yaml @ b'd592b2ad0d4eeab2fbbf25427d63b80fd0c5d72b'

- PowerMax driver - the minimum version of Unisphere for PowerMax required
  for Victoria is 9.2, so all the latest 92 REST endpoints will be used.

