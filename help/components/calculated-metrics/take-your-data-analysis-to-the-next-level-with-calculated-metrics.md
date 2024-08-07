---
title: 계산된 지표로 데이터 분석 수준을 한 차원 끌어올리기
description: 동료 전문가가 계산된 지표를 사용하여 구현을 변경하지 않고 복잡한 비즈니스 질문에 답변하기 위해 이미 수집된 데이터를 사용하여 새 지표를 만드는 방법을 알아봅니다.
feature: Calculated Metrics
role: User
level: Beginner
doc-type: Article
last-substantial-update: 2023-05-16T00:00:00Z
jira: KT-13266
thumbnail: KT-13266.jpeg
exl-id: 74793149-9967-4765-832c-c65e578ee34b
source-git-commit: d95136a21c08312a81baba7673cb7135270af4bd
workflow-type: tm+mt
source-wordcount: '1583'
ht-degree: 3%

---

# 계산된 지표로 데이터 분석 수준을 한 차원 끌어올리기

Adobe Analytics의 새 사용자 대부분은 데이터를 쪼개어 분석하기 위한 방법으로 세그먼트에 익숙합니다. 오늘은 분석가 도구 상자에서 다음으로 좋은 도구인 계산된 지표를 소개합니다.

Adobe Analytics의 고급 기능인 계산된 지표를 사용하면 이미 수집한 데이터를 사용하여 구현을 변경하지 않고 새 지표를 만들 수 있습니다. 계산된 지표 빌더는 다양한 수학 및 통계 함수를 사용할 수 있으므로 가장 복잡한 비즈니스 질문에 답변하는 지표를 만들 수 있습니다.

## 계산된 지표 시작

계산된 지표를 시작하기 위해 간단한 예를 살펴보겠습니다. 온라인 셀프서비스 사용자가 통화 지원 사용자보다 평균 주문 가격(AOV)이 더 높은지 알고 싶다고 상상해 보십시오. 이 질문에 답변할 계산된 지표를 작성하려면 다음을 수행하십시오.

계산된 지표 빌더를 열려면 위쪽 탐색을 사용하여 → **구성 요소** → **계산된 지표** → **+ 추가를 클릭하십시오.** 또는 [구성 요소] 패널에서 **지표** 위의 **+ 기호**&#x200B;를 클릭할 수 있습니다.


![계산 01](assets/calc01.png) ![계산 02](assets/calc03.png) ![계산 03](assets/calc02.png)

![계산 04](assets/calc04.png)

*UI 항목에 대한 아래 설명*

계산된 지표 빌더가 열리면 다음을 추가 및/또는 수행합니다.

**A.** 계산된 지표의 이름입니다. 이 이름은 지표 구성 요소 목록에 표시되므로 *콜센터 AOV*&#x200B;와 같이 본인과 다른 사용자에게 명확하게 표시되도록 하십시오.

**B.** 계산된 지표에 대한 설명입니다. 이 설명은 사용자가 구성 요소 목록의 지표 옆에 있는 &#39;**i**&#39;을(를) 클릭할 때 나타나므로 도움이 되는지 확인하십시오. 예를 들어, 콜 센터 AOV의 경우 *콜 센터 지원 주문에 대한 AOV 계산*&#x200B;을 추가할 수 있습니다.

**C.** 지표 형식: 소수, 시간, 백분율 또는 통화를 선택하고 소수 자릿수와 극성을 추가합니다. 여기서는 *통화는 형식, 0은 소수 자릿수,*&#x200B;은(는) *양호(녹색⬆을 선택합니다.*

**일**. 항목을 적용하고 계산된 지표를 빠르게 찾을 수 있는 태그를 사용하는 경우, 여기에 적용되는 태그를 추가하십시오. *AOV* 및 *콜 센터* 태그를 추가했습니다.

**E.** 이 섹션은 표시용입니다. 섹션 F에서 계산된 지표를 만들면 공식이 여기에 표시됩니다.

**F.** 여기에서 차원(H), 지표(I) 또는 세그먼트(J)를 끌어서 놓아 계산된 지표와 공식에 대한 연산자를 만듭니다. 각 지표에 대해 톱니바퀴 휠을 클릭하면 지표 유형(표준/합계) 및 기여도 분석 모델을 변경할 수 있습니다. *콜센터 매출을 끌어다 놓은 다음 그 아래로*÷￼*. 기본 지표 유형 및 속성 모델을 그대로 사용합니다.*

**G**. 이 **+추가** 옵션을 사용하여 여기에 필요하지 않은 조건 또는 정적 숫자를 추가하십시오.

**K.** 마지막으로 계산을 빌드할 때 여기에서 지난 90일 동안의 데이터를 미리 볼 수 있습니다.

