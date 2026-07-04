---
category: general
date: 2026-05-23
description: Aspose.Words에서 글꼴 대체 경고를 포착하기 위해 경고 콜백을 설정합니다. LoadOptions, FontSettings
  및 IWarningCallback 구현에 대해 알아보세요.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: ko
og_description: Aspose.Words에서 글꼴 대체를 모니터링하기 위해 경고 콜백을 설정합니다. 이 튜토리얼에서는 LoadOptions,
  FontSettings 및 경고 핸들러 구현을 보여줍니다.
og_title: aspose 경고 콜백 설정 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Aspose 경고 콜백 설정 – 워드 문서 로딩 완전 가이드
url: /ko/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Word 문서 로딩을 위한 완전 가이드

한번이라도 **set warning callback aspose** 를 설정해서 폰트 대체 경고를 놓치지 않을 수 있는 방법이 궁금했나요? 당신만 그런 것이 아닙니다. DOCX 파일이 설치되지 않은 폰트를 참조하면 Aspose.Words 가 조용히 대체하고, 적절한 콜백이 없으면 무슨 변화가 있었는지 알 수 없습니다.

이 튜토리얼에서는 경고를 정확히 포착하는 전체 실행 가능한 예제를 단계별로 살펴봅니다. 끝까지 읽으면 **Aspose.Words LoadOptions** 에 대해 이해하고, **FontSettings** 를 구성하는 방법, 그리고 **IWarningCallback** 을 구현하는 것이 가장 깔끔하게 상황을 파악하는 방법임을 알게 됩니다. 불필요한 내용은 없습니다—오늘 바로 .NET 프로젝트에 넣어 사용할 수 있는 코드만 제공합니다.

## 배울 내용

- `LoadOptions` 인스턴스에 **set warning callback aspose** 를 설정하는 방법.  
- 문서를 열 때 **Aspose.Words LoadOptions** 가 수행하는 역할.  
- `FontSettings` 로 **Aspose fonts substitution** 처리를 구성하는 방법.  
- 폰트 문제를 기록하기 위한 맞춤형 **IWarningCallback 구현** 작성법.  
- **Aspose document loading** 모범 사례를 적용해 문서를 안전하게 로드하는 방법.

### 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.5+에서도 작동합니다).  
- 유효한 Aspose.Words for .NET 라이선스 또는 체험 키.  
- Visual Studio, Rider 또는 선호하는 C# 편집기.  
- 누락된 폰트를 참조하는 샘플 DOCX (`fontTest.docx`) (선택 사항이지만 도움이 됩니다).

> **Pro tip:** 누락된 폰트가 포함된 DOCX가 없으면, 문서 스타일에서 폰트 이름을 바꾸고 경고가 발생하는지 확인해 보세요.

---

## How to set warning callback aspose for document loading

아래는 완전하고 독립적인 프로그램 예시입니다. `Program.cs` 로 저장하고 NuGet 패키지를 복원한 뒤 실행하세요. 콘솔에 파일 로드 중 Aspose.Words 가 생성하는 모든 폰트 대체 경고가 출력됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### 예상 콘솔 출력

`fontTest.docx` 가 설치되지 않은 폰트를 참조하면 다음과 같은 내용이 표시됩니다:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

모든 폰트가 존재한다면 출력되는 유일한 문장은 *Document loaded successfully* 뿐이며, 경고나 잡음은 없습니다.

![set warning callback aspose 예시](image.png "set warning callback aspose 예시")

---

## Understanding LoadOptions in Aspose.Words

`LoadOptions` 는 **aspose document loading** 시 할 수 있는 모든 조정을 위한 관문입니다. 이를 통해 다음을 할 수 있습니다:

1. **사용자 지정 `FontSettings` 지정** – 애플리케이션에 자체 폰트를 포함할 때 유용합니다.  
2. **경고 콜백 연결** – 폰트 대체를 포착하기 위해 우리가 바로 사용한 방법입니다.  
3. 문서 형식 감지, 비밀번호 처리 등 기타 설정을 제어합니다.

`LoadOptions` 가 `Document` 생성자에 전달되기 때문에 설정은 **한 번**만 적용되어 파일이 파싱되는 순간에 바로 적용됩니다. 따라서 경고 핸들러가 메모리에 문서가 구축되기 전 모든 대체를 확인할 수 있음을 보장합니다.

