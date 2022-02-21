---
title: 'Adobe Analytics에서 단일 페이지 애플리케이션(SPA) 추적 시 모범 사례 사용 '
description: 이 문서에서는 Adobe Analytics를 사용하여 단일 페이지 애플리케이션(SPA)을 추적할 때 따르고 알아 두어야 할 몇 가지 모범 사례에 대해 설명합니다. 이 문서는 권장 구현 방식인 Experience Platform Launch의 사용을 중점적으로 다룹니다.
feature: Implementation Basics
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
workflow-type: ht
source-wordcount: '1669'
ht-degree: 100%

---

# Adobe Analytics에서 단일 페이지 애플리케이션(SPA) 추적 시 모범 사례 사용 {#using-best-practices-when-tracking-spa-in-adobe-analytics}

이 문서에서는 Adobe Analytics를 사용하여 단일 페이지 애플리케이션(SPA)을 추적할 때 따르고 알아 두어야 할 몇 가지 모범 사례에 대해 설명합니다. 이 문서는 권장 구현 방식인 Adobe [!DNL Experience Platform Launch]의 사용을 중점적으로 다룹니다.

참고 사항

* 다음 항목은 [!DNL Experience Platform Launch]를 사용하여 사이트에서 구현하고 있다고 가정합니다. [!DNL Experience Platform Launch]를 사용하지 않는 경우에도 고려 사항은 여전히 존재하지만, 이를 구현 방식에 맞게 조정해야 합니다.
* 모든 SPA가 서로 다르므로 필요에 따라 다음 항목 중 몇 가지를 조정해야 할 수도 있지만, SPA 페이지에서 Adobe Analytics를 구현할 때 고려할 필요가 있는 몇 가지 모범 사례를 공유해 드리고자 합니다.

## [!DNL Experience Platform Launch]에서의 SPA 작업에 대한 간단한 다이어그램 {#simple-diagram-of-working-with-spas-in-launch}

![Launch의 Analytics용 SPA](assets/spa_for_analyticsinlaunch.png)

**참고:** 이는 설명된 바와 같이 Adobe Analytics 구현에서 [!DNL Experience Platform Launch]를 사용하여 SPA 페이지를 처리하는 방법에 대한 간단한 다이어그램입니다. 이 페이지의 다음 섹션에서는 신중하게 고려하거나 작업해야 하는 단계 및 문제에 대해 논의합니다.

## 데이터 레이어 설정 {#setting-the-data-layer}

SPA 페이지에 새 콘텐츠가 로드될 때 또는 SPA 페이지에서 작업을 수행할 때, 가장 먼저 해야 할 일 중 하나는 데이터 레이어를 업데이트하는 것입니다. 이 작업은 사용자 정의 이벤트가 실행되고 [!DNL Experience Platform Launch]에서 규칙을 트리거하기 전에 수행하여 [!DNL Experience Platform Launch]가 데이터 레이어에서 새 값을 선택하여 Adobe Analytics로 보내도록 해야 합니다.

다음은 보기 변경 또는 SPA 작업 시 변경될 수 있는 요소인 샘플 데이터 레이어입니다. 예를 들어 전체/주요 화면 변경 시 “[!DNL pageName]” 요소를 변경하여 새 요소를 [!DNL Experience Platform Launch]로 캡처한 다음 Adobe Analytics로 전송하는 것이 일반적입니다.

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

## [!DNL Experience Platform Launch]에서 사용자 정의 이벤트 설정 및 수신 {#setting-custom-events-and-listening-in-launch}

새 콘텐츠를 페이지에 로드할 때 또는 사이트에서 작업을 수행할 때, 이를 [!DNL Experience Platform Launch]에 알려 규칙을 실행하고 [!DNL Analytics]에 데이터를 전송하도록 해야 합니다. 두 가지 방법인 [!UICONTROL 직접 호출] [!UICONTROL 규칙] 또는 사용자 정의 이벤트를 사용하여 이 작업을 수행할 수 있습니다.

* [!UICONTROL 직접 호출] [!UICONTROL 규칙]: [!DNL Experience Platform Launch]에서는 페이지에서 직접 호출 시 실행되는 [!UICONTROL 직접 호출] [!UICONTROL 규칙]을 설정할 수 있습니다. 사이트에서의 페이지 로드 또는 작업이 매우 간단한 경우 또는 고유하고 항상 특정 지침 세트를 실행(항상 [!DNL eVar4]를 “X”로 설정하고 [!DNL event2]를 트리거)할 수 있는 경우, [!UICONTROL 직접 호출] [!UICONTROL 규칙]을 사용할 수 있습니다. [!UICONTROL 직접 호출] [!UICONTROL 규칙] 생성과 관련된 [!DNL Experience Platform Launch] 설명서를 참조하십시오.
* 사용자 정의 이벤트: 페이로드에 다양한 값을 동적으로 첨부하려면 페이로드를 사용하여 변수를 설정하고 Adobe Analytics에 데이터를 전송할 수 있는 [!DNL Experience Platform Launch]에서 사용자 정의 JavaScript 이벤트를 설정하고 수신해야 합니다. 이 기능을 사용해야 할 가능성이 높으므로 이 옵션은 모범 사례로 간주됩니다. 그러나 사이트의 각 기능은 가장 적합한 방식이 무엇인지 결정할 수 있습니다. 여기서는 이 사용자 정의 이벤트 방식을 사용해야 한다고 가정하고 이 문서를 진행하겠습니다.

