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
role: Developer
level: Experienced
exl-id: 541c51b8-638e-43b4-90ac-0ce94290a141
TQID: https://experienceleague.adobe.com/msvft7mQiNGjLqGEezPIbwruvSbsunPGUIFF1q7vlT0
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2:
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 677e5a22dab92be7ff021c8410525b9091975aef
workflow-type: tm+mt
source-wordcount: 184
ht-degree: 73%

---

# Experience Platform SDK를 사용하는 모바일 앱의 추적 작업(예: 고객 링크) {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

작업은 모바일 앱에서 발생하는 이벤트입니다. 이 비디오에서는 trackAction API를 사용하여 작업을 추적하고 측정하는 방법에 대해 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/26268/?quality=12&learn=on)

사이트의 모든 비화면 로드 작업을 추적하는 데 사용해야 하는 API입니다. 화면이 나타나면 trackState를 사용하여 페이지 뷰의 횟수를 트리거합니다. 그렇지 않은 경우 trackAction을 사용하여 작업과 관련된 변수를 보냅니다.

이 데이터는 `contextData`(으)로 제공되며, 이는 해당 `contextData` 변수에서 모바일 데이터를 가져와 Adobe Analytics의 [!DNL eVars], [!DNL Props], 이벤트 등으로 매핑하려면 [!UICONTROL 처리 규칙]을(를) 사용해야 함을 의미하기도 합니다.

trackAction에 대한 자세한 내용은 [설명서](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/#track-user-actions-for-adobe-analytics)를 참조하십시오.
