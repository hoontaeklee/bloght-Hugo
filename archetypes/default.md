---
title: "{{ replace .Name "-" " " | title }}"
author: "Hoontaek Lee"
date: {{ now.Format "2006-01-02 11:11:00+09:00" }}
publishdate: {{ .Date }}
lastmod: {{ .Date }}
tags:
- {{ now.Format "2006"}}
draft: true
---
