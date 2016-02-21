# Splunk TA for djbdns

This CIM compliant Splunk TA can be used with Splunk Enterprise Security and
provides field extractions, aliases, eventtypes and tags for the following DNS
components by djb:

* tinydns
* axfrdns
* dnscache

It covers the log files from the original djbdns v1.05, or any newer patched
version that uses the djb daemontools for logging.

## Installation

Install this Splunk TA on your Splunk (Enterprise Security) search head. Make
sure to rename it Splunk_TA_djbdns otherwise ES won't eat it.

## Configuration 

Have the log files indexed by a Splunk Universal Forwarder with sourcetypes
`axfrdns`, `tinydns` or `dnscache`.

## CIM 

The TA provides fields compatible with the Splunk Common Information Model (CIM):

* src_ip
* src_port
* transport (not available for dnscache)
* transaction_id
* query_type
* query
* reply_code
* reply_code_id

And the following non CIM-compliant field:

* resource_record

