---
title: 'Experience Platform SDK를 사용하는 모바일 앱의 추적 작업(예: 고객 링크)'
description: 작업은 모바일 앱에서 발생하는 이벤트입니다. 이 비디오에서는 trackAction API를 사용하여 작업을 추적하고 측정하는 방법에 대해 알아봅니다.
feature: Mobile SDK
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
topic: Mobile
role: Developer, Data Engineer
level: Experienced
exl-id: 541c51b8-638e-43b4-90ac-0ce94290a141
source-git-commit: 8fc641743bc9e07b838a22ca64ccc15344d52764
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 100%

---

# Experience Platform SDK를 사용하는 모바일 앱의 추적 작업(예: 고객 링크) {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

작업은 모바일 앱에서 발생하는 이벤트입니다. 이 비디오에서는 trackAction API를 사용하여 작업을 추적하고 측정하는 방법에 대해 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12&learn=on)

사이트의 모든 비화면 로드 작업을 추적하는 데 사용해야 하는 API입니다. 화면이 나타나면 trackState를 사용하여 페이지 뷰의 횟수를 트리거합니다. 그렇지 않은 경우 trackAction을 사용하여 작업과 관련된 변수를 보냅니다.

이 데이터는 `contextData`로 제공되며 [!UICONTROL 처리 규칙]을 사용하여 해당 `contextData` 변수에서 모바일 데이터를 가져와 [!DNL eVars], [!DNL Props], 이벤트 등으로 매핑해야 한다는 것을 의미하기도 합니다. Adobe Analytics에서.

trackAction에 대한 자세한 내용은 [설명서](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration-reference/mobile-core-api-reference)를 참조하십시오.
