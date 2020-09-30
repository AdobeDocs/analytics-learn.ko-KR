---
title: 데이터 레이어를 사용하여 론치를 통해 Adobe Analytics의 페이지 이름 및 기타 변수 설정
description: Analytics 및 기타 Experience Cloud 솔루션에 데이터 레이어를 사용하는 것이 가장 좋습니다. 이 비디오에서는 값을 데이터 레이어에서 끌어낸 다음 Launch에서 사용하여 Adobe Analytics의 변수를 채우는 방법을 살펴봅니다.
feature: launch implementation
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1852
translation-type: tm+mt
source-git-commit: ee6c03cff5b051d9293d75965e9fd98f151d7fce
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 데이터 레이어를 사용하여 [!DNL Experience Platform Launch] {#using-a-data-layer-to-set-page-name-and-other-variables-in-adobe-analytics-via-launch}

데이터 레이어를 다른 Experience Cloud 솔루션 [!DNL Analytics] 에 사용하는 것이 가장 좋습니다. 이 비디오에서는 데이터 레이어에서 값을 끌어낸 후 Adobe Analytics의 변수를 채우는 방법 [!DNL Experience Platform Launch] 을 살펴봅니다.

## 데이터 레이어 {#data-layers}

특히 Adobe Analytics에서 사이트 및 Adobe Experience Cloud 솔루션의 데이터를 사용하여 작업할 때 데이터 레이어를 사용하는 것이 좋습니다. _데이터 계층_&#x200B;은 개발자가 페이지에 삽입하는 JavaScript 개체의 프레임워크입니다. The data layers can be used by tracking tools (including tag management systems like [!DNL Experience Platform Launch]) to populate reports. 데이터 레이어에 대한 추가 정보는 [Experience Cloud 문서](https://marketing.adobe.com/resources/help/en_US/sc/implement/ref-data-layer.html) 또는 [W3C 사이트에서](https://www.w3.org/)찾을 수 있습니다.

또한 블로그 [데이터 레이어를 참조하십시오.Buzzword에서 Best Practice에 이르기까지](https://theblog.adobe.com/data-layers-buzzword-best-practice/)데이터 레이어 및 두 가지 예제를 통해 유용한 정보를 얻을 수 있습니다.

## 데이터 레이어, [!DNL Experience Platform Launch]및 Adobe Analytics(오 마이?){#data-layers-launch-and-adobe-analytics-oh-my}

1. 사이트에서 사용할 데이터 레이어 표준을 만듭니다. 이 표준을 참조하면 됩니다 [!DNL Experience Platform Launch].

   1. 이 데이터 레이어를 호출하기 전에 페이지 맨 앞에 가능한 한 높게 배치하여 값을 즉시 사용할 수 있도록 [!DNL Experience Platform Launch]하고, Adobe Target과 같이 페이지에서 높아야 [!DNL Launch]하는 Adobe 솔루션으로 값을 사용할 수 있습니다.

1. 데이터 레이어의 데이터를 채웁니다.
1. 에서 [!DNL Experience Platform Launch]데이터 레이어의 데이터 포인트를 참조하는 &quot;[!UICONTROL data elements]&quot;를 만들고, 이 요소는 [!DNL Experience Platform Launch] 규칙, 확장 기능 [!UICONTROL 및]확장 기능 등 [!UICONTROL 에서 사용할 수 있습니다].
1. 확장 글로벌 변수 또는 규칙에서 [!UICONTROL 데이터 요소] 를 [!DNL Analytics] 사용하여 값을 prop에 [!UICONTROL 할당하고], eVars [!UICONTROL ,]eVars [!UICONTROL , pagePageName, 또는 기타 변수에][!DNL Analytics] 값을 지정합니다.
1. 데이터를 보내는 비콘을 트리거합니다 [!DNL Analytics].

다음 비디오에서는 이 과정을 안내합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25899/?quality=12)
