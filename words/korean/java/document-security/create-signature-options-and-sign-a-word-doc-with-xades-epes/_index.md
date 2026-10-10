---
category: general
date: 2026-10-10
description: Java에서 XAdES EPES를 사용해 서명 옵션을 만들고 Word 문서에 서명하세요. 몇 가지 명확한 단계로 인증서를 이용해
  오피스 문서에 서명하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: ko
lastmod: 2026-10-10
og_description: Java에서 XAdES EPES를 사용해 서명 옵션을 만들고 Word 문서를 서명합니다. 이 가이드는 인증서를 이용해
  오피스 문서를 안전하게 서명하는 방법을 보여줍니다.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: 서명 옵션을 만들고 XAdES EPES로 워드 문서에 서명하기
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: 서명 옵션을 만들고 XAdES EPES로 워드 문서에 서명하기
url: /ko/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# XAdES EPES로 Word 문서에 서명하고 서명 옵션 만들기

DOCX 파일에 대한 **서명 옵션을 만들** 필요가 있다면, 이 가이드는 Java에서 XAdES‑EPES 레벨을 사용하여 Word 문서에 서명하는 방법을 보여줍니다. 몇 줄의 코드만으로 PFX 인증서를 사용해 오피스 문서에 서명하는 완전한 실행 가능한 예제를 제공합니다.

오피스 문서에 서명하는 것은 법적 워크플로, 자동 계약 처리 및 안전한 문서 교환에 흔히 요구됩니다. 이 튜토리얼에서 배우게 될 내용:

* `SignatureOptions`를 XAdES‑EPES에 맞게 구성하는 방법.
* `DigitalSignatureUtil.sign`을 호출하여 **워드 문서에 서명**하는 방법.
* 인증서 로드 및 비밀번호 오류와 같은 일반적인 함정을 처리하는 방법.

> **전제 조건** – Java 17 이상, GroupDocs.Signature for Java 라이브러리(또는 호환 가능한 XAdES 라이브러리), 그리고 유효한 `.pfx` 인증서 파일.

## 필요 사항

| 항목 | 이유 |
|------|--------|
| Java 17+ | 현대적인 언어 기능 및 향상된 보안 APIs |
| GroupDocs.Signature for Java (or equivalent) | `SignatureOptions`, `XmlDsigLevel`, 및 `DigitalSignatureUtil` 제공 |
| A PFX certificate (`.pfx`) | 디지털 서명을 위한 개인 키를 제공합니다 |
| Password for the certificate | 개인 키를 잠금 해제하는 데 필요합니다 |
| An unsigned DOCX file (`Unsigned.docx`) | **오피스 문서 서명**을 원하는 원본 문서 |

라이브러리 JAR가 클래스패스에 포함되어 있는지 확인하세요:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

## 단계 1: 필요한 클래스 가져오기

먼저 서명 및 파일 I/O를 처리하는 클래스를 가져옵니다.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

이러한 import는 **서명 옵션을 만들** 때 사용되는 API와 실제 서명 작업을 수행할 수 있게 해줍니다.

## 단계 2: 서명 옵션 만들기

`SignatureOptions` 객체는 서명 레벨, 시각적 표시, 타임스탬프 설정 등 서명 프로세스에 필요한 모든 구성을 보유합니다.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

새로운 `SignatureOptions` 인스턴스를 생성하는 것은 **docx 파일 서명 방법**의 첫 단계이며, 각 서명 요청을 분리해 문서 간 부작용을 방지합니다.

## 단계 3: XAdES EPES 서명 레벨 지정

XAdES‑EPES(Explicit Policy‑based Electronic Signature)는 오피스 문서 서명에 널리 받아들여지는 정책입니다. 레벨을 설정하면 라이브러리에 사용할 암호화 프로파일을 알려줍니다.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

왜 XAdES‑EPES인가요? 서명 정책을 서명에 직접 포함시켜 서명된 문서가 자체적으로 완전하고 많은 전자 서명 규정을 준수하도록 합니다.

## 단계 4: DOCX 파일 서명

이제 `DigitalSignatureUtil.sign`을 호출합니다. 이 메서드는 원본 파일을 읽고 서명을 적용한 뒤 서명된 결과를 씁니다.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**내부에서 무슨 일이 일어나나요?**  
1. 라이브러리가 제공된 비밀번호를 사용해 `.pfx` 파일을 로드하고 개인 키를 추출합니다.  
2. XAdES‑EPES 프로파일에 맞는 XML‑DSig 구조를 생성합니다.  
3. 서명이 DOCX 패키지에 삽입되어 원본 문서 레이아웃을 유지합니다.  

