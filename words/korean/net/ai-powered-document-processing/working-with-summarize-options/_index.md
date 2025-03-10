---
title: 요약 옵션 사용
linktitle: 요약 옵션 사용
second_title: Aspose.Words 문서 처리 API
description: 단계별 가이드를 통해 AI 모델을 통합하여 빠른 통찰력을 얻고, Aspose.Words for .NET을 사용하여 Word 문서를 효과적으로 요약하는 방법을 알아보세요.
weight: 10
url: /ko/net/ai-powered-document-processing/working-with-summarize-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 요약 옵션 사용

## 소개

문서, 특히 규모가 큰 문서를 다룰 때 핵심 요점을 요약하는 것은 축복이 될 수 있습니다. 건초더미에서 바늘을 찾기 위해 텍스트 페이지를 뒤져본 적이 있다면 요약이 제공하는 효율성을 높이 평가할 것입니다. 이 튜토리얼에서는 Aspose.Words for .NET을 활용하여 문서를 효과적으로 요약하는 방법을 자세히 살펴보겠습니다. 개인적인 용도, 직장 프레젠테이션 또는 학업적 노력 여부에 관계없이 이 가이드는 단계별로 프로세스를 안내합니다.

## 필수 조건

문서 요약 여정을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

1.  Aspose.Words for .NET 라이브러리: Aspose.Words 라이브러리를 다운로드했는지 확인하세요. 다음에서 가져올 수 있습니다.[여기](https://releases.aspose.com/words/net/).
2. .NET 환경: 시스템에는 .NET 환경이 설정되어 있어야 합니다(Visual Studio와 유사). .NET을 처음 접한다면 걱정하지 마세요. 매우 사용자 친화적입니다!
3. C#에 대한 기본 지식: C# 프로그래밍에 대한 지식이 도움이 될 것입니다. 코드에서 몇 가지 단계를 따르고 기본 사항을 이해하면 더 매끄럽게 될 것입니다.
4. AI 모델용 API 키: 요약을 위해 생성 언어 모델을 활용하고 있으므로 사용자 환경에서 설정할 수 있는 API 키가 필요합니다.

이러한 전제 조건을 충족하면 시작할 준비가 되었습니다!

## 패키지 가져오기

시작하려면 프로젝트에 필요한 패키지를 가져오세요. Aspose.Words와 요약에 사용하고 싶은 AI 패키지가 필요합니다. 방법은 다음과 같습니다.

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Visual Studio의 NuGet 패키지 관리자를 통해 필요한 NuGet 패키지를 설치하세요.

이제 환경이 준비되었으니 Aspose.Words for .NET을 사용하여 문서를 요약하는 단계를 살펴보겠습니다.

## 1단계: 문서 디렉토리 설정 

문서 처리를 시작하기 전에 디렉토리를 설정하는 것이 좋습니다. 이 구성은 입력 및 출력 파일을 효율적으로 관리하는 데 도움이 됩니다.

```csharp
// 귀하의 문서 디렉토리
string MyDir = "YOUR_DOCUMENT_DIRECTORY"; 
// 귀하의 ArtifactsDir 디렉토리
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY"; 
```

 교체를 꼭 해주세요`"YOUR_DOCUMENT_DIRECTORY"` 그리고`"YOUR_ARTIFACTS_DIRECTORY"` 문서가 저장되어 있는 시스템의 실제 경로와 요약된 파일을 저장할 위치를 지정합니다.

## 2단계: 문서 로딩 

다음으로, 요약하고 싶은 문서를 로드해야 합니다. 여기서 텍스트를 프로그램으로 가져옵니다.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

여기서는 두 개의 문서를 로드하고 있습니다.`Big document.docx` 그리고`Document.docx`. 지정된 디렉토리에 이러한 파일이 있는지 확인하세요.

## 3단계: AI 모델 설정 

이제 문서를 요약하는 데 도움이 되는 AI 모델을 사용할 시간입니다. 먼저 API 키를 설정해야 합니다. 

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

이 예에서는 OpenAI의 GPT-4 Mini를 사용합니다. 이것이 제대로 작동하려면 환경 변수에 API 키가 올바르게 설정되어 있는지 확인하세요.

## 4단계: 단일 문서 요약

이제 재밌는 부분인 요약이 시작됩니다! 먼저 단일 문서를 요약해 보겠습니다. 

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

여기서 우리는 AI 모델에 요약을 요청하고 있습니다.`firstDoc` 짧은 요약 길이. 요약된 문서는 지정된 아티팩트 디렉토리에 저장됩니다.

## 5단계: 여러 문서 요약

요약할 문서가 여러 개라면요? 걱정하지 마세요! 다음 단계에서는 그 처리 방법을 보여드립니다.

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 이 경우, 우리는 두 가지를 모두 요약하고 있습니다.`firstDoc` 그리고`secondDoc` 그리고 우리는 더 긴 요약 길이를 지정했습니다. 요약된 출력은 모든 세부 사항을 읽지 않고도 주요 아이디어를 파악하는 데 도움이 될 것입니다.

## 결론

이제 아시죠! Aspose.Words for .NET을 사용하여 하나 또는 두 개의 문서를 성공적으로 요약했습니다. 우리가 거친 단계는 더 큰 프로젝트에 맞게 조정하거나 다양한 문서 처리 작업에 대해 자동화할 수도 있습니다. 요약은 문서의 본질을 유지하면서 시간과 노력을 크게 절약할 수 있다는 점을 기억하세요. 

코드를 가지고 놀고 싶으신가요? 계속하세요! 이 기술의 장점은 필요에 맞게 조정할 수 있다는 것입니다. 잊지 마세요. 더 많은 리소스와 문서는 다음에서 찾을 수 있습니다.[.NET 설명서를 위한 Aspose.Words](https://reference.aspose.com/words/net/) 그리고 문제가 발생하면[Aspose 지원 포럼](https://forum.aspose.com/c/words/8/) 클릭 한 번 거리에 있습니다.

## 자주 묻는 질문

### Aspose.Words란 무엇인가요?
Aspose.Words는 개발자가 Microsoft Word를 설치하지 않고도 Word 문서에서 작업을 수행할 수 있는 강력한 라이브러리입니다.

### Aspose를 사용하여 PDF를 요약할 수 있나요?
Aspose.Words는 주로 Word 문서를 다룹니다. PDF를 요약하려면 Aspose.PDF를 확인해 보세요.

### AI 모델을 실행하려면 인터넷 연결이 필요합니까?
네, AI 모델은 활성 인터넷 연결에 따라 달라지는 API 호출이 필요합니다.

### Aspose.Words 평가판이 있나요?
 물론입니다! 무료 체험판을 다운로드할 수 있습니다.[여기](https://releases.aspose.com/).

### 문제가 발생하면 어떻게 해야 하나요?
 문제가 발생하거나 질문이 있는 경우 다음을 방문하세요.[지원 포럼](https://forum.aspose.com/c/words/8/) 지침을 위해.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
