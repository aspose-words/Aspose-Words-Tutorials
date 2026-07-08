---
category: general
date: 2026-07-06
description: Aspose.Words를 사용하여 손상된 docx 파일을 열려면 복구 모드를 활성화하십시오. 손상된 Word 문서를 빠르게
  복구하는 방법을 알아보세요.
draft: false
keywords:
- enable recovery mode
- recover corrupted word document
- recover damaged docx file
- how to open corrupted docx
language: ko
og_description: 복구 모드를 활성화하면 손상된 docx 파일을 열어 손상된 Word 문서를 복구하려 시도할 수 있습니다.
og_title: 복구 모드 활성화 – 손상된 Word 문서 복구
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Enable recovery mode to open a corrupted docx file with Aspose.Words.
    Learn how to recover corrupted Word document quickly.
  headline: Enable recovery mode – Recover corrupted Word document
  type: TechArticle
- questions:
  - answer: No. It only affects how the library reads the file in memory. The source
      remains untouched unless you explicitly call `Save`.
    question: Does enabling recovery mode modify the original file?
  - answer: Usually yes, as long as the underlying ZIP entry isn’t broken. If an image
      stream is missing, Aspose.Words will skip it and continue.
    question: Can I recover images that were embedded in the corrupted docx?
  - answer: Slightly, because the parser performs additional checks. The overhead
      is negligible for typical documents (<10 MB).
    question: Is recovery mode slower?
  - answer: '`RecoveryMode.Auto` (default) tries to recover only when an error occurs.
      `RecoveryMode.None` disables any recovery attempts. `RecoveryMode.Recover` forces
      the attempt every time. ## Full Working Example Below is a self‑contained console
      app you can copy‑paste into a new .NET project. It demonstrate'
    question: What other recovery options exist?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Document Recovery
- Word
title: 복구 모드 활성화 – 손상된 Word 문서 복구
url: /ko/net/programming-with-loadoptions/enable-recovery-mode-recover-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 복구 모드 활성화 – 손상된 Word 문서 복구

손상된 **docx** 파일을 열어보고 오류 대화 상자가 계속 나타나는 상황을 겪어본 적 있나요? 파일에 몇 주간의 작업이 들어있다면 정말 답답합니다. 다행히 Aspose.Words는 *복구 모드 활성화* 기능을 제공하여 수동으로 복사‑붙여넣기 하지 않고도 내용을 살릴 수 있습니다.

이 가이드에서는 **복구 모드 활성화** 단계, 손상된 파일 로드, 사용 가능한 복사본 저장까지 정확한 절차를 안내합니다. 끝까지 읽으면 프로그래밍 방식으로 *손상된 Word 문서 복구* 방법과 *손상된 docx 파일 복구* 상황을 우아하게 처리하는 방법을 알게 됩니다.

## 필요 사항

- .NET 6 (또는 최신 .NET 런타임) – 이 라이브러리는 .NET Framework에서도 작동합니다.
- Visual Studio 2022 또는 VS Code – 원하는 IDE면 충분합니다.
- **Aspose.Words for .NET** NuGet 패키지 (`Install-Package Aspose.Words`) – 이것이 유일한 외부 종속성입니다.
- 예시 손상된 `docx` 파일 (이 파일을 `corrupted.docx` 라고 부르겠습니다).

그게 전부입니다. 별도의 도구나 수동 XML 작업이 필요하지 않습니다. C# 몇 줄이면 충분합니다.

![Aspose.Words에서 복구 모드 활성화](image-url-placeholder.png)

*이미지 대체 텍스트: Aspose.Words에서 복구 모드 활성화*

## 단계 1: Aspose.Words 설치 및 프로젝트 설정

터미널(또는 Package Manager Console)을 열고 다음 명령을 실행합니다:

```bash
dotnet add package Aspose.Words
```

또는 Visual Studio에서 **Tools → NuGet Package Manager → Manage NuGet Packages**를 열고 *Aspose.Words*를 검색합니다. 설치가 완료되면 파일 상단에 네임스페이스를 추가합니다:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **팁:** 패키지를 최신 상태로 유지하세요. 복구 로직은 각 릴리스마다 개선됩니다.

## 단계 2: `LoadOptions`를 사용해 복구 모드 활성화

해결책의 핵심은 `LoadOptions` 클래스입니다. `RecoveryMode` 속성을 `RecoveryMode.Recover`로 설정하면 Aspose.Words에 문서를 파싱하는 동안 *복구 모드 활성화*를 지시하게 됩니다.

```csharp
// Step 2: Create LoadOptions and enable recovery mode
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover   // <-- this line turns on recovery
};
```

왜 중요한가요? 복구 모드가 없으면 Aspose.Words는 손상의 첫 징후에서 작업을 중단합니다. 복구 모드를 사용하면 라이브러리는 가능한 한 손상된 부분을 건너뛰고 여전히 사용 가능한 `Document` 객체를 생성하려고 시도합니다.

## 단계 3: 잠재적으로 손상된 파일 로드

이제 실제로 파일을 로드합니다. 문서가 복구 불가능할 경우에도 Aspose.Words는 `Document` 인스턴스를 반환하지만 일부 요소가 누락될 수 있습니다.

```csharp
// Step 3: Load the potentially corrupted document using the recovery options
Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
```

경로가 절대 문자열임을 확인하세요; 테스트 파일이 위치한 곳에 맞게 조정합니다. `Document` 생성자는 **복구 모드가 활성화된** 상태로 파일을 읽어 *손상된 Word 문서 복구* 기회를 제공합니다.

