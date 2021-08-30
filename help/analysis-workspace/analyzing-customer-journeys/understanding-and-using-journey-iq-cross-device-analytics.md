---
title: 여정 IQ 이해 및 사용 - 교차 장치 분석
description: 사용자가 브랜드와 상호 작용할 때 여러 가지 방법 및 여러 장치에서 작동합니다. 교차 장치 분석 은 장치가 사람에게 매핑되는 방법을 확인하기 위해 Adobe Experience Platform Identity Service와 통합됩니다. 그런 다음 이 인텔리전스를 활용하여 사용자 동작에 대한 교차 장치 보기를 만듭니다. 결과적으로 장치가 아닌 사람에 대해 분석을 수행할 수 있습니다.
feature: CDA
topics: null
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
role: User
level: Intermediate
exl-id: 3748d5d7-d250-4057-8131-afdc66c80200
source-git-commit: fe861dfd541c1b9cb3b233fa3f56d55054305fd9
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 4%

---

# [!DNL Journey IQ] 이해 및 사용 - 교차 장치 분석

사용자가 브랜드와 상호 작용할 때 여러 가지 방법 및 여러 장치에서 작동합니다. 교차 장치 분석 은 장치가 사람에게 매핑되는 방법을 확인하기 위해 [!DNL Adobe Experience Platform Identity Service]과 통합됩니다. 그런 다음 이 인텔리전스를 활용하여 사용자 동작에 대한 교차 장치 보기를 만듭니다. 결과적으로 장치가 아닌 사람에 대해 분석을 수행할 수 있습니다.

## 교차 디바이스 분석 개요

### 내 장치가 아님

사용자가 브랜드와 상호 작용할 때 여러 가지 방법 및 여러 &quot;표면&quot; 또는 &quot;장치&quot;에서 그렇게 합니다. PC나 모바일 장치에서 웹 브라우저를 사용하거나 모바일 앱을 사용할 수 있습니다. 쿠키를 기반으로 데이터 수집에서 성장한 기존 디지털 분석에서는 이러한 각 면이 고유한 &quot;방문자&quot;로 표시됩니다. 즉, 각 인간 사용자는 여러 고유 방문자로 표시됩니다.

예를 들어보겠습니다. 이사벨이 귀사의 상표와 다음과 같은 방식으로 연동한다고 가정합니다.

*이사벨은 세*
![명의 방문객이다. 전통적인 분석 여정](assets/cda-isabelle-journey-traditional-analytics.png)

전통적인 분석법을 이용하여 이사벨의 여정은 세 조각으로 분리됩니다. 그녀는 각각 다른 장치를 사용하여 분리된 작업을 수행하는 세 명의 고유 방문자로 표시됩니다. 이사벨의 상호 작용에 대한 통합적이고 교차 장치적인 관점이 필요합니다. [!DNL Journey IQ: Cross-Device Analytics] 이 보기를 제공합니다.

*이사벨은 한*
![사람 교차 디바이스 분석 여정](assets/cda-isabelle-journey-cross-device-analytics.png)

### 교차 장치 보기가 더 나은 분석을 제공합니다.

이사벨의 행동을 사람 중심적이고 교차 장치 방식으로 보는 것은 당신의 분석에 상당한 차이를 만들 수 있다. 예를 들어 기존 방문자 기반 접근 방식은 마케팅 채널 효과를 전체적으로 파악할 수 없습니다. 이사벨의 여정을 다시 한번 살펴보자. 어느 채널이 그녀의 상품 견지와 구매에 대한 크레딧을 받는가 하는 것에 초점을 맞추었다. [!UICONTROL 마지막 터치] 속성은 단순성을 위해 사용하지만 이사벨의 행동을 별도의 방문자로 분할할 때 동일한 문제가 속성 모델을 사용하여 발생합니다. 세계의 기존 방문자 기반 보기를 사용하면 매우 다르며, 잘못된 결과도 볼 수 있습니다.

*기존 Analytics와 교차 장치*
![Analytics 채널 속성 비교](assets/channel-attribution.png)

전자 메일 채널은 교차 장치 뷰를 통해 제품 뷰와 구매 모두에 대한 크레딧을 받게 되며, 이는 이사벨의 실제 세계 경험을 더욱 정확하게 표현합니다.

계속 읽으면서 다음 사항에 대해 알아보십시오.

