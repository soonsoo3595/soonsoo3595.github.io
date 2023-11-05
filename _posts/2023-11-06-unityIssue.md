---
title: "[Unity3D] Character Controller 컴포넌트가 있는 오브젝트의 Position 변경"
author: cho
date: 2023-11-06 00:19:00 +0900
categories: [Develop, Unity]
tags: [unity, c#, unity3D]
---

# 이슈
플레이어로 쓰고 있는 오브젝트를 순간이동시키기위해 position의 값을 바꾸려고 했는데  
`gameobject.transform.positon = 이동하고자 하는 곳` 의 코드가 전혀 먹지 않음. Debug.Log로 이동한 후의 transform을 비교해도 이동은 했다고 뜨는데 게임 상에선 전혀 움직이지 않음을 확인  
이유를 찾다가 프로젝트에서는 플레이어 오브젝트에 Character Controller라는 컴포넌트를 사용해 사용자의 입력을 받아 플레이어를 컨트롤하는데 이 컴포넌트 때문인것같아 구글링을 해보기로 함.  
구글링을 해보니 외국 개발자들에게서 나와 비슷한 문제를 많이 볼 수 있었고 도중 유니티 포럼에서 질문을 보게 되었다 -> [사이트](https://forum.unity.com/threads/does-transform-position-work-on-a-charactercontroller.36149/)  

![image](https://github.com/soonsoo3595/soonsoo3595.github.io/assets/86000058/f37bf36c-59d7-460e-8337-559c0d5cd705)

# 해결
정확한 이유는 잘 모르겠으나 아무튼 Character Controller가 문제인게 맞았고 텔레포트 시키기 전 비활성화시키고 텔레포트 후 활성화시키니까 정상적으로 텔레포트가 되었다.
