---
title: 데이터 계층을 사용하여 Launch를 통해 Adobe Analytics에서 페이지 이름 및 기타 변수 설정
description: Analytics 및 기타 Experience Cloud 솔루션에 데이터 레이어를 사용하는 것이 가장 좋습니다. 이 비디오에서는 데이터 계층에서 값을 가져와서 Launch에서 사용하여 Adobe Analytics의 변수를 채우는 방법을 알아봅니다.
feature: Launch Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
role: Developer, Data Engineer
level: Beginner
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: fe861dfd541c1b9cb3b233fa3f56d55054305fd9
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 4%

---

# 데이터 계층을 사용하여 [!DNL Experience Platform Launch]을 통해 페이지 이름 및 기타 변수 설정 {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

[!DNL Analytics] 및 기타 Experience Cloud 솔루션에 데이터 레이어를 사용하는 것이 가장 좋습니다. 이 비디오에서는 값을 데이터 계층에서 가져와서 [!DNL Experience Platform Launch]에서 사용하여 Adobe Analytics의 변수를 채우는 방법을 알아봅니다.

## 데이터 레이어 {#data-layers}

특히 Adobe Analytics에서 사이트 및 Adobe Experience Cloud 솔루션에서 데이터를 사용하여 작업할 때 데이터 계층을 사용하는 것이 좋습니다. _데이터 계층_&#x200B;은 개발자가 페이지에 삽입하는 JavaScript 개체의 프레임워크입니다. 데이터 계층은 보고서를 채우기 위해 추적 도구( [!DNL Experience Platform Launch]과 같은 태그 관리 시스템 포함)에서 사용할 수 있습니다. [Experience Cloud 설명서](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=en) 또는 [W3C 사이트](https://www.w3.org/)에서 데이터 계층에 대한 추가 정보를 찾습니다.

또한 블로그 [데이터 레이어: Buzzword에서 Best Practice에 이르기까지 두 가지 예와 데이터 계층에 대한 유용한 정보를 제공합니다.](https://theblog.adobe.com/data-layers-buzzword-best-practice/)

## 데이터 레이어, [!DNL Experience Platform Launch] 및 Adobe Analytics (오, 마이?){#data-layers-launch-and-adobe-analytics-oh-my}

1. 사이트에서 사용할 데이터 레이어 표준을 만듭니다. 이 값은 [!DNL Experience Platform Launch]에서 참조할 수 있습니다.

   1. 이 데이터 레이어를 페이지의 헤드에서, [!DNL Experience Platform Launch] 호출 전에, 가능한 한 높게 배치하여 [!DNL Launch] 이 값을 즉시 사용하고, Adobe Target과 같이 페이지에서 높아야 하는 Adobe 솔루션별로 사용할 수 있도록 하십시오.

1. 데이터 계층에서 데이터를 채웁니다.
1. [!DNL Experience Platform Launch]에서 데이터 계층의 데이터 포인트를 참조하는 &quot;[!UICONTROL 데이터 요소]&quot;를 만들고, [!UICONTROL 규칙], [!UICONTROL 확장] 등에서 [!DNL Experience Platform Launch] 전체에서 사용할 수 있습니다.
1. [!UICONTROL 데이터 요소]를 [!DNL Analytics] 확장 글로벌 변수 또는 규칙에서 사용하여 [!UICONTROL props], [!UICONTROL eVars], [!UICONTROL pageName] 또는 기타 [!DNL Analytics] 변수에 값을 할당합니다.
1. 데이터를 [!DNL Analytics]에 전송하는 비콘을 트리거합니다.

다음 비디오에서는 이 프로세스를 안내합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
