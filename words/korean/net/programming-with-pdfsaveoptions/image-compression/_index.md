---
"description": "Aspose.Words for .NET을 사용하여 PDF 문서의 이미지를 압축하는 방법을 알아보세요. 파일 크기와 품질을 최적화하려면 이 가이드를 따르세요."
"linktitle": "PDF 문서의 이미지 압축"
"second_title": "Aspose.Words 문서 처리 API"
"title": "PDF 문서의 이미지 압축"
"url": "/ko/net/programming-with-pdfsaveoptions/image-compression/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF 문서의 이미지 압축

## 소개

오늘날의 디지털 시대에는 문서 크기 관리가 성능과 저장 효율성 모두에 매우 중요합니다. 대용량 보고서든 복잡한 프레젠테이션이든, 품질 저하 없이 파일 크기를 줄이는 것은 필수적입니다. PDF 문서의 이미지 압축은 이러한 목표를 달성하는 데 중요한 기술입니다. Aspose.Words for .NET을 사용하고 있다면, 바로 이 방법을 활용하세요! 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 PDF 문서의 이미지를 압축하는 과정을 안내합니다. 다양한 압축 옵션과 이를 효과적으로 적용하여 PDF의 품질과 크기를 최적화하는 방법을 살펴보겠습니다.

## 필수 조건

튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

