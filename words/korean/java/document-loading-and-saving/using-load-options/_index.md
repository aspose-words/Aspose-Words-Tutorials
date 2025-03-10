---
title: Java용 Aspose.Words에서 로드 옵션 사용
linktitle: 로드 옵션 사용
second_title: Aspose.Words Java 문서 처리 API
description: Java용 Aspose.Words에서 로드 옵션 마스터링. 효율적인 Java 문서 처리를 위해 문서 로딩을 사용자 지정하고, 암호화를 처리하고, 모양을 변환하고, Word 버전을 설정하고, 기타 작업을 수행합니다.
weight: 11
url: /ko/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 로드 옵션 사용


## Aspose.Words for Java에서 로드 옵션 작업 소개

이 튜토리얼에서는 Aspose.Words for Java에서 로드 옵션을 사용하는 방법을 살펴보겠습니다. 로드 옵션을 사용하면 문서를 로드하고 처리하는 방법을 사용자 지정할 수 있습니다. 더티 필드 업데이트, 암호화된 문서 로드, 셰이프를 Office Math로 변환, MS Word 버전 설정, 임시 폴더 지정, 경고 처리, 메타파일을 PNG로 변환하는 등 다양한 시나리오를 다룹니다. 단계별로 살펴보겠습니다.

## 더티 필드 업데이트

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 이 코드 조각은 문서에서 더티 필드를 업데이트하는 방법을 보여줍니다.`setUpdateDirtyFields(true)` 이 방법은 문서 로딩 중에 더티 필드가 업데이트되도록 하는 데 사용됩니다.

## 암호화된 문서 로드

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 여기서는 비밀번호를 사용하여 암호화된 문서를 로드합니다.`LoadOptions` 생성자는 문서 비밀번호를 수락하며 문서를 저장할 때 새 비밀번호를 지정할 수도 있습니다.`OdtSaveOptions`.

## 모양을 사무실 수학으로 변환

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 이 코드는 문서 로딩 중에 모양을 Office Math 개체로 변환하는 방법을 보여줍니다.`setConvertShapeToOfficeMath(true)`이 방법을 사용하면 이러한 변환이 가능합니다.

## MS Word 버전 설정

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 문서 로딩을 위해 MS Word 버전을 지정할 수 있습니다. 이 예에서 우리는 다음을 사용하여 버전을 Microsoft Word 2010으로 설정했습니다.`setMswVersion`.

## 임시 폴더 사용

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 임시 폴더를 설정하여`setTempFolder`문서 처리 중에 임시 파일이 저장되는 위치를 제어할 수 있습니다.

## 경고 콜백

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // 문서 로딩 중에 발생하는 경고를 처리합니다.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

이 코드는 문서 로딩 중 경고를 처리하기 위해 경고 콜백을 설정하는 방법을 보여줍니다. 경고가 발생할 때 애플리케이션의 동작을 사용자 지정할 수 있습니다.

## 메타파일을 PNG로 변환

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 문서 로딩 중에 메타파일(예: WMF)을 PNG 이미지로 변환하려면 다음을 사용할 수 있습니다.`setConvertMetafilesToPng(true)` 방법.

## Aspose.Words for Java에서 로드 옵션 작업을 위한 전체 소스 코드

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// 기본적으로 MS Word 2019 사양에 따라 문서를 로드하는 새 LoadOptions 개체를 만듭니다.
	// 로딩 버전을 Microsoft Word 2010으로 변경하세요.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		//문서를 로딩하는 동안 발생하는 경고와 해당 세부 정보를 인쇄합니다.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## 결론

이 튜토리얼에서는 Aspose.Words for Java에서 로드 옵션으로 작업하는 다양한 측면을 살펴보았습니다. 로드 옵션은 문서가 로드되고 처리되는 방식을 사용자 지정하는 데 중요한 역할을 하며, 문서 처리를 특정 요구 사항에 맞게 조정할 수 있습니다. 이 가이드에서 다룬 핵심 요점을 다시 살펴보겠습니다.

## 자주 묻는 질문

### 문서 로딩 중에 경고가 발생하면 어떻게 처리할 수 있나요?

 표시된 대로 경고 콜백을 설정할 수 있습니다.`warningCallback()` 위의 방법. 사용자 정의`DocumentLoadingWarningCallback` 애플리케이션의 요구 사항에 따라 경고를 처리하는 클래스입니다.

### 문서를 로드할 때 도형을 Office Math 개체로 변환할 수 있나요?

 예, 다음을 사용하여 모양을 Office Math 개체로 변환할 수 있습니다.`loadOptions.setConvertShapeToOfficeMath(true)`.

### 문서 로딩을 위한 MS Word 버전을 어떻게 지정합니까?

 사용`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` 문서 로딩을 위한 MS Word 버전을 지정합니다.

###  의 목적은 무엇입니까?`setTempFolder` method in Load Options?

 그만큼`setTempFolder`이 방법을 사용하면 문서 처리 중에 임시 파일이 저장되는 폴더를 지정할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
