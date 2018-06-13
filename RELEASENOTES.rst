======
cinder
======

.. _cinder_13.0.0.0b2:

13.0.0.0b2
==========

.. _cinder_13.0.0.0b2_New Features:

New Features
------------

.. releasenotes/notes/add-operation-to-request-spec-7yt6ub75uy1284as.yaml @ e1ec4b4c2e1f0de512f09e38824c1d7e2fa38617

- Now scheduler plugins are aware of operation type via ``operation`` attribute in
  RequestSpec dictionary, plugins can support backend filtering according to backend
  status as well as operation type. Current possible values for ``operation`` are:
  
  - create_volume
  - extend_volume
  - create_snapshot
  - retype_volume
  - migrate_volume
  - manage_existing
  - manage_existing_snapshot
  - create_group

.. releasenotes/notes/bp-nvmeof-lvm-target-b7771955b426abe7.yaml @ 8d7e131c587f31d85c76f990998d411af490554f

- A new target, NVMET, is added for the LVM driver over RDMA,
  it allows cinder to use nvmetcli in order to create/delete
  subsystems on attaching/detaching an LVM volume to/from an
  instance.

.. releasenotes/notes/google-auth-for-gcs-backup-1642cd0e741fbdf9.yaml @ 79d7a4e8da6f1118b5c235928876cf78085f4332

- Google backup driver now supports ``google-auth`` library, and is the preferred library if both ``google-auth`` (together with ``google-auth-httplib2``) and ``oauth2client`` libraries are present in the system.

.. releasenotes/notes/nexentaedge-iscsi-driver-302529c56cdbbf38.yaml @ e2bd03ef75b4417e3531186fd6cc0a270ffbd32c

- Added backend driver for Nexenta Edge iSCSI storage.

.. releasenotes/notes/rbd-active-active-replication-b230367912fe4a23.yaml @ 245a488c36003764e3550c2c95fa4bef6119e0ea

- Added support for active-active replication to the RBD driver.  This allows users to configure multiple volume backends that are all a member of the same cluster participating in replication.

.. releasenotes/notes/scaleio-rebranding-d2d113c5d8e5c118.yaml @ a852c46ba483e9a015c30a77fa461b45c1517786

- Dell EMC ScaleIO has been renamed to Dell EMC VxFlex OS.
  Documentation for the driver can be found under the new name.
  The driver maintains full backwards compatability with prior
  ScaleIO releases and no configuration changes are needed upon
  upgrade to the new version of the driver.

.. releasenotes/notes/support-az-in-volumetype-8yt6fg67de3976ty.yaml @ 306fa19079ccf8f5278fdf36341edecd95df04a7

- Now availability zone is supported in volume type as below.
  
  * ``RESKEY:availability_zones`` now is a reserved spec key for AZ volume type,
    and administrator can create AZ volume type that includes AZ restrictions
    by adding a list of Az's to the extra specs similar to:
    ``RESKEY:availability_zones: az1,az2``.
  * Extra spec ``RESKEY:availability_zones`` will only be used for filtering backends
    when creating and retyping volumes.
  * Volume type can be filtered within extra spec: /types?extra_specs={"key":"value"}
    since microversion "3.52".

.. releasenotes/notes/unity-remove-empty-host-17d567dbb6738e4e.yaml @ f9a9aa5a25688cac86e5dc060a20374e4a29bbef

- Dell EMC Unity Driver: Adds support for removing empty host. The new option
  named `remove_empty_host` could be configured as `True` to notify Unity
  driver to remove the host after the last LUN is detached from it.

.. releasenotes/notes/vmax-driver-multiattach-support-43a7f99cd2d742ee.yaml @ 106cf3cbf0a094755d4af063a05de9aa36ae385d

- Dell EMC VMAX driver has added multiattach support.

.. releasenotes/notes/vmware_vmdk_nfs41-450908bbbc9eea6d.yaml @ 68e3b4a1d544683a7d7b0cfd7f730dc9a0bbdd77

- VMware VMDK driver and FCD driver now support NFS 4.1
  datastores in vCenter server.


.. _cinder_13.0.0.0b2_Upgrade Notes:

Upgrade Notes
-------------

.. releasenotes/notes/remove-deprecated-option-9ad954726ed4d8c2.yaml @ d1c5379369b24effdccfe5dde3e93bd21884eda5

- Removed the option ``allow_inuse_volume_type_modification`` which had
  been deprecated in Ocata release.

