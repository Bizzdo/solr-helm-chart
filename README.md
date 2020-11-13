# About

## Reason for this repo/fork

This repo is forked from lucidworks/solr-helm-chart, mainly because that repo has (as of november 2020) not been updated for almost 2 years, and was lacking some needed features.

## Additions

### Expanded ZK_HOST

The status-page for zookeeper in the "Cloud"-menu requires the full list of all instances to properly report the zookeeper status. This is done by expanding the ZK_HOST from the 'zookeeper-headless' service to a list of all pod instances.

Thanks to `loginvarun`'s suggestion in https://github.com/lucidworks/solr-helm-chart/issues/1#issuecomment-572539721 for a solution.

### Basic Authentication

To enable (advanced) plugins in a Solr collection the Solr Cloud config needs to have (at least) Basic Auth enabled. This is passed on to the solr binary using the -Dbasicauth argument (in cleartext)

And since the readiness and liveness-probes also uses HTTP the auth is added as an HTTP header to those definitions as well.

This feature is enabled using the `basic.auth` setting (in values.yaml)

## Other updates

- default Solr updated to version 8.6.3