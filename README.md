web_log
=============
## Description ##

This script allows to setup web access to log dir and stream log files via http.

This script just usage example of [clj-stream-sh](https://github.com/mshytikov/clj-stream-sh)
but perhaps somebody may find it useful for some purposes.

### Env requirements ###

1. [rvm](https://rvm.io/)
2. ruby, java
3. nginx (1.3.9+)

But you can do any part of configuration manualy.
 

### Instalaton ###

```
$ git clone https://github.com/mshytikov/web_log.git
$ cd web_log
$ bundle install
$ rake install log_dir=/var/log/nginx

```

Note: your user should have read permission in pecified log dir (/var/logs/nginx in example)
And you need to wait few seconds(= jvm startup time),  after installation

### Usage ###

If everything configured properly. yuo should be able to see los files

in console ``` $ curl http://127.0.0.1:8135/logs ```

or in browser http://<host_name>:8135/logs


And stream any of listed files
in console ``` $ curl http://127.0.0.1:8135/logs/access.log ```

or in browser http://<host_name>:8135/logs/access.log

### Start/Stop ###

[foreman](https://github.com/ddollar/foreman) is used to export to upstar
that's why start/stop is simple:
```
$ sudo stop  web_log
$ sudo start web_log
```


