---
emoji: 1️⃣
title: 머스테치(Mustache) 사용법 및 문법
date: '2022-06-12 12:20:00'
author: 박재만
tags: Spring-boot
categories: JAVA
---

## 1. 머스테치 사용
* 기본적인 파일위치는 src/main/resources/templates
* 확장자는 .mustache

## 2. 머스테치 문법
```
{{>layout/header}}
    <h1>spring boot</h1>
{{>layout/footer}}
```
* {{>layout/header}}
    * 현재 머스테치 파일을 기준으로 다른 파일을 가져옴
    * include라고 생각하면 됨

