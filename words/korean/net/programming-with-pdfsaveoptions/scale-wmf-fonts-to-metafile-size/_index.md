---
"description": "Aspose.Words for .NET을 사용하여 PDF로 변환할 때 WMF 글꼴을 메타파일 크기로 조정하여 PDF 크기를 줄이는 단계별 가이드입니다."
"linktitle": "Scale WMF 글꼴을 메타파일 크기로 PDF 크기 줄이기"
"second_title": "Aspose.Words 문서 처리 API"
"title": "Scale WMF 글꼴을 메타파일 크기로 PDF 크기 줄이기"
"url": "/ko/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Scale WMF 글꼴을 메타파일 크기로 PDF 크기 줄이기

## 소개

PDF 파일, 특히 WMF(Windows Metafile) 그래픽이 포함된 Word 문서에서 생성된 PDF 파일을 작업할 때 크기 관리는 문서 처리에 매우 중요한 요소가 될 수 있습니다. PDF 크기를 제어하는 한 가지 방법은 문서 내에서 WMF 글꼴이 렌더링되는 방식을 조정하는 것입니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 WMF 글꼴을 메타파일 크기에 맞춰 조정하여 PDF 크기를 줄이는 방법을 살펴보겠습니다.

## 필수 조건

다음 단계를 진행하기 전에 다음 사항이 있는지 확인하세요.

1. Aspose.Words for .NET: Aspose.Words 라이브러리가 설치되어 있는지 확인하세요. 설치되어 있지 않으면 [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. 개발 환경: 이 튜토리얼에서는 C# 코드를 작성하고 실행할 수 있는 .NET 개발 환경(예: Visual Studio)이 설정되어 있다고 가정합니다.
3. .NET 프로그래밍에 대한 기본적인 이해: 기본적인 .NET 프로그래밍 개념과 C# 구문에 대한 지식이 도움이 됩니다.
4. WMF 그래픽이 포함된 Word 문서: WMF 그래픽이 포함된 Word 문서가 필요합니다. 직접 문서를 작성하거나 테스트용으로 만들 수 있습니다.

## 네임스페이스 가져오기

먼저 C# 프로젝트에 필요한 네임스페이스를 가져와야 합니다. 이렇게 하면 Aspose.Words 작업에 필요한 클래스와 메서드에 접근할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1단계: Word 문서 로드

시작하려면 WMF 그래픽이 포함된 Word 문서를 로드하세요. 이 작업은 다음을 사용하여 수행됩니다. `Document` Aspose.Words의 클래스입니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 문서를 로드하세요
Document doc = new Document(dataDir + "WMF with text.docx");
```

여기, `dataDir` 는 문서 디렉터리 경로의 자리 표시자입니다. 우리는 다음 인스턴스를 생성합니다. `Document` Word 파일 경로를 전달하여 클래스를 만듭니다. 이렇게 하면 문서가 메모리에 로드되어 추가 처리를 위해 준비됩니다.

## 2단계: 메타파일 렌더링 옵션 구성

다음으로 메타파일 렌더링 옵션을 구성해야 합니다. 구체적으로는 `ScaleWmfFontsToMetafileSize` 재산에 `false`. 이는 WMF 글꼴의 크기를 메타파일 크기에 맞게 조정할지 여부를 제어합니다.

```csharp
// MetafileRenderingOptions의 새 인스턴스를 만듭니다.
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

그만큼 `MetafileRenderingOptions` 클래스는 메타파일(예: WMF)을 렌더링하는 방법에 대한 옵션을 제공합니다. `ScaleWmfFontsToMetafileSize` 에게 `false`, Aspose.Words가 메타파일 크기에 따라 글꼴 크기를 조정하지 않도록 지시하고 있는데, 이는 전체 PDF 크기를 줄이는 데 도움이 될 수 있습니다.

## 3단계: PDF 저장 옵션 설정

이제 방금 설정한 메타파일 렌더링 옵션을 사용하도록 PDF 저장 옵션을 구성하세요. 이렇게 하면 Aspose.Words가 문서를 PDF로 저장할 때 메타파일을 어떻게 처리할지 결정하게 됩니다.

```csharp
// PdfSaveOptions의 새 인스턴스를 만듭니다.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

그만큼 `PdfSaveOptions` 클래스를 사용하면 문서를 PDF로 저장하기 위한 다양한 설정을 지정할 수 있습니다. 이전에 구성된 `MetafileRenderingOptions` 에게 `MetafileRenderingOptions` 의 속성 `PdfSaveOptions`원하는 메타파일 렌더링 설정에 따라 문서가 저장되었는지 확인하세요.

## 4단계: 문서를 PDF로 저장

마지막으로, 구성된 저장 옵션을 사용하여 Word 문서를 PDF로 저장합니다. 이렇게 하면 메타파일 렌더링 옵션을 포함한 모든 설정이 출력 PDF에 적용됩니다.


```csharp
// 문서를 PDF로 저장
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

이 단계에서는 `Save` 방법 `Document` 클래스는 문서를 PDF 파일로 내보내는 데 사용됩니다. PDF가 저장될 경로와 함께 지정됩니다. `PdfSaveOptions` 메타파일 렌더링 설정을 포함합니다.

## 결론

WMF 글꼴을 메타파일 크기에 맞춰 조정하면 Word 문서에서 생성된 PDF 파일의 크기를 크게 줄일 수 있습니다. 이 기술은 시각적 콘텐츠의 품질을 손상시키지 않으면서 문서 저장 및 배포를 최적화하는 데 도움이 됩니다. 위에 설명된 단계를 따르면 PDF 파일을 더욱 관리하기 쉽고 효율적으로 관리할 수 있습니다.

## 자주 묻는 질문

### WMF란 무엇이고 PDF 크기에 왜 중요한가요?

WMF(Windows Metafile)는 Microsoft Windows에서 사용되는 그래픽 형식입니다. 벡터 데이터와 비트맵 데이터를 모두 포함할 수 있습니다. 벡터 데이터는 크기 조절 및 조작이 가능하므로, 불필요하게 큰 PDF 파일이 생성되지 않도록 적절하게 처리하는 것이 중요합니다.

### WMF 글꼴을 메타파일 크기에 맞게 조정하면 PDF에 어떤 영향이 있나요?

WMF 글꼴을 메타파일 크기에 맞게 조정하면 파일 크기를 늘릴 수 있는 고해상도 글꼴 렌더링을 방지하여 전체 PDF 크기를 줄이는 데 도움이 됩니다.

### Aspose.Words에서 다른 메타파일 형식을 사용할 수 있나요?

네, Aspose.Words는 WMF 외에도 EMF(Enhanced Metafile)를 포함한 다양한 메타파일 형식을 지원합니다.

### 이 기술은 모든 유형의 Word 문서에 적용할 수 있나요?

네, 이 기술은 WMF 그래픽이 포함된 모든 Word 문서에 적용할 수 있어 생성된 PDF의 크기를 최적화하는 데 도움이 됩니다.

### Aspose.Words에 대한 자세한 정보는 어디에서 찾을 수 있나요?

Aspose.Words에 대해 더 자세히 알아보려면 여기를 클릭하세요. [Aspose.Words 문서](https://reference.aspose.com/words/net/)다운로드, 평가판 및 지원을 받으려면 다음을 방문하세요. [Aspose.Words 다운로드 페이지](https://releases.aspose.com/words/net/), [Aspose.Words 구매](https://purchase.aspose.com/buy), [무료 체험](https://releases.aspose.com/), [임시 면허](https://purchase.aspose.com/temporary-license/), 그리고 [지원하다](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}