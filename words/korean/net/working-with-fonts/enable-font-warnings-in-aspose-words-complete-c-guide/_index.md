---
category: general
date: 2026-04-01
description: Aspose.Words를 사용하여 Word 문서를 로드할 때 글꼴 경고를 활성화합니다. C# LoadOptions와 글꼴 설정을
  사용하여 글꼴 대체 이벤트를 포착하는 방법을 알아보세요.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: ko
og_description: Aspose.Words를 사용하여 Word 문서를 로드할 때 글꼴 경고를 활성화합니다. 이 튜토리얼에서는 C#에서 글꼴
  대체 이벤트를 캡처하는 방법을 보여줍니다.
og_title: Aspose.Words에서 글꼴 경고 활성화 – 완전한 C# 가이드
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose.Words에서 글꼴 경고 활성화 – 완전 C# 가이드
url: /ko/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 글꼴 경고 활성화 – 완전한 C# 가이드

프로그래밍으로 Word 문서를 로드했을 때 문서가 갑자기 다르게 보이는 이유가 궁금하셨나요? **글꼴 경고를 활성화**하면 Aspose.Words가 누락된 글꼴을 대체할 때 즉시 알 수 있습니다. 이번 튜토리얼에서는 이러한 대체를 포착할 뿐만 아니라 *왜* 발생하는지 설명하는 실습 예제를 단계별로 살펴보겠습니다.

필요한 NuGet 패키지, 정확한 `LoadOptions` 설정, 교체된 글꼴을 알려주는 깔끔한 콘솔 출력까지, 시작하는 데 필요한 모든 것을 다룹니다. 끝까지 따라오시면 어떤 버전의 Aspose.Words에서도 동작하는 **C# 문서 처리**용 견고하고 재사용 가능한 패턴을 갖추게 됩니다.

## 배울 내용

- 글꼴 변화를 추적하는 `LoadOptions` 인스턴스 생성 방법.  
- `SubstitutionWarning` 이벤트의 목적과 연결 방법.  
- 콘솔에 명확한 경고를 출력하는 완전한 실행 가능한 코드 샘플.  
- 표준 글꼴만 포함된 문서와 같은 엣지 케이스 처리 팁.  

Aspose.Words에 대한 사전 경험은 필요 없으며, C# 및 .NET에 대한 기본적인 이해만 있으면 됩니다.

---

![Enable font warnings diagram](placeholder-image.png "Enable font warnings diagram")
*Alt text: 누락된 글꼴이 대체될 때 이벤트 흐름을 보여주는 글꼴 경고 다이어그램.*

## 단계 1: LoadOptions 설정 및 글꼴 경고 활성화

먼저 `LoadOptions` 객체가 필요합니다. 이 컨테이너는 Aspose.Words에게 로드하려는 파일을 어떻게 처리할지 알려줍니다. 새 `FontSettings` 인스턴스를 할당하면 글꼴 관련 이벤트를 받을 수 있는 문을 엽니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**이것이 중요한 이유:**  
`FontSettings` 할당을 생략하면 Aspose.Words는 여전히 누락된 글꼴을 대체하지만, 알림을 받지 못합니다. 경고 메커니즘은 `FontSettings` 내부에 존재하므로 초기화가 *필수*입니다.

> **프로 팁:** `SetFontsFolder`를 사용해 `FontSettings`를 사용자 지정 글꼴 폴더에 연결할 수 있습니다. 이렇게 하면 누락된 글꼴을 실제로 찾을 수 있어 경고 수가 줄어듭니다.

## 단계 2: SubstitutionWarning 이벤트 구독 (글꼴 대체)

`FontSettings` 객체가 준비되었으니 이제 `SubstitutionWarning` 이벤트에 연결합니다. 이 이벤트는 Aspose.Words가 요청된 글꼴을 다른 글꼴로 교체할 **매번** 발생합니다.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**이것이 중요한 이유:**  
이 리스너가 없으면 대체 과정을 전혀 알 수 없습니다. 콘솔 라인은 빠른 감사 추적을 제공하므로 자동 빌드나 규제가 엄격한 산업 분야에서 PDF를 생성할 때 특히 유용합니다.

