# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [0.2.0] - 2018-04-25
### FluentD Tuning
- Modifying to currently working config set.
  Particularly ensuring we are capturing systemd events from journalD as our current distro is
  debian jessie
  
- Removing log sources that do not exist on systemd distros i.e.
  `/var/log/kubelet`.  Mentioned path will only exists on sysV init
  distros.

- Moving to supported K8s addon release of fluentD-elasticsearch

- Increasing slow_flush_log_threshold to prevent the corresponding
  threshold exceeded exception
  
- Increasing buffer chunk and queue limits helps remedy flush failures while
  elasticsearch falls behind during ingestion
  
- Ensuring this pod can tolerate no-schedule taints on master nodes