.. releasenotes/notes/remove-lvm-over-sub-3c8addbf47827045.yaml @ 2c05388d5ccbbecbbe02b45aec30f24321da0057

- The LVM driver specific `lvm_max_over_subscription_ratio` setting had been
  deprecated and is now removed. Over subscription should now be managed
  using the generic `max_over_subscription_ratio` setting.


.. _cinder_13.0.0.0b2_Deprecation Notes:

Deprecation Notes
-----------------

.. releasenotes/notes/google-auth-for-gcs-backup-1642cd0e741fbdf9.yaml @ 79d7a4e8da6f1118b5c235928876cf78085f4332

- Cinder's Google backup driver is now called gcs, so ``backup_driver`` configuration for Google Cloud Storage should be updated from ``cinder.backup.drivers.google`` to ``cinder.backup.driver.gcs``.


.. _cinder_13.0.0.0b2_Bug Fixes:

Bug Fixes
---------

.. releasenotes/notes/bug-1712651-7bc90264eb5001ea.yaml @ 2b60912d5667350eae7ecbc67d4dba3658518d10

- NetApp ONTAP iSCSI (bug 1712651): Fix ONTAP NetApp iSCSI driver not
  raising a proper exception when trying to extend an attached volume
  beyond its max geometry.

.. releasenotes/notes/bug-1762424-f76af2f37fe408f1.yaml @ 029cadbf4067ad6f0bf08588cf439587f3c7052c

- NetApp ONTAP (bug 1762424): Fix ONTAP NetApp driver not being able to extend
  a volume to a size greater than the corresponding LUN max geometry.

.. releasenotes/notes/bug-1765610-qnap-fix-volume-snapshot-create-fail-2bb785eafdb87fb6.yaml @ 880ff557ca3d6569464b9667ac25825cf5e3c7fd

- Fixed QNAP driver failures to create volume and snapshot in some
  cases.

.. releasenotes/notes/bug-1766768-qnap-fix-upload-volume-detach-fail-33cbee59f1381bda.yaml @ ee9fda3e89b619c058768d5fa17cc3e9ecf4a99f

- Fixed QNAP driver failures to detach iscsi device while uploading volume
  to image.

.. releasenotes/notes/fix-extend-volume-939e30f2e9e516bc.yaml @ c96f3997104f0dca4ed191e3df92715b33bd1a63

- [`bug 1772421 <https://bugs.launchpad.net/keystone/+bug/1772421>`_]
  INFINIDAT fixed a bug in volume extension feature where volumes
  were not extended to target size but added the given target size.

.. releasenotes/notes/google-auth-for-gcs-backup-1642cd0e741fbdf9.yaml @ 79d7a4e8da6f1118b5c235928876cf78085f4332

- Google backup driver now works when using ``google-api-python-client`` version 1.6.0 or higher.


.. _cinder_13.0.0.0b1:

13.0.0.0b1
==========

.. _cinder_13.0.0.0b1_New Features:

New Features
------------

.. releasenotes/notes/bug-1686745-e8f1569455f998ba.yaml @ abca1abc7b01fc1d85af8b9cfa5b646abafc9d4a

- Add support to force detach a volume from all hosts on 3PAR.

.. releasenotes/notes/capacity-based-qos-9f5d174658a40bd5.yaml @ 29d2090aef7b31df23ca846d365c6d21957486ba

- Cinder now allows for capacity based QoS which can be useful in environments where storage performance scales with consumption (such as RBD backed storage).  The newly added QoS specs are `read_iops_sec_per_gb`, `write_iops_sec_per_gb`, `total_iops_sec_per_gb`, `read_bytes_sec_per_gb`, `write_bytes_sec_per_gb` and `total_bytes_sec_per_gb`.  These values will be multiplied by the size of the volume and passed to the consumer.
  For example, setting `total_iops_sec_per_gb` to 30 and setting `total_bytes_sec_per_gb` to `1048576` (1MB) then creating a 100 GB volume with that QoS will result in a volume with 3,000 total IOPs and 100MB/s throughput limit.

.. releasenotes/notes/dell-emc-sc-api-timeouts-ce8d166e1847ea94.yaml @ 1d6ad6ef179f465289c95b5f45ac79b0f03e0866

- Added dell_api_async_rest_timeout option to the Dell EMC SC driver. This is the timeout used for asynchronous REST calls to the Dell EMC SC REST API. Default is 15 seconds.

