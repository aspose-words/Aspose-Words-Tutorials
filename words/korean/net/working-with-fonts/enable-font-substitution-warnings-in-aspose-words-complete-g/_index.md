---
category: general
date: 2026-01-11
description: .NET 문서에서 누락된 글꼴을 감지하려면 글꼴 대체 경고를 활성화하십시오. Aspose.Words를 사용하여 누락된 글꼴
  이름을 가져오고 누락된 글꼴 목록을 확인하는 방법을 알아보세요.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: ko
og_description: Aspose.Words에서 글꼴 대체 경고를 활성화하여 누락된 글꼴을 감지하고, 누락된 글꼴 이름을 가져오며, 문서에
  누락된 글꼴을 나열합니다.
og_title: 글꼴 대체 경고 활성화 – 단계별 C# 튜토리얼
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words에서 글꼴 대체 경고 활성화 – 완전 가이드
url: /ko/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 폰트 대체 경고 활성화 – 완전 가이드

서버에 워드 문서를 올렸을 때 약간 어색하게 보인 적이 있나요? 원본 작성자가 사용한 폰트가 현재 머신에 없어서 Aspose.Words가 조용히 가장 근접한 폰트로 교체했기 때문일 가능성이 높습니다. **폰트 대체 경고를 활성화**하면 어떤 폰트가 누락되었고, 무엇으로 대체되었는지, 그리고 그 정보를 어떻게 활용해야 하는지 즉시 알 수 있습니다.

이 튜토리얼에서는 **누락된 폰트 감지**, **누락된 폰트 이름 가져오기**, 그리고 **누락된 폰트 목록 출력**을 보여주는 실용적인 엔드‑투‑엔드 예제를 단계별로 살펴보겠습니다. 불필요한 내용 없이 바로 .NET 프로젝트에 적용할 수 있는 명확한 솔루션을 제공합니다.

---

## 배울 내용

- `LoadOptions`를 구성하여 Aspose.Words가 상세 경고를 내보내도록 하는 방법
- 문서를 로드하고 폰트 관련 경고를 열거하는 정확한 코드
- 누락된 폰트 이름과 대체 폰트를 추출하고 깔끔한 보고서를 출력하는 방법
- 수십 개의 누락된 폰트가 있는 문서나 사용자 지정 폰트 폴더와 같은 엣지 케이스 처리 팁

### 사전 요구 사항

- .NET 6+ (코드는 .NET Framework 4.7+에서도 동작합니다)
- Aspose.Words for .NET 23.10 이상 (NuGet에서 가져올 수 있습니다)
- 설치되지 않은 폰트를 참조하는 샘플 DOCX 파일 (`MissingFont.docx` 라고 부르겠습니다)

위 기본 사항을 갖추었다면 바로 시작해 보세요.

---

## Step 1: Set Up LoadOptions to Enable Font Substitution Warnings  

먼저 Aspose.Words에 누락된 폰트에 관심이 있음을 알려야 합니다. 기본적으로 라이브러리는 내부적으로만 경고를 기록합니다. `SubstitutionWarningLevel`을 `Typical`(또는 가장 자세한 출력을 원한다면 `All`)로 설정하면 스위치가 켜집니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**왜 중요한가:**  
`SubstitutionWarningLevel`이 설정되면 Aspose.Words가 참조된 폰트를 찾지 못할 때마다 `FontSubstitutionWarning`을 문서의 `Warnings` 컬렉션에 추가합니다. 이 컬렉션은 문서를 직접 파싱하지 않고도 **누락된 폰트를 감지**할 수 있는 유일한 신뢰할 수 있는 방법입니다.

> **프로 팁:** 여러 문서를 한 번에 처리하면서 모든 대체를 확실히 잡아내고 싶다면 `FontSubstitutionWarningLevel.All`을 사용하세요. 다소 시끄럽지만 경고가 빠지는 경우가 없습니다.

---

## Step 2: Load the Document Using the Configured Options  

경고 시스템이 준비되었으니, 앞서 만든 `LoadOptions`를 사용해 DOCX를 로드합니다. 경로는 절대 경로나 상대 경로나 상관없으며, 파일이 존재하는지만 확인하면 됩니다.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**내부에서 무슨 일이 일어나나요?**  
Aspose.Words는 문서의 XML을 파싱하고 각 `<w:font>` 요소를 해석한 뒤 시스템 폰트 카탈로그(및 `FontSettings`에 추가한 사용자 지정 폴더)를 확인합니다. 폰트를 찾지 못하면 경고를 기록합니다—이것이 나중에 **누락된 폰트 목록을 출력**하는 데 필요한 바로 그 정보입니다.

