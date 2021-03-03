---
title: 'Adobe Analytics에서 단일 페이지 애플리케이션(SPA)을 추적할 때의 우수 사례 사용 '
description: 이 문서에서는 Adobe Analytics을 사용하여 SPA(Single Page Applications)를 추적하는 동안 따라야 하는 몇 가지 우수 사례에 대해 설명합니다. 이 문서에서는 권장 구현 방법인 Experience Platform Launch 사용에 중점을 둡니다.
feature: Implementation 기본 사항
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
topic: SPA
role: '"개발자, 데이터 엔지니어"'
level: 중간
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---


# Adobe Analytics {#using-best-practices-when-tracking-spa-in-adobe-analytics}에서 단일 페이지 애플리케이션(SPA)을 추적할 때의 우수 사례 사용

이 문서에서는 Adobe Analytics을 사용하여 SPA(Single Page Applications)를 추적하는 동안 따라야 하는 몇 가지 우수 사례에 대해 설명합니다. 이 문서에서는 권장 구현 방법인 Adobe [!DNL Experience Platform Launch] 사용에 중점을 둡니다.

초기 메모:

* 아래 항목은 [!DNL Experience Platform Launch]을(를) 사용하여 사이트에서 구현한다고 가정합니다. [!DNL Experience Platform Launch]을(를) 사용하지 않을 경우에도 고려 사항이 여전히 존재하지만 구현 방법에 적용되어야 합니다.
* 모든 SPA은 다르므로 귀하의 요구에 가장 잘 맞도록 다음 항목 중 일부를 수정해야 할 수도 있지만, 귀하와 모범 사례를 공유하고자 합니다.SPA 페이지에서 Adobe Analytics을 구현할 때 고려해야 할 사항입니다.

## [!DNL Experience Platform Launch] {#simple-diagram-of-working-with-spas-in-launch}에서 SPA으로 작업하는 간단한 다이어그램

![launch의 분석을 위한 spa](assets/spa_for_analyticsinlaunch.png)

**참고:** 언급된 대로, SPA 페이지가 Adobe Analytics 구현에서 다음을 사용하여 처리되는 방식을 간략히 나타낸 것입니다 [!DNL Experience Platform Launch]. 이 페이지의 다음 섹션에서는 고려 또는 조치를 취해야 하는 단계 및 문제에 대해 다룹니다.

## 데이터 레이어 {#setting-the-data-layer} 설정

SPA 페이지에 새 내용을 로드하거나 SPA 페이지에서 작업을 수행할 때 가장 먼저 해야 할 일은 데이터 레이어를 업데이트하는 것입니다. 이 작업은 [!DNL Experience Platform Launch]이(가) 데이터 레이어에서 새 값을 선택하고 Adobe Analytics으로 푸시할 수 있도록 사용자 지정 이벤트가 실행되고 [!DNL Experience Platform Launch]에서 규칙을 트리거하기 전에 수행해야 합니다.

다음은 SPA의 보기 변경 또는 작업 시 요소를 변경할 수 있는 샘플 데이터 레이어입니다. 예를 들어 전체/대부분의 화면 변경 시 &quot;[!DNL pageName]&quot; 요소를 변경하는 것이 일반적이기 때문에 새 요소를 [!DNL Experience Platform Launch]에서 캡처하여 Adobe Analytics으로 보낼 수 있습니다.

```JavaScript
<script>
    digitalData = {
        pageInstanceID: "Launch Demo Site",
        page:{
            pageInfo:{
                pageID: '2745374',
                pageName: 'acs demo - product listing page'
            },
            attributes:{
                project: "Experience Platform Launch Project"
            }
        },
        user : [ {
          "profile" : [ {
            "attributes" : {
              "gender" : "male",
              "age" : "35"
            }
          } ]
        }],
        libraries : {
          adobe : {
            launch : {
              state : 0, // 0 = not loaded , 1 = loaded
              domain : "assets.adobedtm.com"
            }
          }
        }

     };
    </script>
```

