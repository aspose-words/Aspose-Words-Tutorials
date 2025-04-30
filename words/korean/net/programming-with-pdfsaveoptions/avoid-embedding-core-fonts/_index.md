---
"description": "Aspose.Words for .NET을 사용하여 핵심 글꼴을 포함하지 않고 PDF 파일 크기를 줄이는 방법을 알아보세요. PDF 최적화를 위한 단계별 가이드를 따라해 보세요."
"linktitle": "핵심 글꼴을 포함하지 않아 PDF 파일 크기 줄이기"
"second_title": "Aspose.Words 문서 처리 API"
"title": "핵심 글꼴을 포함하지 않아 PDF 파일 크기 줄이기"
"url": "/ko/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 핵심 글꼴을 포함하지 않아 PDF 파일 크기 줄이기

## 소개

PDF 파일이 왜 이렇게 큰지 궁금해 머리를 긁적여 본 적이 있으신가요? 여러분만 그런 게 아닙니다. 흔한 문제 중 하나는 Arial이나 Times New Roman 같은 핵심 글꼴을 내장하는 것입니다. 다행히 Aspose.Words for .NET에는 이 문제를 해결하는 멋진 방법이 있습니다. 이 튜토리얼에서는 이러한 핵심 글꼴을 내장하지 않고 PDF 파일 크기를 줄이는 방법을 보여드리겠습니다. 바로 시작해 볼까요!

## 필수 조건

이 신나는 여정을 시작하기 전에, 필요한 모든 것을 갖추었는지 확인해 보세요. 간단한 체크리스트를 소개합니다.

- Aspose.Words for .NET: Aspose.Words for .NET이 설치되어 있는지 확인하세요. 아직 설치되어 있지 않다면 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio와 같은 개발 환경이 필요합니다.
- Word 문서: 이 튜토리얼에서는 Word 문서(예: "Rendering.docx")를 사용합니다.
- C# 기본 지식: C#에 대한 기본적인 이해가 있으면 따라가는 데 도움이 됩니다.

좋습니다. 이제 모든 것이 준비되었으니, 본격적으로 시작해 볼까요!

## 네임스페이스 가져오기

먼저, 필요한 네임스페이스를 가져오겠습니다. 이 단계를 통해 필요한 모든 Aspose.Words 기능에 접근할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1단계: 문서 디렉터리 초기화

문서 조작을 시작하기 전에 문서가 저장된 디렉터리를 지정해야 합니다. 이는 파일에 접근하는 데 필수적입니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

바꾸다 `"YOUR DOCUMENT DIRECTORY"` Word 문서가 위치한 실제 경로를 사용합니다.

## 2단계: Word 문서 로드

다음으로, PDF로 변환할 Word 문서를 불러와야 합니다. 이 예시에서는 "Rendering.docx"라는 이름의 문서를 사용합니다.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

이 코드 줄은 문서를 메모리에 로드하여 추가 처리를 준비합니다.

## 3단계: PDF 저장 옵션 구성

이제 마법 같은 순간입니다! 핵심 글꼴이 포함되지 않도록 PDF 저장 옵션을 설정해 보겠습니다. 이 단계는 PDF 파일 크기를 줄이는 데 중요한 단계입니다.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

환경 `UseCoreFonts` 에게 `true` Arial, Times New Roman과 같은 핵심 글꼴이 PDF에 포함되지 않도록 하여 파일 크기를 크게 줄입니다.

## 4단계: 문서를 PDF로 저장

마지막으로, 구성된 저장 옵션을 사용하여 Word 문서를 PDF로 저장합니다. 이 단계에서는 핵심 글꼴을 포함하지 않고 PDF 파일이 생성됩니다.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

자, 이제 PDF 파일이 지정된 디렉터리에 저장되었습니다. 부피가 큰 핵심 글꼴은 제외되었습니다.

## 결론

Aspose.Words for .NET을 사용하면 PDF 파일 크기를 매우 간편하게 줄일 수 있습니다. 핵심 글꼴을 임베드하지 않으므로 파일 크기를 크게 줄여 문서를 공유하고 저장하기가 더 쉬워집니다. 이 튜토리얼이 도움이 되고 작업 과정을 명확하게 이해하는 데 도움이 되었기를 바랍니다. 작은 변화도 큰 차이를 만들 수 있다는 것을 기억하세요!

## 자주 묻는 질문

### PDF에 핵심 글꼴을 포함하지 않아야 하는 이유는 무엇입니까?
핵심 글꼴을 포함하지 않으면 파일 크기가 줄어들어 공유 및 저장이 쉬워집니다.

### 내장된 핵심 글꼴 없이도 PDF를 제대로 볼 수 있나요?
네, Arial, Times New Roman과 같은 핵심 글꼴은 일반적으로 대부분의 시스템에서 사용할 수 있습니다.

### 사용자 정의 글꼴을 포함해야 하는 경우는 어떻게 되나요?
사용자 정의할 수 있습니다 `PdfSaveOptions` 필요에 따라 특정 글꼴을 포함합니다.

### Aspose.Words for .NET은 무료로 사용할 수 있나요?
Aspose.Words for .NET에는 라이선스가 필요합니다. 무료 평가판을 사용해 보세요. [여기](https://releases.aspose.com/).

### Aspose.Words for .NET에 대한 추가 문서는 어디에서 찾을 수 있나요?
자세한 문서를 찾을 수 있습니다 [여기](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}