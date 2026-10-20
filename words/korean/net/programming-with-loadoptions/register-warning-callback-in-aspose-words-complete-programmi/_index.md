---
category: general
date: 2026-06-27
description: Aspose.Words에서 경고 콜백을 등록하여 글꼴 대체 및 로딩 문제를 포착합니다. Aspose.Words와 함께 LoadOptions의
  단계별 사용법을 배우세요.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: ko
og_description: Aspose.Words에서 경고 콜백을 등록하여 글꼴 대체 및 기타 로드 경고를 모니터링합니다. 견고한 구현을 위한 전체
  튜토리얼을 확인하세요.
og_title: Aspose.Words에서 경고 콜백 등록 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Aspose.Words에서 경고 콜백 등록 – 완전 프로그래밍 가이드
url: /ko/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 경고 콜백 등록 – 완전 프로그래밍 가이드

문서를 로드할 때 어떤 글꼴이 교체되는지 정확히 확인하고 싶으신가요? 많은 개발자들이 조용히 이루어지는 글꼴 대체 때문에 생성된 PDF나 Word 파일의 레이아웃이 깨지는 문제에 부딪히곤 합니다.  

이 튜토리얼에서는 **Aspose.Words에서 경고 콜백을 등록**하는 실전 솔루션을 단계별로 살펴보고, *왜* 이를 사용해야 하는지, 콜백이 내부에서 어떻게 동작하는지, 그리고 마주칠 수 있는 엣지 케이스들을 설명합니다. 끝까지 따라오시면 모든 글꼴 교체를 로그에 남기고, 다른 로딩 경고도 포착하며, 문서 처리 파이프라인을 투명하게 만들 수 있습니다.

## 배울 내용

- **LoadOptions** 를 설정해 문서 로딩 동작을 제어하는 방법  
- 글꼴 교체 및 기타 경고 유형에 대해 **경고 콜백**을 등록하는 방법  
- 설정한 옵션으로 DOCX를 로드하고 콜백 출력을 해석하는 방법  
- 흔히 겪는 함정(누락된 글꼴, 사용자 정의 글꼴 폴더, 성능 고려사항)  

