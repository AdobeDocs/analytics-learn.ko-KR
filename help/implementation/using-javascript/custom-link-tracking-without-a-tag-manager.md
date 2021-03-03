---
title: 태그 관리자 없이 맞춤형 링크 추적
description: '페이지에 있는 많은 작업의 경우, 추적은 페이지 보기로 취급되어서는 안 됩니다. 이 비디오에서는 태그 관리자(예: Experience Platform Launch)을 사용하지 않는 경우, Analytics에 링크 추적 비콘을 코딩하는 방법을 알아봅니다. 코드를 확인하고 중요한 팁을 학습합니다.'
feature: Appmeasurement 구현
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1845
role: '"개발자, 데이터 엔지니어"'
level: 중간
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 8%

---


# 태그 관리자 없이 맞춤형 링크 추적 {#custom-link-tracking-without-a-tag-manager}

페이지에 있는 많은 작업의 경우, 추적은 페이지 보기로 취급되어서는 안 됩니다. 이 비디오에서는 태그 관리자(예: [!DNL Experience Platform Launch] Adobe)을 사용하지 않는 경우 Analytics에 링크 추적 비콘을 코딩하는 방법을 알아봅니다. 코드를 확인하고 중요한 팁을 학습합니다.

## s.tl() 비콘 {#sending-an-s-tl-beacon} 전송

Adobe Analytics으로 데이터를 보내는 기능은 두 가지가 있습니다.

1. s.t() - 페이지 보기 히트를 나타내는 &quot;track&quot; 비콘으로, 지정된 페이지 이름에 대한 페이지 보기를 증가시키고 다른 변수를 설정합니다.
1. s.tl() - 페이지 보기를 증가시키지 않고 pageName 변수를 무시하는 &quot;사용자 지정 링크&quot; 히트/비콘이라고 하는 &quot;추적 링크&quot; 비콘. 이 메서드는 일반적으로 새 페이지/화면을 로드하지 않는 페이지의 작은 작업 또는 새 페이지를 로드하지 않는 다른 작업을 추적하는 데 사용됩니다.

>[!NOTE]
>
>이 비디오에서는 Adobe [!DNL Experience Platform Launch]과 같은 태그 관리자를 사용하지 않을 때 사용자 지정 링크 히트를 코딩하는 방법을 보여줍니다. 구현을 위해 모범 사례 권장 사항인 [!DNL Experience Platform Launch]을 사용하는 것이 좋습니다. 그러나 `s.tl()`에서 코드를 작성해야 하는 경우에는 다음 방법을 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/25832/?quality=12)

## 샘플 코드 {#sample-code}

다음은 비디오의 사용자 지정 링크에 사용되는 샘플 코드입니다.

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

사용자 지정 링크에 대한 자세한 내용은 [설명서](https://marketing.adobe.com/resources/help/ko_KR/sc/implement/function_tl.html)를 참조하십시오.