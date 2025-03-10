---
title: 렌더링 시 기본 글꼴 지정
linktitle: 렌더링 시 기본 글꼴 지정
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서를 렌더링할 때 기본 글꼴을 지정하는 방법을 알아보세요. 플랫폼 간에 일관된 문서 모양을 보장합니다.
weight: 10
url: /ko/net/working-with-fonts/specify-default-font-when-rendering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 렌더링 시 기본 글꼴 지정

## 소개

Word 문서가 다양한 플랫폼에서 올바르게 렌더링되도록 하는 것은 어려울 수 있으며, 특히 글꼴 호환성을 다룰 때 더욱 그렇습니다. 일관된 모양을 유지하는 한 가지 방법은 문서를 PDF나 다른 형식으로 렌더링할 때 기본 글꼴을 지정하는 것입니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 기본 글꼴을 설정하는 방법을 살펴보겠습니다. 그러면 문서를 어디에서 보든 멋지게 보일 것입니다.

## 필수 조건

코드를 살펴보기 전에 이 튜토리얼을 따라하는 데 필요한 내용부터 살펴보겠습니다.

- Aspose.Words for .NET: 최신 버전이 설치되어 있는지 확인하세요. 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio 또는 기타 .NET 개발 환경.
- C#에 대한 기본 지식: 이 튜토리얼은 독자가 C# 프로그래밍에 익숙하다고 가정합니다.

## 네임스페이스 가져오기

시작하려면 필요한 네임스페이스를 가져와야 합니다. 이를 통해 Aspose.Words 작업에 필요한 클래스와 메서드에 액세스할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

이제 기본 글꼴을 지정하는 과정을 쉽게 따라할 수 있는 단계로 나누어 보겠습니다.

## 1단계: 문서 디렉토리 설정

먼저, 문서 디렉토리 경로를 정의합니다. 여기에 입력 및 출력 파일이 저장됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 문서 로드

다음으로, 렌더링하려는 문서를 로드합니다. 이 예에서는 "Rendering.docx"라는 파일을 사용합니다.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3단계: 글꼴 설정 구성

 인스턴스를 생성합니다`FontSettings` 그리고 기본 글꼴을 지정합니다. 렌더링 중에 정의된 글꼴을 찾을 수 없는 경우 Aspose.Words는 컴퓨터에서 사용 가능한 가장 가까운 글꼴을 사용합니다.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## 4단계: 문서에 글꼴 설정 적용

구성된 글꼴 설정을 문서에 할당합니다.

```csharp
doc.FontSettings = fontSettings;
```

## 5단계: 문서 저장

마지막으로, 원하는 형식으로 문서를 저장합니다. 이 경우, PDF로 저장하겠습니다.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## 결론

이러한 단계를 따르면 Word 문서가 지정된 기본 글꼴로 렌더링되어 다양한 플랫폼에서 일관성을 유지할 수 있습니다. 이는 널리 공유되거나 글꼴 가용성이 다양한 시스템에서 볼 수 있는 문서에 특히 유용할 수 있습니다.


## 자주 묻는 질문

### Aspose.Words에서 기본 글꼴을 지정하는 이유는 무엇입니까?
기본 글꼴을 지정하면 원래 글꼴을 사용할 수 없더라도 다양한 플랫폼에서 문서가 일관되게 표시됩니다.

### 렌더링 중에 기본 글꼴을 찾을 수 없으면 어떻게 되나요?
Aspose.Words는 문서의 모양을 가능한 한 비슷하게 유지하기 위해 컴퓨터에서 사용 가능한 글꼴 중 가장 가까운 글꼴을 사용합니다.

### 기본 글꼴을 여러 개 지정할 수 있나요?
 아니요, 기본 글꼴을 하나만 지정할 수 있습니다. 그러나 다음을 사용하여 특정 사례에 대한 글꼴 대체를 처리할 수 있습니다.`FontSettings` 수업.

### Aspose.Words for .NET은 모든 버전의 Word 문서와 호환됩니까?
네, Aspose.Words for .NET은 DOC, DOCX, RTF 등 다양한 Word 문서 형식을 지원합니다.

### 문제가 발생하면 어디에서 지원을 받을 수 있나요?
 Aspose 커뮤니티와 개발자로부터 지원을 받을 수 있습니다.[Aspose.Words 지원 포럼](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
