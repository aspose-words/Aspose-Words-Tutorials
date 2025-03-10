---
title: Open AI 모델로 작업하기
linktitle: Open AI 모델로 작업하기
second_title: Aspose.Words 문서 처리 API
description: OpenAI의 강력한 모델과 함께 Aspose.Words for .NET을 사용하여 효율적인 문서 요약을 잠금 해제하세요. 지금 이 포괄적인 가이드를 살펴보세요.
weight: 10
url: /ko/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Open AI 모델로 작업하기

## 소개

오늘날의 디지털 세계에서는 콘텐츠가 왕입니다. 학생이든, 비즈니스 전문가이든, 열렬한 작가이든, 문서를 효율적으로 조작, 요약, 생성하는 능력은 매우 중요합니다. 여기서 Aspose.Words for .NET 라이브러리가 등장하여 전문가처럼 문서를 관리할 수 있습니다. 이 포괄적인 튜토리얼에서는 Aspose.Words를 OpenAI 모델과 함께 활용하여 문서를 효과적으로 요약하는 방법을 자세히 알아보겠습니다. 문서 관리 잠재력을 끌어낼 준비가 되셨나요? 시작해 볼까요!

## 필수 조건

소매를 걷어붙이고 코드를 살펴보기 전에 꼭 갖춰야 할 몇 가지 필수 사항이 있습니다.

### .NET 프레임워크
Aspose.Words와 호환되는 .NET 프레임워크 버전에서 실행 중인지 확인하세요. 일반적으로 .NET 5.0 이상이 완벽하게 작동해야 합니다.

### .NET 라이브러리를 위한 Aspose.Words
 Aspose.Words 라이브러리를 다운로드하여 설치해야 합니다. 다음에서 가져올 수 있습니다.[이 링크](https://releases.aspose.com/words/net/).

### OpenAI API 키
문서 요약을 위해 OpenAI의 언어 모델을 통합하려면 API 키가 필요합니다. OpenAI 플랫폼에 가입하고 계정 설정에서 키를 검색하면 얻을 수 있습니다.

### 개발을 위한 IDE
Visual Studio와 같은 통합 개발 환경(IDE)을 설정하면 .NET 애플리케이션을 개발하는 데 이상적입니다.

### 기본 프로그래밍 지식
C#와 객체 지향 프로그래밍에 대한 기본적인 이해가 있으면 개념을 더 쉽게 이해하는 데 도움이 됩니다.

## 패키지 가져오기

이제 모든 것을 준비했으니 패키지를 가져오도록 합시다. Visual Studio 프로젝트를 열고 필요한 라이브러리를 추가합니다. 방법은 다음과 같습니다.

### Aspose.Words 패키지 추가

NuGet Package Manager를 통해 Aspose.Words 패키지를 추가할 수 있습니다. 방법은 다음과 같습니다.
- 도구 -> NuGet 패키지 관리자 -> 솔루션에 대한 NuGet 패키지 관리로 이동합니다.
- "Aspose.Words"를 검색하고 설치를 클릭하세요.

### 시스템 환경 추가

 다음을 포함해야 합니다.`System`환경 변수를 처리하기 위한 네임스페이스:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Aspose.Words 추가

그런 다음 C# 파일에 Aspose.Words 네임스페이스를 포함합니다.
```csharp
using Aspose.Words;
```

### OpenAI 라이브러리 추가

OpenAI와 인터페이스하기 위해 라이브러리를 사용하는 경우(REST 클라이언트와 같은) 해당 라이브러리도 포함해야 합니다. Aspose.Words를 추가한 것과 같은 방식으로 NuGet을 통해 추가해야 할 수도 있습니다.

이제 환경을 준비하고 필요한 패키지를 가져왔으니, 문서 요약 프로세스를 단계별로 나누어 보겠습니다.

## 1단계: 문서 디렉토리 정의

문서 작업을 시작하기 전에 문서와 아티팩트가 저장될 디렉토리를 설정해야 합니다.

```csharp
// 귀하의 문서 디렉토리
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// 귀하의 유물 디렉토리
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 필요한 경우 경로를 쉽게 변경할 수 있으므로 코드를 더 쉽게 관리할 수 있습니다.`MyDir` 입력 문서가 저장되는 곳입니다.`ArtifactsDir` 생성된 요약을 저장하는 곳입니다.

## 2단계: 문서 로드

다음으로 요약하려는 문서를 로드합니다. Aspose.Words를 사용하면 간단합니다.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
사용하려는 문서의 이름이 일치해야 합니다. 그렇지 않으면 오류가 발생합니다!

## 3단계: API 키 받기

이제 문서가 로드되었으니 OpenAI API 키를 가져올 차례입니다. 안전하게 보관하기 위해 환경 변수에서 가져옵니다.
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
허가받지 않은 사용자를 차단하려면 API 키를 안전하게 관리하는 것이 중요합니다.

## 4단계: OpenAI 모델 인스턴스 생성

API 키가 준비되면 이제 OpenAI 모델의 인스턴스를 만들 수 있습니다. 문서 요약을 위해 Gpt4OMini 모델을 사용하겠습니다.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
이 단계는 기본적으로 문서를 요약하는 데 필요한 두뇌 능력을 설정하여 AI 기반 요약 기능을 사용할 수 있도록 합니다.

## 5단계: 단일 문서 요약

먼저 첫 번째 문서를 요약해 보겠습니다. 마법이 일어나는 곳은 바로 여기입니다.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 여기서 우리는 다음을 사용하고 있습니다.`Summarize` 모델의 방법.`SummaryLength.Short`매개변수는 간략한 요약을 원한다는 것을 지정합니다. 빠른 개요를 보기에 완벽합니다!

## 6단계: 여러 문서 요약

야심이 있으신가요? 여러 문서를 한 번에 요약할 수 있습니다. 얼마나 쉬운지 보세요:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
이 기능은 여러 파일을 비교하는 데 특히 편리합니다. 어쩌면 회의를 준비하고 있고 여러 긴 보고서에서 간결한 메모가 필요할 수도 있습니다. 이것이 당신의 새로운 가장 친한 친구입니다!

## 결론

Aspose.Words for .NET 및 OpenAI로 문서를 요약하는 것은 유익한 기술일 뿐만 아니라 매우 강력합니다. 이 가이드를 따르면 길고 복잡한 텍스트를 간결한 요약으로 바꾸어 시간과 노력을 절약할 수 있습니다. 고객에게 명확성을 보장하든 중요한 프레젠테이션을 준비하든, 이제 효율적으로 수행할 수 있는 도구가 있습니다.

그럼, 무엇을 기다리고 계신가요? 자신감을 가지고 문서를 살펴보고 기술이 힘든 일을 처리하게 하세요!

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?  
Aspose.Words for .NET은 개발자가 프로그래밍 방식으로 문서를 만들고, 조작하고, 변환할 수 있는 강력한 라이브러리입니다.

### OpenAI에 API 키가 필요한가요?  
네, OpenAI 모델을 사용하여 요약 기능에 액세스하려면 유효한 OpenAI API 키가 있어야 합니다.

### 한 번에 여러 문서를 요약할 수 있나요?  
물론입니다! 한 번의 통화로 여러 문서를 요약할 수 있어 광범위한 보고서에 이상적입니다.

### Aspose.Words를 어떻게 설치하나요?  
Visual Studio에서 NuGet 패키지 관리자를 통해 "Aspose.Words"를 검색하여 설치할 수 있습니다.

### Aspose.Words 무료 체험판이 있나요?  
 예, Aspose.Words의 무료 평가판에 액세스할 수 있습니다.[웹사이트](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
