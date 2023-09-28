Version 23.0 LTS Releases
=========================

These are Long Term Support (LTS) versions of HTCondor. As usual, only bug fixes
(and potentially, ports to new platforms) will be provided in future
23.0.y versions. New features will be added in the 23.x.y feature versions.

.. warning::
    The configuration macros JOB_ROUTER_DEFAULTS, JOB_ROUTER_ENTRIES, JOB_ROUTER_ENTRIES_CMD,
    and JOB_ROUTER_ENTRIES_FILE are deprecated and will be removed for V24 of HTCondor. New
    configuration syntax for the job router is defined using JOB_ROUTER_ROUTE_NAMES and
    JOB_ROUTER_ROUTE_<name>. Note: The removal will occur during the lifetime of the
    HTCondor V23 feature series.
    :jira:`1968`

The details of each version are described below.

.. _lts-version-history-2301:

Version 23.0.1
--------------

Release Notes:

.. HTCondor version 23.0.1 released on Month Date, 2023.

- HTCondor version 23.0.1 not yet released.

New Features:

- None.

Bugs Fixed:

- None.

.. _lts-version-history-2300:

Version 23.0.0
--------------

Release Notes:

- HTCondor version 23.0.0 released on September 29, 2023.

New Features:

- A *condor_startd* without any slot types defined will now default to a single partitionable slot rather
  than a number of static slots equal to the number of cores as it was in previous versions.
  The configuration template ``use FEATURE : StaticSlots`` was added for admins wanting the old behavior.
  :jira:`2026`

- The ``TargetType`` attribute is no longer a required attribute in most Classads.  It is still used for
  queries to the *condor_collector* and it remains in the Job ClassAd and the Machine ClassAd because
  of older versions of HTCondor.require it to be present.
  :jira:`1997`

- The ``-dry-run`` option of *condor_submit* will now print the output of a ``SEC_CREDENTIAL_STORER`` script.
  This can be useful when developing such a script.
  :jira:`2014`

- Added ability to query epoch history records from the python bindings.
  :jira:`2036`

- The default value of :macro:`SEC_DEFAULT_AUTHENTICATION_METHODS` will now be visible
  in *condor_config_val*. The default for :macro:`SEC_*_AUTHENTICATION_METHODS`
  will inherit from this value, and thus no ``READ`` and ``CLIENT`` will no longer
  automatically have ``CLAIMTOBE``.
  :jira:`2047`

- Added new tool *condor_test_token*, which will create a SciToken
  with configurable contents (including issuer) which will be accepted
  for a short period of time by the local HTCondor daemons.
  :jira:`1115`

Bugs Fixed:

- Fixed a bug that would cause the *condor_startd* to crash in rare cases
  when jobs go on hold
  :jira:`2016`

- Fixed a bug where if a user-level checkpoint could not be transferred from
  the starter to the AP, the job would go on hold.  Now it will retry, or
  go back to idle.
  :jira:`2034`

- Fixed a bug where the *CommittedTime* attribute was not set correctly
  for Docker Universe jobs doing user level check-pointing.
  :jira:`2014`

- Fixed a bug where *condor_preen* was deleting files named '*OfflineAds*'
  in the spool directory.
  :jira:`2019`

- Fixed a bug where the *blahpd* would incorrectly believe that an LSF
  batch scheduler was not working.
  :jira:`2003`

- Fixed the Execution Point's detection of whether libvirt is working
  properly for the VM universe.
  :jira:`2009`

- Fixed a bug where container universe did not work for late materialization jobs
  submitted to the *condor_schedd*
  :jira:`2031`

- Fixed a bug where the *condor_startd* could crash if a new match is
  made at the end a drain request.
  :jira:`2032`