## [!DNL Experience Platform Launch] {#setting-custom-events-and-listening-in-launch}에서 사용자 지정 이벤트 및 의견 수렴 설정

새 컨텐츠가 페이지에 로드되거나 사이트에서 작업이 발생할 때 규칙을 실행하고 데이터를 [!DNL Analytics]에 보낼 수 있도록 [!DNL Experience Platform Launch]에 알리려는 것입니다. 이 작업을 수행하는 방법에는 몇 가지가 있습니다.[!UICONTROL 직접 호출] [!UICONTROL 규칙] 또는 사용자 지정 이벤트.

* [!UICONTROL 직접 ] [!UICONTROL 호출 규칙]:에서 페이지 [!DNL Experience Platform Launch]에서 직접 호출될 때 실행되는  [!UICONTROL 직접 ]  호출을 설정할 수 있습니다. 페이지 로드 또는 사이트의 작업이 매우 간단하거나, 고유하고 언제든지 특정 지침 집합을 실행할 수 있는 경우(a0/>을 X로 설정하고 항상 [!DNL event2]을 트리거함), [!UICONTROL 직접 호출] [!UICONTROL  규칙]을 사용할 수 있습니다. [!DNL eVar4] [!UICONTROL 직접 호출] [!UICONTROL 규칙]을 만드는 방법에 대한 [!DNL Experience Platform Launch] 설명서를 참조하십시오.
* 사용자 지정 이벤트:더 많은 기능과 다른 값을 갖는 페이로드를 동적으로 첨부하려면 사용자 지정 JavaScript 이벤트를 설정하고 [!DNL Experience Platform Launch]에서 이벤트를 수신해야 합니다. 여기서 페이로드를 사용하여 변수를 설정하고 데이터를 Adobe Analytics으로 보낼 수 있습니다. 이 기능이 필요할 가능성이 높으므로 이 옵션이 가장 좋은 방법으로 간주됩니다. 그러나 사이트의 각 함수는 가장 적합한 방법을 결정할 수 있습니다. 이 사용자 지정 이벤트 방법을 사용해야 한다고 가정할 경우 이 문서에서는 앞으로 이동합니다.

**예:** 이  [](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html) 도움말 문서에는 구현된 샘플 SPA 사이트  [!DNL Analytics] (및 기타 Experience Cloud 솔루션)와 구현된 내용을 설명하는 문서에 대한 링크가 있습니다. 이러한 SPA 예에서 다음과 같은 사용자 지정 이벤트가 사용되었습니다.

* [!DNL event-view-start]:이 이벤트는 로드 중인 보기/상태의 보기 시작 부분에서 발생합니다.
* [!DNL event-view-end]:이 이벤트는 보기/상태 변경이 발생했으며 페이지의 모든 SPA 구성 요소 로드가 완료된 경우에도 실행해야 합니다. 이것은 일반적으로 Adobe Analytics에 대한 호출을 트리거하는 이벤트입니다.
* [!DNL event-action-trigger]:이 이벤트는 보기/상태 로드를 제외한 모든 이벤트가 페이지에서 발생할 때 발생합니다. 이것은 클릭 이벤트나 보기 변경 없이 더 작은 내용의 변경이 될 수 있습니다.

페이지/실행 시기에 대한 자세한 내용은 위의 참조 페이지/문서를 참조하십시오. 동일한 이벤트 이름을 사용할 필요는 없지만 여기에 나열된 기능이 가장 좋은 방법입니다. 다음 비디오에서는 사용자 지정 이벤트를 수신하기 위해 샘플 사이트와 [!DNL Experience Platform Launch]에 있는 위치를 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## [!DNL Experience Platform Launch] [!UICONTROL 규칙] {#running-s-t-or-s-tl-in-the-launch-rule}에서 s.t() 또는 s.tl() 실행

