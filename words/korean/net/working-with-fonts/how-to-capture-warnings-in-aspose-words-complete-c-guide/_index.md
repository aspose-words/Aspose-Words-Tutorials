---
category: general
date: 2026-03-28
description: Aspose.Words로 DOCX를 로드할 때 경고를 포착하고 누락된 글꼴에 대한 경고 메시지를 받는 방법. 누락된 글꼴을
  효율적으로 처리하는 방법을 배워보세요.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: ko
og_description: Aspose.Words로 DOCX를 로드할 때 경고를 캡처하고, 경고 메시지를 확인하며, 누락된 글꼴을 실용적인 코드
  예제로 처리하는 방법.
og_title: Aspose.Words에서 경고 캡처하는 방법 – 완전한 C# 가이드
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words에서 경고를 캡처하는 방법 – 완전한 C# 가이드
url: /ko/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 경고 캡처하기 – 완전 C# 가이드

Aspose.Words로 Word 문서를 로드할 때 나타나는 **경고를 캡처하는 방법**이 궁금하셨나요? 글꼴이 이상하게 바뀌는 현상을 보고 정확히 왜 그런지 알고 싶을 때가 있죠. 간단히 말해, 라이브러리의 경고 시스템에 훅을 걸어 **경고 메시지를 얻고**, 레이아웃을 망치기 전에 **누락된 글꼴을 처리**할 수 있습니다.  

이 튜토리얼에서는 실제 시나리오를 따라가며 DOCX를 로드하고 엔진이 발생시키는 모든 경고를 수집한 뒤, 발생한 글꼴 대체에 대한 상세 정보를 출력합니다. 마지막에는 바로 실행 가능한 코드 샘플을 제공하고, 각 단계의 “왜”를 이해하며, 여러분의 프로젝트에 적용할 수 있는 방법을 알려드립니다.

## 배울 내용

- `LoadOptions`를 설정해 경고를 자동으로 캡처하는 방법.  
- `WarningInfoCollection`에서 **경고 메시지를 얻는** 정확한 방법.  
- `WarningType.FontSubstitution` 플래그를 통해 **누락된 글꼴을 식별하고 대응**하는 방법.  
- 임베디드 글꼴이나 사용자 지정 글꼴 폴더가 있는 문서와 같은 엣지 케이스를 해결하는 팁.  

외부 참고 자료는 필요 없습니다 – 여기서 바로 모든 것을 확인할 수 있습니다.