.. releasenotes/notes/dell-emc-sc-api-timeouts-ce8d166e1847ea94.yaml @ 1d6ad6ef179f465289c95b5f45ac79b0f03e0866

- Added dell_api_sync_rest_timeout option to the Dell EMC SC driver. This is the timeout used for synchronous REST calls to the Dell EMC SC REST API. Default is 30 seconds.

.. releasenotes/notes/feature-abort-restore-fe1252288c59e105.yaml @ 89f6291ee33780ed6d4e4886d5d18a0ce0cdb182

- Support backup restore cancelation by changing the backup status to
  anything other than `restoring` using `cinder backup-reset-state`.

.. releasenotes/notes/feature-cross-az-backups-6b68c4c4456f2fd7.yaml @ 5feaf74ccf10148859e206ce21bfd54dec2c1c16

- Cinder backup creation can now (since microversion 3.51) receive the
  availability zone where the backup should be stored.

.. releasenotes/notes/feature-multi-process-backup-8cf5ad5a0cf9b2d5.yaml @ 373b52404151d80e83004a37d543f825846edea1

- Cinder backup now supports running multiple processes to make the most of
  the available CPU cores.  Performance gains will be significant when
  running multiple concurrent backups/restores with compression.  The number
  of processes is set with `backup_workers` configuration option.

.. releasenotes/notes/feature-rbd-exclusive-pool-a9bdebdeb1f0bf37.yaml @ f33baccc3544cbda6cd5908328a56096046657ed

- When using the RBD pool exclusively for Cinder we can now set
  `rbd_exclusive_cinder_pool` to `true` and Cinder will use DB information
  to calculate provisioned size instead of querying all volumes in the
  backend, which will reduce the load on the Ceph cluster and the volume
  service.

.. releasenotes/notes/infinidat-multi-attach-support-533b3e559c15801f.yaml @ 666c0fc8db20dfe1d5adc036d24b52a3eaa1091a

- Support for volume multi-attach in the INFINIDAT InfiniBox driver.

.. releasenotes/notes/inspur-instorage-fc-cinder-driver-70c13e4a64d785d5.yaml @ a6e79968ed237a7f0982cdc0d8fcf231d63b38fc

- New FC Cinder volume driver for Inspur Instorage.

.. releasenotes/notes/report-backend-state-in-service-list-93e9f2b204b735c0.yaml @ c5a8000b9c857521e896e1fc39a77f0fcfc12ccc

- Added flag 'backend_state' which will give backend state info in service list.

.. releasenotes/notes/smbfs-snapshot-attach-14742fe8f5864ac6.yaml @ 32a08e4d6a18be743e936448f05f97113e80619c

- The SMBFS driver now supports the 'snapshot attach' feature. Special care
  must be taken when attaching snapshots though, as writing to a snapshot
  will corrupt the differencing image chain.

.. releasenotes/notes/sync-bump-versions-a1e6f6359173892e.yaml @ 3cd2ebd3759c76fdf5a292e612127094c7aa2b17

- Cinder-manage DB sync command can now bump the RPC and Objects versions of the services to avoid a second restart when doing offline upgrades.

.. releasenotes/notes/tpool-size-11121f78df24db39.yaml @ e570436d1cca5cfa89388aec8b2daa63d01d0250

- Adds support to configure the size of the native thread pool used by the cinder volume and backup services.  For the backup we use `backup_native_threads_pool_size` in the `[DEFAULT]` section, and for the backends we use `backend_native_threads_pool_size` in the driver section.

.. releasenotes/notes/unity-enable-ssl-14db2497225c4395.yaml @ 8aa49599c7df62de5ab25a0a841265092e2881f7

- Dell EMC Unity Cinder driver allows enabling/disabling the SSL verification. Admin can set `True` or `False` for `driver_ssl_cert_verify` to enable or disable this function, alternatively set the `driver_ssl_cert_path=<PATH>` for customized CA path. Both above 2 options should go under the driver section.

.. releasenotes/notes/veritas_access_iscsi_driver-de642dad9e7d0890.yaml @ a9fad35a20570e6ecd3757ea50e794a0592c3921

- Added ISCSI based driver for Veritas Access.

.. releasenotes/notes/vmax-retype-replicated-volumes-325be6e5fd626819.yaml @ 992542a9fb00efdd479d2d18fd6da848b162adf9

- Support for retype (storage-assisted migration) of replicated volumes on VMAX cinder driver.

.. releasenotes/notes/vmware_vmdk_datastore_regex-fe7b68ad69ef7384.yaml @ f1e21ee2526e35c60f5d2251d569469dddd4efc5

