---
category: general
date: 2026-09-05
description: 전체 C# 예제를 통해 그룹 도형 docx를 만들고, ActiveX 명령 버튼을 삽입하며, Markdown을 Word 문서에
  로드하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: ko
lastmod: 2026-09-05
og_description: C#를 사용해 그룹 형태 docx를 만들고 ActiveX 명령 버튼을 삽입한 뒤, Markdown을 Word 문서에 로드합니다.
  단계별 튜토리얼을 따라 보세요.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: 그룹 도형 docx 만들기 및 ActiveX 컨트롤 삽입 – C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: C#에서 그룹 도형 DOCX를 만들고 인터랙티브 컨트롤을 추가하는 방법
url: /ko/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 그룹 도형 docx 만들기 및 인터랙티브 컨트롤 추가 방법

프로그래밍 방식으로 **create group shape docx** 파일을 만들어야 한다면, 이 가이드가 정확히 방법을 보여줍니다. 또한 **insert ActiveX command button** 컨트롤과 **load Markdown into a Word document** 를 언더라인 서식을 잃지 않고 삽입하는 방법도 확인할 수 있습니다. 튜토리얼을 마치면 벡터 그래픽, 인터랙티브 UI 요소, 마크다운 기반 콘텐츠를 결합한 완전한 `.docx` 파일을 얻게 됩니다.

이 튜토리얼은 기본적인 C# 개발 환경과 Aspose.Words for .NET 라이브러리가 설치되어 있다고 가정합니다. 외부 도구는 필요하지 않으며, 모든 작업은 표준 .NET 콘솔 또는 데스크톱 애플리케이션 내에서 실행됩니다.

## 사전 요구 사항

