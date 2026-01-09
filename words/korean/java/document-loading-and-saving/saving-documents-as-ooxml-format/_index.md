---
date: 2026-01-09
description: Aspose.Words for Java를 사용하여 OOXML 형식으로 문서를 저장할 때 비밀번호로 docx를 암호화하고 압축
  수준을 변경하는 방법을 배우세요.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: 비밀번호로 docx 암호화 – Aspose.Words Java를 사용한 OOXML 저장
url: /ko/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 암호로 docx 암호화 – Aspose.Words Java로 OOXML 저장

## Aspose.Words for Java에서 OOXML 형식으로 문서 저장 소개

이 가이드에서는 **encrypt docx with password** 방법과 Aspose.Words for Java를 사용하여 OOXML 형식으로 문서를 저장하는 방법을 배웁니다. OOXML(Office Open XML)은 Microsoft Word 및 기타 많은 오피스 애플리케이션에서 사용하는 최신 파일 형식입니다. 가장 일반적인 옵션—비밀번호 보호, 호환성 수준, 속성 업데이트, 레거시 문자 처리, 그리고 **how to change compression level**—을 단계별로 살펴보며 필요에 맞게 출력물을 조정할 수 있습니다.

## 빠른 답변
- **How can I protect a Word file?** 저장하기 전에 `OoxmlSaveOptions.setPassword("yourPassword")`를 사용합니다.  
- **What OOXML compliance level should I choose?** 최신 Office 버전과의 최대 호환성을 위해 ISO 29500 2008 Strict를 선택합니다.  
- **Can I keep legacy control characters?** 예, `setKeepLegacyControlChars(true)`를 활성화합니다.  
- **How do I change the compression level?** 필요에 따라 `setCompressionLevel(CompressionLevel.SUPER_FAST)` 또는 `MAXIMUM`을 설정합니다.  
- **Do these options affect file size?** 압축 수준 및 레거시 문자 처리는 최종 .docx 파일 크기에 눈에 띄게 영향을 줄 수 있습니다.

## “encrypt docx with password”란 무엇인가요?
DOCX 파일을 암호화한다는 것은 문서가 AES‑256 암호화된 상태로 저장되어 Word나 호환 가능한 뷰어에서 열기 위해 비밀번호가 필요함을 의미합니다. 이는 파일을 이메일, 클라우드 스토리지, 인트라넷 포털 등으로 공유할 때 기밀 정보를 보호하는 데 필수적입니다.

## OOXML 저장 옵션을 사용하는 이유
- **Security:** 비밀번호 보호는 무단 접근을 방지합니다.  
- **Compatibility:** 호환성 설정은 파일이 다양한 Word 버전에서 작동하도록 보장합니다.  
- **Performance:** 압축을 조정하면 저장 속도를 높이거나 파일 크기를 줄일 수 있습니다.  
- **Preservation:** 레거시 제어 문자를 유지하면 오래된 문서를 변환할 때 원본 충실도를 유지합니다.

## 사전 요구 사항
- Aspose.Words for Java 라이브러리를 프로젝트에 추가(Maven/Gradle 또는 수동 JAR).  
- Java 8 이상.  
- 처리하려는 소스 문서(`.docx` 또는 `.doc`).

## 비밀번호 암호화로 문서 저장

문서를 OOXML 형식으로 저장하면서 비밀번호로 암호화할 수 있습니다. 방법은 다음과 같습니다:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Pro tip:** 강력한 비밀번호를 선택하고 안전하게 보관하세요; 암호화된 파일에서 비밀번호를 복구할 수 없습니다.

## OOXML 호환성 설정

문서를 저장할 때 OOXML 호환성 수준을 지정할 수 있습니다. 예를 들어 ISO 29500:2008 (Strict)으로 설정할 수 있습니다. 방법은 다음과 같습니다:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## 마지막 저장 시간 속성 업데이트

저장 시 문서의 "Last Saved Time" 속성을 업데이트하도록 선택할 수 있습니다. 방법은 다음과 같습니다:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## 레거시 제어 문자 유지

문서에 레거시 제어 문자가 포함된 경우 저장하면서 이를 유지하도록 선택할 수 있습니다. 방법은 다음과 같습니다:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## OOXML 저장 시 압축 수준 변경 방법

문서를 저장할 때 압축 수준을 조정할 수 있습니다. 예를 들어 최소 압축을 위해 `SUPER_FAST`로, 가장 작은 파일 크기를 위해 `MAXIMUM`으로 설정할 수 있습니다. 방법은 다음과 같습니다:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

위는 Aspose.Words for Java를 사용하여 OOXML 형식으로 문서를 저장할 때 사용할 수 있는 주요 옵션 및 설정 중 일부입니다. 필요에 따라 더 많은 옵션을 탐색하고 문서 저장 프로세스를 맞춤 설정하십시오.

## Aspose.Words for Java에서 OOXML 형식으로 문서 저장을 위한 전체 소스 코드

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## 결론

이 포괄적인 가이드에서는 **encrypt docx with password** 방법과 Aspose.Words for Java를 사용하여 OOXML 형식으로 문서를 저장하는 방법을 살펴보았습니다. 파일을 보호하거나, 엄격한 OOXML 호환성을 보장하거나, 문서 속성을 업데이트하거나, 레거시 제어 문자를 유지하거나, **change compression level**이 필요할 때 Aspose.Words는 요구 사항을 충족하는 다목적 도구 세트를 제공합니다.

## 자주 묻는 질문

**Q: How do I remove password protection from a password‑protected document?**  
A: 올바른 비밀번호로 문서를 연 다음 `OoxmlSaveOptions`에 비밀번호를 지정하지 않고 저장합니다. 이렇게 하면 보호되지 않은 복사본이 생성됩니다.

**Q: Can I set custom properties when saving a document in OOXML format?**  
A: 예. `save()`를 호출하기 전에 `Document` 객체의 `BuiltInDocumentProperties`와 `CustomDocumentProperties`를 사용합니다.

**Q: What is the default compression level when saving a document in OOXML format?**  
A: 기본값은 `CompressionLevel.NORMAL`입니다. 속도를 위해 `SUPER_FAST`로, 가장 작은 파일 크기를 위해 `MAXIMUM`으로 전환할 수 있습니다.

**Q: Will enabling `keepLegacyControlChars` affect compatibility with modern Word versions?**  
A: 최신 Word는 레거시 제어 문자가 포함된 파일을 열 수 있지만, 일부 오래된 기능은 다르게 표시될 수 있습니다. 정확한 원본 내용을 보존해야 할 때만 이 옵션을 사용하십시오.

**Q: Is it possible to combine multiple save options (e.g., password + compression) in a single call?**  
A: 물론 가능합니다. `doc.save()`에 전달하기 전에 단일 `OoxmlSaveOptions` 인스턴스에 원하는 모든 속성을 구성하면 됩니다.

---

**Last Updated:** 2026-01-09  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}