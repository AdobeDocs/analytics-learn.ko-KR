---
title: Journey IQ 이해 및 사용 - 크로스 디바이스 분석
description: 사용자가 귀하의 브랜드와 상호 작용할 때, 그들은 여러 디바이스에서 다양한 방식으로 상호 작용합니다. 크로스 디바이스 분석은 디바이스가 사람에게 매핑되는 방법을 확인하기 위해 Adobe Experience Platform ID 서비스와 통합됩니다. 그런 다음 이러한 인텔리전스를 활용하여 사용자 비헤이비어의 크로스 디바이스 보기를 생성합니다. 이를 통해 디바이스가 아닌 사용자에 대한 분석을 수행할 수 있습니다.
feature: CDA
topics: null
activity: use
doc-type: article
team: Technical Marketing
kt: 4138
role: User
level: Intermediate
exl-id: 3748d5d7-d250-4057-8131-afdc66c80200
source-git-commit: 01e6e84f748e359aeb42c9be3afa52088f41018b
workflow-type: ht
source-wordcount: '1529'
ht-degree: 100%

---

# [!DNL Journey IQ] 이해 및 사용 - 크로스 디바이스 분석

사용자가 귀하의 브랜드와 상호 작용할 때, 그들은 여러 디바이스에서 다양한 방식으로 상호 작용합니다. 크로스 디바이스 분석은 디바이스가 사람에게 매핑되는 방법을 확인하기 위해 [!DNL Adobe Experience Platform Identity Service]와 통합됩니다. 그런 다음 이러한 인텔리전스를 활용하여 사용자 비헤이비어의 크로스 디바이스 보기를 생성합니다. 이를 통해 디바이스가 아닌 사용자에 대한 분석을 수행할 수 있습니다.

## 크로스 디바이스 분석 개요

### 나는 디바이스가 아닙니다

사용자가 귀하의 브랜드와 상호 작용할 때, 그들은 여러 “표면” 또는 “디바이스”에서 다양한 방식으로 상호 작용합니다. 사용자는 PC 또는 모바일 디바이스의 웹 브라우저를 사용하거나 모바일 앱을 사용합니다. 데이터 수집에서 쿠키를 기반으로 성장한 기존 디지털 분석에서, 이러한 각각의 표면은 고유 “방문자”로 표시됩니다. 이는 귀하의 사용자는 여러 명의 고유 방문자로 표시됨을 의미합니다.

아래의 예를 참조하십시오. “이사벨”이라는 사용자가 다음과 같은 방식으로 귀하의 브랜드와 상호 작용했다고 가정해 보겠습니다.

*“이사벨”은 3명의 방문자입니다*
![기존 분석 여정](assets/cda-isabelle-journey-traditional-analytics.png)

기존 분석을 사용할 때 “이사벨”의 여정은 세 부분으로 구분됩니다. “이사벨”은 3명의 고유 방문자로 표시되며, 구분된 각 부분은 서로 다른 디바이스를 사용하여 분리 작업을 수행합니다. 필요한 것은 “이사벨”의 상호 작용에 대한 하나의 통합된 크로스 디바이스 보기입니다. [!DNL Journey IQ: Cross-Device Analytics]에서 이 보기를 제공합니다.

*“이사벨”은 1명의 방문자입니다*
![크로스 디바이스 분석 여정](assets/cda-isabelle-journey-cross-device-analytics.png)

### 크로스 디바이스 분석을 통한 더 나은 분석

사용자 중심의 관점에서 볼 때, “이사벨”의 비헤이비어에 대한 크로스 디바이스 보기는 귀하의 분석에 상당한 차이점을 가져올 수 있습니다. 예를 들어 기존 방문자 기반 접근 방식은 마케팅 채널 효과에 대한 완전한 그림을 제공할 수 없습니다. 다시 한 번 “이사벨”의 여정으로 돌아가서, 그녀의 제품 보기 및 구매에 대한 크레딧을 받는 채널을 집중적으로 살펴보겠습니다. 간소화를 위해 [!UICONTROL 마지막 터치] 속성을 사용하지만, “이사벨”의 비헤이비어를 개별 방문자에게 할당할 때 어떠한 속성 모델을 사용해도 동일한 문제가 발생합니다. 기존 방문자 기반 보기를 사용하면 매우 다르고 오해의 소지가 있는 결과가 발생합니다.

