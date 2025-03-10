---
title: 선호하는 너비 설정
linktitle: 선호하는 너비 설정
second_title: Aspose.Words 문서 처리 API
description: 이 단계별 가이드를 통해 Aspose.Words for .NET에서 절대, 상대 및 자동 너비 설정이 적용된 표를 만드는 방법을 알아보세요.
weight: 10
url: /ko/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 선호하는 너비 설정

## 소개

표는 Word 문서에서 정보를 구성하고 표현하는 강력한 방법입니다. Aspose.Words for .NET에서 표로 작업할 때 문서 레이아웃에 완벽하게 맞도록 표 셀의 너비를 설정하는 여러 옵션이 있습니다. 이 가이드에서는 Aspose.Words for .NET을 사용하여 원하는 너비 설정으로 표를 만드는 과정을 안내하며, 절대, 상대 및 자동 크기 조정 옵션에 중점을 둡니다. 

## 필수 조건

튜토리얼을 시작하기 전에 다음 사항이 있는지 확인하세요.

1.  Aspose.Words for .NET: 개발 환경에 Aspose.Words for .NET이 설치되어 있는지 확인하세요. 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).

2. .NET 개발 환경: Visual Studio와 같은 .NET 개발 환경을 설정합니다.

3. C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 코드 조각과 예제를 더 잘 이해하는 데 도움이 됩니다.

4.  Aspose.Words 설명서: 다음을 참조하세요.[Aspose.Words 문서](https://reference.aspose.com/words/net/) 자세한 API 정보와 추가 자료를 확인하세요.

## 네임스페이스 가져오기

코딩을 시작하기 전에 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

이러한 네임스페이스는 Aspose.Words와 Table 개체의 핵심 기능에 대한 액세스를 제공하여 문서 표를 조작할 수 있도록 해줍니다.

다양한 기본 너비 설정을 사용하여 표를 만드는 과정을 명확하고 관리하기 쉬운 단계로 나누어 보겠습니다.

## 1단계: Document 및 DocumentBuilder 초기화

제목: 새 문서 및 DocumentBuilder 만들기

 설명: 새 Word 문서를 만들고 시작합니다.`DocumentBuilder` 인스턴스.`DocumentBuilder` 클래스를 사용하면 문서에 내용을 간단하게 추가할 수 있습니다.

```csharp
// 문서를 저장할 경로를 정의합니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 새 문서를 만듭니다.
Document doc = new Document();

// 이 문서에 대한 DocumentBuilder를 만듭니다.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 여기에서 문서가 저장될 디렉토리를 지정하고 초기화합니다.`Document` 그리고`DocumentBuilder` 사물.

## 2단계: 절대 너비로 첫 번째 테이블 셀 삽입

첫 번째 셀을 고정 너비 40포인트로 테이블에 삽입합니다. 이렇게 하면 테이블 크기에 관계없이 이 셀이 항상 너비 40포인트를 유지합니다.

```csharp
// 절대 크기의 셀을 삽입합니다.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

이 단계에서는 테이블 생성을 시작하고 절대 너비가 있는 셀을 삽입합니다.`PreferredWidth.FromPoints(40)` 이 방법은 셀의 너비를 40포인트로 설정합니다.`Shading.BackgroundPatternColor` 밝은 노란색 배경색을 적용합니다.

## 3단계: 상대 크기 셀 삽입

테이블 전체 너비의 20%인 너비의 다른 셀을 삽입합니다. 이 상대적 크기 조정은 셀이 테이블 너비에 비례하여 조정되도록 합니다.

```csharp
// 상대적(퍼센트) 크기의 셀을 삽입합니다.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

이 셀의 너비는 표 전체 너비의 20%가 되므로 다양한 화면 크기나 문서 레이아웃에 맞게 조정할 수 있습니다.

### 4단계: 자동 크기 조정 셀 삽입

마지막으로, 표의 남은 사용 가능한 공간에 따라 크기가 자동으로 조절되는 셀을 삽입합니다.

```csharp
// 자동 크기 조정 셀을 삽입합니다.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 그만큼`PreferredWidth.Auto` 이 설정은 다른 셀을 고려한 후 남은 공간에 따라 이 셀을 확장하거나 축소할 수 있도록 합니다. 이렇게 하면 테이블 레이아웃이 균형 잡히고 전문적으로 보입니다.

## 5단계: 문서 완성 및 저장

모든 셀을 삽입한 후 표를 완성하고 지정된 경로에 문서를 저장합니다.

```csharp
// 문서를 저장합니다.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

이 단계에서는 표를 완성하고 지정된 디렉토리에 "WorkingWithTables.PreferredWidthSettings.docx"라는 파일 이름으로 문서를 저장합니다.

## 결론

Aspose.Words for .NET에서 선호하는 너비 설정으로 표를 만드는 것은 사용 가능한 다양한 크기 옵션을 이해하면 간단합니다. 고정, 상대 또는 자동 셀 너비가 필요하든 Aspose.Words는 다양한 표 레이아웃 시나리오를 효율적으로 처리할 수 있는 유연성을 제공합니다. 이 가이드에 설명된 단계를 따르면 Word 문서에서 표가 잘 구성되고 시각적으로 매력적으로 보이도록 할 수 있습니다.

## 자주 묻는 질문

### 절대 셀 너비와 상대 셀 너비의 차이점은 무엇입니까?
절대 셀 너비는 고정되어 변경되지 않지만, 상대 너비는 표의 전체 너비에 따라 조정됩니다.

### 상대적 너비에 음수 백분율을 사용할 수 있나요?
아니요, 음수 백분율은 셀 너비에 유효하지 않습니다. 양수 백분율만 허용됩니다.

### 자동 크기 조정 기능은 어떻게 작동하나요?
자동 크기 조정은 다른 셀의 크기가 조정된 후 표의 남은 공간을 채우도록 셀의 너비를 조정합니다.

### 너비 설정이 다른 셀에 다른 스타일을 적용할 수 있나요?
네, 셀 너비 설정에 관계없이 다양한 스타일과 서식을 셀에 적용할 수 있습니다.

### 표의 전체 너비가 모든 셀 너비의 합보다 작으면 어떻게 되나요?
표는 사용 가능한 공간에 맞게 셀 너비를 자동으로 조절하는데, 이로 인해 일부 셀이 줄어들 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
