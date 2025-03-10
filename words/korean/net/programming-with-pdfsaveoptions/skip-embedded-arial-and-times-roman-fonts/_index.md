---
title: Skip Embedded Arial & Times Roman 글꼴로 PDF 크기 최적화
linktitle: Skip Embedded Arial & Times Roman 글꼴로 PDF 크기 최적화
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 내장된 Arial 및 Times Roman 글꼴을 건너뛰어 PDF 크기를 최적화합니다. 이 단계별 가이드를 따라 PDF 파일을 간소화합니다.
weight: 10
url: /ko/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skip Embedded Arial & Times Roman 글꼴로 PDF 크기 최적화

## 소개

PDF 파일 크기가 너무 큰 상황에 처한 적이 있나요? 휴가를 위해 짐을 싸다가 가방이 터질 것 같다는 것을 깨달은 것과 같습니다. 무게를 줄여야 한다는 것은 알지만, 무엇을 버릴까요? PDF 파일, 특히 Word 문서에서 변환한 파일을 작업할 때, 내장된 글꼴이 파일 크기를 부풀릴 수 있습니다. 다행히도 Aspose.Words for .NET은 PDF를 간소하고 의미 있게 유지할 수 있는 세련된 솔루션을 제공합니다. 이 튜토리얼에서는 내장된 Arial 및 Times Roman 글꼴을 건너뛰어 PDF 크기를 최적화하는 방법을 알아보겠습니다. 시작해 볼까요!

## 필수 조건

본격적으로 들어가기 전에 필요한 몇 가지가 있습니다.
-  Aspose.Words for .NET: 이 강력한 라이브러리가 설치되어 있는지 확인하세요. 설치되어 있지 않으면 다음에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
- C#에 대한 기본적인 이해: 이는 코드 조각을 따라가는 데 도움이 됩니다.
- Word 문서: 샘플 문서를 사용하여 과정을 설명하겠습니다. 

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 가져왔는지 확인하세요. 이렇게 하면 Aspose.Words 기능에 액세스할 수 있는 단계가 설정됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

좋습니다. 이제 과정을 단계별로 나누어 보겠습니다.

## 1단계: 환경 설정

시작하려면 개발 환경을 설정해야 합니다. 좋아하는 C# IDE(Visual Studio 등)를 열고 새 프로젝트를 만듭니다.

## 2단계: Word 문서 로드

다음 단계는 PDF로 변환하려는 Word 문서를 로드하는 것입니다. 문서가 올바른 디렉토리에 있는지 확인하세요.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 이 스니펫에서 다음을 교체합니다.`"YOUR DOCUMENT DIRECTORY"` 문서 디렉토리 경로를 포함합니다.

## 3단계: PDF 저장 옵션 구성

이제 PDF 저장 옵션을 구성하여 글꼴이 어떻게 포함되는지 제어해야 합니다. 기본적으로 모든 글꼴이 포함되므로 파일 크기가 커질 수 있습니다. 이 설정을 변경하겠습니다.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## 4단계: 문서를 PDF로 저장

마지막으로, 지정된 저장 옵션으로 문서를 PDF로 저장합니다. 여기서 마법이 일어납니다.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

이 명령은 지정된 디렉토리에 "OptimizedPDF.pdf"라는 이름의 PDF로 문서를 저장합니다.

## 결론

이제 아시죠! 방금 Aspose.Words for .NET을 사용하여 Arial 및 Times Roman 글꼴을 임베딩하지 않고 PDF 파일 크기를 최적화하는 방법을 배웠습니다. 이 간단한 조정으로 파일 크기를 크게 줄여 공유하고 저장하기가 더 쉬워집니다. PDF를 위해 헬스장에 가는 것과 마찬가지로 불필요한 무게를 줄이면서도 모든 필수 요소는 그대로 유지합니다.

## 자주 묻는 질문

### 왜 Arial과 Times Roman 글꼴을 포함하지 않아야 합니까?
대부분의 시스템에는 이미 이러한 글꼴이 설치되어 있으므로, 이러한 일반적인 글꼴을 건너뛰면 PDF 파일 크기를 줄일 수 있습니다.

### 이것이 내 PDF 모양에 영향을 미칠까요?
아니요, 그렇지 않습니다. Arial과 Times Roman은 표준 글꼴이므로 모양은 다른 시스템에서도 일관되게 유지됩니다.

### 다른 글꼴을 포함하는 것도 건너뛸 수 있나요?
네, 필요한 경우 다른 글꼴을 포함하지 않도록 저장 옵션을 구성할 수 있습니다.

### Aspose.Words for .NET은 무료인가요?
 Aspose.Words for .NET은 다운로드할 수 있는 무료 평가판을 제공합니다.[여기](https://releases.aspose.com/) , 하지만 전체 액세스를 위해서는 라이센스를 구매해야 합니다.[여기](https://purchase.aspose.com/buy).

### Aspose.Words for .NET에 대한 추가 튜토리얼은 어디에서 찾을 수 있나요?
포괄적인 문서와 튜토리얼을 찾을 수 있습니다.[여기](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
