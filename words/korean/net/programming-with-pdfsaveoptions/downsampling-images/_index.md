---
title: 다운샘플링 이미지로 PDF 문서 크기 줄이기
linktitle: 다운샘플링 이미지로 PDF 문서 크기 줄이기
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 이미지를 다운샘플링하여 PDF 문서 크기를 줄입니다. 더 빠른 업로드 및 다운로드 시간을 위해 PDF를 최적화합니다.
weight: 10
url: /ko/net/programming-with-pdfsaveoptions/downsampling-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 다운샘플링 이미지로 PDF 문서 크기 줄이기

## 소개

PDF는 디지털 세계의 필수 요소로, 문서 공유부터 전자책 만들기까지 모든 용도로 사용됩니다. 그러나 크기가 장애물이 될 수 있으며, 특히 이미지가 풍부한 콘텐츠를 다룰 때 그렇습니다. 여기서 이미지를 다운샘플링하는 것이 중요합니다. PDF 내 이미지의 해상도를 줄이면 품질을 크게 떨어뜨리지 않고도 파일 크기를 크게 줄일 수 있습니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 이를 달성하는 단계를 살펴보겠습니다.

## 필수 조건

코드로 넘어가기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.

1.  .NET용 Aspose.Words: Aspose.Words 라이브러리가 설치되어 있는지 확인하세요. 설치되어 있지 않으면 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 .NET 개발 환경.
3. C#에 대한 기본 지식: C# 프로그래밍의 기본을 이해하는 것이 도움이 됩니다.
4.  샘플 문서: Word 문서(예:`Rendering.docx`)을 PDF로 변환할 이미지가 포함되어 있습니다.

## 네임스페이스 가져오기

먼저, 필요한 네임스페이스를 가져와야 합니다. 코드 파일 맨 위에 다음을 추가합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

이제 이 과정을 관리 가능한 단계로 나누어 보겠습니다.

## 1단계: 문서 로드

첫 번째 단계는 Word 문서를 로드하는 것입니다. 여기서 문서 디렉토리 경로를 지정합니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

이 단계에서는 지정된 디렉토리에서 Word 문서를 로드합니다. 다음을 반드시 바꾸십시오.`"YOUR DOCUMENT DIRECTORY"` 문서가 위치한 실제 경로를 사용합니다.

## 2단계: 다운샘플링 옵션 구성

다음으로, 다운샘플링 옵션을 구성해야 합니다. 여기에는 이미지의 해상도와 해상도 임계값을 설정하는 것이 포함됩니다.

```csharp
// 다운샘플링에 대한 최소 임계값을 설정할 수 있습니다.
// 이 값을 설정하면 입력 문서의 두 번째 이미지가 다운샘플링되는 것을 방지할 수 있습니다.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

 여기서 우리는 새로운 인스턴스를 생성하고 있습니다`PdfSaveOptions` 그리고 설정`Resolution` 최대 36 DPI 및`ResolutionThreshold` 128 DPI로. 즉, 128 DPI보다 높은 해상도의 이미지는 36 DPI로 다운샘플링됩니다.

## 3단계: 문서를 PDF로 저장

마지막으로 구성된 옵션을 사용하여 문서를 PDF로 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

이 마지막 단계에서는 지정된 다운샘플링 옵션을 사용하여 동일한 디렉토리에 문서를 PDF로 저장합니다.

## 결론

이제 아시죠! Aspose.Words for .NET을 사용하여 이미지를 다운샘플링하여 PDF 크기를 성공적으로 줄였습니다. 이렇게 하면 PDF를 더 관리하기 쉬울 뿐만 아니라 업로드, 다운로드 속도가 빨라지고 보기 환경이 더 매끄러워집니다.

## 자주 묻는 질문

### 다운샘플링이란 무엇인가요?
다운샘플링은 이미지의 해상도를 줄이는 프로세스로, 이를 통해 이미지가 포함된 문서의 파일 크기를 줄이는 데 도움이 됩니다.

### 다운샘플링은 이미지 품질에 영향을 미칩니까?
네, 다운샘플링은 이미지 품질을 떨어뜨립니다. 그러나 그 영향은 해상도 감소 정도에 따라 달라집니다. 파일 크기와 이미지 품질 간의 균형입니다.

### 어떤 이미지를 다운샘플링할지 선택할 수 있나요?
 네, 설정하여`ResolutionThreshold`, 원래 해상도에 따라 어떤 이미지를 다운샘플링할지 제어할 수 있습니다.

### 다운샘플링에 이상적인 해상도는 무엇입니까?
이상적인 해상도는 귀하의 특정 요구 사항에 따라 달라집니다. 일반적으로 72 DPI는 웹 이미지에 사용되는 반면, 더 높은 해상도는 인쇄 품질에 사용됩니다.

### Aspose.Words for .NET은 무료인가요?
 Aspose.Words for .NET은 상용 제품이지만 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.aspose.com/) 또는 신청하세요[임시 면허](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
