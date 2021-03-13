```
enable
configure terminal
event manager applet catchall
event cli pattern ".*" sync no skip no
action 1 syslog msg "$_cli_msg"
end
```

or

```
enable
configure terminal
event manager applet catchall
event cli pattern ".*" sync no skip no
action 1.0 syslog msg "$_cli_msg"
action 2.0 file open FH flash:eem_logall.txt a+
action 2.1 file puts FH "$_event_pub_time %HA_EM-6-LOG: catchall: $_cli_msg"
action 2.2 file close FH
end
```
