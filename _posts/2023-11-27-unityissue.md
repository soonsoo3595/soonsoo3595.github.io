---
title: "[Unity] 엥 TextMeshPro 폰트 컬러가 이상하게 보여요"
author: cho
date: 2023-11-27 01:36:00 +0900
categories: [Develop, Unity]
tags: [unity, c#, textmeshpro]
---

# 이슈
현재 진행중인 새싹의 마법사 프로젝트에서 게임 오버 팝업인 UI 작업 도중 아트에서 넘겨준 가이드대로 폰트와 컬러를 적용하고 있었는데 아무리 적용해봐도 원래 색깔과 프로젝트에 적용한 색깔이 전혀 다르게 보이는 것이었다.  
![image](https://github.com/soonsoo3595/soonsoo3595.github.io/assets/86000058/49bae9d1-07c9-4cb7-997c-afca9557883a)  
그림에서 보이듯이 아래의 Gold와 1200G는 놀랍게도 같은 컬러코드이다(ㄷㄷ)  
이상하다 싶어 TextMeshPro가 아닌 Text로 색을 적용했을 때는 정상적으로 적용이 됐다.  
그리고 프로젝트 설정에서 Color space를 Linear가 아닌 Gamma로 바꾸었을 때도 제대로 작동했다. 여기서 어찌 됐던 Gamma 쪽에서 문제가 있는 것을 알 수 있어서 해당 이슈를 다루고 있는 블로그 글을 찾았다. 지금은 일단 개발해야 하니 여기에 글만 참고해두고 나중에 읽어보자. 관련 이슈 글이 굉장히 많았다.
https://m.blog.naver.com/cdw0424/221827528747  

# 해결
어쩌다보니 우리 프로젝트에서는 렌더러 모드가 Screen Space - Camera인 캔버스와 World Space인 캔버스 두 개를 쓰고 UI 작업을 World Space에서 하고 있었는데 전자 캔버스에서 TextmeshPro를 넣어보니 색깔이 잘 나오는 것을 볼 수 있었다.  
이게 World Space라 문제인가? 했는데 Canvas 컴포넌트를 비교해보니 다른 점이 하나 있었다.
![image](https://github.com/soonsoo3595/soonsoo3595.github.io/assets/86000058/47810054-e4a5-4108-ad8a-426aa2a26e9f)
![image](https://github.com/soonsoo3595/soonsoo3595.github.io/assets/86000058/4c9603b6-1412-4af9-9651-ac856f38acd5)  
바로 맨 아래에 있는 Vertex Color Always In Gamma Color Space의 체크 유무이다. 체크를 푸니까 색이 제대로 돌아온 것을 볼 수 있었다.  
![image](https://github.com/soonsoo3595/soonsoo3595.github.io/assets/86000058/d2b7ecb8-413b-48bc-a5fb-640ab6a133d9)  
옵션을 찾아보니 자료가 거의 없지만 간단하게 "https://docs.unity3d.com/ScriptReference/Canvas-vertexColorAlwaysGammaSpace.html"가 있었다. 솔직히 잘 모르겠다,, 쉐이더 관련인것 같은데,,  
일단 해결했으니 됐다.



