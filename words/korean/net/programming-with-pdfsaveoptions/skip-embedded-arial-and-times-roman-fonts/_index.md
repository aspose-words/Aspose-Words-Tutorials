---
"description": "Aspose.Words for .NET을 사용하여 내장된 Arial 및 Times Roman 글꼴을 건너뛰어 PDF 크기를 최적화하세요. 이 단계별 가이드를 따라 PDF 파일을 간소화하세요."
"linktitle": "내장된 Arial 및 Times Roman 글꼴 건너뛰기로 PDF 크기 최적화"
"second_title": "Aspose.Words 문서 처리 API"
"title": "내장된 Arial 및 Times Roman 글꼴 건너뛰기로 PDF 크기 최적화"
"url": "/ko/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 내장된 Arial 및 Times Roman 글꼴 건너뛰기로 PDF 크기 최적화

## 소개

PDF 파일 크기가 너무 큰 상황에 처해 본 적이 있나요? 휴가를 가려고 짐을 싸다가 가방이 터질 것 같은 상황과 같습니다. 무게를 줄여야 한다는 건 알지만, 무엇을 포기해야 할까요? PDF 파일, 특히 Word 문서에서 변환한 파일을 작업할 때, 내장된 글꼴 때문에 파일 크기가 커질 수 있습니다. 다행히 Aspose.Words for .NET은 PDF 파일을 간결하고 효율적으로 관리할 수 있는 간편한 솔루션을 제공합니다. 이 튜토리얼에서는 내장된 Arial 및 Times Roman 글꼴을 사용하지 않고 PDF 크기를 최적화하는 방법을 자세히 알아보겠습니다. 시작해 볼까요?

## 필수 조건

자세한 내용을 알아보기 전에 먼저 몇 가지 필요한 것이 있습니다.
- Aspose.Words for .NET: 이 강력한 라이브러리가 설치되어 있는지 확인하세요. 설치되어 있지 않으면 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
- C#에 대한 기본적인 이해: 이는 코드 조각을 따라가는 데 도움이 됩니다.
- Word 문서: 샘플 문서를 사용하여 프로세스를 보여드리겠습니다. 

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 가져왔는지 확인하세요. 이렇게 하면 Aspose.Words 기능에 접근할 수 있는 환경이 마련됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

좋습니다. 과정을 단계별로 나누어 보겠습니다.

## 1단계: 환경 설정

시작하려면 개발 환경을 설정해야 합니다. 선호하는 C# IDE(예: Visual Studio)를 열고 새 프로젝트를 만드세요.

## 2단계: Word 문서 로드

다음 단계는 PDF로 변환할 Word 문서를 불러오는 것입니다. 문서가 올바른 디렉터리에 있는지 확인하세요.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

이 스니펫에서 다음을 교체하세요. `"YOUR DOCUMENT DIRECTORY"` 문서 디렉토리 경로를 포함합니다.

## 3단계: PDF 저장 옵션 구성

이제 PDF 저장 옵션을 설정하여 글꼴이 포함되는 방식을 제어해야 합니다. 기본적으로 모든 글꼴이 포함되어 있어 파일 크기가 커질 수 있습니다. 이 설정을 변경해 보겠습니다.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## 4단계: 문서를 PDF로 저장

마지막으로, 지정된 저장 옵션을 사용하여 문서를 PDF로 저장합니다. 바로 여기서 마법이 일어납니다.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

이 명령은 지정된 디렉토리에 "OptimizedPDF.pdf"라는 PDF 파일로 문서를 저장합니다.

## 결론

자, 이제 끝났습니다! Aspose.Words for .NET을 사용하여 Arial 및 Times Roman 글꼴을 임베딩하지 않고 PDF 파일 크기를 최적화하는 방법을 방금 배웠습니다. 이 간단한 변경으로 파일 크기를 크게 줄여 공유 및 저장을 더욱 쉽게 할 수 있습니다. 마치 헬스장에 가서 PDF 파일의 필수 요소는 그대로 유지하면서 불필요한 무게를 줄이는 것과 같습니다.

## 자주 묻는 질문

### 왜 Arial과 Times Roman 글꼴을 삽입하지 않아야 합니까?
대부분의 시스템에는 이미 이러한 글꼴이 설치되어 있으므로, 이러한 일반적인 글꼴을 건너뛰면 PDF 파일 크기를 줄일 수 있습니다.

### 이것이 내 PDF의 모양에 영향을 미칠까요?
아니요, 그렇지 않습니다. Arial과 Times Roman은 표준 글꼴이므로 다른 시스템에서도 모양이 일관되게 유지됩니다.

### 다른 글꼴도 삽입하지 않을 수 있나요?
네, 필요한 경우 다른 글꼴을 포함하지 않도록 저장 옵션을 구성할 수 있습니다.

### Aspose.Words for .NET은 무료인가요?
Aspose.Words for .NET은 다운로드할 수 있는 무료 평가판을 제공합니다. [여기](https://releases.aspose.com/)하지만 전체 액세스를 위해서는 라이센스를 구매해야 합니다. [여기](https://purchase.aspose.com/buy).

### Aspose.Words for .NET에 대한 더 많은 튜토리얼은 어디에서 찾을 수 있나요?
포괄적인 문서와 튜토리얼을 찾을 수 있습니다. [여기](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}