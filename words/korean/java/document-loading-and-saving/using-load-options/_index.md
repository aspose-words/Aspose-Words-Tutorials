---
date: 2025-12-27
description: Aspose.Words for Java에서 LoadOptions를 설정하는 방법을 배우세요. 여기에는 임시 폴더 지정, Word
  버전 설정, 메타파일을 PNG로 변환, 그리고 도형을 수식으로 변환하여 유연한 문서 처리를 수행하는 방법이 포함됩니다.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java에서 LoadOptions 설정 방법
url: /ko/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 LoadOptions 설정 방법

이 튜토리얼에서는 Aspose.Words for Java를 사용할 때 다양한 실제 시나리오에 맞게 **LoadOptions를 설정하는 방법**을 단계별로 살펴봅니다. LoadOptions를 사용하면 문서를 여는 방식을 세밀하게 제어할 수 있습니다—필드 업데이트, 암호화된 파일 작업, 도형을 Office Math로 변환, 임시 데이터 저장 위치 지정 등. 끝까지 읽으면 애플리케이션 요구에 정확히 맞는 로딩 동작을 커스터마이즈할 수 있습니다.

## 빠른 답변
- **LoadOptions란?** Aspose.Words가 문서를 로드하는 방식을 영향을 주는 구성 객체입니다.  
- **로드 중에 필드를 업데이트할 수 있나요?** 예—`setUpdateDirtyFields(true)`를 설정합니다.  
- **비밀번호가 설정된 파일을 여는 방법은?** `LoadOptions` 생성자에 비밀번호를 전달합니다.  
- **임시 폴더를 변경할 수 있나요?** `setTempFolder("path")`를 사용합니다.  
- **도형을 Office Math로 변환하는 메서드는?** `setConvertShapeToOfficeMath(true)`입니다.

## LoadOptions를 사용하는 이유
LoadOptions를 활용하면 로드 후 추가 처리 단계를 없앨 수 있고, 메모리 사용량을 줄이며, 문서가 정확히 원하는 방식으로 해석되도록 할 수 있습니다. 예를 들어, 로드 시 메타파일을 PNG로 변환하면 이후 래스터화 문제를 방지하고, MS Word 버전을 지정하면 레거시 파일의 레이아웃 충실도를 유지할 수 있습니다.

## 사전 요구 사항
- Java 17 이상  
- Aspose.Words for Java (최신 버전)  
- 프로덕션 사용을 위한 유효한 Aspose 라이선스  

## 단계별 가이드

### 더티 필드 업데이트

문서에 편집되었지만 아직 새로 고쳐지지 않은 필드가 있는 경우, 로드 중에 Aspose.Words가 자동으로 업데이트하도록 할 수 있습니다.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*`setUpdateDirtyFields(true)` 호출은 문서가 열리는 즉시 모든 더티 필드가 재계산되도록 보장합니다.*

### 암호화된 문서 로드

소스 파일에 비밀번호가 설정되어 있다면 `LoadOptions` 인스턴스를 만들 때 비밀번호를 제공하면 됩니다. 다른 형식으로 저장할 때 새 비밀번호를 설정할 수도 있습니다.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### 도형을 Office Math로 변환

레거시 문서에서는 수식이 도형 형태로 저장되는 경우가 있습니다. 이 옵션을 활성화하면 해당 도형을 네이티브 Office Math 객체로 변환하여 이후 편집이 쉬워집니다.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### MS Word 버전 지정

대상 Word 버전을 지정하면 라이브러리가 올바른 렌더링 규칙을 선택하게 되며, 특히 오래된 파일 형식을 다룰 때 유용합니다.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### 임시 폴더 사용

대용량 문서는 이미지 추출 등으로 임시 파일을 생성할 수 있습니다. 이러한 파일을 원하는 폴더로 지정하면 샌드박스 환경에서 유용합니다.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### 경고 콜백

로드 중에 Aspose.Words가 경고(예: 지원되지 않는 기능)를 발생시킬 수 있습니다. 콜백을 구현하면 이러한 이벤트를 기록하거나 처리할 수 있습니다.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### 메타파일을 PNG로 변환

WMF와 같은 메타파일을 로드 시 PNG로 래스터화하면 플랫폼 간 일관된 렌더링을 보장합니다.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Aspose.Words for Java에서 Load Options를 활용한 전체 소스 코드

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## 일반 사용 사례 및 팁

- **배치 변환 파이프라인** – `setTempFolder`와 스케줄러 작업을 결합해 수백 개 파일을 시스템 임시 디렉터리를 채우지 않고 처리합니다.  
- **레거시 문서 마이그레이션** – `setMswVersion`과 `setConvertShapeToOfficeMath`를 함께 사용해 오래된 엔지니어링 문서를 최신 형식으로 옮기면서 수식을 보존합니다.  
- **보안 문서 처리** – `loadEncryptedDocument`와 `OdtSaveOptions`를 조합해 파일을 새로운 비밀번호로 재암호화하고 다른 형식으로 저장합니다.  

## 자주 묻는 질문

**Q: 문서 로드 중에 발생하는 경고를 어떻게 처리하나요?**  
A: *Warning Callback* 예제와 같이 사용자 정의 `IWarningCallback`을 구현하고 `loadOptions.setWarningCallback(...)`에 등록합니다. 이를 통해 경고 심각도에 따라 로그를 남기거나 무시하거나 중단할 수 있습니다.

**Q: 로드 시 도형을 Office Math 객체로 변환할 수 있나요?**  
A: 예—`loadOptions.setConvertShapeToOfficeMath(true)`를 `Document` 생성 전에 호출하면 호환 가능한 도형이 자동으로 네이티브 Office Math 객체로 교체됩니다.

**Q: 문서 로드에 사용할 MS Word 버전을 어떻게 지정하나요?**  
A: `loadOptions.setMswVersion(MsWordVersion.WORD_2010)`(또는 다른 enum 값)으로 Aspose.Words에 적용할 Word 버전의 렌더링 규칙을 알려줍니다.

**Q: LoadOptions의 `setTempFolder` 메서드 목적은 무엇인가요?**  
A: 로드 중에 생성되는 모든 임시 파일(예: 추출된 이미지)을 사용자가 제어하는 폴더로 지정합니다. 시스템 임시 디렉터리 접근이 제한된 환경에서 필수적입니다.

**Q: 로드 시 WMF와 같은 메타파일을 PNG로 변환할 수 있나요?**  
A: 물론입니다—`loadOptions.setConvertMetafilesToPng(true)`를 활성화하면 래스터 이미지가 PNG로 저장되어 최신 뷰어와의 호환성이 향상됩니다.

## 결론

Aspose.Words for Java에서 **LoadOptions 설정 방법**에 대해 더티 필드 업데이트, 암호화 파일 처리, 도형 변환, Word 버전 지정, 임시 저장소 지정 등 핵심 기술을 살펴보았습니다. 이러한 옵션을 활용하면 다양한 입력 시나리오에 맞는 견고하고 고성능의 문서 처리 파이프라인을 구축할 수 있습니다.

---

**마지막 업데이트:** 2025-12-27  
**테스트 환경:** Aspose.Words for Java 24.11  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}