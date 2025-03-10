---
title: 메타파일을 Emf 또는 Wmf로 변환
linktitle: 메타파일을 Emf 또는 Wmf로 변환
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 문서를 HTML로 변환할 때 메타파일을 EMF 또는 WMF 형식으로 변환하는 방법에 대한 단계별 가이드입니다.
weight: 10
url: /ko/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 메타파일을 Emf 또는 Wmf로 변환

## 소개

Aspose.Words for .NET의 세계에 대한 또 다른 심층적인 탐구에 오신 것을 환영합니다. 오늘은 멋진 트릭을 다루겠습니다. Word 문서에서 SVG 이미지를 EMF 또는 WMF 형식으로 변환하는 것입니다. 약간 기술적으로 들릴 수 있지만 걱정하지 마세요. 이 튜토리얼을 마칠 때쯤이면 전문가가 될 것입니다. 노련한 개발자이든 Aspose.Words for .NET을 막 시작하든 이 가이드는 단계별로 알아야 할 모든 것을 안내합니다.

## 필수 조건

코드로 들어가기 전에 모든 것이 설정되어 있는지 확인해 보겠습니다. 필요한 것은 다음과 같습니다.

1.  Aspose.Words for .NET 라이브러리: 최신 버전이 있는지 확인하세요. 최신 버전이 없으면 다음에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
2. .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
3. 개발 환경: Visual Studio와 같은 IDE는 당신의 삶을 더욱 편리하게 만들어 줄 것입니다.
4. C#에 대한 기본 지식: 전문가가 될 필요는 없지만, 기본적인 이해가 도움이 됩니다.

다 받으셨나요? 좋아요! 시작해 볼까요.

## 네임스페이스 가져오기

우선, 필요한 네임스페이스를 가져와야 합니다. 이는 프로그램에서 사용할 클래스와 메서드를 어디에서 찾을 수 있는지 알려주기 때문에 중요합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

이러한 네임스페이스는 기본 시스템 기능부터 이 튜토리얼에 필요한 특정 Aspose.Words 기능까지 모든 것을 포괄합니다.

## 1단계: 문서 디렉토리 설정

문서 디렉토리 경로를 정의하는 것으로 시작해 보겠습니다. 메타파일을 변환한 후 Word 문서가 저장되는 곳입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 문서를 저장하려는 실제 경로를 입력합니다.

## 2단계: SVG로 HTML 문자열 만들기

다음으로, 변환하려는 SVG 이미지가 포함된 HTML 문자열이 필요합니다. 간단한 예는 다음과 같습니다.

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' 너비='500' 높이='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

이 HTML 스니펫에는 "Hello world!"라고 말하는 기본 SVG가 포함되어 있습니다.

## 3단계: ConvertSvgToEmf 옵션으로 HTML 로드

 이제 우리는 다음을 사용합니다.`HtmlLoadOptions` HTML에서 SVG 이미지를 처리하는 방법을 지정합니다. 설정`ConvertSvgToEmf` 에게`true` SVG 이미지가 EMF 형식으로 변환되도록 합니다.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

 이 코드 조각은 새 것을 만듭니다.`Document` 지정된 로드 옵션을 사용하여 HTML 문자열을 로드하여 개체를 만듭니다.

## 4단계: 메타파일 형식에 대한 HtmlSaveOptions 설정

 올바른 메타파일 형식으로 문서를 저장하려면 다음을 사용합니다.`HtmlSaveOptions` . 여기서 우리는 설정`MetafileFormat` 에게`HtmlMetafileFormat.Png` , 하지만 이것을 변경할 수 있습니다`Emf` 또는`Wmf` 귀하의 요구 사항에 따라 다릅니다.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## 5단계: 문서 저장

마지막으로 지정된 저장 옵션을 사용하여 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

이렇게 하면 정의된 대로 메타파일 형식이 변환되어 지정된 디렉토리에 문서가 저장됩니다.

## 결론

이제 다 됐습니다! 이러한 단계를 따르면 Aspose.Words for .NET을 사용하여 Word 문서에서 SVG 이미지를 EMF 또는 WMF 형식으로 성공적으로 변환했습니다. 이 방법은 호환성을 보장하고 다양한 플랫폼에서 문서의 시각적 무결성을 유지하는 데 유용합니다. 즐거운 코딩 되세요!

## 자주 묻는 질문

### 이 방법을 사용하여 다른 이미지 형식을 변환할 수 있나요?
네, 로드 및 저장 옵션을 적절히 조정하여 다양한 이미지 형식을 변환할 수 있습니다.

### 특정 .NET Framework 버전을 사용해야 합니까?
Aspose.Words for .NET은 여러 .NET Framework 버전을 지원하지만, 최상의 호환성과 기능을 위해 항상 최신 버전을 사용하는 것이 좋습니다.

### SVG를 EMF나 WMF로 변환하면 어떤 이점이 있나요?
SVG를 EMF 또는 WMF로 변환하면 SVG를 완벽하게 지원하지 않는 환경에서도 벡터 그래픽이 올바르게 보존되고 렌더링됩니다.

### 여러 문서에 대해 이 프로세스를 자동화할 수 있나요?
물론입니다! 여러 HTML 파일을 반복하여 동일한 프로세스를 적용하여 일괄 처리를 위한 변환을 자동화할 수 있습니다.

### Aspose.Words for .NET에 대한 추가 리소스와 지원은 어디에서 찾을 수 있나요?
 포괄적인 문서를 찾을 수 있습니다[여기](https://reference.aspose.com/words/net/) Aspose 커뮤니티로부터 지원을 받으세요[여기](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
