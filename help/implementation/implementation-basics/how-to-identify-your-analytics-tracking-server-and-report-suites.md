---
title: 분석 추적 서버 및 보고서 세트 ID를 식별하는 방법
description: Adobe Analytics를 설정하거나 다른 Experience Cloud 솔루션에서 참조할 때 사용 중인 Analytics “추적 서버” 또는 데이터를 보내는 “보고서 세트”를 아는 것이 도움이 되거나 필요한 경우가 많습니다. 이 비디오에서는 Adobe Analytics를 이미 구현했는지 여부에 관계없이 두 값을 모두 찾는 방법을 보여 줍니다.
feature: Implementation Basics
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2358
role: Developer, Data Engineer
level: Beginner
exl-id: 3925026f-69f1-4425-b3a9-6fef26375fed
source-git-commit: 42bf16df9585d1f41206b81bf509a72c10f1d7f2
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 100%

---

# 분석 [!DNL tracking server] 및 [!UICONTROL 보고서 세트 ID]를 식별하는 방법 {#how-to-identify-your-analytics-tracking-server-and-report-suites}

Adobe Analytics를 설정하거나 다른 Experience Cloud 솔루션에서 참조할 때 사용 중인 Analytics “추적 서버” 또는 데이터를 보내는 “[!UICONTROL 보고서 세트]”를 아는 것이 도움이 되거나 필요한 경우가 많습니다. 이 비디오에서는 Adobe Analytics를 이미 구현했는지 여부에 관계없이 두 값을 모두 찾는 방법을 보여 줍니다.

>[!IMPORTANT]
>
>이 문서와 비디오는 Web SDK를 사용한 구현이 아니라 Adobe Analytics의 “AppMeasurement” 구현에 적용됩니다.

## 구현 후 {#after-implementation}

사이트에서 Analytics를 구현한 후 추적 비콘에서 [!DNL tracking server]와 [!DNL report suite ID]를 찾을 수 있습니다. [!DNL tracking server]는 비콘의 호스트 이름이므로 쉽게 찾을 수 있습니다. [!UICONTROL 보고서 세트] ID는 비콘의 경로 이름에서 “/b/ss/” 바로 뒤에 쉼표로 구분된 목록입니다.

비콘뿐만 아니라 Analytics 및 다른 Experience Cloud 솔루션에 제공되는 기타 모든 정보를 보려면 [“Experience Cloud Debugger” Chrome 확장 기능](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=ko-KR)을 설치하십시오.

## 구현 전 {#before-implementation}

**[!DNL Tracking server]** - 아직 Adobe Analytics 구현을 시작하지 않은 경우 “.sc.omtrdc.net” [!DNL tracking server]의 하위 도메인을 선택합니다. 예를 들어 “Jim’s Brims”라는 온라인 모자 스토어가 있다고 가정해 보십시오. [!DNL tracking server]를 다음과 같이 간단히 설정할 수 있습니다.

“jimsbrims.sc.omtrdc.net”.

**[!UICONTROL 보고서 세트]** - 생성된 [!UICONTROL 보고서 세트] 목록을 찾으려면 [!DNL Analytics]에 로그인하고 상단 메뉴에서 [!UICONTROL 관리자] > [!UICONTROL 보고서 세트]로 이동하여 ID 및 제목을 포함한 [!UICONTROL 보고서 세트] 목록을 확인하십시오.

자세한 내용은 아래 비디오를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/40900/?quality=12&learn=on&captions=kor)