## 단계 4: 복구된 내용 확인 (선택 사항이지만 유용함)

무언가를 덮어쓰기 전에 로드된 문서를 검사하는 것이 좋은 습관입니다. 간단한 검증을 위해 첫 몇 개의 단락을 콘솔에 출력할 수 있습니다:

```csharp
// Optional: Print first 3 paragraphs to verify recovery
for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
{
    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
}
```

깨진 텍스트나 빈 문자열이 많이 보이면 파일이 **너무 손상**된 것일 수 있습니다. 그래도 이제 `Document` 객체를 가지고 있으니 헤더를 추가하거나 누락된 이미지를 교체하는 등 조작이 가능합니다.

## 단계 5: 복구된 문서 저장

검증 결과가 괜찮다면 복구된 버전을 새 파일에 저장합니다. 이 단계는 사실상 *손상된 docx 파일 복구*를 수행하며 Word에서 열 수 있는 깨끗한 복사본을 제공합니다.

```csharp
// Step 5: Save the recovered document
string outputPath = @"C:\Temp\recovered.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Recovered document saved to: {outputPath}");
```

원본 파일이 `.doc` 또는 다른 형식이라면 `SaveFormat`을 적절히 변경하면 됩니다(예: PDF 출력은 `SaveFormat.Pdf`).

## 단계 6: 예외 및 엣지 케이스 처리

복구 모드가 있더라도 일부 심각한 손상은 복구가 불가능합니다(예: 완전히 잘린 zip 구조). 이러한 문제를 드러내기 위해 로드를 try‑catch 블록으로 감싸세요:

```csharp
try
{
    Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
    // proceed with saving...
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to recover the document: {ex.Message}");
    // You might log the stack trace or notify the user.
}
```

일반적인 질문은 파일이 비밀번호로 보호된 경우 **“손상된 docx를 여는 방법”** 입니다. 복구 모드는 암호화를 우회하지 않으며, 여전히 비밀번호가 필요합니다. 이 경우 로드하기 전에 `LoadOptions.Password`를 설정하세요.

## 자주 묻는 질문 (FAQ)

**Q: 복구 모드 활성화가 원본 파일을 수정합니까?**  
A: 아닙니다. 라이브러리가 메모리에서 파일을 읽는 방식에만 영향을 줍니다. `Save`를 명시적으로 호출하지 않는 한 원본은 그대로 유지됩니다.

**Q: 손상된 docx에 포함된 이미지를 복구할 수 있나요?**  
A: 일반적으로 가능합니다. 기본 ZIP 엔트리가 손상되지 않은 경우에 한합니다. 이미지 스트림이 없으면 Aspose.Words가 이를 건너뛰고 진행합니다.

**Q: 복구 모드가 느려지나요?**  
A: 약간 느려집니다. 파서가 추가 검사를 수행하기 때문입니다. 일반적인 문서(<10 MB)에서는 오버헤드가 무시할 수준입니다.

**Q: 다른 복구 옵션은 무엇이 있나요?**  
A: `RecoveryMode.Auto`(기본값)는 오류가 발생했을 때만 복구를 시도합니다. `RecoveryMode.None`은 복구 시도를 전혀 하지 않습니다. `RecoveryMode.Recover`는 매번 복구를 강제로 시도합니다.

## 전체 작업 예제

아래는 새 .NET 프로젝트에 복사‑붙여넣기 할 수 있는 독립형 콘솔 앱 예제입니다. 패키지 설치부터 복구된 파일 저장까지 전체 흐름을 보여줍니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace RecoverCorruptedDocx
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the corrupted document
            string inputPath = @"C:\Temp\corrupted.docx";
            // Where the recovered file will be written
            string outputPath = @"C:\Temp\recovered.docx";

            // Step 1: Create LoadOptions and enable recovery mode
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Recover
            };

            try
            {
                // Step 2: Load the document with recovery enabled
                Document doc = new Document(inputPath, loadOptions);

                // Optional sanity check – print first three paragraphs
                Console.WriteLine("=== First three paragraphs after recovery ===");
                for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
                {
                    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
                }

                // Step 3: Save the recovered document
                doc.Save(outputPath, SaveFormat.Docx);
                Console.WriteLine($"\nRecovered document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to open or recover the document: {ex.Message}");
            }
        }
    }
}
```

**예상 출력 (복구가 성공했다고 가정):**

```
=== First three paragraphs after recovery ===
Paragraph 1: Project Overview
Paragraph 2: This document outlines...
Paragraph 3: ...

Recovered document saved to: C:\Temp\recovered.docx
```

파일이 복구 불가능하면 단락 덤프 대신 오류 메시지가 표시됩니다.

## 결론

우리는 이제 Aspose.Words에서 **복구 모드 활성화**하고 손상된 `docx`를 로드한 뒤 **손상된 Word 문서** 데이터를 새 파일로 **복구**하는 방법을 보여주었습니다. 동일한 패턴을 사용하면 배치 작업, 자동 이메일 첨부 파일 등에서 *손상된 docx 파일 복구*가 가능합니다.

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [docx 복구 방법 – 복구 모드 설정 및 손상된 Word 파일 열기](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Aspose.Words를 사용한 docx 복구 방법 – 단계별](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [손상된 Word 파일 복구 – 손상된 DOCX 열기 및 페이지 가져오기 완전 가이드](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}