인증서 비밀번호가 틀리거나 파일을 읽을 수 없을 경우 `IOException`이 발생하며, 예시와 같이 처리해야 합니다.

## 단계 5: 서명된 문서 검증 (선택 사항)

서명 후 서명이 존재하고 유효한지 확인하고 싶을 수 있습니다. GroupDocs는 검증 API를 제공하지만, Microsoft Word를 사용해 빠르게 수동 확인도 가능합니다:

1. Word에서 `SignedXades.docx` 파일을 엽니다.  
2. **File → Info → View signatures**를 클릭합니다.  
3. Word가 녹색 체크 표시를 보여주며 유효한 디지털 서명을 나타냅니다.

라이브러리를 사용한 자동 검증은 다음과 같습니다:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

검증 단계를 실행하면 **오피스 문서 서명**이 성공했음을 프로그램적으로 확인할 수 있습니다.

## 전체 실행 가능한 예제

모든 요소를 합쳐서 복사·붙여넣기만 하면 실행할 수 있는 독립형 Java 클래스를 아래에 제공합니다.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**예상 출력**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

문제가 발생하면 콘솔에 명확한 오류 메시지가 표시되어 인증서 또는 파일 경로 문제를 해결하는 데 도움이 됩니다.

## 일반적인 질문 및 예외 상황 처리

| 질문 | 답변 |
|----------|--------|
| **다른 서명 레벨을 사용할 수 있나요?** | 예. 컴플라이언스 요구에 따라 `XmlDsigLevel.XAdES_EPES`를 `XAdES_BES`, `XAdES_T` 등으로 교체하면 됩니다. |
| **인증서가 .pfx 파일이 아닌 keystore에 저장된 경우는 어떻게 하나요?** | `KeyStore`를 직접 로드하고 `PrivateKey`와 `Certificate`를 추출한 뒤, `KeyStore` 객체를 인수로 받는 `sign` 오버로드에 전달합니다. |
| **보이는 서명 이미지를 추가하려면 어떻게 하나요?** | `sign`을 호출하기 전에 `signatureOptions.setSignatureImage("path/to/image.png")`를 사용합니다. |
| **서명 프로세스가 스레드 안전한가요?** | `DigitalSignatureUtil.sign` 메서드는 상태를 유지하지 않으므로 각 스레드가 자체 `SignatureOptions` 인스턴스를 사용한다면 여러 스레드에서 안전하게 호출할 수 있습니다. |
| **DOCX에 기존 서명이 포함된 경우는 어떻게 하나요?** | 라이브러리는 새로운 서명 패키지 항목을 추가하여 기존 서명을 보존합니다. 필요에 따라 서명 정책이 다중 서명을 허용하는지 확인하세요. |

## 팁 및 모범 사례 (E‑E‑A‑T)

* **Pro tip:** 인증서 비밀번호를 하드코딩하지 말고 보안 금고(예: Azure Key Vault)에 저장하세요.  
* **Watch out for:** Windows(`\`)와 Unix(`/`)의 파일 경로 구분자를 유의하세요. `Paths.get(...)`를 사용해 플랫폼에 독립적인 경로를 구축합니다.  
* **Performance:** 큰 DOCX 파일 서명은 I/O에 의존할 수 있으므로, 배치로 많은 문서를 처리할 경우 입력 파일을 스트리밍하는 것을 고려하세요.  
* **Compliance:** XAdES‑EPES는 EU eIDAS 규정을 준수합니다. 서명 레벨을 선택하기 전에 현지 법적 요구사항을 확인하세요.

## 결론

이 튜토리얼에서는 Java를 사용해 XAdES‑EPES 레벨로 **서명 옵션을 만들**고 **Word 문서에 서명**하는 방법을 배웠습니다. 전체 예제는 인증서 로드, 옵션 구성, 서명 호출 및 선택적 검증을 포함하여, 프로덕션 환경에서 **docx 파일 서명 방법**에 대한 즉시 사용 가능한 솔루션을 제공합니다.

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [Java에서 로드 옵션 만들기 – 누락된 글꼴 감지 및 DOCX 로드 방법](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Aspose.Words for Java에서 문서 옵션 및 설정 사용](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Aspose.Words for Java를 사용해 읽기 전용 문서에 편집 가능한 범위 만들기](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}