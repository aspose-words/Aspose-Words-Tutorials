---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에서 CustomXmlPart에 매핑된 반복 섹션이 있는 표를 만드는 방법을 알아보세요."
"linktitle": "사용자 정의 XML 부분에 매핑된 테이블 반복 섹션 만들기"
"second_title": "Aspose.Words 문서 처리 API"
"title": "사용자 정의 XML 부분에 매핑된 테이블 반복 섹션 만들기"
"url": "/ko/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 사용자 정의 XML 부분에 매핑된 테이블 반복 섹션 만들기

## 소개

이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 사용자 지정 XML 파트에 매핑되는 반복되는 섹션이 있는 표를 만드는 과정을 살펴보겠습니다. 이 기능은 구조화된 데이터를 기반으로 동적으로 문서를 생성하는 데 특히 유용합니다.

## 필수 조건

시작하기에 앞서 다음 사항이 있는지 확인하세요.
1. Aspose.Words for .NET 라이브러리가 설치되어 있습니다. 다음에서 다운로드할 수 있습니다. [Aspose 웹사이트](https://releases.aspose.com/words/net/).
2. C#과 XML에 대한 기본적인 이해.

## 네임스페이스 가져오기

프로젝트에 필요한 네임스페이스를 포함했는지 확인하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## 1단계: Document 및 DocumentBuilder 초기화

먼저 새 문서를 만들고 초기화합니다. `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2단계: 사용자 정의 XML 부분 추가

문서에 사용자 지정 XML 부분을 추가합니다. 이 XML에는 테이블에 매핑할 데이터가 포함되어 있습니다.

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## 3단계: 테이블 구조 만들기

다음으로, 다음을 사용하세요 `DocumentBuilder` 테이블 머리글을 만들려면:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## 4단계: 반복 섹션 만들기

생성하다 `StructuredDocumentTag` 반복되는 섹션에 대한 (SDT)를 XML 데이터에 매핑합니다.

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## 5단계: 반복 섹션 항목 만들기

반복 섹션 항목에 대한 SDT를 만들고 반복 섹션에 추가합니다.

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## 6단계: XML 데이터를 테이블 셀에 매핑

제목과 저자에 대한 SDT를 만들고 이를 XML 데이터에 매핑한 다음 행에 추가합니다.

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## 7단계: 문서 저장

마지막으로, 지정된 디렉토리에 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## 결론

다음 단계를 따르면 Aspose.Words for .NET을 사용하여 사용자 지정 XML 파트에 매핑된 반복 구역이 있는 표를 성공적으로 만들 수 있습니다. 이를 통해 구조화된 데이터를 기반으로 동적 콘텐츠를 생성할 수 있으므로 문서 작성이 더욱 유연하고 강력해집니다.

## 자주 묻는 질문

### StructuredDocumentTag(SDT)란 무엇인가요?
SDT는 콘텐츠 컨트롤이라고도 하며, 문서 내에서 구조화된 데이터를 담는 데 사용되는 제한된 영역입니다.

### 사용자 정의 XML 부분에서 다른 데이터 유형을 사용할 수 있나요?
네, 사용자 정의 XML 부분을 원하는 데이터 유형으로 구성하고 이에 따라 매핑할 수 있습니다.

### 반복 섹션에 행을 더 추가하려면 어떻게 해야 하나요?
반복 섹션은 매핑된 XML 경로의 각 항목에 대한 행 구조를 자동으로 복제합니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}