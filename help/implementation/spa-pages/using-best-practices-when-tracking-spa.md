---
title: 단일 페이지 애플리케이션(SPA)에 대한 구현 모범 사례
description: 단일 페이지 애플리케이션(SPA)에서 Adobe Analytics를 구현하기 위한 몇 가지 모범 사례에 대해 알아봅니다. 여기에는 권장 구현 방식인 Experience Platform Tags 사용이 포함됩니다.
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
source-git-commit: 8fc641743bc9e07b838a22ca64ccc15344d52764
workflow-type: ht
source-wordcount: '1313'
ht-degree: 100%

---

# 단일 페이지 애플리케이션(SPA)에 대한 구현 모범 사례 {#implementation-best-practices-for-single-page-appliations}

단일 페이지 애플리케이션(SPA)에서 [!DNL Adobe Analytics]를 구현하기 위한 몇 가지 모범 사례에 대해 알아봅니다. 여기에는 권장 구현 방식인 [!DNL Experience Platform Tags] 사용이 포함됩니다.

참고 사항

* 아래의 콘텐츠는 [!DNL Experience Platform Tags]를 참조하여 사이트에서 Adobe Analytics를 구현합니다. 이러한 고려 사항은 [!DNL Experience Platform Tags]가 사용되지 않은 경우 적용되므로 구현 방식에 맞게 조정해야 합니다.
* SPA가 서로 다르므로 최대한 필요에 따라 접근 방식을 조정해야 합니다.

## [!DNL Experience Platform Tags]에서의 SPA 작업에 대한 간단한 다이어그램 {#simple-diagram-of-working-with-spas-in-tags}

![Tags의 Analytics용 SPA](assets/spa_for_analyticsinlaunch.png)

**참고:** 이는 Adobe Analytics 구현에서 [!DNL Experience Platform Tags]를 사용하여 SPA 페이지를 처리하는 방법에 대한 간단한 다이어그램입니다. 다음 섹션에서 고려해야 할 단계 및 문제를 식별합니다.

## 데이터 레이어 설정 {#set-the-data-layer}

SPA 페이지에 새 콘텐츠가 로드되거나 SPA 페이지에서 작업을 수행할 때, *먼저 데이터 레이어를 업데이트합니다*. 규칙을 트리거하는 사용자 정의 이벤트가 [!DNL Experience Platform Tags]에서 실행되기 **전에** 작업을 수행해야 합니다. 이렇게 하면 데이터 레이어의 올바른 값이 Tags에 푸시된 다음 Adobe Analytics에 푸시됩니다.

다음은 샘플 데이터 레이어입니다. SPA 페이지에서 수행된 작업을 고려하여 다음 요소 중 하나가 초기 보기 또는 후속 보기에 따라 변경될 수 있습니다. 예를 들어 전체/주요 보기 변경 시 Adobe Analytics 보고에서 보기 사이를 구분하도록 고유 “[!DNL pageName]“ 값을 전달하는 것이 일반적입니다.

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

## 사용자 정의 이벤트를 설정하고 [!DNL Experience Platform Tags]에서 해당 이벤트를 수신합니다. {#setting-custom-events-and-listening-in-tags}

SPA 페이지에 새 콘텐츠가 로드되거나 SPA 페이지에서 작업을 수행할 때, [!DNL Analytics]에 데이터를 전송하는 규칙을 실행하도록 Experience Platform Tags에 알림을 전송해야 합니다. [!UICONTROL 직접 호출 규칙] 또는 사용자 정의 이벤트의 두 가지 접근 방식을 사용하여 이 작업을 수행할 수 있습니다.

* [!UICONTROL 직접 호출 규칙]: 페이지에서 직접 호출 시 실행되는 [!UICONTROL 직접 호출 규칙]을 설정합니다. 페이지 로드 또는 작업이 간단하거나 고유하고 항상 특정 지침 세트를 실행(예: 항상 [!DNL eVar4]를 “X”로 설정하고 [!DNL event2]를 트리거)할 수 있는 경우, 이 접근 방식이 적합합니다. [!UICONTROL 직접 호출 규칙] 만들기에 대한 자세한 내용은 [!DNL Experience Platform Tags] 설명서를 참조하십시오.
* 사용자 정의 이벤트: SPA 페이지에서 발생하는 이벤트에 대해 고유 값을 동적으로 첨부해야 하는 경우, 사용자 정의 JavaScript 이벤트를 사용한 다음 [!DNL Experience Platform Tags]에서 수신합니다. 페이로드를 사용하여 Tags에서 데이터 요소 및 Analytics 변수를 설정합니다. 이 메서드는 SPA에 일반적으로 사용되므로 모범 사례로 간주됩니다. 아래의 예제에서 사용자 정의 이벤트 메서드를 사용합니다.

