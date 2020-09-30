---
title: 고객 여정 IQ 이해 및 사용 - 디바이스 간 분석
description: 사용자가 브랜드와 상호 작용하는 경우 다양한 방법으로 다양한 장치에서 이를 수행합니다. 크로스 디바이스 분석은 Adobe Experience Platform ID 서비스와 통합되므로 장치가 사람에게 매핑되는 방식을 식별할 수 있습니다. 그런 다음 이러한 인텔리전스를 활용하여 사용자 동작에 대한 크로스 디바이스 보기를 만듭니다. 따라서 장치가 아닌 사람에 대한 분석을 수행할 수 있습니다.
feature: cda
topics: null
audience: all
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
translation-type: tm+mt
source-git-commit: 24ad92b0ccdf1112e3ed4a0968cd47db757598c3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 이해 및 사용 [!DNL Journey IQ] - 장치 간 분석

사용자가 브랜드와 상호 작용하는 경우 다양한 방법으로 다양한 장치에서 이를 수행합니다. 크로스 디바이스 분석은 디바이스 [!DNL Adobe Experience Platform Identity Service] 가 사람에게 매핑되는 방식을 식별하기 위해 그런 다음 이러한 인텔리전스를 활용하여 사용자 동작에 대한 크로스 디바이스 보기를 만듭니다. 따라서 장치가 아닌 사람에 대한 분석을 수행할 수 있습니다.

## 장치 간 분석 개요

### 내 장치가 아님

사용자가 브랜드와 상호 작용하는 경우 다양한 방법으로 여러 &quot;표면&quot; 또는 &quot;장치&quot;에서 그렇게 합니다. PC 또는 모바일 장치에서 웹 브라우저를 사용하거나 모바일 앱을 사용할 수 있습니다. 쿠키를 기반으로 데이터 수집에서 성장한 기존 디지털 분석에서는 이러한 각 표면은 고유한 &quot;방문자&quot;로 표현됩니다. 즉, 각 인간 사용자가 여러 고유 방문자로 표시됩니다.

예를 들어 이사벨이 귀사의 브랜드에 다음과 같은 방식으로 인터랙션했다고 가정해 봅시다.

*이사벨은 세 명의 방문자*![로 전통적인 분석 여행](assets/cda-isabelle-journey-traditional-analytics.png)

이자벨의 여행은 전통적인 분석으로 세 조각으로 분열된다. 세 명의 고유 방문자로 나타나서, 각각 다른 장치를 사용하여 분리된 작업을 수행합니다. 이사벨의 상호 작용에 대한 통합된 상호 장치 보기가 필요합니다. [!DNL Journey IQ: Cross-Device Analytics] 이 보기를 제공합니다.

*이사벨은 한 사람*![의 크로스 디바이스 분석 여정이다](assets/cda-isabelle-journey-cross-device-analytics.png)

### 향상된 분석 기능을 제공하는 크로스 디바이스 보기

이사벨의 행동에 대해 사람 중심의, 장치 간 뷰를 갖는 것은 당신의 분석에 큰 차이를 만들 수 있다. 예를 들어 기존 방문자 기반 접근 방식은 마케팅 채널 효과를 완벽하게 파악하지 못합니다. 이사벨의 여정을 다시 한번 살펴보자. 어느 채널에서 그녀의 상품 뷰와 구매에 대한 크레딧을 받는지에 집중한다. 간단한 용도로 [!UICONTROL 마지막 터치] 기여도 분석을 사용하지만 같은 문제는 이사벨의 행동을 개별 방문자로 나누는 어트리뷰션 모델을 통해 발생합니다. 방문자 기반의 기존 보기를 사용하면 매우 다르고 잘못된 결과가 나옵니다.

*기존 분석과 크로스 디바이스 분석*![채널 어트리뷰션 비교](assets/channel-attribution.png)

디바이스 간 보기를 통해 이메일 채널은 제품 뷰와 구매 모두에 대한 크레딧을 받게 됩니다. 이러한 크레딧은 이사벨의 실제 경험을 보다 정확하게 나타냅니다.

다음 사항에 대한 자세한 내용을 살펴보십시오.

* How [!DNL Cross-Device Analytics] Works
* 사전 요구 사항 [!DNL Cross-Device Analytics]
* 장치 간 데이터 해석
* Analysis Workspace의 장치 간 데이터 분석

