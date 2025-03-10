---
title: Word 문서에서 행 책갈피 풀기
linktitle: Word 문서에서 행 책갈피 풀기
second_title: Aspose.Words 문서 처리 API
description: .NET용 Aspose.Words를 사용하여 Word 문서에서 얽힌 행 북마크를 쉽게 풀 수 있습니다. 이 가이드는 보다 깨끗하고 안전한 북마크 관리를 위한 과정을 안내합니다.
weight: 10
url: /ko/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 행 책갈피 풀기

## 소개

책갈피로 Word 문서의 행을 삭제하면 인접한 행의 다른 책갈피가 엉망이 되는 상황을 겪은 적이 있습니까? 이는 특히 복잡한 테이블을 처리할 때 매우 실망스러울 수 있습니다. 다행히 Aspose.Words for .NET은 행 북마크 풀기라는 강력한 솔루션을 제공합니다. 

이 가이드는 .NET용 Aspose.Words를 사용하여 Word 문서에서 행 북마크를 푸는 과정을 안내합니다. 코드를 이해하기 쉬운 단계로 나누고 각 기능의 목적을 설명하여 성가신 북마크 문제를 자신있게 해결할 수 있도록 도와드립니다.

## 전제 조건

다이빙을 시작하기 전에 몇 가지 사항이 필요합니다.

