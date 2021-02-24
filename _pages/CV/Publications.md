---
title: Publications
permalink: /CV/Publications.html
layout: single
author_profile: true
toc: true
---
## Journal Articles
{% bibliography --query @article %}

## Refereed Conference Proceedings
{% bibliography --query @inproceedings %}

## Technical Reports and Internal Memos
{% bibliography --query !@article  --query !@inproceedings %}

