---
title: 태그 관리자 없이 사용자 정의 링크 추적
description: 페이지의 많은 작업에서 추적은 페이지 조회수처럼 취급되지 않습니다. 이 비디오에서는 Experience Platform Launch와 같은 태그 관리자를 사용하지 않는 경우 Analytics에 링크 추적 비콘을 코딩하는 방법에 대해 알아봅니다. 코드를 확인하고 중요한 팁을 알아보십시오.
feature: Appmeasurement Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
role: Developer, Data Engineer
level: Intermediate
exl-id: e4567b1c-414e-44ad-982f-52b0150e7eda
source-git-commit: fe861dfd541c1b9cb3b233fa3f56d55054305fd9
workflow-type: ht
source-wordcount: '271'
ht-degree: 100%

---

# 태그 관리자 없이 사용자 정의 링크 추적 {#custom-link-tracking-without-a-tag-manager}

페이지의 많은 작업에서 추적은 페이지 조회수처럼 취급되지 않습니다. 이 비디오에서는 Adobe [!DNL Experience Platform Launch]와 같은 태그 관리자를 사용하지 않는 경우 Analytics에 링크 추적 비콘을 코딩하는 방법에 대해 알아봅니다. 코드를 확인하고 중요한 팁을 알아보십시오.

## s.tl() 비콘 전송 {#sending-an-s-tl-beacon}

Adobe Analytics로 데이터를 전송하는 함수에는 두 가지가 있습니다.

1. s.t() - 지정된 페이지 이름에 대한 페이지 조회수를 증가시키며 기타 변수를 설정하는 페이지 조회수 히트인 “추적” 비콘입니다.
1. s.tl() - “사용자 정의 링크” 히트/비콘이라고도 하며, 페이지 조회수를 증가시키지 않고 pageName 변수를 무시하는 “추적 링크” 비콘입니다. 일반적으로 새 페이지/화면을 로드하지 않는 페이지에서의 소규모 작업 또는 새 페이지를 로드하지 않는 기타 작업을 추적하는 데 사용합니다.

>[!NOTE]
>
>이 비디오에서는 Adobe [!DNL Experience Platform Launch]와 같은 태그 관리자를 사용하지 않는 경우 사용자 정의 링크 히트를 코딩하는 방법에 대해 알아봅니다. 구현을 위해 모범 사례 권장 사항인 [!DNL Experience Platform Launch]를 사용하는 것이 좋습니다. 그러나 `s.tl()`에서 코딩해야 하는 경우 방법은 다음과 같습니다.

>[!VIDEO](https://video.tv.adobe.com/v/25832/?quality=12)

## 샘플 코드 {#sample-code}

다음은 이 비디오에서 사용자 정의 링크에 사용되는 샘플 코드입니다.

```JavaScript
<a href="#" onclick="
    s.linkTrackVars='events,eVar2,prop2';
    s.linkTrackEvents=s.events='event2';
    s.eVar2='facebook share';
    s.prop2='facebook share';
    s.tl(this,'o','Social Share');
    s.manageVars('clearVars',s.linkTrackVars,1);">
    Click here to share on FaceBook
</a>
```
