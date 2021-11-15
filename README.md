#!/bin/bash

systemctl stop nessusd.service
rm -rf /opt/nessus/var/nessus/plugins-code.db* 2&>/dev/null rm -rf  /opt/nessus/var/nessus/plugins-desc.db* 2&>/dev/null rm -rf  /opt/nessus/var/nessus/plugins-attributes.db 2&>/dev/null rm -rf  /opt/nessus/var/nessus/services* 2&>/dev/null /opt/nessus/sbin/nessuscli update  $1 sed -i 's/"HomeFeed (Non-commercial use only)"/"ProfessionalFeed (Direct)"/g' /opt/nessus/var/nessus/plugin_feed_info.inc
sed -i 's/"HomeFeed (Non-commercial use only)"/"ProfessionalFeed (Direct)"/g' /opt/nessus/lib/nessus/plugins/plugin_feed_info.inc
systemctl start nessusd.service
