---
title: Google Analytics에서 Adobe Analytics로 전환에 대한 포괄적인 안내서
description: 도구 간에 전환할 때 겪는 가장 큰 어려움 중 하나는 동일한 기능을 찾는 것과 이를 효율적으로 사용하는 방법을 학습하는 것입니다. 다음은 사용자가 Adobe Analytics로 간편하게 전환하는 데 도움이 되는 대규모 안내서의 일부입니다.
feature: Third-party Integration
role: User
level: Beginner
doc-type: feature video
thumbnail: 34749.jpg
kt: 9830
exl-id: b2be6081-a1c0-4435-affb-454ed5a74662
source-git-commit: de78868e07b0fa59a7babc092c463bbe4d8e2da7
workflow-type: ht
source-wordcount: '3690'
ht-degree: 100%

---

# Google Analytics에서 Adobe Analytics로 전환에 대한 포괄적인 안내서

## 1. 소개

도구 간에 전환할 때 겪는 가장 큰 어려움 중 하나는 동일한 기능을 찾는 것과 이를 효율적으로 사용하는 방법을 학습하는 것입니다. 다음은 사용자(신규 사용자 또는 Google Analytics 사용자)가 Adobe Analytics로 간편하게 전환할 수 있도록 지원하는 대규모 안내서의 일부입니다. 많은 사용자에게 친숙한 비교 도구인 GA와 상세하게 비교합니다. 이를 통해 사용자는 기존 지식을 새로운 도구 세트와 연관시킬 수 있습니다. 가장 좋은 방법은 실제로 사용해 보는 것이지만, 비교 도구를 활용하면 시작하는 데 도움이 되며 적응 기간 동안 겪을 수 있는 어려움을 줄일 수 있습니다.

간단한 용어 비교도 필요합니다.

| **설명** | **Adobe Analytics** | **Google Analytics** |
|--------------------------------------------------------------------------------------------------------------------------------|---------------------|----------------------|
| 페이지(또는 앱의 화면)를 나타내는 이벤트 지표가 조회되었습니다. | 페이지 보기 | 페이지 보기 |
| 동일한 시간대에서 열리는 웹 사이트 또는 앱의 인터랙션 그룹을 나타내는 지표 | 방문 | 세션 |
| 식별된 디바이스를 정의하는 지표 (쿠키 및 사용자 정보를 결합하는 기타 비헤이비어 패턴을 포함한 여러 기준에 기반) | 고유 방문자 수 | 사용자 |

## 2. 인터페이스

사용자들이 Adobe Analytics와 Google Analytics를 비교할 때 작업이 많이 되어있다는 것 때문에 전환을 주저하기도 합니다. 이는 사실이지만, 약점이 아니라 강점이기도 합니다. Adobe는 데이터 시각화에 다양한 도구와 유연성을 제공하므로 필요한 것을 더욱 자유롭게 구축할 수 있습니다.

먼저 “사이트 내” 보고를 살펴보겠습니다.

### 2.1. 사이트 내 보고

#### 2.1.1. 홈 화면

Adobe Analytics와 Google Analytics는 모두 사용자가 로그인할 때 표시되는 첫 번째 보기를 맞춤화하는 기능을 제공합니다.

##### 2.1.1.1. 작업 영역/맞춤형 설정 홈 화면 (Adobe Analytics)

Adobe Analytics는 모든 사용자가 로그인할 때 볼 수 있도록 미리 작성된 보고서를 만들지는 않습니다. 기본 홈 페이지는 각 사용자가 생성했거나 공유한 모든 작업 영역 보고서를 표시하는 작업 영역 랜딩 화면으로 사용자를 안내합니다. 또한 각 사용자는 원하는 경우 이러한 보고서를 홈 화면으로 설정할 수 있습니다.

![image1](assets/ga-to-aa_1.png)

작업 영역에 대한 자세한 내용은 이 안내서의 뒷부분에 설명되어 있습니다. 섹션 2.1.2.1 참조

>[!TIP]
>
>조직에 대한 몇 가지 표준 보고서를 생성/공유하여 즉시 자체 보고서를 작성하지 않고도 정보를 볼 수 있는 시작 지점을 만들 수 있습니다.



