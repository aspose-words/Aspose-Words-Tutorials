---
"description": "Aspose.Words for Java에서 문서를 복제하고 결합하는 방법을 알아보세요. 소스 코드 예제를 포함한 단계별 가이드입니다."
"linktitle": "문서 복제 및 결합"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Java용 Aspose.Words에서 문서 복제 및 결합"
"url": "/ko/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 문서 복제 및 결합


## Aspose.Words for Java에서 문서 복제 및 결합 소개

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 문서를 복제하고 결합하는 방법을 살펴봅니다. 문서 복제, 바꾸기 지점에 문서 삽입, 책갈피 추가, 편지 병합 작업 등 다양한 시나리오를 다룹니다.

## 1단계: 문서 복제

Java용 Aspose.Words에서 문서를 복제하려면 다음을 사용할 수 있습니다. `deepClone()` 방법입니다. 간단한 예를 들어 보겠습니다.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

이 코드는 원본 문서의 심층 복제본을 만들어 새 파일로 저장합니다.

## 2단계: 바꾸기 지점에 문서 삽입

다른 문서의 특정 바꾸기 지점에 문서를 삽입할 수 있습니다. 방법은 다음과 같습니다.

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

이 예에서 우리는 다음을 사용합니다. `FindReplaceOptions` 교체에 대한 콜백 핸들러를 지정하는 개체입니다. `InsertDocumentAtReplaceHandler` 클래스는 삽입 논리를 처리합니다.

## 3단계: 북마크에 문서 삽입

다른 문서의 특정 책갈피에 문서를 삽입하려면 다음 코드를 사용할 수 있습니다.

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

여기서 우리는 이름으로 북마크를 찾고 사용합니다. `insertDocument` 내용을 삽입하는 방법 `subDoc` 북마크 위치에 있는 문서.

## 4단계: 메일 병합 중 문서 삽입

Aspose.Words for Java에서 메일 병합 작업 중에 문서를 삽입할 수 있습니다. 방법은 다음과 같습니다.

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

이 예에서 우리는 다음을 사용하여 필드 병합 콜백을 설정합니다. `InsertDocumentAtMailMergeHandler` "Document_1" 필드에서 지정한 문서의 삽입을 처리하는 클래스입니다.

## 결론

Aspose.Words for Java에서는 다양한 기술을 사용하여 문서를 복제하고 결합할 수 있습니다. 문서 복제, 바꾸기 지점, 책갈피 또는 메일 병합 시 콘텐츠 삽입 등 어떤 작업을 수행하든 Aspose.Words는 문서를 원활하게 조작할 수 있는 강력한 기능을 제공합니다.

## 자주 묻는 질문

### Java용 Aspose.Words에서 문서를 복제하려면 어떻게 해야 하나요?

Java용 Aspose.Words에서 문서를 복제하려면 다음을 사용하십시오. `deepClone()` 방법입니다. 예를 들면 다음과 같습니다.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### 북마크에 문서를 삽입하려면 어떻게 해야 하나요?

Aspose.Words for Java에서 북마크에 문서를 삽입하려면 이름으로 북마크를 찾은 다음 다음을 사용할 수 있습니다. `insertDocument` 콘텐츠를 삽입하는 방법입니다. 예를 들면 다음과 같습니다.

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Java용 Aspose.Words에서 메일 병합 중에 문서를 삽입하려면 어떻게 해야 하나요?

Aspose.Words for Java에서 메일 병합 중에 필드 병합 콜백을 설정하고 삽입할 문서를 지정하여 문서를 삽입할 수 있습니다. 다음은 그 예입니다.

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

이 예에서는 `InsertDocumentAtMailMergeHandler` 클래스는 메일 병합 중에 "DocumentField"에 대한 삽입 논리를 처리합니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}