> **자주 묻는 질문:** *경고를 억제하고 싶다면?*  
> 핸들러를 분리하거나 `FontSettings.SubstitutionWarning += null;` 로 설정하면 됩니다. 하지만 경고를 유지하는 것이 일반적으로 안전합니다. 조용한 대체는 레이아웃 오류를 초래할 수 있기 때문입니다.

## 단계 3: 구성된 옵션으로 문서 로드 (C# 문서 처리)

경고 시스템이 준비되었으니 이제 문서를 로드합니다. `LoadOptions` 인스턴스를 `Document` 생성자에 전달하면 Aspose.Words가 나머지를 처리합니다.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**이것이 중요한 이유:**  
`LoadOptions` 객체는 원시 파일과 경고 인프라 사이의 다리 역할을 합니다. 이를 생략하면 문서는 조용히 로드되고, 누락된 글꼴은 흔적 없이 교체됩니다.

> **엣지 케이스:** 일부 문서는 필요한 정확한 글꼴 파일을 포함하고 있습니다. 이 경우 Aspose.Words가 포함된 글꼴을 찾아 경고가 표시되지 않습니다. 위 코드는 여전히 동작하지만 콘솔 출력은 비어 있게 됩니다.

## 단계 4: 출력 확인 및 일반적인 함정

명령 프롬프트나 IDE 디버거에서 프로그램을 실행합니다. 원본 문서에 머신에 설치되지 않았거나 사용자 지정 글꼴 폴더에 없는 글꼴이 포함되어 있으면 다음과 같은 라인이 표시됩니다:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

아무 것도 출력되지 않으면 다음 중 하나일 수 있습니다:

1. 모든 글꼴을 찾았음, **또는**  
2. `SubstitutionWarning` 핸들러가 올바르게 연결되지 않음 (단계 2를 다시 확인).

### 글꼴 대체가 발생하는 이유

- **시스템에 글꼴이 없음:** OS에 요청된 글꼴이 존재하지 않음.  
- **지원되지 않는 글꼴 형식:** Aspose.Words는 TrueType 및 OpenType을 읽을 수 있지만 모든 독점 형식은 지원하지 않음.  
- **라이선스 제한:** 일부 상용 글꼴은 임베딩을 차단해 대체 글꼴을 강제함.

*왜* 발생했는지를 이해하면 누락된 글꼴을 앱에 포함할지, 문서 스타일을 조정할지 결정하는 데 도움이 됩니다.

## 보너스: 대체 글꼴 제어

모든 누락된 글꼴을 특정 패밀리(예: “Calibri”)로 대체하고 싶다면 전역 대체 규칙을 설정합니다:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

이제 콘솔은 여전히 경고를 표시하지만, 시각적인 결과는 모든 누락된 글꼴에 대해 일관되게 유지됩니다.

---

## 요약

- 새 `FontSettings`와 함께 `LoadOptions`를 만들어 **글꼴 경고를 활성화**합니다.  
- `SubstitutionWarning` 이벤트를 연결해 글꼴이 교체될 때 실시간 알림을 받습니다.  
- 구성된 옵션으로 문서를 로드하고, 필요시 PDF로 저장해 시각적 효과를 확인합니다.  
- 대체가 발생한 원인을 진단하고, 필요하면 특정 대체 글꼴을 강제합니다.

이제 **Aspose.Words** 워크플로에 안전망을 추가해 조용한 레이아웃 변화를 방지했습니다. 다음 단계로 `DefaultFontName` 같은 **글꼴 설정**이나 **문서 렌더링** 옵션을 탐색해 PDF 출력 품질을 미세 조정해 보세요.

---

### 다음에 시도해 볼 내용

- **다른 FontSettings 기능 탐색**: `SetFontsFolder`, `LoadFontSources`, `DefaultFontName`.  
- **경고와 로깅 프레임워크 결합** (Serilog, NLog)으로 프로덕션 수준 진단 구현.  
- **다양한 문서 형식 실험** (`.doc`, `.rtf`, `.html`)하여 각각이 누락된 글꼴을 어떻게 처리하는지 확인.  

질문이나 특이한 상황이 있나요? 아래 댓글에 남겨 주세요. 즐거운 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}