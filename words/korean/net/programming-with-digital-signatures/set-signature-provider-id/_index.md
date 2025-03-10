---
title: Word 문서에서 서명 공급자 ID 설정
linktitle: Word 문서에서 서명 공급자 ID 설정
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에서 Signature Provider ID를 안전하게 설정하세요. 자세한 2000단어 가이드를 따라 문서에 디지털 서명하세요.
weight: 10
url: /ko/net/programming-with-digital-signatures/set-signature-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 서명 공급자 ID 설정

## 소개

안녕하세요! 디지털 서명이 필요한 놀라운 Word 문서가 있나요? 하지만 그저 어떤 서명이든 아닙니다. 특정 서명 공급자 ID를 설정해야 합니다. 법률 문서, 계약서 또는 서류를 처리하든, 안전한 디지털 서명을 추가하는 것이 중요합니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에서 서명 공급자 ID를 설정하는 전체 프로세스를 안내해 드리겠습니다. 준비되셨나요? 시작해 볼까요!

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1. .NET 라이브러리용 Aspose.Words: 아직 없다면,[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio 또는 C# 호환 IDE.
3. Word 문서: 서명란이 있는 문서(`Signature line.docx`).
4.  디지털 인증서: A`.pfx` 인증서 파일(예:`morzal.pfx`).
5. C#에 대한 기본 지식: 기본적인 내용만 알고 계셔도 걱정하지 마세요. 저희가 도와드리겠습니다!

이제, 액션에 들어가볼까요!

## 네임스페이스 가져오기

우선, 프로젝트에 필요한 네임스페이스를 포함해야 합니다. 이는 Aspose.Words 라이브러리와 관련 클래스에 액세스하는 데 필수적입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

좋습니다. 간단하고 이해하기 쉬운 단계로 나누어 보겠습니다.

## 1단계: Word 문서 로드

첫 번째 단계는 서명 줄이 포함된 Word 문서를 로드하는 것입니다. 이 문서는 지정된 서명 공급자 ID가 있는 디지털 서명을 포함하도록 수정됩니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 여기서 문서가 있는 디렉토리를 지정합니다. 바꾸기`"YOUR DOCUMENT DIRECTORY"` 문서의 실제 경로를 입력합니다.

## 2단계: 서명란에 접근

다음으로, 문서 내의 서명란에 접근해야 합니다. 서명란은 Word 문서에 셰이프 객체로 내장되어 있습니다.

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 이 코드 줄은 문서의 첫 번째 섹션 본문에서 첫 번째 모양을 가져와서 다음 형식으로 캐스팅합니다.`SignatureLine` 물체.

## 3단계: 사인 옵션 설정

이제 액세스한 서명 줄의 공급자 ID와 서명 줄 ID를 포함하는 서명 옵션을 생성합니다.

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

이러한 옵션은 문서에 서명할 때 올바른 서명 공급자 ID가 설정되었는지 확인하는 데 사용됩니다.

## 4단계: 인증서 로드

 문서에 디지털로 서명하려면 인증서가 필요합니다. 다음은 인증서를 로드하는 방법입니다.`.pfx` 파일:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 바꾸다`"aw"` 인증서 파일에 비밀번호가 있으면 해당 비밀번호를 입력하세요.

## 5단계: 문서 서명

 마지막으로 문서에 서명할 시간입니다.`DigitalSignatureUtil.Sign` 방법.

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 이렇게 하면 문서에 서명하고 새 파일로 저장됩니다.`Digitally signed.docx`.

## 결론

이제 다 되었습니다! Aspose.Words for .NET을 사용하여 Word 문서에 서명 공급자 ID를 성공적으로 설정했습니다. 이 프로세스는 문서를 보호할 뿐만 아니라 디지털 서명 표준을 준수하도록 보장합니다. 이제 문서로 시도해 보세요. 궁금한 점이 있으신가요? 아래의 FAQ를 확인하거나[Aspose 지원 포럼](https://forum.aspose.com/c/words/8).

## 자주 묻는 질문

### 서명 공급자 ID란 무엇인가요?

서명 공급자 ID는 디지털 서명 공급자를 고유하게 식별하여 진위성과 보안을 보장합니다.

### 서명에 .pfx 파일을 사용할 수 있나요?

네, 유효한 디지털 인증서라면 가능합니다. 보호된 경우 올바른 비밀번호를 사용하세요.

### .pfx 파일은 어떻게 얻을 수 있나요?

인증 기관(CA)에서 .pfx 파일을 얻거나 OpenSSL과 같은 도구를 사용하여 파일을 생성할 수 있습니다.

### 한 번에 여러 문서에 서명할 수 있나요?

네, 여러 문서를 반복하여 각 문서에 동일한 서명 프로세스를 적용할 수 있습니다.

### 문서에 서명란이 없으면 어떻게 해야 하나요?

먼저 서명란을 삽입해야 합니다. Aspose.Words는 서명란을 프로그래밍 방식으로 추가하는 방법을 제공합니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
