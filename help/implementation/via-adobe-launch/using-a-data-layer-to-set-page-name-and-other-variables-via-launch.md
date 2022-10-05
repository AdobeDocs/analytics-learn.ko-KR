---
title: 데이터 계층을 사용하여 태그를 통해 Analytics 변수를 설정합니다
description: Analytics 데이터 및 기타 Experience Cloud 솔루션 소싱에 데이터 레이어를 사용하는 방법에 대해 알아봅니다.
feature: Launch Implementation
role: Developer, Data Engineer
level: Beginner
kt: 1852
thumbnail: 25899.jpg
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: d78c3351d2a98704396ceb8f84d123dd463befe5
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 9%

---

# 데이터 계층을 사용하여 [!DNL Tags] {#use-a-data-layer-to-set-analytics-variables-in-adobe-analytics-via-tags}

데이터 레이어 사용 [!DNL Analytics] 및 기타 Experience Cloud 솔루션은 모범 사례입니다. 이 비디오에서는 데이터 레이어에서 값을 가져와 을(를) 사용하는 방법을 알아봅니다. [!DNL Experience Platform Tags] Adobe Analytics에서 변수를 채우려면 다음을 수행하십시오.

## 데이터 레이어 {#data-layers}

A _데이터 계층_ 는 개발자가 디지털 웹 페이지에 추가하는 JavaScript 개체의 프레임워크입니다. Analytics 솔루션은 궁극적으로 데이터 계층을 사용하여 보고서를 채웁니다. 다음을 포함한 태그 관리 시스템 [!DNL Experience Platform Tags])은 데이터 계층을 읽고, 값을 변수에 매핑하고, 해당 데이터를 digital experience 솔루션에 전송하는 중개자입니다.

에서 데이터 계층에 대한 추가 정보 검토 [Experience Cloud 설명서](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=ko) 그리고 블로그 [데이터 레이어: 유행어부터 우수 사례까지](https://blog.adobe.com/en/2014/03/13/data-layers-buzzword-best-practice).

## 데이터 레이어, [!DNL Experience Platform Tags], 및 Adobe Analytics{#data-layers-launch-and-adobe-analytics}

1. 사이트에서 사용할 데이터 계층 표준을 정의하거나 식별합니다.

   1. 데이터 레이어를 페이지의 헤드 섹션과 호출 전에 가능한 한 높게 배치합니다 [!DNL Experience Platform Tags]. 이렇게 하면 [!DNL Tags] 그리고 Adobe Target처럼 페이지에서 높아야 하는 Adobe 솔루션별로 사용할 수 있습니다.

1. 데이터 레이어의 데이터를 채웁니다.
1. in [!DNL Experience Platform Tags], 만들기 &quot;[!UICONTROL 데이터 요소]데이터 계층에 데이터 포인트를 매핑합니다. 이러한 데이터 요소는 전체에서 사용됩니다 [!DNL Experience Platform Tags] in [!UICONTROL 규칙] 및 [!UICONTROL 확장].
1. 다음 중 하나에서 [!DNL Analytics] 확장의 전역 변수 섹션이나 [!DNL Tags rule]에서 값을 지정합니다. [!UICONTROL 데이터 요소] to [!UICONTROL prop], [!UICONTROL eVar], [!UICONTROL pageName], 및 기타 [!DNL Analytics] 변수를 채우는 방법을 설명합니다.
1. [!DNL Analytics]에 데이터를 전송하는 비콘을 트리거합니다.

다음 비디오는 이 과정에 대해 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)

>[!NOTE]
>
>이 비디오에서 사용되는 특정 데이터 계층은 조직의 &quot;우수 사례&quot;로 간주되지 않을 수 있습니다. 디지털 마케팅 솔루션에 중요한 데이터를 표시하기 위해 데이터 계층을 사용하는 개념은 가장 좋은 방법입니다.