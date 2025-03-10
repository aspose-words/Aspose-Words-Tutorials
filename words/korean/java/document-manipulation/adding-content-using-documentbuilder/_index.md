---
title: Java용 Aspose.Words에서 DocumentBuilder를 사용하여 콘텐츠 추가
linktitle: DocumentBuilder를 사용하여 콘텐츠 추가
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java로 마스터 문서 생성. 텍스트, 표, 이미지 등을 추가하는 단계별 가이드. 멋진 Word 문서를 손쉽게 만드세요.
weight: 26
url: /ko/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 DocumentBuilder를 사용하여 콘텐츠 추가


## Aspose.Words for Java에서 DocumentBuilder를 사용하여 콘텐츠 추가 소개

이 단계별 가이드에서는 Aspose.Words for Java의 DocumentBuilder를 사용하여 Word 문서에 다양한 유형의 콘텐츠를 추가하는 방법을 살펴보겠습니다. 텍스트, 표, 수평선, 양식 필드, HTML, 하이퍼링크, 목차, 인라인 및 플로팅 이미지, 문단 등을 삽입하는 방법을 다룹니다. 시작해 봅시다!

## 필수 조건

 시작하기 전에 프로젝트에 Aspose.Words for Java 라이브러리가 설정되어 있는지 확인하세요. 여기에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/java/).

## 텍스트 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 간단한 텍스트 문단 삽입
builder.write("This is a simple text paragraph.");

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## 테이블 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//테이블 시작
Table table = builder.startTable();

// 셀과 내용 삽입
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// 테이블 종료
builder.endTable();

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## 수평선 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 수평선 삽입
builder.insertHorizontalRule();

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## 양식 필드 추가

### 텍스트 입력 양식 필드

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 텍스트 입력 양식 필드 삽입
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

### 체크박스 양식 필드

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 체크박스 양식 필드 삽입
builder.insertCheckBox("CheckBox", true, true, 0);

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

### 콤보 상자 양식 필드

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 콤보 상자의 항목 정의
String[] items = { "Option 1", "Option 2", "Option 3" };

// 콤보 상자 양식 필드 삽입
builder.insertComboBox("DropDown", items, 0);

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## HTML 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// HTML 콘텐츠 삽입
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## 하이퍼링크 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 하이퍼링크 삽입
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", 거짓);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## 목차 추가

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 목차 삽입
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// 문서 내용 추가
// ...

// 목차 업데이트
doc.updateFields();

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## 이미지 추가

### 인라인 이미지

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 인라인 이미지 삽입
builder.insertImage("path/to/your/image.png");

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

### 떠있는 이미지

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 떠있는 이미지 삽입
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## 문단 추가하기

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 문단 서식 설정
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

// 문단 삽입
builder.writeln("This is a formatted paragraph.");

// 문서를 저장하세요
doc.save("path/to/your/document.docx");
```

## 10단계: 커서 이동

 다음과 같은 다양한 방법을 사용하여 문서 내에서 커서 위치를 제어할 수 있습니다.`moveToParagraph`, `moveToCell`그리고 더 많은 것들. 여기에 예가 있습니다:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 커서를 특정 문단으로 이동합니다.
builder.moveToParagraph(2, 0);

// 새로운 커서 위치에 콘텐츠 추가
builder.writeln("This is the 3rd paragraph.");
```

다음은 Java의 DocumentBuilder용 Aspose.Words를 사용하여 수행할 수 있는 몇 가지 일반적인 작업입니다. 더 고급 기능과 사용자 지정 옵션은 라이브러리 설명서를 살펴보세요. 행복한 문서 생성을 기원합니다!


## 결론

이 포괄적인 가이드에서는 Aspose.Words for Java의 DocumentBuilder가 Word 문서에 다양한 유형의 콘텐츠를 추가하는 기능을 살펴보았습니다. 텍스트, 표, 가로줄, 양식 필드, HTML, 하이퍼링크, 목차, 이미지, 문단 및 커서 이동을 다루었습니다.

## 자주 묻는 질문

### 질문: Java용 Aspose.Words란 무엇인가요?

A: Aspose.Words for Java는 개발자가 Microsoft Word 문서를 프로그래밍 방식으로 만들고, 수정하고, 조작할 수 있는 Java 라이브러리입니다. 문서 생성, 서식 지정 및 콘텐츠 삽입을 위한 광범위한 기능을 제공합니다.

### 질문: 문서에 목차를 추가하려면 어떻게 해야 하나요?

A: 목차를 추가하려면 다음을 사용하세요.`DocumentBuilder` 문서에 목차 필드를 삽입합니다. 목차를 채우기 위해 콘텐츠를 추가한 후 문서의 필드를 업데이트해야 합니다. 다음은 예입니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 목차 필드 삽입
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// 문서 내용 추가
// ...

// 목차 업데이트
doc.updateFields();
```

### 질문: Aspose.Words for Java를 사용하여 문서에 이미지를 삽입하려면 어떻게 해야 합니까?

 A: 인라인 및 플로팅 이미지를 삽입할 수 있습니다.`DocumentBuilder`. 다음은 두 가지 모두의 예입니다.

#### 인라인 이미지:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 인라인 이미지 삽입
builder.insertImage("path/to/your/image.png");
```

#### 떠있는 이미지:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 떠있는 이미지 삽입
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### 질문: 콘텐츠를 추가할 때 텍스트와 문단을 서식 지정할 수 있나요?

 A: 예, 다음을 사용하여 텍스트와 문단을 서식 지정할 수 있습니다.`DocumentBuilder`. 글꼴 속성, 문단 정렬, 들여쓰기 등을 설정할 수 있습니다. 다음은 예입니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 글꼴 및 문단 서식 설정
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

// 서식이 지정된 문단 삽입
builder.writeln("This is a formatted paragraph.");
```

### 질문: 문서 내의 특정 위치로 커서를 이동하려면 어떻게 해야 하나요?

 A: 다음과 같은 방법을 사용하여 커서 위치를 제어할 수 있습니다.`moveToParagraph`, `moveToCell`그리고 더 많은 것들. 여기에 예가 있습니다:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 커서를 특정 문단으로 이동합니다.
builder.moveToParagraph(2, 0);

// 새로운 커서 위치에 콘텐츠 추가
builder.writeln("This is the 3rd paragraph.");
```

다음은 Aspose.Words for Java의 DocumentBuilder를 시작하는 데 도움이 되는 몇 가지 일반적인 질문과 답변입니다. 질문이 더 있거나 추가 지원이 필요한 경우 다음을 참조하십시오.[도서관 문서](https://reference.aspose.com/words/java/) 또는 Aspose.Words 커뮤니티와 지원 리소스에서 도움을 구하세요.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
