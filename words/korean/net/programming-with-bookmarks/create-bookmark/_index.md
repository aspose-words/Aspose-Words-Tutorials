---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에 북마크를 만드는 방법을 단계별로 자세히 알아보세요. 문서 탐색 및 정리에 매우 유용합니다."
"linktitle": "Word 문서에 북마크 만들기"
"second_title": "Aspose.Words 문서 처리 API"
"title": "Word 문서에 북마크 만들기"
"url": "/ko/net/programming-with-bookmarks/create-bookmark/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에 북마크 만들기

## 소개

Word 문서에 북마크를 만드는 것은, 특히 큰 문서를 손쉽게 탐색하고 싶을 때 매우 유용합니다. 오늘은 Aspose.Words for .NET을 사용하여 북마크를 만드는 과정을 살펴보겠습니다. 이 튜토리얼에서는 단계별로 안내하여 과정의 각 단계를 이해할 수 있도록 도와드립니다. 자, 바로 시작해 볼까요!

## 필수 조건

시작하기에 앞서 다음 사항이 필요합니다.

1. Aspose.Words for .NET 라이브러리: 다운로드 및 설치 [여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET 개발 환경.
3. C#에 대한 기본 지식: 기본 C# 프로그래밍 개념에 대한 이해.

## 네임스페이스 가져오기

Aspose.Words for .NET을 사용하려면 필요한 네임스페이스를 가져와야 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1단계: 문서 및 DocumentBuilder 설정

문서 초기화

먼저 새 문서를 만들고 초기화해야 합니다. `DocumentBuilder`이는 문서에 콘텐츠와 책갈피를 추가하는 시작점입니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

설명: `Document` 객체는 캔버스입니다. `DocumentBuilder` 문서에 내용을 쓰고 책갈피를 만들 수 있는 펜과 같습니다.

## 2단계: 기본 북마크 만들기

메인 북마크 시작 및 종료

북마크를 만들려면 시작점과 끝점을 지정해야 합니다. 여기서는 "내 북마크"라는 이름의 북마크를 만들어 보겠습니다.

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

설명: `StartBookmark` 방법은 북마크의 시작을 표시하고 `Writeln` 북마크에 텍스트를 추가합니다.

## 3단계: 중첩된 북마크 만들기

메인 북마크 안에 중첩 북마크 추가

다른 북마크 안에 북마크를 중첩할 수 있습니다. 여기서는 "내 북마크" 안에 "중첩 북마크"를 추가합니다.

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

설명: 북마크를 중첩하면 콘텐츠를 더욱 체계적이고 계층적으로 구성할 수 있습니다. `EndBookmark` 이 메서드는 현재 북마크를 닫습니다.

## 4단계: 중첩된 책갈피 외부에 텍스트 추가

콘텐츠 추가 계속

중첩된 북마크 다음에, 기본 북마크 안에 더 많은 콘텐츠를 추가할 수 있습니다.

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

설명: 이렇게 하면 기본 책갈피가 중첩된 책갈피와 추가 텍스트를 모두 포함하게 됩니다.

## 5단계: PDF 저장 옵션 구성

북마크에 대한 PDF 저장 옵션 설정

문서를 PDF로 저장할 때 책갈피를 포함하도록 옵션을 구성할 수 있습니다.

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

설명: `PdfSaveOptions` 클래스를 사용하면 문서를 PDF로 저장하는 방법을 지정할 수 있습니다. `BookmarksOutlineLevels` 속성은 PDF의 북마크 계층 구조를 정의합니다.

## 6단계: 문서 저장

문서를 PDF로 저장

마지막으로, 지정된 옵션으로 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

설명: `Save` 이 메서드는 지정된 형식과 위치에 문서를 저장합니다. 이제 PDF에 생성된 북마크가 포함됩니다.

## 결론

Aspose.Words for .NET을 사용하여 Word 문서에 북마크를 만드는 것은 간단하고 문서 탐색 및 정리에 매우 유용합니다. 보고서 작성, 전자책 제작, 대용량 문서 관리 등 어떤 작업을 하든 북마크를 사용하면 작업이 훨씬 수월해집니다. 이 튜토리얼에 설명된 단계를 따라 하면 북마크가 적용된 PDF 파일을 바로 만들 수 있습니다.

## 자주 묻는 질문

### 여러 개의 북마크를 다른 레벨로 만들 수 있나요?

물론입니다! 필요한 만큼 북마크를 만들고, 문서를 PDF로 저장할 때 북마크의 계층 구조를 정의할 수 있습니다.

### 북마크의 텍스트를 어떻게 업데이트하나요?

북마크로 이동하려면 다음을 사용할 수 있습니다. `DocumentBuilder.MoveToBookmark` 그리고 텍스트를 업데이트합니다.

### 북마크를 삭제할 수 있나요?

네, 북마크를 삭제할 수 있습니다. `Bookmarks.Remove` 북마크의 이름을 지정하여 방법을 지정합니다.

### PDF 외에 다른 형식으로 북마크를 만들 수 있나요?

네, Aspose.Words는 DOCX, HTML, EPUB 등 다양한 형식의 북마크를 지원합니다.

### PDF에 책갈피가 올바르게 표시되도록 하려면 어떻게 해야 하나요?

정의를 꼭 하세요 `BookmarksOutlineLevels` 제대로 `PdfSaveOptions`이렇게 하면 책갈피가 PDF 개요에 포함됩니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}