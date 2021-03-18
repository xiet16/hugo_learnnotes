---
title: "ElasticSearch"
date: 2021-03-18T09:29:52+08:00
draft: true
---

1、ElasticSearch 规范:



2、ElasticSearch 踩过的坑:

(1)es中展示的是北京时间,存的时间是utc时间

"script": { "source": " return (new Date().getTime() - doc['ArrivalDate'].value.toInstant().toEpochMilli() + 28800000) " }

(2)es中distinc 是不准的

"cardinality": {"precision_threshold": 100000,"field": "Single_NO"}

