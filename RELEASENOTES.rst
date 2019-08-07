======
cinder
======

.. _cinder_14.0.0.0rc1-198:

14.0.0.0rc1-198
===============

.. _cinder_14.0.0.0rc1-198_New Features:

New Features
------------

.. releasenotes/notes/MacroSAN-volume-driver-6477e4ec7c38f49d.yaml @ b'22a04777995ad92f7afc8fc58c176220ed2a9dd5'

- Added MacroSAN drivers that allows cinder to manage volumes in ISCSI and FC environment

.. releasenotes/notes/compress-images-fed3e354d94b0845.yaml @ b'1e74f318d68c131948dcad566ac11034bcef49ab'

- When uploading qcow2 images to Glance, image data will be compressed.  This
  will generally result in less data transferred to Glance at the expense of
  higher CPU usage.  This behavior is controlled by the
  "image_compress_on_upload" boolean option, which defaults to True.

.. releasenotes/notes/hpe_3par_multiattach-bf98a9e5c2208902.yaml @ b'1926a035216ed156cdb28ea27774d4e1115eeee3'

- Enabled multiattach capability for hpe3par driver.

.. releasenotes/notes/msa-multiattach-5407eb60093de8f1.yaml @ b'a91708bd2a78035ef590b017b7c76830b434a0ff'

- Support for multiattach is enabled for HPE MSA Storage

.. releasenotes/notes/netapp-solidfire-stats-improving-57207f313d7faf42.yaml @ b'eb4e6c9246e7aca65f81f8958485263513c94fec'

- NetApp SolidFire now reports QoS and efficiency stats allowing operators
  to use those values in consideration for weighting and filtering of their
  backends.

.. releasenotes/notes/new-config-opts-for-periodic_interval-d0cb17a2d72e0cd0.yaml @ b'b0279f2080ea54a123a9249c7a1a8fb027909ce2'

- Added new configuration options to allow more specific control over
  some periodic processes.  See the 'Upgrade' section for details.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added revert to snapshot support for NexentaStor5 iSCSI and NFS drivers.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- NexentaStor5 iSCSI and NFS drivers multiattach capability enabled.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added support for creating, deleting, and updating consistency groups for NexentaStor5 iSCSI and NFS drivers.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added support for taking, deleting, and restoring consistency group snapshots for NexentaStor5 iSCSI and NFS drivers.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added consistency group capability to generic volume groups for NexentaStor5 iSCSI and NFS drivers.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added volume manage/unmanage support for NexentaStor5 iSCSI and NFS drivers.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added snapshot manage/unmanage support for NexentaStor5 iSCSI and NFS drivers.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added the ability to list manageable volumes and snapshots for NexentaStor5 iSCSI and NFS drivers.

.. releasenotes/notes/powermax-ode-metro-support-ed50bb20f932548b.yaml @ b'fd8b74b61c79c7d4b7f095c608b90a5b2be31993'

- PowerMax for Cinder driver now supports extending in-use Metro RDF enabled
  volumes.

.. releasenotes/notes/powermax-tdev-deallocation-90bda0f95ab0b271.yaml @ b'cd39a9b2f19e5a3fff86dd6908ea8d76db6f0e55'

- PowerMax driver - Volume deallocate and volume delete functionality
  have been combined into a single workflow.

.. releasenotes/notes/pure-host-personality-3512f7ccd961d4ad.yaml @ b'd50d6a24d721e6ff737db4f2d8f0d19cc3e25d65'

- Pure Storage FlashArray driver has added configuration option
  ``pure_host_personality`` for setting the host personality upon host
  creation (existing hosts are not affected).

.. releasenotes/notes/pure-iscsi-cidr-cbc1afb3850a9217.yaml @ b'23cfc6efab58b239b37c6bdd16852239810dbbac'

- Pure Storage FlashArray driver has added configuration option
  ``pure_iscsi_cidr`` for setting a network CIDR for iSCSI target
  connection. The default value will allow connections to all
  iSCSI targets.

.. releasenotes/notes/readd-infortrend-driver-d9b399b53a4355f8.yaml @ b'99cb4a0b5d3ec7598d38991d39f58ed4cbedb7fa'

