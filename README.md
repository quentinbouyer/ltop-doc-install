## ltop-doc-install
<br>
How to build rpms for cerebro : <br>
<br>
Go to https://github.com/chaos/cerebro<br>
<br>
download the cerebro-master.zip (or clone the repo )<br>
unzip it<br>
rename cerebro_master directory to cerebro-1.21<br>
tar zcvf cerebro-1.21.tar.gz cerebro-1.21<br>
copy cerebro-1.21.tar.gz to $HOME_DIRECTORY/rpmbuild/SOURCES<br>
go inside cerebro-1.21 directory<br>
<pre>
sh autogen.sh
rpmbuild -bb cerebro.spec
</pre>
and normally, after the build, you will have all rpms in $HOME_DIRECTORY/rpmbuild/RPMS/x86_64<br>
<br>
How to build rpms for lmt :<br>
<br>
Go to https://github.com/LLNL/lmt<br>
<br>
download the lmt-master.zip ( or clone the repo )<br>
unzip it<br>
rename lmt-master directory to lmt-3.2.10<br>
tar zcvf lmt-3.2.10.tar.gz lmt-3.2.10<br>
copy lmt-3.2.10.tar.gz lmt-3.2.10 to $HOME_DIRECTORY/rpmbuild/SOURCES<br>
go inside lmt-3.2.10 directory<br>
<pre>
sh autogen.sh
rpmbuild -bb lmt.spec
</pre>
and all rpms will be in $HOME_DIRECTORY/rpmbuild/RPMS/X86_64<br>
<br>
Install cerebro and lmt-server-agent on lustre servers<br>
Modifiy /etc/cerebro.conf :<br>
<pre>
cerebro_metric_server ip-address-of-ltop-host
cerebro_event_server ip-address-of-ltop-host
cerebrod_speak on
cerebrod_speak_message_config ip-address-of-ltop-host
cerebrod_listen off
</pre>
<br>
Install cerebro and lmt-server on server where you want to run ltop utility<br>
modify /etc/cerebro.conf :<br>
<pre>
cerebrod_speak on
cerebrod_speak_message_config ip-address-of-ltop-host
cerebrod_listen on
cerebrod_listen_message_config ip-address-of-ltop-host
cerebrod_metric_controller on
cerebrod_metric_server on
cerebrod_event_server on
</pre>
start cerebrod everywhere<br>