##### 2.1.1.2. 홈 화면 인사이트 (Google Analytics)

* Google Analytics 홈 화면에는 사전 설치된 시각화 기능이 있습니다. 이는 다음과 같은 내용을 다룹니다.
* 지난 7일 동안의 사용자, 세션, 바운스 비율 및 세션 시간
* 지난 30일 동안의 시간별 사용자
* 현재 사용자 및 상위 활성 페이지
* 지난 7일 동안의 트래픽 채널, 소스/Medium 및 참조
* 지난 7일 동안의 국가별 세션
* 지난 7일 동안의 상위 페이지
* 지난 30일 동안의 활성 사용자 추세
* 등

GA4에는 홈 화면에 사용자의 보고서를 맞춤화하고 추가할 수 있는 더 많은 옵션이 있습니다.

![image2](assets/ga-to-aa_2.png)

이는 Adobe에서 가장 찾게 될만한 기능입니다. 사전 설치된 홈 화면은 없지만 위에서 필요한 것을 복제하도록 맞춤형 작업 영역을 간편하게 설정하고, 원하는 경우 이를 랜딩 화면으로 설정할 수 있습니다. 자세한 내용은 뒤에서 참조하십시오(또는 섹션 2.1.2.1 Adobe Workspace 참조).

#### 2.1.2. 사이트 내 Report Builders

분석 도구에서 제공하는 간단한 보고서 외에도 각 도구는 맞춤형 보고서를 작성하는 데 사용할 수 있는 보다 강력한 도구도 제공합니다.

##### 2.1.2.1. Adobe Analytics Workspace

이는 2017년에 도입된 이래 Adobe Analytics의 분석을 위한 강력한 기능이며 보고서 섹션이 곧 종료되는 주된 이유입니다.

이 도구를 사용하여 자유롭게 보고서를 작성할 수 있습니다.

보고서는 패널로 나눌 수 있으며 해당 패널에는 다양한 시각화가 포함될 수 있습니다. 패널은 날짜 범위 및 공통 세그먼트 필터와 같은 일반 정보로 설정할 수 있습니다.

패널과 패널 내의 시각화 모두 크기를 조정하고 드래그하여 항목을 나란히 표시하거나 겹칠 수 있습니다. 따라서 두 개의 서로 다른 데이터 제품군을 나란히 비교하려는 경우 쉽게 비교할 수 있도록 나란히 표시된 두 사이트의 중간을 50/50으로 분할하는 패널을 만들 수 있습니다.

사용자가 사용할 수 있는 다양한 시각화가 있습니다.

* 자유 형식 테이블
* 집단 테이블
* 폴아웃
* 흐름
* 그래프
   * 영역 (스택 및 언스택)
   * 선
   * 분산
   * 바 (스택 및 언스택)
   * 글머리 기호
   * 도넛
   * 히스토그램
   * 가로 막대 (스택 및 언스택)
* 맵
* 요약 블록
   * 요약 변경
   * 요약 텍스트
   * 텍스트 (컨텍스트를 제공하기 위해 추가 정보를 입력하는 자유 텍스트 필드)
* 벤

각 패널 및 시각화에는 정보가 표시되는 내용에 대한 컨텍스트를 제공하는 데 도움이 되도록 제목을 지정하고 설명을 적용할 수 있습니다.
Adobe에서 세그먼트(기본적으로 데이터 필터)는 소급 적용되며, 이를 자유 형식 테이블의 열로 가져와 데이터를 나란히 비교할 수 있습니다. 예를 들어 사용자가 트래픽에 대해 사이트에서 두 개의 다른 범주를 비교하려는 경우 “범주 A”와 “범주 B”에 대해 다른 세그먼트를 만들 수 있습니다.

![image3](assets/ga-to-aa_3.png)

자유 형식 테이블을 사용하면 원하는 방식으로 데이터를 시각화하는 데 필요한 만큼의 여러 열과 세그먼테이션을 사용할 수 있습니다.

위에서 날짜별 분류를 보시겠습니까? 다른 치수 또는 세그먼트를 드래그 앤 드롭하여 다른 방식으로 데이터를 보십시오. 예를 들어 디바이스 유형에 대한 세그먼트를 사용한 다음 모바일/태블릿 사용자에 대한 OS별 분석을 추가할 수 있습니다.

