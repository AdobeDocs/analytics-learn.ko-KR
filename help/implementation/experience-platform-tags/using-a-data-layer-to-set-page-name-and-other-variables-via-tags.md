---
title: 데이터 레이어를 사용하여 Experience Platform에서 Analytics 변수를 설정합니다. [!DNL tags]
description: Analytics 데이터 및 기타 Experience Cloud 솔루션 소싱에 데이터 레이어를 사용하는 방법에 대해 알아봅니다.
feature: Tags
topics: Development
role: Developer, Data Engineer
level: Beginner
kt: 1852
thumbnail: 25899.jpg
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: a45667a8d7ccb46b9e33bd11a78fac9714a61df5
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 50%

---

# 데이터 레이어를 사용하여 Experience Platform에서 Analytics 변수를 설정합니다. [!DNL tags]

[!DNL Analytics] 및 기타 Experience Cloud 솔루션에 데이터 레이어를 사용하는 것은 하나의 모범 사례입니다. 이 비디오에서는 데이터 레이어에서 값을 가져와 Experience Platform에서 사용하는 방법을 알아봅니다 [!DNL tags] 을 클릭하여 Adobe Analytics에서 변수를 채울 수 있습니다.

## 데이터 레이어

_데이터 레이어_&#x200B;는 개발자가 디지털 웹 페이지에 추가하는 JavaScript 오브젝트의 프레임워크입니다. Analytics 솔루션은 궁극적으로 데이터 레이어를 사용하여 보고서를 채웁니다. Experience Platform을 포함한 태그 관리 시스템 [!DNL tags])는 데이터 레이어를 읽고, 값을 변수에 매핑하고, 해당 데이터를 디지털 경험 솔루션에 전송하는 중개 시스템입니다.

에서 데이터 계층에 대한 추가 정보 검토 [Experience Cloud 설명서](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=ko).

## 데이터 레이어, Experience Platform [!DNL tags], 및 Adobe Analytics

1. 사이트에서 사용할 데이터 레이어 표준을 정의하거나 식별합니다.

   1. 데이터 레이어를 Experience Platform 호출 전 페이지 헤드에 최대한 높게 배치합니다. [!DNL tags]. 이렇게 하면 Adobe Target과 같이 페이지 상단에 배치되어야 하는 [!DNL tags] 및 Adobe 솔루션에서 값을 바로 사용할 수 있습니다.

1. 데이터 레이어의 데이터를 채웁니다.
1. Experience Platform [!DNL tags], 만들기[!UICONTROL 데이터 요소]&quot;데이터 레이어에서 데이터 포인트를 매핑합니다. 이러한 데이터 요소는 Experience Platform 전체에서 사용됩니다 [!DNL tags] 위치: [!UICONTROL 규칙] 및 [!UICONTROL 확장].
1. [!DNL Analytics] 확장 기능의 전역 변수 섹션 또는 [!DNL Tags rule]에서 [!UICONTROL prop], [!UICONTROL eVar], [!UICONTROL pageName] 및 기타 [!DNL Analytics] 변수에 [!UICONTROL 데이터 요소]의 값을 할당합니다.
1. [!DNL Analytics]에 데이터를 전송하는 비콘을 트리거합니다.

다음 비디오는 이 과정에 대해 소개합니다.

>[!NOTE]
>
> 이제 Launch가 **[!DNL tags]**

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12&learn=on)

>[!NOTE]
>
>이 비디오에 사용되는 특정 데이터 레이어는 조직의 “모범 사례”로 간주될 수 없습니다. 모범 사례는 중요 데이터를 디지털 마케팅 솔루션에 표시하기 위해 데이터 레이어를 사용하는 개념입니다.
