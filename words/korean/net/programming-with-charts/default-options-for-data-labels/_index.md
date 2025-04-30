---
"description": "Aspose.Words for .NET을 사용하여 차트의 데이터 레이블에 대한 기본 옵션을 설정하는 방법을 알아보세요. 단계별 가이드를 따라 차트를 손쉽게 만들고 사용자 정의해 보세요."
"linktitle": "차트의 데이터 레이블에 대한 기본 옵션 설정"
"second_title": "Aspose.Words 문서 처리 API"
"title": "차트의 데이터 레이블에 대한 기본 옵션 설정"
"url": "/ko/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 차트의 데이터 레이블에 대한 기본 옵션 설정

## 소개

안녕하세요! 문서 자동화의 세계로 뛰어들고 싶으신가요? 오늘은 Aspose.Words for .NET을 사용하여 프로그래밍 방식으로 멋진 문서를 만드는 방법을 알아보겠습니다. Aspose.Words는 Word 문서를 손쉽게 조작할 수 있는 강력한 라이브러리이며, 이 튜토리얼에서는 차트의 데이터 레이블에 대한 기본 옵션을 설정하는 방법을 중점적으로 살펴보겠습니다. 숙련된 개발자든 초보자든, 이 가이드를 통해 각 단계를 안내받아 빠르게 시작하고 실행할 수 있습니다.

## 필수 조건

시작하기 전에, 이 튜토리얼을 따라 하는 데 필요한 모든 것이 있는지 확인해 보세요. 간단한 체크리스트는 다음과 같습니다.

- Visual Studio 또는 기타 .NET 호환 IDE: 여기에서 코드를 작성하고 실행할 수 있습니다.
- Aspose.Words for .NET: 다음을 수행할 수 있습니다. [최신 버전을 다운로드하세요](https://releases.aspose.com/words/net/) 프로젝트에 설치하세요.
- C# 프로그래밍에 대한 기본 지식: 이 가이드는 초보자에게 친화적이지만, C#에 대해 약간 알고 있으면 도움이 될 것입니다.
- .NET Framework가 설치되어 있는지 확인하세요. 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
- Aspose.Words에 대한 임시 라이센스: 하나를 얻으세요 [여기](https://purchase.aspose.com/temporary-license/) 모든 기능을 사용하려면.

이러한 전제 조건을 충족하면 이제 시작할 준비가 되었습니다!

## 네임스페이스 가져오기

먼저 프로젝트를 설정하고 필요한 네임스페이스를 가져오겠습니다. 이 네임스페이스는 Aspose.Words 기능에 접근하는 데 필수적입니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## 1단계: 새 문서 만들기


여행은 새 문서를 만들고 초기화하는 것으로 시작됩니다. `DocumentBuilder`. 그 `DocumentBuilder` 클래스는 문서 내용을 쉽게 조작할 수 있는 일련의 메서드를 제공합니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 새 문서 만들기
Document doc = new Document();

// DocumentBuilder 초기화
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 설명

이 단계에서는 콘텐츠를 삽입하고 서식을 지정하는 데 사용할 문서와 빌더를 설정했습니다. `dataDir` 변수는 최종 문서를 저장할 경로를 저장합니다.

## 2단계: 차트 삽입

다음으로, 문서에 원형 차트를 추가하겠습니다. `InsertChart` 방법 `DocumentBuilder` 수업을 들으면 정말 쉬워집니다.

```csharp
// 파이 차트 삽입
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// 차트 객체에 접근
Chart chart = shape.Chart;
```

### 설명

여기서는 문서에 원형 차트를 삽입합니다. `InsertChart` 이 메서드는 차트 유형, 너비, 높이를 매개변수로 요구합니다. 차트를 삽입한 후에는 차트 객체에 접근하여 추가로 조작할 수 있습니다.

## 3단계: 차트 시리즈 사용자 지정

이제 차트에서 기존 계열을 모두 지우고 사용자 지정 계열을 추가하겠습니다. 이 계열은 데이터 포인트를 나타냅니다.

```csharp
// 기존 차트 시리즈 지우기
chart.Series.Clear();

// 차트에 새로운 시리즈 추가
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### 설명

이 단계에서는 기존 시리즈를 모두 지워 차트가 비어 있는지 확인합니다. 그런 다음, 사용자 지정 범주와 값을 가진 새 시리즈를 추가하여 원형 차트에 표시합니다.

## 4단계: 데이터 레이블에 대한 기본 옵션 설정

데이터 레이블은 차트를 유익하게 만드는 데 매우 중요합니다. 백분율, 값 표시, 구분 기호 사용자 지정 옵션을 설정해 보겠습니다.

```csharp
// 데이터 레이블 컬렉션에 액세스
ChartDataLabelCollection labels = series.DataLabels;

// 데이터 레이블 옵션 설정
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### 설명

여기서 우리는 접근하고 있습니다 `DataLabels` 시리즈의 속성을 사용하여 각 데이터 레이블에 표시되는 모양과 정보를 사용자 지정할 수 있습니다. 백분율과 값을 모두 표시하고, 지시선을 숨기고, 사용자 지정 구분 기호를 설정하도록 했습니다.

## 5단계: 문서 저장

마지막으로, 지정된 디렉터리에 문서를 저장합니다. 이 단계를 통해 모든 변경 사항이 파일에 기록됩니다.

```csharp
// 문서를 저장하세요
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### 설명

이 마지막 단계에서는 다음을 사용하여 문서를 저장합니다. `Save` 메서드. 문서는 지정된 디렉토리에 저장됩니다. `dataDir`이름은 "WorkingWithCharts.DefaultOptionsForDataLabels.docx"입니다.

## 결론

자, 이제 완성되었습니다! Aspose.Words for .NET을 사용하여 사용자 지정 원형 차트가 포함된 Word 문서를 성공적으로 만들었습니다. 이 강력한 라이브러리를 사용하면 문서 생성 및 조작을 쉽게 자동화하여 시간과 노력을 절약할 수 있습니다. 보고서, 송장 또는 기타 유형의 문서를 생성할 때 Aspose.Words가 모든 것을 해결해 드립니다.

자유롭게 탐험해보세요 [Aspose.Words 문서](https://reference.aspose.com/words/net/) 더 많은 기능과 예시를 확인해 보세요. 즐거운 코딩 되세요!

## 자주 묻는 질문

### Aspose.Words를 무료로 사용할 수 있나요?
Aspose.Words를 무료로 사용할 수 있습니다. [임시 면허](https://purchase.aspose.com/temporary-license/) 또는 다음을 사용하여 기능을 탐색하세요. [무료 체험](https://releases.aspose.com/).

### Aspose.Words에 대한 지원을 받으려면 어떻게 해야 하나요?
다음을 통해 지원을 받을 수 있습니다. [Aspose.Words 지원 포럼](https://forum.aspose.com/c/words/8).

### 다른 유형의 차트를 추가할 수 있나요?
네, Aspose.Words는 막대형, 꺾은선형, 세로막대형 차트 등 다양한 차트 유형을 지원합니다. [선적 서류 비치](https://reference.aspose.com/words/net/) 자세한 내용은.

### Aspose.Words는 .NET Core와 호환됩니까?
네, Aspose.Words는 .NET Core와 호환됩니다. 자세한 내용은 [선적 서류 비치](https://reference.aspose.com/words/net/).

### Aspose.Words 라이선스를 어떻게 구매할 수 있나요?
라이센스는 다음에서 구매할 수 있습니다. [애스포즈 매장](https://purchase.aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}