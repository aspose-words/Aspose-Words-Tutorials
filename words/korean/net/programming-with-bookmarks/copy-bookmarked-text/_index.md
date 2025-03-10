---
title: 북마크된 텍스트를 Word 문서에 복사
linktitle: 북마크된 텍스트를 Word 문서에 복사
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 북마크된 텍스트를 Word 문서 간에 손쉽게 복사하세요. 이 단계별 가이드로 방법을 알아보세요.
weight: 10
url: /ko/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 북마크된 텍스트를 Word 문서에 복사

## 소개

한 Word 문서에서 다른 문서로 특정 섹션을 복사해야 하는 경우가 있었나요? 글쎄요, 운이 좋으시네요! 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 한 Word 문서에서 다른 문서로 북마크된 텍스트를 복사하는 방법을 안내해 드리겠습니다. 동적 보고서를 작성하든 문서 생성을 자동화하든 이 가이드는 프로세스를 간소화해 드립니다.

## 필수 조건

자세한 내용을 살펴보기 전에 다음 사항이 있는지 확인하세요.

-  Aspose.Words for .NET 라이브러리: 여기에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio 또는 기타 .NET 개발 환경.
- C#에 대한 기본 지식: C# 프로그래밍과 .NET 프레임워크에 익숙함.

## 네임스페이스 가져오기

시작하려면 프로젝트에 필요한 네임스페이스를 가져왔는지 확인하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## 1단계: 소스 문서 로드

먼저, 복사하려는 북마크된 텍스트가 포함된 소스 문서를 로드해야 합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 여기,`dataDir` 문서 디렉토리의 경로입니다.`Bookmarks.docx` 출처 문서입니다.

## 2단계: 북마크 식별

다음으로, 원본 문서에서 복사하려는 책갈피를 식별합니다.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 바꾸다`"MyBookmark1"` 북마크의 실제 이름을 입력하세요.

## 3단계: 대상 문서 만들기

이제 북마크된 텍스트를 복사할 새 문서를 만듭니다.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## 4단계: 북마크된 콘텐츠 가져오기

 스타일과 서식이 유지되도록 하려면 다음을 사용하세요.`NodeImporter` 북마크된 콘텐츠를 소스 문서에서 대상 문서로 가져옵니다.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## 5단계: AppendBookmarkedText 메서드 정의

마법이 일어나는 곳은 바로 여기입니다. 북마크된 텍스트의 복사를 처리하는 방법을 정의합니다.

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## 6단계: 대상 문서 저장

마지막으로 복사된 내용을 확인하기 위해 대상 문서를 저장합니다.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## 결론

그리고 그게 전부입니다! Aspose.Words for .NET을 사용하여 북마크된 텍스트를 한 Word 문서에서 다른 문서로 성공적으로 복사했습니다. 이 방법은 문서 조작 작업을 자동화하는 데 강력하여 워크플로를 보다 효율적이고 간소화합니다.

## 자주 묻는 질문

### 여러 개의 북마크를 한 번에 복사할 수 있나요?
네, 여러 개의 북마크를 반복하면서 동일한 방법으로 각각을 복사할 수 있습니다.

### 북마크를 찾을 수 없으면 어떻게 되나요?
 그만큼`Range.Bookmarks` 재산은 반환됩니다`null`따라서 예외를 피하기 위해 이 사례를 처리해야 합니다.

### 원본 책갈피의 서식을 보존할 수 있나요?
 물론입니다! 사용 중`ImportFormatMode.KeepSourceFormatting` 원래 서식이 보존되도록 합니다.

### 북마크된 텍스트의 크기에 제한이 있나요?
특별한 제한은 없지만, 매우 큰 문서의 경우 성능이 달라질 수 있습니다.

### 서로 다른 Word 문서 형식 간에 텍스트를 복사할 수 있나요?
네, Aspose.Words는 다양한 Word 형식을 지원하며, 이 방법은 이러한 형식에서 작동합니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
