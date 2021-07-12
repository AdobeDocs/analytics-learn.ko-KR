---
title: 'Adobe Analytics에서 단일 페이지 애플리케이션(SPA)을 추적할 때 모범 사례 사용 '
description: 이 문서에서는 Adobe Analytics을 사용하여 SPA(단일 페이지 애플리케이션)을 추적하는 동안 따라야 하는 몇 가지 우수 사례를 설명합니다. 이 설명서는 권장되는 구현 방법인 Experience Platform Launch 사용에 중점을 둡니다.
feature: 구현 기본 사항
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1389
topic: SPA
role: Developer, Data Engineer
level: Intermediate
exl-id: 8fe63dd1-9629-437f-ae07-fe1c5a05fa42
source-git-commit: 32424f3f2b05952fe4df9ea91dcbe51684cee905
workflow-type: tm+mt
source-wordcount: '1672'
ht-degree: 0%

---

# Adobe Analytics에서 단일 페이지 애플리케이션(SPA)을 추적할 때 모범 사례 사용 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

이 문서에서는 Adobe Analytics을 사용하여 SPA(단일 페이지 애플리케이션)을 추적하는 동안 따라야 하는 몇 가지 우수 사례를 설명합니다. 이 설명서는 권장되는 구현 방법인 Adobe [!DNL Experience Platform Launch] 사용에 중점을 둡니다.

초기 참고 사항:

* 아래 항목에서는 [!DNL Experience Platform Launch]을 사용하여 사이트에서 를 구현한다고 가정합니다. [!DNL Experience Platform Launch] 을 사용하지 않는 경우에도 고려 사항이 여전히 존재하지만 구현 방법을 조정해야 합니다.
* 모든 SPA이 다르므로 다음 항목 중 일부를 조정해야 사용자의 요구 사항을 가장 잘 충족할 수 있지만 일부 우수 사례를 여러분과 공유하려고 했습니다. SPA 페이지에서 Adobe Analytics을 구현할 때 고려해야 할 사항입니다.

## [!DNL Experience Platform Launch]에서 SPA으로 작업하는 간단한 다이어그램 {#simple-diagram-of-working-with-spas-in-launch}

![launch의 analytics용 spa](assets/spa_for_analyticsinlaunch.png)

**참고:**  기술한 대로, 이 다이어그램은 를 사용하여 Adobe Analytics 구현에서 SPA 페이지를 처리하는 방법을 간략히 보여줍니다 [!DNL Experience Platform Launch]. 이 페이지의 다음 섹션에서는 고려 사항 또는 조치를 취해야 하는 단계 및 문제에 대해 설명합니다.

## 데이터 레이어 설정 {#setting-the-data-layer}

SPA 페이지에 새 컨텐츠가 로드되거나 SPA 페이지에서 작업이 수행될 때 수행해야 하는 첫 번째 작업 중 하나는 데이터 레이어를 업데이트하는 것입니다. 이 작업은 사용자 지정 이벤트가 [!DNL Experience Platform Launch]에서 실행되고 규칙을 트리거하기 전에 수행해야 합니다. 따라서 [!DNL Experience Platform Launch] 에서는 데이터 레이어에서 새 값을 선택하고 Adobe Analytics에 푸시할 수 있습니다.

다음은 SPA에서 보기 변경 또는 작업 시 요소를 변경할 수 있는 샘플 데이터 레이어입니다. 예를 들어, 전체/대부분의 화면 변경 시 새 요소를 [!DNL Experience Platform Launch]에 캡처하고 Adobe Analytics으로 전송할 수 있도록 &quot;[!DNL pageName]&quot; 요소를 변경하는 것이 일반적입니다.

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

## [!DNL Experience Platform Launch]에서 사용자 지정 이벤트 및 수신 대기 {#setting-custom-events-and-listening-in-launch}

페이지에 새 컨텐츠가 로드되거나 사이트에서 작업이 발생하면 규칙을 실행하고 데이터를 [!DNL Analytics]로 전송할 수 있도록 [!DNL Experience Platform Launch]에 알릴 수 있습니다. 이 작업을 수행하는 방법은 두 가지가 있습니다. [!UICONTROL 직접 호출] [!UICONTROL 규칙] 또는 사용자 지정 이벤트.