![image3](assets/ga-to-aa_4.png)

작업 영역을 사용하면 창의력을 발휘할 수 있으며 “표준” 분류에 국한되지 않습니다. 실행해야 하는 비교를 자세히 분석하는 데 필요한 시각화를 구축할 수 있습니다.

>[!TIP]
>
>자유롭게 작업하고 탐색해 보십시오. 틀을 벗어나 생각할 수 있는 많은 방법이 제공됩니다. 무엇을 수행할 수 있는지 확인하십시오. 또한 여러분이 구축한 것이 스스로 생각하는 것을 실제로 보여 주고 있는지 확인하십시오. 다음 경험이 유용할 것입니다!

보고서 내부에만 있는 즉석으로 계산된 지표 또는 세그먼트를 생성할 수도 있습니다. (세그먼트 및 계산 저장소 초과를 방지할 뿐만 아니라 조직을 다른 컨텍스트에서 유용하지 않은 것과 혼동하지 않고 특정 보고서에 필요한 집중 항목을 생성할 수 있도록 합니다.)

다음은 이 도구에 대한 소개일 뿐이며, 시작에 도움이 되는 다른 포괄적인 안내서가 있을 것입니다. 하지만 이 안내서를 사용하면 다음과 같은 포괄적인 보고서를 작성할 수 있습니다.

![image3](assets/ga-to-aa_5.png)

또한 작업 영역은 자동 저장되지 않으므로 보고서 저장소를 막지 않고 일회성 애드혹을 수행하는 것이 보다 간편합니다.

작업 영역의 또 다른 강력한 기능은 대화형 수정자를 드롭다운 형태로 보고서에 적용하는 것입니다. 이 드롭다운은 보고서의 내보낸 CSV 또는 PDF 파일에서 작동하지 않지만 라이브 보고서 내에서는 패널의 모든 시각화를 업데이트하여 다른 조건에서 동일한 보고서를 표시할 수 있습니다. 여러 드롭다운을 사용할 수 있으며 옵션이 상호 배타적이지 않은 한 선택한 항목이 스택되어 정보를 깔끔하게 표시할 수 있습니다.

>[!IMPORTANT]
>
>드롭다운 및 자유 형식 분석 사용에 대한 자세한 내용은 <https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/the-power-of-dropdown-filters-and-dimension-breakdowns-in-adobe/td-p/434680>을 참조하십시오.

##### 2.1.2.2. Google Analytics: 대시보드, 맞춤형 보고서 및 저장된 보고서

Google에는 인터페이스 내에서 보고서를 작성하기 위한 몇 가지 도구가 있지만 여전히 보고서 섹션의 동일한 표시 및 제한을 따릅니다.

이제 이 글을 읽으면서 Google Analytics를 숙달한 사람들은 “Google Data Studio가 Adobe Workspace와 더 비슷하지 않습니까?”라는 질문을 할 수 있습니다. 맞습니다. 그러나 Data Studio는 기술적으로 Analytics 도구의 일부가 아니며 서로 다른 데이터 소스에 연결할 수 있으므로 해당 도구는 이 문서의 뒷부분 “확장된 보고서 액세스” 섹션(특히 섹션 2.2.3)에서 다루게 됩니다.

Google 대시보드 및 맞춤형 보고서를 사용하면 여러 시각화를 하나의 보고서로 가져올 수 있지만 작업 영역과 달리 여전히 간단한 상관 관계와 어떤 데이터를 어떤 열에 배치할 수 있는지에 대해 잠겨 있습니다.

맞춤형 보고서에서 가장 큰 문제 중 하나는 필터를 만들 때 보고서의 모든 탭에 적용되는 것입니다. 동일한 보고서 내에서 두 개의 서로 다른 필터를 비교할 방법이 없습니다.

표면 비교를 위해 작업을 수행합니다. 이는 모두 Adobe Legacy Dashboards, 맞춤형 보고서 및 책갈피와 유사합니다. 보고서 세트 내에 있는 요구 사항을 지원하기 위해 제공되는 기본 도구입니다.

#### 2.1.3. 보고서

