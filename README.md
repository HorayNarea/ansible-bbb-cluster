small scale BBB cluster
=======================

This is an ansible playbook for a small scale [BigBlueButton](https://bigbluebutton.org) cluster. 

Notes:
* BBB and the hosts are monitored with [prometheus node-exporter](https://github.com/prometheus/node_exporter) and [greenstatics bigbluebutton-exporter](https://github.com/greenstatic/bigbluebutton-exporter)
* TURN is handled seperately, because we have it on an own VM listening on Port 443 (breaking firewalls and stuff)
* Configuring BBB instances into the loadbalancer happens [manually](https://github.com/blindsidenetworks/scalelite#administration)
* Access is provided with [bbb-easy-join](https://github.com/stadtulm/bbb-easy-join), so people can use it without registration

If you need a bigger, more featured BBB cluster with greenlight, wiki and rocketchat for support etc., look into [stadtulm/a13-ansible](https://github.com/stadtulm/a13-ansible).

If you want to enable telephony call-in, place files named like your bbb hosts into `host_vars` and add following content:
```
---
bbb_dialin_enabled: yes
bbb_dialin_provider_proxy: "sip.example"
bbb_dialin_provider_username: "example12345"
bbb_dialin_provider_password: "example12345"
bbb_dialin_provider_extension: "80012345678"
bbb_dialin_default_number: "+4980012345678"
```
