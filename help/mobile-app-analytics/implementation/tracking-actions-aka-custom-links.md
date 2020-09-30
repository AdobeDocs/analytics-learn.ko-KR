---
title: Experience Platform SDK를 사용한 모바일 앱의 추적 작업(AKA 사용자 지정 링크)
description: '작업은 모바일 앱에서 발생하는 이벤트입니다. 이 비디오에서는 trackAction API를 사용하여 동작을 추적하고 측정하는 방법을 알아봅니다. '
feature: mobile sdk
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
translation-type: tm+mt
source-git-commit: a42658cfd4bae7b077ddd48b4cf5c7db54e35c98
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Experience Platform SDK를 사용한 모바일 앱의 추적 작업(AKA 사용자 지정 링크) {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

작업은 모바일 앱에서 발생하는 이벤트입니다. 이 비디오에서는 trackAction API를 사용하여 동작을 추적하고 측정하는 방법을 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12)

이 API는 사이트에서 모든 비스크린 로드 작업을 추적하는 데 사용해야 합니다. 화면이 나타나면 페이지 보기 히트를 트리거하는 trackState를 사용합니다. 그렇지 않으면 trackAction을 사용하여 수행되는 작업과 관련된 변수를 전송합니다.

이 데이터 `contextData`는 [!UICONTROL 처리 규칙] 을 사용하여 해당 `contextData` 변수의 모바일 데이터를 가져와서 [!DNL eVars], [!DNL Props]이벤트 등에 매핑해야 합니다. 방문자 우편 번호.

trackAction에 대한 자세한 내용은 [설명서를 참조하십시오](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration-reference/mobile-core-api-reference).