이제 콜 센터 AOV를 구축했으므로 온라인 AOV에 대한 계산된 지표도 필요합니다. 위에 설명된 동일한 단계에 따라 이 작업을 수행합니다.

그런 다음 Calculated Metrics Builder를 사용하거나 자유 형식 테이블 내에서 즉석으로 콜센터와 온라인 AOV를 비교하여 세 번째 계산된 지표를 빌드할 수 있으므로 다음과 같은 결과가 나옵니다.

![계산 05](assets/calc05.png)

이 예에서는 구매자가 콜센터를 사용하여 구매를 수행하는 경우 상당한 상승세가 보입니다. 그런 다음 이 데이터는 팝업 오퍼 또는 기타 안내 경험을 통해 고객이 구매에 대한 지원을 받는 데 도움이 되는 방법에 대한 의사 결정을 알려 줄 수 있습니다.

## 계산된 지표에서 세그먼트 사용

이제 계산된 지표에 세그먼트를 사용하여 고객 행동, 선호도 및 동기에 대한 더 많은 통찰력을 얻는 방법에 대해 살펴보도록 하겠습니다. 세그먼트 및 계산된 지표를 통해 고객에 대해 충분히 학습하여 경험을 개선하고 매출을 증대하며 고객 만족도 및 충성도를 향상시킬 수 있습니다.

우리는 이미 위의 AOV 예제를 통해 콜 센터 지원 구매가 일반적으로 더 높은 AOV를 가진다는 것을 알고 있습니다. 그러나 다른 지표들은 대부분의 사용자가 구매 시 콜센터를 사용하지 않는다는 것을 알려줍니다.

그렇다면 어떤 소매 범주 및 해당 범주를 통한 사용자 경로가 가장 높은 AOV를 발생시킵니까?  세그먼트를 계산된 지표와 결합하여 확인할 수 있습니다.

이렇게 하려면 먼저 각 제품 범주에 대한 방문 수준 *포함* 및 *제외* 세그먼트를 만들어야 합니다. 포함 또는 제외는 컨테이너의 오른쪽 모서리에 있는 **옵션** 기어를 클릭하여 결정합니다. 기본값은 포함입니다.

![계산 06](assets/calc06.png) ![계산 07](assets/calc07.png)

이러한 세그먼트를 만들고 나면 계산된 지표를 만들어 질문에 대한 답변을 제공할 수 있습니다. 계산된 지표 빌더를 열고 다음 작업을 수행합니다.

1. 새로 만든 세그먼트를 검색하고 사용할 세그먼트를 **정의** 상자 상단의 회색 영역으로 끌어서 놓습니다. 예를 들어, 어린이가 아닌 여성 및 남성 범주를 모두 방문한 사용자를 위해 AOV를 만들려면 다음 세 가지 세그먼트를 해당 영역으로 끌어다 놓을 수 있습니다. *여성 포함*, *남성 포함* 및 *어린이 제외*. 이 *세그먼트 스택*&#x200B;을 호출합니다.

   ![계산 09](assets/calc09.png) ![계산 08](assets/calc08.png)

1. 그런 다음 **온라인 매출** 지표를 같은 컨테이너에 끌어다 놓은 다음 **온라인 주문**&#x200B;을 만듭니다. 컨테이너는 연산 순서를 결정하는 수학 표현식처럼 작동하므로, 이 계산에는 컨테이너나 프로세스가 여러 개 없지만 컨테이너의 항목은 후속 프로세스 전에 처리됩니다.
1. 두 지표 간의 연산자를 나눗셈(÷)으로 변경합니다.
1. **통화**&#x200B;를 형식으로 선택하고, 소수점 이하 자리수는 **0**&#x200B;이고, 극성은 **UP**&#x200B;입니다.
1. 계산된 지표의 이름을 지정하고 설명을 제공합니다.
1. 저장.

완료되면 계산된 지표는 다음과 같습니다.

![계산 10](assets/calc10.png)

방문자의 카테고리 여정 각 조합에 대해 누적된 세그먼트를 사용하여 계산된 지표를 만들고 데이터를 본 후 학습한 내용을 살펴봅니다! 방문 중에 여성 및 남성 범주를 모두 방문하는 사용자는 AOV가 가장 높으며, 단일 범주의 방문자와 비교할 때 상승도는 중요합니다.

![계산 11](assets/calc11.png) ![계산 12](assets/calc12.png)

이를 통해 페이지 레이아웃, 제품 배치 및 홍보 메시지를 최적화하여 체크아웃 전에 더 많은 사용자를 이러한 카테고리로 보낼 수 있습니다.

## 귀중하지만 어디에서나 사용할 수 없음

**따라서 단순 및 복합 계산된 지표는 분석가에게 매우 중요합니다!**

그러나 이러한 지표는 Adobe Analytics의 모든 영역에서 사용할 수 없습니다. 다음에서 계산된 지표를 사용할 수 없습니다.

