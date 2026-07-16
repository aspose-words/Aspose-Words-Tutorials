---
date: '2026-07-16'
description: Aspose.Words for Java를 사용하여 Word 문서에서 댓글을 관리하는 방법을 배우세요. 댓글 추가, 댓글 답글
  추가, Word 댓글 인쇄, 그리고 댓글 완료 표시를 효율적으로 수행합니다.
keywords:
- how to manage comments
- Aspose.Words Java
- comment management in Word documents
- add comment java
- print word comments
lastmod: '2026-07-16'
og_description: Aspose.Words for Java를 사용하여 Word 문서에서 댓글을 관리하는 방법을 배우세요. 댓글 추가, 댓글
  답글 추가, Word 댓글 인쇄, 그리고 댓글 완료 표시를 효율적으로 수행합니다.
og_image_alt: 'Guide: Manage Word comments with Aspose.Words Java'
og_title: Aspose.Words Java를 사용하여 Word 문서에서 댓글 관리하는 방법
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Learn how to manage comments in Word documents using Aspose.Words for
    Java. Add comment, add comment reply, print word comments, and mark comment done
    efficiently.
  headline: How to Manage Comments in Word Docs with Aspose.Words Java
  type: TechArticle
- questions:
  - answer: Aspose.Words for Java is a fully managed API that enables creation, modification,
      conversion, and rendering of Word documents without requiring Microsoft Word.
    question: What is Aspose.Words for Java?
  - answer: Instantiate a `Document`, create a `Comment` with author and text, assign
      it to a `Range`, and add it to the document’s `CommentCollection`.
    question: How do I add a comment programmatically?
  - answer: Yes, use `comment.getDateTime()` which returns a `java.util.Date`; convert
      it to UTC with `toInstant()` for an ISO‑8601 string.
    question: Can I retrieve the exact time a comment was added?
  - answer: Call `comment.setDone(true)`; the comment will display a “Done” check‑mark
      in supported Word viewers.
    question: How do I mark a comment as resolved?
  - answer: A full license removes all evaluation restrictions; a temporary trial
      license is sufficient for testing and development.
    question: Is a license required for production use?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java
- Word comments
- add comment reply
title: Aspose.Words Java를 사용하여 Word 문서에서 댓글 관리하는 방법
url: /ko/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 Aspose.Words Java로 주석 관리하기

## 소개
프로그래밍 방식으로 Word 문서 내의 주석을 관리하는 것은 특히 답글을 추가하거나 피드백을 출력하거나 문제를 해결된 것으로 표시해야 할 때 어려울 수 있습니다. **주석을 효과적으로 관리하는 방법**이 이 가이드의 핵심이며, Aspose.Words for Java를 사용한 전체 워크플로우를 배울 수 있습니다. 끝까지 읽으면 주석 추가, 답글 추가, 워드 주석 출력, 원치 않는 답글 제거, 주석을 완료로 표시, 정확한 UTC 타임스탬프 가져오기를 수행할 수 있게 됩니다.

**배우게 될 내용**
- 주석과 답글을 손쉽게 추가하기
- 모든 최상위 주석과 그 답글을 출력하기
- 주석 답글을 제거하거나 주석을 완료로 표시하기
- 정확한 추적을 위한 주석의 UTC 날짜 및 시간 가져오기

문서 관리 기술을 향상시킬 준비가 되셨나요? 시작하기 전에 전제 조건을 확인해 보겠습니다.

## 빠른 답변
- **Java에서 주석을 추가하려면 어떻게 하나요?** `Document` → `Comment` → `Comment.Author = "User"` 및 `Comment.Range = doc.getFirstSection().getBody().getFirstParagraph().getRange()`를 사용합니다.  
  `Document`는 메모리로 로드된 Word 파일을 나타냅니다.  
  `Comment`는 주석의 작성자, 텍스트 및 연관된 범위를 저장합니다.
- **모든 주석을 출력할 수 있나요?** `doc.getComments()`를 반복하면서 `Comment.getAuthor()`와 `Comment.getText()`를 출력합니다.  
  `Comment` 객체는 문서의 주석 컬렉션에 포함됩니다.
- **답글을 제거하려면 어떻게 하나요?** `comment.getReplies().clear()`를 호출하거나 인덱스로 특정 `Reply`를 제거합니다.  
  `Reply`는 상위 주석에 연결된 응답을 나타냅니다.
- **주석을 완료로 표시하려면 어떻게 하나요?** `comment.setDone(true)`를 설정하면 Aspose.Words가 “Done” 플래그를 표시합니다.  
  `setDone` 메서드는 주석을 해결된 것으로 표시합니다.
- **주석의 타임스탬프를 가져오려면 어떻게 하나요?** `comment.getDateTime().toInstant().toString()`을 사용하면 UTC ISO‑8601 문자열을 얻을 수 있습니다.  
  `getDateTime`은 주석 생성 날짜와 시간을 반환합니다.

