---
title: "{{ replace .Name "-" " " | title }}"
author: "Hoontaek Lee"
date: {{ now.Format "2006-01-02 15:04:05+09:00" }}
publishdate: {{ now.Format "2006-01-02 15:04:05+09:00" }}
lastmod: {{ now.Format "2006-01-02 15:04:05+09:00" }}
tags:
- {{ now.Format "2006"}}
draft: true
---
