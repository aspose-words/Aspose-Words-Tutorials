---
date: 2026-01-01
description: Aspose.Words for Java DocumentBuilder를 사용하여 양식 필드를 만들고 텍스트, 표, 이미지, 하이퍼링크
  등을 추가하는 방법을 배웁니다. 개발자를 위한 단계별 가이드.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java에서 DocumentBuilder를 사용하여 양식 필드를 만들고 콘텐츠를 추가하는 방법
url: /ko/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java의 DocumentBuilder를 사용하여 콘텐츠 추가

## Aspose.Words for Java의 DocumentBuilder를 사용하여 콘텐츠 추가 소개

## 빠른 답변
- **폼 필드를 어떻게 생성하나요?** `DocumentBuilder`에서 `insertTextInput`, `insertCheckBox` 또는 `insertComboBox`를 사용합니다.
- **일반 텍스트를 추가하는 메서드는?** `builder.write("Your text")` 또는 `builder.writeln("Your text")`를 호출합니다.
- **수평 구분선을 삽입할 수 있나요?** 예—`builder.insertHorizontalRule()`가 선 구분자를 추가합니다.
- **HTML을 삽입하려면?** `builder.insertHtml("<p>HTML content</p>")`를 사용합니다.
- **인라인 이미지를 추가하려면?** `builder.insertImage("path/to/image.png")`가 텍스트 흐름 내에 이미지를 배치합니다.

## DocumentBuilder란 무엇이며 폼 필드 생성에 왜 사용하는가?

`DocumentBuilder`는 Aspose.Words의 유창한 API로, 프로그래밍 방식으로 Word 문서를 구성하고 편집합니다. 저수준 OpenXML 구조를 추상화하여 **폼 필드**와 같은 추가하고자 하는 *무엇*에 집중하게 해 주며, XML이 어떻게 보이는지는 신경 쓰지 않아도 됩니다. 이는 동적 폼, 계약서 또는 사용자 상호작용이 필요한 모든 문서를 생성하는 데 이상적입니다.

## 전제 조건

시작하기 전에 프로젝트에 Aspose.Words for Java 라이브러리가 설치되어 있는지 확인하십시오. [here](https://releases.aspose.com/words/java/)에서 다운로드할 수 있습니다.

## 텍스트 추가 (텍스트 추가 방법)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## 표 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## 수평 구분선 추가 (수평 구분선 추가)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## 폼 필드 추가 (폼 필드 생성)

### 텍스트 입력 폼 필드

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### 체크 박스 폼 필드

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### 콤보 박스 폼 필드

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## HTML 추가 (HTML 삽입)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## 하이퍼링크 추가 (하이퍼링크 추가 방법)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## 목차 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## 이미지 추가

### 인라인 이미지 (인라인 이미지 삽입)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### 플로팅 이미지

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## 단락 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## 커서 이동 (단계 10)

문서 내에서 커서 위치를 `moveToParagraph`, `moveToCell` 등과 같은 메서드를 사용하여 제어할 수 있습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

이것은 Aspose.Words for Java의 `DocumentBuilder`를 사용하여 수행할 수 있는 일반적인 작업들입니다. 보다 고급 기능 및 사용자 지정 옵션은 라이브러리 문서를 살펴보세요. 즐거운 문서 제작 되세요!

## 결론

이 포괄적인 가이드에서는 Aspose.Words for Java의 `DocumentBuilder`를 사용하여 **폼 필드**를 생성하고 텍스트, 표, 수평 구분선, HTML, 하이퍼링크, 목차, 이미지, 서식이 적용된 단락 및 커서 탐색 등 다양한 유형의 콘텐츠를 추가하는 방법을 보여주었습니다. 이제 프로그래밍 방식으로 동적이고 인터랙티브한 Word 문서를 생성할 수 있는 탄탄한 기반을 갖추게 되었습니다.

## FAQ

### Q: Aspose.Words for Java란 무엇인가요?

A: Aspose.Words for Java는 개발자가 Microsoft Word 문서를 프로그래밍 방식으로 생성, 수정 및 조작할 수 있도록 하는 Java 라이브러리입니다. 문서 생성, 서식 지정 및 콘텐츠 삽입을 위한 다양한 기능을 제공합니다.

### Q: 문서에 목차를 어떻게 추가할 수 있나요?

A: 목차를 추가하려면 `DocumentBuilder`를 사용하여 TOC 필드를 삽입하고, 콘텐츠를 추가한 후 `doc.updateFields()`를 호출합니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Aspose.Words for Java를 사용하여 문서에 이미지를 어떻게 삽입하나요?

A: `DocumentBuilder`를 사용하면 인라인 이미지와 플로팅 이미지를 모두 삽입할 수 있습니다.

#### 인라인 이미지:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### 플로팅 이미지:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: 콘텐츠를 추가할 때 텍스트와 단락을 서식 지정할 수 있나요?

A: 예, `DocumentBuilder`를 사용하여 텍스트와 단락을 서식 지정할 수 있습니다. 콘텐츠를 쓰기 전에 글꼴 속성, 단락 정렬, 들여쓰기 등을 설정하십시오.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: 문서 내 특정 위치로 커서를 이동하려면 어떻게 하나요?

A: `moveToParagraph`, `moveToCell` 등과 같은 메서드를 사용하여 새 콘텐츠를 삽입하기 전에 커서를 원하는 위치에 배치할 수 있습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

이 답변들은 Aspose.Words for Java의 `DocumentBuilder`를 사용할 때 가장 일반적인 시나리오를 다룹니다. 자세한 내용은 [library's documentation](https://reference.aspose.com/words/java/)을 참고하거나 Aspose.Words 커뮤니티에 참여하여 지원을 받으세요.

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}