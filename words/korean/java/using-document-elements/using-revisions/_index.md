---
title: Java용 Aspose.Words에서 Revisions 사용
linktitle: 개정판 사용
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java의 개정을 효율적으로 사용하는 방법을 배우세요. 개발자를 위한 단계별 가이드. 문서 관리를 최적화하세요.
weight: 22
url: /ko/java/using-document-elements/using-revisions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 Revisions 사용


문서 작업을 하고 리비전 컨트롤을 구현해야 하는 Java 개발자라면 Aspose.Words for Java가 리비전을 효과적으로 관리하는 데 도움이 되는 강력한 도구 세트를 제공합니다. 이 튜토리얼에서는 Aspose.Words for Java에서 리비전을 단계별로 사용하는 방법을 안내해 드립니다. 

## 1. Java용 Aspose.Words 소개

Aspose.Words for Java는 Microsoft Word가 필요 없이 Word 문서를 만들고, 수정하고, 조작할 수 있는 강력한 Java API입니다. 문서 내에서 수정을 구현해야 할 때 특히 유용합니다.

## 2. 개발 환경 설정

Aspose.Words for Java를 사용하기 전에 개발 환경을 설정해야 합니다. 필요한 Java 개발 도구와 Aspose.Words for Java 라이브러리가 설치되어 있는지 확인하세요.

## 3. 새 문서 만들기

Aspose.Words for Java를 사용하여 새 Word 문서를 만드는 것으로 시작해 보겠습니다. 방법은 다음과 같습니다.

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. 문서에 내용 추가

이제 빈 문서가 생겼으니, 여기에 콘텐츠를 추가할 수 있습니다. 이 예에서는 세 개의 문단을 추가합니다.

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. 개정 추적 시작

문서의 수정 사항을 추적하려면 다음 코드를 사용할 수 있습니다.

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. 수정하기

다른 문단을 추가하여 수정해 보겠습니다.

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. 수정 사항 수락 및 거부

Aspose.Words for Java를 사용하여 문서의 개정을 수락하거나 거부할 수 있습니다. 문서가 생성된 후 Microsoft Word에서 개정을 쉽게 관리할 수 있습니다.

## 8. 개정 추적 중지

수정 사항 추적을 중지하려면 다음 코드를 사용하세요.

```java
doc.stopTrackRevisions();
```

## 9. 문서 저장

마지막으로 문서를 저장합니다.

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. 결론

이 튜토리얼에서는 Aspose.Words for Java에서 revision을 사용하는 기본 사항을 다루었습니다. 문서를 만들고, 콘텐츠를 추가하고, revision 추적을 시작하고 중지하고, 문서를 저장하는 방법을 배웠습니다.

이제 Aspose.Words for Java를 사용하여 Java 애플리케이션의 개정 내용을 효과적으로 관리하는 데 필요한 도구를 갖추게 되었습니다.

## 완전한 소스 코드
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
// 첫 번째 문단에 텍스트를 추가한 다음 두 개의 문단을 더 추가합니다.
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// 우리는 3개의 문단을 가지고 있는데, 그 중 어느 것도 어떤 유형의 개정으로 등록되지 않았습니다.
// 개정 내용을 추적하는 동안 문서에 내용을 추가하거나 제거하는 경우
// 이는 문서에 그대로 표시되며 승인/거부될 수 있습니다.
doc.startTrackRevisions("John Doe", new Date());
// 이 문단은 개정판이므로 "IsInsertRevision" 플래그가 설정됩니다.
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
// 문서의 문단 컬렉션을 가져와서 문단을 제거합니다.
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
// 개정 사항을 추적하고 있으므로 해당 문단이 문서에 여전히 존재하며 "IsDeleteRevision"이 설정됩니다.
// 모든 수정 사항을 승인하거나 거부할 때까지 Microsoft Word에서 수정 사항으로 표시됩니다.
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
// 변경 사항이 승인되면 수정 내용 삭제 문단이 제거됩니다.
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //Is.Empty 였습니다
// 수정 내용 추적을 중지하면 이 텍스트가 일반 텍스트로 표시됩니다.
//문서가 변경된 경우, 수정 사항은 계산되지 않습니다.
doc.stopTrackRevisions();
// 문서를 저장합니다.
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## 자주 묻는 질문

### 1. Aspose.Words for Java를 다른 프로그래밍 언어와 함께 사용할 수 있나요?

아니요. Aspose.Words for Java는 특별히 Java 개발을 위해 설계되었습니다.

### 2. Aspose.Words for Java는 모든 버전의 Microsoft Word와 호환됩니까?

네, Aspose.Words for Java는 다양한 버전의 Microsoft Word와 호환되도록 설계되었습니다.

### 3. 기존 Word 문서의 수정 사항을 추적할 수 있나요?

네, Aspose.Words for Java를 사용하여 기존 Word 문서의 수정 사항을 추적할 수 있습니다.

### 4. Aspose.Words for Java를 사용하는 데 라이선스 요구 사항이 있습니까?

 네, 프로젝트에서 Aspose.Words for Java를 사용하려면 라이선스를 취득해야 합니다.[여기에서 라이센스에 액세스하세요](https://purchase.aspose.com/buy).

### 5. Java용 Aspose.Words에 대한 지원은 어디에서 찾을 수 있나요?

 질문이나 문제가 있는 경우 다음을 방문하세요.[Aspose.Words for Java 지원 포럼](https://forum.aspose.com/).

지금 바로 Aspose.Words for Java를 시작하여 문서 관리 프로세스를 간소화하세요.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
