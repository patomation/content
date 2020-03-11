---
templateKey: blog-post
title: Linux Command Line Cheat Sheet Notes
date: 2020-03-11T15:04:10.000Z
featuredpost: false
featuredimage: /img/flavor_wheel.jpg
description: 
tags:
  - ubuntu
  - linux
  - command line
  - cheat sheet
---

### Check disk space
```df -h```
### Check disk space usage by folder
```sudo du -hsx /* | sort -rh | head -n 40```
### view the end of a log file
```tail -n 100 /var/log/syslog```
### Clearing a log file without deleting it
```truncate -s 0 /var/log/syslog```