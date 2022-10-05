---
title: 단일 페이지 애플리케이션에 대한 구현 우수 사례(SPA)
description: SPA(단일 페이지 애플리케이션)에서 Adobe Analytics을 구현하는 우수 사례를 알아봅니다. 여기에는 Experience Platform 태그인 권장 구현 방법이 포함됩니다.
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
source-git-commit: d78c3351d2a98704396ceb8f84d123dd463befe5
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 2%

---

# 단일 페이지 애플리케이션에 대한 구현 우수 사례(SPA) {#implementation-best-practices-for-single-page-appliations}

구현에 대한 몇 가지 우수 사례 알아보기 [!DNL Adobe Analytics] 단일 페이지 애플리케이션(SPA)에서. 여기에는 [!DNL Experience Platform Tags]를 설정하는 것이 좋습니다.

참고 사항

* 아래 콘텐츠는 [!DNL Experience Platform Tags] 사이트에서 Adobe Analytics을 구현하려면 다음을 수행하십시오. 이러한 고려 사항은 다음과 같은 경우에 적용됩니다 [!DNL Experience Platform Tags] 를 사용하지 않으므로 구현 방법에 맞게 조정해야 합니다.
* SPA에는 차이가 있으므로 필요에 가장 잘 맞게 접근 방식을 조정해야 합니다.

## [!DNL Experience Platform Tags]에서의 SPA 작업에 대한 간단한 다이어그램 {#simple-diagram-of-working-with-spas-in-tags}

![태그의 analytics용 SPA](assets/spa_for_analyticsinlaunch.png)

**참고:** 이 다이어그램은 를 사용하여 Adobe Analytics 구현에서 SPA 페이지를 처리하는 방법을 간략히 보여줍니다 [!DNL Experience Platform Tags]. 다음 섹션에서는 고려해야 할 단계 및 문제를 식별합니다.

## 데이터 레이어 설정 {#set-the-data-layer}

새 컨텐츠가 로드되거나 SPA 페이지에서 작업이 발생하면 *먼저 데이터 레이어 업데이트*. 이런 일이 일어나야 합니다 **이전** 규칙을 트리거하는 사용자 지정 이벤트 [!DNL Experience Platform Tags]. 이렇게 하면 데이터 계층의 올바른 값이 태그로 푸시된 다음 Adobe Analytics이 됩니다.

다음은 샘플 데이터 레이어입니다. 이러한 요소 중 하나는 SPA 페이지에서 수행한 작업이 있는 경우 보기의 초기 보기 또는 후속 변경을 기준으로 변경될 수 있습니다. 예를 들어, 전체 또는 대부분 보기 변경 시 고유한 &quot;[!DNL pageName]Adobe Analytics 보고의 보기를 구분하기 위한 값.

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

## 에서 사용자 지정 이벤트를 설정하고 이러한 이벤트를 수신합니다. [!DNL Experience Platform Tags] {#setting-custom-events-and-listening-in-tags}

새 컨텐츠가 로드되거나 SPA 페이지에서 작업이 발생하면 데이터를 보내는 규칙을 실행하도록 Experience Platform 태그에 정보를 제공해야 합니다 [!DNL Analytics]. 이에 대한 두 가지 접근 방법이 있습니다. [!UICONTROL 직접 호출 규칙] 또는 사용자 지정 이벤트 를 사용할 수 있습니다.

* [!UICONTROL 직접 호출 규칙]: 설정 [!UICONTROL 직접 호출 규칙] 페이지에서 바로 호출될 때 실행됩니다. 페이지 로드 또는 작업이 간단하거나 고유하며 매번 특정 지침 세트를 실행할 수 있는 경우(예: [!DNL eVar4] X 및 트리거하기 [!DNL event2] 매번) 그러면 이 방법이 적절합니다. 을(를) 참조하십시오. [!DNL Experience Platform Tags] 작성에 대한 자세한 설명서 [!UICONTROL 직접 호출 규칙].
* 사용자 지정 이벤트: SPA 페이지에서 발생하는 이벤트에 대해 고유한 값이 있는 페이로드를 동적으로 첨부해야 하는 경우 사용자 지정 JavaScript 이벤트를 사용하고 의 응답을 수신합니다. [!DNL Experience Platform Tags]. 페이로드를 사용하여 태그에서 데이터 요소 및 Analytics 변수를 설정합니다. 이 방법은 일반적으로 SPA에 널리 사용되므로 이 방법이 가장 좋습니다. 아래 예제는 사용자 지정 이벤트 메서드를 사용합니다.

