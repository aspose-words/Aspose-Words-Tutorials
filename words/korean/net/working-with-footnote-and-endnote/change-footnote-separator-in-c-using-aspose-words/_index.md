---
category: general
date: 2026-08-04
description: Aspose.Words를 사용한 C#에서 각주 구분자 변경 – Word 문서에서 각주 구분자를 편집하고 미주 구분자를 변경하는
  방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: ko
lastmod: 2026-08-04
og_description: Aspose.Words를 사용하여 C#에서 각주 구분자를 변경합니다. 이 가이드는 각주 구분자를 편집하고, 미주 구분자를
  사용자 정의하며, 업데이트된 문서를 저장하는 방법을 보여줍니다.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: C#에서 각주 구분자 변경 – 전체 Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: C#에서 Aspose.Words를 사용하여 각주 구분자 변경
url: /ko/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 Aspose.Words를 사용하여 각주 구분자 변경하기

Word 문서에서 **각주 구분자 변경**이 필요하다면, 이 튜토리얼은 Aspose.Words for .NET을 사용한 정확한 단계별 방법을 안내합니다. 기본 선을 기호로 교체하거나, 미주 구분자에 다른 스타일을 적용하고 싶을 때도 아래 코드는 전체 워크플로우를 다룹니다.

또한 **각주 구분자 편집** 및 관련 **미주 구분자 변경** 작업을 배우게 되어, 동일한 문서에서 각주와 미주 모두 일관된 스타일을 적용할 수 있습니다. 외부 도구는 필요 없으며, C# 몇 줄만 있으면 됩니다.

## 달성할 목표

이 가이드를 마치면 다음을 수행할 수 있습니다:

* 각주와 미주가 포함된 기존 *.docx* 파일을 로드합니다.  
* 각주, 각주 연속, 그리고 미주에 대한 구분자 노드를 접근합니다.  
* 구분자 문자를 교체합니다(예: 기본 선을 별표(*)로 변경).  
* 다른 콘텐츠는 손상되지 않도록 수정된 문서를 저장합니다.  

본 튜토리얼은 C# 기본 지식이 있으며 **Aspose.Words** NuGet 패키지(버전 24.9 이상)가 설치되어 있다고 가정합니다.  

---

## 전제 조건

| 요구 사항 | 이유 |
|-------------|--------|
| .NET 6.0+ 또는 .NET Framework 4.7.2+ | Aspose.Words 실행에 필요한 런타임 |
| Aspose.Words for .NET 라이브러리 | `Document` 및 `FootnoteOptions` API 제공 |
| 최소 하나의 각주 또는 미주가 포함된 입력 Word 파일(`input.docx`) | 구분자 변경을 시연하기 위함 |

다음 CLI 명령으로 Aspose.Words를 프로젝트에 추가할 수 있습니다:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Step 1: 각주가 포함된 문서 로드

첫 번째 작업은 소스 파일을 `Document` 객체로 읽어들이는 것입니다. 이 객체는 전체 Word 파일을 메모리에 나타내며 모든 노드에 접근할 수 있게 해줍니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**왜 중요한가:** 문서를 로드하는 것이 모든 조작의 시작점입니다. 파일을 찾을 수 없으면 Aspose.Words가 `FileNotFoundException`을 발생시키므로, 진행하기 전에 경로가 올바른지 확인하세요.

---

## Step 2: 각주 및 미주 구분자 노드 접근

`Document.FootnoteOptions`는 세 개의 구분자 노드를 노출합니다:

* `Separator` – 첫 페이지 각주 컬렉션 뒤에 나타나는 선.  
* `ContinuationSeparator` – 각주가 다음 페이지로 이어질 때 사용되는 선.  
* `EndnoteSeparator` – 본문 텍스트와 미주 목록을 구분하는 선.

이 노드들을 일반 `Node` 객체로 가져온 뒤 `Run`으로 캐스팅하여 텍스트를 수정합니다.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**왜 중요한가:** 시각적 구분자 문자는 이 노드들에만 존재합니다. 다른 노드(예: 일반 단락)를 변경해도 각주 서식에는 영향을 주지 않습니다.

---

## Step 3: 각주 구분자 문자 변경

가장 흔한 요구는 기본 선을 별표(`*`)와 같은 기호로 교체하는 것입니다. 구분자는 `Run`으로 저장되므로 `Text` 속성을 안전하게 수정할 수 있습니다.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**왜 중요한가:** `Run.Text`를 직접 편집하면 다른 각주 내용에 영향을 주지 않고 최종 문서의 시각적 표현을 업데이트할 수 있습니다. 동일한 패턴으로 Unicode 기호를 포함한 어떤 문자열도 적용할 수 있습니다.

