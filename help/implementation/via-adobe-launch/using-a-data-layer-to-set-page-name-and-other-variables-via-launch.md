---
title: 데이터 레이어를 사용하여 Tags를 통해 Analytics 변수를 설정합니다.
description: Analytics 데이터 및 기타 Experience Cloud 솔루션 소싱에 데이터 레이어를 사용하는 방법에 대해 알아봅니다.
feature: Launch Implementation
role: Developer, Data Engineer
level: Beginner
kt: 1852
thumbnail: 25899.jpg
exl-id: 408ceb47-df05-4456-85bb-0ef2798a05a5
source-git-commit: d78c3351d2a98704396ceb8f84d123dd463befe5
workflow-type: ht
source-wordcount: '324'
ht-degree: 100%

---

# 데이터 레이어를 사용하여 [!DNL Tags]를 통해 Analytics 변수를 설정합니다. {#use-a-data-layer-to-set-analytics-variables-in-adobe-analytics-via-tags}

[!DNL Analytics] 및 기타 Experience Cloud 솔루션에 데이터 레이어를 사용하는 것은 하나의 모범 사례입니다. 이 비디오를 통해 데이터 레이어에서 값을 가져와 [!DNL Experience Platform Tags]에서 사용하여 Adobe Analytics의 변수를 채우는 방법에 대해 알아봅니다.

## 데이터 레이어 {#data-layers}

_데이터 레이어_&#x200B;는 개발자가 디지털 웹 페이지에 추가하는 JavaScript 오브젝트의 프레임워크입니다. Analytics 솔루션은 궁극적으로 데이터 레이어를 사용하여 보고서를 채웁니다. [!DNL Experience Platform Tags]가 포함된 태그 관리 시스템은 데이터 레이어를 읽고, 값을 변수에 매핑하고, 해당 데이터를 디지털 경험 솔루션에 전송하는 중개 시스템입니다.

[Experience Cloud 설명서](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=ko)에서 데이터 레이어에 대한 추가 정보를 검토하고 블로그 [데이터 레이어: 유행어부터 모범 사례까지](https://blog.adobe.com/en/2014/03/13/data-layers-buzzword-best-practice)를 참조하십시오.

## 데이터 레이어, [!DNL Experience Platform Tags] 및 Adobe Analytics{#data-layers-launch-and-adobe-analytics}

1. 사이트에서 사용할 데이터 레이어 표준을 정의하거나 식별합니다.

   1. 데이터 레이어를 [!DNL Experience Platform Tags] 호출 전 페이지 헤드에 최대한 높게 배치합니다. 이렇게 하면 Adobe Target과 같이 페이지 상단에 배치되어야 하는 [!DNL Tags] 및 Adobe 솔루션에서 값을 바로 사용할 수 있습니다.

1. 데이터 레이어의 데이터를 채웁니다.
1. [!DNL Experience Platform Tags]에서 데이터 레이어에서 데이터 포인트를 매핑하는 “[!UICONTROL 데이터 요소]”를 생성합니다. 해당 데이터 요소는 [!UICONTROL 규칙]과 [!UICONTROL 확장]의 [!DNL Experience Platform Tags] 전체에서 사용됩니다.
1. [!DNL Analytics] 확장 기능의 전역 변수 섹션 또는 [!DNL Tags rule]에서 [!UICONTROL prop], [!UICONTROL eVar], [!UICONTROL pageName] 및 기타 [!DNL Analytics] 변수에 [!UICONTROL 데이터 요소]의 값을 할당합니다.
1. [!DNL Analytics]에 데이터를 전송하는 비콘을 트리거합니다.

다음 비디오는 이 과정에 대해 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)

>[!NOTE]
>
>이 비디오에 사용되는 특정 데이터 레이어는 조직의 “모범 사례”로 간주될 수 없습니다. 모범 사례는 중요 데이터를 디지털 마케팅 솔루션에 표시하기 위해 데이터 레이어를 사용하는 개념입니다.