- VMware VMDK driver and FCD driver now support a config option
  ``vmware_datastore_regex`` to specify the regular expression
  pattern to match the name of datastores where backend volumes
  are created.

.. releasenotes/notes/vnx-revert-to-snapshot-e5494b6fb5ad5a1e.yaml @ 2cd65abb713381bbf6155e6e176043f9c41c04a7

- Added support to revert a volume to a snapshot with the Dell EMC VNX
  driver.

.. releasenotes/notes/windows-volume-backup-b328858a20f5a499.yaml @ 302402df330a52fbe9e531cf5603babad0c1f367

- The Cinder Volume Backup service can now be run on Windows. It supports
  backing up volumes exposed by SMBFS/iSCSI Windows Cinder Volume backends,
  as well as any other Cinder backend that's accessible on Windows (e.g.
  SANs exposing volumes via iSCSI/FC).
  
  The Swift and Posix backup drivers are known to be working on Windows.


.. _cinder_13.0.0.0b1_Known Issues:

Known Issues
------------

.. releasenotes/notes/feature-rbd-exclusive-pool-a9bdebdeb1f0bf37.yaml @ f33baccc3544cbda6cd5908328a56096046657ed

- If RBD stats collection is taking too long in your environment maybe even
  leading to the service appearing as down you'll want to use the
  `rbd_exclusive_cinder_pool = true` configuration option if you are using
  the pool exclusively for Cinder and maybe even if you are not and can live
  with the innacuracy.


.. _cinder_13.0.0.0b1_Upgrade Notes:

Upgrade Notes
-------------

.. releasenotes/notes/remove-backup-service-to-driver-mapping-4d2ed6f868a64175.yaml @ 497cd4e3cdbea7b61d9bca46a65561993e0b9f26

- Backup service to driver mapping is removed. If you use old values like
  'cinder.backup.services.swift' or 'cinder.backup.services.ceph' it should
  be changed to 'cinder.backup.drivers.swift' or 'cinder.backup.drivers.ceph'
  accordingly to get your backup service working.

.. releasenotes/notes/sync-bump-versions-a1e6f6359173892e.yaml @ 3cd2ebd3759c76fdf5a292e612127094c7aa2b17

- On offline upgrades, due to the rolling upgrade mechanism we need to restart the cinder services twice to complete the installation just like in the rolling upgrades case.  First you stop the cinder services, then you upgrade them, you sync your DB, then you start all the cinder services, and then you restart them all.  To avoid this last restart we can now instruct the DB sync to bump the services after the migration is completed, the command to do this is `cinder-manage db sync --bump-versions`


.. _cinder_13.0.0.0b1_Deprecation Notes:

Deprecation Notes
-----------------

.. releasenotes/notes/add-option-max_luns_per_storage_group-dfe3e1396b262bc8.yaml @ 04847424b462ceade2daaca519a14e28779a026d

- Deprecate option `check_max_pool_luns_threshold`. The VNX driver will
  always check the threshold.


.. _cinder_13.0.0.0b1_Security Issues:

Security Issues
---------------

.. releasenotes/notes/scaleio-zeropadding-a0273c56c4d14fca.yaml @ 7feb62197d371ab7253dc86a34af6ff8b484b4df

- Removed the ability to create thick volumes in a ScaleIO Storage Pool
  that has zero-padding disabled; creation of thin volumes from these
  pools is allowed. A new configuration option has been added to
  override this new behavior and allow thick volumes, but should not
  be enabled if multiple tenants will utilize thick volumes from a shared
  Storage Pool.


.. _cinder_13.0.0.0b1_Bug Fixes:

Bug Fixes
---------

.. releasenotes/notes/add-option-max_luns_per_storage_group-dfe3e1396b262bc8.yaml @ 04847424b462ceade2daaca519a14e28779a026d

- Add option `max_luns_per_storage_group` back. The max LUNs per storage
  group was set to 255 before. With the new option, admin can set it to a
  larger number.

.. releasenotes/notes/bug-1690954-40fc21683977e996.yaml @ 4d75cbf3c35a8aa917d3970beac99d612f13eed3

- NetApp ONTAP NFS (bug 1690954): Fix wrong usage of export path
  as volume name when deleting volumes and snapshots.

.. releasenotes/notes/dell-emc-sc-bugfix-1756914-ffca3133273040f6.yaml @ f8980ea128dd6698a1cb3a283d98b47371b854f6

