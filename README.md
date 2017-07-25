# TA-djbdns for Splunk 

This CIM compliant TA can be used with Splunk Enterprise Security and
provides field extractions, aliases, eventtypes and tags for the following DNS
components by djb:

* tinydns
* axfrdns
* dnscache

It covers the log files from the original djbdns v1.05, or any newer patched
version that uses the djb daemontools for logging.

## Installation

Install this TA on your Splunk (Enterprise Security) search head. 

## Configuration 

Have the log files indexed by a Splunk Universal Forwarder with sourcetypes
`axfrdns`, `tinydns` or `dnscache`. For example with the following inputs.conf:

```
[monitor:///etc/tinydns/log/main/current]
index=dns
sourcetype = tinydns
disabled = 0

[monitor:///etc/dnscache/log/main/current]
index=dns
sourcetype = dnscache
disabled = 0

[monitor:///etc/axfrdns/log/main/current]
index=dns
sourcetype = axfrdns
disabled = 0
```

## CIM 

The TA provides fields compatible with the Splunk Common Information Model (CIM):

* message_type
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

## Support

This is an MIT licensed open source project without warranty of any kind. No
support is provided. A public repository and issue tracker are available at
[https://github.com/jorritfolmer/TA-djbdns](https://github.com/jorritfolmer/TA-djbdns)
