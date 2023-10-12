---
title: Analytics 추적 서버 및 보고서 세트 ID를 식별하는 방법
description: Adobe Analytics을 설정하거나 다른 Experience Cloud 솔루션에서 참조할 때 사용 중인 Analytics "Tracking Server" 또는 데이터를 보내는 "보고서 세트"를 아는 것이 도움이 되거나 필요한 경우가 많습니다. 이 비디오에서는 Adobe Analytics를 이미 구현했는지 여부에 관계없이 두 값을 모두 찾는 방법을 보여 줍니다.
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
source-wordcount: '330'
ht-degree: 18%

---

# 분석을 식별하는 방법 [!DNL tracking server] 및 [!UICONTROL 보고서 세트 ID] {#how-to-identify-your-analytics-tracking-server-and-report-suites}

Adobe Analytics을 설정하거나 다른 Experience Cloud 솔루션에서 참조할 때 사용 중인 Analytics &quot;추적 서버&quot; 또는 &quot;[!UICONTROL 보고서 세트]데이터를 로 보내는 경우입니다. 이 비디오에서는 Adobe Analytics를 이미 구현했는지 여부에 관계없이 두 값을 모두 찾는 방법을 보여 줍니다.

>[!IMPORTANT]
>
>이 문서와 비디오는 Web SDK를 사용하는 구현이 아니라 Adobe Analytics의 &quot;AppMeasurement&quot; 구현에 적용됩니다.

## 구현 후 {#after-implementation}

사이트에서 Analytics를 구현하면 다음을 찾을 수 있습니다. [!DNL tracking server] 및 [!DNL report suite ID] 추적 비콘에 있습니다. 다음 [!DNL tracking server] 는 비콘의 호스트 이름이므로 쉽게 찾을 수 있습니다. 다음 [!UICONTROL 보고서 세트] ID는 비콘의 경로 이름에서 &quot;/b/ss/&quot; 바로 뒤에 쉼표로 구분된 목록입니다.

비콘뿐만 아니라 Analytics 및 기타 Experience Cloud 솔루션에 제공되는 기타 모든 정보를 보려면 [&quot;Experience Cloud Debugger&quot; Chrome 확장 프로그램](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj?hl=ko-KR).

## 구현 전 {#before-implementation}

**[!DNL Tracking server]** - 아직 Adobe Analytics 구현을 시작하지 않은 경우 &quot;.sc.omtrdc.net&quot;에 대한 하위 도메인을 선택합니다. [!DNL tracking server]. 예를 들어 &quot;짐스 브림스&quot;라는 온라인 모자 스토어가 있다고 가정해 보겠습니다. [!DNL tracking server]를 다음과 같이 간단히 설정할 수 있습니다.

&quot;jimsbrims.sc.omtrdc.net&quot;.

**[!UICONTROL 보고서 세트]** - 내 목록 찾기 [!UICONTROL 보고서 세트] 생성되었습니다. 로그인하십시오. [!DNL Analytics] 다음으로 이동 [!UICONTROL 관리자] > [!UICONTROL 보고서 세트] 을 클릭하여 목록을 확인합니다. [!UICONTROL 보고서 세트], 해당 ID 및 제목.

자세한 내용은 아래 비디오를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/26061/?quality=12&learn=on)
