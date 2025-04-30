---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에 앵커 주석을 추가하는 방법을 알아보세요. 효율적인 문서 협업을 위한 단계별 가이드를 따라해 보세요."
"linktitle": "앵커 코멘트"
"second_title": "Aspose.Words 문서 처리 API"
"title": "앵커 코멘트"
"url": "/ko/net/working-with-comments/anchor-comment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 앵커 코멘트

## 소개

Word 문서의 특정 텍스트 섹션에 프로그래밍 방식으로 주석을 추가해야 하는 상황을 경험해 보신 적이 있으신가요? 팀원들과 공동으로 문서를 작업하고 있는데, 다른 사람들이 검토할 수 있도록 특정 부분을 주석으로 강조 표시해야 한다고 가정해 보겠습니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에 앵커 주석을 삽입하는 방법을 자세히 살펴보겠습니다. 이 과정을 간단한 단계로 나누어 쉽게 따라 하고 프로젝트에 구현할 수 있도록 도와드리겠습니다.

## 필수 조건

시작하기에 앞서, 필요한 모든 것이 있는지 확인해 보겠습니다.

- Aspose.Words for .NET: Aspose.Words 라이브러리가 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio와 같은 .NET 개발 환경.
- C#에 대한 기본적인 이해: C# 프로그래밍에 익숙하면 단계를 쉽게 따라갈 수 있습니다.

이제 이 작업에 필요한 네임스페이스를 살펴보겠습니다.

## 네임스페이스 가져오기

먼저, 프로젝트에 필요한 네임스페이스를 가져오세요. 필요한 네임스페이스는 다음과 같습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.CommentRangeStart;
using Aspose.Words.CommentRangeEnd;
```

필수 구성 요소와 네임스페이스를 살펴보았으니 이제 재미있는 부분으로 넘어가서 프로세스를 단계별로 살펴보겠습니다.

## 1단계: 새 문서 만들기

먼저, 새 Word 문서를 만들어 보겠습니다. 이 문서는 댓글을 작성할 캔버스 역할을 할 것입니다.

```csharp
// 문서가 저장될 디렉토리를 정의하세요
string dataDir = "YOUR DOCUMENT DIRECTORY";        

// Document 클래스의 인스턴스를 생성합니다
Document doc = new Document();
```

이 단계에서는 새로운 것을 초기화합니다. `Document` 주석을 추가하는 데 사용될 객체입니다.

## 2단계: 문서에 텍스트 추가

다음으로, 문서에 텍스트를 추가하겠습니다. 이 텍스트가 주석의 대상이 될 것입니다.

```csharp
// 첫 번째 문단과 런을 만듭니다.
Paragraph para1 = new Paragraph(doc);
Run run1 = new Run(doc, "Some ");
Run run2 = new Run(doc, "text ");
para1.AppendChild(run1);
para1.AppendChild(run2);
doc.FirstSection.Body.AppendChild(para1);

// 두 번째 문단과 런을 만듭니다.
Paragraph para2 = new Paragraph(doc);
Run run3 = new Run(doc, "is ");
Run run4 = new Run(doc, "added ");
para2.AppendChild(run3);
para2.AppendChild(run4);
doc.FirstSection.Body.AppendChild(para2);
```

여기서는 텍스트가 포함된 두 개의 문단을 만듭니다. 각 텍스트는 `Run` 객체는 문단에 추가됩니다.

## 3단계: 댓글 작성

이제 텍스트에 첨부할 주석을 만들어 보겠습니다.

```csharp
// 새로운 댓글을 만드세요
Comment comment = new Comment(doc, "Awais Hafeez", "AH", DateTime.Today);
comment.SetText("Comment text.");
```

이 단계에서는 다음을 생성합니다. `Comment` 객체를 추가하고 문단과 주석 텍스트를 추가합니다.

## 4단계: 주석 범위 정의

특정 텍스트에 주석을 고정하려면 주석 범위의 시작과 끝을 정의해야 합니다.

```csharp
// CommentRangeStart 및 CommentRangeEnd 정의
CommentRangeStart commentRangeStart = new CommentRangeStart(doc, comment.Id);
CommentRangeEnd commentRangeEnd = new CommentRangeEnd(doc, comment.Id);

// 문서에 CommentRangeStart 및 CommentRangeEnd를 삽입합니다.
run1.ParentNode.InsertAfter(commentRangeStart, run1);
run3.ParentNode.InsertAfter(commentRangeEnd, run3);

// 문서에 주석을 추가합니다
commentRangeEnd.ParentNode.InsertAfter(comment, commentRangeEnd);
```

여기서 우리는 만듭니다 `CommentRangeStart` 그리고 `CommentRangeEnd` 객체를 만들고 ID를 통해 주석과 연결합니다. 그런 다음 이 범위를 문서에 삽입하여 주석을 지정된 텍스트에 효과적으로 고정합니다.

## 5단계: 문서 저장

마지막으로, 문서를 지정된 디렉토리에 저장해 보겠습니다.

```csharp
// 문서를 저장하세요
doc.Save(dataDir + "WorkingWithComments.AnchorComment.doc");
```

이 단계에서는 고정된 주석이 포함된 문서를 지정된 디렉토리에 저장합니다.

## 결론

자, 이제 끝났습니다! Aspose.Words for .NET을 사용하여 Word 문서의 특정 텍스트 섹션에 앵커 주석을 추가하는 방법을 성공적으로 익혔습니다. 이 기술은 문서 협업에 매우 유용하며, 텍스트의 특정 부분을 쉽게 강조 표시하고 주석을 달 수 있습니다. 팀과 함께 프로젝트를 진행하든 문서를 검토하든, 이 방법은 생산성을 향상시키고 워크플로우를 간소화하는 데 도움이 됩니다.

## 자주 묻는 질문

### Word 문서에서 앵커 주석을 사용하는 목적은 무엇입니까?
앵커 주석은 텍스트의 특정 부분을 강조하고 주석을 달 때 사용되며, 이를 통해 피드백을 제공하고 문서에서 협업하기가 더 쉬워집니다.

### 같은 텍스트 섹션에 여러 개의 댓글을 추가할 수 있나요?
네, 여러 개의 댓글 범위를 정의하여 동일한 텍스트 섹션에 여러 개의 댓글을 추가할 수 있습니다.

### Aspose.Words for .NET은 무료로 사용할 수 있나요?
Aspose.Words for .NET은 다운로드할 수 있는 무료 평가판을 제공합니다. [여기](https://releases.aspose.com/). 전체 기능을 사용하려면 라이선스를 구매하세요. [여기](https://purchase.aspose.com/buy).

### 댓글의 모양을 사용자 지정할 수 있나요?
Aspose.Words는 기능에 중점을 두는 반면, Word 문서에서 주석의 모양은 일반적으로 Word 자체에서 제어됩니다.

### Aspose.Words for .NET에 대한 추가 문서는 어디에서 찾을 수 있나요?
자세한 문서를 찾을 수 있습니다 [여기](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}