---
"description": "Aspose.Words for Java를 사용하여 Word 문서를 Markdown으로 변환하는 방법을 알아보세요. 이 단계별 가이드에서는 표 정렬, 이미지 처리 등에 대해 다룹니다."
"linktitle": "문서를 마크다운으로 저장"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Java용 Aspose.Words에서 문서를 마크다운으로 저장하기"
"url": "/ko/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 문서를 마크다운으로 저장하기


## Java용 Aspose.Words에서 문서를 마크다운으로 저장하는 방법 소개

이 단계별 가이드에서는 Aspose.Words for Java를 사용하여 문서를 마크다운으로 저장하는 방법을 보여드리겠습니다. 마크다운은 텍스트 문서의 서식을 지정하는 데 일반적으로 사용되는 가벼운 마크업 언어입니다. Aspose.Words for Java를 사용하면 Word 문서를 마크다운 형식으로 쉽게 변환할 수 있습니다. 표 내용 정렬 및 이미지 처리 등 마크다운 파일 저장의 다양한 측면을 다룹니다.

## 필수 조건

시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

- 시스템에 Java Development Kit(JDK)가 설치되어 있어야 합니다.
- Aspose.Words for Java 라이브러리입니다. 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/java/).

## 1단계: Word 문서 만들기

먼저, 나중에 마크다운 형식으로 변환할 Word 문서를 만들어 보겠습니다. 필요에 따라 이 문서를 사용자 정의할 수 있습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 두 개의 셀이 있는 표 삽입
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// 문서를 마크다운으로 저장하세요
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

이 예제에서는 두 개의 셀로 구성된 간단한 표를 만들고 각 셀 내 문단의 정렬을 설정합니다. 그런 다음, 다음 명령을 사용하여 문서를 마크다운으로 저장합니다. `MarkdownSaveOptions`.

## 2단계: 표 내용 정렬 사용자 지정

Aspose.Words for Java를 사용하면 마크다운으로 저장할 때 표 내용의 정렬을 사용자 지정할 수 있습니다. 표 내용을 왼쪽, 오른쪽, 가운데 정렬하거나 각 표 열의 첫 번째 문단을 기준으로 자동으로 정렬되도록 할 수 있습니다.

표 내용 정렬을 사용자 지정하는 방법은 다음과 같습니다.

```java
// 테이블 내용 정렬을 왼쪽으로 설정
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// 표 내용 정렬을 오른쪽으로 설정하세요
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// 테이블 내용 정렬을 가운데로 설정
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// 표 내용 정렬을 자동(첫 번째 문단에 따라 결정)으로 설정합니다.
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

변경하여 `TableContentAlignment` 속성을 사용하면 Markdown으로 변환할 때 표 내부의 콘텐츠가 어떻게 정렬되는지 제어할 수 있습니다.

## 3단계: 이미지 처리

마크다운 문서에 이미지를 포함하려면 이미지가 있는 폴더를 지정해야 합니다. Aspose.Words for Java를 사용하면 이미지 폴더를 다음과 같이 설정할 수 있습니다. `MarkdownSaveOptions`.

이미지 폴더를 설정하고 이미지가 포함된 문서를 저장하는 방법은 다음과 같습니다.

```java
// 이미지가 포함된 문서를 로드합니다
Document doc = new Document("document_with_images.docx");

// 이미지 폴더 경로 설정
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// 이미지와 함께 문서를 저장합니다
doc.save("document_with_images.md", saveOptions);
```

교체를 꼭 해주세요 `"document_with_images.docx"` 이미지가 포함된 Word 문서의 경로와 함께 `"images_folder/"` 이미지가 저장된 폴더의 실제 경로를 포함합니다.

## Java용 Aspose.Words에서 문서를 마크다운으로 저장하기 위한 전체 소스 코드

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// 표 안의 모든 문단을 정렬합니다.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// 이 경우 정렬은 해당 표 열의 첫 번째 문단에서 적용됩니다.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## 결론

이 가이드에서는 Aspose.Words for Java를 사용하여 문서를 마크다운으로 저장하는 방법을 살펴보았습니다. Word 문서 생성, 표 내용 정렬 사용자 지정, 그리고 마크다운 파일 이미지 처리 방법을 다루었습니다. 이제 Word 문서를 마크다운 형식으로 효율적으로 변환하여 다양한 출판 플랫폼 및 문서 작성 요구에 적합하게 만들 수 있습니다.

## 자주 묻는 질문

### Java용 Aspose.Words를 어떻게 설치하나요?

Aspose.Words for Java는 Java 프로젝트에 라이브러리를 포함시켜 설치할 수 있습니다. 라이브러리는 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/java/) 설명서에 제공된 설치 지침을 따르세요.

### 표와 이미지가 있는 복잡한 Word 문서를 Markdown으로 변환할 수 있나요?

네, Aspose.Words for Java는 표, 이미지, 다양한 서식 요소가 포함된 복잡한 Word 문서를 마크다운으로 변환하는 기능을 지원합니다. 문서의 복잡성에 따라 마크다운 출력을 맞춤 설정할 수 있습니다.

### 마크다운 파일에서 이미지를 어떻게 처리할 수 있나요?

Markdown 파일에 이미지를 포함하려면 다음을 사용하여 이미지 폴더 경로를 설정하세요. `setImagesFolder` 방법 `MarkdownSaveOptions`이미지 파일이 지정된 폴더에 저장되어 있는지 확인하세요. 그러면 Aspose.Words for Java가 이미지 참조를 적절히 처리합니다.

### Aspose.Words for Java의 평가판이 있나요?

네, Aspose 웹사이트에서 Aspose.Words for Java 평가판을 받으실 수 있습니다. 평가판을 통해 라이선스를 구매하기 전에 라이브러리의 기능을 평가해 보실 수 있습니다.

### 더 많은 예와 문서는 어디에서 찾을 수 있나요?

Aspose.Words for Java에 대한 더 많은 예제, 문서 및 자세한 정보는 다음을 방문하세요. [선적 서류 비치](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}