<!--
    This Source Code Form is subject to the terms of the Mozilla Public
    License, v. 2.0. If a copy of the MPL was not distributed with this
    file, You can obtain one at http://mozilla.org/MPL/2.0/.
-->

<!--
    Copyright 2021 Joyent, Inc.
    Copyright 2022 MNX Cloud, Inc.
-->

# sdcadm Changelog

## 1.37.0

- TRITON-2304 New image server names

## 1.36.1

- TRITON-2266 cloudapi should be core

## 1.36.0

- TRITON-2228 Linux CN minimum viable product
- TRITON-2214 Z version bump in bind-obj-methods transient dependency broke several builds
- sdcadm#80 platform install --latest should not force linux on users

## 1.35.2

- TRITON-2194 provisionTmpVm should include metadata object

## 1.35.1

- TRITON-2148 Fix the '-s, --server' option for "sdcadm post-setup grafana".

## 1.35.0

- MANTA-5293 add GZ link to 'manta-hotpatch-rebalancer-agent' tool in the
  manta-deployment zone (when updating or deploying the 'manta' service).

## 1.34.0

- MANTA-4811 'sdcadm post-setup manta' now supports migrating from a mantav1
  to a mantav2. See the following for full migration docs:
  https://github.com/joyent/manta/blob/master/docs/operator-guide/mantav2-migration.md

## 1.33.6

- TRITON-2098 Fix a bug where `sdcadm platform` commands no longer worked.

## 1.33.5

- TRITON-2040 Fix a bug where `sdcadm post-setup manta` would not result in
  the created manta0 VM having an external NIC (required for it to function).

## 1.33.4

- TRITON-2039 Fix a bug where `sdcadm up --all` would error out with:

        $ sdcadm up --all -y
        ...
        sdcadm up: error: no "manta" instance was found

  if the DC has a "manta" SAPI service, but not instance of that service.

## 1.33.3

- TRITON-2016 sdcadm insts and sdcadm up fail if the dockerlogger image isn't
  in IMGAPI.

## 1.33.2

- TRITON-2009 EnsureMantaDeploymentGzLinksProcedure() breaks updating setups
  w/o manta instances

## 1.33.1

- MANTA-4817 sdcadm's detection of current mantav from
  $mantaApp.metadata.MANTAV is broken

## 1.33.0

