---
title: 표준화된 이름 지정 규칙 만들기
description: 표준화된 이름 지정 규칙은 AA 관리자 UI에서 활성화될 때 변수 이름 자체와 차원에 전달된 값 모두에 적용됩니다.
feature: Implementation Basics
topic: Administration
role: Admin
level: Beginner
doc-type: article
thumbnail: 10531.jpg
kt: 10531
source-git-commit: 160df6c23acb67f1b07f2fcd25f1eca96eb6dee7
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# 표준화된 이름 지정 규칙 만들기

**내용:** 표준화된 이름 지정 규칙은 AA(Adobe Analytics) 관리 UI에서 활성화될 때 변수 이름 자체와 차원에 전달된 값 모두에 적용됩니다. (즉, 페이지 이름은 변수 이름으로 &quot;page name (v1)&quot;이고 전달된 페이지 이름 값은 동일해야 하며 &quot;sitename|homepage&quot; 또는 &quot;sitename|search|searchresults&quot;와 같은 특정 구조/계층을 따라야 합니다.)

**이유:** 이름 지정 규칙은 모든 항목을 균일하게 유지하고 사용자가 쉽게 이해할 수 있도록 하는 좋은 방법입니다. 처음부터 만들고 플랫폼과 코드에 적용하면 더 쉽게 크기가 조정됩니다.

**방법:** 인터페이스와 태깅 문서는 &#39;이름&#39;과 &#39;설명&#39;에 모두 일치해야 합니다. 이렇게 하면 사용자가 Excel 문서를 가져올 필요가 없고 인터페이스에서 직접 데이터를 이해할 수 있습니다. 일관성을 위해 모든 대/소문자를 줄이는 것이 좋습니다.

플랫폼뿐만 아니라(또는 앱의 화면 이름)에서 페이지 이름을 일관되게 유지하는 것이 가장 좋습니다. 예를 들어 &quot;property&quot;를 설정할 수 있습니다:section:하위 섹션: 하위 섹션:고유 페이지 이름&quot;을 변수/차원에 추가합니다. 이러한 모든 필드가 데이터 계층의 개별 필드인 경우 JS 파일/Launch에서 직접 페이지 이름을 작성할 수도 있습니다. 이러한 모든 요소를 자체 차원으로 설정하면 사이트/앱의 특정 속성 또는 영역을 보다 쉽게 분류하고 트래픽 및 흐름을 더 잘 이해할 수 있습니다.

명명 규칙과 같은 간단한 명명 규칙을 포함하여 사용자가 데이터를 쉽게 찾고 이해할 수 있게 되면 Adobe Analytics의 사용이 증가하고 비즈니스에 대한 더 나은 통찰력을 제공할 수 있습니다.

## 작성자

이 문서는 다음에 의해 공동 작성되었습니다.

![크리스텔 구이돈](assets/Christel-Headshot-150.png)

Chritel Guidon, NortonLifeLock Adobe Analytics Champion의 Digital Analytics Platform Manager

![레이철 펜윅](assets/Rachel-Fenwick-150.png)

Rachel Fenwick, Adobe 수석 컨설턴트