---

## Step 4: 미주 구분자 변경 (선택 사항)

**미주 구분자도 변경**해야 한다면, 절차는 각주 변경과 동일합니다. `endnoteSeparator`의 텍스트를 원하는 문자로 교체하면 됩니다.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**왜 중요한가:** 미주는 각주와 스타일이 다르게 지정되는 경우가 많습니다. 별도의 구분자를 제공하면 문서 디자인 가이드라인에 맞는 시각적 일관성을 유지할 수 있습니다.

---

## Step 5: 수정된 문서 저장

모든 수정이 끝났으면 `Document.Save`를 사용해 변경 사항을 영구 저장합니다. 원본 파일을 덮어쓰거나 새 위치에 저장할 수 있습니다.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**왜 중요한가:** `Save`는 메모리상의 표현을 디스크에 기록하므로, 스타일, 이미지, 표 등 다른 요소는 그대로 유지됩니다.

---

## 전체 실행 가능한 예제

모든 코드를 하나로 모은 자체 포함 콘솔 애플리케이션 예제는 다음과 같습니다:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**예상 결과:** Microsoft Word에서 *ModifiedSeparators.docx*를 열면 첫 번째 각주 페이지 하단의 각주 구분자 선이 이제 별표(`*`) 하나로 표시됩니다. 문서에 미주가 포함된 경우, 본문과 미주 목록을 구분하는 선은 대시(`-`)로 표시됩니다. 텍스트, 이미지, 표 등 다른 모든 콘텐츠는 그대로 유지됩니다.

---

## 일반적인 질문 및 엣지 케이스 처리

| 질문 | 답변 |
|----------|--------|
| **문서에 각주가 전혀 없으면 어떻게 되나요?** | `FootnoteOptions.Separator`는 여전히 `Run` 노드를 반환하지만 텍스트가 비어 있을 수 있습니다. 코드는 노드 유형을 안전하게 확인한 뒤 수정합니다. |
| **다중 문자 문자열(예: "***")을 사용할 수 있나요?** | 가능합니다. `Run.Text` 속성은 Unicode 문자를 포함한 모든 문자열을 허용합니다. |
| **구분자를 변경해도 기존 각주 번호 매김에 영향을 주나요?** | 영향을 주지 않습니다. 구분자는 번호 매김 체계와 독립적입니다. |
| **`Document` 객체를 명시적으로 해제해야 하나요?** | `Document`는 `Node`를 통해 암묵적으로 `IDisposable`을 구현합니다. 짧은 수명의 콘솔 앱에서는 선택 사항이지만, 장시간 실행 서비스에서는 `using` 블록으로 감싸는 것이 좋습니다. |
| **.NET Core와 .NET Framework에서 동작 방식이 다른가요?** | API는 런타임에 관계없이 동일합니다. 다만 대상 프레임워크 버전이 Aspose.Words 패키지에서 지원되는지 확인하면 됩니다. |

**팁:** 섹션마다 다른 구분자를 적용해야 한다면 `doc.GetChildNodes(NodeType.Footnote, true)`를 순회하면서 각 각주의 `Separator` 속성을 개별적으로 조정할 수 있습니다. 이는 고급 기능이지만 복잡한 문서에 유용합니다.

---

## 결론

이제 C#과 Aspose.Words를 사용해 Word 파일의 **각주 구분자 변경** 및 **미주 구분자 변경** 방법을 알게 되었습니다. 문서 로드, 관련 구분자 노드 접근, 텍스트 수정, 저장까지 한 번에 수행하는 자체 포함 프로그램을 살펴보았습니다.

이후에는 **각주 구분자 스타일 편집**, 각주 번호 매김 사용자 정의, 페이지 레이아웃 기반 조건부 서식 적용 등 관련 주제를 탐색해 볼 수 있습니다. 동일한 패턴(노드 가져오기 → `Run`으로 캐스팅 → `Text` 수정)은 다양한 Word 처리 시나리오에 적용됩니다.

즐거운 코딩 되시고, 다양한 기호를 실험하거나 심지어 이미지를 구분자로 삽입해 독특한 문서 레이아웃을 만들어 보세요!

## 다음에 배울 내용

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하며, 밀접하게 관련된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공해 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 다양한 구현 방식을 탐색하도록 돕습니다.

- [각주 및 미주 처리하기](/words/english/net/working-with-footnote-and-endnote/)
- [Word 문서에서 단락 스타일 구분자 가져오기](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Word에 문서 스타일 구분자 삽입](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}