**예:** [이](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html) 도움말 문서, 를 구현하는 샘플 SPA 사이트에 대한 링크가 있습니다 [!DNL Analytics] 및 기타 Experience Cloud 솔루션. 이러한 예에서 다음 사용자 지정 이벤트가 사용됩니다.

* **[!DNL Event-view-start]**: 로드하는 보기/상태의 보기 시작 시 실행됩니다.
* **[!DNL Event-view-end]**: 보기/상태 변경이 발생하고 페이지의 모든 SPA 구성 요소 로드가 완료되면 실행됩니다. 이 이벤트는 일반적으로 Adobe Analytics으로 데이터를 보내는 이벤트입니다.
* **[!DNL Event-action-trigger]**: 보기/상태 로드를 제외하고 페이지에서 이벤트가 발생할 때 실행됩니다. 예를 들면 클릭 이벤트나 보기 변경 없이 더 작은 컨텐츠 변경이 있습니다.

이러한 이벤트가 실행되는 방법과 시기에 대한 자세한 내용은 위에서 참조되는 페이지 및 문서를 참조하십시오. 구현에서 동일한 이벤트 이름을 사용할 필요는 없습니다. 사용되는 메서드에 대한 기능 사용 사례는 각각에 대해 권장되는 우수 사례로서 이해하는 데 중요합니다. 다음 비디오에서는 의 샘플 SPA 페이지 및 샘플 코드를 보여 줍니다. [!DNL Experience Platform Tags] 사용자 지정 이벤트를 수신합니다.

