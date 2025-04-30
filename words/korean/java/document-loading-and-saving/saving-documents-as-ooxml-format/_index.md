---
"description": "Aspose.Words for Java를 사용하여 OOXML 형식으로 문서를 저장하는 방법을 알아보세요. 파일을 손쉽게 보호하고, 최적화하고, 맞춤 설정하세요."
"linktitle": "OOXML 형식으로 문서 저장"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Java용 Aspose.Words에서 OOXML 형식으로 문서 저장"
"url": "/ko/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 OOXML 형식으로 문서 저장


## Aspose.Words for Java에서 OOXML 형식으로 문서 저장 소개

이 가이드에서는 Aspose.Words for Java를 사용하여 문서를 OOXML 형식으로 저장하는 방법을 살펴보겠습니다. OOXML(Office Open XML)은 Microsoft Word 및 기타 오피스 애플리케이션에서 사용되는 파일 형식입니다. OOXML 형식으로 문서를 저장하기 위한 다양한 옵션과 설정을 살펴보겠습니다.

## 필수 조건

시작하기에 앞서, 프로젝트에 Aspose.Words for Java 라이브러리가 설정되어 있는지 확인하세요.

## 암호 암호화를 사용하여 문서 저장

OOXML 형식으로 문서를 저장할 때 비밀번호를 사용하여 암호화할 수 있습니다. 방법은 다음과 같습니다.

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// 문서를 로드하세요
Document doc = new Document("Document.docx");

// OoxmlSaveOptions를 생성하고 비밀번호를 설정합니다.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// 암호화하여 문서 저장
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXML 규정 준수 설정

문서를 저장할 때 OOXML 준수 수준을 지정할 수 있습니다. 예를 들어 ISO 29500:2008(엄격)로 설정할 수 있습니다. 방법은 다음과 같습니다.

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// 문서를 로드하세요
Document doc = new Document("Document.docx");

// Word 2016에 최적화
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// OoxmlSaveOptions를 생성하고 규정 준수 수준을 설정합니다.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// 규정 준수 설정으로 문서 저장
doc.save("ComplianceDoc.docx", saveOptions);
```

## 마지막으로 저장된 시간 속성 업데이트

문서를 저장할 때 "마지막으로 저장된 시간" 속성을 업데이트하도록 선택할 수 있습니다. 방법은 다음과 같습니다.

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// 문서를 로드하세요
Document doc = new Document("Document.docx");

// OoxmlSaveOptions를 생성하고 마지막으로 저장된 시간 속성 업데이트를 활성화합니다.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// 업데이트된 속성으로 문서를 저장합니다.
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## 레거시 제어 문자 유지

문서에 기존 제어 문자가 포함된 경우, 저장하는 동안 해당 문자를 유지하도록 선택할 수 있습니다. 방법은 다음과 같습니다.

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// 레거시 제어 문자가 있는 문서 로드
Document doc = new Document("LegacyControlChars.doc");

// FLAT_OPC 형식으로 OoxmlSaveOptions를 생성하고 레거시 제어 문자 유지를 활성화합니다.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// 레거시 제어 문자로 문서 저장
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## 압축 레벨 설정

문서를 저장할 때 압축 수준을 조정할 수 있습니다. 예를 들어, 최소 압축을 위해 SUPER_FAST로 설정할 수 있습니다. 방법은 다음과 같습니다.

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// 문서를 로드하세요
Document doc = new Document("Document.docx");

// OoxmlSaveOptions를 생성하고 압축 수준을 설정합니다.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// 지정된 압축 수준으로 문서를 저장합니다.
doc.save("FastCompressionDoc.docx", saveOptions);
```

Aspose.Words for Java를 사용하여 OOXML 형식으로 문서를 저장할 때 사용할 수 있는 주요 옵션과 설정은 다음과 같습니다. 필요에 따라 더 많은 옵션을 살펴보고 문서 저장 프로세스를 사용자 지정할 수 있습니다.

## Aspose.Words for Java에서 문서를 OOXML 형식으로 저장하기 위한 전체 소스 코드

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

이 종합 가이드에서는 Aspose.Words for Java를 사용하여 문서를 OOXML 형식으로 저장하는 방법을 살펴보았습니다. 문서를 비밀번호로 암호화하거나, 특정 OOXML 표준을 준수하거나, 문서 속성을 업데이트하거나, 기존 제어 문자를 유지하거나, 압축 수준을 조정하는 등 어떤 작업이든 Aspose.Words는 사용자의 요구 사항을 충족하는 다양한 도구 세트를 제공합니다.

## 자주 묻는 질문

### 암호로 보호된 문서에서 암호 보호를 제거하려면 어떻게 해야 하나요?

암호로 보호된 문서의 암호 보호를 해제하려면, 올바른 암호로 문서를 연 다음 저장 옵션에서 암호를 지정하지 않고 저장하면 됩니다. 이렇게 하면 암호 보호 없이 문서가 저장됩니다.

### OOXML 형식으로 문서를 저장할 때 사용자 정의 속성을 설정할 수 있나요?

네, OOXML 형식으로 저장하기 전에 문서의 사용자 지정 속성을 설정할 수 있습니다. `BuiltInDocumentProperties` 그리고 `CustomDocumentProperties` 작성자, 제목, 키워드, 사용자 정의 속성 등 다양한 속성을 설정하는 클래스입니다.

### OOXML 형식으로 문서를 저장할 때 기본 압축 수준은 무엇입니까?

Aspose.Words for Java를 사용하여 OOXML 형식으로 문서를 저장할 때 기본 압축 수준은 다음과 같습니다. `NORMAL`압축 수준을 변경할 수 있습니다. `SUPER_FAST` 또는 `MAXIMUM` 필요에 따라.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}