- Re-added Infortrend Cinder volume driver. The Infortrend driver, removed in Cinder 12.0.0 (Queens), has been restored in this release.

.. releasenotes/notes/rsd-cinder-driver-d71b88292536bfea.yaml @ b'b92b80241c86d74d71298077b3357989a9188b43'

- Added a new Cinder driver for RackScale Design NVMe-oF storage solution.

.. releasenotes/notes/support-cg-2b55da0bd9f69c7d.yaml @ b'661a4f121261569e1ce73c3ba19811db2342762d'

- Dell EMC Unity driver: Add consistent group support. Users could create a
  group type supporting consistent groups with specification
  `'consistent_group_snapshot_enabled': <is> True`, then any groups created
  of that group type are consistent groups, otherwise they are generic
  groups. The supported operations are: create/delete consistent groups, add
  volumes to and remove volumes from consistent groups, create/delete
  consistent group snapshots, create consistent groups from snapshots, clone
  consistent groups.

.. releasenotes/notes/synology-support-uc-model-9cda442828c2eb32.yaml @ b'66bfd46e4b683b2e826e9c34bd2bbfa3e3a92a7f'

- Added support for UC-Series model to Synology Cinder driver.

.. releasenotes/notes/vxflexos-support-compression-9139e556677ac093.yaml @ b'e102f3a715aad3bc55724f83320948fe71872be1'

- VxFlex OS driver now supports VxFlex OS 3.0 features:
  storage pools with fine granularity layout,
  volume compression(SPEF).


.. _cinder_14.0.0.0rc1-198_Upgrade Notes:

Upgrade Notes
-------------

.. releasenotes/notes/bug-1813851-60a4f0ffe386d9b6.yaml @ b'd960cb0477c3e782463632c94d888bcd121083da'

- Added config option ``backup_mount_attempts`` to specify the
  number of attempts to mount NFS share in the NFS backup driver.

.. releasenotes/notes/cinder-status-check-backup_driver-fe009985df2bc32f.yaml @ b'cef38b5e849bad294374adaf213efabfc26b0d5c'

- A new check is added to the ``cinder-status upgrade check`` CLI to check
  for the use of backup driver module path instead of full driver class path
  in the ``backup_driver`` configuration setting.

.. releasenotes/notes/cinder-status-check-policyjson-ef61826eab95372b.yaml @ b'8c6355f3ccb64cb949a8280b6cd98a37e13bfaa7'

- A warning has been added to the ``cinder-status upgrade check`` CLI if a
  ``policy.json`` file is present. Documentation has been updated to
  correct the file as ``policy.yaml`` if any policies need to be changed from
  their defaults.

.. releasenotes/notes/cinder-status-check-stein_removed_drivers-8184abe8ce82f373.yaml @ b'e78e05c95dcb01336811a503c4292ac528959b8d'

- A new check is added to the ``cinder-status upgrade check`` CLI to check
  for the configuration of CoprHD, HGST or ITRI DISCO drivers.  These
  drivers were removed in the Stein release and should not be
  configured at the time of upgrade.

.. releasenotes/notes/cinder-status-check-windows_iscsi_driver-5f4e0b93c7b92f53.yaml @ b'bc18906f01b10ca21a68b0b760503436caa4f91a'

- A new check is added to the ``cinder-status upgrade check`` CLI to check
  for the use of ``cinder.volume.drivers.windows.windows.WindowsDriver``
  and a message is reported that the user needs to update the setting
  to ``cinder.volume.drivers.windows.iscsi.WindowsISCSIDriver`` if
  it is encountered.

.. releasenotes/notes/datera-mark-unsupported-7b71d9124b3fded2.yaml @ b'32aa53eaf54efa8e5e49e40c195afe8e90f5136d'

- The driver for Datera's Storage Systems has been marked as unsupported
  and is now deprecated. ``enable_unsupported_driver`` will need to
  be set to ``True`` in the driver's section in cinder.conf to continue
  to use it.

.. releasenotes/notes/db-schema-from-queens-de5025a780ff1d30.yaml @ b'883e78537592e9764e86329153d5e52922473092'

- The Cinder database can now only be upgraded with changes since the Queens
  release. In order to upgrade from a version prior to that, you must now
  upgrade to at least Queens first.

