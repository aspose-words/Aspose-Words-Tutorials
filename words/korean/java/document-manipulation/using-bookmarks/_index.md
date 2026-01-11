---
date: 2026-01-11
description: Aspose.Words for Java를 사용하여 북마크를 표시하고 숨기는 방법 및 Java에서 북마크를 생성하는 방법을 배워
  효율적인 문서 탐색 및 조작을 수행하세요.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java로 책갈피 표시 및 숨기기
url: /ko/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Show Hide Bookmarks with Aspose.Words for Java

## Introduction to Using Bookmarks in Aspose.Words for Java

Bookmarks는 Aspose.Words for Java에서 강력한 기능으로, **create bookmark java**를 통해 북마크를 만들고, 특정 콘텐츠로 이동하며, 필요에 따라 **show hide bookmarks**를 사용해 다양한 문서 버전을 생성할 수 있습니다. 이 단계별 가이드에서는 북마크를 생성, 접근, 업데이트, 복사 및 가시성 전환하는 방법을 살펴보며 문서 조작을 완벽히 제어할 수 있도록 합니다.

## Quick Answers
- **What is the primary purpose of bookmarks?** 문서의 특정 부분을 표시하고 나중에 검색하기 위함입니다.  
- **Can I hide bookmark markers in the final output?** 예—show/hide API를 사용해 가시성을 전환할 수 있습니다.  
- **How do I create a bookmark inside a table cell?** 커서가 셀 안에 있을 때 `DocumentBuilder`로 북마크를 시작하고 종료합니다.  
- **Is it possible to copy bookmarked text to another document?** 물론—`NodeImporter`를 사용해 서식을 유지하면서 복사합니다.  
- **What version of Aspose.Words is required?** 최근 릴리스라면 모두 사용 가능하며, 코드는 최신 2026 빌드에서도 동작합니다.

## What is “show hide bookmarks”?

**show hide bookmarks** 기능은 저장된 문서에서 북마크 구분자를 프로그래밍 방식으로 표시하거나 숨길 수 있게 해줍니다. 최종 사용자를 위한 깔끔한 출력물을 생성하면서도 내부 처리용으로 북마크 데이터를 유지하고 싶을 때 유용합니다.

## Why use bookmarks in Java document automation?

- **Efficient navigation** – 전체 파일을 스캔하지 않고 섹션으로 바로 이동합니다.  
- **Dynamic content generation** – 북마크에 연결된 텍스트를 삽입, 교체 또는 제거합니다.  
- **Conditional visibility** – 사용자 선호도나 출력 형식에 따라 북마크 마커를 표시하거나 숨깁니다.  
- **Reusability** – 스타일을 보존하면서 북마크된 조각을 문서 간에 복사합니다.

## Prerequisites
- Java Development Kit (JDK) 8 이상.  
- 프로젝트에 Aspose.Words for Java 라이브러리 추가 (Maven/Gradle 또는 JAR).  
- `Document`와 `DocumentBuilder` 클래스에 대한 기본 지식.

## Step‑by‑Step Guide

### Step 1: Create a Bookmark (create bookmark java)

북마크를 추가하려면 시작하고, 내용을 작성한 뒤 종료합니다. 다음 예제는 **My Bookmark**라는 간단한 북마크를 생성합니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Step 2: Access Bookmarks (access bookmarks java)

북마크는 0부터 시작하는 인덱스 또는 이름으로 조회할 수 있습니다. 아래 코드는 두 가지 접근 방식을 모두 보여줍니다.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Step 3: Update Bookmark Data (update bookmark text)

북마크 이름을 바꾸거나 텍스트 내용을 교체할 수 있습니다. 문서가 변경될 때 유용합니다.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Step 4: Work with Bookmarked Text (copy bookmarked text)

`NodeImporter`를 사용하면 원본 서식을 유지하면서 북마크된 조각을 다른 문서로 복사할 수 있습니다.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Step 5: Show and Hide Bookmarks (show hide bookmarks)

다음 스니펫은 저장 파일에서 북마크 마커를 숨기는 방법을 보여줍니다. `false`를 전달하면 숨기고, `true`를 전달하면 표시합니다.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Step 6: Untangle Row Bookmarks (bookmark table cell)

북마크가 테이블 행을 가로지를 경우 얽힐 수 있습니다. 아래 유틸리티 메서드는 이를 풀어주고, 특정 행을 해당 북마크로 삭제할 수 있게 합니다.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Common Issues and Solutions

| 문제 | 해결책 |
|-------|----------|
| **Bookmark not found** | 북마크 이름이 정확히 일치하는지(대소문자 구분) 확인하고, 생성 후 문서가 저장되었는지 확인하세요. |
| **Copied text loses formatting** | Step 4에서 보여준 대로 `NodeImporter`에 `ImportFormatMode.KEEP_SOURCE_FORMATTING`을 사용하세요. |
| **Show/hide does not affect output** | 문서를 저장하기 **전에** `showHideBookmarkedContent`를 호출했는지 확인하세요. |
| **Bookmark inside a table cell is ignored** | Builder 커서를 대상 셀 안으로 이동한 후 시작/종료 호출을 수행하세요. |

## Frequently Asked Questions

**Q: How do I create a bookmark in a table cell?**  
A: `DocumentBuilder`를 사용해 커서를 원하는 셀로 이동한 뒤, 셀 내용 앞뒤에 `startBookmark`와 `endBookmark`를 호출합니다.

**Q: Can I copy a bookmark to another document?**  
A: 예—Step 4에서 설명한 대로 `NodeImporter` 클래스를 사용해 원본 서식을 보존하면서 북마크된 노드를 가져옵니다.

**Q: How can I delete a row by its bookmark?**  
A: 먼저 북마크가 포함된 행을 찾은 뒤, 해당 행 노드에 `remove`를 호출합니다(Step 6 참고).

**Q: What are some common use cases for bookmarks?**  
A: 목차 생성, 보고서를 위한 특정 섹션 추출, 사용자 선택에 기반한 문서 조립 자동화 등.

**Q: Where can I find more information about Aspose.Words for Java?**  
A: 자세한 문서와 다운로드는 [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)를 방문하세요.

---

**Last Updated:** 2026-01-11  
**Tested With:** Aspose.Words for Java 24.11 (2026)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}