## How [!DNL Cross-Device Analytics] Works

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 는 [!DNL Adobe Experience Platform Identity Service][!DNL Co-op Graph] [또는 장치가 사람에게 매핑되는 방식을 식별하기 위해](https://docs.adobe.com/content/help/ko-KR/device-co-op/using/home.html) [!DNL Private Graph] 과 통합됩니다. 그런 다음 이러한 인텔리전스를 활용하여 사용자 동작에 대한 크로스 디바이스 보기를 만듭니다. CDA에는 기업에서 귀사의 브랜드와의 상호 작용에서 여러 장치의 사용 방식과 고객 경험을 이해할 수 있도록 지원하는 독보적인 기능과 툴이 포함되어 있습니다. Adobe Experience Manager는 개인 고객 분석 및 크로스 디바이스 어트리뷰션, 세분화 및 경로 분석에 대한 심층적인 통찰력을 제공하는 Analysis Workspace의 한 레이어로 [!UICONTROL 폴아웃], [!DNL Flow][!DNL Cohort], [!DNL Segment IQ][!DNL Attribution IQ]및같은 강력한 툴을 제공합니다.

### 다음 [!DNL Cross-Device Virtual Report Suite]

CDA는 특별한 종류의 장치 간 [[!UICONTROL 가상 보고서 세트를 통해 제공됩니다]](https://docs.adobe.com/content/help/ko-KR/analytics/components/virtual-report-suites/vrs-about.html). 이를 통해 조직 전체에 크로스 디바이스 분석을 적용할 때 원본 디바이스 기반의 보고서 세트를 계속 사용할 수 있습니다. CDA VRS를 설정하는 방법은 간단합니다.

VRS 빌더 중 한 단계에서 CDA가 활성화된 Adobe에 의해 구성된 [!UICONTROL 보고서 세트를] 선택합니다.

*CDA 지원 기본(소스)[!UICONTROL 보고서 세트]*![[!UICONTROL 가상 보고서 세트] 1단계](assets/cda-vrs-step-one.png)

그런 다음 [!UICONTROL 보고서 시간 처리를] 활성화하고 [!UICONTROL 장치 간 스티칭을 활성화합니다].

*보고서[!UICONTROL 시간 처리]및[!UICONTROL 장치 간 연결]*![[!UICONTROL 가상 보고서 세트] 2단계사용](assets/cda-vrs-step-two.png)

VRS 설정을 완료하고 저장합니다. CDA VRS는 다음과 같이 Analysis Workspace 옆에 특수 아이콘이 표시됩니다.

*Analysis Workspace 가상 보고서 세트*![[!UICONTROL 3단계에서 CDA VRS를] 선택합니다.](assets/cda-vrs-step-three.png)

>[!TIP]
>
>CDA 사용 기반 [!UICONTROL 보고서 세트] 맨 위에 원하는 만큼 CDA 가상 보고서 세트를 만들 수 있습니다.

### 작업 내역 다시 설정

사용자가 로그인하거나 장치를 식별하거나 장치를 함께 매핑하는 데 시간이 오래 [!DNL Co-op Graph] 걸릴 수 [!DNL Private Graph] 있습니다. CDA는 30일 동안의 룩백 창을 활용하여 이전에 식별되지 않은 방문자를 이전 방문자로 최대 30일까지 재설정할 수 있습니다.

어떻게 도움이 됩니까? 이사벨의 위에서 있었던 논의들을 기억하라:

![[!DNL Cross-Device Analytics] 여정](assets/cda-isabelle-journey-cross-device-analytics.png)

이사벨이 이사벨을 매입하기 바로 전까지 이사벨을 로그인하지 않고 이사벨이 [!DNL Co-op Graph] 혹은 이사벨이 이사벨을 사게 될 때까지 이사벨의 장치들을 함께 [!DNL Private Graph] 지도하지 않았을 가능성이 있다. 그러나 CDA의 30일 동안의 룩백을 통해 CDA는 이사벨의 과거 행동을 한 사람 수준에서 다시 볼 수 있게 해 주므로, 여러분이 필요로 하는 그녀의 여정에 대한 크로스 디바이스 보기를 제공할 수 있다.

>[!NOTE]
>
>내역을 재설정할 수 있으므로, 이는 CDA가 활성화된 [!UICONTROL 가상 보고서 세트에서 시간이 지남에 따라 데이터가 변경될 수 있음을 의미합니다]. CDA 기반 분석에서 인사이트를 전달하면서 이를 염두에 두십시오.

## 크로스 디바이스 [!UICONTROL 분석을 위한 전제 조건]

CDA는 [[!DNL Analytics Ultimate]에 포함되어 있습니다](https://helpx.adobe.com/legal/product-descriptions/adobe-analytics.html). 2019년 9월부터 아래 [!DNL Analytics Ultimate] 사전 요구 사항을 충족하는 고객은 CDA를 사용할 수 있습니다. CDA의 사전 요구 사항은 다음과 같습니다.

* 회사는 [!DNL Adobe Experience Platform Identity Service] [!DNL Co-op Graph] [의 구성원이거나, Adobe를 사용해야](https://docs.adobe.com/content/help/ko-KR/device-co-op/using/home.html)[!DNL Adobe Experience Platform Identity Service Private Graph]합니다.
* 그래프와 동기화되는 [!DNL Co-op Graph] Experience Cloud ID(ECID) [!DNL Private Graph] [](https://docs.adobe.com/content/help/ko-KR/id-service/using/home.html) 및 ID를 포함하거나 이에 필요한 모든 것을 구현해야 합니다. 기술 요구 사항 외에 기타 법적 및 계약 요구 [!DNL Co-op Graph] 사항도 있습니다.
* 현재 단일 IMS 조직을 두 개 사용할 수 없으므로 단일 IMS 조직 [!DNL Private Graph]으로 표준화해야 합니다. 경우에 따라 여러 IMS 조직이 있는 고객이 CDA와 함께 IMS를 사용할 수 [!DNL Co-op Graph] 있습니다.
* CDA의 [!DNL Co-op graph] 일부 구성 요소 및 [!DNL Private Graph]는 에서 호스팅됩니다 [!DNL Microsoft Azure]. 즉, Adobe의 데이터 처리 센터와 Adobe의 현재 상태 간에 데이터가 복사됩니다 [!DNL Analytics] [!DNL Microsoft Azure]. 일부 [!DNL Analytics] 데이터가 저장됩니다 [!DNL Azure]. 당신 회사는 이 합의에 동의해야 합니다.
* CDA에는 &quot;장치 간&quot; [!UICONTROL 보고서 세트가 필요합니다]. 즉, CDA에 사용하는 [!UICONTROL 보고서 세트는] 데스크톱 웹, 모바일 웹 및 모바일 앱과 같은 여러 다른 장치 유형이나 &quot;표면&quot;의 데이터를 포함해야 합니다. 2019년 9월 현재 이 [!UICONTROL 보고서 세트에] 대한 서버 호출 볼륨은 1일 이하여야 합니다. (서버 호출 볼륨 제한은 향후 몇 개월 동안 증가합니다.)
* 2019년 9월 현재 [!DNL Co-op Graph] 는 북아메리카에서만 이용 [!DNL Private Graph] 가능합니다. EMEA 및 APAC 지역의 그래프 존재에 대한 일정은 추후 발표될 예정입니다. 해당 지역에 있는 경우, 그래프를 사용할 수 있을 때 사용할 준비가 되도록 이러한 전제 조건을 확인할 것을 권장합니다.

## 장치 간 데이터 해석

### 방문자가 아닌 사람

CDA [!UICONTROL 가상 보고서 세트]내에서 몇 가지 변경 사항이 표시됩니다. 예를 들어 고유 방문자 수 [!UICONTROL 지표는] 두 개의 새 지표로 대체됩니다. [!UICONTROL 사용자] 및 [!UICONTROL 고유 장치]. 이러한 새로운 지표는 고객 규모에 대한 보다 나은 통찰력을 제공합니다.

*사용자 및 고유 장치*![CDA [!UICONTROL 사용자 지표]](assets/cda-people-metric.png)

세그먼트 [[!UICONTROL 빌더에서]](https://docs.adobe.com/content/help/ko-KR/analytics/components/segmentation/segmentation-workflow/seg-build.html)[!UICONTROL 방문자] 세그먼트 컨테이너는 [!UICONTROL 사람] 세그먼트컨테이너로대체되었습니다. CDA VRS를 사용하여 다음과 같은 장치 간 세그먼트를 만들 수 있습니다.

* 두 개 이상의 장치를 사용하는 사람
* 모바일 디바이스에서 시작한 이후 나중에 데스크탑 디바이스에서 구매한 사용자
* 사람들이 작업을 수행하기 위해 두 개 이상의 장치를 사용하는 방문

*개인 수준 세그먼트*![[!DNL Segment Builder] [!UICONTROL 개인] 컨테이너](assets/cda-segment-builder-person-container.png)

### Dimension 지속성

CDA VRS에서 크기(예: 크기)는 [!DNL eVars] 이제 장치 간에 자동으로 지속됩니다. 예를 들어 다음과 같이 [!DNL eVar] 구성된

* 할당:최근(마지막)
* 만료 날짜:구매

는 이제 구매 이벤트가 발생할 때까지 한 장치에서 다른 장치로 자동으로 지속됩니다.

## Analysis Workspace의 장치 간 데이터 분석

### 개인 기반 고객 분석

얼마나 많은 사람들이 귀사의 브랜드와 교류하고 있는지 궁금하신 적이 있습니까? 고객이 사용하는 디바이스의 수와 유형을 알고 싶으십니까? 사용량은 어떻게 겹치나요? CDA VRS를 사용하여 장치 간 벤 [다이어그램](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/analysis-workspace/visualizations/venn.html) 및 장치별 막대 그래프 [를 만들 수 있습니다](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/analysis-workspace/visualizations/histogram.html).

*사람 기반 고객 분석*&#x200B;벤안![및 히스토그램](assets/cda-venn-and-histogram.png)

### Cross-Device [!DNL Flow]

CDA와 Analysis Workspace을 사용하면 [[!DNL 흐름 시각화]에서 시간에 따라 사람들이 한 장치에서 다른 장치로 이동하는 방식을 시각화할 수 있습니다](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/analysis-workspace/visualizations/flow/flow.html). 여러분은 그들이 그들의 여행에서 어디에서 그리고 그들이 어디로 가는지 볼 수 있습니다.

*[!DNL Flow]CDA 사용*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### Cross-Device [!DNL Fallout]

몇 가지 [[!DNL 폴아웃 시각화]를 사용하여](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html) 성공을 달성하기 전에 사용자가 지정된 일련의 단계를 통해 얼마나 잘 수행하는지 분석할 수 있습니다. 기존 디바이스 기반의 분석 기능을 사용할 때 이러한 데이터 [!DNL Fallout visualizations] 에 대한 관점을 제한적으로 알고 계십니까? 성공적으로 &quot;폴스루&quot;하기 위해서는 다음 단계가 이전 단계와 동일한 브라우저 또는 앱에서 발생해야 합니다. 장치 기반 분석에서는 다른 장치에서 다음 단계를 성공적으로 완료한 사람을 잘 보지 못합니다.

걱정하지 마십시오. CDA가 회원님을 보호했습니다. CDA는 보다 유용하게 사용할 수 있는 크로스 디바이스 뷰를 [!DNL Fallout visualizations] 생성합니다. 결국, 진짜 중요한 것은, 그 사람이 어디에서 그들의 일에 궁극적으로 성공했는지 여부이다.

*[!DNL Fallout]CDA 사용*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

CDA가 Analysis Workspace 아래에 크로스 디바이스 데이터의 레이어를 만들기 때문에 모든 분석은 크로스 디바이스 원근감으로 다양하게 변형됩니다. 한 가지 강력한 예는 [[!DNL Attribution IQ]을 통해 가능합니다](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/panels/attribution/attribution.html). [!DNL Attribution IQ] analysis workspace에서 여러 속성 모델을 나란히 비교할 수 있습니다. CDA와 함께 이 기능을 사용하면 다양한 디바이스가 성공에 기여하는 정도를 비교할 수 있습니다.

예를 들어 모바일 전화기가 상호 작용에서 첫 번째 장치로 사용되는 빈도를 이해하면 결국 성공을 이룰 수 있다고 가정합니다. 이는 휴대전화의 &#39;고객 확보율&#39;을 의미한다. CDA + [!DNL Attribution IQ] 를 사용하여 다음과 같은 분석을 수행할 수 있습니다.

*[!DNL Attribution IQ]CDA 사용*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

For more information, see the [[!DNL Cross-Device Analytics] help documentation](https://docs.adobe.com/content/help/ko-KR/analytics/components/cda/cda-home.html).