.. releasenotes/notes/deprecate-nested-quota-d1ad7e8f54492a87.yaml @ b'8fbfe923bd99760293117dea47040c77746bc2d5'

- A new check is added to the ``cinder-status upgrade check`` CLI to check
  for the use of the deprecated ``cinder.quota.NestedDbQuotaDriver``. This
  driver will be replaced by a new, OpenStack-wide, nested quota management.

.. releasenotes/notes/new-config-opts-for-periodic_interval-d0cb17a2d72e0cd0.yaml @ b'b0279f2080ea54a123a9249c7a1a8fb027909ce2'

- The ``periodic_interval`` configuration option was being used in too
  many places, and as a result, it had become difficult to tune specific
  periodic tasks without affecting other functionality.  The following
  configuration options should now be used in place of ``periodic_interval``:
  
  * ``backup_driver_init_check_interval``
  * ``backup_driver_status_check_interval``
  * ``scheduler_driver_init_wait_time``
  * ``backend_stats_polling_interval``
  
  See the help text for these options for more information.  The default
  value of each option is 60, which has been the default value of
  ``periodic_interval``.
  
  * If you *have not* modified ``periodic_interval``, you should see no
    differences from current behavior.
  * If you *have* modified ``periodic_interval``, please review the new
    options to determine which one(s) should be adjusted.  Also, you should
    consider setting ``periodic_interval`` back to its default value of 60.
  
  A warning has been added to the ``cinder-status upgrade check`` CLI
  to detect whether the ``periodic_interval`` option has been modified
  from its default value to remind you which of the above situations
  currently applies to you.
  
  The ``periodic_interval`` configuration option still exists but its
  use is now restricted to providing a default periodicity for objects
  created from the ``cinder.service.Service`` class.

.. releasenotes/notes/nexenta-edge-driver-removal-5626d542d75f3d43.yaml @ b'a1c58b50ea90986242afa9efe684bd5b87a39daf'

- The Nexenta Edge storage driver has been removed after completion of its
  deprecation period without a reliable 3rd Party CI system being
  supported.  Customers using the Nexenta Edge driver should not upgrade
  Cinder without first migrating all volumes from their Nexenta backend
  to a supported storage backend.  Failure to migrate volumes will
  result in no longer being able to access volumes back by the Nexenta Edge
  storage backend.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added a new config option ``nexenta_rest_connect_timeout``. This option specifies the time limit (in seconds), within which the connection to NexentaStor management REST API server must be established.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added a new config option ``nexenta_rest_read_timeout``. This option specifies the time limit (in seconds), within which NexentaStor management REST API server must send a response.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added a new config option ``nexenta_rest_backoff_factor``. This option specifies the backoff factor to apply between connection attempts to NexentaStor management REST API server.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added a new config option ``nexenta_rest_retry_count``. This option specifies the number of times to repeat NexentaStor management REST API call in case of connection errors and NexentaStor appliance EBUSY or ENOENT errors.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added a new config option ``nexenta_origin_snapshot_template``. This option specifies template string to generate origin name of clone.

.. releasenotes/notes/nexentastor5-driver-update-937d2a1ba76a504a.yaml @ b'c981616d59576afb36afe602d09f081a6d37edfd'

- Added a new config option ``nexenta_group_snapshot_template``. This option specifies template string to generate group snapshot name.

.. releasenotes/notes/nimble-mark-usnsupported-0c8e5e21c8d1179d.yaml @ b'f37b98ed9ac837bdf9307734b5fe0d6c0e089169'

- The Nimble driver has been marked as unsupported and is now
  deprecated. ``enable_unsupported_driver`` will need to be set
  to ``True`` in the driver's section in cinder.conf to continue
  to use it.

.. releasenotes/notes/remove-datacore-300c667e9f504590.yaml @ b'7f2c9f103eda6d04e115f9959b1cbdcb6d2982ff'

- The DataCore drivers were marked as unsupported in the Rocky release and
  have now been removed.

.. releasenotes/notes/remove-drbdmanage-driver-4edd1e1e43b6ba39.yaml @ b'fbab79dee253b8fa2b58e491e3a358b0e30c7065'

