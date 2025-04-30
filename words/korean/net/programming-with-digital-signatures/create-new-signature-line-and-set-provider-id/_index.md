---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에 새 서명란을 만들고 공급자 ID를 설정하는 방법을 알아보세요. 단계별 가이드입니다."
"linktitle": "새 서명란을 만들고 공급자 ID를 설정합니다."
"second_title": "Aspose.Words 문서 처리 API"
"title": "새 서명란을 만들고 공급자 ID를 설정합니다."
"url": "/ko/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 새 서명란을 만들고 공급자 ID를 설정합니다.

## 소개

안녕하세요, 기술 애호가 여러분! Word 문서에 프로그래밍 방식으로 서명란을 추가하는 방법을 궁금해하셨나요? 오늘은 Aspose.Words for .NET을 사용하여 바로 그 방법을 알아보겠습니다. 이 가이드에서는 모든 단계를 안내하여 Word 문서에 새 서명란을 만들고 공급자 ID를 설정하는 과정을 아주 쉽게 만들어 드립니다. 문서 처리를 자동화하거나 워크플로를 간소화하려는 경우, 이 튜토리얼이 도움이 될 것입니다.

## 필수 조건

실제로 작업을 시작하기 전에, 필요한 모든 것이 있는지 확인해 보겠습니다.

1. Aspose.Words for .NET: 아직 다운로드하지 않았다면 지금 다운로드하세요. [여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio 또는 기타 C# 개발 환경.
3. .NET Framework: .NET Framework가 설치되어 있는지 확인하세요.
4. PFX 인증서: 문서에 서명하려면 PFX 인증서가 필요합니다. 신뢰할 수 있는 인증 기관에서 인증서를 받을 수 있습니다.

## 네임스페이스 가져오기

우선, C# 프로젝트에 필요한 네임스페이스를 가져오겠습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

좋습니다. 이제 본격적으로 시작해 보겠습니다. 새 서명란을 만들고 공급자 ID를 설정하는 각 단계를 자세히 살펴보겠습니다.

## 1단계: 새 문서 만들기

시작하려면 새 Word 문서를 만들어야 합니다. 이 문서가 서명란의 캔버스가 될 것입니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

이 스니펫에서는 새로운 것을 초기화하고 있습니다. `Document` 그리고 `DocumentBuilder`. 그 `DocumentBuilder` 문서에 요소를 추가하는 데 도움이 됩니다.

## 2단계: 서명란 옵션 정의

다음으로, 서명란에 대한 옵션을 정의합니다. 여기에는 서명자의 이름, 직함, 이메일 주소 및 기타 세부 정보가 포함됩니다.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

이러한 옵션을 사용하면 서명란을 개인화하여 명확하고 전문적인 서명으로 만들 수 있습니다.

## 3단계: 서명란 삽입

옵션이 설정되었으니 이제 문서에 서명줄을 삽입할 수 있습니다.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

여기서, `InsertSignatureLine` 이 방법은 서명 줄을 추가하고, 여기에 고유한 공급자 ID를 할당합니다.

## 4단계: 문서 저장

서명란을 삽입한 후 문서를 저장해 보겠습니다.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

이렇게 하면 새로 추가된 서명란이 포함된 문서가 저장됩니다.

## 5단계: 서명 옵션 설정

이제 문서 서명 옵션을 설정해야 합니다. 여기에는 서명란 ID, 공급자 ID, 주석, 서명 시간이 포함됩니다.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

이러한 옵션을 사용하면 문서에 올바른 세부 정보가 서명되었는지 확인할 수 있습니다.

## 6단계: 인증서 소유자 생성

문서에 서명하려면 PFX 인증서를 사용하겠습니다. 인증서 소유자를 생성해 보겠습니다.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

교체를 꼭 해주세요 `"morzal.pfx"` 실제 인증서 파일과 함께 `"aw"` 인증서 비밀번호를 입력하세요.

## 7단계: 문서에 서명하기

마지막으로 디지털 서명 유틸리티를 사용하여 문서에 서명합니다.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

이렇게 하면 문서에 서명하고 새 파일로 저장됩니다.

## 결론

자, 이제 완료되었습니다! Aspose.Words for .NET을 사용하여 Word 문서에 새 서명란을 만들고 공급자 ID를 설정하는 데 성공했습니다. 이 강력한 라이브러리를 사용하면 문서 처리 작업을 매우 쉽게 관리하고 자동화할 수 있습니다. 한번 사용해 보시고 워크플로우를 얼마나 간소화할 수 있는지 확인해 보세요.

## 자주 묻는 질문

### 서명란의 모양을 사용자 지정할 수 있나요?
물론입니다! 다양한 옵션을 조정할 수 있습니다. `SignatureLineOptions` 귀하의 필요에 맞게.

### PFX 인증서가 없으면 어떻게 하나요?
신뢰할 수 있는 인증 기관에서 인증서를 받아야 합니다. 문서에 디지털 서명을 하려면 인증서가 필수적입니다.

### 문서에 여러 개의 서명줄을 추가할 수 있나요?
네, 다양한 옵션을 사용하여 삽입 과정을 반복하면 필요한 만큼 서명 줄을 추가할 수 있습니다.

### Aspose.Words for .NET은 .NET Core와 호환됩니까?
네, Aspose.Words for .NET은 .NET Core를 지원하므로 다양한 개발 환경에서 다양하게 활용할 수 있습니다.

### 디지털 서명은 얼마나 안전한가요?
Aspose.Words로 생성된 디지털 서명은 유효하고 신뢰할 수 있는 인증서를 사용하는 경우 매우 안전합니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}