*기존 분석과 크로스 디바이스 분석 비교*
![채널 속성](assets/channel-attribution.png)

크로스 디바이스 보기를 사용하면 이메일 채널은 프로젝트 보기 및 구매 모두에 대한 크레딧을 받으며, 이렇게 하면 “이사벨”의 현실 세계 경험을 보다 정확하게 나타낼 수 있습니다.

여기서 다음에 대해 알아보십시오.

* [!DNL Cross-Device Analytics] 작동 방식
* [!DNL Cross-Device Analytics] 사전 요구 사항
* 크로스 디바이스 데이터 해석
* Analysis Workspace에서 크로스 디바이스 데이터 분석

## [!DNL Cross-Device Analytics] 작동 방식

[!DNL Journey IQ: Cross-Device Analytics (CDA)]는 디바이스가 사람에게 매핑되는 방법을 확인하기 위해 [!DNL Device Graph]를 활용하여 [!DNL Adobe Experience Platform Identity Service]와 통합됩니다. 그런 다음 이러한 인텔리전스를 활용하여 사용자 비헤이비어의 크로스 디바이스 보기를 생성합니다. CDA에는 기업이 귀하의 브랜드와의 상호 작용에 있어 이러한 디바이스를 통한 여러 디바이스 사용 및 고객 경험을 이해하는 데 도움이 되는 뛰어난 기능 및 도구가 포함되어 있습니다. CDA는 Analysis Workspace 아래에 레이어로 존재하며 [!UICONTROL 폴아웃], [!DNL Flow], [!DNL Cohort], [!DNL Segment IQ] 및 [!DNL Attribution IQ]와 같은 강력한 도구를 사용하여 사용자 기반 대상 분석 및 크로스 디바이스 속성, 세분화 및 여정 분석에 대한 심도 있는 통찰력을 제공합니다.

### [!DNL Cross-Device Virtual Report Suite]

CDA는 특별한 종류의 크로스 디바이스 [[!UICONTROL 가상 보고서 세트]](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html)를 통해 제공됩니다. 이를 통해 조직에 크로스 디바이스 분석을 도입할 때에도 원래의 디바이스 기반 보고서 세트를 계속 사용할 수 있습니다. CDA VRS 설정 방법은 간단합니다.

VRS 빌더의 첫 번째 단계에서, Adobe에서 CDA가 활성화되도록 구성한 [!UICONTROL 보고서 세트]를 선택합니다.

*CDA 활성화 기반(소스) [!UICONTROL 보고서 세트]* 선택
![[!UICONTROL 가상 보고서 세트] 1단계](assets/cda-vrs-step-one.png)

그런 다음 [!UICONTROL 보고서 처리 시간]을 켜고 [!UICONTROL 크로스 디바이스 결합]을 활성화합니다.

*[!UICONTROL 보고서 처리 시간] 및 [!UICONTROL 크로스 디바이스 결합]* 활성화
![[!UICONTROL 가상 보고서 세트] 2단계](assets/cda-vrs-step-two.png)

VRS 설정을 완료한 다음 저장합니다. CDA VRS가 Analysis Workspace에서 아래와 같이 VRS 설정 옆에 특수 아이콘으로 표시됩니다.

*Analysis Workspace에서 CDA VRS 선택*
![[!UICONTROL 가상 보고서 세트] 3단계](assets/cda-vrs-step-three.png)

>[!TIP]
>
>CDA 활성화 기반 [!UICONTROL 보고서 세트] 상단에 원하는 만큼 여러 CDA [!UICONTROL 가상 보고서 세트]를 생성할 수 있습니다.

### 고침 내역

경우에 따라 사용자가 로그인하고 [!DNL Device Graph]가 이들 사용자를 식별하고 디바이스를 매핑하는 데 어느 정도 시간이 소요됩니다. CDA는 30일 룩백 창을 활용하여 이전에 최대 30일 전까지 식별되지 않은 방문자를 개인으로 고쳐 표시할 수 있도록 합니다.

이것이 어떤 도움을 줄 수 있는지 알아보겠습니다. 위에서 논의했던 “이사벨”의 사용자 여정을 다시 떠올려 보십시오.

![[!DNL Cross-Device Analytics] 여정](assets/cda-isabelle-journey-cross-device-analytics.png)