**전제 조건:** Visual Studio 2022(또는 기타 C# IDE), .NET 6+ 런타임, 그리고 활성 Aspose.Words 라이선스(무료 체험판으로 실험 가능). `Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

---

![Diagram illustrating the flow of registering a warning callback in Aspose.Words and handling font substitution warnings](register-warning-callback-aspose-words.png "register warning callback aspose.words diagram")

## 1단계: LoadOptions 생성 – 경고 처리를 위한 진입점  

콜백이 실행되려면 먼저 **LoadOptions** 인스턴스를 만들어야 합니다. 이는 “이 파일을 로드하되, 문제가 있으면 알려줘” 라는 요청을 Aspose.Words에 전달하는 제어판과 같습니다.  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **이것이 중요한 이유:** `LoadOptions` 를 통해 암호 비밀번호부터 글꼴 디렉터리까지 모든 것을 조정할 수 있습니다. 이 객체에 경고 콜백을 연결하면 무음 처리 과정을 관찰 가능한 과정으로 바꿀 수 있습니다.

## 2단계: 경고 콜백 등록 – 글꼴 교체 포착  

이제 주인공인 **경고 콜백**을 등록합니다. Aspose.Words 가 로딩 중 발생하는 모든 경고에 대해 호출하는 익명 메서드(람다)를 등록합니다. 콜백 내부에서 `WarningType.FontSubstitution` 을 필터링하고 친절한 메시지를 출력합니다.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **프로 팁:** 누락된 이미지나 지원되지 않는 기능도 로그에 남기고 싶다면 `args.WarningType` 을 검사하는 `if` 분기를 추가하세요. 이렇게 하면 **Aspose.Words에서 경고 콜백 등록** 구현이 모든 로딩 진단을 한 번에 처리합니다.

## 3단계: 구성한 LoadOptions 로 문서 로드  

콜백을 연결했으니 이제 문서를 로드하기만 하면 됩니다. `loadOptions` 인스턴스를 `Document` 생성자에 전달합니다. Aspose.Words 가 찾지 못한 글꼴을 만날 때마다 콜백이 실행되어 콘솔에 출력됩니다.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

프로그램을 실행하면 다음과 유사한 출력이 나타납니다:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

이것이 **Aspose.Words에서 경고 콜백 등록**의 핵심—어떤 프로젝트에서도 재사용 가능한 3단계 패턴입니다.

## 4단계: 실제 시나리오에 맞게 콜백 확장  

### 4.1 콘솔 대신 파일에 로그 기록  

운영 환경에서는 콘솔 스팸을 원하지 않습니다. `Console.WriteLine` 을 로거(예: `Serilog`, `NLog`) 혹은 텍스트 파일 쓰기로 교체하세요:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 사용자 정의 글꼴 디렉터리 제공  

기업 전용 글꼴을 사용한다면, Aspose.Words 가 대체에 들어가기 전에 해당 폴더를 지정해 주세요:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

이제 엔진이 올바른 글꼴을 찾게 되므로 콜백이 **덜** 호출될 수 있습니다.

### 4.3 비글꼴 경고 처리  

로드 경고 전체를 포착하도록 범위를 넓힐 수 있습니다:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## 5단계: 구현 테스트 – 기대 결과  

### 5.1 누락된 글꼴이 있는 문서로 검증  

머신에 설치되지 않은 글꼴(예: Linux 서버에서 “Comic Sans MS”)을 참조하는 작은 DOCX 를 만들고 로더를 실행하세요. 교체 메시지가 표시되어야 합니다.  

### 5.2 오버헤드 벤치마크  

콜백은 거의 무시할 수준의 오버헤드(경고당 몇 마이크로초)를 추가합니다. 수천 개 문서를 로드한다면 로그를 배치 처리하거나 비핵심 실행에서는 콜백을 비활성화하는 것이 좋습니다.

### 5.3 엣지 케이스  

- **동일 글꼴에 대한 다중 교체:** 동일한 누락 글꼴이 여러 페이지에 나타나면 콜백이 여러 번 호출될 수 있습니다. 필요하면 로거에서 중복을 제거하세요.  
- **암호화된 문서:** DOCX 가 비밀번호로 보호된 경우 `loadOptions.Password` 도 설정해야 합니다. 복호화 후에도 콜백은 정상 작동합니다.  
- **비동기 로딩:** API 자체는 동기이지만 `Task.Run` 으로 로드 호출을 감싸면 백그라운드 처리에 사용할 수 있습니다. 콜백은 스레드 안전합니다.

## 흔히 겪는 함정 & 해결 방법  

| 함정 | 발생 원인 | 해결 방법 |
|------|----------|----------|
| **출력이 전혀 없음** | 콜백을 할당하지 않았거나 `WarningCallback` 이 나중에 덮어쓰기된 경우 | 로드하기 **전** 콜백을 **한 번** 할당하고, 할당 후 `loadOptions` 를 다시 재설정하지 않도록 합니다. |
| **잘못된 형변환 예외** | `FontSubstitutionWarningInfo` 가 아닌 다른 경고를 캐스팅하려 할 때 | 항상 `args.WarningType` 을 확인한 뒤에 캐스팅합니다. |
| **성능 저하** | 느린 I/O 대상에 동기식 로그를 기록할 때 | 비동기 로깅 프레임워크를 사용하거나 버퍼링하여 기록합니다. |
| **사용자 정의 글꼴 누락** | `FontSettings` 에 글꼴 폴더를 추가하지 않은 경우 | 4.2 단계와 같이 `SetFontsFolder` 를 추가합니다. |

## 전체 동작 예제 – 복사‑붙여넣기만 하면 실행  

아래 코드는 새 콘솔 앱 프로젝트에 그대로 복사해 넣을 수 있는 완전한 프로그램입니다. 시작부터 끝까지 흐름을 보여줍니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**예상 콘솔 출력**(누락된 글꼴이 있을 경우):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

프로그램을 실행하면 Aspose.Words 가 교체한 글꼴을 정확히 확인할 수 있어, 로딩 과정을 완전히 투명하게 파악할 수 있습니다.

---

## 결론  

우리는 **Aspose.Words에서 경고 콜백을 등록하는 방법**, 이를 문서 처리 워크플로우에 적용해야 하는 이유, 그리고 로깅, 사용자 정의 글꼴, 광범위한 경고 처리 등으로 패턴을 확장하는 방법을 살펴보았습니다. 단 세 줄의 코드만으로 블랙박스 로드 작업을 감사 가능하고 디버깅 가능한 단계로 바꿀 수 있습니다—이제 레이아웃이 신비롭게 변하는 일은 없습니다.

다음 단계는 무엇일까요? 이 콜백을 **Aspose.Words SaveOptions** 와 결합해 로드와 저장 모두에서 경고를 기록하거나, 실시간 업로드를 처리하는 웹 API에 연결해 보세요. 또한 여기서 소개한 보조 키워드(예: *loadoptions font substitution warning*) 를 활용해 성능을 미세 조정하거나 모니터링 대시보드와 통합할 수 있습니다.

궁금한 점이나 어려운 상황이 있나요? 댓글로 알려 주세요. 함께 해결해 봅시다. 즐거운 코딩 되시고, PDF 가 항상 올바른 글꼴로 렌더링되길 바랍니다!


## 다음에 배울 내용


아래 튜토리얼들은 이번 가이드에서 다룬 기술을 기반으로 하여 관련 주제를 심도 있게 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하므로, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}