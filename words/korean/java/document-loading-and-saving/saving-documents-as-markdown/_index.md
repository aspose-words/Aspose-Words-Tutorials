---
date: 2025-12-22
description: Word 문서를 Markdown으로 변환하여 Aspose.Words for Java로 마크다운을 내보내는 방법을 배워보세요.
  이 단계별 가이드에서는 표 정렬, 이미지 처리 등 다양한 내용을 다룹니다.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용하여 마크다운 내보내는 방법
url: /ko/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용한 Markdown 내보내기 방법

## Aspose.Words for Java에서 Markdown 내보내기 소개

이 단계별 튜토리얼에서는 Aspose.Words for Java를 사용하여 Word 문서에서 **Markdown을 내보내는 방법**을 배웁니다. Markdown은 문서화, 정적 사이트 생성기 및 다양한 출판 플랫폼에 적합한 가벼운 마크업 언어입니다. 이 가이드를 마치면 **Word를 Markdown으로 변환**, 표 정렬 사용자 지정, 그리고 **Markdown에서 이미지 처리**를 손쉽게 할 수 있게 됩니다.

## 빠른 답변
- **Markdown으로 저장하기 위한 기본 클래스는 무엇인가요?** `MarkdownSaveOptions`
- **이미지를 자동으로 포함시킬 수 있나요?** 예 – `setImagesFolder`를 사용해 이미지 폴더를 지정합니다.
- **표 정렬을 어떻게 제어하나요?** `TableContentAlignment`(LEFT, RIGHT, CENTER, AUTO)를 사용합니다.
- **최소 요구 사항은 무엇인가요?** JDK 8 이상 및 Aspose.Words for Java 라이브러리.
- **체험판을 제공하나요?** 예, Aspose 웹사이트에서 다운로드할 수 있습니다.

## “Markdown 내보내기”란 무엇인가요?
Markdown 내보내기는 풍부한 서식의 Word 문서(`.docx`)를 가져와서 제목, 표, 이미지 등을 Markdown 구문으로 보존한 순수 텍스트 `.md` 파일을 생성하는 것을 의미합니다.

## 이미지가 포함된 docx를 변환할 때 Aspose.Words for Java를 사용하는 이유
Aspose.Words는 복잡한 레이아웃, 삽입된 그림 및 표 구조를 손실 없이 처리합니다. 또한 표 정렬 및 이미지 폴더 관리와 같은 Markdown 출력에 대한 세밀한 제어를 제공합니다.

## 전제 조건

- 시스템에 설치된 Java Development Kit(JDK).
- Aspose.Words for Java 라이브러리. [here](https://releases.aspose.com/words/java/)에서 다운로드할 수 있습니다.

## 1단계: 간단한 Word 문서 만들기

먼저, 표가 포함된 작은 문서를 만들겠습니다. 이를 통해 나중에 **표 정렬 사용자 지정**을 시연할 수 있습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

위 코드 스니펫에서는 다음을 수행합니다:

1. 새 `Document` 객체를 생성합니다.
2. `DocumentBuilder`를 사용해 두 개 셀의 표를 삽입합니다.
3. 각 셀 안에 **오른쪽** 및 **가운데** 단락 정렬을 적용합니다.
4. `MarkdownSaveOptions`를 사용해 파일을 Markdown 형식으로 저장합니다.

## 2단계: 표 내용 정렬 사용자 지정

Aspose.Words를 사용하면 최종 Markdown에서 표 셀의 렌더링 방식을 지정할 수 있습니다. 왼쪽, 오른쪽, 가운데 정렬을 강제하거나, 각 열의 첫 번째 단락을 기준으로 라이브러리가 자동으로 결정하도록 할 수 있습니다.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

`TableContentAlignment` 속성을 전환함으로써 Markdown 출력에 대한 **표 정렬 사용자 지정**을 제어합니다.

## 3단계: Markdown으로 내보낼 때 이미지 처리

문서에 그림이 포함된 경우, 생성된 `.md` 파일에 이미지가 올바르게 표시되도록 해야 합니다. Aspose.Words가 추출한 이미지를 저장할 폴더를 지정합니다.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

`"document_with_images.docx"`를 소스 파일 경로로, `"images_folder/"`를 이미지 저장 위치로 교체하십시오. 결과 Markdown에는 이 폴더를 가리키는 이미지 링크가 포함되어 **Markdown에서 이미지 처리**를 원활하게 할 수 있습니다.

## Aspose.Words for Java에서 문서를 Markdown으로 저장하기 위한 전체 소스 코드

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## 일반적인 문제 및 해결책

| 문제 | 해결책 |
|------|--------|
| `.md` 파일에 이미지가 표시되지 않음 | `setImagesFolder`가 쓰기 가능한 디렉터리를 가리키는지, 그리고 생성된 Markdown에서 폴더가 올바르게 참조되는지 확인하십시오. |
| 표 정렬이 어색함 | `TableContentAlignment.AUTO`를 사용해 Aspose.Words가 각 열의 첫 번째 단락을 기준으로 최적의 정렬을 추론하도록 합니다. |
| 출력 파일이 비어 있음 | `save`를 호출하기 전에 `Document` 객체에 실제 내용이 포함되어 있는지 확인하십시오. |

## 자주 묻는 질문

**Q: Aspose.Words for Java를 어떻게 설치하나요?**  
A: Aspose.Words for Java는 Java 프로젝트에 라이브러리를 포함시켜 설치할 수 있습니다. 라이브러리는 [here](https://releases.aspose.com/words/java/)에서 다운로드할 수 있으며, 문서에 제공된 설치 안내를 따라 주세요.

**Q: 복잡한 표와 이미지가 포함된 Word 문서를 Markdown으로 변환할 수 있나요?**  
A: 예, Aspose.Words for Java는 표, 이미지 및 다양한 서식 요소가 포함된 복잡한 Word 문서를 Markdown으로 변환하는 것을 지원합니다. 문서의 복잡도에 맞게 Markdown 출력을 사용자 지정할 수 있습니다.

**Q: Markdown 파일에서 이미지를 어떻게 처리하나요?**  
A: `MarkdownSaveOptions`의 `setImagesFolder` 메서드를 사용해 이미지 폴더 경로를 설정합니다. 이미지 파일이 지정된 폴더에 저장되어 있는지 확인하면, Aspose.Words가 적절한 Markdown 이미지 링크를 생성합니다.

**Q: Aspose.Words for Java 체험판을 제공하나요?**  
A: 예, Aspose 웹사이트에서 Aspose.Words for Java 체험판을 받을 수 있습니다. 체험판을 통해 라이선스를 구매하기 전에 라이브러리 기능을 평가할 수 있습니다.

**Q: 더 많은 예제와 문서는 어디서 찾을 수 있나요?**  
A: Aspose.Words for Java에 대한 더 많은 예제, 문서 및 자세한 정보를 보려면 [documentation](https://reference.aspose.com/words/java/)을 방문하십시오.

---

**마지막 업데이트:** 2025-12-22  
**테스트 환경:** Aspose.Words for Java 24.12 (작성 시 최신)  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}