---

## Step 3: Iterate Over Warnings and Extract Missing Font Details  

문서가 메모리에 로드되면 `Warnings` 컬렉션에 모든 `FontSubstitutionWarning`이 들어 있습니다. 이를 순회하면서 원하는 타입만 필터링하고 친절한 보고서를 출력합니다.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**예상 출력** (소스 문서가 설치되지 않은 `MyCustomFont`를 참조한다고 가정):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

각 항목이 **누락된 폰트 이름**(`MyCustomFont`)과 대체 폰트(`Arial`)를 모두 제공하는 것을 확인할 수 있습니다. 바로 이 정보가 원본 폰트를 임베드할지, 작성자에게 교체를 요청할지, 아니면 대체를 그대로 받아들일지 결정하는 데 필요합니다.

---

## Step 4: Optional – Collect the Data into a List for Further Processing  

보고서를 CSV로 내보내거나 API로 전송하거나 메모리에 보관하고 싶다면, 경고 정보를 강타입 리스트에 저장할 수 있습니다.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

이제 **누락된 폰트 목록**을 downstream 시스템이 바로 사용할 수 있는 형태로 갖게 되었습니다. 대시보드에 연결하거나 감사 로그를 생성하는 등 다양한 용도로 활용하세요.

---

## Step 5: Handling Edge Cases and Common Pitfalls  

### Multiple Missing Fonts in a Single Run  

대기업 템플릿은 종종 수십 개의 사용자 지정 폰트를 참조합니다. 경고 컬렉션이 커질 수 있지만, 앞서 보여준 순회 방식은 선형적으로 확장되므로 성능에 큰 영향을 주지 않습니다. 출력이 가독성을 유지하도록 페이지별이나 스타일별로 그룹화하면 더 깊은 분석에 도움이 됩니다.

### Custom Font Folders  

비표준 디렉터리(예: 공유 네트워크 드라이브)에 폰트를 보관한다면 Aspose.Words에 해당 위치를 알려야 합니다:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

문서를 로드하기 **전에** 이 설정을 하면 라이브러리가 폰트를 찾아낼 수 있어 일부 경고를 완전히 없앨 수 있습니다.

### Suppressing Specific Warnings  

특정 대체가 허용 가능한 경우(예: 장식용 폰트를 교체해도 괜찮을 때)에는 나중에 해당 경고를 필터링할 수 있습니다:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Version Compatibility  

`FontSubstitutionWarningLevel` 열거형은 Aspose.Words 20.12부터 안정적으로 제공됩니다. 오래된 버전을 사용 중이라면 경고 레벨 기능을 사용하려면 업그레이드가 필요합니다.

---

## Full Working Example  

아래는 앞서 설명한 모든 단계를 포함한 완전 실행 가능한 프로그램입니다. 새 콘솔 프로젝트에 붙여넣고 Aspose.Words NuGet 패키지를 추가한 뒤, `docPath`를 누락된 폰트를 참조하는 문서로 지정하면 됩니다.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

이 프로그램을 실행하면 **폰트 대체 경고를 활성화**하고, **누락된 폰트를 감지**하며, **누락된 폰트 이름을 가져오고**, **누락된 폰트 목록을** 콘솔과 CSV 파일 모두에 출력합니다.

---

## Conclusion  

Aspose.Words에서 **폰트 대체 경고를 활성화**하는 방법을 초기 설정부터 누락된 폰트 목록 추출까지 모두 다뤘습니다. 위 단계들을 따르면 문서를 감사하고 시각적 일관성을 보장하며, 서버에서 렌더링할 때 발생할 수 있는 불쾌한 서프라이즈를 방지할 수 있습니다.

다음 단계로 고려해볼 내용:

- **누락된 폰트를 PDF 또는 DOCX에 직접 임베드** (`FontSettings.EmbeddedFonts` 사용)
- **빌드 에이전트에 자동 폰트 설치**를 보고서 기반으로 구현
- **CI 파이프라인과 통합**하여 중요한 폰트가 없을 경우 빌드 실패 처리

시도해 보시고, 단순 경고 시스템을 완전한 폰트 관리 워크플로우로 확장해 보세요.

행복한 코딩 되시길, 그리고 모든 폰트를 찾을 수 있기를 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}