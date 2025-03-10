---
title: Word 문서에서 북마크된 콘텐츠 표시 및 숨기기
linktitle: Word 문서에서 북마크된 콘텐츠 표시 및 숨기기
second_title: Aspose.Words 문서 처리 API
description: 이 자세하고 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 북마크된 콘텐츠를 표시하거나 숨기는 방법을 알아보세요.
weight: 10
url: /ko/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 북마크된 콘텐츠 표시 및 숨기기

## 소개

Aspose.Words for .NET으로 문서 조작의 세계로 뛰어들 준비가 되셨나요? 문서 작업을 자동화하려는 개발자이든 Word 파일을 프로그래밍 방식으로 처리하는 데 관심이 있는 사람이든, 여러분은 올바른 곳에 있습니다. 오늘은 Aspose.Words for .NET을 사용하여 Word 문서에서 북마크된 콘텐츠를 표시하고 숨기는 방법을 살펴보겠습니다. 이 단계별 가이드를 통해 북마크를 기반으로 콘텐츠 가시성을 제어하는 전문가가 될 수 있습니다. 시작해 볼까요!

## 필수 조건

본격적으로 들어가기 전에 필요한 몇 가지가 있습니다.

1. Visual Studio: .NET과 호환되는 모든 버전.
2.  Aspose.Words for .NET: 다운로드[여기](https://releases.aspose.com/words/net/).
3. C#에 대한 기본적인 이해: 간단한 "Hello World" 프로그램을 작성할 수 있다면 괜찮습니다.
4. 북마크가 포함된 Word 문서: 이 튜토리얼에서는 북마크가 포함된 샘플 문서를 사용합니다.

## 네임스페이스 가져오기

우선, 필요한 네임스페이스를 임포트해 보겠습니다. 이렇게 하면 작업에 필요한 모든 도구가 갖춰집니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

이러한 네임스페이스가 준비되면 이제 여정을 시작할 준비가 되었습니다.

## 1단계: 프로젝트 설정

좋습니다. Visual Studio에서 프로젝트를 설정하여 시작해 보겠습니다.

### 새 프로젝트 만들기

Visual Studio를 열고 새 콘솔 앱(.NET Core) 프로젝트를 만듭니다. "BookmarkVisibilityManager"와 같이 눈길을 끄는 이름을 지정합니다.

### .NET용 Aspose.Words 추가

프로젝트에 Aspose.Words for .NET을 추가해야 합니다. NuGet Package Manager를 통해 이를 수행할 수 있습니다.

1. 도구 > NuGet 패키지 관리자 > 솔루션용 NuGet 패키지 관리로 이동합니다.
2. "Aspose.Words"를 검색하세요.
3. 패키지를 설치합니다.

좋습니다! 이제 프로젝트가 설정되었으니, 문서 로딩으로 넘어가겠습니다.

## 2단계: 문서 로딩

북마크가 포함된 Word 문서를 로드해야 합니다. 이 튜토리얼에서는 "Bookmarks.docx"라는 샘플 문서를 사용합니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 이 코드 조각은 문서 디렉토리 경로를 설정하고 문서를 로드합니다.`doc` 물체.

## 3단계: 북마크된 콘텐츠 표시/숨기기

이제 재미있는 부분이 시작됩니다. 북마크에 따라 콘텐츠를 표시하거나 숨기는 것입니다. 우리는 다음과 같은 메서드를 만들 것입니다.`ShowHideBookmarkedContent` 이 문제를 처리합니다.

북마크된 콘텐츠의 표시 여부를 전환하는 방법은 다음과 같습니다.

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### 방법의 분석

-  북마크 검색:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` 북마크를 가져옵니다.
- 노드 탐색: 북마크 내의 노드를 탐색합니다.
-  가시성 토글: 노드가`Run` (연속된 텍스트 실행)을 설정합니다.`Hidden` 재산.

## 4단계: 방법 적용

이제 방법을 적용해 북마크를 기준으로 콘텐츠를 표시하거나 숨겨 보겠습니다.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

이 코드 줄은 "MyBookmark1"이라는 북마크 내의 내용을 숨깁니다.

## 5단계: 문서 저장

마지막으로 수정된 문서를 저장해 보겠습니다.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

이렇게 하면 변경한 내용이 포함된 문서가 저장됩니다.

## 결론

이제 다 봤습니다! 방금 Aspose.Words for .NET을 사용하여 Word 문서에서 북마크된 콘텐츠를 표시하고 숨기는 방법을 배웠습니다. 이 강력한 도구는 보고서를 자동화하든, 템플릿을 만들든, Word 파일을 만지작거리든 문서 조작을 아주 쉽게 해줍니다. 즐거운 코딩 되세요!

## 자주 묻는 질문

### 여러 개의 북마크를 동시에 전환할 수 있나요?
 네, 전화할 수 있습니다.`ShowHideBookmarkedContent` 전환하려는 각 북마크에 대한 방법입니다.

### 콘텐츠를 숨기면 문서의 구조에 영향을 미칩니까?
아니요, 콘텐츠를 숨기면 가시성에만 영향을 미칩니다. 콘텐츠는 문서에 그대로 남아 있습니다.

### 이 방법을 다른 유형의 콘텐츠에도 사용할 수 있나요?
이 방법은 특히 텍스트 런을 토글합니다. 다른 콘텐츠 유형의 경우 노드 순회 논리를 수정해야 합니다.

### Aspose.Words for .NET은 무료인가요?
 Aspose.Words는 무료 체험판을 제공합니다[여기](https://releases.aspose.com/) , 하지만 프로덕션 사용에는 전체 라이센스가 필요합니다. 구매할 수 있습니다.[여기](https://purchase.aspose.com/buy).

### 문제가 발생하면 어떻게 지원을 받을 수 있나요?
 Aspose 커뮤니티에서 지원을 받을 수 있습니다.[여기](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
