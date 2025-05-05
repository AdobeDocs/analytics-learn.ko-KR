---
title: 이제 세그먼트를 기다려 주세요. 세그먼테이션을 사용하여 Analysis Workspace에서 새로운 인사이트 발견
description: Adobe Analytics의 세그먼트를 사용하여 Analysis Workspace 시각화 및 자유 형식 테이블에서 새로운 통찰력을 발견하는 방법에 대해 알아봅니다.
feature: Segmentation
role: User
level: Beginner
doc-type: Article
last-substantial-update: 2023-05-16T00:00:00Z
jira: KT-13268
thumbnail: KT-13268.jpeg
exl-id: 7743debd-57d8-4c79-a332-187180fc9701
source-git-commit: d95136a21c08312a81baba7673cb7135270af4bd
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 1%

---

# 이제 세그먼트를 기다려 주세요. 세그먼트를 사용하여 Analysis Workspace에서 새로운 인사이트 발견

새로운 Adobe Analytics 사용자든 숙련된 프로든 간에 Analysis Workspace 프로젝트에서 세그먼트를 상당히 활용합니다. [Adobe Experience League](https://experienceleague.adobe.com/docs/analytics/components/segmentation/seg-overview.html?lang=ko)에서 설명한 대로 &quot;세그먼트를 사용하면 특성 또는 웹 사이트 상호 작용에 따라 방문자의 하위 집합을 식별할 수 있습니다.&quot; 이 기능의 기본 결과는 사용자, 방문 또는 사이트 히트 그룹을 격리하는 의미이지만, 본인과 같은 예리한 정신의 분석가는 이 도구를 사용하여 창의력을 발휘하고 사이트 활동에 대한 통찰력을 얻을 수 있는 새로운 방법을 찾을 수 있습니다. 가능한 옵션 목록은 광범위하므로 주저하지 말고 직접 만들어 조직 또는 Experience League의 [Adobe Analytics 커뮤니티](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics/ct-p/adobe-analytics-community?profile.language=ko) 또는 [#Measure Slack](https://www.measure.chat/) 커뮤니티와 같은 커뮤니티의 온라인에서 다른 사용자와 공유해 보십시오.

세그먼트를 만드는 방법에 대한 빠른 새로 고침이 필요한 경우 Analysis Workspace에서 [세그먼트 빌더](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html?lang=ko) 사용에 대한 Experience League 설명서를 확인하십시오.

## 세그먼트 비교 및 대비

Analysis Workspace에서는 &quot;[세그먼트 비교](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/panels/segment-comparison/segment-comparison.html?lang=ko)&quot;를 사용하여 두 세그먼트를 비교할 수 있습니다. 세그먼트 비교는 왼쪽 탐색 막대의 패널 섹션에서 찾을 수 있습니다.

![세그먼트 01](assets/seg01.png)

그러나 홈 키 통찰력을 최종 사용자에게 제공하기 위해 전체 비교 패널이 필요하지 않은 경우가 있습니다. 감사하게도 일부 기능은 표준 패널에서도 비교할 수 있습니다.

[벤 다이어그램 시각화](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/venn.html?lang=ko)를 사용하면 빠른 비교를 만들어 겹치는 세션, 주문, 사용자 등을 마우스로 가리키고 확인할 수 있습니다. 사용자 지정 세그먼트 2-3개 사이에 있어야 합니다. 겹치는 섹션 중 하나를 마우스 오른쪽 버튼으로 클릭하여 세그먼트를 빠르게 작성할 수도 있습니다.

![세그먼트 02](assets/s02.png)

중요한 정보가 겹치는 자료에 있지 않고 겹치지 않는 자료에 있는 경우도 있다. 이 항목을 빠르게 확인하는 방법은 한 세그먼트의 사본을 만들어 &quot;제외&quot; 세그먼트로 만드는 것입니다.

![세그먼트 03](assets/s03.png)

비교의 다른 세그먼트와 함께 &quot;제외&quot; 세그먼트를 스택하면 이제 동일한 세션에서 홈 페이지를 보지 않고 메뉴 페이지에 히트한 방문 수를 빠르게 계산할 수 있습니다.

![세그먼트 04](assets/s04.png)

## 스택 공격

마찬가지로 세그먼트를 함께 스택하여 벤 다이어그램의 교차 데이터를 만들 수 있습니다. 스택하는 세그먼트 수나 개별 차원에 대해서는 제한이 없습니다. 예를 들어, 지난 달에 내 사이트에서 어떤 요일이 휴대 전화, 특히 삼성 갤럭시 A52s로 방문했는지에 대해 빠르게 찾고 싶었지만, 내 메뉴 및 영양 페이지는 보았지만 홈 페이지는 보지 못했다면 다음과 같이 즉석으로 빠르게 만들 수 있습니다.

![세그먼트 05](assets/s05.png)

하지만 사용자 또는 방문 기반의 완벽한 하위 집합을 찾으면 이러한 모든 값을 선택하고 마우스 오른쪽 버튼으로 클릭한 다음 세그먼트를 즉시 만들 수 있습니다.

![세그먼트 06](assets/s06.png)

![세그먼트 07](assets/s07.png)

![세그먼트 08](assets/s08.png)

그것은 하나의 부분에서 많은 힘입니다.

## 여러 세그먼트에 대한 숫자 세그먼트

많은 사용자가 세그먼트를 작성할 때, 과거에 방문한 페이지, 사용자의 연령 범위 또는 사용자가 수행한 방문 수와 같은 명목, 서수 또는 간격 값을 종종 봅니다. 하지만 이러한 값이 표준 차원이든, 표준 지표이든, 조직의 사용자 지정 변수 및 지표이든 간에 이러한 값을 버킷하여 세그먼트를 생성할 때도 비율 데이터를 사용할 수 있습니다.

예를 들어 페이지에서 보낸 시간 또는 방문당 체류 시간에는 사전 빌드된 버킷을 사용할 수 있습니다.

![세그먼트 09](assets/s09.png)

그러나 이러한 방문이 항상 조직의 필요에 맞는 것은 아닐 수 있습니다. 대부분의 사이트 방문이 10분 이내에 실행될 수 있습니다. 세분화된 측정을 사용하여 크기가 다른 버킷을 만들 수 있습니다. 1분, 1초~1분, 30초 동안 지속되는 방문을 살펴보기 위해 만든 보고서는 다음과 같습니다.

![세그먼트 10](assets/s10.png)

이제 만들고 나면 사용자 지정한 다양한 버킷된 시간 그룹의 방문, 주문 및 기타 이벤트를 볼 수 있습니다.

![세그먼트 11](assets/s11.png)

사용자가 얼마나 많은 시간을 소비했는지, 방문에서 얼마나 많은 페이지를 방문했는지, 과거에 몇 번 방문했는지 또는 다른 숫자 값을 기준으로 KPI(주요 성과 지표)가 어떻게 변경되는지 검사할 수도 있습니다. 기본적으로 지표를 다른 지표의 요소로 볼 수 있습니다.

![세그먼트 12](assets/s12.png)

세그먼트를 사용하여 새로운 통찰력을 찾을 수 있는 가능성은 무한합니다! 이것은 단순히 시작점에 불과합니다. 직접 몇 가지 시도를 해보고 발견한 내용을 커뮤니티에 알려주십시오. Experience League 또는 [#MeasureSlack](https://www.measure.chat/) 커뮤니티에서 [Adobe Analytics 커뮤니티](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics/ct-p/adobe-analytics-community?profile.language=ko).

즐거운 세그먼트화!

## 작성자

이 문서의 작성자:

![Dan 커밍스](assets/seg13.png)

McDonald&#39;s Corporation의 제품 엔지니어링 분석 관리자인 **Dan Cummings**

Adobe Analytics 챔피언
