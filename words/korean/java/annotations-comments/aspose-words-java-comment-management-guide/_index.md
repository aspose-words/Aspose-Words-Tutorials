---
date: '2026-05-18'
description: Aspose.Words for Java로 Word 문서의 댓글을 관리하는 방법을 배워보세요. Add comment java,
  print word comments, delete word comment, 그리고 add comment reply를 효율적으로 수행합니다.
keywords:
- how to manage comments
- add comment java
- print word comments
- java document comments
- delete word comment
- add comment reply
schemas:
- author: Aspose
  dateModified: '2026-05-18'
  description: Learn how to manage comments in Word documents with Aspose.Words for
    Java. Add comment java, print word comments, delete word comment, and add comment
    reply efficiently.
  headline: How to Manage Comments in Word Documents Using Aspose.Words for Java
  type: TechArticle
- questions:
  - answer: Yes, with a valid license; a free trial is available for evaluation.
    question: Can I use Aspose.Words for Java in a commercial application?
  - answer: Yes, provide the password when loading the document via `LoadOptions`.
    question: Does the library work with password‑protected Word files?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, covering both legacy
      and modern environments.
    question: Which Java versions are supported?
  - answer: Use `LoadOptions.setLoadFormat(LoadFormat.DOCX)` and enable `LoadOptions.setMemoryOptimization(true)`
      to reduce memory footprint.
    question: How do I handle documents larger than 200 MB?
  - answer: Iterate `doc.getComments()` and write each comment’s properties to a CSV
      using standard Java I/O.
    question: Is there a way to export comments to a CSV file?
  type: FAQPage
title: Aspose.Words for Java를 사용하여 Word 문서에서 댓글 관리하는 방법
url: /ko/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용하여 Word 문서에서 댓글 관리하기

프로그래밍 방식으로 댓글을 관리하는 것은 미로를 탐색하는 것처럼 느껴질 수 있습니다. 특히 답글을 추가하고, 원치 않는 메모를 삭제하며, 각 댓글이 언제 작성되었는지 추적해야 할 때 더욱 그렇습니다. 이 튜토리얼에서는 Aspose.Words for Java를 사용하여 **댓글을 효율적으로 관리하는 방법**을 알아보고, 댓글 추가부터 UTC 타임스탬프 가져오기까지 모든 과정을 다룹니다.

## 빠른 답변
- **Java에서 댓글을 추가하려면 어떻게 해야 하나요?** `Document` → `Comment` 객체를 사용하고 `CommentRangeStart`에서 `appendChild`를 호출합니다.
- **Word 파일의 모든 댓글을 출력할 수 있나요?** `doc.getComments()`를 반복하면서 각 댓글의 텍스트와 작성자를 출력합니다.
- **댓글을 삭제하는 방법이 있나요?** 문서의 댓글 컬렉션에서 해당 댓글 노드를 제거합니다.
- **댓글에 답글을 추가하려면 어떻게 하나요?** `Comment` 객체를 생성하고 `ParentComment` 속성을 설정한 뒤 문서에 추가합니다.
- **댓글의 타임스탬프를 가져오려면 어떻게 해야 하나요?** UTC `java.time` 값을 반환하는 `Comment.getDateTime()`에 접근합니다.

## Word 문서에서 댓글 관리란 무엇인가요?
댓글 관리는 Word 파일 내에서 댓글 객체를 프로그래밍 방식으로 생성, 검색, 수정 및 삭제하는 것을 의미합니다. 이를 통해 수동 편집 없이 자동화된 검토 워크플로우를 구현할 수 있으며, 개발자는 댓글을 추가, 답글 달기, 해결 및 추출할 수 있어 팀 간 협업 및 감사 프로세스를 효율화합니다.

