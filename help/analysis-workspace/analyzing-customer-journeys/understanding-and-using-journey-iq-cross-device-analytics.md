---
title: 여정 IQ 이해 및 사용 - 크로스 디바이스 분석
description: 사용자가 브랜드와 상호 작용할 때 다양한 방법으로 다양한 디바이스에서 이러한 행동을 취할 수 있습니다. 크로스 디바이스 분석은 Adobe Experience Platform Identity Service와 통합되어 장치가 사람에게 매핑되는 방식을 식별합니다. 그런 다음 이 인텔리전스를 활용하여 사용자 행동의 장치 간 보기를 만듭니다. 따라서 장치가 아니라 사람에 대한 분석을 수행할 수 있습니다.
feature: CDA
topics: null
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
role: Business Practitioner
level: Intermediate
translation-type: tm+mt
source-git-commit: f3b3fa7d91b0cb21005b57768ca23ed6700fcc03
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 6%

---


# [!DNL Journey IQ] 이해 및 사용 - 장치 간 분석

사용자가 브랜드와 상호 작용할 때 다양한 방법으로 다양한 디바이스에서 이러한 행동을 취할 수 있습니다. 크로스 디바이스 분석은 [!DNL Adobe Experience Platform Identity Service]과 통합되어 장치가 사람들에게 매핑되는 방식을 식별합니다. 그런 다음 이 인텔리전스를 활용하여 사용자 행동의 장치 간 보기를 만듭니다. 따라서 장치가 아니라 사람에 대한 분석을 수행할 수 있습니다.

## 장치 간 분석 개요

### 내 장치가 아닙니다.

사용자가 브랜드와 상호 작용하는 경우 다양한 방법으로 여러 &quot;표면&quot; 또는 &quot;장치&quot;에서 그렇게 합니다. PC 또는 모바일 장치에서 웹 브라우저를 사용하거나 모바일 앱을 사용할 수 있습니다. 쿠키를 기반으로 데이터 수집에서 성장한 기존의 디지털 분석에서는 이러한 각 표면은 고유한 &quot;방문자&quot;로 표현됩니다. 즉, 각 인간 사용자가 여러 고유 방문자로 표시됩니다.

예를 들어 이사벨이 귀사의 브랜드와 다음과 같은 방식으로 인터랙션했다고 가정합니다.

*이사벨은 세 명의*
![방문자이고 전통적인 분석 여정](assets/cda-isabelle-journey-traditional-analytics.png)

전통적인 분석으로 이사벨의 여정은 세 조각으로 분열되었다. 세 명의 고유 방문자로 표시되는데 각각 다른 장치를 사용하여 분리된 작업을 수행합니다. 이사벨의 상호작용을 통합적으로 다양한 장치를 통해 볼 필요가 있다. [!DNL Journey IQ: Cross-Device Analytics] 이 보기를 제공합니다.

*이사벨은*
![크로스 디바이스 분석 여정](assets/cda-isabelle-journey-cross-device-analytics.png)

### 장치 간 보기를 통해 더 나은 분석 제공

이사벨의 행동을 사람 중심의, 여러 장치를 통해 보는 관점이 분석에 중요한 차이를 만들 수 있습니다. 예를 들어, 기존 방문자 기반 접근 방식은 마케팅 채널 효과를 완벽하게 파악하지 못합니다. 이사벨의 여정을 다시 한번 보자. 어떤 채널이 그녀의 상품 관점과 구매에 대한 크레딧을 받는지에 집중한다. 단순함을 위해 [!UICONTROL last-touch] 속성을 사용하지만 이자벨러의 행동을 별개의 방문자로 나눌 때 동일한 기여도 모델을 사용하여 동일한 문제가 발생합니다. 일반적인 방문자 기반 보기를 사용하면 매우 다르며 오해의 소지가 있는 결과를 얻을 수 있습니다.

*기존 분석과 크로스 디바이스*
![분석채널 어트리뷰션 비교](assets/channel-attribution.png)

상호 장치 보기를 통해 이메일 채널은 제품 보기 및 구매에 대한 크레딧을 받게 됩니다. 이러한 크레딧은 이사벨의 실제 경험을 보다 정확하게 나타냅니다.

다음과 같은 정보를 읽어 보십시오.

* [!DNL Cross-Device Analytics] 작동 방식
* [!DNL Cross-Device Analytics]에 대한 사전 요구 사항
* 장치 간 데이터 해석
* Analysis Workspace에서 장치 간 데이터 분석