1. Aspose.Words for .NET: Aspose.Words for .NET이 설치되어 있어야 합니다. 다음에서 다운로드할 수 있습니다. [Aspose 웹사이트](https://releases.aspose.com/words/net/).

2. C#에 대한 기본 지식: C# 프로그래밍에 대한 지식은 이 튜토리얼에서 제공하는 코드 예제를 이해하는 데 도움이 됩니다.

3. 개발 환경: Visual Studio와 같은 .NET 개발 환경이 설정되어 있는지 확인하세요.

4. 샘플 문서: 이미지 압축을 테스트하기 위해 샘플 Word 문서(예: "Rendering.docx")를 준비하세요.

5. Aspose 라이선스: Aspose.Words for .NET 라이선스 버전을 사용하는 경우 라이선스가 제대로 구성되어 있는지 확인하세요. 임시 라이선스가 필요한 경우 다음에서 라이선스를 받을 수 있습니다. [Aspose의 임시 라이센스 페이지](https://purchase.aspose.com/temporary-license/).

## 네임스페이스 가져오기

Aspose.Words for .NET을 사용하여 PDF 문서에서 이미지 압축을 시작하려면 필요한 네임스페이스를 가져와야 합니다. 방법은 다음과 같습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

이러한 네임스페이스는 Word 문서를 조작하고 다양한 옵션을 사용하여 PDF로 저장하는 데 필요한 핵심 기능에 대한 액세스를 제공합니다.

## 1단계: 문서 디렉터리 설정

코딩을 시작하기 전에 문서 디렉터리 경로를 정의하세요. 이렇게 하면 파일을 쉽게 찾고 저장할 수 있습니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

바꾸다 `"YOUR DOCUMENT DIRECTORY"` 샘플 문서가 저장된 경로를 사용합니다.

## 2단계: Word 문서 로드

다음으로 Word 문서를 로드합니다. `Aspose.Words.Document` 객체입니다. 이를 통해 프로그래밍 방식으로 문서를 다룰 수 있습니다.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

여기, `"Rendering.docx"` 샘플 Word 문서의 이름입니다. 이 파일이 지정된 디렉터리에 있는지 확인하세요.

## 3단계: 기본 이미지 압축 구성

생성하다 `PdfSaveOptions` 이미지 압축을 포함한 PDF 저장 옵션을 구성하는 개체입니다. `ImageCompression` 재산에 `PdfImageCompression.Jpeg` 이미지에 JPEG 압축을 사용합니다.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
	// JPEG를 사용하여 이미지 압축
    ImageCompression = PdfImageCompression.Jpeg,
	// 선택 사항: PDF에서 양식 필드 보존
    PreserveFormFields = true
};
```

## 4단계: 기본 압축으로 문서 저장

구성된 이미지 압축 옵션을 사용하여 Word 문서를 PDF로 저장합니다. 이렇게 하면 PDF의 이미지에 JPEG 압축이 적용됩니다.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);
```

이 예에서 출력 PDF의 이름은 다음과 같습니다. `"WorkingWithPdfSaveOptions.PdfImageCompression.pdf"`필요에 따라 파일 이름을 조정하세요.

## 5단계: PDF/A 규정을 준수하는 고급 압축 구성

더욱 향상된 압축을 위해, 특히 PDF/A 표준을 준수해야 하는 경우 추가 옵션을 구성할 수 있습니다. `Compliance` 재산에 `PdfCompliance.PdfA2u` 그리고 조정하다 `JpegQuality` 재산.

```csharp
PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	// PDF/A-2u에 대한 규정 준수 설정
    Compliance = PdfCompliance.PdfA2u,
	// JPEG 압축 사용
    ImageCompression = PdfImageCompression.Jpeg,
	// JPEG 품질을 조정하여 압축 수준을 제어합니다.
    JpegQuality = 100 
};
```

## 6단계: 고급 압축으로 문서 저장

고급 압축 설정을 사용하여 Word 문서를 PDF로 저장합니다. 이 설정을 사용하면 PDF가 PDF/A 표준을 준수하고 고품질 JPEG 압축을 사용합니다.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
```

여기서 출력 PDF의 이름은 다음과 같습니다. `"WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf"`. 선호도에 따라 파일 이름을 수정하세요.

## 결론

이미지를 압축하여 PDF 문서 크기를 줄이는 것은 문서 성능과 저장 공간을 최적화하는 데 중요한 단계입니다. Aspose.Words for .NET을 사용하면 이미지 압축을 효과적으로 제어할 수 있는 강력한 도구를 활용할 수 있습니다. 이 튜토리얼에 설명된 단계를 따르면 PDF 문서의 품질을 높이고 압축률을 낮출 수 있습니다. 기본 압축부터 고급 압축까지, Aspose.Words는 사용자의 요구에 맞는 유연성을 제공합니다.


## 자주 묻는 질문

### PDF에서 이미지 압축이란 무엇인가요?
이미지 압축은 이미지 품질을 낮춰 PDF 문서의 파일 크기를 줄이는데, 이는 저장 공간과 성능을 최적화하는 데 도움이 됩니다.

### Aspose.Words for .NET은 이미지 압축을 어떻게 처리하나요?
Aspose.Words for .NET은 다음을 제공합니다. `PdfSaveOptions` JPEG 압축을 포함하여 다양한 이미지 압축 옵션을 설정할 수 있는 클래스입니다.

### PDF/A 표준을 준수하기 위해 Aspose.Words for .NET을 사용할 수 있나요?
네, Aspose.Words는 PDF/A 규격을 지원하므로 보관 및 장기 보존 표준을 충족하는 형식으로 문서를 저장할 수 있습니다.

### JPEG 품질은 PDF 파일 크기에 어떤 영향을 미칩니까?
JPEG 품질 설정을 높이면 이미지 품질은 좋아지지만 파일 크기가 커지고, 품질 설정을 낮추면 파일 크기는 줄어들지만 이미지 선명도에 영향을 미칠 수 있습니다.

### Aspose.Words for .NET에 대한 자세한 정보는 어디에서 찾을 수 있나요?
Aspose.Words for .NET에 대해 자세히 알아보려면 여기를 클릭하세요. [선적 서류 비치](https://reference.aspose.com/words/net/), [지원하다](https://forum.aspose.com/c/words/8), 그리고 [다운로드](https://releases.aspose.com/words/net/) 페이지.

### Aspose.Words for .NET을 사용하여 이미지를 압축하기 위한 샘플 소스 코드

```csharp

// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");

PdfSaveOptions saveOptions = new PdfSaveOptions
{
	ImageCompression = PdfImageCompression.Jpeg, PreserveFormFields = true
};

doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);

PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	Compliance = PdfCompliance.PdfA2u,
	ImageCompression = PdfImageCompression.Jpeg,
	JpegQuality = 100, // 파일 크기를 줄이려면 JPEG 압축을 50% 품질로 사용하세요.
};



doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
	
```


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}