**예:** [이](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html) 도움말 문서에는 [!DNL Analytics] 및 기타 Experience Cloud 솔루션을 구현하는 샘플 SPA 사이트로의 링크가 있습니다. 이 예제에는 다음과 같은 사용자 정의 이벤트가 사용됩니다.

* **[!DNL Event-view-start]**: 로드되는 보기/상태의 보기 시작 시 실행됩니다.
* **[!DNL Event-view-end]**: 보기/상태가 변경되고 페이지의 모든 SPA 구성 요소 로드가 완료되면 실행됩니다. 일반적으로 Adobe Analytics에 데이터를 전송하는 이벤트입니다.
* **[!DNL Event-action-trigger]**: 보기/상태 로드를 제외한 모든 이벤트 발생 시 실행됩니다. 이 예제에는 클릭 이벤트 또는 보기 변경이 없는 소규모 콘텐츠 변경이 포함됩니다.

이벤트 발생 방법 및 시기에 대한 자세한 내용은 위에서 참조된 페이지 및 문서를 참조하십시오. 구현에서 동일한 이벤트 이름을 사용할 필요가 없습니다. 사용된 메서드에 대한 기능 사용 사례는 각 메서드의 권장 모범 사례로 이해해야 합니다. 다음 비디오는 사용자 정의 이벤트를 수신하는 [!DNL Experience Platform Tags]에서 샘플 SPA 페이지와 샘플 코드를 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12&learn=on)

## [!DNL Experience Platform Tags]에서 s.t() 또는 s.tl() 실행 {#running-s-t-or-s-tl-in-the-launch-rule}

SPA로 작업 시 [!DNL Analytics]를 이해하는 데 필요한 중요 개념은 `s.t()` 및 `s.tl()` 간의 차이점입니다. 코드는 [!DNL Experience Platform Tags]에서 이 메서드 둘 중 하나를 트리거하여 [!DNL Analytics]에 데이터를 전송합니다.

* **s.t()** - “t”는 “트랙”을 의미하며 페이지 조회수를 나타냅니다. 새 “페이지”로 *간주*&#x200B;되는 보기가 충분히 변경된 경우, 이 호출을 사용하십시오. 고유 값을 [!DNL s.pageName] 변수로 설정한 다음 `s.t()`를 사용하여 데이터를 [!DNL Analytics]에 전송합니다.

* **s.tl()** - “tl”은 “트랙 링크”를 의미하며 링크 클릭 또는 사소한 콘텐츠 변경을 나타냅니다. 보기 변경이 최소인 경우, `s.tl()`를 사용하여 상호 작용에 대한 고유 값을 [!DNL Analytics]에 전달합니다. 전달된 해당 변수는 `s.tl()` 호출이 수신되면 Analytics에서 무시되므로 [!DNL s.pageName]이(가) 아닙니다.

**팁:** 일반적인 가이드라인으로서, 화면이 50% 이상 변경되는 경우에는 `s.t()` 페이지 보기 호출을 사용하십시오. 그렇지 않으면 `s.tl()`을 사용하십시오. 단, 새 “페이지”를 구성하는 작업과 Adobe Analytics 보고서에 표시하는 방식을 고려할 때는 잘 판단해야 합니다.

다음 비디오는 Tags에서 `s.t()` 또는 `s.tl()`을 트리거하는 위치와 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12&learn=on)

## 변수 지우기 {#clear-variables}

적절한 시기에 [!DNL Analytics]에 올바른 데이터를 전송합니다. SPA 환경에서는 [!DNL Analytics] 변수에 저장되는 값이 유지되어 더 이상 원하지 않을 때에도 [!DNL Analytics]에 다시 전송됩니다. 다음 호출이 데이터를 [!DNL Analytics]에 잘못 전송하지 않도록 변수를 지우는 함수가 [!DNL Analytics] [!DNL Tags] 확장자에 존재합니다.