Google과 Adobe 모두 차원을 기반으로 하는 기본 타임라인 그래프와 구축된 테이블인 탐색 가능한 보고서를 제공합니다.

##### 2.1.3.1. Adobe Analytics 보고서

Adobe Analytics에는 보고서 섹션도 있지만 대부분 Analysis Workspace를 위해 단계적으로 폐지되고 있습니다(작업 영역 [섹션 2.1.2.1]이 훨씬 강력한 툴이기 때문에 실제로 이 인터페이스의 서비스 종료가 발표됨). 이러한 테이블의 대부분은 더 쉽게 작성하고 수정할 수 있습니다. Adobe의 섹션은 훨씬 더 세분화되어 있으며 이는 매우 어려울 수 있습니다.

![image3](assets/ga-to-aa_6.png)

위의 대부분은 작업 영역을 통해 액세스할 수 있으므로 이러한 섹션의 개요와 Google Analytics와 관련된 방법을 간략히 설명하고 여전히 관련성이 있는 보고서를 강조합니다.

사이트 지표는 사용자가 예상할 수 있는 표준 지표(페이지 조회수, 고유 방문자, 방문 및 설정한 사용자 지정 이벤트)를 포함합니다. 이는 비헤이비어 보고서 GA와 유사하지만 Adobe는 지표 유형을 분할하지 않으므로 Audience에서 볼 수 있는 내용도 일부 포함합니다.

여기에서도 “보트” 보고서를 찾을 수 있습니다. 보트의 트래픽은 모든 표준 보고서에서 제외되지만, 어떤 보트가 사이트로 전송되는지 확인할 수 있는 두 가지 보고서가 있습니다. 이는 사이트를 자주 공격하는 알려진 스패머 보트를 제외하도록 사용자 지정 보트 규칙을 설정하는 경우에 특히 유용합니다. 이러한 보트가 트래픽을 제외하고 기본 보고서가 용량을 초과하지 않고 수행하는 작업에 대한 통찰력을 얻을 수 있습니다. 보트 보고서는 현재 작업 영역을 통해 사용할 수 없습니다(그러나 곧 제공될 새로운 보고 기능을 통해 사용자는 해당 정보도 얻을 수 있습니다).

사이트 콘텐츠는 Adobe 표준 차원(페이지 이름, 사이트 섹션(채널), 계층(웹 사이트 내에 조직의 사용자 지정 드릴다운 보고서를 작성하는 방법), 서버(사이트에 여러 하위 도메인이 있거나 여러 사이트를 하나의 추적 모음으로 태그 지정하려는 경우 특히 유용함)) 등의 그룹입니다. 이러한 모든 기능은 작업 영역에서 사용할 수 있습니다.

모바일은 디바이스, 디바이스 유형 등과 같은 모바일 디바이스 특정 데이터의 그룹입니다. 이러한 모든 기능은 작업 영역에서 사용할 수 있습니다.

경로는 “작업 영역에서 잘 사용할 수 없는” 항목 중 하나입니다. 작업 영역에는 흐름 다이어그램이 있지만 단일 페이지/값에 대한 입력 및 출력 흐름만 볼 수 있습니다. 반면 경로에서는 웹 사이트에서 사용되는 가장 일반적인 경로를 볼 수 있습니다. 기본적으로 페이지는 사용자를 위해 설정된 첫 번째 경로 보고서이지만 사용자 지정 Prop에 대해 이 기능을 켤 수 있습니다(예: “페이지 유형” 값을 추적하려는 경우 페이지 유형 내에서 경로를 볼 수 있음). 경로가 유용한 또 다른 점은 이유는 표시되는 방식의 단순함입니다. 작업 영역의 흐름도(표시되는 양에 따라 다름)는 압도적일 수 있습니다. 두 가지 모두 사용해 보는 것이 좋습니다. 각각은 달성하고자 하는 것에 따라 용도와 가치가 있습니다. 플로우에서는 모든 차원을 사용할 수 있지만, 관리 패널의 Prop에 경로를 지정해야 합니다.

