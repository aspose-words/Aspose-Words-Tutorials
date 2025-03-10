---
title: 포맷된 표
linktitle: 포맷된 표
second_title: Aspose.Words 문서 처리 API
description: 이 자세한 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 표를 만들고 서식을 지정하는 방법을 알아보세요.
weight: 10
url: /ko/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 포맷된 표

## 소개

Word 문서에서 프로그래밍 방식으로 표를 만들고 서식을 지정하는 것은 어려운 작업처럼 보일 수 있지만 Aspose.Words for .NET을 사용하면 간단하고 관리하기 쉬워집니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에서 서식이 지정된 표를 만드는 방법을 안내합니다. 환경을 설정하는 것부터 문서를 아름답게 서식이 지정된 표로 저장하는 것까지 모든 것을 다룹니다.

## 필수 조건

코드를 살펴보기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.

1. Aspose.Words for .NET 라이브러리: 여기에서 다운로드하세요.[여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 IDE.
3. .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.

## 네임스페이스 가져오기

실제 코드를 작성하기 전에 필요한 네임스페이스를 가져와야 합니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## 1단계: 문서 디렉토리 설정

먼저, 문서가 저장될 경로를 정의해야 합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 문서를 저장하려는 실제 경로를 입력합니다.

## 2단계: Document 및 DocumentBuilder 초기화

이제 새 문서와 DocumentBuilder 객체를 초기화합니다.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 그만큼`DocumentBuilder` 문서 작성 과정을 단순화하는 도우미 클래스입니다.

## 3단계: 테이블 시작

 다음으로, 다음을 사용하여 테이블 생성을 시작합니다.`StartTable` 방법.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

표를 시작하려면 셀을 삽입해야 합니다.

## 4단계: 표 전체 서식 적용

전체 표에 영향을 미치는 서식을 적용할 수 있습니다. 예를 들어, 왼쪽 들여쓰기 설정:

```csharp
table.LeftIndent = 20.0;
```

## 5단계: 헤더 행 서식 지정

헤더 행의 높이, 정렬 및 기타 속성을 설정합니다.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

이 단계에서는 배경색, 글꼴 크기, 정렬을 설정하여 헤더 행을 눈에 띄게 만듭니다.

## 6단계: 추가 헤더 셀 삽입

헤더 행에 더 많은 셀을 삽입하세요:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## 7단계: 본문 행 서식 지정

헤더를 설정한 후 표 본문의 서식을 지정합니다.

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## 8단계: 본문 행 삽입

내용이 있는 본문 행을 삽입합니다.

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

추가 행에 대해 반복합니다.

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## 9단계: 문서 저장

마지막으로, 지정된 디렉토리에 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

이렇게 하면 서식이 지정된 표가 포함된 Word 문서가 생성되어 저장됩니다.

## 결론

이제 다 됐어요! 다음 단계를 따르면 Aspose.Words for .NET을 사용하여 Word 문서에서 잘 포맷된 표를 만들 수 있습니다. 이 강력한 라이브러리를 사용하면 Word 문서를 프로그래밍 방식으로 쉽게 조작할 수 있어 시간과 노력을 절약할 수 있습니다.

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?
Aspose.Words for .NET은 Word 문서를 프로그래밍 방식으로 만들고, 편집하고, 변환하기 위한 강력한 라이브러리입니다.

### 다른 줄에 다른 색상을 사용할 수 있나요?
네, 다양한 행이나 셀에 색상 등 다양한 서식을 적용할 수 있습니다.

### Aspose.Words for .NET은 무료인가요?
 Aspose.Words for .NET은 유료 라이브러리이지만 다음을 얻을 수 있습니다.[무료 체험](https://releases.aspose.com/).

### Aspose.Words for .NET에 대한 지원을 받으려면 어떻게 해야 하나요?
 당신은에서 지원을 받을 수 있습니다[Aspose 커뮤니티 포럼](https://forum.aspose.com/c/words/8).

### Aspose.Words for .NET으로 다른 유형의 문서를 만들 수 있나요?
네, Aspose.Words for .NET은 PDF, HTML, TXT 등 다양한 문서 형식을 지원합니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