- .NET 6.0 SDK 또는 그 이후 버전 (코드는 .NET Framework 4.7+에서도 작동합니다)
- Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`)
- 서명 단계를 테스트하려면 유효한 X.509 인증서(`.pfx`)
- 알려진 폴더에 배치된 이미지 파일(예: `logo.png`) 및 마크다운 파일(`sample.md`)

> **Pro tip:** 모든 입력 파일을 단일 *resources* 폴더에 보관하면 상대 경로를 단순화할 수 있습니다.

## 단계 1: 프로젝트 설정 및 네임스페이스 가져오기

새 콘솔 프로젝트를 만들고 필요한 `using` 지시문을 추가합니다. 이 블록은 나중에 사용할 Aspose.Words 클래스를 참조하는 방법도 보여줍니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

`using` 문은 튜토리얼 전반에 걸쳐 사용되는 `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` 등 타입에 직접 접근할 수 있게 해줍니다.

## 단계 2: **Create group shape docx** – 자식 요소가 포함된 그룹 도형 추가

*그룹 도형*은 여러 개의 그리기 객체를 하나의 단위로 다룰 수 있게 해줍니다. 관련 그래픽을 함께 이동하거나 크기를 조정할 때 유용합니다.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**왜 그룹 도형인가?**  
그룹화하면 사용자가 Word에서 사각형과 타원을 끌어다 놓을 때 정렬이 유지됩니다. 또한 공통 테두리를 적용하거나 전체 그래픽을 프로그래밍 방식으로 이동하는 등 이후 작업을 단순화합니다.

## 단계 3: 일반 텍스트 콘텐츠 컨트롤 삽입 (사용자 입력용 플레이스홀더)

콘텐츠 컨트롤은 최종 사용자에게 텍스트를 입력할 구조화된 영역을 제공합니다. 사용자가 입력을 시작하면 플레이스홀더 텍스트가 사라집니다.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

`PlaceholderName` 속성은 Word가 밝은 회색 힌트로 표시하는 내용입니다. 사용자는 이를 자신의 텍스트로 교체할 수 있으며, 기본 XML은 올바른 형태를 유지합니다.

## 단계 4: **Insert ActiveX command button** – 문서에 인터랙티브 UI 추가

ActiveX 컨트롤은 최신 Word 파일에서도 여전히 지원되며 매크로나 외부 자동화를 트리거할 수 있습니다. 아래에서는 *command button*을 추가하고 캡션을 설정합니다.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**ActiveX 버튼을 언제 사용하나요?**  
VBA 매크로에 의존하는 기업 환경에 문서를 배포한다면, ActiveX 버튼으로 매크로를 실행하거나 외부 애플리케이션을 시작할 수 있습니다. 순수 HTML 기반 인터랙티브를 원한다면 *content controls*와 *Office.js*를 사용하는 것을 고려하세요.

## 단계 5: 숨겨진 이미지 삽입 (예: 로고) – 브랜딩 또는 이후 스크립트 접근용

숨겨진 도형은 인쇄된 문서에 표시되지 않지만 XML에 남아 있어 이후에 프로그래밍 방식으로 가져올 수 있습니다.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## 단계 6: **Load markdown into a Word document** – 언더라인 서식 보존

Aspose.Words는 마크다운을 직접 가져올 수 있습니다. `ImportUnderlineFormatting`을 활성화하면 마크다운 언더라인(` <u>` 또는 `__text__`)이 일반 텍스트가 아니라 Word 언더라인 스타일로 변환됩니다.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**예외 상황:** 마크다운 파일에 표가 포함되어 있으면 자동으로 Word 표로 변환됩니다. 사용자 지정 표 스타일이 필요하면 삽입 후 `DocumentBuilder`를 사용해 적용하세요.

## 단계 7: XAdES‑EPES로 문서 서명 (선택적 보안 단계)

디지털 서명은 문서 무결성을 보장합니다. 다음 코드는 **create group shape docx** 파일을 XAdES‑EPES 프로파일로 서명합니다.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Security note:** 인증서 비밀번호를 소스 컨트롤에 포함시키지 마세요. 프로덕션에서는 환경 변수나 보안 금고를 사용하세요.

## 전체 실행 가능한 예제

모든 단계를 합치면 단일 독립형 프로그램이 됩니다. 파일을 `Program.cs`로 저장하고 명령줄에서 실행하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Running the program generates `CompleteGroupShape.docx` containing:

- 그룹화된 사각형 + 타원 (the **create group shape docx** core)
- 플레이스홀더 텍스트가 있는 일반 텍스트 콘텐츠 컨트롤
- “Click Me” 라벨이 붙은 **insert ActiveX command button**
- 숨겨진 로고 이미지
- 언더라인이 보존된 마크다운 콘텐츠
- XAdES‑EPES 디지털 서명 (인증서가 제공된 경우)

## 일반적인 질문 및 문제 해결

| Question | Answer |
|---|---|
| **ActiveX 버튼이 macOS Word에서 작동합니까?** | macOS Word는 ActiveX 컨트롤을 지원하지 않습니다. 버튼은 정적 이미지로 표시됩니다. 크로스 플랫폼 인터랙티브를 위해서는 Office.js와 함께 콘텐츠 컨트롤을 사용하세요. |
| **마크다운 파일에 사용자 정의 CSS가 포함된 경우는 어떻게 하나요?** | Aspose.Words는 CSS를 무시하고 표준 마크다운 구문만 처리합니다. CSS로 스타일링된 요소는 가져온 후 수동으로 Word 스타일로 변환해야 합니다. |
| **나중에 같은 그룹에 더 많은 도형을 추가할 수 있나요?** | 예. `GroupShape`를 이름이나 인덱스로 가져온 다음 `AppendChild(newShape)`를 호출하면 됩니다. 수정 후에는 문서를 다시 저장하는 것을 잊지 마세요. |
| **서명 알고리즘을 어떻게 변경하나요?** | `Sign`을 호출하기 전에 `signature.SignatureAlgorithm`을 설정하세요. 기본값은 SHA‑256이며 대부분의 규정 요구사항을 충족합니다. |
| **숨겨진 이미지가 Word UI에 보이나요?** | 아니요, 하지만 Word 옵션에서 *Show hidden text*를 켜면 표시할 수 있습니다. 레이아웃을 어지럽히지 않고 메타데이터를 저장하는 데 유용합니다. |

## 다음 단계

이제 **create group shape docx**, **insert ActiveX command button**, **load markdown into a Word document** 를 할 수 있게 되었으니, 다음을 탐색해 볼 수 있습니다:

- **Embedding VBA macros**: ActiveX 버튼 클릭에 반응하도록 매크로를 삽입합니다.
- **Applying custom styles**: 마크다운으로 생성된 단락에 사용자 정의 스타일을 적용합니다.
- **Generating PDFs**: `doc.Save("output.pdf", SaveFormat.Pdf)`를 사용해 동일한 문서에서 PDF를 생성합니다.
- **Automating batch processing**: 여러 마크다운 파일을 하나의 종합 보고서로 배치 처리 자동화합니다.

이러한 확장을 통해 풍부한 그래픽, 인터랙티브 컨트롤, 마크다운 기반 저작을 결합한 완전 자동화 문서 파이프라인을 C#만으로 구축할 수 있습니다.

---

*행복한 코딩 되세요! 이 튜토리얼을 찾았다면

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [C#을 사용하여 Word에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Word에서 마크다운 만들기 – 완전한 C# 가이드](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}