트래픽 소스, 캠페인 및 마케팅 채널 보고서는 모두 Google의 획득 보고서와 유사합니다. 트래픽 소스는 실제 추천자에 초점을 맞추고, 캠페인은 캠페인 코드에 초점을 맞추고, 마케팅 채널도 캠페인 코드에 초점을 맞추지만 정보 처리 방법에 대해 사용자가 결정한 추가 논리도 적용합니다. Adobe는 규칙을 설정하는 방법에 있어 보다 많은 자유를 제공하고 Google은 사용자를 위해 많은 작업을 수행하므로 생각에 약간의 변화가 있을 것입니다. 또한 기본적으로 캠페인 코드에 대한 Google의 속성은 6개월이고 Adobe는 기본적으로 1주로 설정되어 있습니다. 이는 관리자 설정에서 변경할 수 있지만 작업 영역에서는 실제로 모든 차원 위에 사용자 지정 속성을 적용하여 보다 “즉시” 유연성을 제공할 수 있습니다.

방문자 유지 및 방문자 프로필 보고서는 Google Analytics의 대상 보고서와 유사합니다. 유지는 재방문 주기에 더 중점을 두는 반면 방문자 프로필은 사용자의 지역 및 기술에 더 중점을 둡니다.

사용자 지정 전환 및 사용자 지정 트래픽은 모두 사용자 지정 차원 보고서이고, 전환은 eVar입니다. 여기서 사용자 지정 만료(예: 히트, 방문, 월, 년 등)를 사용자 지정 만료 값으로 설정할 수 있으며, 이 값은 덮어쓰지 않는 한 지정된 시간 동안 유지됩니다. 트래픽 변수는 사용자의 Prop이지만 경로 지정 보고서 또는 목록 항목으로 설정할 수도 있습니다(선택한 구분 기호에 따라 여러 값을 구분).

미디어는 특수 미디어 추적을 설정한 비디오 또는 오디오 파일을 위한 것입니다.

사용자 정의 보고서는 사용자가 보고서 인터페이스 내에서 생성한 열 및 분류를 사용자 정의하고 이를 사용자 정의 보고서로 저장할 수 있는 섹션입니다. 그러나 위에서 언급했듯이 작업 영역은 훨씬 더 강력한 분류 및 상관 관계를 허용하므로 사용자 정의된 모든 항목을 작업 영역에서 만들어야 합니다. 이는 작업 영역이 존재하기 이전에 유용한 솔루션이었습니다.

책갈피 섹션은 자주 사용하는 보고서를 보고서 인터페이스 내에서 책갈피로 지정하여 보다 쉽게 찾을 수 있는 사용자 지정 보고서와 유사합니다.

대시보드는 사람들이 데이터 리포트릿을 하나의 시각화로 결합할 수 있도록 하는 레거시 제품이었습니다. 그러나 작업 영역의 기능(섹션 2.1.2.1)을 통해 작업하기가 보다 쉽기 때문에 이 기능이 종료되기 전에 다시 작성해야 하는 레거시 보고서에 대한 액세스 포인트로만 존재합니다.

Targets는 팀이 캠페인과 같은 것을 모니터링하고 트래픽 목표를 달성하기 위한 적절한 과정에 있는지 확인할 수 있도록 사람들이 특정 시간대 내의 목표를 기반으로 보고서를 생성할 수 있는 특별 보고서 영역입니다.

여기에 있는 보고서는 모두 여러 지표 열 및 치수 분류가 허용되었습니다. 그러나 어떤 요소들이 상관관계가 있을 수 있는지에 대한 일부 논리와 시각화가 단순화됨에 따라 때때로 불편함이 있을 수 있습니다.

##### 2.1.3.2. Google Analytics 보고서

Google Analytics는 이러한 보고서를 실시간, 고객, 획득, 비헤이비어 및 대화(GA3), 수명 주기(하위 섹션 포함: 획득, 참여, 수익성, 유지 및 사용자) 및 사용자(하위 섹션 포함: 인구 분포 및 기술) 섹션으로 나눕니다.

![image3](assets/ga-to-aa_7.png)

이러한 시각화를 약간 수정하고, 보조 차원 분류를 추가하고, 시각화를 변경하고, 데이터에 대한 필터를 만드는 등의 작업을 수행할 수 있습니다. 사용자 정의를 저장된 보고서로 저장할 수 있습니다.

