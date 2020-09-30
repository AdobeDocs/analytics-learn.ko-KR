---
title: Analytics 추적 서버 및 보고서 세트를 식별하는 방법
description: Adobe Analytics을 설정하거나 다른 Experience Cloud 솔루션에서 참조할 때 사용 중인 Analytics "추적 서버" 또는 데이터를 보내는 "보고서 세트"를 알고 있으면 유용하거나 심지어 필요할 수도 있습니다. 이 비디오에서는 Adobe Analytics을 이미 구현했는지 여부와 상관없이 두 값을 찾는 방법을 보여 줍니다.
feature: implementation basics
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2358
translation-type: tm+mt
source-git-commit: 60f4ce4f563a990576b3331b01cd87c29d424f43
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 분석 [!DNL Tracking Server] 및 보고서 [!UICONTROL 세트를 식별하는 방법] {#how-to-identify-your-analytics-tracking-server-and-report-suites}

Adobe Analytics을 설정하거나 다른 Experience Cloud 솔루션에서 참조할 때, 사용 중인 [!DNL Analytics] &quot;[!DNL Tracking Server]&quot; 또는 데이터를 보내는 &quot;[!UICONTROL 보고서 세트]&quot;를 알고 있으면 유용하거나 심지어 필요할 수도 있습니다. 이 비디오에서는 Adobe Analytics을 이미 구현했는지 여부와 상관없이 두 값을 찾는 방법을 보여 줍니다.

## 구현 후 {#after-implementation}

사이트 [!DNL Analytics] 에서 구현한 후 추적 비콘에서 해당 [!DNL tracking server] 및 [!DNL report suite ID] 권한을 찾을 수 있습니다. 이 [!DNL tracking server] 는 비콘의 호스트 이름이므로 쉽게 찾을 수 있습니다. 보고서 세트  ID는 비콘 경로 이름에서 &quot;/b/ss/&quot; 바로 뒤에 있는 쉼표로 구분된 목록입니다.

비콘과 앞으로 오는 기타 모든 정보 [!DNL Analytics] 및 기타 Experience Cloud 솔루션을 보려면 [&quot;Experience Cloud Debugger&quot; 크롬 익스텐션을 설치하십시오](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=en).

## 구현 전 {#before-implementation}

**[!DNL Tracking Server]** - 아직 Adobe Analytics 구현을 시작하지 않은 경우 &quot;.sc.omtrdc.net&quot;의 하위 도메인을 선택합니다 [!DNL tracking server]. 예를 들어 &quot;Jim&#39;s Brims&quot;라는 온라인 모자 가게가 있다고 가정합시다. 간단하게 다음을 설정할 수 [!DNL tracking server] 있습니다.

&quot;jimsbrims.sc.omtrdc.net&quot;.

**[!UICONTROL 보고서 세트]** - 만든 [!UICONTROL 보고서 세트] 목록을 찾으려면 [!DNL Analytics] 관리 [!UICONTROL > 보고서 세트] 에 로그인하여 상위 [!UICONTROL 보고서 세트] 에서 상위 메뉴Facebook에 있는 보고서 세트ID 및 제목을 포함한 상위 보고서 세트 [!UICONTROL 의 목록을 보려면 해당 보고서 세트ID와 제목]을 포함한 보고서 세트 목록을 참조하십시오.

자세한 내용은 아래 비디오를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/26061/?quality=12)
