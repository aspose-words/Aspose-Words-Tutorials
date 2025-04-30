---
"description": "Aspose.Words for .NET을 사용하여 내장 글꼴을 비활성화하여 PDF 크기를 줄이세요. 효율적인 저장 및 공유를 위해 문서를 최적화하는 단계별 가이드를 따르세요."
"linktitle": "내장 글꼴 비활성화로 PDF 크기 줄이기"
"second_title": "Aspose.Words 문서 처리 API"
"title": "내장 글꼴 비활성화로 PDF 크기 줄이기"
"url": "/ko/net/programming-with-pdfsaveoptions/disable-embed-windows-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 내장 글꼴 비활성화로 PDF 크기 줄이기

## 소개

PDF 파일 크기를 줄이는 것은 효율적인 저장과 빠른 공유를 위해 매우 중요합니다. 효과적인 방법 중 하나는 내장 글꼴을 비활성화하는 것입니다. 특히 대부분의 시스템에서 표준 글꼴을 이미 사용할 수 있는 경우에는 더욱 그렇습니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 내장 글꼴을 비활성화하여 PDF 크기를 줄이는 방법을 살펴보겠습니다. 각 단계를 자세히 살펴보고 이를 자신의 프로젝트에서 쉽게 구현할 수 있도록 하겠습니다.

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

- .NET용 Aspose.Words: 아직 설치하지 않았다면 다음에서 다운로드하여 설치하세요. [다운로드 링크](https://releases.aspose.com/words/net/).
- .NET 개발 환경: Visual Studio가 인기 있는 선택입니다.
- 샘플 Word 문서: PDF로 변환하려는 DOCX 파일을 준비하세요.

## 네임스페이스 가져오기

시작하려면 프로젝트에 필요한 네임스페이스를 가져와야 합니다. 이렇게 하면 작업에 필요한 클래스와 메서드에 접근할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

이 과정을 간단하고 관리하기 쉬운 단계로 나누어 보겠습니다. 각 단계는 작업을 안내하여 모든 지점에서 무슨 일이 일어나고 있는지 이해할 수 있도록 도와줍니다.

## 1단계: 문서 초기화

먼저, PDF로 변환하려는 Word 문서를 불러와야 합니다. 여기서부터 여정이 시작됩니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

여기, `dataDir` 는 문서가 있는 디렉터리의 자리 표시자입니다. 바꾸기 `"YOUR DOCUMENT DIRECTORY"` 실제 경로와 함께.

## 2단계: PDF 저장 옵션 구성

다음으로 PDF 저장 옵션을 설정하겠습니다. 여기서는 표준 Windows 글꼴을 포함하지 않도록 지정합니다.

```csharp
// 출력 PDF는 표준 Windows 글꼴을 포함하지 않고 저장됩니다.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedNone
};
```

설정하여 `FontEmbeddingMode` 에게 `EmbedNone`, Aspose.Words에서는 PDF에 이러한 글꼴을 포함하지 않도록 지시하여 파일 크기를 줄입니다.

## 3단계: 문서를 PDF로 저장

마지막으로, 구성된 저장 옵션을 사용하여 문서를 PDF로 저장합니다. 이때 DOCX가 압축 PDF로 변환되는 결정적인 순간이 옵니다.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DisableEmbedWindowsFonts.pdf", saveOptions);
```

바꾸다 `"YOUR DOCUMENT DIRECTORY"` 실제 디렉터리 경로를 다시 입력하세요. 이제 출력 PDF는 내장된 표준 글꼴 없이 지정된 디렉터리에 저장됩니다.

## 결론

다음 단계를 따르면 PDF 파일 크기를 크게 줄일 수 있습니다. 내장 글꼴을 비활성화하는 것은 문서를 더 가볍고 공유하기 쉽게 만드는 간단하면서도 효과적인 방법입니다. Aspose.Words for .NET은 이 과정을 원활하게 처리하여 최소한의 노력으로 파일을 최적화할 수 있도록 지원합니다.

## 자주 묻는 질문

### PDF에 내장된 글꼴을 비활성화해야 하는 이유는 무엇입니까?
내장된 글꼴을 비활성화하면 PDF 파일 크기가 크게 줄어들어 저장 효율성이 높아지고 공유 속도도 빨라집니다.

### 내장된 글꼴 없이도 PDF가 올바르게 표시될까요?
네, PDF를 보는 시스템에서 해당 글꼴이 표준이고 사용 가능하다면 올바르게 표시됩니다.

### PDF에 특정 글꼴만 선택적으로 포함할 수 있나요?
네, Aspose.Words for .NET을 사용하면 어떤 글꼴을 포함할지 사용자 지정할 수 있으므로 파일 크기를 줄이는 데 있어 유연성이 제공됩니다.

### PDF에 내장된 글꼴을 비활성화하려면 Aspose.Words for .NET이 필요합니까?
네, Aspose.Words for .NET은 PDF에 글꼴 포함 옵션을 구성하는 데 필요한 기능을 제공합니다.

### 문제가 발생하면 어떻게 지원을 받을 수 있나요?
방문할 수 있습니다 [지원 포럼](https://forum.aspose.com/c/words/8) 문제가 발생하면 도움을 받으세요.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}