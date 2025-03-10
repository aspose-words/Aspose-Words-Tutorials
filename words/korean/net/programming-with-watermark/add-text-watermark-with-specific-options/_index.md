---
title: 특정 옵션으로 텍스트 워터마크 추가
linktitle: 특정 옵션으로 텍스트 워터마크 추가
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에 특정 옵션이 있는 텍스트 워터마크를 추가하는 방법을 알아보세요. 글꼴, 크기, 색상 및 레이아웃을 쉽게 사용자 지정하세요.
weight: 10
url: /ko/net/programming-with-watermark/add-text-watermark-with-specific-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 특정 옵션으로 텍스트 워터마크 추가

## 소개

워터마크는 Word 문서에 세련되고 기능적인 추가 기능이 될 수 있으며, 문서를 기밀로 표시하는 것부터 개인화된 터치를 추가하는 것까지 다양한 용도로 사용할 수 있습니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에 텍스트 워터마크를 추가하는 방법을 살펴보겠습니다. 글꼴 패밀리, 글꼴 크기, 색상 및 레이아웃과 같이 구성할 수 있는 특정 옵션에 대해 자세히 알아보겠습니다. 마지막에는 문서의 워터마크를 정확한 요구 사항에 맞게 사용자 지정할 수 있습니다. 그러니 코드 편집기를 가져와 시작해 봅시다!

## 필수 조건

시작하기 전에 다음 사항이 준비되었는지 확인하세요.

1.  Aspose.Words for .NET 라이브러리: Aspose.Words 라이브러리를 설치해야 합니다. 아직 설치하지 않았다면 다음에서 다운로드할 수 있습니다.[Aspose.Words 다운로드 링크](https://releases.aspose.com/words/net/).
2. C#에 대한 기본 이해: 이 튜토리얼은 C#을 프로그래밍 언어로 사용합니다. C# 구문에 대한 기본적인 이해가 도움이 될 것입니다.
3. .NET 개발 환경: .NET 애플리케이션을 만들고 실행할 수 있는 개발 환경(예: Visual Studio)이 설정되어 있는지 확인하세요.

## 네임스페이스 가져오기

Aspose.Words를 사용하려면 프로젝트에 필요한 네임스페이스를 포함해야 합니다. 가져와야 할 내용은 다음과 같습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## 1단계: 문서 설정

 먼저 작업하려는 문서를 로드해야 합니다. 이 튜토리얼에서는 샘플 문서 이름을 사용합니다.`Document.docx`. 이 문서가 지정된 디렉토리에 있는지 확인하세요.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 이 단계에서는 문서가 있는 디렉토리를 정의하고 이를 인스턴스에 로드합니다.`Document` 수업.

## 2단계: 워터마크 옵션 구성

다음으로, 텍스트 워터마크에 대한 옵션을 구성합니다. 글꼴 패밀리, 글꼴 크기, 색상 및 레이아웃과 같은 다양한 측면을 사용자 정의할 수 있습니다. 이러한 옵션을 설정해 보겠습니다.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

각 옵션의 기능은 다음과 같습니다.
- `FontFamily`: 워터마크 텍스트의 글꼴을 지정합니다.
- `FontSize`: 워터마크 텍스트의 크기를 설정합니다.
- `Color`: 워터마크 텍스트의 색상을 정의합니다.
- `Layout`워터마크의 방향(수평 또는 대각선)을 결정합니다.
- `IsSemitrasparent`: 워터마크를 반투명하게 할지 여부를 설정합니다.

## 3단계: 워터마크 텍스트 추가

이제 이전에 구성한 옵션을 사용하여 문서에 워터마크를 적용합니다. 이 단계에서는 워터마크 텍스트를 "테스트"로 설정하고 정의한 옵션을 적용합니다.

```csharp
doc.Watermark.SetText("Test", options);
```

이 코드 줄은 지정된 옵션을 적용하여 "테스트"라는 텍스트가 있는 워터마크를 문서에 추가합니다.

## 4단계: 문서 저장

마지막으로, 새로운 워터마크가 적용된 문서를 저장합니다. 원본 문서를 덮어쓰지 않으려면 새 이름으로 저장할 수 있습니다.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

이 코드 조각은 수정된 문서를 새 파일 이름으로 같은 디렉토리에 저장합니다.

## 결론

Aspose.Words for .NET을 사용하여 Word 문서에 텍스트 워터마크를 추가하는 것은 관리 가능한 단계로 나누면 간단한 프로세스입니다. 이 튜토리얼을 따라하면 글꼴, 크기, 색상, 레이아웃 및 투명도를 포함한 다양한 워터마크 옵션을 구성하는 방법을 배웠습니다. 이러한 기술을 사용하면 이제 문서를 사용자 정의하여 필요에 더 잘 부합하거나 기밀성 또는 브랜딩과 같은 필수 정보를 포함할 수 있습니다.

 질문이 있거나 추가 지원이 필요한 경우 언제든지 확인하세요.[Aspose.Words 문서](https://reference.aspose.com/words/net/) 또는 방문하세요[Aspose 지원 포럼](https://forum.aspose.com/c/words/8) 더 많은 도움이 필요하면.

## 자주 묻는 질문

### 워터마크에 다른 글꼴을 사용할 수 있나요?

 예, 시스템에 설치된 글꼴을 지정하여 선택할 수 있습니다.`FontFamily` 에 있는 재산`TextWatermarkOptions`.

### 워터마크의 색상을 어떻게 바꾸나요?

 워터마크의 색상은 설정을 통해 변경할 수 있습니다.`Color` 에 있는 재산`TextWatermarkOptions` 어떤 것에`System.Drawing.Color` 값.

### 한 문서에 워터마크를 여러 개 추가할 수 있나요?

Aspose.Words는 한 번에 하나의 워터마크를 추가하는 것을 지원합니다. 여러 개의 워터마크를 추가하려면 순차적으로 생성하여 적용해야 합니다.

### 워터마크의 위치를 조정할 수 있나요?

 그만큼`WatermarkLayout`속성은 방향을 결정하지만 정확한 위치 조정은 직접 지원되지 않습니다. 정확한 배치를 위해 다른 기술을 사용해야 할 수도 있습니다.

### 반투명 워터마크가 필요한 경우 어떻게 해야 하나요?

 설정하다`IsSemitrasparent`재산에`true` 워터마크를 반투명하게 만드세요.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