---

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 동작합니다).  
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`).  
- 일부 글꼴이 없거나 머신에 설치되지 않은 글꼴을 사용하는 샘플 DOCX (`input.docx`).  

이것만 있으면 됩니다. C#과 Visual Studio에 익숙하다면 코드를 복사‑붙여넣기만 하면 바로 실행할 수 있습니다.

---

## 1단계: 로드 옵션 및 경고 콜백 준비

`new Document(path, loadOptions)`를 호출하면 Aspose.Words는 파일을 파싱합니다. 파싱 중에 누락된 글꼴, 지원되지 않는 기능, 폐기된 마크업 등을 마주칠 수 있습니다. 이러한 이벤트를 잡으려면 **경고 콜백** 객체가 필요합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**왜 중요한가요:** 콜백이 없으면 Aspose.Words는 경고를 콘솔에 조용히 기록하거나 버립니다. 따라서 레이아웃에 영향을 줄 수 있는 글꼴 대체를 전혀 알 수 없습니다. 전용 `WarningInfoCollection`을 제공하면 모든 경고를 완전히 가시화할 수 있습니다.

> **프로 팁:** 글꼴 관련 경고만 관심 있다면 나중에 필터링하면 되지만, *모든* 경고를 수집해 두면 향후 문제에 대비할 수 있는 안전망이 됩니다.

---

## 2단계: 구성된 옵션으로 문서 로드

콜백이 준비됐으니 이제 파일을 로드합니다. `Document` 생성자는 발견된 문제마다 자동으로 콜백을 호출합니다.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**내부에서 무슨 일이 일어나나요?** Aspose.Words는 Open XML을 파싱하고, 스타일을 해석하며, 각 글꼴 참조를 시스템에 설치된 글꼴과 매핑하려고 시도합니다. 매치가 없으면 `FontSubstitution` 유형의 `WarningInfo` 항목을 생성합니다.

---

## 3단계: 수집된 경고 가져오기 및 검사

로드가 완료되면 `warningCollector`에 발생한 모든 경고가 들어 있습니다. 이를 꺼내어 글꼴 대체 메시지만 집중해서 살펴보겠습니다.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**샘플 출력** (콘솔에 다음과 비슷하게 표시될 수 있습니다):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

모든 경고가 필요하면 `if` 조건을 제거하거나 각 항목에 대해 `warning.Type`을 로그에 남기면 됩니다.

---

## 4단계: 누락된 글꼴 처리 – 단순 로그 이상

경고를 캡처하는 것만으로도 유용하지만, 실제로 **누락된 글꼴을 프로그래밍적으로 처리**해야 할 때가 많습니다. 여기 두 가지 일반적인 전략을 소개합니다:

### 4.1 특정 폰트로 누락된 글꼴 교체

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

이제 누락된 글꼴은 라이브러리 기본 폰트 대신 *Calibri*로 교체됩니다.

### 4.2 대체 글꼴을 동적으로 임베드

맞춤 글꼴 파일(예: `MyFallback.ttf`)이 있다면 런타임에 등록할 수 있습니다:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

특정 기업 글꼴을 애플리케이션과 함께 배포할 때 유용한 방법입니다.

> **엣지 케이스:** 문서에 이미 필요한 글꼴이 임베드되어 있으면 시스템 대체 규칙이 무시됩니다. 이 경우 해당 글꼴에 대한 경고 컬렉션은 비어 있게 되며, 이것이 바로 원하는 동작입니다.

---

## 5단계: 전체 작동 예제 (복사‑붙여넣기 가능)

아래는 시작부터 끝까지 모든 과정을 보여주는 독립 실행형 프로그램입니다. `YOUR_DIRECTORY/input.docx`를 테스트 파일 경로로 바꾸기만 하면 됩니다.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**예상 결과**

- 콘솔에 글꼴 대체 경고가 경고 이모지와 함께 출력됩니다.  
- 출력 DOCX(`output.docx`)는 누락된 글꼴이 감지된 모든 위치에서 *Calibri*를 사용합니다.  
- 예외가 발생하지 않으며, 경고 시스템이 모든 알 수 없는 글꼴을 부드럽게 처리합니다.

---

## 자주 묻는 질문 & 답변

**Q: Word에서 생성된 PDF에도 적용되나요?**  
A: 네. Aspose.Words는 PDF를 또 다른 출력 형식으로 취급합니다. 경고 캡처는 *로드* 단계에서 이루어지므로 최종 내보내기와는 무관합니다.

**Q: 모든 문서 작업(저장, 변환 등)에서 경고를 캡처하려면 어떻게 하나요?**  
A: 문서 인스턴스화 후 `Document.WarningCallback`에 동일한 `WarningInfoCollection`을 할당하면 됩니다. 이후 수행되는 모든 작업이 같은 컬렉션에 새로운 항목을 추가합니다.

**Q: 경고 콜백이 성능에 영향을 주나요?**  
A: 거의 없습니다. 컬렉션은 단순히 객체를 저장할 뿐이며, 수천 개의 경고를 아주 짧은 루프에서 처리하지 않는 한 눈에 띄는 지연을 느끼지 못합니다.

**Q: 관심 없는 경고는 어떻게 억제하나요?**  
A: `IWarningCallback`을 상속한 커스텀 클래스를 구현하고 `Warning` 메서드 내부에서 필터링하면 됩니다. 기본 제공 `WarningInfoCollection`은 저장만 할 뿐 필터링은 하지 않습니다.

---

## 프로 팁 & 함정

- **프로 팁:** `Warning.Description`을 항상 확인하세요 – 누락된 정확한 글꼴 이름이 들어 있습니다. 이를 통해 해당 글꼴을 앱에 포함시킬지 결정할 수 있습니다.  
- **임베디드 글꼴 주의:** 원본 DOCX에 필요한 글꼴이 이미 임베드돼 있으면 Aspose.Words는 대체 경고를 발생시키지 않으며, 로컬에 설치되지 않아도 무시됩니다.  
- **스레드 안전성:** `WarningInfoCollection`은 스레드‑안전하지 않습니다. 여러 문서를 동시에 로드한다면 각 스레드마다 별도의 컬렉션을 사용하세요.  
- **버전 확인:** 경고 API는 Aspose.Words 20.8 이후 안정화되었습니다. 최신 버전을 사용해 최신 경고 유형을 놓치지 않도록 하세요.

---

## 결론

우리는 **Aspose.Words에서 경고를 캡처하는 방법**을 다루고, **경고 메시지를 얻는 방법**을 시연했으며, **누락된 글꼴을 대체 글꼴이나 사용자 지정 폰트 폴더**를 통해 처리하는 실용적인 방안을 제시했습니다. 전체 예제는 어떤 .NET 프로젝트에도 바로 삽입할 수 있으며, 개념은 더 큰 자동화 파이프라인에도 확장됩니다.

다음 단계로 고려해볼 내용:

- `Document.WarningCallback`을 사용해 **저장** 작업 중에도 경고를 캡처하기.  
- 경고를 파일이나 텔레메트리 시스템에 기록해 프로덕션 모니터링에 활용하기.  
- 콜백을 확장해 브랜드 전용 글꼴을 자동으로 적용하도록 만들기.

실험해 보세요—대체 글꼴을 바꾸거나, 배치에 문서를 추가하거나, CI 파이프라인에 경고 수집기를 통합해 글꼴 관련 회귀를 감지할 수 있습니다. 즐거운 코딩 되시고, 문서가 언제나 기대한 대로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}