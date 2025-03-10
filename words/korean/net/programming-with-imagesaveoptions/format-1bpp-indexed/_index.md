---
title: 형식 1Bpp 색인됨
linktitle: 형식 1Bpp 색인됨
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서를 1Bpp 인덱스 이미지로 변환하는 방법을 알아보세요. 쉬운 변환을 위한 단계별 가이드를 따르세요.
weight: 10
url: /ko/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 형식 1Bpp 색인됨

## 소개

몇 줄의 코드만으로 Word 문서를 흑백 이미지로 저장하는 방법을 궁금해하신 적이 있나요? 글쎄요, 운이 좋으시네요! 오늘은 Aspose.Words for .NET을 사용하여 문서를 1Bpp 색인 이미지로 변환할 수 있는 멋진 작은 요령을 알아보겠습니다. 이 형식은 특정 유형의 디지털 보관, 인쇄 또는 공간을 절약해야 할 때 적합합니다. 각 단계를 나누어 아주 쉽게 설명해 드리겠습니다. 시작할 준비가 되셨나요? 시작해 볼까요!

## 필수 조건

실제로 작업을 시작하기 전에 꼭 준비해야 할 몇 가지 사항이 있습니다.

-  Aspose.Words for .NET: 라이브러리가 설치되어 있는지 확인하세요.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- .NET 개발 환경: Visual Studio가 좋은 옵션이지만, 편안한 환경을 사용하면 됩니다.
- C#에 대한 기본 지식: 걱정하지 마세요. 간단하게 설명하겠지만 C#에 대한 약간의 지식이 도움이 될 것입니다.
- Word 문서: 변환할 샘플 Word 문서를 준비하세요.

## 네임스페이스 가져오기

우선, 필요한 네임스페이스를 가져와야 합니다. 이는 Aspose.Words에서 필요한 클래스와 메서드에 액세스할 수 있게 해주기 때문에 매우 중요합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1단계: 문서 디렉토리 설정

문서 디렉토리 경로를 지정해야 합니다. Word 문서가 저장되는 곳이고 변환된 이미지가 저장되는 곳입니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: Word 문서 로드

 이제 Aspose.Words에 Word 문서를 로드해 보겠습니다.`Document` 객체. 이 객체는 Word 파일을 나타내며 조작할 수 있습니다.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3단계: 이미지 저장 옵션 구성

 다음으로, 우리는 다음을 설정해야 합니다.`ImageSaveOptions`마법이 일어나는 곳입니다. 1Bpp 인덱스 색상 모드로 PNG 형식으로 이미지를 저장하도록 구성하겠습니다.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: 이것은 문서를 PNG 이미지로 저장하고 싶다는 것을 지정합니다.
- PageSet(1): 이는 첫 번째 페이지만 변환하고 있음을 나타냅니다.
- ImageColorMode.BlackAndWhite: 이미지를 흑백으로 설정합니다.
- ImagePixelFormat.Format1bppIndexed: 이미지 형식을 1Bpp 인덱스로 설정합니다.

## 4단계: 문서를 이미지로 저장

 마지막으로, 우리는 다음을 사용하여 문서를 이미지로 저장합니다.`Save` 의 방법`Document` 물체.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## 결론

이제 다 되었습니다! 몇 줄의 코드만으로 Aspose.Words for .NET을 사용하여 Word 문서를 1Bpp 인덱스 이미지로 변환했습니다. 이 방법은 문서에서 고대비, 공간 효율적인 이미지를 만드는 데 매우 유용합니다. 이제 프로젝트와 워크플로에 쉽게 통합할 수 있습니다. 즐거운 코딩 되세요!

## 자주 묻는 질문

### 1Bpp 인덱스 이미지란 무엇인가요?
1Bpp(픽셀당 1비트) 인덱스 이미지는 각 픽셀이 0 또는 1의 단일 비트로 표현되는 흑백 이미지 형식입니다. 이 형식은 공간 효율성이 매우 높습니다.

### 한 번에 Word 문서의 여러 페이지를 변환할 수 있나요?
 네, 가능합니다. 수정하세요.`PageSet` 에 있는 재산`ImageSaveOptions` 여러 페이지나 전체 문서를 포함합니다.

### Aspose.Words for .NET을 사용하려면 라이선스가 필요합니까?
 네, Aspose.Words for .NET은 전체 기능을 사용하려면 라이선스가 필요합니다.[여기 임시 면허증](https://purchase.aspose.com/temporary-license/).

### Word 문서를 어떤 다른 이미지 형식으로 변환할 수 있나요?
 Aspose.Words는 JPEG, BMP, TIFF를 포함한 다양한 이미지 형식을 지원합니다. 간단히 변경하세요.`SaveFormat` 에서`ImageSaveOptions`.

### .NET용 Aspose.Words에 대한 추가 문서는 어디에서 찾을 수 있나요?
 자세한 문서는 다음에서 찾을 수 있습니다.[.NET 설명서 페이지용 Aspose.Words](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
