---
category: general
date: 2026-01-03
description: Aspose.Words에서 글꼴을 감지하고 Aspose 글꼴 설정을 사용하여 경고를 처리하는 방법 – 개발자를 위한 단계별
  가이드.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: ko
og_description: Aspose.Words에서 글꼴을 감지하고 Aspose 글꼴 설정으로 경고를 구성하는 방법. 몇 분 안에 전체 워크플로를
  배워보세요.
og_title: Aspose.Words에서 글꼴 감지 방법 – 경고 처리
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words에서 글꼴 감지 방법 – 경고 및 설정 처리
url: /ko/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 글꼴 감지하기 – 경고 및 설정 처리

프로덕션에 배포하기 전에 **워드 문서의 글꼴을 감지**하는 방법이 궁금하셨나요? 여러분만 그런 것이 아닙니다. 글꼴이 없으면 레이아웃이 엉망이 되고, 적절한 경고 없이 깨진 PDF나 DOCX를 배포할 수도 있습니다.  

이 튜토리얼에서는 Aspose.Words를 사용해 **글꼴을 감지**하는 방법을 살펴보고, **경고를 처리**하는 방법과 **Aspose 글꼴 설정**을 조정해 **경고를 원하는 대로 구성**하는 방법을 보여드립니다. 마지막에는 Aspose가 수행하는 모든 대체 작업을 출력하는 실행 가능한 스니펫을 제공하고, 이를 여러분의 프로젝트에 적용하는 방법도 알려드립니다.

## 필수 조건

- .NET 6+ (또는 .NET Framework 4.6+).  
- NuGet을 통해 설치한 Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- 의도적으로 누락된 글꼴을 참조하는 워드 파일 (예: *DocumentWithMissingFonts.docx*).  

이미 준비가 되었다면, 바로 시작해 보겠습니다.

![how to detect fonts screenshot](https://example.com/detect-fonts.png "how to detect fonts example output")

## Aspose.Words로 글꼴 감지하기

첫 번째 단계는 Aspose.Words에 글꼴 대체 이벤트에 관심이 있음을 알려주는 것입니다. 이는 **Aspose 글꼴 설정**을 통해 사용자 정의 경고 콜백을 제공함으로써 이루어집니다. 콜백은 각 대체에 대해 `WarningInfo` 객체를 받아 **런타임에 글꼴을 감지**할 수 있게 합니다.

### 1단계: 경고 콜백 클래스 생성

`IWarningCallback` 인터페이스를 구현합니다. `Warning` 메서드 안에서 `WarningType.FontSubstitution`을 필터링하고 세부 정보를 로그에 기록합니다.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Pro tip:** `info.Description` 문자열에는 누락된 글꼴 이름과 Aspose가 선택한 대체 글꼴이 모두 포함됩니다. 구조화된 보고서가 필요하면 파싱할 수 있습니다.

### 2단계: Aspose 글꼴 설정을 사용하여 LoadOptions 구성

`LoadOptions` 인스턴스를 만들고, 새 `FontSettings` 객체를 연결한 뒤, `WarningCallback`을 방금 만든 핸들러에 지정합니다. 이렇게 하면 Aspose에 **경고를 어떻게 구성할지** 알려줍니다.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

개인 글꼴 폴더가 있다면 다음과 같이 추가할 수 있습니다:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

이 라인은 **Aspose 글꼴 설정**의 또 다른 측면을 보여줍니다—Aspose가 대체를 수행하기 전에 글꼴을 검색할 위치를 정확히 제어할 수 있습니다.

### 3단계: 문서 로드 및 콜백 실행

이제 `loadOptions`를 사용해 대상 문서를 로드합니다. Aspose가 파일을 파싱하면서 누락된 글꼴이 발견될 때마다 경고 핸들러가 호출되어 **실시간으로 글꼴을 감지**합니다.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

프로그램을 실행하면 다음과 유사한 출력이 표시됩니다:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### 4단계: (선택 사항) 추후 사용을 위해 경고 수집

보고서를 위해 대체 데이터를 저장해야 한다면, 핸들러를 수정해 메시지를 리스트에 누적합니다.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

이후 `handler.Substitutions`를 JSON 파일로 저장하거나 로깅 서비스에 전송하거나 UI에 표시할 수 있습니다.

### 5단계: 프로그램적으로 결과 검증

때때로 *대체가 전혀 발생하지 않았는지*를 CI 빌드에서 확인하고 싶을 때가 있습니다. 간단한 검증 코드는 다음과 같습니다:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

이 스니펫은 **경고를 처리**하는 방법을 결정론적으로 보여주며, 빌드 파이프라인에 대한 완전한 제어권을 제공합니다.

## 자주 묻는 질문 (및 예외 상황)

**특정 대체를 무시하고 싶다면?**  
`Warning` 내부에 조건문을 추가하고, 허용 가능한 글꼴에 대해서는 로그를 남기지 않고 바로 반환하면 됩니다.

**모든 경고를 억제하고 불리언 결과만 받고 싶다면?**  
`loadOptions.WarningCallback = null` 로 설정한 뒤, 로드 후 `doc.FontInfo` 를 검사하면 됩니다(하지만 상세 로그는 사라집니다).

**PDF 변환에도 적용되나요?**  
물론입니다. `doc.Save("out.pdf")` 를 호출할 때도 동일한 경고 메커니즘이 작동합니다. 콜백은 변환 단계에서 발생하는 모든 글꼴 교체를 포착합니다.

**성능에 영향을 미치나요?**  
오버헤드는 최소 수준이며, 누락된 글꼴당 몇 번의 메서드 호출만 추가됩니다. 대량 배치 처리 시 결과를 캐시하는 것이 좋습니다.

## 요약: 다룬 내용

- 사용자 정의 `IWarningCallback`을 구현해 **글꼴을 감지**하는 방법.  
- `LoadOptions.WarningCallback`을 통해 **경고를 처리**하는 방법.  
- **Aspose 글꼴 설정**을 조정하는 방법(사용자 정의 글꼴 폴더 추가, 경고 활성/비활성화).  
- 즉시 콘솔 출력과 사후 분석을 모두 지원하도록 **경고를 구성**하는 방법.  

이러한 요소들을 갖추면 워드 문서를 자신 있게 처리하고, 누락된 글꼴을 정확히 표시하며, 환경 간 출력 일관성을 유지할 수 있습니다.

## 다음 단계

- `FontSettings.SubstitutionSettings` 를 탐색해 보다 세밀한 제어(예: 특정 누락 글꼴을 지정된 대체 글꼴에 매핑)를 시도해 보세요.  
- 이 접근 방식을 Aspose.PDF와 결합해 정확한 타이포그래피를 유지하는 PDF를 생성하세요.  
- CI/CD 파이프라인에 경고 검사를 자동화해 글꼴 문제가 있는 릴리스를 차단하세요—품질 게이트의 일환으로 **경고를 처리**하는 팀에 최적입니다.

**Aspose 글꼴 설정**에 대해 추가 질문이 있거나 더 큰 서비스에 통합하는 데 도움이 필요하면 아래 댓글로 알려 주세요. 즐거운 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}