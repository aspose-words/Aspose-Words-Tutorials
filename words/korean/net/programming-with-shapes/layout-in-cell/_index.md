---
"description": "Aspose.Words for .NET을 사용하여 셀 레이아웃을 설정하는 방법을 포괄적으로 안내하는 가이드입니다. Word 문서를 사용자 지정하려는 개발자에게 적합합니다."
"linktitle": "셀 레이아웃"
"second_title": "Aspose.Words 문서 처리 API"
"title": "셀 레이아웃"
"url": "/ko/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 셀 레이아웃

## 소개

Word 문서에서 표 셀의 레이아웃을 프로그래밍 방식으로 미세 조정하고 싶었던 적이 있다면, 바로 여기가 정답입니다. 오늘은 Aspose.Words for .NET을 사용하여 셀의 레이아웃을 설정하는 방법을 자세히 알아보겠습니다. 쉽게 따라 할 수 있도록 단계별로 나누어 실제 예제를 살펴보겠습니다.

## 필수 조건

코드로 넘어가기 전에 필요한 모든 것이 있는지 확인해 보겠습니다.

1. Aspose.Words for .NET: Aspose.Words for .NET 라이브러리가 설치되어 있는지 확인하세요. 설치되어 있지 않은 경우 [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. 개발 환경: .NET으로 설정된 개발 환경이 필요합니다. Visual Studio는 추천을 받고 싶다면 좋은 선택입니다.
3. C#에 대한 기본 지식: 각 단계를 설명하겠지만, C#에 대한 기본적인 이해가 있으면 더 쉽게 따라갈 수 있습니다.
4. 문서 디렉터리: 문서를 저장할 디렉터리 경로를 준비합니다. 이를 "문서 디렉터리"라고 합니다. `YOUR DOCUMENT DIRECTORY`.

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

먼저 새 Word 문서를 만들고 초기화합니다. `DocumentBuilder` 우리의 콘텐츠 구성에 도움을 주는 객체입니다.

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

다음으로, 표에 셀을 삽입하기 위해 루프를 돌립니다. 셀이 7개씩 추가될 때마다 행을 종료하여 새 셀을 만듭니다.

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

이제 문서에 워터마크를 추가해 보겠습니다. `Shape` 객체를 만들고 속성을 설정합니다.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // 셀에 배치될 경우, 표 셀 외부에 모양을 표시합니다.
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

## 7단계: Word 2010에 맞게 문서 최적화

호환성을 보장하기 위해 Word 2010에 맞춰 문서를 최적화하겠습니다.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## 8단계: 문서 저장

마지막으로, 지정된 디렉토리에 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## 결론

자, 이제 완성했습니다! Aspose.Words for .NET을 사용하여 사용자 지정 표 레이아웃을 적용하고 워터마크를 추가한 Word 문서를 성공적으로 만들었습니다. 이 튜토리얼은 각 과정의 이해를 돕기 위한 명확한 단계별 가이드를 제공합니다. 이러한 기술을 활용하면 이제 더욱 정교하고 사용자 지정 가능한 Word 문서를 프로그래밍 방식으로 만들 수 있습니다.

## 자주 묻는 질문

### 워터마크 텍스트에 다른 글꼴을 사용할 수 있나요?
네, 글꼴을 설정하여 변경할 수 있습니다. `watermark.TextPath.FontFamily` 원하는 글꼴에 속성을 추가합니다.

### 워터마크의 위치를 어떻게 조정합니까?
수정할 수 있습니다 `RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment`, 그리고 `VerticalAlignment` 워터마크의 위치를 조정하는 속성입니다.

### 워터마크에 텍스트 대신 이미지를 사용할 수 있나요?
물론입니다! `Shape` 유형으로 `ShapeType.Image` 그리고 이미지를 사용하여 설정합니다. `ImageData.SetImage` 방법.

### 행 높이가 다른 표를 만들 수 있나요?
예, 각 행에 대해 다른 높이를 설정하려면 다음을 변경하세요. `RowFormat.Height` 해당 행에 셀을 삽입하기 전에 속성을 선택합니다.

### 문서에서 워터마크를 제거하려면 어떻게 해야 하나요?
문서의 모양 컬렉션에서 워터마크를 찾아 호출하면 워터마크를 제거할 수 있습니다. `Remove` 방법.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}