이를 통해 빠르고 간편하게 데이터에 대한 통찰력을 얻을 수 있습니다. 그러나 사용자와 같은 항목을 동일한 테이블에 있는 페이지의 페이지 조회수와 비교할 수 없으며 추가 데이터를 보기 위해 두 개 이상의 추가 차원을 추가할 수 없습니다.

이는 빠른 분석 데이터에는 좋지만 실제로 깊이 분석해야 하는 경우에는 한계가 있습니다.

### 2.2. 확장된 보고서 액세스

“사이트 내 보고” 외에도 대부분의 도구는 도구 외부에서 분석을 수행하고 보다 사용자 정의된 것을 구축할 수 있는 확장된 기능을 제공합니다.

#### 2.2.1. Adobe Analytics Report Builder (Microsoft Excel 확장)

작업 영역은 유용한 도구이지만 때로는 데이터를 사용자 정의된 스프레드시트로 가져와야 하므로 여러 데이터 소스를 결합해야 할 수 있습니다. 여기에서 Report Builder가 필요합니다.

Report Builder는 Excel 내에서 조작할 수 있는 테이블 형식 데이터를 가져오기 위해 Adobe Analytics 데이터에 대한 연결을 만들 수 있는 Microsoft Excel용 플러그인입니다. 일반적으로 이를 효율적으로 사용하려면 데이터를 일부 원시 데이터 탭으로 가져온 다음 Excel 셀 참조를 사용하여 이러한 탭의 데이터를 단일 통합 보고서로 가져온 다음 그래프와 시각화를 만듭니다.

>[!NOTE]
>
>Report Builder에는 이 플러그인에 액세스하기 위해 사용자에게 적용해야 하는 특정 권한이 있습니다. 이 권한은 도구를 올바르게 사용하는 방법을 학습한 사용자에게 부여되어야 합니다.

#### 2.2.2. Adobe Analytics API 연결

Adobe Analytics를 Excel이 아닌 다른 항목으로 요약해야 하지만 처리된 데이터(보트 규칙 제외 포함)의 이점을 계속 얻고 싶다면 Adobe의 API를 사용하여 데이터를 직접 가져온 다음 스크립트를 통해 처리하거나 다른 시스템에서 사용할 수 있도록 데이터베이스에 추가할 수 있습니다.

API는 끌어오기 요청에 지정된 대로 분류 및 세그먼트를 적용하는 상관 관계 데이터를 계속 가져옵니다.

Adobe의 작업 영역(섹션 2.1.2.1)은 실제로 API를 사용하여 모든 보고서를 작성하며 작업 영역에서 디버그 모드를 활성화하면 사용된 정확한 API 호출이 표시됩니다. 이는 작업 영역을 사용하여 가져올 데이터를 빌드 및 확인한 다음 해당 API 호출을 사용하여 데이터를 자체 처리에 사용함으로써 API 호출을 빠르게 빌드하는 방법입니다.


#### 2.2.3. Google Analytics Data Studio

위에서 언급했듯이 Data Studio는 Adobe의 작업 영역과 동일합니다. Data Studio를 사용하면 Google Analytics 데이터뿐만 아니라 다른 소스의 데이터도 가져올 수 있습니다. 이는 분석 데이터를 수집된 다른 데이터와 통합하려는 경우에 유용합니다. 그러나 Google Analytics에 있는 것과 동일한 종류의 시각화 제한 사항이 발견되었습니다. 행과 열이 형성되는 방식은 여전히 수행할 수 있는 작업이 매우 제한적입니다.

여전히 강력한 도구이기 때문에 사용하지 않도록 설득하지는 않을 것입니다. 하지만 작업 영역을 오래 사용해 보니 경직된 비헤이비어가 상당히 제한적이었습니다.


#### 2.2.4. Google Spreadsheet Extension

Google Analytics에서 확장된 방식으로 데이터를 가져와야 할 때 선택하길 추천하는 도구는 Google Spreadsheet Extension입니다. GA 테이블에 여러 번 연결해야 하지만 Adobe의 Report Builder와 마찬가지로 원시 데이터의 셀을 참조하고 필요한 보고서를 작성한 다음 Google Spreadsheet의 그래프 생성 기능을 사용하여 시각화할 수 있습니다.