SPA에서 작업할 때 [!DNL Analytics]에 대해 알아야 할 가장 중요한 것 중 하나는 `s.t()`과 `s.tl()`의 차이입니다. [!DNL Experience Platform Launch]에서 이러한 메서드 중 하나를 트리거하여 데이터를 [!DNL Analytics]로 보내지만 각 메서드를 보낼 시기를 알아야 합니다.

* **s.t()** - &quot;t&quot;는 &quot;track&quot;을 나타내며 일반적인 페이지 보기입니다. URL이 변경되지 않더라도 보기는 *a1/>이 새 &quot;페이지&quot;로 간주하기에 충분합니까?* 이 경우 s.[!DNL pageName] 변수를 설정하고 `s.t()`을 사용하여 [!DNL Analytics](으)로 호출을 전송합니다.

* **s.tl()** - &quot;tl&quot;은 &quot;track link&quot;를 나타내며, 일반적으로 전체 화면 변경과 반대로 페이지에서 클릭 또는 작은 컨텐츠 변경을 추적하는 데 사용됩니다. 페이지의 변경 내용이 너무 작아서 완전히 새로운 &quot;page&quot;로 간주하지 않도록 하려면 `s.tl()`을 사용하고 s.pageName 변수 설정에 대해 걱정하지 마십시오. [!DNL Analytics]은 이 변수를 무시합니다.

**팁:** 어떤 사람들은 화면이 50% 이상 변경되면 페이지 보기로 간주하여 사용해야 한다는 일반적인 지침을 사용합니다 `s.t()`. 화면 변경이 50% 미만인 경우 `s.tl()`을(를) 사용하십시오. 그러나 Adobe Analytics에서 사이트를 추적하는 방법과 새로운 &quot;페이지&quot;로 간주하는 것은 전적으로 사용자에게 달려 있습니다.