데이터 전송 *이후* 위의 다이어그램은 지워진 변수를 보여 줍니다. 단, 이 작업은 구현 간소화를 위해 호출이 [!DNL Experience Platform Tags] 규칙에서 일관성을 유지하기 전 또는 후에 실제로 발생할 수 있습니다. `s.t()` 실행 *이전*&#x200B;에 변수를 지우는 경우, 호출 직후 변수를 새로 설정한 다음 계속해서 새 데이터를 [!DNL Analytics]에 전송합니다.

**참고:** `s.tl()`을 실행할 때 변수 지우기가 항상 필요한 것은 아닙니다. 이 호출에서 [!DNL linkTrackVars] 변수를 사용하여 [!DNL Analytics] 설정할 변수를 지시할 수 있습니다. 구성을 통해 [!DNL Experience Platform Tags] 자동으로 발생합니다. SPA 환경에서 `s.t()` 호출을 사용하는 비헤이비어와 달리 잘못된 변수가 설정되지 않습니다. 가장 간소하고 안정적인 구현을 이루기 위해서 SPA 환경에서 두 호출에 변수 지우기 함수를 사용하는 것이 더 쉬울 수 있습니다.

다음 비디오는 [!DNL Tags]에서 변수를 지우는 위치 및 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12&learn=on)

## 추가 고려 사항 {#additional-considerations}

### [!DNL Experience Platform Tags]의 사용자 정의 코드 창 {#custom-code-windows-in-tags}

[!DNL Tags] [!DNL Analytics] 확장 기능에는 사용자 정의 코드를 삽입할 수 있는 위치인 “[!UICONTROL 라이브러리 관리]” 섹션과 “[!UICONTROL 사용자 정의 코드를 사용하여 추적자 구성]” 섹션이 있습니다.

![Tags Analytics 사용자 정의 코드 창](assets/launch_analyticscustomcodewindows.png)

이들 위치 중 하나에서 SPA 페이지의 초기 페이지 로드 시 한 번 포함된 코드가 실행됩니다. 보기 또는 작업 변경 시 코드를 실행해야 하는 경우, [!UICONTROL 규칙]이 실행될 때마다 코드가 실행되도록 적절한 **[!UICONTROL 규칙]**(예: “page load: event-view-end” 규칙)으로 해당 코드를 구현합니다. [!UICONTROL 규칙]에서 작업을 생성하는 경우, *확장 기능은 코어*&#x200B;로, *작업 유형은 사용자 정의 코드*&#x200B;로 설정합니다.

### “하이브리드” SPA 및 기존 사이트 {#hybrid-spa-and-traditional-sites}

일부 사이트는 “기존” 페이지와 SPA 페이지의 조합으로 구성됩니다. 이 인스턴스에서는 각 페이지 유형에 적용될 수 있는 전략을 사용합니다. 사이트에서 사용자 정의 이벤트를 구성하고 [!DNL Experience Platform Tags]에서 규칙을 트리거하는 경우, 해시 변경 등에 따라 더블 히트가 [!DNL Analytics]에 전송되지 않도록 해야 합니다. 이 경우 중복 페이지가 Adobe Analytics에 전달되지 않도록 페이지 보기 중 하나를 표시하지 않습니다.

추가 제어를 위해 기능을 고유 [!UICONTROL 규칙]으로 분리하고자 하는 경우 이 작업을 수행했음을 기억하고 문서화합니다. 하나의 [!UICONTROL 규칙]을 변경하는 경우 다른 [!UICONTROL 규칙]도 동일하게 변경해야 합니다.

### A4T를 사용하여 [!DNL Target]과 통합 {#integration-with-target-using-a4t}

A4T를 사용하여 [!DNL Target]과 통합하는 경우, 동일한 보기 또는 작업에 전송된 [!DNL Target] 및 [!DNL Analytics] 요청으로 동일한 SDID 매개변수 값이 전달되고 있는지 확인합니다. 이렇게 하면 백엔드에서 데이터가 올바르게 동기화될 수 있습니다.

히트를 보려면 디버거 또는 패킷 모니터링 도구를 사용하십시오. 이러한 목적으로 Adobe는 Experience Platform Debugger를 제공합니다. [여기서 다운로드](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob?hl=en)할 수 있는 Chrome 확장 기능입니다. [!DNL Target]을 페이지에서 가장 먼저 실행하여 해야 합니다. 디버거에서도 확인할 수 있습니다.

## 추가 리소스 {#additional-resources}

* [Adobe 포럼에서의 SPA 토론](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-launch/best-practices-for-single-page-apps/m-p/267940)
* [Experience Platform Launch에서의 SPA 구현 방법에 대한 참조 아키텍처 사이트](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)
