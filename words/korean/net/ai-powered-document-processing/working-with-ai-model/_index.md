---
title: AI 모델로 작업하기
linktitle: AI 모델로 작업하기
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 AI로 문서를 요약하는 방법을 알아보세요. 문서 관리를 개선하기 위한 간단한 단계.
weight: 10
url: /ko/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# AI 모델로 작업하기

## 소개

.NET용 Aspose.Words의 매혹적인 세계에 오신 것을 환영합니다! 문서 관리를 한 단계 업그레이드하고 싶었던 적이 있다면, 당신은 올바른 곳에 있습니다. 몇 줄의 코드만으로 대량의 문서를 자동으로 요약할 수 있다고 상상해보세요. 놀랍지 않나요? 이 가이드에서는 OpenAI의 GPT와 같은 강력한 AI 언어 모델을 사용하여 Aspose.Words를 사용하여 문서 요약을 생성하는 방법을 자세히 살펴보겠습니다. 애플리케이션을 개선하려는 개발자이든 새로운 것을 배우고 싶어 하는 기술 매니아이든, 이 튜토리얼이 도움이 될 것입니다.

## 필수 조건

소매를 걷어붙이고 코딩을 시작하기 전에 꼭 갖춰야 할 몇 가지 필수 사항이 있습니다.

1. Visual Studio 설치됨: 컴퓨터에 Visual Studio가 설치되어 있는지 확인하세요. 아직 설치되어 있지 않으면 무료로 다운로드할 수 있습니다.
  
2. .NET Framework: Aspose.Words에 호환되는 .NET Framework 버전을 사용하고 있는지 확인하세요. .NET Framework와 .NET Core를 모두 지원합니다.

3.  Aspose.Words for .NET: Aspose.Words를 다운로드하고 설치해야 합니다. 최신 버전을 가져올 수 있습니다.[여기](https://releases.aspose.com/words/net/).

4. AI 모델을 위한 API 키: AI 요약을 활용하려면 AI 모델에 액세스해야 합니다. OpenAI나 Google과 같은 플랫폼에서 API 키를 받으세요.

5. C#에 대한 기본 지식: 이 튜토리얼을 최대한 활용하려면 C# 프로그래밍에 대한 기본적인 이해가 필요합니다.

모든 것을 다 얻었나요? 대단해요! 재밌는 부분으로 넘어가 봅시다 - 필요한 패키지를 가져오는 것.

## 패키지 가져오기

Aspose.Words의 힘을 활용하고 AI 모델로 작업하려면 먼저 필요한 패키지를 가져옵니다. 방법은 다음과 같습니다.

### 새 프로젝트 만들기

먼저, Visual Studio를 실행하고 새 콘솔 애플리케이션 프로젝트를 만듭니다.

1. Visual Studio를 엽니다.
2. “새 프로젝트 만들기”를 클릭하세요.
3. 설정에 따라 "콘솔 앱(.NET Framework)" 또는 "콘솔 앱(.NET Core)"을 선택하세요.
4. 프로젝트 이름을 지정하고 위치를 지정하세요.

### Aspose.Words 및 AI 모델 패키지 설치

Aspose.Words를 사용하려면 NuGet을 통해 패키지를 설치해야 합니다.

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 "NuGet 패키지 관리"를 선택합니다.
2. “Aspose.Words”를 검색하고 “설치”를 클릭합니다.
3. 특정 AI 모델 패키지(예: OpenAI)를 사용하는 경우 해당 패키지도 설치되어 있는지 확인하세요.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
축하합니다! 패키지가 준비되었으니, 구현을 더 깊이 파헤쳐 봅시다.

## 1단계: 문서 디렉토리 설정

우리의 코드에서는 문서를 저장할 위치와 출력물을 저장할 위치를 관리하는 디렉토리를 정의할 것입니다. 

```csharp
// 귀하의 문서 디렉토리
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// 귀하의 ArtifactsDir 디렉토리
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

-  여기서 교체하세요`YOUR_DOCUMENT_DIRECTORY` 문서가 저장된 위치와 함께`YOUR_ARTIFACTS_DIRECTORY` 요약된 파일을 저장할 위치입니다.

## 2단계: 문서 로드

다음으로, 요약하고 싶은 문서를 프로그램에 로드합니다. 아주 간단합니다! 방법은 다음과 같습니다.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- 파일 이름을 저장한 대로 조정합니다. 이 예에서는 "Big document.docx"와 "Document.docx"라는 두 개의 문서가 있다고 가정합니다.

## 3단계: AI 모델 초기화

다음 단계는 AI 모델과 연결을 설정하는 것입니다. 여기서 앞서 얻은 API 키가 작용합니다.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- API 키를 환경 변수로 저장해 두세요. 비밀 소스를 안전하게 보관하는 것과 마찬가지입니다!

## 4단계: 첫 번째 문서에 대한 요약 생성

이제 첫 번째 문서에 대한 요약을 만들어 보겠습니다. 요약 길이를 정의하기 위한 매개변수도 설정합니다.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- 이 스니펫은 첫 번째 문서를 요약하고 지정한 아티팩트 디렉토리에 출력을 저장합니다. 요약 길이를 원하는 대로 변경하세요!

## 5단계: 여러 문서에 대한 요약 생성

모험심이 있나요? 여러 문서를 한 번에 요약할 수도 있습니다! 방법은 다음과 같습니다.

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- 그렇게 하면 두 문서를 동시에 요약할 수 있어요! 효율성에 대해 이야기하는 거죠, 그렇죠?

## 결론

이제 다 됐습니다! 이 가이드를 따르면 Aspose.Words for .NET과 강력한 AI 모델을 사용하여 문서를 요약하는 기술을 익혔습니다. 개인적인 용도이든 전문적인 애플리케이션에 통합하든 엄청난 시간을 절약할 수 있는 흥미로운 기능입니다. 이제 자동화의 힘을 발휘하고 생산성이 치솟는 것을 지켜보세요!

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?
Aspose.Words for .NET은 개발자가 Word 문서를 프로그래밍 방식으로 만들고, 수정하고, 변환하고, 렌더링할 수 있는 강력한 라이브러리입니다.

### AI 모델에 대한 API 키는 어떻게 얻을 수 있나요?
OpenAI나 Google과 같은 AI 제공업체에서 API 키를 얻을 수 있습니다. 계정을 만들고 해당 지침을 따라 키를 생성하세요.

### Aspose.Words를 다른 파일 형식에도 사용할 수 있나요?
네! Aspose.Words는 DOCX, RTF, HTML을 포함한 다양한 파일 형식을 지원하여 텍스트 문서 외에도 광범위한 기능을 제공합니다.

### Aspose.Words의 무료 버전이 있나요?
Aspose는 무료 체험판을 제공하여 기능을 테스트할 수 있습니다. 사이트에서 다운로드할 수 있습니다.

### Aspose.Words에 대한 추가 리소스는 어디에서 찾을 수 있나요?
 문서를 확인할 수 있습니다[여기](https://reference.aspose.com/words/net/) 포괄적인 가이드와 통찰력을 얻으세요.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
