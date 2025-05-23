# Change log

## 9.2.4.0 (2021-09-06)

* Updated to MQ version 9.2.4.0

## 9.2.3.0 (2021-07-22)

* Updated to MQ version 9.2.3.0

## 9.2.2.0 (2021-03-26)

* Updated to MQ version 9.2.2.0

## 9.2.1.0 (2020-02-18)

* Updated to MQ version 9.2.1.0


## 9.2.0.1-LTS (2020-12-04)

* Added support for MQ Long Term Support (production licensed only) in the mq-container

## 9.2.0.0 (2020-07-23)

* Updated to [MQ version 9.2.0.0](https://www.ibm.com/support/knowledgecenter/SSFKSJ_9.2.0/com.ibm.mq.pro.doc/q113110_.htm)
* Use `-ic` arguments with `crtmqm` to process MQSC files in `/etc/mqm`. Replaces previous use of "runmqsc" commands

## 9.1.5.0 (2020-04-02)

* Updated to MQ version 9.1.5.0
* Can now run as a random user, instead of the "mqm" user, which has now been removed. This adds compatability for the [Red Hat OpenShift restricted SCC](https://docs.openshift.com/container-platform/4.3/authentication/managing-security-context-constraints.html#security-context-constraints-about_configuring-internal-oauth). The default image UID is `1001`.

## 9.1.4.0 (2019-12-06)

* Updated to MQ version 9.1.4.0
* Updated to use UBI8 as base image
* Added required security settings to self signed certificates to align with macOS Catalina requirements

## 9.1.3.0 (2019-07-19)

* Updated to MQ version 9.1.3.0
* Allow generation of TLS certificate with given hostname
* Fixes for the following issues:
  * `MQ_EPHEMERAL_PREFIX` UNIX sockets fix
  * Fix Makefile for Windows
  * Use -a option on crtmqdir
  * Remove check for certificate environment variable

## 9.1.2.0-UBI (2019-06-21)

**Breaking changes**:
* UID of the mqm user is now 888.  You need to run the container with an entrypoint of `runmqserver -i` under the root user to update any existing files.
* MQSC files supplied will be verified before being run. Files containing invalid MQSC will cause the container to fail to start

**Other changes**:
* Security fixes
* Web console added to production image
* Container built on RedHat host

## 9.1.2.0 (2019-03-21)

* Updated to MQ version 9.1.2.0
* Now runs using the "mqm" user instead of root.  See new [security doc](https://github.com/ibm-messaging/mq-container/blob/master/docs/security.md)
* New [IGNSTATE](https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_9.1.0/com.ibm.mq.pro.doc/q132310_.htm#q132310___ignstateparm) parameter used in default developer config
* Termination log moved from `/dev/termination-log` to `/run/termination-log`, to make permissions easier to handle
* Fixes for the following issues:
    * Brackets no longer appear in termination log
    * Test timeouts weren't being used correctly
    * Building on subscribed and unsubscribed hosts ([#273](https://github.com/ibm-messaging/mq-container/pull/273))
    * Gosec failures ([#286](https://github.com/ibm-messaging/mq-container/pull/286))
    * Security fix for perl-base ([#253](https://github.com/ibm-messaging/mq-container/pull/253))

## 9.1.1.0 (2018-11-30)

* Updated to MQ version 9.1.1.0
* Created seperate RedHat Makefile for building images on RedHat machines with buildah
* Enabled REST messaging capability for app user.
* Added support for container supplementary groups
* Removed IBM MQ version 9.0.5 details.
* Added additional Diagnostics ([#203](https://github.com/ibm-messaging/mq-container/pull/203))
* Implementted GOSec to perform code scans for security vulnerabilities. (([#227](https://github.com/ibm-messaging/mq-container/pull/227)))
* Removed Queue manager create option from the MQ Console.
* Fixes for the following issues:
    * Check explicitly for `/mnt/mqm` ([#175](https://github.com/ibm-messaging/mq-container/pull/175))
    * Force string output in chkmqhealthy ([#174](https://github.com/ibm-messaging/mq-container/pull/174))
    * Use -aG not -G when adding a group for a user
    * Security fixes for libsystemd0 systemd systemd-sysv & libudev1

## 9.1.0.0 (2018-07-23)

* Updated to MQ version 9.1.0.0
* Added Docker 1.12 tests
* Added MQ SDK Docker image sample
* Added MQ Golang SDK Docker image sample
* Added Prometheus metric gathering implementation
* Added MQ Internet Pass-Thru (MS81) Docker image sample
* Added POWER & z/Linux image builds
* `devjmstest` image now built with Maven instead of gradle
* Added FAT manifests for Docker Hub/Docker Store
* Added Red Hat Enterprise Linux image build
* Added basic versioning debug information into golang programs
* Removed 9.0.4

## 9.0.5.0 (2018-03-13)

* Updated to MQ version 9.0.5.0
* Container's stdout can now be set to JSON format (set LOG_FORMAT=json)
* MQ error logs (in JSON or plain text) are now mirrored on stdout for the container.
* `chkmqready` now waits until MQSC scripts in `/etc/mqm` have been applied
* `chkmqready` and `chkmqhealthy` now run as the "mqm" user
* Added ability to optionally use an alternative base image
* Various build and test improvements
* Removed 9.0.3

## 9.0.4 (2017-11-06)

* Updated to MQ version 9.0.4.0
* Updated to Go version 9
* Removed packages `curl`, `ca-certificates`, and their dependencies, which were only used at build time
* Improved logging
* Helm charts now work on Kubernetes V1.6
* Production Helm chart now includes a default image repository and tag
* Updated to use multi-stage Docker build, so that Go code is built inside a container

## 9.0.3 (2017-10-17)

* Initial version