### When to use a custom LoadOptions

- **다수 파일을 일괄 처리**하면서 일관된 로깅 전략이 필요할 때.  
- **클라우드 서비스**에서 누락된 폰트를 호출자에게 보고해야 할 때.  
- **테스트 파이프라인**에서 문서가 기업 폰트 정책을 준수하는지 검증할 때.

---

## Configuring FontSettings for Aspose fonts substitution

`FontSettings` 객체는 Aspose.Words 가 폰트를 해석하는 방식을 제어합니다. 기본적으로 시스템 폰트 폴더를 검색하고, 그 다음 내장 대체 폰트를 사용합니다. 이 동작을 세밀하게 조정할 수 있습니다:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

위 코드는 기본 “set warning callback aspose” 시나리오에 필수는 아니지만, 적절한 폰트를 미리 제공함으로써 대체 경고 수를 **줄일** 수 있음을 보여줍니다.

---

## Implementing IWarningCallback for font substitution warnings

`IWarningCallback` 인터페이스는 매우 작으며, 단 하나의 `Warning` 메서드만 포함합니다. 그러나 이를 통해 **경고 처리에 대한 완전한 제어**가 가능합니다:

- 콘솔 대신 **파일에 기록**.  
- 나중에 분석할 수 있도록 **리스트에 경고 수집**.  
- 중요한 경고(예: 필수 폰트 누락)에서는 **예외 발생**.

다음은 `List<string>` 에 경고를 저장하는 간단한 예시입니다:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

문서를 로드한 뒤 `handler.Messages` 를 검사하여 처리 중단 여부를 결정할 수 있습니다.

---

## Loading a document with custom warning handling (full workflow)

모든 요소를 합치면 다음과 같은 최종 패턴을 재사용하게 될 것입니다:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

이 스니펫은 **aspose document loading** 흐름을 보여줍니다—구성 → 로드 → 반응. 단일 파일을 처리하든 수천 개를 순회하든 패턴이 자연스럽게 확장됩니다.

---

## Common Questions & Edge Cases

**문서가 비밀번호로 보호되어 있다면 어떻게 하나요?**  
`LoadOptions` 초기화 구문에 `Password = "secret"` 를 추가하면 됩니다. 파일이 복호화된 뒤에도 경고 콜백은 정상 작동합니다.

**다른 유형의 경고에도 콜백이 호출되나요?**  
네—`WarningInfo.Type` 은 `DocumentStructure`, `UnsupportedFileFormat` 등 다양한 값을 가질 수 있습니다. 예제에서는 `FontSubstitution` 만 필터링했지만 `if` 조건을 제거하면 모든 경고를 기록할 수 있습니다.

**성능에 영향을 미치나요?**  
거의 영향을 주지 않습니다. 콜백은 경고가 발생할 때만 호출되므로 일반 파싱 단계보다 훨씬 적은 빈도로 실행됩니다.

**폰트 대체 기능을 완전히 비활성화할 수 있나요?**  
`fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` 로 설정하면 누락된 폰트에 대해 Aspose.Words 가 예외를 발생시키고 자동 대체는 수행되지 않습니다.

---

## Conclusion

이제 **set warning callback aspose** 를 사용해 **Aspose.Words LoadOptions** 처리 중 폰트 대체 이벤트를 모니터링하는 방법을 정확히 알게 되었습니다. `FontSettings` 를 구성하고 가벼운 `IWarningCallback` 을 구현한 뒤 해당 옵션으로 문서를 로드하면 Aspose 가 배경에서 수행하는 모든 폰트 변경을 완전히 파악할 수 있습니다.  

다음과 같은 활용이 가능합니다:

- 경고 핸들러를 중앙 로깅 서비스에 기록하도록 확장.  
- 콜백을 맞춤형 폰트 폴백 전략과 결합.  
- 클라이언트가 업로드한 문서를 검증하는 클라우드 API 구축 시 이 패턴 사용.

직접 DOCX 파일로 시도해 보고, `FontSettings` 를 조정하면서 콘솔이 어떤 폰트를 교체했는지 확인해 보세요. 즐거운 코딩 되시고, 문서가 항상 의도한 대로 렌더링되길 바랍니다!

## Related Tutorials

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}