- Dell EMC SC driver correctly returns initialize_connection data when more than one IQN is attached to a volume. This fixes some random Nova Live Migration failures where the connection information being returned was for an IQN other than the one for which it was being requested.

.. releasenotes/notes/fail-detach-lun-when-auto-zone-enabled-9c87b18a3acac9d1.yaml @ c816be897e7ab1c95b38979b2cc94ecf179e44e7

- Dell EMC Unity Driver: Fixes `bug 1759175
  <https://bugs.launchpad.net/cinder/+bug/1759175>`__
  to detach the lun correctly when auto zone was enabled and the lun was the
  last one attached to the host.

.. releasenotes/notes/fix-abort-backup-df196e9dcb992586.yaml @ 4ff9e63707e2c4cf5869f28e3e86fd0606d2db9a

- We no longer leave orphaned chunks on the backup backend or leave a
  temporary volume/snapshot when aborting a backup.

.. releasenotes/notes/fix-cross-az-migration-ce97eff61280e1c7.yaml @ fb8085894b69f56091bde19683a919cb15d502cc

- Resolve issue with cross AZ migrations and retypes where the destination
  volume kept the source volume's AZ, so we ended up with a volume where the
  AZ does not match the backend. (bug 1747949)

.. releasenotes/notes/migrate-backup-encryption-keys-to-barbican-6f07fd48d4937b2a.yaml @ 341dd44ba796e933920da6718a2891e35ed88506

- When encryption keys based on the ConfKeyManager's fixed_key are migrated
  to Barbican, ConfKeyManager keys stored in the Backup table are included
  in the migration process.
  Fixes `bug 1757235 <https://bugs.launchpad.net/tripleo/+bug/1757235>`__.

.. releasenotes/notes/netapp-ontap-use_exact_size-d03c90efbb8a30ac.yaml @ 67391f1f0f30172190882e7d3f4a4ddc271dfa00

- Fixed bug #1731474 on NetApp Data ONTAP driver that was causing LUNs to be created
  with larger size than requested. This fix requires version 9.1 of ONTAP
  or later.

.. releasenotes/notes/quobyte_vol-snap-cache-baf607f14d916ec7.yaml @ 8c72fcadae92640331807f021401a7c250e56286

- Added a new optional cache of volumes generated from snapshots for the
  Quobyte backend. Enabling this cache speeds up creation of multiple
  volumes from a single snapshot at the cost of a slight increase in
  creation time for the first volume generated for this given snapshot.
  The ``quobyte_volume_from_snapshot_cache`` option is off by default.

.. releasenotes/notes/storwize-hyperswap-host-site-update-621e763768fab9ee.yaml @ b13a8f810b143f5f0f465ab45eab453c1e65de7d

- Updated the parameter storwzie_preferred_host_site from StrOpt to DictOpt
  in cinder back-end configuration, and removed it from volume type
  configuration.

.. releasenotes/notes/sync-bump-versions-a1e6f6359173892e.yaml @ 3cd2ebd3759c76fdf5a292e612127094c7aa2b17

- After an offline upgrade we had to restart all Cinder services twice, now with the `cinder-manage db sync --bump-versions` command we can avoid the second restart.

.. releasenotes/notes/tpool-size-11121f78df24db39.yaml @ e570436d1cca5cfa89388aec8b2daa63d01d0250

- Fixes concurrency issue on backups, where only 20 native threads could be concurrently be executed.  Now default will be 60, and can be changed with `backup_native_threads_pool_size`.

.. releasenotes/notes/tpool-size-11121f78df24db39.yaml @ e570436d1cca5cfa89388aec8b2daa63d01d0250

- RBD driver can have bottlenecks if too many slow operations are happening at the same time (for example many huge volume deletions), we can now use the `backend_native_threads_pool_size` option in the RBD driver section to resolve the issue.


.. _cinder_13.0.0.0b1_Other Notes:

Other Notes
-----------

.. releasenotes/notes/remove-cinder-manage-logs-cmds-40fb8f475b37fb2f.yaml @ adfda23b609aae482208966e8fd65f176d4bcd49

- The "cinder-manage logs" commands have been removed.  Information
  previously gathered by these commands may be found in cinder service and
  syslog logs.

.. releasenotes/notes/vnx-perf-optimize-bd55dc3ef7584228.yaml @ b54e7ff3576e495c4a1ed95a3e307b897860209b

- Dell EMC VNX driver: Enhances the performance of create/delete volume.