* [!UICONTROL 직접 ] [!UICONTROL 호출 규칙]: 에서 페이지 [!DNL Experience Platform Launch]에서 직접 호출될 때  [!UICONTROL 실행되는 ]  직접 호출을 설정할 수 있습니다. 페이지 로드 또는 사이트의 작업이 매우 간단하거나, 고유한 경우([!DNL eVar4] 을 X로 설정하고 매번 [!DNL event2] 트리거)를 실행할 수 있는 경우, [!UICONTROL 직접 호출] [!UICONTROL 규칙]을 사용할 수 있습니다. [!DNL Experience Platform Launch] 직접 호출] [!UICONTROL 규칙]을 작성하는 방법에 대한 설명서를 참조하십시오.[!UICONTROL 
* 사용자 지정 이벤트: 추가 기능 및 다른 값이 있는 페이로드를 동적으로 첨부하기 위해서는 사용자 지정 JavaScript 이벤트를 설정하고 [!DNL Experience Platform Launch]에서 수신 대기해야 합니다. 여기서 페이로드를 사용하여 변수를 설정하고 데이터를 Adobe Analytics에 보낼 수 있습니다. 이 기능이 필요할 가능성이 높으므로 이 옵션이 가장 좋은 방법으로 간주됩니다. 그러나 사이트의 각 함수는 가장 적합한 방법을 결정할 수 있습니다. 이 사용자 지정 이벤트 방법을 사용해야 한다고 가정할 경우 이 문서에서 앞으로 이동합니다.

**예:**  [](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html) 이 도움말 문서에는 구현된 샘플 SPA 사이트  [!DNL Analytics] (및 기타 Experience Cloud 솔루션)에 대한 링크와 구현된 내용을 설명하는 문서가 있습니다. 이러한 SPA 예에서는 다음 사용자 지정 이벤트가 사용되었습니다.

* [!DNL event-view-start]: 이 이벤트는 로드 중인 보기/상태의 보기 시작 시 실행해야 합니다.
* [!DNL event-view-end]: 이 이벤트는 보기/상태 변경이 발생하고 페이지의 모든 SPA 구성 요소 로드가 완료된 경우에도 실행해야 합니다. 일반적으로 Adobe Analytics에 대한 호출을 트리거하는 이벤트입니다.
* [!DNL event-action-trigger]: 이 이벤트는 보기/상태 로드를 제외하고 페이지에서 이벤트가 발생할 때 실행해야 합니다. 이는 클릭 이벤트나 보기 변경 없이 더 작은 컨텐츠 변경일 수 있습니다.

페이지 실행 방법/시기에 대한 자세한 내용은 위의 참조 페이지/문서를 참조하십시오. 이와 동일한 이벤트 이름을 사용할 필요는 없지만 여기에 나열된 기능이 권장되는 우수 사례입니다. 다음 비디오에서는 샘플 사이트를 표시하고 [!DNL Experience Platform Launch]에서 사용자 지정 이벤트를 수신 대기하는 위치를 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## [!DNL Experience Platform Launch] [!UICONTROL Rule]에서 s.t() 또는 s.tl() 실행 {#running-s-t-or-s-tl-in-the-launch-rule}

SPA에서 작업할 때 [!DNL Analytics]에 대해 이해해야 할 가장 중요한 사항 중 하나는 `s.t()` 와 `s.tl()` 간의 차이입니다. [!DNL Experience Platform Launch]에서 이러한 메서드 중 하나를 트리거하여 [!DNL Analytics]로 데이터를 전송하지만 각 메서드를 언제 보내야 하는지 알아야 합니다.

* **s.t()**  - &quot;t&quot;는 &quot;track&quot;을 나타내며 일반적인 페이지 보기입니다. URL은 변경되지 않지만 *이(가)*&#x200B;새 &quot;페이지&quot;로 간주할 만큼 보기가 충분히 변경됩니까? 그럴 경우 s.[!DNL pageName] 변수를 설정하고 `s.t()` 을 사용하여 호출을 [!DNL Analytics]에 보냅니다.

* **s.tl()**  - &quot;tl&quot;은 &quot;추적 링크&quot;를 의미하며 일반적으로 전체 화면 전환과 대조적으로 페이지에서 클릭 또는 작은 컨텐츠 변경 사항을 추적하는 데 사용됩니다. 페이지의 변경 사항이 작아서 완전히 새로운 &quot;page&quot;로 간주하지 않는 경우 `s.tl()` 을 사용하고, [!DNL Analytics] 은 이 변수를 무시하므로 s.pageName 변수 설정에 대해 걱정하지 마십시오.

**팁:** 일부 사용자는 화면이 50% 이상 변경되면 페이지 보기로 간주하여 사용해야 한다는 일반 지침을 사용합니다 `s.t()`. 화면 변경 내용이 50% 미만이면 `s.tl()`을 사용하십시오. 그러나 새 &quot;페이지&quot;로 간주하는 대상과 Adobe Analytics에서 사이트를 추적하는 방법은 전적으로 귀하의 책임입니다.

다음 비디오는 Launch by Adobe에서 `s.t()` 또는 `s.tl()`을 트리거하는 위치/방법을 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 변수 지우기 {#clearing-variables}

Adobe Analytics을 사용하여 사이트를 추적할 때 적절한 시간에 [!DNL Analytics]에 올바른 데이터만 보낼 수 있습니다. SPA 환경에서는 [!DNL Analytics] 변수에서 추적된 값이 지속되어 [!DNL Analytics] 로 다시 전송될 수 있으며, 이 값이 더 이상 필요하지 않을 가능성이 있습니다. 이러한 이유로 [!DNL Analytics] [!DNL Launch] 확장에는 변수를 지울 수 있는 함수가 있으므로, 다음 이미지 요청을 실행하고 데이터를 [!DNL Analytics]에 보낼 때 새 슬레이트가 생깁니다.

위의 다이어그램에서는 프로세스 끝에 히트를 통해 전송하는 *after* 변수를 지우는 목록이 있습니다. 실제로 히트가 전송되기 전이나 후에 수행할 수 있지만 [!DNL Experience Platform Launch] 규칙에서 일관되어야 변수를 설정하고 보낸 전이나 후에 항상 변수를 지울 수 있습니다. *전에*&#x200B;변수를 지우려는 경우, `s.t()` 변수를 먼저 지운 다음, 새 변수를 설정한 다음 마지막으로 새 데이터를 [!DNL Analytics]로 보내십시오.

**참고:** 변수를  `s.tl()`지우려면 설정할 변수를 항상  `s.tl()` 함께 사용해야 하므로(의 백그라운드에서 자동 [!DNL linkTrackVars] 으로 추가) [!DNL Analytics]   [!DNL Experience Platform Launch]를 실행할 때 변수가 항상 필요한 것은 아닙니다. 즉, 잘못된 변수는 일반적으로 `s.tl()` 사용 시 로그인하지 않지만 SPA 환경에서 `s.t()` 를 사용할 때는 매우 권장됩니다. 즉, 품질 데이터 수집을 보장하기 위해 SPA 환경에서 `s.t()` 및 `s.tl()` 모두에 변수 지우기 함수를 사용하는 것이 가장 좋습니다.

다음 비디오는 [!DNL Launch]에서 변수를 지울 위치/방법을 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 추가 고려사항 {#additional-considerations}

### [!DNL Experience Platform Launch]의 사용자 지정 코드 창 {#custom-code-windows-in-launch}

[!DNL Launch] [!DNL Analytics] 확장에는 사용자 지정 코드를 삽입할 수 있는 두 개의 위치가 있습니다. [!UICONTROL 라이브러리 관리] 섹션 및 추가 &quot;[!UICONTROL 사용자 지정 코드를 사용하여 추적기 구성]&quot; 섹션.

![Analytics 사용자 지정 코드 창을 시작합니다](assets/launch_analyticscustomcodewindows.png)

이러한 위치 중 하나는 SPA 페이지에서 초기 페이지 로드가 발생할 때 실제로 한 번만 코드를 실행한다는 것을 알고 있어야 합니다. 보기 변경 시 또는 사이트의 작업에 대해 실행할 코드가 필요한 경우 해당 **[!UICONTROL 규칙]**(예: &quot;페이지 로드&quot;에서)에 추가 작업을 추가해야 합니다. event-view-end&quot; [!UICONTROL rule])가 실행되므로 [!UICONTROL 규칙]이 실행될 때마다 코드가 실행됩니다. [!UICONTROL 규칙]에서 해당 작업을 만들 때 *확장 = Core* 및 *작업 유형 = 사용자 지정 코드*&#x200B;를 설정하십시오.

### &quot;하이브리드&quot; SPA/일반 사이트 {#hybrid-spa-regular-sites}

일부 사이트는 &quot;일반&quot; 페이지와 SPA 페이지의 조합입니다. 이 경우 두 페이지 유형에 대해 작동하는 전략을 사용해야 합니다. 사이트에서 사용자 지정 이벤트를 구성하고 [!DNL Experience Platform Launch]에서 규칙을 트리거할 때는 해시 변경 사항 등을 기준으로 페이지에서 [!DNL Analytics]에 두 개의 히트가 발생하지 않도록 주의하십시오. ( [!DNL Experience Platform Launch] 규칙을 트리거하도록 선택한 방식인 경우) 이 경우 Adobe Analytics의 잘못된 데이터를 제공하지 않도록 페이지 보기 중 하나를 표시하지 않아야 합니다.

기능을 별도의 [!UICONTROL 규칙]으로 세분화하여 제어함으로써 더 많은 권한을 갖도록 결정한 경우, 하나의 [!UICONTROL 규칙]을 변경한 경우에도 다른 [!UICONTROL 규칙]에도 적용할 수 있도록 이 작업을 수행한 것을 기억하거나 문서화하십시오. 따라서 [!DNL Analytics] 데이터 무결성을 보호하십시오.

### A4T를 통해 [!DNL Target]과 통합 {#integration-with-target-via-a4t}

여기서 잠깐 설명해주세요 A4T를 사용하여 [!DNL Target]과 통합하는 경우, 동일한 보기의 [!DNL Target] 요청 및 [!DNL Analytics] 요청에 동일한 SDID가 있는지 확인하십시오. 이렇게 하면 데이터가 솔루션에서 제대로 동기화됩니다.

히트를 보려면 디버거 또는 패킷 스니퍼 프로그램을 사용하십시오. [HERE](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj))를 다운로드할 수 있는 Chrome 확장인 Experience Cloud Debugger을 사용할 수도 있습니다. [!DNL Target] 페이지에서 먼저 실행되어야 JavaScript 콘솔 또는 디버거에서도 확인할 수 있습니다.

## 추가 리소스 {#additional-resources}

* [Adobe 포럼에 대한 SPA 토론](https://forums.adobe.com/thread/2451022)
* [Experience Platform Launch에서 SPA을 구현하는 방법을 보여주는 참조 아키텍처 사이트](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