- TRITON-1979, TRITON-1981: Add `sdcadm post-setup manta` to be used to create
  the manta deployment zone. This will become the first step to deploying a
  Manta on Triton (https://joyent.github.io/manta/#deploying-manta) and will
  replace the old `/usbkey/scripts/setup_manta_zone.sh`.

  By default this will create a manta deployment zone suitable for a "mantav2".
  See https://github.com/joyent/manta/blob/master/docs/mantav2.md for details
  on mantav1 vs. mantav2.

## 1.32.0

- TRITON-1980 Add support for multiple valid image names for a service
  and update binder, mahi, moray, and prometheus to support both the
  "manta-" and "mantav2-" prefixed names in preparation of coming mantav2
  images.

## 1.31.0

- TRITON-2001 Improve 'sdcadm up manta' to (re-)create the manta deployment
  symlinks in the GZ (e.g. /opt/smartdc/bin/manta-adm).

## 1.30.4

- TRITON-1991 Internal refactoring of finding an image when adding a service.
  (This drops the undocumented support for specifying the string "default"
  to the `-C, --channel` option of `sdcadm post-setup
  {grafana,logarchiver,kbmapi,firewall-logger-agent,prometheus}`.)

## 1.30.3

- TRITON-1907 output the correct command to install the docker service

## 1.30.2

- TRITON-1696 sdcadm should verify that triton_cns_enabled is set for the admin
  user before deploying prometheus

## 1.30.1

- TRITON-1744 Fix a crash in `sdcadm experimental remove-ca` if a given CNAPI
  server record does not have an "agents" field.
- TRITON-1748 Ensure 'sdcadm experimental remove-ca' does trace logging to file.

## 1.30.0

- TRITON-1319 need firewall-logger agent (`sdcadm post-setup firewall-logger-agent`)

## 1.29.1

- TRITON-1730 Want `sdcadm post-setup common-external-nics` to not prompt for
  confirmation

## 1.29.0

- MANTA-3992 Add `sdcadm post-setup grafana` to setup a core Triton
  Grafana service.
- TRITON-1656 Want new EnsureNicOnServiceInstances procedure in sdcadm

## 1.28.0

- TRITON-1700 update sdcadm to use 64 bit node (18.4)

## 1.27.3

- TRITON-1707 `sdcadm post-setup prometheus` breaks if CNS allow\_transfer
  metadata does not exist yet

## 1.27.2

- TRITON-1706 'sdcadm post-setup dev-sample-data' will now ensure that sample
  images are public.

## 1.27.1

- TRITON-1670 sdcadm AddAllowTransferProcedure uses incorrect parameter name when listing service

## 1.27.0

- TRITON-1625 Have `sdcadm post-setup prometheus` add prometheus zone IP to CNS allow\_transfer list
- TRITON-1624 Change prometheus image name to "manta-prometheus" in sdcadm

## 1.26.0

- MANTA-3552 Add `sdcadm post-setup prometheus` to setup a core Triton
  Prometheus service.

## 1.25.3

- TRITON-1349 Subcommand `sdcadm post-setup kbmapi` using AddServiceProcedure

## 1.25.2

- TRITON-1298 Added `sdcadm post-setup logarchiver`, including new
  "AddServiceProcedure" procedure.
- TRITON-1313 Random missing package failures running `sdcadm create` tests

## 1.25.1

- TRITON-1337 `sdcadm experimental fix-core-vm-resolvers` broken

## 1.25.0

- TRITON-1307 Fix a few commands were broken in the TRITON-1300 change.
- TRITON-1305 Improvements to internal "Procedures" API. Convert
  'sdcadm create'.

## 1.24.9

(Bad release. Upgrade to 1.24.10. See TRITON-1307.)

- TRITON-1300 Start improving CLI output with a `<cli>.ui` interface. So far
  only `sdcadm experimental update-gz-tools` has been updated to use it.

## 1.24.8

- TRITON-1293 Correct the interpretation of whether a server is running from
  a CNAPI server object (CNAPI `<server>.transitional_status` is an
  implementation detail and not relevant for running status. This fixes a
  potential failure in `sdcadm post-setup docker`.

## 1.24.7

- TRITON-1276 sdcadm experimental update-gz-tools --latest --just-download dumps core
- TRITON-1272 sdcadm test failures due to outdated tape version

## 1.24.6

- TRITON-1236 steps.servers.selectServers for convenient -s/-S opt handling,
  add to 'sdcadm ex update-gz-tools'

## 1.24.5

- TRITON-954 sdcadm post-setup common-external-nics should be rack aware

## 1.24.4

- TRITON-1178 sdcadm man page build expects node in $PATH

## 1.24.3

- TRITON-754 lib/sdcadm.js is not admin rack aware
- TRITON-956 sdcadm procedures needs to be rack aware
- TRITON-948 sdcadm check-config shouldnt depend on admin NIC being tagged as "admin"
- TRITON-931 sdcadm admin IP functions need to be factored out
- TRITON-953 sdcadm checkCoreVmInstancesResolvers() needs to be rack aware
- TRITON-1004 sdcadm post-setup docker needs to be rack aware
- TRITON-1063 sdcadm experimental tests need update post TRITON-904

## 1.24.2

- TRITON-1055 sdcadm experimental update-agents with --just-download flag fails on SHA1

## 1.24.1

- TOOLS-2117 sdcnode updates for November 2018 node.js security releases

## 1.24.0

- TRITON-904 Needs some useful enhancements for "sdcadm experimental update-agents".
- TRITON-912 Agentshar update does not check for an ongoing agent update before running another agent installation.

## 1.23.0

- TRITON-889 Improvements to sdcadm's trace logging to file.
- TRITON-990 Change 'sdcadm check-health' and 'sdcadm check-config' to *no
  longer* write a trace log to file.

## 1.22.0

- TRITON-987 fabric setup broken by needless dependency on broken CA

## 1.21.6

- TOOLS-2114 sdcadm treats server as "unavailable" when it doesn't have a transitional_status

## 1.21.5

- TOOLS-2110 sdcadm can crash when SAPI instance has undefined image

## 1.21.4

- TRITON-722 "sdcadm health" still assumes each CN will have an "admin" nictag

## 1.21.3

- TRITON-723 Improve the output of unhealthy instances from `sdcadm health`.

## 1.21.2

- TRITON-619 Manatee upgrades broken due to SAPI not loading data from local
  storage and instead keep trying to download it from moray, with problems due
  to manatee being frozen during updates. This change modifies sdcadm behavior
  to freeze manatee shard only during manatee primary's update and also forces
  SAPI to load data from local storage by removing moray from DNS right after
  freezing the shard, bringing it back as soon as manatee's primary is
  operative again.

## 1.21.1

- TRITON-724 Fix a case where some sdcadm commands can exit with a `0` status
  when there is an error to report.

## 1.21.0

- TRITON-696 sdcadm want info subcommand, adds `sdcadm experimental info`

## 1.20.4

- TRITON-689 improve `sdcadm post-setup cmon` to not require
  `<server>.transitional_status` be defined on CNAPI server records.

## 1.20.3

- TRITON-313 walk back sdcadm steps export sugar

## 1.20.2

- TOOLS-1963 `sdcadm create assets -s NEW-HEADNODE` should work
- TOOLS-1962 `sdcadm create sdc -s NEW-HEADNODE` should work
- TOOLS-1966 `sdcadm create -s dhcpd` should set `dhcpd_server` flag to admin Nic
- TRITON-636 trouble with timeouts in `sdcadm health`

## 1.20.1

- TOOLS-1958 / TOOLS-1959 `sdcadm experimental update-agents` Uses a consistent
  name for the downloaded agents shars and only retains a finite number.

## 1.20.0

- TRITON-574 sdcadm platform assign is broken with rack aware networking

## 1.19.1

- TRITON-572 sdcadm post-setup cloudapi should let sapi determine instance networks

## 1.19.0

- TOOLS-1896 `sdcadm update sapi` could avoid using a temporary instance
- TOOLS-1776 `sdcadm health` can exit 0 when there are service errors
- TRITON-477 `sdcadm create $SVC --image` does not support channels
- TOOLS-1926 `sdcadm health` is stuck and won't exit
- TRITON-417 sdcadm tests implicitly assume dev channel
- TOOLS-1699 `sdcadm health -j` should always provide JSON even on exceptions
- TOOLS-1569 sdcadm missing tests for ha-manatee
- TRITON-458 Remove JSStyle and Javascriptlint from sdcadm
- TRITON-347 `sdcadm exp update-gz-tools --just-download` should not decompress and validate files
- TRITON-395 Drop sdcadm support for manatee v1.0
- TRITON-455 sdcadm experimental doesn't load sdcApp when needed
- TOOLS-1717 sdcadm should not load SDC Application from SAPI when not required
- TOOLS-1345 `sdcadm update manatee` does not update more than one async
- TRITON-398 upgrade sdcadm to use node v6
- TRITON-325 sdcadm still aggressively gives up after updating non-HA moray
- TOOLS-1517 `scdcam check-config` should not complain about missing docker/cns vars in SAPI

## 1.18.0

- TRITON-391 Get rid of sdcadm history

## 1.17.4

- TOOLS-1977 Modify `sdcadm post-setup ha-binder` to move insts to different servers
- TOOLS-1224 `sdcadm <subcommand> -h|--help` hits SAPI to get the sdc app: that's overkill

## 1.17.3

- TRITON-348 Support for using eslint

## 1.17.2

- TOOLS-1387 `sdcadm platform install` should fail early if there's not enough
  free space on the USB.
- TOOLS-2006 `sdcadm platform usage` dumps core.

## 1.17.1

- TOOLS-1579 `sdcadm post-setup ha-binder` should update core zones' resolvers.
- Add `sdcadm experimental fix-core-vm-resolvers` as part of TOOLS-1579.

## 1.17.0

- Add `sdcadm post-setup volapi` to setup a core VOLAPI service.
- Add `sdcadm experimental nfs-volumes` command to enable or disable various
  feature flags related to NFS volumes support for CloudAPI and sdc-docker.

## 1.16.3

- TOOLS-1899 Update to using node v4.

## 1.16.2

- TOOLS-1883 Allow 'sdcadm up manatee' to work correctly with newer MANATEE-346
  changes which include multiple postgres versions.

## 1.16.1

- TOOLS-1842 Fix 'sdcadm create SERVICE-NAME -s SERVER' which was failing
  after TOOLS-1770 changes.

## 1.16.0

- TOOLS-1798 'sdcadm post-setup dev-sample-data' will now add a few sample
  packages for use with KVM instances.

## 1.15.9

- TOOLS-1767 Fix 'sdcadm up' to fail faster if there is a download error
  with on in a number of images.

## 1.15.8

- TOOLS-1634 'sdcadm up' parallel import of images can break when multiple
  images share a new origin image
- TOOLS-1728 sdcadm update for service with multiple instances should skip
  up-to-date ones
- TOOLS-1764 'sdcadm up SERVICE@VERSION' fails for services where the image
  name differs from the service name

## 1.15.7

- TOOLS-1731 'sdcadm post-setup common-external-nics' should set external
  network as primary

## 1.15.6

- TOOLS-1642: Use cueball HttpAgent to connect to Triton HTTP services.
- TOOLS-1704 'sdcadm post-setup cmon' requires CNS being setup

## 1.15.5

- TOOLS-1651 sdcadm create should support agent instances.
- TOOLS-1689 Fix a problem where `sdcadm` would hang on exit for many commands that
  used Ur.

## 1.15.4

- TOOLS-1683 'sdcadm experimental update AGENT' should support updates of
  individual instances.
- TOOLS-1685 make 'sdcadm ex<TAB>' completion work.
- TOOLS-1681 sdcadm experimental update doesn't summarize properly when there
  are several agent updates.
- TOOLS-1644 'sdcadm create portolan' should be used for portolan HA setup.
- TOOLS-1648 sdcadm post-setup cmon should setup cmon-agent.
- TOOLS-1667 Deprecate 'sdcadm experimental cns' in favor of
  'sdcadm post-setup cns'.

## 1.15.3

- Deprecate 'sdcadm experimental add-new-agent-svcs' and roll its functionality
  into 'sdcadm experimental update-other' and 'sdcadm experimental
  update-agent'. This allows the documented upgrade procedure to work
  unchanged, and not hit TOOLS-1665.

## 1.15.2

- TOOLS-1648 sdcadm post-setup cmon should setup cmon-agent
- TOOLS-1662: Fix 'sdcadm experimental add-new-agent-svcs' when adding new
  services.

## 1.15.1

- TOOLS-1574, TOOLS-1631: Fix `sdcadm experimental update AGENT` when there are
  no agent instances or missing service image uuids.
- TOOLS-1633: Fix 'sdcadm up' of the assets zone. It was broken in
  version 1.15.0.

## 1.15.0

- TOOLS-1591: 'sdcadm up' of a number of core Triton services (the simple
  "stateless" ones, e.g. vmapi, napi, papi, etc.) will ensure the instance
  has a delegate dataset if required (if the SAPI service says it should
  have one).

## 1.14.1

- joyent/sdcadm#28 Allow 'sdcadm create portolan --skip-ha-check' to work.

## 1.14.0

- TOOLS-1610 Drop the "-$buildstamp" suffix on the sdcadm image version field
  that was added by TOOLS-1599, because it breaks 'sdcadm self-update
  --latest'.

## 1.13.0

- TOOLS-1610 Bump ver as a workaround to get 'sdcadm self-update --latest'
  working.

## 1.12.0

- TOOLS-1499: add -C channel command line option to sdcadm experimental
  update-gz-tools.

## 1.11.2

- TOOLS-1429 sdcadm update-gz-tools /path/to/file does not work.
- TOOLS-1336 sdcadm should also update USB keys.
- TOOLS-1462: Modify update.md to reflect current update process reality.
- TOOLS-1434: Clearly explain SAPI update impediments and how to proceed.
- TOOLS-1272: Fix incorrect InternalError invocation.
- TOOLS-1414: `sdcadm self-update` reports channel in use.
- TOOLS-1464/TOOLS-1467: Fix regression.
- TOOLS-1464/TOOLS-1467: `--ufds-backup-timeout` opt for `sdcadm up`.
- TOOLS-1425: Added `-C|--channel` option to `sdcadm experimental
  update-agents`.
- TOOLS-1464: Added `--ufds-backup-timeout` option to `sdcadm up` (Set default
  to 10 mins).
- TOOLS-1466: `sdcadm create` validates provided server before printing summary.
- TOOLS-1465: When updating individual instances, check if those are part of HA
  setup.
- TOOLS-1272/TOOLS-1019: Use `sdc-usbkey` when avail. Do not mount/unmount
  usbkey when already mounted.
- TOOLS-1405: Avoid errors emitted by ur client raise TypeError when trying to
  log/print them.
- TOOLS-1405: Prevent history raising "TypeError: Converting circular structure
  to JSON".
- TOOLS-1046: Make clear which API causes errors during `post-setup cloudapi`.
- TOOLS-1384: Check for Ur availability when updating manatee instances not on
  the HN.
- TOOLS-1263/TOOLS-1046: Retry up to 5 times `platform assign|set-default` and
  `post-setup cloudapi` on connection or SDCClient errors.
- TOOLS-1454: `sdcadm health` "quiet" and "json" options should not be mutually
  exclusive (Fixes GH-19).
- TOOLS-1138/TOOLS-1263: Provided detailed information regarding APIs failing
  during booter caches update after platform assignment.
- TOOLS-1138/TOOLS-1263: Avoid false positive updating booter caches after
  platform assignment.
- TOOLS-1430: Added minimal validation of the presence of required files for
  update-gz-tools tarball.
- TOOLS-1439: removed hostvolumes from `update-docker`. Drop `--servers` option.
- TOOLS-1440: removed hostvolume service and hostvolume instances as part of
  `update-other`.
- TOOLS-1441: removed nat setup from `update-docker` (Already into
  `post-setup fabrics`).
- TOOLS-1438: replaced `sdcadm experimental update-docker` with `sdcadm
  post-setup docker` and `sdcadm update docker`. Emit deprecation warning when
  using the former update cmd. Setup `dockerlogger` as part of `sdcadm
  post-setup docker`.
- TOOLS-1381: Use dockerlogger instances created during dockerlogger setup.
  Cleanup legacy CN UUIDs being used by dockerlogger instances before. Add
  server, hostname and server_ip to dockerlogger instance list (same than for
  other agents). Fixed typo which was preventing cabase and cainstsvc to be
  updated through `sdcadm experimental update`.
- TOOLS-1365: `sdcadm platform available` provides feedback when latest platform
  is already installed
- TOOLS-1258: better error feedback for `common-external-nics`

## 1.11.1

- TOOLS-1380: 'sdcadm insts' (and other code paths) crash on gather dockerlogger
  instance info

## 1.11.0

- TOOLS-1359: `sdcadm` no longer logs JSON-formatted bunyan logs to `stderr`,
  preferring instead to emit actionable information formatted for human
  readability.  The log data is still available in `/var/log/sdcadm`.
- TOOLS-1342: `sdcadm` now correctly respects longer execution timeouts
  for agent updates and docker deployments.
- TOOLS-1367: `sdcadm` now connects more reliably to RabbitMQ when
  communicating with remote `ur` agents.
- TOOLS-1335: `sdcadm` will now retry DNS resolution for SAPI updates,
  avoiding one failure mode for any service updated immediately after
  a `binder` update.

## 1.10.0

- TOOLS-1323: Split `sdcadm dc-maint` command into three subcommands due
  to incompatible options for each one of the tasks this command was trying
  to perform: start/stop and display DC maintenance status.
- TOOLS-1326: Do not exit when there's an unknown service in SAPI, just warn
  about it.

## 1.9.2

- TOOLS-1301: sdcadm update cannot call method reprovFailLock_Lock of undefined
- TOOLS-1320: "sdcadm update dockerlogger" failed against multiple CNs
- TOOLS-1318: Added `--message` and `--eta` options to `dc-maint --start`
- TOOLS-1324: Added `--docker-only` and `--cloudapi-only` options to
  `dc-maint --start`.

## 1.9.1

- TOOLS-1311: Updated to latest `cmdln` and `dashdash` for better CLI
  completion.

## 1.9.0

- TOOLS-1298: Support for Underlay NICs provided by aggregations for `sdcadm
  post-setup underlay-nics`
- TOOLS-1219: `sdcadm experimental update dockerlogger` will install/update
  dockerlogger service into setup servers.
- TOOLS-1025: Use newest `manatee-adm` subcommands when possible.

## 1.8.7

- TOOLS-1293: Increase the timeout for the agents install step of `sdcadm
  experimental update-agents` to 20 minutes (from 10).

## 1.8.6

- TOOLS-1223: Set canmount=noauto for `zones/$ZONE_UUID/data/manatee` dataset
  when setting to something else.
- TOOLS-1287: Renamed `sdcadm post-setup zookeeper` to
  `sdcadm post-setup ha-binder` in order to make clear what type of VMs the
  command will create.
- TOOLS-1121: `sdcadm update manatee` doesn't use the "sleep(60)" anymore and,
  instead, uses waitForInstToBeUp properly.
- TOOLS-1289: Improved error messages when sysinfo-refresh fails for one or
  more servers during agents update.
- TOOLS-1076: Fixed help message for `post-setup zookeeper/binder`.
- TOOLS-1191: Fixed PostgreSQL availability check.

## 1.8.5

- TOOLS-905: Move `dc-maint` out of `experimental`. Now should be used just as
  `sdcadm dc-maint [options]`.
- TOOLS-1187: Fixed `sdcadm update manatee` not properly freezing shard for
  updates.

## 1.8.4

- TOOLS-1277: `sdcadm experimental cns` to setup the CNS service and instance,
  and `sdcadm up cns` to update. Note: Eventually this will move to either
  post-setup or being a default created service.

## 1.8.3

- TOOLS-1269: Always force `no_rabit=true` when updating agents

## 1.8.2

- TOOLS-1172: Reject `sdcadm up <unknown svc or inst>` with error msg
- TOOLS-1239: Prevent `sdcadm up <svc>@<UUID of different svc image>`
- TOOLS-1173: Fixed support for `sdcadm up <svc>@<version>`
- TOOLS-1074: Added bash completion

## 1.8.1

- TOOLS-1264/TOOLS-563: Moved sdcadm subcommands to their own files and added
  `sdcadm experimental update` and `scdadm experimental avail` which can handle
  individual updates (and availability) of vm, cn and net agents.
- TOOLS-1252: `sdcadm avail sdcadm` and `sdcadm avail` will now include
  `sdcadm` available images without adding `sdcadm` to SAPI services.
  (This may be modified in the future).

## 1.8.0

- TOOLS-1251: `sdcadm self-update` no longer updates to latest sdcadm available
  image and requires either a given image UUID or `--latest` option to be
  provided.

## 1.7.5

- TOOLS-1246: sdcadm commands would break due to bad sshpk 1.5.0 release

## 1.7.4

- TOOLS-1225 Drop confusing `-x,--exclude SERVERS` options on `sdcadm
  experimental update-agents ...` and `sdcadm platform assign ...`.  Also a
  number of robustness improvements to `sdcadm experimental update-agents`.

## 1.7.3

- TOOLS-1167/TOOLS-1166: sdcadm ex update-agents now updates node.config
  in all CNs, has limited concurrency and agentsshar file download and
  execution are now two separated steps
- TOOLS-1236: 'sdcadm avail' doesn't need to print out channel info
- TOOLS-1234: 'sdcadm post-setup underlay-nics -h' for help doesn't work
- TOOLS-1031: 'sdcadm post-setup underlay-nics' verifies that CNs have the
  configured fabric underlay network tag assigned to any actual nic before
  trying to add them an otherwise useless underlay nic.

## 1.7.2

- Implemented changes from https://github.com/joyent/rfd/tree/master/rfd/0009:
  Replaced `sdcadm experimental fabrics` + `sdcadm experimental portolan` with
  `sdcadm post-setup fabrics`. Dropped support for `--coal` option and added
  documentation about how to setup fabrics in CoaL to SDC's developers guide
  (https://github.com/joyent/sdc/blob/master/docs/developer-guide/coal-post-setup-fabrics.md).
- Get `sdcadm experimental default-fabric` out of experimental, i.e. now is
  `sdcadm default-fabric`.

## 1.7.1

- Deprecated 'latest' symlink for platforms
- Added `sdcadm platform set-default PLATFORM` subcommand
- Include default platform column in `sdcadm platform list`
- Added `sdcadm platform assign --latest`

## 1.7.0

- TOOLS-754: http_proxy support. If your SDC is firewalled of, but you
  have an HTTP proxy that can be used to given `sdcadm` (and IMGAPI)
  external access, then sdcadm can work with that.

        sapiadm update $(sdc-sapi /applications?name=sdc | json -H 0.uuid) \
            metadata.http_proxy=http://my-proxy.example.com:8080

  Then after a minute or two (to allow config-agents to update configurations
  appropriately) you should be able to 'sdcadm up ...' et al via
  that proxy.

  A side-effect of this change is that programmatic usage of "lib/sdcadm.js"
  must explicitly finialize the `SdcAdm` instance:

        var SdcAdm = require('./lib/sdcadm');
        var adm = new SdcAdm({...});
        // ...
        adm.fini();

## 1.6.1

- `sdcadm experimental udpate-agents` now runs its own Ur Queue, instead of
  passing a script to each CN using sdc-oneachnode. Command options have been
  modified accordingly.

## 1.6.0

- Changed the behaviour of `sdcadm update --all --force-rabbitmq` and
  `sdcadm update --all --force-data-path` to allow updating of rabbitmq
  and portolan (currently the sole "data path" service) along with the
  usual `--all` services.
- Allows `sdcadm avail` to show available updates for portolan and rabbitmq.
- Added `sdcadm platform avail`

## 1.5.8

- Added `--force-data-path` option for portolan upgrade

## 1.5.7

- Added `sdcadm avail(able)`.
- Added `sdcadm channel get`
- Added `-x|--exclude` option to `sdcadm update` and `sdcadm avail`.
- Added `-k|--keep-latest` option to `sdcadm platform remove`

## 1.5.6

- Add support for installing custom TLS certificates for sdc-docker with
  `sdcadm experimental install-docker-cert`
- `sdcadm experimental update-docker` now ensures that the zone has
  a delegate dataset

## 1.5.5

- Support full HA for `sdcadm update mahi`.
- TOOLS-913, TOOLS-910, TOOLS-684 A number of fixes to properly support pulling
  and updating from channels other than the default.

## 1.5.4

- Add `sdcadm experimental default-fabric <UUID>` for adding a default fabric
for a user

## 1.5.3

- `sdcadm experimental fabrics` now requires the `sdc_nat_pool` property in
its config for configuring the fabric NAT network pool.

## 1.5.2

- Added `--force` and `--yes` option to `sdcadm experimental update-agents`.
- Added ability to continue from a previously failed run to
`post-setup ha-manatee`.

## 1.5.1

- Added `sdcadm channel` to retrieve available update channels and
set/unset `updates_channel` into SAPI.

## 1.5.0

- Added `sdcadm experimental fabric` to initialize the SDC fabrics
sub-system.

## 1.4.5
- Added `sdcadm platform`. Moved `sdcadm experimental assign-platform` and
`sdcadm experimental install-platform` under `sdcadm platform` command as
`assign` and `install`. Also added `list`, `usage` and `remove` subcommands.

## 1.4.4

- Modified `sdcadm post-setup zookeeper` to use binder images instead of
zookeeper images.
- Added `sdcadm rollback`

## 1.4.3

- Added DNS to docker and portolan instances.
- Stop lying regarding image used for ha-manatee.
- Added `--just-download` option to `sdcadm experimental update-gz-tools`
and `sdcadm experimental update-agents`.

## 1.4.2

- Added `sdcadm experimental portolan` to add/update the portolan service.
- Everything `sdcadm experimental` added to `sdcadm history`.

## 1.4.1

- Added `sdcadm create <service> --server=<UUID> [--image=<UUID>]`.
- Moved `sdcadm experimental add-2nd-manatee` to `sdcadm post-setup ha-manatee`
and include creation of 3rd manatee instance as part of it.

## 1.4.0
- Add `sdcadm post-setup zookeeper` to create the zookeeper service and add a
cluster of zookeeper instances.
- Added `sdcadm update zookeeper`.
- Added a warning for users when an image download fails due to the lack of
external nic for IMGAPI
- Save `self-update` changes into history.
- Save history into SAPI when available.

## 1.3.9

- Add `sdcadm experimental update-docker` to add/update the docker service &&
  docker0 instance.
- Added post-setup commands, `cloudapi`, `common-external-nics`

## 1.3.8

- Add `sdcadm experimental install-platform` and `sdcadm experimental assign-platform`

## 1.3.7

- Add `sdcadm check-health` as an eventual replacement for `sdc-healthcheck`.

## 1.3.6

- Add `sdcadm experimental add-new-agent-svcs`.
- Support full HA for `sdcadm update moray`.

## 1.3.5

- Add `sdcadm update mahi` with support for creating a delegate dataset
- Add `sdcadm update binder`
- Add `sdcadm experimental update-gz-tools` to be able to update global zone
  tools
- Add `sdcadm update manatee` both, for HA setups and single dev VM.
- Add `sdcadm experimental add-2nd-manatee --server=<UUID>` to create the
second manatee VM for HA.

## 1.3.4

- Add `sdcadm experimental update-agents` to be able to update agents

## 1.3.3

- Add --all flag for updating all available services at once.
- Add `sdcadm update sapi`, limited to a single instance on the headnode.
- Add `sdcadm update moray`, limited to a single instance on the headnode.
- Add `sdcadm update ufds`, limited to a single instance on the headnode.

## 1.3.2

- Add `sdcadm update --force-same-image ...` to be able to for an
  update/reprovision of an instance using the same image. Usually that
  would be a no-op.

- `sdcadm update` can now update imgapi, limited to a single imgapi
  instance on the headnode.

- Add `sdcadm experimental update-other` temporary grabbag of SDC update
  steps.

## 1.3.1

- Add `sdcadm experimental dc-maint` for starting and stopping DC maintenance
  mode (i.e. putting cloudapi in readonly mode).

## 1.3.0

- Add --force-rabbitmq flag and prevent updating of RabbitMQ if flag not used.

## 1.2.5

- TOOLS-582 correct bug in self-update that would break when multiple build
  branches were available.

- TOOLS-581 a self-update that finds no updates should not create a
  /var/sdcadm/self-updates dir

## 1.2.4

- Add 'sdcadm check-config'.

- Add 'sdcadm experimental ...'  where experimental commands will hang
  until fully integrated into the planned upgrade process.

## 1.2.3

- Save old user-script to 'sdcadm update' work dir for possible rollback.


## 1.2.2

- `config.vmMinPlatform` guard for minimum platform supported for core
  VM updates.
- `sdcadm svcs` lists one service per row, JSON is mostly from SAPI's
  ListServices.
- `sdcadm insts -I` to group by (service, image) unique pairs


## 1.2.1

- 'sdcadm update' will correctly do nothing (saying "Up-to-date") if the given
  services are already at the latest candidate image. It also now properly
  excludes images published earlier than the currently used image as update
  candidates.
- 'sdcadm update <svc>@<version>' and other calling forms

## 1.2.0

- Change shar self-installer input envvar from SDCADM_LOGDIR to SDCADM_WRKDIR.
- 'sdcadm update -I ...'

## 1.1.0

- First stab at `sdcadm update SERVICE`. Currently limited to most of the
  stateless services (e.g. vmapi, cnapi) with just a single instance, and only
  on the headnode.

## 1.0.4

- TOOLS-437: `sdcadm instances`, `sdcadm services`.

## 1.0.3

- TOOLS-436: `sdcadm self-update`

## 1.0.0

First version.
