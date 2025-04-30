---
"description": "Aspose.Words for .NET을 사용하여 반복되는 표 머리글 행이 있는 Word 문서를 만드는 방법을 알아보세요. 이 가이드를 따라 전문적이고 세련된 문서를 만들어 보세요."
"linktitle": "다음 페이지에서 행 반복"
"second_title": "Aspose.Words 문서 처리 API"
"title": "다음 페이지에서 행 반복"
"url": "/ko/net/programming-with-tables/repeat-rows-on-subsequent-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 다음 페이지에서 행 반복

## 소개

Word 문서를 프로그래밍 방식으로 만드는 것은, 특히 여러 페이지에 걸쳐 서식을 유지해야 할 때 매우 어려운 작업일 수 있습니다. Word에서 표를 만들다가 머리글 행이 다음 페이지에서 반복되지 않는다는 것을 깨달은 적이 있으신가요? 걱정하지 마세요! Aspose.Words for .NET을 사용하면 표 머리글이 각 페이지에서 반복되도록 간편하게 설정할 수 있어 문서에 전문적이고 세련된 느낌을 더할 수 있습니다. 이 튜토리얼에서는 간단한 코드 예제와 자세한 설명을 통해 이를 구현하는 단계를 안내해 드리겠습니다. 자, 시작해 볼까요!

## 필수 조건

시작하기에 앞서 다음 사항이 있는지 확인하세요.

1. Aspose.Words for .NET: 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
2. 컴퓨터에 .NET Framework가 설치되어 있어야 합니다.
3. Visual Studio나 .NET 개발을 지원하는 다른 IDE.
4. C# 프로그래밍에 대한 기본적인 이해.

계속하기 전에 Aspose.Words for .NET을 설치하고 개발 환경을 설정했는지 확인하세요.

## 네임스페이스 가져오기

시작하려면 프로젝트에 필요한 네임스페이스를 가져와야 합니다. C# 파일 맨 위에 다음 using 지시문을 추가합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

이러한 네임스페이스에는 Word 문서와 표를 조작하는 데 필요한 클래스와 메서드가 포함되어 있습니다.

## 1단계: 문서 초기화

먼저 새 Word 문서를 만들고 `DocumentBuilder` 우리의 테이블을 구성합니다.

```csharp
// 문서 디렉토리 경로 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

이 코드는 새 문서를 초기화합니다. `DocumentBuilder` 문서 구조를 구축하는 데 도움이 되는 객체입니다.

## 2단계: 표 시작 및 머리글 행 정의

다음으로, 표를 시작하고 후속 페이지에서 반복할 헤더 행을 정의합니다.

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

여기서 우리는 새로운 테이블을 시작하고 설정합니다. `HeadingFormat` 재산에 `true` 행이 머리글임을 나타내고, 셀의 정렬과 너비를 정의합니다.

## 3단계: 테이블에 데이터 행 추가

이제 표에 여러 개의 데이터 행을 추가해 보겠습니다. 이 행들은 다음 페이지에서 반복되지 않습니다.

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

이 루프는 각 행에 두 개의 열이 있는 50개 행의 데이터를 테이블에 삽입합니다. `HeadingFormat` 로 설정됩니다 `false` 이 행은 헤더 행이 아니므로

## 4단계: 문서 저장

마지막으로, 지정된 디렉토리에 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

이렇게 하면 지정된 이름의 문서가 문서 디렉토리에 저장됩니다.

## 결론

자, 이제 완성되었습니다! Aspose.Words for .NET을 사용하면 몇 줄의 코드만으로 다음 페이지에 반복되는 머리글 행이 있는 표가 있는 Word 문서를 만들 수 있습니다. 이렇게 하면 문서의 가독성이 향상될 뿐만 아니라 일관되고 전문적인 디자인도 보장됩니다. 자, 이제 여러분의 프로젝트에서 이 기능을 직접 사용해 보세요!

## 자주 묻는 질문

### 헤더 행을 추가로 사용자 지정할 수 있나요?
예, 헤더 행의 속성을 수정하여 추가 서식을 적용할 수 있습니다. `ParagraphFormat`, `RowFormat`, 그리고 `CellFormat`.

### 표에 열을 더 추가할 수 있나요?
물론입니다! 더 많은 셀을 삽입하여 필요한 만큼 열을 추가할 수 있습니다. `InsertCell` 방법.

### 다음 페이지에서 다른 행을 반복하려면 어떻게 해야 하나요?
행을 반복하려면 다음을 설정하세요. `RowFormat.HeadingFormat` 재산에 `true` 해당 행에 대해서.

### 이 방법을 문서의 기존 표에도 사용할 수 있나요?
예, 다음을 통해 기존 테이블에 액세스하여 수정할 수 있습니다. `Document` 객체를 선택하고 비슷한 서식을 적용합니다.

### Aspose.Words for .NET에는 어떤 다른 표 서식 옵션이 있나요?
Aspose.Words for .NET은 셀 병합, 테두리 설정, 표 정렬 등 다양한 표 서식 옵션을 제공합니다. [선적 서류 비치](https://reference.aspose.com/words/net/) 자세한 내용은.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}