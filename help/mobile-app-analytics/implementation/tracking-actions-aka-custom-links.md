---
title: 'Experience Platform SDK를 사용하는 모바일 앱의 추적 작업(예: 고객 링크)'
description: 액션은 모바일 애플리케이션에서 발생하는 이벤트입니다. 이 비디오에서는 trackAction API를 사용하여 액션을 추적하고 측정하는 방법에 대해 알아봅니다.
feature: Mobile SDK
topics:
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2563
topic: Mobile
role: Developer
level: Experienced
exl-id: 541c51b8-638e-43b4-90ac-0ce94290a141
TQID: 'https://experienceleague.adobe.com/msvft7mQiNGjLqGEezPIbwruvSbsunPGUIFF1q7vlT0'
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
subfeature_v2:
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
    internal-label: Events
  - id: c77ba355-6681-41fe-b719-563d3f507fdb
    internal-label: Mobile SDK
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 3e00cf9416ba2c6886e5a7efb952cac8ce370930
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 73%
---
# Experience Platform SDK를 사용하는 모바일 앱의 추적 작업(예: 고객 링크) {#tracking-actions-aka-custom-links-in-a-mobile-app-with-the-experience-platform-sdk}

액션은 모바일 애플리케이션에서 발생하는 이벤트입니다. 이 비디오에서는 trackAction API를 사용하여 작업을 추적하고 측정하는 방법에 대해 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/328311/?captions=kor&quality=12&learn=on)

사이트의 모든 비화면 로드 작업을 추적하는 데 사용해야 하는 API입니다. 화면이 나타나면 페이지 조회수 히트를 트리거하는 trackState를 사용합니다. 그렇지 않은 경우 trackAction을 사용하여 작업과 관련된 변수를 보냅니다.

이 데이터는 `contextData`(으)로 제공되며, 이는 해당 `contextData` 변수에서 모바일 데이터를 가져와 Adobe Analytics의 [!DNL eVars], [!DNL Props], 이벤트 등으로 매핑하려면 [!UICONTROL 처리 규칙]을(를) 사용해야 함을 의미하기도 합니다.

trackAction에 대한 자세한 내용은 [설명서](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/#track-user-actions-for-adobe-analytics)를 참조하십시오.
