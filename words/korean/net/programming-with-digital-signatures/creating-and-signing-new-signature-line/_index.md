---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에 서명란을 만들고 디지털 서명하는 방법을 단계별 튜토리얼을 통해 알아보세요. 문서 자동화에 매우 유용합니다."
"linktitle": "새 서명란 만들기 및 서명"
"second_title": "Aspose.Words 문서 처리 API"
"title": "새 서명란 만들기 및 서명"
"url": "/ko/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 새 서명란 만들기 및 서명

## 소개

안녕하세요! Word 문서에 서명란을 추가하고 디지털 서명을 해야 합니다. 어렵게 들리시나요? 전혀 그렇지 않습니다! Aspose.Words for .NET 덕분에 몇 줄의 코드만으로 이 작업을 완벽하게 수행할 수 있습니다. 이 튜토리얼에서는 환경 설정부터 새 서명으로 문서를 저장하는 과정까지 전체 과정을 안내해 드리겠습니다. 준비되셨나요? 시작해 볼까요!

## 필수 조건

코드로 넘어가기 전에 필요한 모든 것이 있는지 확인해 보겠습니다.
1. Aspose.Words for .NET - 다음을 수행할 수 있습니다. [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. .NET 개발 환경 - Visual Studio를 적극 권장합니다.
3. 서명할 문서 - 간단한 Word 문서를 만들거나 기존 문서를 사용하세요.
4. 인증서 파일 - 디지털 서명에 필요합니다. 다음을 사용할 수 있습니다. `.pfx` 파일.
5. 서명란 이미지 - 선택적으로 서명에 대한 이미지 파일을 추가할 수 있습니다.

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 가져와야 합니다. 이 단계는 Aspose.Words 기능을 사용하기 위한 환경을 설정하므로 매우 중요합니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## 1단계: 문서 디렉터리 설정

모든 프로젝트는 좋은 시작이 필요합니다. 문서 디렉터리 경로를 설정해 보겠습니다. 이 경로에 문서가 저장되고 검색됩니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 새 문서 만들기

이제 Aspose.Words를 사용하여 새 Word 문서를 만들어 보겠습니다. 이 문서는 서명란을 추가할 캔버스가 될 것입니다.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3단계: 서명란 삽입

마법이 일어나는 곳이 바로 여기입니다. 다음을 사용하여 문서에 서명 줄을 삽입합니다. `DocumentBuilder` 수업.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## 4단계: 서명란이 있는 문서 저장

서명란을 설정한 후에는 문서를 저장해야 합니다. 이는 서명하기 전의 중간 단계입니다.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## 5단계: 서명 옵션 설정

이제 문서 서명 옵션을 설정해 보겠습니다. 여기에는 서명란 ID와 사용할 이미지 지정이 포함됩니다.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## 6단계: 인증서 로드

디지털 서명에는 인증서가 필요합니다. 여기서는 문서 서명에 사용할 인증서 파일을 로드합니다.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## 7단계: 문서 서명

이것은 마지막 단계입니다. 우리는 다음을 사용합니다. `DigitalSignatureUtil` 문서에 서명하는 클래스입니다. 서명된 문서는 새 이름으로 저장됩니다.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## 결론

자, 이제 완료되었습니다! 이 단계를 통해 새 Word 문서를 만들고, 서명란을 추가하고, Aspose.Words for .NET을 사용하여 디지털 서명을 완료했습니다. Aspose.Words for .NET은 문서 자동화를 간편하게 만들어 주는 강력한 도구입니다. 계약서, 합의서 또는 기타 공식 문서를 다룰 때 이 방법을 사용하면 안전하게 서명하고 인증할 수 있습니다.

## 자주 묻는 질문

### 서명란에 다른 이미지 형식을 사용할 수 있나요?
네, PNG, JPG, BMP 등 다양한 이미지 형식을 사용할 수 있습니다.

### 를 사용해야 합니까? `.pfx` 인증서 파일?
네, 하나 `.pfx` 파일은 인증서와 개인 키를 포함한 암호화 정보를 저장하는 데 일반적으로 사용되는 형식입니다.

### 하나의 문서에 여러 개의 서명줄을 추가할 수 있나요?
물론입니다! 각 서명마다 삽입 단계를 반복하여 여러 개의 서명 줄을 삽입할 수 있습니다.

### 디지털 인증서가 없으면 어떻게 하나요?
신뢰할 수 있는 인증 기관에서 디지털 인증서를 얻거나 OpenSSL과 같은 도구를 사용하여 인증서를 생성해야 합니다.

### 문서의 디지털 서명을 어떻게 검증합니까?
Word에서 서명된 문서를 열고 서명 세부 정보로 이동하여 서명의 진위성과 무결성을 확인할 수 있습니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}