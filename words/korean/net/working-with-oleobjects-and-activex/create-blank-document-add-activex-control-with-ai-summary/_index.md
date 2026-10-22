---
category: general
date: 2026-10-16
description: 빈 문서를 만든 다음 C#에서 AI를 활용해 텍스트를 요약·번역하면서 ActiveX 컨트롤을 추가합니다. 하나의 완전한 예제로
  Word 문서를 저장합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add activex control
- summarize document with ai
- translate text to spanish
- save word document
language: ko
lastmod: 2026-10-16
og_description: 빈 문서를 만들고 ActiveX 컨트롤을 추가한 뒤 AI를 사용해 텍스트를 요약하고 번역합니다. 최종 Word 문서를
  하나의 워크플로우로 저장합니다.
og_image_alt: Screenshot of a create blank document with an ActiveX CommandButton
  inserted
og_title: 빈 문서를 만들고 C#에서 AI 요약이 포함된 ActiveX 컨트롤을 추가합니다
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create blank document and add ActiveX control while using AI to summarize
    and translate text in C#. Save the Word document with one complete example.
  headline: Create blank document, add ActiveX control with AI summary
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI
- ActiveX
title: 빈 문서 만들기, AI 요약이 포함된 ActiveX 컨트롤 추가
url: /ko/net/working-with-oleobjects-and-activex/create-blank-document-add-activex-control-with-ai-summary/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 문서를 만들고 AI 요약이 포함된 ActiveX 컨트롤 추가

**빈 문서를 만들고** 인터랙티브 요소를 삽입해야 할 경우, 이 가이드는 **ActiveX 컨트롤을 추가**하고, **AI 요약기**를 실행하며, **텍스트를 스페인어로 번역**하고, 마지막으로 **Word 문서를 저장**하는 방법을 보여줍니다. Aspose.Words, Aspose.Words.AI 및 필요한 클라우드 키를 활용하는 완전한 실행 가능한 C# 프로그램을 확인할 수 있습니다.

이 튜토리얼은 프로젝트 설정부터 결과 검증까지 모든 단계를 다룹니다. 외부 문서는 전혀 필요하지 않으며—코드를 복사하고, 자리표시자 키를 교체한 뒤 실행하면 됩니다. 끝까지 진행하면 각 API 호출이 왜 중요한지, 일반적인 함정은 어떻게 처리하는지, 그리고 다른 언어나 컨트롤에 솔루션을 확장하는 방법을 이해하게 됩니다.

## 필요 사항

- .NET 6.0 이상 (.NET Framework 4.7+에서도 작동)
- 유효한 Aspose.Words 라이선스 (전체 기능 사용 시 선택 사항)
- 요약기를 위한 OpenAI API 키
- 번역기를 위한 Google Cloud Translation API 키
- Visual Studio 2022 또는 선호하는 C# IDE

## 빈 문서를 만들고 Aspose.Words 초기화

첫 번째 작업은 **빈 문서를 만들기**입니다. Aspose.Words는 `Document` 클래스를 제공하며, 이는 조작이 가능한 빈 Word 파일을 나타냅니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Fields;
using Aspose.Words.AI;
using Aspose.Words.AI.Summarizer;
using Aspose.Words.AI.Translator;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```


## 다음에 배울 내용은?


다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 동작 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고, 자체 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Summarize Word Document in C# with Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}