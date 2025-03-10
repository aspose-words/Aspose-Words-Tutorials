---
title: 글꼴 대체 설정 설정
linktitle: 글꼴 대체 설정 설정
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET에서 글꼴 대체 설정을 설정하는 방법을 알아보세요. 이 포괄적인 가이드는 문서의 모든 문자가 올바르게 표시되도록 보장합니다.
weight: 10
url: /ko/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 대체 설정 설정

## 소개

다양한 언어나 특수 문자와 같이 다양한 텍스트 요소가 포함된 문서로 작업할 때는 이러한 요소가 올바르게 표시되는지 확인하는 것이 중요합니다. Aspose.Words for .NET은 글꼴 대체 설정이라는 강력한 기능을 제공하는데, 이는 원래 글꼴이 특정 문자를 지원하지 않을 때 글꼴을 대체하기 위한 규칙을 정의하는 데 도움이 됩니다. 이 가이드에서는 Aspose.Words for .NET을 사용하여 단계별 자습서로 글꼴 대체 설정을 설정하는 방법을 살펴보겠습니다.

## 필수 조건

튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

- C#에 대한 기본 지식: C# 프로그래밍 언어와 .NET 프레임워크에 익숙함.
-  .NET용 Aspose.Words: 다음에서 다운로드하고 설치하세요.[다운로드 링크](https://releases.aspose.com/words/net/).
- 개발 환경: 코드를 작성하고 실행할 수 있는 Visual Studio와 같은 환경입니다.
-  샘플 문서: 샘플 문서(예:`Rendering.docx`) 테스트 준비 완료.
- 글꼴 대체 규칙 XML: 글꼴 대체 규칙을 정의하는 XML 파일을 준비합니다.

## 네임스페이스 가져오기

Aspose.Words를 사용하려면 필요한 네임스페이스를 가져와야 합니다. 이를 통해 문서 처리에 필요한 다양한 클래스와 메서드에 액세스할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## 1단계: 문서 디렉토리 정의

먼저, 문서가 저장된 디렉토리를 정의합니다. 이는 문서를 찾고 처리하는 데 필수적입니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 문서 로드

 Aspose.Words에 문서를 로드하세요`Document` 객체. 이 단계에서는 문서를 프로그래밍 방식으로 작업할 수 있습니다.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3단계: 글꼴 설정 구성

 새로운 것을 만드세요`FontSettings` 객체를 만들고 XML 파일에서 글꼴 폴백 설정을 로드합니다. 이 XML 파일에는 글꼴 폴백 규칙이 들어 있습니다.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## 4단계: 문서에 글꼴 설정 적용

 구성된 것을 할당합니다`FontSettings`문서에. 이렇게 하면 문서를 렌더링할 때 글꼴 대체 규칙이 적용됩니다.

```csharp
doc.FontSettings = fontSettings;
```

## 5단계: 문서 저장

마지막으로 문서를 저장합니다. 글꼴 대체 설정은 저장 작업 중에 사용되어 적절한 글꼴 대체를 보장합니다.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML 파일: 글꼴 대체 규칙

다음은 글꼴 대체 규칙을 정의하는 XML 파일의 예입니다.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## 결론

이러한 단계를 따르면 Aspose.Words for .NET에서 글꼴 대체 설정을 효과적으로 설정하고 사용할 수 있습니다. 이렇게 하면 원래 글꼴이 특정 문자를 지원하지 않더라도 문서가 모든 문자를 올바르게 표시합니다. 이러한 설정을 구현하면 문서의 품질과 가독성이 크게 향상됩니다.

## 자주 묻는 질문

### 질문 1: 글꼴 대체 기능이란 무엇인가요?

글꼴 대체 기능은 원래 글꼴이 특정 문자를 지원하지 않을 때 글꼴을 대체하여 모든 텍스트 요소가 올바르게 표시되도록 보장하는 기능입니다.

### 질문 2: 대체 글꼴을 여러 개 지정할 수 있나요?

네, XML 규칙에서 여러 개의 대체 글꼴을 지정할 수 있습니다. Aspose.Words는 지정된 순서대로 각 글꼴을 확인하여 문자를 지원하는 글꼴을 찾을 때까지 확인합니다.

### 질문 3: Aspose.Words for .NET을 어디서 다운로드할 수 있나요?

 여기에서 다운로드할 수 있습니다[Aspose 다운로드 페이지](https://releases.aspose.com/words/net/).

### 질문 4: 글꼴 대체 규칙에 대한 XML 파일은 어떻게 만듭니까?

XML 파일은 모든 텍스트 편집기를 사용하여 만들 수 있습니다. 이 튜토리얼에서 제공하는 예제에 표시된 구조를 따라야 합니다.

### 질문 5: Aspose.Words에 대한 지원이 있나요?

 네, 다음에서 지원을 받을 수 있습니다.[Aspose.Words 지원 포럼](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