- The DRBDManage driver is now removed.  Customers using the DRBDManage driver should not upgrade Cinder without first migrating all volumes from their DRBDManage backend to a supported storage backend such as LINSTOR.  Failure to migrate volumes will result in not being able to access volumes backed by the DRBDManage storage backend.

.. releasenotes/notes/remove_veritas_hyperscale_driver-988ad62d2417124f.yaml @ b'9aca21f5cec8f03a3bb410acb21399955144fe0f'

- The Veritas HyperScale storage driver has been removed after completion of its
  deprecation period without a reliable 3rd Party CI system being
  supported.  Customers using the Veritas HyperScale driver should not upgrade
  Cinder without first migrating all volumes from their Veritas backend
  to a supported storage backend.  Failure to migrate volumes will
  result in no longer being able to access volumes backed by the Veritas
  HyperScale storage backend.

.. releasenotes/notes/scaleio-vxflexos-rebrand-27dfe2b82d35b6a2.yaml @ b'0eaca453bc1e8a45d8883d95080d0cab01dadcd7'

- Dell EMC ScaleIO has been rebranded to VxFlex OS. The drivers
  ``cinder.volume.drivers.dell_emc.scaleio.driver.ScaleIODriver``
  will now be updated to
  ``cinder.volume.drivers.dell_emc.vxflexos.driver.VxFlexOSDriver``
  in cinder.conf. Driver configuration options that start with ``sio``
  should also be updated to ``vxflexos``. Existing sio configuration options
  will continue to work but will be removed in the V release.
  Online documentation will also change to reflect these changes.

.. releasenotes/notes/sheepdog-mark-unsupported-648b2458d4a198de.yaml @ b'e2e5bddd4c6a23ebb6a3a84d73e80bc90513645b'

- The Sheepdog driver has been marked as unsupported
  and is now deprecated. ``enable_unsupported_driver`` will
  need to be set to ``True`` in the driver's section in
  cinder.conf to continue to use the driver.

.. releasenotes/notes/tintri-driver-removal-91a0931c417481d2.yaml @ b'0423642951f309a2ac3338e9a02ed9982f4563b8'

- The Tintri storage driver has been removed after completion of its
  deprecation period without a reliable 3rd Party CI system being
  supported.  Customers using the Tintri driver should not upgrade
  Cinder without first migrating all volumes from their Tintri backend
  to a supported storage backend.  Failure to migrate volumes will
  result in no longer being able to access volumes backed by the Tintri
  storage backend.

.. releasenotes/notes/unsupport-prophetstor-bfbc674fd86303db.yaml @ b'1d488005a59d47342431b9b788279a61a66aff3d'

- The Prophetstor driver has been marked as unsupported and is now
  deprecated. ``enable_unsupported_driver`` will need to be set
  to ``True`` in the driver's section in cinder.conf to continue
  to use it.

.. releasenotes/notes/unsupport-veritas-access-ecfb4122770d93f9.yaml @ b'197b7fc179dcc37701da9467019cc8067885c167'

- The Veritas Access driver has been marked as unsupported and is now
  deprecated. ``enable_unsupported_driver`` will need to be set
  to ``True`` in the driver's section in cinder.conf to continue
  to use it.

.. releasenotes/notes/vxflexos_drop_deprecated_opt-3231a222e458fa92.yaml @ b'7fb9b430eea0538e42dadbcab35f93979c667c64'

- VxFlex OS (ScaleIO) driver drops support for options, which
  were marked as deprecated in Pike release.
  Remove config options: ``sio_protection_domain_id``,
  ``sio_protection_domain_name``,
  ``sio_storage_pool_name``,
  ``sio_storage_pool_id``.
  Remove volume type options: ``sio:sp_name``,
  ``sio:sp_id``,
  ``sio:pd_name``,
  ``sio:pd_id``,
  ``sio:provisioning_type``,
  ``sio:iops_limit``,
  ``sio:bandwidth_limit``.


.. _cinder_14.0.0.0rc1-198_Deprecation Notes:

Deprecation Notes
-----------------

.. releasenotes/notes/datera-mark-unsupported-7b71d9124b3fded2.yaml @ b'32aa53eaf54efa8e5e49e40c195afe8e90f5136d'

