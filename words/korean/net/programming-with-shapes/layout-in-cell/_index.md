---
title: 셀의 레이아웃
linktitle: 셀의 레이아웃
second_title: Aspose.Words 문서 처리 API
description: 이 포괄적인 가이드를 통해 Aspose.Words for .NET을 사용하여 셀의 레이아웃을 설정하는 방법을 알아보세요. Word 문서를 사용자 지정하려는 개발자에게 완벽합니다.
weight: 10
url: /ko/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 셀의 레이아웃

## 소개

Word 문서에서 테이블 셀의 레이아웃을 프로그래밍 방식으로 미세 조정하고 싶었던 적이 있다면, 당신은 올바른 곳에 있습니다. 오늘은 Aspose.Words for .NET을 사용하여 셀의 레이아웃을 설정하는 방법을 알아보겠습니다. 실용적인 예를 살펴보고, 쉽게 따라할 수 있도록 단계별로 나누어 설명하겠습니다.

## 필수 조건

코드로 넘어가기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.

1.  Aspose.Words for .NET: Aspose.Words for .NET 라이브러리가 설치되어 있는지 확인하세요. 설치되어 있지 않으면 다음을 수행할 수 있습니다.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. 개발 환경: .NET으로 설정된 개발 환경이 필요합니다. 추천 사항을 찾고 있다면 Visual Studio가 좋은 선택입니다.
3. C#에 대한 기본 지식: 각 단계를 설명하겠지만, C#에 대한 기본적인 이해가 있으면 더 쉽게 따라갈 수 있습니다.
4.  문서 디렉토리: 문서를 저장할 디렉토리 경로를 준비합니다. 이것을 다음과 같이 지칭합니다.`YOUR DOCUMENT DIRECTORY`.

## 네임스페이스 가져오기

시작하려면 프로젝트에 필요한 네임스페이스를 가져오는지 확인하세요.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

이 과정을 관리 가능한 단계로 나누어 보겠습니다.

## 1단계: 새 문서 만들기

 먼저 새 Word 문서를 만들고 초기화합니다.`DocumentBuilder` 우리의 콘텐츠 구성에 도움을 주는 객체입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2단계: 테이블 시작 및 행 형식 설정

표를 구성하고 행의 높이와 높이 규칙을 지정해 보겠습니다.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## 3단계: 셀 삽입 및 콘텐츠 채우기

다음으로, 우리는 테이블에 셀을 삽입하기 위해 루프를 돌립니다. 7개의 셀마다, 우리는 행을 끝내서 새로운 셀을 만듭니다.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## 4단계: 워터마크 모양 추가

 이제 문서에 워터마크를 추가해 보겠습니다.`Shape` 객체를 만들고 속성을 설정합니다.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // 셀에 배치될 경우 표 셀 외부에 모양을 표시합니다.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## 5단계: 워터마크 모양 사용자 지정

워터마크의 색상과 텍스트 속성을 설정하여 워터마크의 모양을 더욱 세부적으로 사용자 지정합니다.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## 6단계: 문서에 워터마크 삽입

문서에서 마지막 실행 부분을 찾아 해당 위치에 워터마크를 삽입합니다.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## 7단계: Word 2010에 대한 문서 최적화

호환성을 보장하기 위해 문서를 Word 2010에 맞춰 최적화하겠습니다.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## 8단계: 문서 저장

마지막으로, 지정된 디렉토리에 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## 결론

이제 Aspose.Words for .NET을 사용하여 사용자 지정 테이블 레이아웃이 있는 Word 문서를 성공적으로 만들고 워터마크를 추가했습니다. 이 튜토리얼은 프로세스의 각 부분을 이해하는 데 도움이 되는 명확하고 단계별 가이드를 제공하는 것을 목표로 했습니다. 이러한 기술을 사용하면 이제 더 정교하고 사용자 지정 Word 문서를 프로그래밍 방식으로 만들 수 있습니다.

## 자주 묻는 질문

### 워터마크 텍스트에 다른 글꼴을 사용할 수 있나요?
 네, 글꼴을 설정하여 변경할 수 있습니다.`watermark.TextPath.FontFamily` 원하는 글꼴에 속성을 추가합니다.

### 워터마크의 위치를 어떻게 조정합니까?
 수정할 수 있습니다`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , 그리고`VerticalAlignment` 워터마크의 위치를 조정하는 속성입니다.

### 워터마크에 텍스트 대신 이미지를 사용할 수 있나요?
 물론입니다! 당신은 만들 수 있습니다`Shape` 유형으로`ShapeType.Image` 그리고 이미지를 설정하려면 다음을 사용합니다.`ImageData.SetImage` 방법.

### 행 높이가 다른 표를 만들 수 있나요?
네, 행마다 높이를 다르게 설정할 수 있습니다.`RowFormat.Height` 해당 행에 셀을 삽입하기 전에 속성을 선택합니다.

### 문서에서 워터마크를 제거하려면 어떻게 해야 하나요?
 문서의 모양 컬렉션에서 워터마크를 찾아 호출하면 워터마크를 제거할 수 있습니다.`Remove` 방법.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
