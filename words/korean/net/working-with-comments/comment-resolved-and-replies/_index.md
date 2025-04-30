---
"description": "Aspose.Words for .NET을 사용하여 Word 문서의 댓글을 자동으로 해결하고 답장하세요. 단계별 가이드가 포함되어 있습니다."
"linktitle": "댓글이 해결되고 답변이 달렸습니다."
"second_title": "Aspose.Words 문서 처리 API"
"title": "댓글이 해결되고 답변이 달렸습니다."
"url": "/ko/net/working-with-comments/comment-resolved-and-replies/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 댓글이 해결되고 답변이 달렸습니다.

## 소개

Word 문서 작업을 하신다면 댓글을 다뤄보셨을 겁니다. 댓글은 협업에 유용하지만, 관리가 번거로울 수 있습니다. Aspose.Words for .NET을 사용하면 댓글을 확인하고 답글을 달 수 있는 프로세스를 자동화할 수 있습니다. 이 가이드에서는 그 방법을 단계별로 안내해 드립니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1. Aspose.Words for .NET: 여기에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
2. 개발 환경: .NET Framework로 설정합니다.
3. C#에 대한 기본 지식: 구문과 개념에 대한 지식이 필요합니다.

## 네임스페이스 가져오기

먼저, 필요한 네임스페이스를 가져오겠습니다. 이렇게 하면 필요한 모든 클래스와 메서드를 쉽게 사용할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

이 과정을 간단하고 따라 하기 쉬운 단계로 나누어 보겠습니다. 각 단계를 통해 코드와 기능을 이해하는 데 도움이 될 것입니다.

## 1단계: 문서 로드

시작하려면 메모가 포함된 Word 문서를 로드하세요. `Document` 이에 대한 수업입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

이 코드 줄은 새로운 것을 초기화합니다. `Document` Word 문서의 경로가 있는 개체입니다.

## 2단계: 댓글 검색

다음으로, 문서의 모든 주석을 가져와야 합니다. `GetChildNodes` 컬렉션을 검색하는 방법 `Comment` 노드.

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

이 코드는 문서의 모든 주석을 검색하여 저장합니다. `NodeCollection`.

## 3단계: 부모 의견에 접근

이 예시에서는 컬렉션의 첫 번째 댓글에 초점을 맞춰 보겠습니다. 이 댓글이 부모 댓글이 됩니다.

```csharp
Comment parentComment = (Comment)comments[0];
```

여기서 우리는 컬렉션의 첫 번째 노드를 캐스팅하고 있습니다. `Comment` 물체.

## 4단계: 회신 반복

이제 부모 댓글에 대한 답글을 반복해 보겠습니다. `foreach` 각 답변을 반복하기 위한 루프입니다.

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

이 루프에서는 상위 댓글의 ID와 상태(완료 여부)를 출력합니다. 그런 다음 각 댓글을 완료로 표시합니다.

## 5단계: 문서 저장

마지막으로 수정된 문서를 디렉토리에 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

이 코드는 새 문서에 변경 사항을 저장하여 원본 파일은 손상되지 않도록 합니다.

## 결론

Word 문서의 메모를 처리하는 것이 더 이상 번거로울 필요는 없습니다. Aspose.Words for .NET을 사용하면 이 과정을 자동화하여 시간을 절약하고 오류를 줄일 수 있습니다. 이 가이드를 따라 문서의 메모를 효율적으로 처리하고 답장하세요.

## 자주 묻는 질문

### Aspose.Words for .NET을 사용하여 다른 주석 관련 작업을 자동화할 수 있나요?  
네, 댓글 추가, 삭제, 수정 등 다양한 작업을 자동화할 수 있습니다.

### Aspose.Words for .NET은 .NET Core와 호환됩니까?  
네, Aspose.Words for .NET은 .NET Framework와 .NET Core를 모두 지원합니다.

### Aspose.Words for .NET의 무료 평가판을 받으려면 어떻게 해야 하나요?  
무료 평가판을 다운로드할 수 있습니다. [여기](https://releases.aspose.com/).

### Aspose.Words for .NET을 사용하여 다른 문서 유형으로 작업할 수 있나요?  
네, Aspose.Words는 DOCX, PDF, HTML 등 다양한 형식을 지원합니다.

### Aspose.Words for .NET에 대한 자세한 문서는 어디에서 찾을 수 있나요?  
문서에 접근할 수 있습니다 [여기](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}