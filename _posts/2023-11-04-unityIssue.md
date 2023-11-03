---
title: "[Unity] 일관성 없는 액세스 가능성 해결"
author: cho
date: 2023-11-04 01:27:00 +0900
categories: [Develop, Unity]
tags: [unity, c#]
---

# 이슈
매개변수에 enum으로 만든 타입의 건물번호를 전달하려고 하는데 이런 이슈가 발생

![image](https://github.com/soonsoo3595/soonsoo3595.github.io/assets/86000058/c91cc661-8b5c-4a7e-8a87-2c45aed19cd8)

# 해결
바로 enum으로 선언했을 때 public을 안붙였던 실수 