1.  Aspose.Words for .NET: 이 상용 라이브러리는 프로그래밍 방식으로 Word 문서 작업을 위한 기능을 제공합니다. 2. 다음에서 무료 평가판을 다운로드할 수 있습니다.[다운로드 링크](https://releases.aspose.com/words/net/) 또는 다음에서 라이센스를 구매하세요.[구입하다](https://purchase.aspose.com/buy).
3. AC# 개발 환경: Visual Studio 또는 기타 C# IDE가 완벽하게 작동합니다.
4. 행 책갈피가 있는 Word 문서: 데모 목적으로 "테이블 열 책갈피.docx"라는 샘플 문서를 사용합니다.

## 네임스페이스 가져오기

첫 번째 단계에서는 필요한 네임스페이스를 C# 프로젝트로 가져오는 작업이 포함됩니다. 이러한 네임스페이스는 .NET용 Aspose.Words에서 사용할 클래스와 기능에 대한 액세스를 제공합니다.

```csharp
using Aspose.Words;
using System;
```

## 1단계: Word 문서 로드

 얽힌 행 책갈피가 포함된 Word 문서를 로드하는 것부터 시작합니다. 그만큼`Document` 클래스는 Aspose.Words에서 문서 조작을 처리합니다. 문서를 로드하는 방법은 다음과 같습니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // 문서 위치로 바꾸기
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 교체하는 것을 기억하세요`"YOUR DOCUMENT DIRECTORY"` "테이블 열 북마크.docx" 파일의 실제 경로를 사용하세요.

## 2단계: 행 북마크 풀기

 이곳이 바로 마법이 일어나는 곳입니다! 그만큼`Untangle` 함수는 행 북마크를 풀어줍니다. 기능을 분석해 보겠습니다.

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // 북마크와 북마크 끝의 상위 행을 가져옵니다.
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // 행이 유효하고 인접한지 확인하세요.
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //북마크 끝을 맨 위 행 마지막 셀의 마지막 단락으로 이동합니다.
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

다음은 코드가 수행하는 작업에 대한 단계별 설명입니다.

 우리는 다음을 사용하여 문서의 모든 북마크를 반복합니다.`foreach` 고리.
각 북마크에 대해 북마크 시작(`bookmark.BookmarkStart`) 및 북마크 끝(`bookmark.BookmarkEnd` )를 사용하여`GetAncestor` 방법.
그런 다음 두 행이 모두 발견되었는지 확인합니다(`row1 != null`그리고`row2 != null`) 그리고 인접한 행인 경우(`row1.NextSibling == row2`). 이렇게 하면 인접한 행에 걸쳐 있는 책갈피만 수정할 수 있습니다.
조건이 충족되면 북마크 끝 노드를 맨 위 행의 마지막 셀에 있는 마지막 단락의 끝으로 이동합니다(`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) 효과적으로 엉킨 부분을 풀어줍니다.

## 3단계: 북마크별로 행 삭제

 이제 북마크가 풀렸으므로 북마크 이름을 사용하여 행을 안전하게 삭제할 수 있습니다. 그만큼`DeleteRowByBookmark` 함수가 이 작업을 처리합니다.

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

이 기능에 대한 분석은 다음과 같습니다.

북마크 이름을 사용합니다(`bookmarkName`)를 입력으로 사용합니다.
 다음을 사용하여 해당 북마크 객체를 검색합니다.`doc.Range.Bookmarks[bookmarkName]`.
그런 다음 북마크의 상위 행을 사용하여 시작합니다.`GetAncestor` (비슷하다`Untangle` 기능).
마지막으로 북마크와 행이 존재하는지 확인합니다(`bookmark != null` 그리고

## 4단계: 풀림 확인

 동안`Untangle` 기능은 다른 북마크의 안전을 보장해야 하므로 항상 확인하는 것이 좋습니다. 풀기 과정에서 다른 책갈피의 끝 부분이 실수로 삭제되지 않았는지 확인하는 방법은 다음과 같습니다.

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

이 코드 조각은 "ROW2" 책갈피가 있는 행을 삭제한 후에도 "ROW1"이라는 책갈피의 끝이 여전히 존재하는지 확인합니다. null인 경우 예외가 발생하여 풀기 프로세스에 문제가 있음을 나타냅니다. 

## 5단계: 문서 저장

 마지막으로 북마크를 풀고 행을 삭제할 가능성이 있는 경우 다음을 사용하여 수정된 문서를 저장합니다.`Save` 방법:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

이렇게 하면 얽힌 북마크와 삭제된 행이 포함된 문서가 새 파일 이름 "WorkingWithBookmarks.UntangleRowBookmarks.docx"로 저장됩니다. 

## 결론

 다음 단계를 따르고`Untangle`기능을 사용하면 .NET용 Aspose.Words를 사용하여 Word 문서에서 행 북마크를 효과적으로 풀 수 있습니다. 이렇게 하면 책갈피로 행을 삭제할 때 인접한 행의 다른 책갈피에 의도하지 않은 결과가 발생하지 않습니다. 다음과 같은 자리 표시자를 교체하는 것을 잊지 마세요.`"YOUR DOCUMENT DIRECTORY"` 실제 경로와 파일 이름으로.

## FAQ

### .NET용 Aspose.Words는 무료인가요?

 Aspose.Words for .NET은 무료 평가판이 제공되는 상용 라이브러리입니다. 다음에서 다운로드할 수 있습니다.[다운로드 링크](https://releases.aspose.com/words/net/).

### Word에서 수동으로 행 책갈피를 풀 수 있나요?

기술적으로는 가능하지만 Word에서 북마크를 수동으로 푸는 것은 지루하고 오류가 발생하기 쉽습니다. Aspose.Words for .NET은 이 프로세스를 자동화하여 시간과 노력을 절약해 줍니다.

###  다음과 같은 경우 어떻게 되나요?`Untangle` function encounters an error?

코드에는 풀기 프로세스에서 실수로 다른 책갈피의 끝을 삭제하는 경우 예외를 발생시키는 예외 처리기가 포함되어 있습니다. 특정 요구 사항에 맞게 이 오류 처리를 사용자 정의할 수 있습니다.

### 이 코드를 사용하여 인접하지 않은 행의 북마크를 풀 수 있나요?

현재 코드는 인접한 행에 걸쳐 있는 북마크를 푸는 데 중점을 두고 있습니다. 인접하지 않은 행을 처리하도록 코드를 수정하려면 해당 시나리오를 식별하고 처리하기 위한 추가 논리가 필요합니다.

### 이 접근 방식을 사용하는 데 제한이 있나요?

이 접근 방식에서는 책갈피가 테이블 셀 내에 잘 정의되어 있다고 가정합니다. 북마크가 셀 외부 또는 예상치 못한 위치에 배치된 경우 엉킴 풀기 프로세스가 의도한 대로 작동하지 않을 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