다음 비디오는 Launch by Adobe에서 `s.t()` 또는 `s.tl()`을 트리거하는 위치/방법을 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 변수 {#clearing-variables} 지우기

Adobe Analytics을 사용하여 사이트를 추적할 때는 적절한 데이터만 [!DNL Analytics](으)로 전송해야 합니다. SPA 환경에서는 [!DNL Analytics] 변수에서 추적된 값이 지속되어 [!DNL Analytics]로 다시 전송될 수 있으며, 이는 더 이상 원하지 않을 가능성이 있습니다. 이러한 이유로 [!DNL Analytics] [!DNL Launch] 확장명에 변수를 지울 수 있는 함수가 있으므로 다음 이미지 요청을 실행하고 데이터를 [!DNL Analytics]에 보낼 때 새 슬레이트가 만들어집니다.

위의 다이어그램에는 히트에서 보내는 *after* 변수를 지우는 프로세스 끝에 나열됩니다. 실제로 히트가 전송되기 전에 OR 중 하나를 수행할 수 있지만, [!DNL Experience Platform Launch] 규칙에서는 일관되어야 변수를 설정하고 보내기 전 또는 후에 항상 변수를 지울 수 있습니다. *전에*&#x200B;변수 `s.t()`를 지우려면 먼저 변수를 지운 다음 새 변수를 설정한 다음 마지막으로 새 데이터를 [!DNL Analytics]에 보냅니다.

**참고:** 변수 지우기는 설정될 변수 `s.tl()`를 알리기 위해 변수 `s.tl()` 와 함께 변수 [!DNL linkTrackVars] 를 사용해야  [!DNL Analytics] 하므로(백그라운드에서 자동으로 추가됨)를 실행할 때 항상 필요한 것은  [!DNL Experience Platform Launch]아닙니다. 즉, 잘못된 변수는 일반적으로 `s.tl()`을 사용할 때 나타나지 않지만 SPA 환경에서 `s.t()`을(를) 사용할 때는 매우 권장됩니다. 즉, 품질 데이터 수집을 위해 SPA 환경에서 `s.t()` 및 `s.tl()` 모두에 대해 변수 지우기 기능을 사용하는 것이 좋습니다.

다음 비디오는 [!DNL Launch]에서 변수를 지우는 위치/방법을 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 추가 고려사항 {#additional-considerations}

### [!DNL Experience Platform Launch] {#custom-code-windows-in-launch}의 사용자 지정 코드 창

[!DNL Launch] [!DNL Analytics] 확장에는 사용자 지정 코드를 삽입할 수 있는 두 개의 위치가 있습니다.[!UICONTROL 라이브러리 관리] 섹션 및 추가 &quot;[!UICONTROL 사용자 지정 코드를 사용하여 추적기 구성]&quot; 섹션.

![Analytics 사용자 지정 코드 창 시작](assets/launch_analyticscustomcodewindows.png)

이러한 위치 중 하나가 SPA 페이지에서 초기 페이지 로드가 발생하는 경우 실제로 한 번만 해당 위치에서 코드를 실행한다는 것을 알고 있어야 합니다. 보기 변경 시 또는 사이트의 작업에 대해 코드를 실행할 필요가 있는 경우 적절한 **[!UICONTROL 규칙]**(예: &quot;페이지 로드:event-view-end&quot; [!UICONTROL 규칙])에 대해 코드가 [!UICONTROL 규칙]이 실행될 때마다 실행됩니다. [!UICONTROL 규칙]에서 해당 동작을 만들 때 *Extension = Core* 및 *작업 유형 = 사용자 지정 코드*&#x200B;를 설정합니다.

### &quot;하이브리드&quot; SPA/일반 사이트 {#hybrid-spa-regular-sites}

일부 사이트는 &quot;일반&quot; 페이지와 SPA 페이지의 조합입니다. 이 경우 두 페이지 유형에 모두 작동하는 전략을 사용해야 합니다. 사이트에서 사용자 지정 이벤트를 구성하고 [!DNL Experience Platform Launch]에서 규칙을 트리거할 때는 해시 변경 등에 따라 페이지에서 [!DNL Analytics]에 이중 히트가 발생하지 않도록 주의하십시오. (이 방법으로 [!DNL Experience Platform Launch] 규칙을 트리거하도록 선택한 경우) 이 경우 Adobe Analytics에서 잘못된 데이터를 제공하지 않도록 페이지 보기 중 하나를 표시하지 않아야 합니다.

기능을 별도의 [!UICONTROL 규칙]으로 분할하여 제어하게 되면 이 작업을 수행한 사실을 기억하거나 문서화하여 다른 [!UICONTROL 규칙]에도 변경 사항을 적용할 수 있으므로 [!DNL Analytics] 데이터 무결성을 보호할 수 있습니다.

### A4T {#integration-with-target-via-a4t}을(를) 통해 [!DNL Target]과 통합

여기 짧은 설명선만 해주세요 A4T를 사용하여 [!DNL Target]과 통합하려는 경우 동일한 보기의 [!DNL Target] 요청과 [!DNL Analytics] 요청의 SDID가 동일해야 합니다. 이렇게 하면 데이터가 솔루션에서 제대로 동기화됩니다.

히트를 보려면 디버거 또는 패킷 스니퍼 프로그램을 사용합니다. 또한 [HERE](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)을(를) 다운로드할 수 있는 Chrome 확장인 Experience Cloud Debugger을 사용할 수도 있습니다. [!DNL Target] 페이지에서 먼저 실행되어야 하므로 JavaScript 콘솔 또는 디버거에서도 확인할 수 있습니다.

## 추가 리소스 {#additional-resources}

* [Adobe 포럼에 대한 SPA 토론](https://forums.adobe.com/thread/2451022)
* [Experience Platform Launch에서 SPA을 구현하는 방법을 보여주는 참조 아키텍처 사이트](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)