---
title: Word 문서에서 책갈피 숨기기 표시
linktitle: Word 문서에서 책갈피 숨기기 표시
second_title: Aspose.Words 문서 처리 API
description: 단계별 가이드를 통해 .NET용 Aspose.Words를 사용하여 Word 문서에서 북마크를 동적으로 표시하거나 숨기는 방법을 알아보세요. 개발자에게 적합합니다.
weight: 10
url: /ko/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 책갈피 숨기기 표시

## 소개

Word 문서의 특정 부분을 동적으로 숨기거나 표시해야 했던 적이 있습니까? 글쎄, 당신은 운이 좋다! Aspose.Words for .NET을 사용하면 문서에서 북마크된 콘텐츠의 가시성을 쉽게 관리할 수 있습니다. 이 튜토리얼은 Aspose.Words for .NET을 사용하여 Word 문서에서 북마크를 표시하고 숨기는 과정을 안내합니다. 우리는 코드를 단계별로 분석할 것이므로 숙련된 개발자이든 초보자이든 이 가이드를 쉽게 따라할 수 있습니다.

## 전제조건

코드를 살펴보기 전에 필요한 모든 것이 갖추어져 있는지 확인하겠습니다.

1.  .NET용 Aspose.Words: .NET용 Aspose.Words 라이브러리가 설치되어 있는지 확인하세요. 그렇지 않은 경우 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 IDE.
3. C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 도움이 됩니다.
4. Word 문서: 책갈피가 포함된 샘플 Word 문서입니다.

## 네임스페이스 가져오기

코드를 시작하기 전에 필요한 네임스페이스를 가져와야 합니다. C# 파일 시작 부분에 다음을 추가합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## 1단계: 문서 로드

먼저 책갈피가 포함된 Word 문서를 로드해야 합니다. 방법은 다음과 같습니다.

```csharp
// 문서 디렉터리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### 설명

- dataDir: Word 문서가 있는 디렉터리 경로입니다.
-  문서 문서: 이는 새 인스턴스를 초기화합니다.`Document` 지정된 파일로 클래스를 작성하십시오.

## 2단계: 북마크된 콘텐츠 표시 또는 숨기기

다음으로 북마크된 콘텐츠를 표시하거나 숨기는 방법을 정의하겠습니다. 완전한 방법은 다음과 같습니다.

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD 북마크}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### 설명

- Bookmark bm: 문서에서 북마크를 가져옵니다.
- DocumentBuilder 빌더: 문서 탐색 및 수정에 도움이 됩니다.
- 필드 필드: 북마크 상태를 확인하기 위한 IF 필드를 삽입합니다.
- Node currentNode: 노드를 탐색하여 필드 시작 및 끝을 찾습니다.

## 3단계: 표시/숨기기 기능 실행

 이제 전화를 걸어야 합니다.`ShowHideBookmarkedContent` 메소드, 문서, 북마크 이름 및 가시성 플래그를 전달합니다.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### 설명

- doc: 문서 개체입니다.
- "MyBookmark1": 표시하거나 숨기려는 북마크의 이름입니다.
- false: 가시성 플래그입니다(표시하는 경우 true, 숨기는 경우 false).

## 4단계: 문서 저장

마지막으로 수정된 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### 설명

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": 변경 사항이 저장될 새 문서의 경로와 이름입니다.

## 결론

그리고 거기에 있습니다! Aspose.Words for .NET을 사용하여 Word 문서에서 북마크를 표시하고 숨기는 방법을 성공적으로 배웠습니다. 이 기술은 조건부 콘텐츠가 포함된 문서를 동적으로 생성하는 데 매우 유용할 수 있습니다.

## FAQ

### .NET용 Aspose.Words란 무엇입니까?
Aspose.Words for .NET은 개발자가 프로그래밍 방식으로 Word 문서를 생성, 수정 및 변환할 수 있는 강력한 문서 처리 라이브러리입니다.

### .NET용 Aspose.Words를 어떻게 얻나요?
 .NET용 Aspose.Words는 다음에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/). 무료 평가판도 제공됩니다.

### 다른 유형의 북마크에 이 방법을 사용할 수 있나요?
예, 이 방법을 적용하여 Word 문서의 책갈피에 대한 가시성을 관리할 수 있습니다.

### 내 문서에 지정된 책갈피가 포함되어 있지 않으면 어떻게 되나요?
북마크가 존재하지 않으면 메서드에서 오류가 발생합니다. 북마크를 표시하거나 숨기기 전에 북마크가 있는지 확인하세요.

### 문제가 발생하면 어떻게 지원을 받을 수 있나요?
 Aspose 커뮤니티에서 지원을 받을 수 있습니다[여기](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