## 댓글 관리를 위해 Aspose.Words for Java를 사용하는 이유
Aspose.Words는 **35개 이상의 입력 및 출력 형식**을 지원하며, 표준 서버 하드웨어에서 **500페이지 문서를 3초 이하**로 처리할 수 있습니다. Microsoft Word가 필요 없으며, 풍부한 API를 통해 댓글 객체, 타임스탬프 및 답글 계층 구조를 세밀하게 제어할 수 있습니다.

## 전제 조건
- Java Development Kit (JDK) 8 이상이 설치되어 있어야 합니다.
- Java 문법 및 객체 지향 개념에 대한 기본적인 이해가 필요합니다.
- IntelliJ IDEA 또는 Eclipse와 같은 IDE를 사용하면 프로젝트 관리가 용이합니다.
- 유효한 Aspose.Words for Java 라이선스(체험판 또는 정식 구매)가 필요합니다.

### Aspose.Words for Java 설정
Aspose.Words는 Maven 또는 Gradle 아티팩트 형태로 제공됩니다. 사용 중인 빌드 시스템에 맞는 종속성을 추가하세요.

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
Aspose.Words는 상용 라이브러리이지만, 무료 체험판으로 시작하거나 전체 기능 접근을 위한 임시 라이선스를 요청할 수 있습니다. 라이선스 옵션을 확인하려면 [purchase page](https://purchase.aspose.com/buy) 를 방문하세요.

## Java 스타일로 댓글 추가하기
`Document`는 메모리로 로드된 Word 파일을 나타내는 주요 Aspose.Words 객체입니다. `Comment`는 작성자, 텍스트 및 타임스탬프 정보를 저장할 수 있는 개별 댓글 노드를 나타냅니다. 최상위 댓글을 추가하려면 `Document`를 로드하거나 생성하고, 원하는 작성자와 텍스트를 사용해 `Comment`를 인스턴스화한 뒤 대상 위치의 `CommentRangeStart`에 연결합니다. 이 방법으로 몇 줄의 코드만으로 댓글을 삽입할 수 있습니다.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

## Java에서 댓글 답글 추가하기
`Comment` 객체는 `ParentComment` 속성을 사용해 답글 체인을 형성할 수 있습니다. 이 속성을 기존 댓글에 설정하면 새 댓글이 해당 부모의 자식(답글)으로 연결됩니다. 자식 `Comment`를 생성하고 `ParentComment`를 원본 댓글에 할당한 뒤 문서에 삽입하면 답글이 부모 바로 아래에 중첩되어 토론 계층 구조가 유지됩니다.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## Word 댓글 출력하기
`Document.getComments()`는 Word 파일에 존재하는 모든 `Comment` 노드의 컬렉션을 반환합니다. 이 컬렉션을 반복하면 각 댓글의 작성자, 텍스트 및 타임스탬프에 접근할 수 있습니다. 문서를 로드하고 `getComments()`를 호출한 뒤, 각 `Comment`의 세부 정보를 콘솔이나 로그에 출력하면 파일에 포함된 모든 피드백을 한눈에 확인할 수 있습니다.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

## Word 댓글 삭제하기
`Comment.remove()`는 댓글 노드를 문서 트리에서 분리하여 실질적으로 삭제합니다. 먼저 `Document.getComments()` 컬렉션에서 원하는 댓글을 찾은 다음, 해당 댓글의 `remove()` 메서드를 호출합니다. 전체 계층을 정리하려면 자식 답글도 함께 제거할 수 있어 댓글이 파일에서 완전히 사라집니다.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

## 댓글을 완료로 표시하기
`Comment.setDone(boolean)`은 댓글을 해결된 상태로 표시하여 Word UI에서 시각적인 “Done” 플래그를 토글합니다. 댓글을 생성하거나 찾은 뒤 `setDone(true)`를 호출하면 해당 이슈가 처리되었음을 나타냅니다. 필요에 따라 `setDone(false)`로 플래그를 해제할 수도 있습니다.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

## 댓글의 UTC 날짜 및 시간 가져오기
`Comment.getDateTime()`은 댓글 생성 시점을 UTC 기준 `java.time.OffsetDateTime` 형태로 반환합니다. 문서를 로드한 후 이 속성에 접근하면 각 댓글에 대한 정확한 시간 정보를 얻을 수 있어 감사 로그 및 버전 관리에 유용합니다. 필요에 따라 다른 시간대로 변환할 수도 있습니다.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 실용적인 적용 사례
이 댓글 관리 기능을 이해하고 활용하면 다양한 실제 워크플로우를 혁신할 수 있습니다:

- **협업 편집:** 팀이 문서를 떠나지 않고도 댓글을 추가, 답글 달기 및 해결할 수 있습니다.
- **문서 검토 파이프라인:** 자동화 스크립트가 모든 피드백을 추출하고 요약 보고서를 생성하며 항목을 완료로 표시합니다.
- **감사 및 규정 준수:** UTC 타임스탬프는 각 댓글이 언제 작성되었는지에 대한 변조 불가능한 기록을 제공하여 규제 추적에 유용합니다.

## 성능 고려 사항
대용량 파일을 처리할 때 다음 모범 사례를 기억하세요:

- 전체 댓글 트리를 메모리에 로드하기보다 배치 단위로 처리합니다.
- 모든 댓글을 한 번에 제거해야 할 경우에만 `Document.getComments().clear()`를 사용합니다.
- 최신 Aspose.Words 버전으로 업그레이드하여 메모리 최적화된 댓글 처리를 활용합니다.

## 일반적인 문제 및 해결책
| 문제 | 해결책 |
|-------|----------|
| **댓글에 접근할 때 NullPointerException** | `getComments()`를 호출하기 전에 문서가 완전히 로드(`Document.load`)되었는지 확인하세요. |
| **답글이 Word UI에 표시되지 않음** | `ParentComment` 속성을 올바르게 설정하세요; 답글은 기존 댓글을 참조해야 합니다. |
| **타임스탬프가 UTC가 아닌 로컬 시간으로 표시됨** | UTC를 강제하려면 `Comment.getDateTime().withOffsetSameInstant(ZoneOffset.UTC)`를 사용하세요. |

## 자주 묻는 질문

**Q: Aspose.Words for Java를 상용 애플리케이션에서 사용할 수 있나요?**  
A: 네, 유효한 라이선스가 있으면 가능합니다; 평가용 무료 체험판도 제공됩니다.

**Q: 라이브러리가 암호로 보호된 Word 파일에서도 작동하나요?**  
A: 네, `LoadOptions`를 통해 문서를 로드할 때 비밀번호를 제공하면 됩니다.  

**Q: 지원되는 Java 버전은 어떤 것인가요?**  
A: Aspose.Words for Java는 JDK 8부터 JDK 21까지 지원하여 레거시와 최신 환경 모두를 포괄합니다.  

**Q: 200 MB보다 큰 문서는 어떻게 처리하나요?**  
A: `LoadOptions.setLoadFormat(LoadFormat.DOCX)`를 사용하고 `LoadOptions.setMemoryOptimization(true)`를 활성화하여 메모리 사용량을 줄이세요.  

**Q: 댓글을 CSV 파일로 내보낼 방법이 있나요?**  
A: `doc.getComments()`를 반복하면서 각 댓글의 속성을 표준 Java I/O를 사용해 CSV에 기록하면 됩니다.

---

**마지막 업데이트:** 2026-05-18  
**테스트 환경:** Aspose.Words for Java 24.12  
**작성자:** Aspose  

```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

{{< blocks/products/products-backtop-button >}}

## 관련 튜토리얼

- [Aspose.Words Java를 사용한 Word 문서에서 변경 내용 추적: 문서 개정에 대한 완전 가이드](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words for Java 튜토리얼로 주석 및 댓글 마스터하기](/words/java/annotations-comments/)
- [Aspose.Words for Java 마스터: Word 문서에 북마크 삽입 및 관리 방법](/words/java/content-management/aspose-words-java-manage-bookmarks/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

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

```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```