- The driver for Datera's Storage Systems has been marked as unsupported
  and is now deprecated. ``enable_unsupported_driver`` will need to
  be set to ``True`` in the driver's section in cinder.conf to continue
  to use it. If its support status does not change, it will be
  removed in the 'U' development cycle.

.. releasenotes/notes/deprecate-nested-quota-d1ad7e8f54492a87.yaml @ b'8fbfe923bd99760293117dea47040c77746bc2d5'

- The ``cinder.quota.NestedDbQuotaDriver`` quota driver for handling nested
  projects is now deprecated. There is an OpenStack-wide effort to move to
  "unified limits" that will require changes in how quotas are handled for
  these types of configurations. The ``NestedDbQuotaDriver`` will continue
  to work until it is replaced with this new mechanism.

.. releasenotes/notes/nimble-mark-usnsupported-0c8e5e21c8d1179d.yaml @ b'f37b98ed9ac837bdf9307734b5fe0d6c0e089169'

- The Nimble driver has been marked as unsupported and is now
  deprecated. ``enable_unsupported_driver`` will need to be set
  to ``True`` in the driver's section in cinder.conf to continue
  to use it. If its support status does not change, it will be
  removed in the 'U' development cycle.

.. releasenotes/notes/remove-drbdmanage-driver-4edd1e1e43b6ba39.yaml @ b'fbab79dee253b8fa2b58e491e3a358b0e30c7065'

- The DRBDManage driver is deprecated as of the Stein release and is removed in the Train release.  Users should use the new LINSTOR driver instead.

.. releasenotes/notes/sheepdog-mark-unsupported-648b2458d4a198de.yaml @ b'e2e5bddd4c6a23ebb6a3a84d73e80bc90513645b'

- The Sheepdog driver has been marked as unsupported
  and is now deprecated. ``enable_unsupported_driver`` will
  need to be set to ``True`` in the driver's section in
  cinder.conf to continue to use the driver. The driver
  is scheduled for removal in the 'U' release.

.. releasenotes/notes/unsupport-prophetstor-bfbc674fd86303db.yaml @ b'1d488005a59d47342431b9b788279a61a66aff3d'

- The Prophetstor driver has been marked as unsupported and is now
  deprecated. ``enable_unsupported_driver`` will need to be set
  to ``True`` in the driver's section in cinder.conf to continue
  to use it. If its support status does not change, it will be
  removed in the 'U' development cycle.

.. releasenotes/notes/unsupport-veritas-access-ecfb4122770d93f9.yaml @ b'197b7fc179dcc37701da9467019cc8067885c167'

- The Veritas Access driver has been marked as unsupported and is now
  deprecated. ``enable_unsupported_driver`` will need to be set
  to ``True`` in the driver's section in cinder.conf to continue
  to use it. If its support status does not change, it will be
  removed in the 'U' development cycle.

.. releasenotes/notes/vmware_revert_datastore_stats-ba85b30612970d91.yaml @ b'f3ee3dbf4e4794d77cf263be3eec144328a3bedf'

- The config option ``vmware_storage_profile`` is now deprecated
  and ignored. Setting this option results in performance degradation
  of the controller and put lot of load on vCenter server.


.. _cinder_14.0.0.0rc1-198_Bug Fixes:

Bug Fixes
---------

.. releasenotes/notes/bug-1782588-7e058b379da95309.yaml @ b'12a7bf699df1558f081513b1686d9c389bd3b812'

- Solidfire fix extend volume with qos-Scaling to honor the increased size
  with increased iops on the extended volume.

.. releasenotes/notes/bug-1833115-fix-netapp-ontap-python3-failures-dd869e602f9539e1.yaml @ b'31d8f6b38fec4e186e54a2275999c25502197368'

