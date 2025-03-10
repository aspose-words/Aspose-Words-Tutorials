---
title: 문서 삽입 위치 바꾸기
linktitle: 문서 삽입 위치 바꾸기
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 한 Word 문서를 다른 문서에 매끄럽게 삽입하는 방법을 자세한 단계별 가이드로 알아보세요. 문서 처리를 간소화하려는 개발자에게 완벽합니다.
weight: 10
url: /ko/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 문서 삽입 위치 바꾸기

## 소개

안녕하세요, 문서의 거장 여러분! 코드에 깊이 빠져서 한 Word 문서를 다른 문서에 매끄럽게 삽입하는 방법을 알아내려고 했던 적이 있나요? 걱정하지 마세요. 오늘은 Aspose.Words for .NET의 세계로 뛰어들어 그 작업을 쉽게 만들어드립니다. 찾기 및 바꾸기 작업 중에 특정 지점에 문서를 삽입하는 데 이 강력한 라이브러리를 사용하는 방법에 대한 자세한 단계별 가이드를 살펴보겠습니다. Aspose.Words 마법사가 될 준비가 되셨나요? 시작해 볼까요!

## 필수 조건

코드로 넘어가기 전에 꼭 준비해야 할 몇 가지 사항이 있습니다.

-  Visual Studio: 컴퓨터에 Visual Studio가 설치되어 있는지 확인하세요. 아직 설치되어 있지 않으면 다음에서 다운로드할 수 있습니다.[여기](https://visualstudio.microsoft.com/).
-  .NET용 Aspose.Words: Aspose.Words 라이브러리가 필요합니다. 다음에서 얻을 수 있습니다.[Aspose 웹사이트](https://releases.aspose.com/words/net/).
- 기본 C# 지식: C#과 .NET에 대한 기본적인 이해가 있으면 이 튜토리얼을 따라가는 데 도움이 됩니다.

좋습니다. 이제 코드를 직접 작성해 볼까요!

## 네임스페이스 가져오기

우선 Aspose.Words에서 작업하는 데 필요한 네임스페이스를 가져와야 합니다. 이는 프로젝트를 시작하기 전에 모든 도구를 모으는 것과 같습니다. C# 파일의 맨 위에 다음 using 지시문을 추가합니다.

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

이제 전제 조건이 마련되었으니, 프로세스를 한 입 크기의 단계로 나누어 보겠습니다. 각 단계는 중요하며 목표에 더 가까이 다가갈 수 있게 해줍니다.

## 1단계: 문서 디렉토리 설정

먼저, 우리는 문서가 저장되는 디렉토리를 지정해야 합니다. 이것은 큰 공연 전에 무대를 준비하는 것과 같습니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 디렉토리로 가는 경로입니다. 여기가 문서가 살아 숨쉬는 곳입니다.

## 2단계: 주요 문서 로드

다음으로, 다른 문서를 삽입하려는 주 문서를 로드합니다. 이것을 모든 작업이 발생하는 주 스테이지로 생각하세요.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

이 코드는 지정된 디렉토리에서 주요 문서를 로드합니다.

## 3단계: 찾기 및 바꾸기 옵션 설정

문서를 삽입하려는 특정 위치를 찾으려면 찾기 및 바꾸기 기능을 사용합니다. 이는 지도를 사용하여 새 추가 항목의 정확한 위치를 찾는 것과 같습니다.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

여기서는 방향을 뒤로 설정하고 다음에 정의할 사용자 정의 콜백 핸들러를 지정합니다.

## 4단계: 바꾸기 작업 수행

이제 우리는 기본 문서에 특정 자리 표시자 텍스트를 찾아 아무것도 없는 것으로 바꾸도록 지시하고, 사용자 정의 콜백을 사용하여 다른 문서를 삽입합니다.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

이 코드는 찾아서 바꾸기 작업을 수행한 후 업데이트된 문서를 저장합니다.

## 5단계: 사용자 정의 대체 콜백 핸들러 만들기

마법이 일어나는 곳은 바로 저희의 커스텀 콜백 핸들러입니다. 이 핸들러는 찾기 및 바꾸기 작업 중에 문서 삽입이 어떻게 수행되는지 정의합니다.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // 일치 텍스트가 포함된 문단 뒤에 문서를 삽입합니다.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // 일치하는 텍스트가 있는 문단을 제거하세요.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

여기서는 삽입할 문서를 로드한 다음 삽입을 수행하기 위한 도우미 메서드를 호출합니다.

## 6단계: 문서 삽입 방법 정의

퍼즐의 마지막 조각은 지정된 위치에 문서를 실제로 삽입하는 방법입니다.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // 삽입 대상이 문단인지 표인지 확인하세요
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // 소스 문서에서 노드를 가져오기 위해 NodeImporter를 만듭니다.
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // 소스 문서 섹션의 모든 블록 수준 노드를 반복합니다.
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // 섹션의 마지막 빈 문단을 건너뜁니다.
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // 노드를 가져와서 대상에 삽입합니다.
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

이 방법은 삽입할 문서에서 노드를 가져와서 기본 문서의 올바른 위치에 배치하는 작업을 담당합니다.

## 결론

이제 다 봤습니다! Aspose.Words for .NET을 사용하여 한 문서를 다른 문서에 삽입하는 포괄적인 가이드입니다. 이러한 단계를 따르면 문서 조립 및 조작 작업을 쉽게 자동화할 수 있습니다. 문서 관리 시스템을 구축하든 문서 처리 워크플로를 간소화해야 하든 Aspose.Words는 믿음직한 조력자입니다.

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?
Aspose.Words for .NET은 Word 문서를 프로그래밍 방식으로 조작하기 위한 강력한 라이브러리입니다. Word 문서를 쉽게 만들고, 수정하고, 변환하고, 처리할 수 있습니다.

### 한 번에 여러 문서를 삽입할 수 있나요?
네, 문서 컬렉션을 반복하여 여러 삽입을 처리하도록 콜백 핸들러를 수정할 수 있습니다.

### 무료 체험판이 있나요?
 물론입니다! 무료 체험판을 다운로드할 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Words에 대한 지원을 받으려면 어떻게 해야 하나요?
 방문하면 지원을 받을 수 있습니다.[Aspose.Words 포럼](https://forum.aspose.com/c/words/8).

### 삽입한 문서의 서식을 유지할 수 있나요?
 네,`NodeImporter` 클래스를 사용하면 한 문서에서 다른 문서로 노드를 가져올 때 서식을 처리하는 방법을 지정할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