>[!VIDEO](https://video.tv.adobe.com/v/23024/?quality=12)

## 에서 s.t() 또는 s.tl()을 실행합니다. [!DNL Experience Platform Tags] {#running-s-t-or-s-tl-in-the-launch-rule}

에 대한 중요한 개념 [!DNL Analytics] SPA을 사용할 때의 차이점은 다음과 같습니다 `s.t()` 및 `s.tl()`. 코드에서 [!DNL Experience Platform Tags] 데이터를에 보내기 [!DNL Analytics].

* **s.t()** - &quot;t&quot;는 &quot;track&quot;을 나타내고, 이는 페이지 보기를 나타냅니다. 보기가 충분히 변경되면  *고려 사항* 새 &quot;페이지&quot;인 경우 이 호출을 사용하십시오. 고유한 값을 로 설정합니다. [!DNL s.pageName] 변수 및 사용 `s.t()` 로 데이터를 보내려면 [!DNL Analytics].

* **s.tl()** - &quot;tl&quot;은 &quot;추적 링크&quot;를 의미하며 링크 클릭 또는 작은 컨텐츠 변경을 나타냅니다. 뷰 변경이 최소한으로 수행되면 `s.tl()` 상호 작용에 대한 고유한 값을에 전달합니다. [!DNL Analytics]. 전달된 이 변수는 표시되지 않습니다 [!DNL s.pageName]인 경우 Analytics에서 무시되므로 `s.tl()` 호출이 수신됩니다.

**팁:** 일반적인 지침으로서, 화면이 50% 이상 변경되는 경우 `s.t()` 페이지 보기 호출. 그렇지 않으면 `s.tl()`. 그러나 새 &quot;페이지&quot;를 구성하는 작업과 Adobe Analytics 보고서에 나타낼 방법을 고려할 때 판단을 사용하십시오.

다음 비디오에서는 트리거되는 위치와 방법을 보여줍니다 `s.t()` 또는 `s.tl()` 태그에 가깝게 포함했습니다.

>[!VIDEO](https://video.tv.adobe.com/v/23048/?quality=12)

## 변수 지우기 {#clear-variables}

올바른 데이터를에 보내기 [!DNL Analytics] 적시에 SPA 환경에서 은 [!DNL Analytics] 가 지속되어 [!DNL Analytics]: 사용자가 더 이상 원하지 않는 경우 이 문제가 발생할 수 있습니다. 함수는 [!DNL Analytics] [!DNL Tags] 확장을 사용하여 다음 호출에서 로 데이터를 잘못 보내지 않도록 합니다. [!DNL Analytics].

위의 다이어그램은 지워진 변수를 보여줍니다 *after* 데이터를 보냅니다. 하지만 실제로는 호출 전 OR 후에 이러한 상황이 발생할 수 있으므로 [!DNL Experience Platform Tags] 를 설정하는 것이 좋습니다. 변수를 지우는 경우 *이전* 실행 `s.t()`를 호출한 직후 새 변수를 설정한 다음 새 데이터를으로 보냅니다 [!DNL Analytics].

**참고:** 실행 시 변수 지우기가 항상 필요한 것은 아닙니다 `s.tl()`. 이 호출에는 [!DNL linkTrackVars] 변수를 [!DNL Analytics] 설정할 변수입니다. 이 작업은 자동으로 수행됩니다 [!DNL Experience Platform Tags] 구성 사용. 따라서 잘못된 변수가 `s.t()` SPA 환경에서 을 호출합니다. 가장 깨끗하고 안정적인 구현을 위해 SPA 환경의 두 호출에 clear variables 함수를 사용하는 것이 더 쉽습니다.

다음 비디오에서는에서 변수를 지울 위치와 방법을 보여줍니다 [!DNL Tags].

>[!VIDEO](https://video.tv.adobe.com/v/23049/?quality=12)

## 추가 고려 사항 {#additional-considerations}

### 의 사용자 지정 코드 창 [!DNL Experience Platform Tags] {#custom-code-windows-in-tags}

에서 [!DNL Tags] [!DNL Analytics] 확장에는 사용자 지정 코드를 삽입할 수 있는 두 개의 위치가 있습니다. &quot;[!UICONTROL 라이브러리 관리]&quot; 및 &quot;[!UICONTROL 사용자 지정 코드를 사용하여 추적기 구성]&quot; 섹션을 참조하십시오.

![태그 Analytics 사용자 지정 코드 창](assets/launch_analyticscustomcodewindows.png)

이러한 위치 중 하나는 SPA 페이지를 로드하는 초기 페이지에 대해 포함된 코드를 한 번 실행합니다. 보기 또는 작업 변경 시 코드를 실행해야 하는 경우 해당 코드를 적절한 **[!UICONTROL 규칙]** (예: &quot;페이지 로드: event-view-end&quot; 규칙입니다. [!UICONTROL 규칙] 가 실행됩니다. 에서 이 작업을 만들 때 [!UICONTROL 규칙], 설정 *확장 = 코어* 및 *작업 유형 = 사용자 지정 코드*.

### &quot;하이브리드&quot; SPA 및 기존 사이트 {#hybrid-spa-and-traditional-sites}

일부 사이트는 기존 페이지와 SPA 페이지의 조합으로 구성됩니다. 이 경우 두 페이지 유형에 대해 작동하는 전략을 사용합니다. 사이트에서 사용자 지정 이벤트를 구성하고 의 규칙을 트리거할 때 [!DNL Experience Platform Tags]: 이중 히트가 [!DNL Analytics] 해시 변경 사항 등을 기반으로 합니다. 이 경우 중복 데이터가 Adobe Analytics으로 전달되지 않도록 페이지 보기 중 하나를 표시하지 않습니다.

기능을 고유한 로 구분하기로 결정하는 경우 [!UICONTROL 규칙] 더 세밀하게 제어하려면 이 작업을 수행했음을 문서화하는 것을 잊지 마십시오. 다른 것으로 바꾸시면 [!UICONTROL 규칙]를 설정하는 경우 다른 것과 동일한 변경 작업을 수행합니다 [!UICONTROL 규칙].

### 통합 [!DNL Target] a4T 사용 {#integration-with-target-using-a4t}

통합 시 [!DNL Target] A4T를 사용하여 [!DNL Target] 및 [!DNL Analytics] 동일한 보기 또는 작업에서 전송된 요청은 동일한 SDID 매개 변수 값을 전달합니다. 이렇게 하면 데이터가 백엔드에서 제대로 동기화됩니다.

이러한 히트를 보려면 디버거 또는 패킷 모니터링 도구를 사용하십시오. Adobe은 이 용도로 Experience Platform 디버거를 제공합니다. Chrome 확장 프로그램은 [여기에서 다운로드](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob?hl=en). [!DNL Target] 페이지에서 먼저 실행해야 합니다. 이 점은 디버거에서도 확인할 수 있습니다.

## 추가 리소스 {#additional-resources}

* [Adobe 포럼에서의 SPA 토론](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-launch/best-practices-for-single-page-apps/m-p/267940)
* [Experience Platform Launch에서의 SPA 구현 방법에 대한 참조 아키텍처 사이트](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)
