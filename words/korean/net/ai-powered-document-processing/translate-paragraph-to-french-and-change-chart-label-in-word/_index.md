---
category: general
date: 2026-10-10
description: 단락을 프랑스어로 번역하고, 차트 데이터 레이블을 변경 및 사용자 지정하며, Aspose.Words AI를 사용해 편집된 docx
  파일을 저장하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: ko
lastmod: 2026-10-10
og_description: 문단을 프랑스어로 번역하고 차트 데이터 레이블을 변경하는 방법, 차트 데이터 레이블을 사용자 정의하는 방법, 그리고 Aspose.Words
  AI를 사용하여 편집된 docx 파일을 저장하는 방법을 배워보세요.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: 단락을 프랑스어로 번역하고 Word에서 차트 레이블을 변경하기
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: 단락을 프랑스어로 번역하고 Word에서 차트 레이블을 변경하기
url: /ko/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 문단을 프랑스어로 번역하고 Word에서 차트 레이블 변경

문단을 **프랑스어로 번역**하면서 동일한 Word 문서 안에 차트도 업데이트해야 할 경우, 이 가이드는 정확한 방법을 보여줍니다. Aspose.Words AI를 사용하면 텍스트를 자동으로 번역하고 차트의 데이터 레이블을 수정한 뒤 편집된 `.docx` 파일을 몇 단계만에 저장할 수 있습니다.

이 튜토리얼은 파일 로드부터 변경 사항 저장까지 모든 과정을 다룹니다. 최종적으로 어떤 문단이든 번역하고, 차트 데이터 레이블을 사용자 지정하며, 배포 가능한 새로운 Word 파일을 생성할 수 있게 됩니다. 외부 스크립트는 필요 없으며, 전체 워크플로는 단일 C# 프로그램 안에서 실행됩니다.

## 사전 요구 사항

- .NET 6.0 이상 (.NET Framework 4.7+에서도 동작)
- Aspose.Words for .NET 라이선스(또는 무료 평가 키)
- Google AI 번역기를 사용하기 위한 인터넷 연결(`Translator` 클래스가 내부적으로 Google API를 호출)
- 최소 하나의 문단과 하나의 차트를 포함한 Word 문서(`input.docx`)

## 1단계: 프로젝트 설정 및 네임스페이스 가져오기

새 콘솔 애플리케이션을 만들고 Aspose.Words NuGet 패키지를 추가합니다:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

이제 `Program.cs` 상단에 필요한 네임스페이스를 포함합니다:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

이 임포트들을 통해 문서 로드, AI 번역 및 차트 편집 기능을 사용할 수 있습니다.

## 2단계: 원본 Word 문서 로드

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

파일을 로드하면 원본 파일을 건드리지 않고 메모리 상에서 조회 및 수정이 가능한 객체가 생성됩니다.

## 3단계: 첫 번째 문단을 프랑스어로 번역

첫 번째 문단은 보통 제목이나 소개 문장으로, 번역 대상에 적합합니다. `Translator` 클래스가 Google AI 모델 호출을 추상화합니다.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**동작 원리:**  
`paragraph.Runs.Clear()`는 기존 텍스트 런을 모두 제거해 새 번역이 기존 내용과 연결되지 않도록 합니다. `new Run(document, translatedText)`는 문단의 서식을 그대로 물려받는 새로운 런을 생성합니다.

## 4단계: 첫 번째 차트를 찾아 데이터 레이블 사용자 지정

차트는 `NodeType.Shape` 타입의 `Shape` 노드로 저장됩니다. 첫 번째 차트는 `GetChild` 메서드로 가져올 수 있습니다.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**핵심 단계 설명:**

- `GetChild(NodeType.Shape, 0, true)`는 깊이 우선 탐색을 수행해 첫 번째 `Shape`(즉, 차트)를 반환합니다.
- `ChartSeries`는 데이터 포인트 컬렉션을 나타내며, 첫 번째 시리즈(`Series[0]`)는 일반적으로 기본 데이터 세트를 의미합니다.
- `ChartDataLabelPosition.OutsideEnd`는 레이블을 막대 끝 바깥쪽으로 이동시켜 가독성을 높입니다.
- `dataLabel.Text`에 프랑스어 문자열을 지정하면 레이블이 번역된 문단과 일치합니다.

## 5단계: 번역된 문단을 포함해 문서 저장

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

이 시점에서 문서는 프랑스어 문단을 포함하지만 차트 구성은 아직 원본 그대로입니다.

## 6단계: 업데이트된 차트와 함께 문서 저장

같은 `Document` 인스턴스를 재사용하면 다시 로드할 필요가 없습니다. 차트 수정 내용이 이미 메모리에 반영되어 있기 때문입니다.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

두 파일 모두 배포 준비가 완료되었습니다:

- **`translated.docx`** – 프랑스어 문단이 포함된 파일
- **`chart-updated.docx`** – 프랑스어 문단과 사용자 지정 차트 레이블이 모두 포함된 파일

## 전체 실행 가능한 예제

아래는 `Program.cs`에 복사·붙여넣기 할 수 있는 전체 프로그램입니다. `YOUR_DIRECTORY`를 실제 폴더 경로로 교체하면 바로 컴파일·실행됩니다.



## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 도와줍니다.

- [차트 데이터 레이블 사용자 지정](/words/english/net/programming-with-charts/chart-data-label/)
- [차트 데이터 레이블의 숫자 서식 지정](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [차트 데이터 레이블](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}