## [!DNL Cross-Device Analytics] 작동 방식

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 디바이스 [!DNL Adobe Experience Platform Identity Service]와 통합됩니다. 또는 [[!DNL Co-op Graph]](https://docs.adobe.com/content/help/ko-KR/device-co-op/using/home.html) 를 활용하여 디바이스 [!DNL Private Graph] 가 사람에게 매핑되는 방식을 식별할 수 있습니다. 그런 다음 이 인텔리전스를 활용하여 사용자 행동의 장치 간 보기를 만듭니다. CDA에는 기업이 귀사의 브랜드와의 인터랙션에 있어 다양한 디바이스의 사용 방식과 고객 경험을 파악하는 데 도움이 되는 탁월한 기능과 툴이 포함되어 있습니다. 이 레이어는 Analysis Workspace 아래 레이어로 사용되므로 [!UICONTROL 폴아웃], [!DNL Flow], [!DNL Cohort], [!DNL Segment IQ] 및 [!DNL Attribution IQ]와 같은 강력한 툴을 사용하여 개인 기반 고객 분석 및 장치 간 기여도 분석, 세분화 및 여정 분석에 대한 심층적인 통찰력을 제공합니다.

### 다음 [!DNL Cross-Device Virtual Report Suite]

CDA는 특별한 종류의 크로스 장치 [[!UICONTROL 가상 보고서 세트]](https://docs.adobe.com/content/help/ko-KR/analytics/components/virtual-report-suites/vrs-about.html)를 통해 제공됩니다. 상호 장치 분석을 조직에 소개할 때 원래 장치 기반 보고서 세트를 계속 사용할 수 있습니다. CDA VRS를 설정하는 방법은 간단합니다.

VRS 빌더 중 하나의 단계에서 Adobe에서 CDA가 활성화됨으로 구성된 [!UICONTROL 보고서 세트]를 선택합니다.

*CDA 지원 기본(소스)  [!UICONTROL 보고서 세트]*
![[!UICONTROL 선택가상 보고서 ] 세트 1단계](assets/cda-vrs-step-one.png)

그런 다음 [!UICONTROL 보고서 시간 처리]를 켜고 [!UICONTROL 장치 간 스티칭]을 활성화합니다.

*보고서  [!UICONTROL 시간 처리 ] 및  [!UICONTROL 장치 간 연결 활성화가상 보고서]*
![[!UICONTROL 세트 ] 2단계](assets/cda-vrs-step-two.png)

VRS 설정을 완료하고 저장합니다. CDA VRS는 아래에 표시된 대로 Analysis Workspace 옆에 특수 아이콘이 표시됩니다.

*분석 작업 공간에서 CDA VRS를*
![[!UICONTROL 선택합니다. 가상 보고서 ] 세트 3단계](assets/cda-vrs-step-three.png)

>[!TIP]
>
>CDA 사용 기반 [!UICONTROL 보고서 세트]의 맨 위에 원하는 만큼 CDA [!UICONTROL 가상 보고서 세트]를 만들 수 있습니다.

### 작업 내역 다시 설정

사용자가 로그인하고 [!DNL Co-op Graph] 또는 [!DNL Private Graph]이(가) 사용자를 식별하고 장치를 함께 매핑하는 데 시간이 걸릴 수 있습니다. CDA는 30일 룩백 윈도우를 활용하여 이전에 식별되지 않은 방문자를 이전 방문자까지의 최대 30일까지 재설정할 수 있습니다.

어떻게 도움이 됩니까? 위에서 논의했던 논의에서 이자벨의 사용자 여정을 다시 불러라:

![[!DNL Cross-Device Analytics] 여정](assets/cda-isabelle-journey-cross-device-analytics.png)

이사벨이 구입하기 직전에 로그인하지 않고 [!DNL Co-op Graph] 또는 [!DNL Private Graph]이 이사벨의 장치를 구입하기 전까지는 함께 매핑하지 않았을 가능성이 있습니다. 그러나 CDA의 30일간의 룩백을 통해 CDA는 이사벨의 과거 행동을 한 사람 수준에서 재조정할 수 있으며, 이것은 여러분이 필요한 그녀의 여정의 크로스 디바이스 보기를 여러분에게 제공합니다.

>[!NOTE]
>
>내역을 복원할 수 있으므로, 이것은 CDA가 활성화된 [!UICONTROL 가상 보고서 세트]에서 시간이 지남에 따라 데이터가 변경될 수 있음을 의미합니다. CDA 기반 분석에서 통찰력을 전달할 때 이를 염두에 두십시오.

## [!UICONTROL 장치 간 분석 사전 요구 사항]

CDA는 [[!DNL Analytics Ultimate]](https://helpx.adobe.com/legal/product-descriptions/adobe-analytics.html)에 포함됩니다. 2019년 9월부터 아래 나열된 사전 요구 사항을 충족하는 [!DNL Analytics Ultimate] 고객은 CDA를 사용할 수 있습니다. CDA의 사전 요구 사항은 다음과 같습니다.

* 회사는 [!DNL Adobe Experience Platform Identity Service] [[!DNL Co-op Graph]](https://docs.adobe.com/content/help/en/device-co-op/using/home.html)의 구성원이거나 [!DNL Adobe Experience Platform Identity Service Private Graph]을(를) 사용해야 합니다.
* 그래프와 동기화하는 ID(Experience Cloud ID)](https://docs.adobe.com/content/help/ko-KR/id-service/using/home.html) 및 ID(A0/> 또는 [!DNL Private Graph]에 필요한 모든 것을 구현해야 합니다. [!DNL Co-op Graph][ 기술 요구 사항 외에도 [!DNL Co-op Graph]은(는) 기타 법적 및 계약 요구 사항을 가지고 있습니다.
* 현재 단일 [!DNL Private Graph]으로 2개의 IMS 조직을 사용할 수 없으므로 단일 IMS 조직에 표준화해야 합니다. 경우에 따라 여러 IMS 조직이 있는 고객은 CDA와 함께 [!DNL Co-op Graph]을 사용할 수 있습니다.
* [!DNL Co-op graph] 및 [!DNL Private Graph] 및 CDA의 특정 구성 요소는 [!DNL Microsoft Azure]에서 호스팅됩니다. 즉, [!DNL Analytics] 데이터는 Adobe의 데이터 처리 센터와 [!DNL Microsoft Azure]의 Adobe의 존재 간에 복사됩니다. 일부 [!DNL Analytics] 데이터는 [!DNL Azure]에 저장됩니다. 귀사는 이 합의에 동의해야 한다.
* CDA에는 &quot;상호 장치&quot; [!UICONTROL 보고서 세트]가 필요합니다. 즉, CDA에 사용하는 [!UICONTROL 보고서 세트]에는 데스크톱 웹, 모바일 웹 및 모바일 앱과 같은 여러 다른 장치 유형 또는 &quot;표면&quot;의 데이터가 포함되어야 합니다. 2019년 9월 현재 이 [!UICONTROL 보고서 세트]에 대한 서버 호출 볼륨은 100MM 서버 호출/일 이하여야 합니다. (서버 호출 볼륨 제한은 향후 몇 개월 동안 증가합니다.)
* 2019년 9월부터 [!DNL Co-op Graph] 및 [!DNL Private Graph]은(는) 북아메리카에서만 사용할 수 있습니다. EMEA 및 APAC 지역의 그래프 존재에 대한 일정은 향후 발표됩니다. 해당 지역에 있는 경우 그래프를 사용할 수 있을 때 사용할 준비가 되도록 이러한 사전 요구 사항을 살펴보도록 권장합니다.

## 장치 간 데이터 해석

### 방문자가 아닌 사람

CDA [!UICONTROL 가상 보고서 세트] 내에 몇 가지 변경 사항이 있을 것입니다. 예를 들어 [!UICONTROL 고유 방문자] 지표는 두 개의 새 지표로 대체됩니다.[!UICONTROL 사용자] 및 [!UICONTROL 고유 장치]. 이러한 새로운 지표는 고객 규모에 대한 보다 나은 통찰력을 제공합니다.

*사람 및 고유*
![장치CDA  [!UICONTROL 사람 지표]](assets/cda-people-metric.png)

[[!UICONTROL 세그먼트 빌더]](https://docs.adobe.com/content/help/ko-KR/analytics/components/segmentation/segmentation-workflow/seg-build.html)에서 [!UICONTROL 방문자] 세그먼트 컨테이너가 [!UICONTROL Person] 세그먼트 컨테이너로 대체되었습니다. CDA VRS를 사용하여 다음과 같은 장치 간 세그먼트를 만들 수 있습니다.

* 장치를 두 개 이상 사용하는 사람
* 모바일 장치에서 여정을 시작한 다음 나중에 데스크톱 장치에서 구매하는 사람
* 사람들이 작업을 수행하기 위해 두 개 이상의 장치를 사용하는 방문

*개인 수준 세그먼트PersonContainer*
![[!DNL Segment Builder]  ](assets/cda-segment-builder-person-container.png)

### Dimension 지속성

이제 CDA VRS 내에서 [!DNL eVars]과 같은 차원이 장치 간에 자동으로 지속됩니다. 예를 들어 다음과 같이 구성된 [!DNL eVar]

* 할당:최근(마지막)
* 만료 날짜:구매

이제 구매 이벤트가 발생할 때까지 한 장치에서 다른 장치로 자동으로 지속됩니다.

## Analysis Workspace에서 장치 간 데이터 분석

### 개인 기반 고객 분석

귀사의 브랜드에 얼마나 많은 사람들이 교류하고 있는지 궁금해 본 적이 있습니까? 고객이 사용하는 디바이스의 수와 유형을 파악하고자 하십니까? 사용량은 어떻게 겹치나요? CDA VRS를 사용하여 크로스 디바이스 [벤 다이어그램](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/analysis-workspace/visualizations/venn.html) 및 장치별 [막대 그래프](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/analysis-workspace/visualizations/histogram.html)를 만들 수 있습니다.

*개인 기반 고객*
![분석벤 및 히스토그램](assets/cda-venn-and-histogram.png)

### 상호 장치 [!DNL Flow]

CDA 및 Analysis Workspace을 사용하면 [[!DNL Flow visualization]](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/analysis-workspace/visualizations/flow/flow.html)에서 시간에 따라 사람들이 한 장치에서 다른 장치로 이동하는 방식을 시각화할 수 있습니다. 여러분은 여정에서 어디에서 떨어지거나, 어디로 그들이 이동하는지 볼 수 있습니다.

*[!DNL Flow](CDA 포함)*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### 상호 장치 [!DNL Fallout]

일부 [[!DNL Fallout visualizations]](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html)을 사용하여 성공을 달성하기 전에 지정된 일련의 단계를 통해 사용자가 얼마나 잘 수행하는지 분석할 수 있습니다. 기존 디바이스 기반 분석을 사용할 때 이러한 [!DNL Fallout visualizations]에 대한 보기가 제한적이라는 것을 알고 계십니까? &quot;폴스루&quot;에 성공하려면 다음 단계가 이전 단계와 동일한 브라우저 또는 앱에서 진행되어야 합니다. 장치 기반 분석에서는 다른 장치에서 다음 단계를 성공적으로 완료한 사람을 잘 보지 못합니다.

걱정하지 마십시오. CDA는 당신이 책임져야 합니다. CDA는 [!DNL Fallout visualizations]이(가) 훨씬 유용하도록 하는 크로스 디바이스 보기를 만듭니다. 결국 진짜 중요한 것은 그 사람이 자신의 일을 어딘가에 최종적으로 성공했느냐 하는 것이다.

*[!DNL Fallout](CDA 포함)*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

CDA는 Analysis Workspace 아래에 크로스 디바이스 데이터 레이어를 만들기 때문에 모든 분석은 크로스 디바이스 원근감으로 향하게 됩니다. 강력한 예 중 하나가 [[!DNL Attribution IQ]](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/panels/attribution/attribution.html)입니다. [!DNL Attribution IQ] Analysis Workspace에서는 여러 속성 모델을 나란히 비교할 수 있습니다. 이제 CDA와 함께 이 기능을 사용하여 다양한 디바이스가 성공에 기여하는 정도를 비교할 수 있습니다.

예를 들어, 궁극적으로 성공을 유도하는 인터랙션에서 휴대 전화기가 가장 먼저 사용되는 장치의 빈도를 파악하고자 한다고 가정합니다. 이는 휴대전화의 &#39;고객 확보율&#39;을 의미한다. CDA + [!DNL Attribution IQ]에서 이 분석을 수행할 수 있습니다.

*[!DNL Attribution IQ](CDA 포함)*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

자세한 내용은 [[!DNL Cross-Device Analytics] 도움말 설명서](https://docs.adobe.com/content/help/ko-KR/analytics/components/cda/cda-home.html)를 참조하십시오.