“이사벨”은 구매하기 직전까지 로그인하지 않았을 수 있으며, [!DNL Device Graph]는 구매 후 얼마가 지나서야 “이사벨”의 디바이스를 매핑했을 가능성도 있습니다. 그러나 CDA의 30일 룩백을 사용하면 CDA가 “이사벨”의 이전 비헤이비어를 개인 수준으로 고쳐 표시할 수 있으며, 이를 통해 필요한 여정의 크로스 디바이스 분석을 제공할 수 있습니다.

>[!NOTE]
>
>내역을 고쳐 표시할 수 있으므로 이는 CDA가 활성화된 [!UICONTROL 가상 보고서 세트]에서 귀하의 데이터가 변경될 수 있음을 의미합니다. CDA 기반 분석에서 통찰력을 제공할 때 이 점을 염두에 두십시오.

## [!UICONTROL 크로스 디바이스 분석] 사전 요구 사항

CDA는 [[!DNL Analytics Ultimate]](https://helpx.adobe.com/kr/legal/product-descriptions/adobe-analytics.html)에 포함되어 있습니다. 2019년 9월부터 아래에 나열된 사전 요구 사항을 충족하는 [!DNL Analytics Ultimate] 고객은 CDA를 사용할 수 있습니다. CDA에 대한 사전 요구 사항은 다음과 같습니다.

* 귀사에서 [!DNL Adobe Experience Platform Identity Service Device Graph]를 사용해야 합니다.
* [Experience Cloud ID(ECID)](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=ko) 및 해당 그래프와 동기화되는 ID를 포함하여 [!DNL Device Graph]에 필요한 모든 사항을 구현해야 합니다.
* 현재 단일 [!DNL Device Graph]로 두 개의 IMS 조직을 사용할 수 없으므로 단일 IMS 조직을 표준화해야 합니다.
* CDA의 특정 구성 요소와 더불어 [!DNL Device Graph]는 [!DNL Microsoft Azure]에서 호스팅됩니다. 이는 [!DNL Analytics] 데이터가 Adobe의 데이터 처리 센터와 [!DNL Microsoft Azure]에서의 Adobe 상태 간에 서로 복사됨을 의미합니다. 일부 [!DNL Analytics] 데이터는 [!DNL Azure]에 저장됩니다. 귀사는 이러한 방식에 동의해야 합니다.
* CDA는 “크로스 디바이스” [!UICONTROL 보고서 세트]가 필요합니다. 즉, CDA에 사용하는 [!UICONTROL 보고서 세트]에는 데스크탑 웹, 모바일 웹 및 모바일 앱과 같은 다양한 디바이스 유형 또는 “표면”의 데이터가 포함되어야 합니다. 2019년 9월부터 이 [!UICONTROL 보고서 세트]에 대한 서버 호출 볼륨은 100MM 서버 호출/일 이하여야 합니다. 서버 호출 볼륨 제한은 향후 몇 개월에 걸쳐 증가합니다.

## 크로스 디바이스 데이터 해석

### “방문자”가 아닌 “사람”

CDA [!UICONTROL 가상 보고서 세트]에서 몇 가지 사항이 변경되었습니다. 예를 들어 [!UICONTROL 고유 방문자] 지표는 두 개의 새로운 지표인 [!UICONTROL 사람] 및 [!UICONTROL 고유 디바이스]로 대체됩니다. 이들 새 지표를 통해 대상 크기에 대한 더 나은 통찰력을 가질 수 있습니다.

*사람 및 고유 디바이스*
![CDA [!UICONTROL 사람 지표]](assets/cda-people-metric.png)

[[!UICONTROL 세그먼트 빌더]](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html)에서 [!UICONTROL 방문자] 세그먼트 컨테이너는 [!UICONTROL 사람] 세그먼트 컨테이너로 대체됩니다. CDA VRS를 사용하여 다음과 같은 크로스 디바이스 세그먼트를 생성할 수 있습니다.

* 한 개 이상의 디바이스를 사용하는 사람
* 모바일 디바이스에서 여정을 시작하여 나중에 데스크탑 디바이스에서 구매를 수행하는 사람
* 사람들이 한 개 이상의 디바이스를 사용하여 작업을 완료하는 방문

*개인 수준 세그먼트*
![[!DNL Segment Builder] [!UICONTROL 사람] 컨테이너](assets/cda-segment-builder-person-container.png)

### 차원 지속성

이제 CDA VRS에서 [!DNL eVars]와 같은 차원은 자동으로 모든 디바이스에서 지속됩니다. 예를 들어 [!DNL eVar]가

* 할당: 가장 최근
* 만료 시기: 구매 이후

로 구성되는 경우 이는 구매 이벤트가 실행될 때까지 자동으로 하나의 디바이스부터 다른 디바이스로 지속됩니다.

## Analysis Workspace에서 크로스 디바이스 데이터 분석

### 사용자 기반 대상 분석

얼마나 많은 사람들이 내 브랜드와 상호작용하고 있는지 생각해 본 적이 있습니까? 그들이 얼마나 많은 디바이스와 어떤 유형의 디바이스를 사용하고 있는지 파악하고 싶습니까? 그들의 사용은 어떻게 중첩됩니까? CDA VRS를 사용하면 크로스 디바이스 [벤 다이어그램](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/venn.html) 및 사람당 디바이스 개수에 대한 [히스토그램](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/histogram.html)을 생성할 수 있습니다.

*사용자 기반 대상 분석*
![벤 및 히스토그램](assets/cda-venn-and-histogram.png)

### 크로스 디바이스 [!DNL Flow]

CDA와 Analysis Workspace를 통해 [[!DNL Flow visualization]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/flow/flow.html)에 사람들이 시간이 지남에 따라 하나의 디바이스에서 다른 디바이스로 어떻게 이동하는지를 시각화할 수 있습니다. 사람들이 어느 지점에서 여정을 중단하고 어느 지점에서 여정을 계속 수행하는지 확인해 보십시오.

CDA *와*[!DNL Flow]
![[!DNL Flow Visualization]](assets/cda-flow-viz.png)

### 크로스 디바이스 [!DNL Fallout]

몇 가지 [[!DNL Fallout visualizations]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/fallout/fallout-flow.html)을 사용하여 사용자가 성공적으로 작업을 완료하기 전에 주어진 일련의 단계를 얼마나 잘 수행하는지 분석할 수 있습니다. 기존 디바이스 기반 분석을 사용할 때에는 이러한 [!DNL Fallout visualizations]에 대한 보기가 제한되어 있다는 점을 알고 계십니까? “폴스루”를 성공적으로 수행하려면 이전 단계와 동일한 브라우저 또는 앱에서 다음 단계를 수행해야 합니다. 디바이스 기반 분석에서는 다른 디바이스에서 다음 단계를 성공적으로 완료하는 사용자를 볼 수 없습니다.

걱정하지 마십시오. CDA를 사용하면 가능합니다. CDA는 훨씬 유용한 [!DNL Fallout visualizations]을 제공하는 크로스 디바이스 보기를 생성합니다. 결과적으로 정말 중요한 것은 사용자가 궁극적으로 어딘가에서 자신의 작업을 완료했는지 여부입니다.

CDA *와*[!DNL Fallout]
![[!DNL Fallout Visualization]](assets/cda-fallout-viz.png)

### [!DNL Cross-Device Attribution IQ]

CDA가 Analysis Workspace 아래에 크로스 디바이스 데이터 레이어를 생성하므로 모든 분석을 크로스 디바이스 관점에서 수행할 수 있습니다. 한 가지 강력한 예는 [[!DNL Attribution IQ]](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/panels/attribution/attribution.html)입니다. Analysis Workspace의 [!DNL Attribution IQ]를 사용하면 여러 속성 모델을 나란히 비교할 수 있습니다. CDA와 함께 이 기능을 사용하면 다양한 디바이스가 어떻게 성공에 기여하는지 비교할 수 있습니다.

예를 들어 휴대폰이 궁극적으로 성공적인 성과를 얻을 수 있는 상호 작용에 첫 번째 디바이스로 사용되는 빈도를 알고자 한다고 가정해 보겠습니다. 이는 휴대폰의 “확보율”을 나타냅니다. CDA와 함께 [!DNL Attribution IQ]를 사용하면 이러한 분석을 수행할 수 있습니다.

CDA *와*[!DNL Attribution IQ]
![[!DNL Attribution IQ]](assets/cda-attribution-iq.png)

자세한 내용은 [[!DNL Cross-Device Analytics] 도움말 문서](https://experienceleague.adobe.com/docs/analytics/components/cda/cda-home.html)를 참조하십시오.