- Analysis Workspace의 폴아웃
- Analysis Workspace의 집단 분석
- Data Warehouse
- 실시간 보고서
- 현재 데이터 보고서
- Target용 Analytics
- Report Builder

## 계산된 지표 우수 사례

이제 계산된 지표가 얼마나 중요한지 알았으므로 이를 작성하는 데 도움이 되는 몇 가지 모범 사례를 살펴보겠습니다.

1. **수식 구문을 확인하십시오.** 수식 구문이 모두 올바르고 Adobe Analytics 구문을 따르므로 의미 있는 정보를 얻을 수 있습니다.
1. **작업 순서를 확인합니다.** 컨테이너를 주의 깊게 사용하고 작업을 적절한 수학적 순서에 따라 넣으십시오.
1. **데이터를 두 번 계산하지 마십시오**. 계산된 지표에 사용된 공식이 동일한 데이터를 여러 번 계산하지 않도록 하여 데이터를 두 번 계산하지 않도록 할 수 있습니다. 이 작업은 계산된 지표에서 *Include* 및 *Exclude* 조건을 결합하거나 세그먼트를 사용하여 수행하는 경우가 많습니다.
1. **시간 세부기간을 확인하십시오.** 계산된 지표에 수식에 사용된 원본 지표와 동일한 시간 세부기간이 있는지 확인하십시오.
1. **정확한 데이터 사용:** 계산에 정확하고 신뢰할 수 있는 데이터를 사용하는 경우에만 귀중한 결과를 얻을 수 있습니다.

## 사용자 지정 세그먼트 모범 사례

Adobe Analytics에서 세그먼트를 만들 때 다음 모범 사례를 염두에 두십시오.

1. **단순하게 유지하십시오.** 세그먼트를 너무 복잡하게 만들지 마십시오. 가능한 단순하게 유지하고 정확성을 확보하는 데 필요한 조건만 사용하십시오.
1. **올바른 컨테이너 형식을 사용하십시오**. 잘못된 결과가 나오지 않도록 세그먼트 정의에 올바른 컨테이너 유형(방문자, 방문 또는 히트)을 사용해야 합니다.
1. **데이터를 두 번 계산하지 마십시오**. 계산된 지표의 경우와 마찬가지로, 세그먼트가 동일한 데이터를 여러 번 카운트하지 않는지 확인하십시오. 컨테이너 포함 및 제외가 도움이 될 수 있습니다.
   1. 포함 컨테이너를 사용하는 경우, 히트가 방문 내의 조건과 일치하는 경우 *포함* *방문의 모든 콘텐츠*&#x200B;입니다.
   1. 제외 컨테이너를 사용하면, 어떤 히트가 방문 내의 조건과 일치하는 경우 *방문의 모든 콘텐츠를 제외*&#x200B;합니다.
1. **컨테이너를 올바르게 중첩**&#x200B;합니다. 가장 바깥쪽 컨테이너를 사용하여 포함된 데이터를 결정한 다음 나머지 데이터에 중첩 규칙을 적용합니다. 중첩된 규칙이 적용되면 세그먼트 흐름은 단계 역할을 하며 후속 규칙은 첫 번째 규칙이 제외된 어떤 히트에도 적용되지 않습니다.
1. **데이터가 최신 상태인지 확인하세요.** 정확한 결과를 얻으려면 세그먼트 정의에 정확한 최신 데이터를 사용해야 합니다.
1. **세그먼트를 테스트합니다.** 세그먼트를 다른 사람에게 릴리스하기 전에 의도한 대로 작동하는지 항상 테스트하십시오.
1. **성능을 고려하십시오.** 세그먼트는 보고서 처리 속도가 느려질 수 있으므로 작성할 때 이러한 영향을 고려하십시오.

## 주요 학습 사항

Adobe Analytics에서 세그먼트와 계산된 지표를 결합하면 보다 강력하고 효과적인 데이터 분석을 수행할 수 있습니다. 데이터를 슬라이스 및 다이싱하고 비교를 위한 계산을 구축함으로써 마케팅 캠페인을 최적화하고 맞춤화된 대시보드 및 보고서를 만드는 데 사용할 수 있는 고객 행동에 대한 보다 심층적인 통찰력을 얻을 수 있습니다. 그러나 계산된 지표는 Adobe Analytics의 모든 영역에서 사용할 수 있는 것은 아니라는 점을 기억하고, 정확하고 유용한 데이터를 얻을 수 있도록 모범 사례를 따라야 합니다.


## 작성자

이 문서의 작성자:

![Debbie Kern](assets/calc13.jpeg)

Adswerve의 Adobe Analytics 관리자 **Debbie Kern**

![Adswerve](assets/calc14.png)
