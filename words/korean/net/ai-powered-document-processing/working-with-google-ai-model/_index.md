---
"description": "Aspose.Words for .NET과 Google AI를 사용하여 문서 처리 능력을 향상시키고 간결한 요약을 손쉽게 작성하세요."
"linktitle": "Google AI 모델 작업"
"second_title": "Aspose.Words 문서 처리 API"
"title": "Google AI 모델 작업"
"url": "/ko/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Google AI 모델 작업

## 소개

이 글에서는 Aspose.Words와 Google의 AI 모델을 사용하여 문서를 요약하는 방법을 단계별로 살펴보겠습니다. 긴 보고서를 요약하거나 여러 출처에서 인사이트를 추출해야 하는 경우, 저희가 도와드리겠습니다.

## 필수 조건

실습에 들어가기 전에, 성공적인 결과를 위한 준비가 되어 있는지 확인해 보세요. 필요한 것은 다음과 같습니다.

1. C#과 .NET에 대한 기본 지식: 프로그래밍 개념에 익숙하면 예제를 더 잘 이해하는 데 도움이 됩니다.
   
2. Aspose.Words for .NET 라이브러리: 이 강력한 라이브러리를 사용하면 Word 문서를 원활하게 만들고 조작할 수 있습니다. [여기서 다운로드하세요](https://releases.aspose.com/words/net/).

3. Google AI 모델용 API 키: AI 모델을 활용하려면 인증용 API 키가 필요합니다. 이 키는 환경 변수에 안전하게 저장하세요.

4. 개발 환경: 작동하는 .NET 환경(Visual Studio 또는 다른 IDE)이 설정되어 있는지 확인하세요.

5. 샘플 문서: 요약을 테스트하려면 샘플 Word 문서(예: "Big document.docx", "Document.docx")가 필요합니다.

이제 기본 사항을 살펴보았으니 코드를 살펴보겠습니다!

## 패키지 가져오기

Aspose.Words를 사용하고 Google AI 모델을 통합하려면 필요한 네임스페이스를 가져와야 합니다. 방법은 다음과 같습니다.

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

이제 필요한 패키지를 가져왔으니, 문서 요약 과정을 단계별로 살펴보겠습니다.

## 1단계: 문서 디렉터리 설정

문서를 처리하기 전에 파일의 위치를 지정해야 합니다. 이 단계는 Aspose.Words가 문서에 접근할 수 있도록 하는 데 매우 중요합니다.

```csharp
// 귀하의 문서 디렉토리
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// 귀하의 ArtifactsDir 디렉토리
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

바꾸다 `"YOUR_DOCUMENT_DIRECTORY"` 그리고 `"YOUR_ARTIFACTS_DIRECTORY"` 문서가 저장된 시스템의 실제 경로를 사용합니다. 이는 문서를 읽고 저장하는 기준이 됩니다.

## 2단계: 문서 로드

다음으로, 요약할 문서를 불러와야 합니다. 이 경우에는 앞서 지정한 두 문서를 불러옵니다.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

그만큼 `Document` Aspose.Words 클래스를 사용하면 Word 파일을 메모리에 로드할 수 있습니다. 파일 이름이 디렉터리의 실제 문서와 일치하는지 확인하세요. 그렇지 않으면 "파일을 찾을 수 없음" 오류가 발생합니다!

## 3단계: API 키 검색

AI 모델을 활용하려면 API 키를 발급받아야 합니다. 이 키는 Google AI 서비스에 대한 액세스 권한과 같은 역할을 합니다.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

이 코드 줄은 환경 변수에 저장된 API 키를 가져옵니다. 보안상의 이유로 API 키와 같은 민감한 정보는 코드에 포함하지 않는 것이 좋습니다.

## 4단계: AI 모델 인스턴스 생성

이제 AI 모델의 인스턴스를 생성할 차례입니다. 여기서 사용할 모델을 선택할 수 있는데, 이 예시에서는 GPT-4 Mini 모델을 선택했습니다.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

이 줄은 문서 요약에 사용할 AI 모델을 설정합니다. 다음을 참조하세요. [문서](https://reference.aspose.com/words/net/) 다양한 모델과 기능에 대한 자세한 내용은 여기를 참조하세요.

## 5단계: 단일 문서 요약

첫 번째 문서를 요약하는 데 집중해 보겠습니다. 여기서는 간략한 요약을 볼 수 있습니다.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

이 단계에서는 다음을 사용합니다. `Summarize` AI 모델 인스턴스에서 첫 번째 문서의 요약본을 가져오는 메서드를 사용합니다. 요약 길이는 짧게 설정되어 있지만, 필요에 따라 사용자 지정할 수 있습니다. 마지막으로 요약된 문서는 아티팩트 디렉터리에 저장됩니다.

## 6단계: 여러 문서 요약

여러 문서를 한 번에 요약하고 싶으신가요? Aspose.Words를 사용하면 간편하게 요약할 수 있습니다!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

여기서 우리는 다음을 호출합니다. `Summarize` 다시 한번 방법을 사용하지만, 이번에는 문서 배열을 사용합니다. 이렇게 하면 두 파일의 핵심을 요약한 긴 요약이 생성됩니다. 이전과 마찬가지로 결과는 지정된 아티팩트 디렉터리에 저장됩니다.

## 결론

자, 이제 Aspose.Words for .NET과 Google의 AI 모델을 사용하여 문서를 요약하는 환경을 성공적으로 구축했습니다. 문서 로딩부터 간결한 요약 생성까지, 이 단계들을 통해 방대한 양의 텍스트를 효과적으로 관리할 수 있는 간소화된 접근 방식을 제공합니다.

## 자주 묻는 질문

### Aspose.Words란 무엇인가요?
Aspose.Words는 .NET을 사용하여 Word 문서를 만들고, 수정하고, 변환하는 강력한 라이브러리입니다.

### Google AI에 대한 API 키는 어떻게 얻을 수 있나요?
일반적으로 Google Cloud에 가입하고 필요한 API 서비스를 활성화하면 API 키를 얻을 수 있습니다.

### 여러 문서를 한 번에 요약할 수 있나요?
네! 시연된 것처럼, 요약 메서드에 문서 배열을 전달할 수 있습니다.

### 어떤 유형의 요약을 만들 수 있나요?
귀하의 필요에 따라 짧은 요약, 중간 요약, 긴 요약 중에서 선택하실 수 있습니다.

### Aspose.Words에 대한 더 많은 자료는 어디에서 찾을 수 있나요?
확인해 보세요 [선적 서류 비치](https://reference.aspose.com/words/net/) 더 많은 예와 지침을 보려면 여기를 클릭하세요.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}