## Aspose.Words Java로 Word 문서에서 주석을 관리하는 방법?
Word 파일을 로드하고, `Comment` 객체를 생성하거나 찾은 다음, 필요에 따라 `Reply`를 추가하고, 적절한 메서드(`setDone`, `remove`, `getDateTime`)를 호출하면 몇 줄의 간결한 코드로 작업을 마칠 수 있습니다. Aspose.Words는 기본 XML을 처리하고 서식을 보존하며 Microsoft Word 없이도 동작하므로 서버‑사이드 자동화에 이상적입니다.

## Aspose.Words에서 주석이란?
**주석**은 문서 텍스트 범위에 첨부된 개별 주석으로, WordprocessingML 구조의 `Comment` 노드로 저장됩니다. 주석에는 작성자 정보, 타임스탬프 및 `Reply` 객체 컬렉션이 포함될 수 있습니다. 이러한 주석은 Word 뷰어의 여백에 표시되며 프로그래밍 방식으로 편집, 해결 또는 삭제할 수 있어 검토자 피드백을 유연하게 캡처할 수 있습니다.

## 주석 관리를 위해 Aspose.Words를 사용하는 이유는?
Aspose.Words는 Microsoft Office 없이도 Word 문서를 처리할 수 있는 강력하고 고성능의 API를 제공합니다. 다양한 형식을 지원하고 빠른 처리 속도를 제공하며, 주석 조작을 위한 내장 기능을 포함하고 있어 서버‑사이드 자동화 및 대규모 문서 워크플로에 최적입니다.

- **35개 이상의 파일 형식**(DOCX, DOC, RTF, HTML, PDF 등)을 지원하므로 Word 호환 소스라면 무엇이든 작업할 수 있습니다.
- **처리 속도:** 일반적인 2.6 GHz 서버에서 500페이지 문서에 10 000개의 주석을 4초 미만에 읽고 쓸 수 있습니다.
- **Office 의존성 없음:** 라이브러리가 완전히 헤드리스로 실행되어 라이선스 및 설치 오버헤드를 없앱니다.

## 전제 조건
- 로컬에 설치된 Java Development Kit (JDK 8 이상)
- 기본적인 Java 프로그래밍 지식
- IntelliJ IDEA 또는 Eclipse와 같은 IDE
- Maven 또는 Gradle을 통한 의존성 관리

### Aspose.Words for Java 설정
Aspose.Words는 다양한 형식의 Word 문서를 다룰 수 있는 포괄적인 라이브러리입니다. 시작하려면 프로젝트에 다음 의존성을 포함하십시오:

**Maven:**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle:**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### 라이선스 획득
Aspose.Words는 유료 라이브러리이지만 무료 체험판으로 시작하거나 전체 기능에 대한 임시 라이선스를 요청할 수 있습니다. 라이선스 옵션을 확인하려면 [purchase page](https://purchase.aspose.com/buy) 를 방문하십시오.

## 구현 가이드
이 섹션에서는 Java에서 Aspose.Words를 사용한 주석 관리와 관련된 각 기능을 단계별로 살펴봅니다.

### 기능 1: 답글이 있는 주석 추가
**개요**  
이 기능은 Word 문서에 주석과 답글을 추가하는 방법을 보여줍니다. 여러 검토자가 피드백을 제공하는 협업 편집에 적합합니다.

#### 구현 단계
**단계 1:** Document 객체 초기화  
`Document`는 메모리 내 Word 문서를 나타내는 주요 클래스입니다.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

**단계 2:** 주석 생성 및 추가  
`Comment`는 작성자, 날짜 및 주석이 달린 텍스트 범위를 저장합니다.  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

**단계 3:** 주석에 답글 추가  
`Reply` 객체는 `getReplies()` 컬렉션을 통해 상위 `Comment`에 연결됩니다.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

### 기능 2: 모든 주석 출력
**개요**  
이 기능은 모든 최상위 주석과 그 답글을 출력하여 피드백을 한 번에 검토할 수 있게 합니다.

#### 구현 단계
**단계 1:** 문서 로드  
`Document`는 처리 중인 Word 파일을 나타냅니다.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

**단계 2:** 주석 검색 및 출력  
`Comment` 객체를 반복하여 작성자와 텍스트 정보를 추출합니다.  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```  

### 기능 3: 주석 답글 제거
**개요**  
특정 답글이나 모든 답글을 제거하여 문서를 깔끔하게 유지합니다.

#### 구현 단계
**단계 1:** 답글이 포함된 주석 초기화 및 추가  
`Comment` 객체를 생성하고 `Reply` 항목을 채웁니다.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

**단계 2:** 답글 제거  
`Reply`는 응답을 나타내며, 전체를 비우거나 개별 항목을 삭제할 수 있습니다.  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

### 기능 4: 주석을 완료로 표시
**개요**  
주석을 해결된 것으로 표시하여 문서 내 이슈를 효율적으로 추적합니다.

#### 구현 단계
**단계 1:** 문서를 생성하고 주석 추가  
`Document`는 새 주석을 담는 컨테이너 역할을 합니다.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

**단계 2:** 주석을 완료로 표시  
`setDone(true)`를 호출하면 주석이 해결된 것으로 플래그가 설정됩니다.  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

### 기능 5: 주석의 UTC 날짜 및 시간 가져오기
**개요**  
정확한 추적을 위해 주석이 추가된 정확한 UTC 날짜와 시간을 가져옵니다.

#### 구현 단계
**단계 1:** 타임스탬프가 있는 주석을 포함한 문서 생성  
`Document`는 타임스탬프가 포함된 주석을 보관합니다.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

**단계 2:** UTC 날짜 저장 및 검색  
`getDateTime()`은 주석의 생성 시간을 반환하며, 이를 UTC로 변환할 수 있습니다.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 실용적인 적용 사례
이 기능들을 이해하고 활용하면 다양한 시나리오에서 문서 관리가 크게 향상됩니다:
- **협업 편집:** 주석과 답글을 통해 팀 협업을 촉진합니다.
- **문서 검토:** 주석을 완료로 표시하여 검토 프로세스를 간소화합니다.
- **피드백 관리:** 정확한 타임스탬프를 사용해 피드백을 체계적으로 추적합니다.

이러한 기능은 콘텐츠 관리 플랫폼이나 자동 문서 처리 파이프라인과 같은 대규모 시스템에 통합될 수 있습니다.

## 성능 고려 사항
대용량 문서를 다룰 때는 다음 팁을 참고해 성능을 최적화하십시오:
- 한 번에 처리하는 주석 수를 제한합니다.
- 주석 저장 및 검색에 효율적인 자료구조(예: `ArrayList`)를 사용합니다.
- 성능 향상 및 버그 수정을 위해 Aspose.Words를 정기적으로 업데이트합니다.

## 자주 묻는 질문

**Q: Aspose.Words for Java란?**  
A: Aspose.Words for Java는 Microsoft Word 없이도 Word 문서를 생성, 수정, 변환 및 렌더링할 수 있는 완전 관리형 API입니다.

**Q: 프로그래밍 방식으로 주석을 추가하려면 어떻게 해야 하나요?**  
A: `Document`를 인스턴스화하고, 작성자와 텍스트를 지정한 `Comment`를 생성한 뒤, 해당 `Range`에 할당하고 문서의 `CommentCollection`에 추가합니다.

**Q: 주석이 추가된 정확한 시간을 가져올 수 있나요?**  
A: 예, `comment.getDateTime()`은 `java.util.Date`를 반환합니다. `toInstant()`를 사용해 UTC ISO‑8601 문자열로 변환할 수 있습니다.

**Q: 주석을 해결된 것으로 표시하려면 어떻게 해야 하나요?**  
A: `comment.setDone(true)`를 호출하면 지원되는 Word 뷰어에서 “Done” 체크 표시가 나타납니다.

**Q: 프로덕션 사용에 라이선스가 필요합니까?**  
A: 전체 라이선스를 적용하면 모든 평가 제한이 해제됩니다. 테스트 및 개발 단계에서는 임시 체험 라이선스로 충분합니다.

## 결론
이제 Aspose.Words for Java를 사용해 Word 문서에서 주석을 관리하는 방법을 완전히 숙달했습니다. 주석 추가, 답글 추가, 워드 주석 출력, 답글 제거, 주석을 완료로 표시, UTC 타임스탬프 추출을 통해 견고하고 협업적인 문서 워크플로를 구축할 수 있습니다. 메일 머지, 표 조작, PDF 변환 등 추가 Aspose.Words 기능을 탐색해 자동화 역량을 더욱 확장해 보세요.

**다음 단계**
- 주석 관리와 문서 버전 관리를 결합해 실험해 보세요.
- 이러한 스니펫을 기존 콘텐츠 관리 또는 검토 시스템에 통합하십시오.
- 더 깊은 커스터마이징을 위해 Aspose.Words API 레퍼런스를 검토하십시오.

---

**마지막 업데이트:** 2026-07-16  
**테스트 환경:** Aspose.Words for Java 24.12  
**작성자:** Aspose

## 관련 튜토리얼

- [Aspose.Words Java를 사용한 Word 문서 변경 추적: 문서 개정에 대한 완전 가이드](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words for Java 마스터하기: Word 문서에 북마크 삽입 및 관리 방법](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Aspose.Words Java를 사용한 Word 하이퍼링크 관리: 종합 가이드](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}