---
title: 마지막으로 저장된 시간 속성 업데이트
linktitle: 마지막으로 저장된 시간 속성 업데이트
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에서 마지막으로 저장된 시간 속성을 업데이트하는 방법을 알아보세요. 자세한 단계별 가이드를 따르세요.
weight: 10
url: /ko/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 마지막으로 저장된 시간 속성 업데이트

## 소개

Word 문서에서 마지막으로 저장된 시간 속성을 프로그래밍 방식으로 추적하는 방법에 대해 궁금해 본 적이 있습니까? 여러 문서를 다루고 해당 메타데이터를 유지 관리해야 하는 경우 마지막으로 저장된 시간 속성을 업데이트하는 것이 매우 편리할 수 있습니다. 오늘은 Aspose.Words for .NET을 사용하여 이 프로세스를 안내해 드리겠습니다. 안전띠를 매고 시작해 볼까요!

## 필수 조건

단계별 가이드를 살펴보기 전에 몇 가지 필요한 사항이 있습니다.

1.  Aspose.Words for .NET: Aspose.Words for .NET이 설치되어 있는지 확인하세요. 설치되어 있지 않으면 다음을 수행할 수 있습니다.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 개발 환경.
3. C#에 대한 기본 지식: C# 프로그래밍의 기본을 이해하는 것이 도움이 됩니다.

## 네임스페이스 가져오기

우선, 프로젝트에 필요한 네임스페이스를 가져오세요. 그러면 Word 문서를 조작하는 데 필요한 클래스와 메서드에 액세스할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

이제 프로세스를 간단한 단계로 나누어 보겠습니다. 각 단계는 Word 문서에서 마지막으로 저장된 시간 속성을 업데이트하는 프로세스를 안내합니다.

## 1단계: 문서 디렉토리 설정

먼저, 문서 디렉토리 경로를 지정해야 합니다. 이는 기존 문서가 저장되는 곳이고 업데이트된 문서가 저장되는 곳입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 디렉토리의 실제 경로를 포함합니다.

## 2단계: Word 문서 로드

 다음으로 업데이트하려는 Word 문서를 로드합니다. 인스턴스를 만들어서 이를 수행할 수 있습니다.`Document` 클래스와 문서 경로를 전달합니다.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

 문서 이름이 다음과 같은지 확인하세요.`Document.docx` 지정된 디렉토리에 있습니다.

## 3단계: 저장 옵션 구성

 이제 인스턴스를 생성하세요.`OoxmlSaveOptions` 클래스. 이 클래스를 사용하면 Office Open XML(OOXML) 형식으로 문서를 저장하기 위한 옵션을 지정할 수 있습니다. 여기에서 다음을 설정합니다.`UpdateLastSavedTimeProperty` 에게`true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

이렇게 하면 Aspose.Words가 문서의 마지막 저장 시간 속성을 업데이트하게 됩니다.

## 4단계: 업데이트된 문서 저장

 마지막으로 다음을 사용하여 문서를 저장합니다.`Save` 의 방법`Document` 클래스에서 업데이트된 문서를 저장할 경로와 저장 옵션을 전달합니다.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

이렇게 하면 업데이트된 마지막 저장 시간 속성으로 문서가 저장됩니다.

## 결론

이제 다 됐습니다! 다음 단계를 따르면 Aspose.Words for .NET을 사용하여 Word 문서의 마지막 저장 시간 속성을 쉽게 업데이트할 수 있습니다. 이는 문서의 정확한 메타데이터를 유지하는 데 특히 유용하며, 이는 문서 관리 시스템 및 기타 다양한 애플리케이션에 매우 중요할 수 있습니다.

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?
Aspose.Words for .NET은 .NET 애플리케이션에서 Word 문서를 만들고, 편집하고, 변환하기 위한 강력한 라이브러리입니다.

### 마지막으로 저장된 시간 속성을 업데이트해야 하는 이유는 무엇입니까?
마지막으로 저장된 시간 속성을 업데이트하면 문서 추적 및 관리에 필수적인 정확한 메타데이터를 유지하는 데 도움이 됩니다.

### Aspose.Words for .NET을 사용하여 다른 속성을 업데이트할 수 있나요?
네, Aspose.Words for .NET을 사용하면 제목, 작성자, 주제 등 다양한 문서 속성을 업데이트할 수 있습니다.

### Aspose.Words for .NET은 무료인가요?
 Aspose.Words for .NET은 무료 평가판을 제공하지만 모든 기능을 사용하려면 라이선스가 필요합니다. 라이선스를 얻을 수 있습니다.[여기](https://purchase.aspose.com/buy).

### Aspose.Words for .NET에 대한 추가 튜토리얼은 어디에서 찾을 수 있나요?
더 많은 튜토리얼과 문서를 찾을 수 있습니다[여기](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