**예:** [이](https://helpx.adobe.com/kr/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html) 도움말 문서에는 [!DNL Analytics] (및 기타 Experience Cloud 솔루션)가 구현된 샘플 SPA 사이트로의 링크 및 구현 항목을 설명하는 문서가 있습니다. 이 SPA 예에는 다음과 같은 사용자 정의 이벤트가 사용되었습니다.

* [!DNL event-view-start]: 이 이벤트는 로드 중인 보기/상태의 보기 시작 시 실행해야 합니다.
* [!DNL event-view-end]: 이 이벤트는 보기/상태가 변경되었거나 페이지의 모든 SPA 구성 요소의 로드가 완료되어도 실행해야 합니다. 일반적으로 Adobe Analytics로의 호출을 트리거하는 이벤트입니다.
* [!DNL event-action-trigger]: 이 이벤트는 보기/상태 로드를 제외한 모든 이벤트 발생 시 실행해야 합니다. 이는 클릭 이벤트 또는 보기 변경이 없는 소규모 콘텐츠 변경일 수 있습니다.

이벤트 실행 방법/시기에 대한 자세한 내용은 위에서 참조된 페이지/문서를 참조하십시오. 동일한 이벤트 이름을 사용해야 할 필요는 없지만, 여기에 나열된 기능은 권장되는 모범 사례입니다. 다음 비디오는 샘플 사이트 및 [!DNL Experience Platform Launch]에서 사용자 정의 이벤트를 수신하는 위치를 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## [!DNL Experience Platform Launch] [!UICONTROL 규칙]에서 s.t() 또는 s.tl() 실행 {#running-s-t-or-s-tl-in-the-launch-rule}

SPA를 사용하여 작업할 때 [!DNL Analytics]를 이해하는 데 가장 중요한 사항 중 하나는 `s.t()` 및 `s.tl()` 간의 차이점입니다. [!DNL Experience Platform Launch]에서 이러한 방법 중 하나를 트리거하여 데이터를 [!DNL Analytics]에 전송해야 하지만, 그 전에 각 데이터를 전송할 시기를 알아야 합니다.

* **s.t()** - “t”는 “트랙”을 의미하며 일반적인 페이지 조회수를 나타냅니다. URL이 변경되지 않더라도 보기가 새로운 “페이지”로 *간주*&#x200B;될 만큼 변경되었습니까? 그렇다면 s.[!DNL pageName] 변수를 설정한 다음 `s.t()`를 사용하여 [!DNL Analytics]로 호출을 전송하십시오.

* **s.tl()** - “tl”은 “트랙 링크”를 의미하며, 일반적으로 전체 화면 변경과 반대로 클릭 수 또는 페이지에서의 사소한 콘텐츠 변경을 추적하는 데 사용됩니다. 페이지에서의 변경이 사소하여 완전히 새로운 “페이지”로 간주되지 않는 경우 `s.tl()`을 사용하고, [!DNL Analytics]에서 s.pageName 변수를 무시하므로 이를 설정하지 마십시오.

**팁:** 일부 사용자는 일반 가이드라인을 사용하여 화면이 50% 이상 변경되는 경우 페이지 조회수로 간주하여 `s.t()`를 사용합니다. 화면 변경률이 50% 미만인 경우 `s.tl()`을 사용하면 됩니다. 그러나 이는 전적으로 귀하가 새 “페이지”로 간주하는 기준과 Adobe Analytics에서 사이트를 추적하는 방식에 따라 결정됩니다.

다음 비디오는 Adobe에서 제공하는 Launch에서 `s.t()` 또는 `s.tl()`을 트리거하는 위치/방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 변수 지우기 {#clearing-variables}

Adobe Analytics를 사용하여 사이트를 추적할 때, 적절한 데이터만 적절한 시기에 [!DNL Analytics]로 전송하고자 할 것입니다. SPA 환경에서는 [!DNL Analytics] 변수에서 추적되는 값은 유지되어 더 이상 원하지 않을 때에도 [!DNL Analytics]로 다시 전송될 수 있습니다. 이러한 이유로 [!DNL Analytics] [!DNL Launch] 확장 기능에는 변수를 지우고 다음 이미지 요청을 실행하여 [!DNL Analytics]로 데이터를 전송할 때 깨끗한 슬레이트를 유지할 수 있는 기능이 있습니다.

위의 다이어그램의 프로세스 끝에 이 기능이 나열되어 있어 히트를 전송한 *후* 변수를 지울 수 있습니다. 실제로 히트가 전송되기 전과 후 해당 작업을 수행할 수 있지만, [!DNL Experience Platform Launch] 규칙에서 일관성을 지켜 변수를 설정하고 전송하기 전 또는 후에는 항상 변수를 지워야 합니다. `s.t()`를 실행하기 *전*&#x200B;에 변수를 지우려면 먼저 변수를 지운 다음 새 변수를 설정하고 최종적으로 새 데이터를 [!DNL Analytics]로 전송해야 합니다.

**참고:** `s.tl()`은 [!DNL Analytics]에 설정할 변수([!DNL Experience Platform Launch]에서 화면 뒤에 자동으로 추가될 변수)를 전달하기 위해 항상 [!DNL linkTrackVars] 변수와 함께 사용되므로, `s.tl()`을 실행할 때 변수 지우기가 항상 필요한 것은 아닙니다. 즉, `s.tl()`을 사용할 때는 잘못된 변수가 자주 발생하지 않습니다. 단, SPA 환경에서 `s.t()`를 사용할 때에는 이 작업이 매우 권장됩니다. SPA 환경에서는 데이터 수집의 품질 보장을 위해 `s.t()` 및 `s.tl()` 모두에 대해 [변수 지우기] 기능을 사용하는 것이 좋습니다.

다음 비디오는 [!DNL Launch]에서 변수를 지우는 위치/방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 추가 고려 사항 {#additional-considerations}

### [!DNL Experience Platform Launch]의 사용자 정의 코드 창 {#custom-code-windows-in-launch}

[!DNL Launch] [!DNL Analytics] 확장 기능에는 사용자 정의 코드를 삽입할 수 있는 위치인 [!UICONTROL 라이브러리 관리] 섹션과 추가 “[!UICONTROL 사용자 정의 코드를 사용하여 추적자 구성]” 섹션이 있습니다.

![Launch Analytics 사용자 정의 코드 창](assets/launch_analyticscustomcodewindows.png)

이들 위치 중 하나는 SPA 페이지에서 초기 페이지 로드가 발생할 때 코드를 한 번만 실행한다는 사실을 아는 것이 중요합니다. 보기 변경 시 또는 사이트에서 작업 시 코드를 실행해야 하는 경우 적절한 **[!UICONTROL 규칙]**(예: “page load: event-view-end” [!UICONTROL 규칙])에 작업을 추가하여 해당 [!UICONTROL 규칙]이 실행될 때마다 코드가 실행되도록 해야 합니다. [!UICONTROL 규칙]에 작업을 생성할 때, *확장 기능은 코어*&#x200B;로, *작업 유형은 사용자 정의 코드*&#x200B;로 설정하십시오.

### “하이브리드” SPA/일반 사이트 {#hybrid-spa-regular-sites}

일부 사이트는 “일반” 페이지와 SPA 페이지가 조합되어 있습니다. 이 인스턴스에서는 각 페이지 유형에 적용될 수 있는 전략을 사용해야 합니다. 사이트에서 사용자 정의 이벤트를 구성하고 [!DNL Experience Platform Launch]에서 규칙을 트리거할 때, 해시 변경 등에 따라 페이지에서 [!DNL Analytics]로 이동하는 더블 히트가 발생하지 않도록 주의하십시오 (이렇게 해서 [!DNL Experience Platform Launch] 규칙을 트리거하도록 선택한 경우). 이 경우 페이지 조회수 중 하나를 차단하여 Adobe Analytics에서 잘못된 데이터를 제공하지 않도록 해야 합니다.

기능을 개별 [!UICONTROL 규칙]으로 분할하여 보다 효율적으로 관리하기로 결정한 경우 이 작업을 수행했음을 기억/문서화하여 한 [!UICONTROL 규칙]에 대한 변경 내용이 다른 [!UICONTROL 규칙]에도 적용되어 [!DNL Analytics] 데이터 무결성을 보호할 수 있도록 하십시오.

### A4T를 통해 [!DNL Target]과 통합 {#integration-with-target-via-a4t}

여기에 빠른 설명 상자가 있습니다. A4T를 사용하여 [!DNL Target]과 통합하는 경우 동일한 보기 변경 시 [!DNL Target] 요청 및 [!DNL Analytics] 요청이 동일한 SDID를 갖도록 하십시오. 이렇게 하면 데이터가 올바르게 솔루션에 동기화될 수 있습니다.

히트를 보려면 디버거 또는 패킷 스니퍼 프로그램을 사용하십시오. [여기](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)에서 다운로드할 수 있는 Chrome 확장 프로그램인 Experience Cloud Debugger를 사용할 수도 있습니다. JavaScript 콘솔 또는 디버거에서 확인할 수 있도록 [!DNL Target]을 페이지에서 가장 먼저 실행하여 해야 합니다.

## 추가 리소스 {#additional-resources}

* [Adobe 포럼에서의 SPA 토론](https://forums.adobe.com/thread/2451022)
* [Experience Platform Launch에서의 SPA 구현 방법에 대한 참조 아키텍처 사이트](https://helpx.adobe.com/kr/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
