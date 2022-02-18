---
title: 데이터 레이어를 사용하여 Launch를 통해 Adobe Analytics에서 페이지 이름 및 기타 변수 설정
description: Analytics 및 기타 Experience Cloud 솔루션에 데이터 레이어를 사용하는 것은 하나의 모범 사례입니다. 이 비디오는 데이터 레이어에서 값을 가져와 Launch에서 사용하여 Adobe Analytics의 변수를 채우는 방법에 대해 설명합니다.
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
workflow-type: ht
source-wordcount: '365'
ht-degree: 100%

---

# 데이터 레이어를 사용하여 [!DNL Experience Platform Launch]를 통해 페이지 이름 및 기타 변수 설정 {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

[!DNL Analytics] 및 기타 Experience Cloud 솔루션에 데이터 레이어를 사용하는 것은 하나의 모범 사례입니다. 이 비디오는 데이터 레이어에서 값을 가져와 [!DNL Experience Platform Launch]에서 사용하여 Adobe Analytics의 변수를 채우는 방법에 대해 설명합니다.

## 데이터 레이어 {#data-layers}

사이트 및 Adobe Experience Cloud 솔루션, 특히 Adobe Analytics의 데이터를 사용하여 작업할 때 데이터 레이어를 사용하는 것은 하나의 모범 사례입니다. _데이터 레이어_&#x200B;는 개발자가 페이지에 삽입하는 JavaScript 오브젝트의 프레임워크입니다. 데이터 레이어는 [!DNL Experience Platform Launch]와 같은 태그 관리 시스템을 포함하는 추적 도구로 보고서를 채우는 데 사용할 수 있습니다. [Experience Cloud 설명서](https://experienceleague.adobe.com/docs/analytics/implementation/prepare/data-layer.html?lang=ko) 또는 [W3C 사이트](https://www.w3.org/)에서 데이터 레이어에 대한 추가 정보를 찾아보십시오.

또한 블로그 [데이터 레이어: 유행어부터 모범 사례까지](https://theblog.adobe.com/data-layers-buzzword-best-practice/)를 참조하여 데이터 레이어와 몇 가지 예에 대한 유익한 정보를 확인하십시오.

## 데이터 레이어, [!DNL Experience Platform Launch] 및 Adobe Analytics{#data-layers-launch-and-adobe-analytics-oh-my}

1. [!DNL Experience Platform Launch]에서 참조할 수 있고 사이트에서 사용할 데이터 레이어 표준을 생성합니다.

   1. 이 데이터 레이어를 [!DNL Experience Platform Launch] 호출 전 페이지 헤드에 최대한 높게 배치하여 [!DNL Launch], 그리고 Adobe Target과 같이 페이지 상단에 배치되어야 하는 Adobe 솔루션에서 값을 바로 사용할 수 있도록 합니다.

1. 데이터 레이어의 데이터를 채웁니다.
1. [!DNL Experience Platform Launch]에서, 데이터 레이어에서 데이터 포인트를 참조하며 [!UICONTROL 규칙], [!UICONTROL 확장 기능] 등의 [!DNL Experience Platform Launch] 전체에서 사용할 수 있는 “[!UICONTROL 데이터 요소]”를 생성합니다.
1. [!DNL Analytics] 확장 기능 전역 변수 또는 규칙에서 [!UICONTROL 데이터 요소]를 사용하여 [!UICONTROL prop], [!UICONTROL eVar], [!UICONTROL pageName] 또는 기타 [!DNL Analytics] 변수에 값을 할당합니다.
1. [!DNL Analytics]에 데이터를 전송하는 비콘을 트리거합니다.

다음 비디오는 이 과정에 대해 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