## 3. 원시 데이터 내보내기

원시 데이터가 필요한 경우 Adobe와 Google은 이러한 방식으로 정보를 가져올 수 있는 기능을 제공합니다.

### 3.1. Adobe 데이터 피드

섹션 2.2.2에서 Adobe Analytics API가 “처리된 데이터”에서 추출되었다고 언급했습니다. 원시 데이터 피드는 관리 패널에 설정된 “처리 규칙”에 의해 처리된 데이터를 계속 가져오지만(원시 데이터 피드를 가져올 때까지 이러한 모든 규칙이 완료되도록 원시 데이터가 지연되는지 확인), 이 원시 데이터에는 다른 모든 위치에서 제외되는 모든 데이터가 포함됩니다.

즉, 모든 보트를 제외한 내부 IP 필터링 데이터 등이 원시 데이터 피드에 포함됩니다. 이 데이터를 식별하는 플래그가 있으므로 데이터 레이크를 구축하는 경우 엔지니어링 팀에서 이 데이터를 적절하게 처리하는 논리를 생성할 수 있습니다.

원시 데이터 피드를 사용자 정의하여 데이터의 모든 열을 전송하거나 보다 집중적인 피드가 필요한 경우 특정 열만 전송할 수 있습니다.

피드는 FTP, SFTP, S3 등으로 직접 전송할 수 있습니다.


### 3.2. Google Big Query

이는 직접 사용해 보지 않은 Google 도구이지만 이론상 Adobe의 데이터 피드와 유사해야 엔지니어링 팀이 Google Analytics 계정의 원시 데이터에 액세스할 수 있습니다.

그러나 전체 원시 데이터 덤프가 아닌 SQL 쿼리를 통해 데이터에 액세스할 수 있으므로 엔지니어는 대상 원시 데이터를 가져오거나 모든 원시 데이터 열을 데이터 레이크로 가져올 수 있습니다.

## 4. 결론

다른 시스템과 마찬가지로 익숙해지려면 연습이 필요하지만 이 안내서가 시작하는 데 도움이 되었거나 이를 통해 Adobe Analytics 사용 경험을 개선할 수 있는 팁을 얻을 수 있기를 바랍니다.

그러나 구현 전략에 Adobe Analytics와 Google Analytics를 모두 사용하는 것이 좋습니다(Google Analytics가 무료 버전일지라도). 완벽한 시스템은 없으므로, 이렇게 하여 데이터를 확실하게 보관할 수 있는 백업 시스템을 가질 수 있습니다.

이 안내서 외에도 전략을 개선하는 데 도움이 될 수 있는 많은 리소스가 있습니다.

* [Adobe Experience League](https://experienceleague.adobe.com/#home) - 튜토리얼, 비디오, 설명서 및 커뮤니티 포럼 포함
* [Adobe 사용자 그룹](https://analytics-augs.adobe.com/) - 사용자가 서로 연결하고 구현을 개선하는 데 도움이 되는 커뮤니티 실행 이벤트의 허브입니다. 특정 시간대를 기반으로 하기 때문에 다른 지역에서도 실행되고 있는지 확인하는 것이 좋습니다.
* [Adobe Analytics 사용자 그룹 YouTube 채널](https://www.youtube.com/channel/UCQOHnCs7KZgsuFHVzwboQuA) - Adobe Analytics 사용자 그룹 세션을 만들 수 없습니까? 전 세계의 이전 사용자 그룹 세션을 다시 시청하여 동료들이 도구를 사용하는 방법에 대해 자세히 알아보십시오.
* [채팅 Slack 측정 채널](https://www.measure.chat/) - 전 세계 Adobe Analytics 사용자와 연결하여 업계의 학습 내용을 공유하고, 동료들에게 질문하고, 측정 중심의 관심 그룹에 참여하십시오.
* 이 외에도 다양한 내용이 있습니다!

## 작성자

이 문서의 작성자:

![Jennifer Dungan](assets/Jennifer_Dungan_Headshot150.png)

Jennifer Dungan, Torstar의 최적화 관리자 분석

Adobe Analytics 챔피언
