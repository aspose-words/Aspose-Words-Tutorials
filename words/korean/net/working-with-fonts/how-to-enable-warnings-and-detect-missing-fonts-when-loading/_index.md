---
category: general
date: 2026-02-21
description: 경고를 활성화하고, 누락된 글꼴을 감지하며, Aspose.Words를 사용하여 C#에서 docx를 안전하게 로드하는 방법을
  배우세요. 단계별 가이드를 따라보세요.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: ko
og_description: Aspose.Words를 사용하여 경고를 활성화하고, 누락된 글꼴을 감지하며, docx 파일을 올바르게 로드하는 방법.
  전체 코드 예제가 포함되어 있습니다.
og_title: DOCX 로드 시 경고를 활성화하고 누락된 글꼴을 감지하는 방법
tags:
- C#
- Aspose.Words
- Document processing
title: DOCX 파일을 로드할 때 경고를 활성화하고 누락된 글꼴을 감지하는 방법
url: /ko/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX 파일을 로드할 때 경고를 활성화하고 누락된 글꼴을 감지하는 방법

문서 렌더링이 조용히 깨지는 것을 방지하기 위해 **누락된 글꼴에 대한 경고를 활성화하는 방법**을 궁금해 본 적이 있나요? 여러분만 그런 것이 아닙니다—대부분의 개발자는 라이브러리가 자동으로 “올바르게” 처리해 줄 것이라 생각하지만, 나중에 글꼴이 교체된 사실을 전혀 알지 못하게 됩니다.  

이 튜토리얼에서는 **경고를 활성화하는 방법**, **누락된 글꼴을 감지하는 방법**, 그리고 Aspose.Words for .NET을 사용하여 **docx를 로드하는 올바른 방법**을 정확히 보여드립니다. 마지막에는 모든 글꼴 교체 경고를 콘솔에 출력하는 실행 가능한 샘플을 제공하므로 파일 내부에서 무슨 일이 일어났는지 추측할 필요가 없습니다.

## Prerequisites

- .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 동작합니다)  
- Visual Studio 2022 또는 선호하는 C# IDE  
- **Aspose.Words** NuGet 패키지 (`Install-Package Aspose.Words`)  
- 머신에 설치되지 않은 글꼴이 포함될 수 있는 DOCX 파일 (여기서는 `input.docx`라고 부릅니다)

> **Pro tip:** 테스트 파일이 없으면, 커스텀 기업 글꼴을 사용하는 Word 문서를 열어 `input.docx`로 저장하세요. 그러면 우리가 캡처하려는 경고가 발생합니다.

## Overview of the solution

1. **Create** a `LoadOptions` object with `FontSubstitutionWarnings` turned on.  
2. **Load** the DOCX file using those options.  
3. **Inspect** the `WarningCallback` collection for any `FontSubstitution` entries.  
4. **React** – you might log, display, or even replace the missing font programmatically.

Below we break each step down, explain *why* it matters, and give you a complete, runnable code snippet.

---

## Step 1: Install Aspose.Words and set up the project

Before we can **how to enable warnings**, we need the library that actually supports them.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Or, in the Visual Studio Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Why this step?**  
> Without the package, the `LoadOptions`, `Document`, and warning infrastructure simply don’t exist. Adding the NuGet reference ensures you’re pulling the latest stable version (as of this writing, 24.5).

---

## Step 2: Create load options that enable font‑substitution warnings

The heart of **how to enable warnings** lives in the `LoadOptions` class. Setting `FontSubstitutionWarnings` to `true` tells the engine to record every time it has to replace a missing font.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Why enable this flag?**  
> By default Aspose.Words silently swaps missing fonts with a fallback (usually Arial). That can lead to layout shifts, invisible characters, or branding violations. Turning the flag on gives you full visibility.

---

## Step 3: Load the DOCX file using the configured options

Now that we know **how to load docx** with warnings turned on, we actually perform the load.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **What happens under the hood?**  
> While parsing the DOCX, Aspose.Words checks every `<w:rFonts>` element. If the specified font isn’t installed, it records a `FontSubstitution` warning and falls back to a default font. Because we enabled warnings, those entries end up in `document.WarningCallback.Warnings`.

---

## Step 4: Retrieve and display font substitution warnings

The `WarningCallback` property holds a `WarningInfoCollection`. Loop through it, filter for `WarningType.FontSubstitution`, and output the messages.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Expected output** (example):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **What to do with these messages?**  
> You might log them to a file, surface them in a UI, or even trigger a custom font‑fallback routine. The key is you now *detect missing fonts* instead of guessing later.

---

## Step 5: (Optional) Replace missing fonts with a specific fallback

If you have a corporate font that you want to enforce, you can handle the warnings and replace them on the fly.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Why consider this?**  
> It guarantees visual consistency across all generated documents, which is crucial for brand compliance.

---

## Full, runnable example

Below is a single C# file you can copy‑paste into a console app. It covers everything—from installing the package to printing warnings.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Run it**: `dotnet run` from the project folder. If any fonts are missing, you’ll see the warnings printed, and the optional replacement will be applied before the file is saved.

---

## Frequently asked questions

### Does this work with PDF conversion too?

Yes. After you’ve handled the warnings, you can call `doc.Save("output.pdf")` and the substituted fonts will appear in the PDF as they do in the DOCX.

### What if I need to suppress warnings for a specific font?

You can filter them out in the loop—just skip the `WarningInfo` whose `Message` contains the font name you want to ignore.

### Is `FontSubstitutionWarnings` available in older Aspose.Words versions?

It was introduced in version 20.5. If you’re stuck on an older release, upgrade via NuGet; the API change is backward‑compatible.

---

## Conclusion

We’ve walked through **how to enable warnings**, shown you **detect missing fonts**, and demonstrated the proper way **how to load docx** with Aspose.Words while keeping full visibility into font substitutions. By inspecting `document.WarningCallback.Warnings` you get a reliable audit trail—no more silent fallbacks.

Next steps? Try hooking the warning logic into a logging framework like Serilog, or build a UI that highlights missing fonts before you ship the document to users. You might also explore the `FontSettings` class for more granular control over font substitution policies.

Happy coding, and may your documents always render exactly as you intended! 

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}