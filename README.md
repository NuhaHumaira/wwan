# Example

### Network /etc/config/network
<pre>
  <code>
  config interface 'wwan'
	option proto 'quectel'
	option auth 'none'
	option delay '5'
	option mtu '1500'
	option pdptype 'ipv4v6'
	option device '/dev/cdc-wdm0'
	option apn 'internet'
	list dns '1.1.1.1'
	list dns '1.0.0.1'

config interface 'wwan_4'
	option proto 'dhcp'
	option peerdns '1'
	option defaultroute '1'
	option metric '10'
	option device 'wwan0_1'

config interface 'wwan_6'
	option proto 'dhcpv6'
	option reqaddress 'try'
	option reqprefix 'auto'
	option peerdns '1'
	option defaultroute '1'
	option metric '20'
	option device 'wwan0_1'
  </code>
</pre>

### Firewall etc/config/firewall
<pre>
  <code>
config zone
	option name 'wan'
	list network 'wwan'
        list network 'wwan_4'
        list network 'wwan_6'
	option input 'REJECT'
	option output 'ACCEPT'
	option forward 'REJECT'
	option masq '1'
	option mtu_fix '1'
  </code>
</pre>
