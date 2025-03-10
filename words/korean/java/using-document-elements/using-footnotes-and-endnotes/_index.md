---
title: Aspose.Words for Java에서 각주와 미주 사용
linktitle: 각주와 미주 사용
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java에서 각주와 미주를 효과적으로 사용하는 방법을 배우세요. 오늘 문서 서식 기술을 향상시키세요!
weight: 13
url: /ko/java/using-document-elements/using-footnotes-and-endnotes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 각주와 미주 사용


이 튜토리얼에서는 Aspose.Words for Java에서 각주와 미주를 사용하는 과정을 안내해 드리겠습니다. 각주와 미주는 문서 서식에서 필수적인 요소로, 종종 인용, 참조 및 추가 정보에 사용됩니다. Aspose.Words for Java는 각주와 미주를 원활하게 작업할 수 있는 강력한 기능을 제공합니다.

## 1. 각주와 미주 소개

각주와 미주는 문서 내에서 보충 정보나 인용문을 제공하는 주석입니다. 각주는 페이지 하단에 표시되는 반면 미주는 섹션이나 문서의 끝에 수집됩니다. 이들은 일반적으로 학술 논문, 보고서 및 법률 문서에서 출처를 참조하거나 내용을 명확히 하는 데 사용됩니다.

## 2. 환경 설정

각주와 미주 작업에 들어가기 전에 개발 환경을 설정해야 합니다. 프로젝트에 Aspose.Words for Java API가 설치되고 구성되어 있는지 확인하세요.

## 3. 문서에 각주 추가

문서에 각주를 추가하려면 다음 단계를 따르세요.
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // 각주 영역의 서식이 적용되는 열 수를 지정합니다.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. 각주 옵션 수정

각주 옵션을 수정하여 모양과 동작을 사용자 지정할 수 있습니다. 방법은 다음과 같습니다.
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. 문서에 각주 추가하기

문서에 각주를 추가하는 것은 간단합니다. 다음은 예입니다.
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. Endnote 설정 사용자 정의

문서 요구 사항에 맞게 각주 설정을 추가로 사용자 정의할 수 있습니다.

## 완전한 소스 코드
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // 각주 영역의 서식이 적용되는 열 수를 지정합니다.
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. 결론

이 튜토리얼에서는 Aspose.Words for Java에서 각주와 미주를 사용하는 방법을 살펴보았습니다. 이러한 기능은 적절한 인용과 참조가 있는 잘 구성된 문서를 만드는 데 매우 중요합니다.

이제 각주와 미주를 사용하는 방법을 배웠으니, 문서 형식을 개선하고 콘텐츠를 보다 전문적으로 만들 수 있습니다.

### 자주 묻는 질문

### 1. 각주와 미주의 차이점은 무엇인가요?
각주는 페이지 하단에 표시되고, 미주는 섹션이나 문서의 끝에 표시됩니다.

### 2. 각주나 미주의 위치를 어떻게 바꿀 수 있나요?
 당신은 사용할 수 있습니다`setPosition` 각주나 미주의 위치를 변경하는 방법입니다.

### 3. 각주와 미주의 서식을 사용자 정의할 수 있나요?
네, Aspose.Words for Java를 사용하여 각주와 미주의 서식을 사용자 정의할 수 있습니다.

### 4. 각주와 미주는 문서 서식에서 중요한가요?
네, 각주와 미주는 문서에서 참고문헌과 추가 정보를 제공하는 데 필수적입니다.

Aspose.Words for Java의 더 많은 기능을 자유롭게 탐색하고 문서 생성 기능을 향상시키세요. 즐거운 코딩 되세요!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