* [!DNL Cross-Device Analytics] 작동 방식
* [!DNL Cross-Device Analytics] 사전 요구 사항
* 교차 장치 데이터 해석
* Analysis Workspace에서 교차 장치 데이터 분석

## [!DNL Cross-Device Analytics] 작동 방식

[!DNL Journey IQ: Cross-Device Analytics (CDA)] 장치 [!DNL Adobe Experience Platform Identity Service]가 사람 [[!DNL Co-op Graph]](https://experienceleague.adobe.com/docs/device-co-op/using/home.html?lang=ko-KR) 에게 매핑되는 방법을 식별하기 위해 또는 를  [!DNL Private Graph] 사용하여 와 통합됩니다. 그런 다음 이 인텔리전스를 활용하여 사용자 동작에 대한 교차 장치 보기를 만듭니다. CDA에는 기업이 브랜드와의 상호 작용에서 다중 장치 사용과 해당 장치의 고객 경험을 이해하는 데 도움이 되는 탁월한 기능과 도구가 포함되어 있습니다. 이 디자이너는 Analysis Workspace 아래의 레이어로 사용하여 [!UICONTROL 폴아웃], [!DNL Flow], [!DNL Cohort], [!DNL Segment IQ] 및 [!DNL Attribution IQ]와 같은 강력한 도구를 사용하여 개인 기반 대상 분석 및 교차 장치 속성, 세그먼테이션 및 여정 분석에 대한 심층적인 통찰력을 제공합니다.

### 다음 [!DNL Cross-Device Virtual Report Suite]

CDA는 특별한 종류의 교차 장치 [[!UICONTROL 가상 보고서 세트]](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html)를 통해 제공됩니다. 이렇게 하면 조직에 교차 장치 분석을 도입하면서 원래 장치 기반 보고서 세트를 계속 사용할 수 있습니다. CDA VRS를 설정하는 것은 쉽습니다.

VRS 빌더의 1단계에서 Adobe이 CDA를 사용하도록 구성한 [!UICONTROL 보고서 세트]를 선택합니다.

*CDA를 사용할 수 있는 기본(소스)  [!UICONTROL 보고서 세트]*
![[!UICONTROL 가상 보고서 세트 ] 1단계 선택](assets/cda-vrs-step-one.png)

그런 다음 [!UICONTROL 보고서 처리 시간]을 설정하고 [!UICONTROL 교차 장치 결합]을 활성화합니다.

*보고서  [!UICONTROL 시간 처리 ] 및  [!UICONTROL 장치 간]*
![[!UICONTROL 결합 가상 보고서 세트 ] 2단계](assets/cda-vrs-step-two.png)

VRS 설정을 완료하고 저장합니다. CDA VRS는 아래에 표시된 대로 Analysis Workspace 옆에 특별한 아이콘이 표시됩니다.

*Analysis Workspace가상 보고서 세트에서 CDA*
![[!UICONTROL VRS ] 선택 3단계](assets/cda-vrs-step-three.png)

>[!TIP]
>
>CDA를 사용할 수 있는 기본 [!UICONTROL 보고서 세트]의 맨 위에서 원하는 만큼 CDA [!UICONTROL 가상 보고서 세트]를 만들 수 있습니다.

### 기록 재작성

사용자가 로그인하고 [!DNL Co-op Graph] 또는 [!DNL Private Graph] 가 사용자를 식별하고 해당 장치를 함께 매핑하는 데 시간이 걸릴 수 있습니다. CDA는 30일 전환 확인 기간을 사용하여 이전에 식별되지 않은 방문자를 과거 30일까지 다시 기술할 수 있습니다.

이 기능은 어떤 도움이 됩니까? 위의 논의에서 이사벨의 사용자 여정을 상기시켜라:

![[!DNL Cross-Device Analytics] 여정](assets/cda-isabelle-journey-cross-device-analytics.png)

이사벨이 이 제품을 구입하기 직전에 로그인하지 않고 [!DNL Co-op Graph] 또는 [!DNL Private Graph]이 그녀가 구입한 후 얼마 지나지 않아 이사벨의 장치들을 함께 매핑하지 않았을 가능성이 있습니다. 그러나 CDA의 30일 동안의 회상은 CDA가 이사벨의 과거 행동을 개인 수준에서 다시 기술할 수 있도록 해주며, 이것은 여러분이 필요로 하는 그녀의 여정에 대한 교차 장치 보기를 여러분에게 제공합니다.

>[!NOTE]
>
>기록을 다시 작성할 수 있으므로 이는 CDA가 활성화된 [!UICONTROL 가상 보고서 세트]에서 시간이 지남에 따라 데이터가 변경될 수 있음을 의미합니다. CDA 기반 분석에서 통찰력을 전달할 때 이를 염두에 두십시오.

## [!UICONTROL 교차 장치 분석 사전 요구 사항]

CDA는 [[!DNL Analytics Ultimate]](https://helpx.adobe.com/legal/product-descriptions/adobe-analytics.html)에 포함되어 있습니다. 2019년 9월부터 아래 나열된 사전 요구 사항을 충족하는 [!DNL Analytics Ultimate] 고객은 CDA를 사용할 수 있습니다. CDA를 위한 사전 요구 사항은 다음과 같습니다.

* 회사가 [!DNL Adobe Experience Platform Identity Service] [[!DNL Co-op Graph]](https://experienceleague.adobe.com/docs/device-co-op/using/home.html)의 구성원이거나 [!DNL Adobe Experience Platform Identity Service Private Graph]을 사용해야 합니다.
* 그래프와 함께 [Experience Cloud ID(ECID)](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=ko-KR) 및 ID 동기화를 포함하여 [!DNL Co-op Graph] 또는 [!DNL Private Graph]에 필요한 모든 것을 구현해야 합니다. [!DNL Co-op Graph] 에는 기술 요구 사항 외에 다른 법적 및 계약 요구 사항이 있습니다.
* 현재 단일 [!DNL Private Graph] 로 두 개의 IMS 조직을 사용할 수 없으므로 단일 IMS 조직을 표준화해야 합니다. 경우에 따라 여러 IMS 조직이 있는 고객이 CDA와 함께 [!DNL Co-op Graph]을 사용할 수 있습니다.
* CDA의 특정 구성 요소와 [!DNL Co-op graph] 및 [!DNL Private Graph] 는 [!DNL Microsoft Azure]에서 호스팅됩니다. 즉, [!DNL Analytics] 데이터는 Adobe의 데이터 처리 센터와 [!DNL Microsoft Azure]에 있는 Adobe 간에 서로 복사됩니다. 일부 [!DNL Analytics] 데이터는 [!DNL Azure]에 저장됩니다. 귀사는 이 계약에 동의해야 한다.
* CDA에는 &quot;교차 장치&quot; [!UICONTROL 보고서 세트]가 필요합니다. 즉, CDA에 사용하는 [!UICONTROL 보고서 세트]에는 데스크톱 웹, 모바일 웹 및 모바일 앱과 같은 여러 가지 다른 장치 유형 또는 &quot;표면&quot;의 데이터가 포함되어야 합니다. 2019년 9월부터 이 [!UICONTROL 보고서 세트]에 대한 서버 호출 볼륨은 100MM 서버 호출/일 이하여야 합니다. (서버 호출 볼륨 제한은 앞으로 몇 개월 동안 증가합니다.)
* 2019년 9월 현재 [!DNL Co-op Graph] 및 [!DNL Private Graph]은 북아메리카에서만 사용할 수 있습니다. EMEA 및 APAC 지역의 그래프 유무 일정은 나중에 발표됩니다. 해당 지역에 있는 경우 그래프를 사용할 수 있을 때 시작할 수 있도록 지금 이러한 전제 조건을 확인하는 것이 좋습니다.

## 교차 장치 데이터 해석

### 방문자가 아닌 사람

CDA [!UICONTROL 가상 보고서 세트] 내에서 몇 가지 변경 사항이 표시됩니다. 예를 들어 [!UICONTROL 고유 방문자 수] 지표는 두 개의 새 지표로 대체됩니다. [!UICONTROL People] 및 [!UICONTROL 고유한 장치]. 이러한 새로운 지표는 대상 크기에 대한 보다 나은 통찰력을 제공합니다.

*사람 및 고유*
![장치CDA  [!UICONTROL 사람 지표]](assets/cda-people-metric.png)

[[!UICONTROL 세그먼트 빌더]](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html?lang=ko-KR)에서 [!UICONTROL 방문자] 세그먼트 컨테이너가 [!UICONTROL Person] 세그먼트 컨테이너로 대체되었습니다. CDA VRS를 사용하여 다음과 같은 교차 장치 세그먼트를 만들 수 있습니다.

* 두 개 이상의 장치를 사용하는 사람
* 모바일 장치에서 여정을 시작한 다음 나중에 데스크탑 장치에서 구매하는 사람
* 사람들이 작업을 수행하기 위해 두 개 이상의 장치를 사용하는 방문

*개인 수준*
![[!DNL Segment Builder]  세그먼트PersonContainer](assets/cda-segment-builder-person-container.png)

### Dimension 지속성

CDA VRS 내에서 [!DNL eVars] 와 같은 차원은 이제 장치 간에 자동으로 유지됩니다. 예를 들어 다음과 같이 구성된 [!DNL eVar]

* 할당: 가장 최근 (마지막)
* 다음 시기 이후에 만료: 구매

이제 Purchase 이벤트가 실행될 때까지 한 장치에서 다른 장치로 자동으로 지속됩니다.

## Analysis Workspace에서 교차 장치 데이터 분석

### 개인 기반 대상 분석

얼마나 많은 사람들이 브랜드와 상호 작용하고 있는지 궁금해한 적이 있습니까? 얼마나 많은 장치와 어떤 유형의 장치를 사용하고 있는지 알고 싶습니까? 사용량은 어떻게 중첩됩니까? CDA VRS를 사용하여 교차 장치 [벤 다이어그램](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/venn.html?lang=ko-KR) 및 장치-per-person [히스토그램](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/histogram.html?lang=ko-KR)을 만들 수 있습니다.

*개인 기반 대상*
![분석 벤 및 히스토그램](assets/cda-venn-and-histogram.png)

### 교차 장치 [!DNL Flow]

CDA 및 Analysis Workspace을 사용하면 [[!DNL Flow visualization]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/flow/flow.html)에서 시간이 지남에 따라 사람들이 한 장치에서 다른 장치로 이동하는 방식을 시각화할 수 있습니다. 여러분은 여정에서 어디에서 어디에서 중단되고 어디에서 실행되는지 볼 수 있습니다.

*[!DNL Flow]CDA 사용*
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### 교차 장치 [!DNL Fallout]

몇 개의 [[!DNL Fallout visualizations]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html?lang=ko-KR)을 사용하여 사용자가 성공을 달성하기 전에 일련의 단계를 통해 얼마나 잘 수행하고 있는지를 분석할 수 있습니다. 기존 장치 기반 분석을 사용할 때 이러한 [!DNL Fallout visualizations]에 대한 보기가 제한된다는 사실을 알고 있습니까? &quot;폴스루&quot;를 성공적으로 수행하려면 다음 단계가 이전 단계와 동일한 브라우저 또는 앱에서 발생해야 합니다. 장치 기반 분석에서는 다른 장치에서 다음 단계를 성공적으로 완료한 사람을 볼 수 없습니다.

걱정 마세요, CDA는 당신이 담당했습니다. CDA는 [!DNL Fallout visualizations]을 훨씬 더 유용한 교차 장치 보기를 만듭니다. 결국 진짜 중요한 것은 어디에 가서 성공한 사람인가.

*[!DNL Fallout]CDA 사용*
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

CDA는 Analysis Workspace 아래에 교차 장치 데이터의 레이어를 만들기 때문에 모든 분석은 교차 장치 관점에서 변형됩니다. 한 가지 강력한 예는 [[!DNL Attribution IQ]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/panels/attribution/attribution.html?lang=ko-KR)을 통해 입니다. [!DNL Attribution IQ] Analysis Workspace에서 여러 속성 모델을 나란히 비교할 수 있습니다. 이제 CDA에서 이 기능을 사용하여 다양한 장치가 성공에 기여하는 방식을 비교할 수 있습니다.

예를 들어, 궁극적으로 성공으로 이어지는 상호 작용에서 휴대 전화기가 사용되는 첫 번째 장치의 빈도를 이해하려 한다고 가정합니다. 이것은 휴대폰의 &quot;획득율&quot;을 나타냅니다. CDA + [!DNL Attribution IQ]을(를) 사용하여 이 분석을 수행할 수 있습니다.

*[!DNL Attribution IQ]CDA 사용*
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

자세한 내용은 [[!DNL Cross-Device Analytics] 도움말 설명서](https://experienceleague.adobe.com/docs/analytics/components/cda/cda-home.html?lang=ko-KR)를 참조하십시오.
