---
title: 'Adobe Analytics에서 단일 페이지 애플리케이션(SPA)을 추적할 때의 모범 사례 '
description: 본 문서에서는 Adobe Analytics을 사용하여 SPA(Single Page Applications)를 추적하는 것처럼 따라야 하는 몇 가지 모범 사례를 설명합니다. 이 문서는 권장 구현 방법인 Experience Platform Launch 사용에 중점을 둡니다.
feature: implementation basics
topics: spa
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
translation-type: tm+mt
source-git-commit: 548ac75589383dfd4da4ae02412de91a0a3b28d6
workflow-type: tm+mt
source-wordcount: '1669'
ht-degree: 0%

---


# Adobe Analytics에서 단일 페이지 애플리케이션(SPA)을 추적할 때의 모범 사례 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

본 문서에서는 Adobe Analytics을 사용하여 SPA(Single Page Applications)를 추적하는 것처럼 따라야 하는 몇 가지 모범 사례를 설명합니다. 이 문서는 권장 구현 방법인 Adobe [!DNL Experience Platform Launch]를 사용하는 데 중점을 둡니다.

초기 메모:

* 아래 항목은 사이트에서 구현하는 데 사용 [!DNL Experience Platform Launch] 을 한다고 가정합니다. 고려 사항은 사용하지 않는 경우에도 존재하지만 구현 방법 [!DNL Experience Platform Launch]에 적용해야 합니다.
* 모든 SPA는 서로 다르기 때문에 다음 중 일부 항목을 필요에 맞게 수정해야 할 수도 있습니다. 하지만 우수 사례를 여러분과 공유하려고 했습니다.SPA 페이지에서 Adobe Analytics을 구현할 때 고려해야 할 사항입니다.

## SPA를 사용한 간단한 작업 다이어그램 [!DNL Experience Platform Launch] {#simple-diagram-of-working-with-spas-in-launch}

![launch의 분석을 위한 spa](assets/spa_for_analyticsinlaunch.png)

**참고:** 앞에서 설명한 바와 같이, 이 다이어그램은 SPA 페이지가 Adobe Analytics 구현에서 처리되는 방식을 설명한 것입니다 [!DNL Experience Platform Launch]. 이 페이지의 다음 섹션에서는 고려 또는 수행해야 하는 단계 및 모든 문제에 대해 논의합니다.

## 데이터 레이어 설정 {#setting-the-data-layer}

SPA 페이지에 새로운 컨텐츠가 로드되거나 SPA 페이지에서 작업이 수행될 때 가장 먼저 데이터 레이어를 업데이트하는 것이 좋습니다. 사용자 지정 이벤트가 실행되거나 규칙이 트리거되기 전에 이 [!DNL Experience Platform Launch]가 발생해야 데이터 레이어에서 새 값을 선택하여 Adobe Analytics으로 푸시할 [!DNL Experience Platform Launch] 수 있습니다.

다음은 SPA에서 보기 변경 또는 작업 시 요소를 변경할 수 있는 샘플 데이터 레이어입니다. 예를 들어 전체/대다수 화면 변경 시 &quot;[!DNL pageName]&quot; 요소를 변경하는 것이 일반적이므로 새 요소를 캡처하여 Adobe Analytics으로 보낼 수 [!DNL Experience Platform Launch] 있습니다.

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

## 사용자 지정 이벤트 및 의견 수렴 [!DNL Experience Platform Launch] {#setting-custom-events-and-listening-in-launch}

새 컨텐츠가 페이지에 로드되거나 사이트에서 작업이 발생할 때 규칙을 실행하고 데이터를 보낼 수 [!DNL Experience Platform Launch] 있도록 알리려는 것입니다 [!DNL Analytics]. 이 작업을 수행하는 방법에는 몇 가지가 있습니다. [!UICONTROL 직접 호출] [!UICONTROL 규칙] 또는 사용자 지정 이벤트를 참조하십시오.

* [!UICONTROL 직접 호출] [!UICONTROL 규칙]:에서 페이지 [!DNL Experience Platform Launch]에서 직접 호출될 때 실행되는 [!UICONTROL 직접 호출] [!UICONTROL 규칙] 을 설정할 수 있습니다. 페이지 로드 또는 사이트의 작업이 매우 간단하거나, 고유하며, 매번(X로 설정하고 매번 트리거) 특정 지침 세트 [!DNL eVar4] 를 실행할 수 있는 경우, [!DNL event2] 직접 호출 [!UICONTROL 규칙을 사용할 수 있습니다]. [!DNL Experience Platform Launch] 직접 호출 [!UICONTROL 규칙 만들기에 관한 설명서를] 참조하십시오 .
* 사용자 지정 이벤트:더 많은 기능과 다른 값이 있는 페이로드를 동적으로 첨부하려면 사용자 지정 JavaScript 이벤트를 설정하고 이 이벤트를 수신해야 합니다. 여기서 페이로드를 사용하여 변수를 설정하고 데이터를 Adobe Analytics으로 보낼 수 [!DNL Experience Platform Launch]있습니다. 이 기능이 필요할 가능성이 높으므로 이 옵션이 가장 좋은 것으로 간주됩니다. 그러나 사이트의 각 기능에서 가장 적합한 방법을 결정할 수 있습니다. 이 사용자 지정 이벤트 방법을 사용해야 한다고 가정할 경우 이 문서에서 앞으로 이동합니다.