- Fix python 3 incompatibility issues preventing NetApp cDOT driver from
  generating EMS logging messages (Bug #1833115).

.. releasenotes/notes/detachedinstanceerror-64be35894c624eae.yaml @ b'2e73bede80cc2acdb3527f06bc5c5f9c1a8463a7'

- Fix DetachedInstanceError is not bound to a Session for VolumeAttachments.
  This affected VolumeList.get_all, and could make a service fail on startup
  and make it stay in down state.

.. releasenotes/notes/hpe-3par-specify-nsp-for-fc-bootable-volume-f372879e1b625b4d.yaml @ b'b7c81a7b426136314fb12f5aafcb977b25d49cc6'

- This change fixes bug 1809249 - 3PAR driver picks wrong port when
  not in multipath mode. Now the user can specify target NSP (Node-
  Slot-Port) in cinder.conf. This information is used to create
  initiator target map accordingly. And then bootable volume is
  created successfully.

.. releasenotes/notes/kaminario-cinder-driver-bug-44c728f026394a85.yaml @ b'49331b2bb6fc8154343fe2655a0c57e814cf4f7a'

- Kaminario FC and iSCSI drivers: Fixed `bug 1829398
  <https://bugs.launchpad.net/cinder/+bug/1829398>`_ where
  force detach would fail.

.. releasenotes/notes/netapp-non-discovery-19af4e10f7b190ea.yaml @ b'c65869626594522231709d9c90a30524a1f0d18c'

- NetApp iSCSI drivers no longer use the discovery mechanism for multipathing
  and they always return all target/portals when attaching a volume.  Thanks
  to this, volumes will be successfully attached even if the target/portal
  selected as primary is down, this will be the case for both, multipath and
  single path connections.

.. releasenotes/notes/rbd_replication_add_secret_uuid_config-c74d65e6d3d610c6.yaml @ b'e0e912b084923e6da831533c21b10e46f48d2cf1'

- Rbd replication secondary device could set different user and keyring with primary cluster.
  Secondary secret_uuid value is configed in libvirt secret, and libvirtd using secondary secret
  reconnect to secondary cluster after Cinder failover host.

.. releasenotes/notes/vnx-add-async-migrate-option-0734164feeaecadc.yaml @ b'3ecdc2bfc827c5ae8003f877bd95ca8c1385c596'

- Dell EMC VNX Driver: Fix `bug 1796825
  <https://bugs.launchpad.net/cinder/+bug/1796825>`__, adding an option named
  `vnx_async_migrate` to accept the default setting for async migration.

.. releasenotes/notes/vnx-fail-delete-lun-due-to-tmp-snapshot-edd3cdd85e28be60.yaml @ b'b3a89dc187ae4d71fb1fc27645cb4383209b0ef8'

- Dell EMC VNX Cinder Driver: Fixes `bug 1794646
  <https://bugs.launchpad.net/cinder/+bug/1794646>`__ to delete the LUN from
  the VNX storage. Because a temporary snapshot is created from the LUN
  during creating a volume from a snapshot and isn't deleted, the LUN cannot
  be deleted before its snapshot is deleted. The fix makes sure the temp
  snapshot is deleted.


.. _cinder_14.0.0.0rc1-198_Other Notes:

Other Notes
-----------

.. releasenotes/notes/nexenta-edge-driver-removal-5626d542d75f3d43.yaml @ b'a1c58b50ea90986242afa9efe684bd5b87a39daf'

- The Nexenta Edge storage driver was marked unsupported  in Stein due to
  3rd Party CI not meeting Cinder's requirements.  As a result the
  driver is removed starting from the Train release.

.. releasenotes/notes/powermax-90-to-91-endpoints-a92c4d158cb63fe4.yaml @ b'bcc12d383a82250bda0f5c4c06203b0655613be1'

- PowerMax driver - the minimum version of Unisphere for PowerMax required
  for Train is 9.1, so all the latest 91 REST endpoints will be used.

.. releasenotes/notes/remove_veritas_hyperscale_driver-988ad62d2417124f.yaml @ b'9aca21f5cec8f03a3bb410acb21399955144fe0f'

- The Veritas HyperScale storage driver was marked unsupported  in Stein due to
  3rd Party CI not meeting Cinder's requirements.  As a result the
  driver is removed starting from the Train release.

.. releasenotes/notes/tintri-driver-removal-91a0931c417481d2.yaml @ b'0423642951f309a2ac3338e9a02ed9982f4563b8'

- The Tintri storage driver was marked unsupported in Stein due to
  3rd Party CI not meeting Cinder's requirements.  As a result the
  driver is removed starting from the Train release.

