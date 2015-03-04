# simple-elk-docker

## Goals
* Simple to Grok
* Latest at this time (Kibana4)
* Documented
* Centos 7

## Running
* `fig up`
* Browse to <http://dockerhost:5601/>
* **Note:** Kibana will try to setup your initial index, if there are no logs for it to look at yet you **wont get past the setup page**. See logstash.conf notes below on how to get logs in.

# Config
* **kibana.yml** - changed `elasticsearch` host to the one fig/docker injects into `hosts`

* **logstash.conf** - Simple example, you'd usually run this on a different host or your app to get logs in. You can copy/paste some logs in (since it's listening on `stdin`) or setup one on a different host pointing to your `dockerhost`.

 Again `elasticsearch` hostname is injected by fig/docker to `/etc/hosts`

```
input {
  stdin { }
  file {
    path => "/var/log/yum.log"
    type => "syslog"
  }
 }
output {
  elasticsearch { host => elasticsearch }
  stdout { codec => rubydebug }
}
```
 More info on this logformat here  http://logstash.net/docs/1.4.2/configuration

# Issues/Limitations
- [ ] Kibana 4.0.0 isn't rendering graphs?
 - https://github.com/elasticsearch/kibana/issues/3261
- [ ] No data volumes/persistance, keeping it simple