**예:** 본 [도움말](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html) 문서에는 구현된 SPA 사이트 [!DNL Analytics] (및 기타 Experience Cloud 솔루션)와 구현된 내용을 설명하는 문서에 대한 링크가 있습니다. 이 SPA 예에서 다음과 같은 사용자 지정 이벤트가 사용되었습니다.

* [!DNL event-view-start]:이 이벤트는 로드되는 보기/상태의 보기 시작에서 실행되어야 합니다.
* [!DNL event-view-end]:이 이벤트는 보기/상태 변경이 발생했으며 페이지의 모든 SPA 구성 요소가 로드를 마친 경우에도 실행해야 합니다. 이것은 일반적으로 Adobe Analytics에 대한 호출을 트리거하는 이벤트입니다.
* [!DNL event-action-trigger]:이 이벤트는 보기/상태 로드를 제외한 모든 이벤트가 페이지에서 발생할 때 발생합니다. 이것은 클릭 이벤트나 보기 변경 없이 더 작은 내용 변경이 될 수 있습니다.

페이지/문서가 실행되는 방법과 시기에 대한 자세한 내용은 위의 참조 페이지/문서를 참조하십시오. 동일한 이벤트 이름을 사용할 필요는 없지만 여기에 나열된 기능이 가장 좋습니다. 다음 비디오에서는 샘플 사이트와 사용자 지정 이벤트를 들을 위치 [!DNL Experience Platform Launch] 를 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 규칙에서 s.t() 또는 s.tl() [!DNL Experience Platform Launch] 을 [!UICONTROL 실행] {#running-s-t-or-s-tl-in-the-launch-rule}

SPA에서 작업할 [!DNL Analytics] 때 알아야 할 가장 중요한 것 중 하나는 `s.t()` 와 `s.tl()`의 차이이다. 데이터를 전송하기 위해 이러한 방법 중 하나 [!DNL Experience Platform Launch] 가 트리거되지만 각 데이터 [!DNL Analytics]를 보낼 시기를 알아야 합니다.

* **s.t()** - &quot;t&quot;는 &quot;track&quot;을 나타내며 일반 페이지 보기입니다. URL이 변경되지 않더라도 보기가 변경되어 새로운 &quot;페이지&quot;로 *간주될* 수 있습니까? 그렇다면 s를 설정합니다.[!DNL pageName] 변수를 사용하여 호출 `s.t()` 을 [!DNL Analytics]

* **s.tl()** - &quot;tl&quot;은 &quot;track link&quot;를 나타내며 전체 화면 변경 내용이 아닌 페이지의 클릭 또는 작은 컨텐츠 변경을 추적하는 데 사용됩니다. 페이지의 변경 내용이 너무 작아 완전히 새로운 &quot;페이지&quot;로 간주하지 않도록 하려면 s.pageName 변수 `s.tl()` 를 무시하므로 사용하고 걱정하지 [!DNL Analytics] 마십시오.

**팁:** 화면이 50% 이상 변하면 페이지 보기로 보고 사용해야 한다는 일반적인 지침을 사용하는 경우도 있습니다 `s.t()`. 화면 크기가 50% 미만인 경우 를 사용하십시오 `s.tl()`. 그러나 새로운 &quot;페이지&quot;로 간주되는 사이트와 Adobe Analytics에서 사이트를 추적하는 방법은 전적으로 사용자에게 달려 있습니다.

다음 비디오에서는 Launch by Adobe에서 트리거하는 위치/방법 `s.t()` 을 보여줍니다 `s.tl()` .

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 변수 지우기 {#clearing-variables}

Adobe Analytics을 사용하여 사이트를 추적할 때는 정확한 데이터를 적시에 전달해야 [!DNL Analytics] 합니다. SPA 환경에서는 변수에서 추적된 값이 유지될 수 있으며, 이 값 [!DNL Analytics] [!DNL Analytics]을 더 이상 원하지 않을 가능성이 있습니다. 이러한 이유로 확장명에 변수를 지울 수 있는 기능이 [!DNL Analytics] 있으므로 다음 이미지 요청을 실행하고 데이터를 보낼 때 새로 추가된 기능을 사용할 수 [!DNL Launch] [!DNL Analytics]있습니다.

위의 다이어그램에서는 히트를 보낸 *후* 변수를 지우는 프로세스를 종료할 때 이 목록이 표시됩니다. 실제로 히트가 전송되기 전 OR 후에 수행할 수 있지만, 규칙 상의 일관성을 유지해야 하므로 변수를 설정하고 보내기 전 또는 후에 항상 지우도록 해야 합니다. [!DNL Experience Platform Launch] 실행을 *전에* 변수를 지우려면 먼저 변수를 지운 다음 새 변수를 설정한 다음 마지막으로 새 데이터를 `s.t()`[!DNL Analytics]보냅니다.

**참고:** 변수가 설정될 변수 `s.tl()`를 알려주기 위해 매번 `s.tl()` 변수 [!DNL linkTrackVars] 와 함께 [!DNL Analytics] 변수를 사용해야 하기 때문에 실행 시 변수 [!DNL Experience Platform Launch]를 지울 필요가없습니다. 이는 잘못된 변수가 일반적으로 사용 시 나타나지 `s.tl()``s.t()` 않지만 SPA 환경에서 사용하는 경우 매우 권장된다는 것을 의미합니다. 말하자면, 품질 데이터를 수집하기 위해 SPA 환경 `s.t()` 과 SPA 환경 모두에서 변수 지우기 기능을 사용하는 `s.tl()` 것이 좋습니다.

다음 비디오에서는 변수를 지우는 위치/방법을 보여 줍니다 [!DNL Launch].

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 추가 고려사항 {#additional-considerations}

### 사용자 지정 코드 창( [!DNL Experience Platform Launch] {#custom-code-windows-in-launch}

확장명에 사용자 지정 코드를 삽입할 수 있는 두 [!DNL Launch] [!DNL Analytics] 위치가 있습니다.라이브러리 [!UICONTROL 관리] 섹션 및 추가 &quot;[!UICONTROL 사용자 지정 코드를 사용하여 추적기 구성]&quot; 섹션.

![Analytics 사용자 지정 코드 창 실행](assets/launch_analyticscustomcodewindows.png)

이러한 위치 중 하나가 SPA 페이지에서 초기 페이지 로드가 발생하는 경우 해당 위치에서 코드를 한 번만 실행한다는 사실을 알고 있어야 합니다. 보기 변경 시 또는 사이트의 작업에 대해 코드를 실행해야 하는 경우 적절한 **[!UICONTROL 규칙]** (예: &quot;페이지 로드:event-view-end&quot; [!UICONTROL 규칙])을 사용하여 [!UICONTROL 규칙이] 실행될 때마다 코드가 실행됩니다. 규칙에서 해당 작업을 만들 때 [!UICONTROL 확장]*= 코어* 및 *작업 유형 = 사용자 지정 코드*&#x200B;를 설정합니다.

### &quot;하이브리드&quot; SPA/일반 사이트 {#hybrid-spa-regular-sites}

일부 사이트에는 &quot;일반&quot; 페이지와 SPA 페이지가 결합되어 있습니다. 이 경우 두 페이지 유형에 모두 작동하는 전략을 사용해야 합니다. 사이트에서 사용자 지정 이벤트를 구성하고 규칙을 트리거할 [!DNL Experience Platform Launch]때는 해시 변경 사항 등에 따라 페이지에서 이중 히트 [!DNL Analytics] 가 발생하지 않도록 주의하십시오. (규칙이 트리거되도록 선택한 [!DNL Experience Platform Launch] 경우입니다.) 이 경우 Adobe Analytics에서 잘못된 데이터를 제공하지 않도록 페이지 보기 중 하나를 표시하지 않아야 합니다.

기능을 별도의 [!UICONTROL 규칙으로] 분리하면 더 많은 제어를 할 수 있도록 하려면, 한 [!UICONTROL 규칙] 의 변경 사항을 다른 [!UICONTROL 규칙] 과 함께 적용할 수 있도록 [!DNL Analytics] 데이터 무결성을 보호하면서 이 작업을 수행한 사실을 기억하거나 문서화합니다.

### A4T를 [!DNL Target] 통한 통합 {#integration-with-target-via-a4t}

여기 짧은 설명선이요 A4T를 [!DNL Target] 사용하는 것과 통합하는 경우 동일한 보기의 [!DNL Target] 요청과 [!DNL Analytics] 요청이 동일한 SDID인지 확인하십시오. 이렇게 하면 데이터가 솔루션에서 제대로 동기화됩니다.

히트를 보려면 디버거 또는 패킷 스니퍼 프로그램을 사용하십시오. 여기에서 다운로드할 수 있는 Chrome 확장 프로그램인 Experience Cloud Debugger을 사용할 수도 [있습니다](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj). [!DNL Target] 페이지에서 먼저 실행되어야 하므로 JavaScript 콘솔 또는 디버거에서도 확인할 수 있습니다.

## 추가 리소스 {#additional-resources}

* [Adobe 포럼 SPA 토론](https://forums.adobe.com/thread/2451022)
* [Experience Platform Launch에서 SPA를 구현하는 방법을 보여주는 참조 아키텍처 사이트](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)