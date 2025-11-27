---
date: '2025-11-27'
description: Aspose.Words를 사용하여 Java에서 북마크를 생성하고, 북마크가 포함된 PDF를 생성하며, Word를 PDF로 변환하는
  방법을 배웁니다. 이 가이드는 중첩 북마크와 개요 수준을 다룹니다.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: ko
title: Aspose.Words Java를 사용하여 PDF에 북마크를 만들고 개요 레벨을 설정하는 방법
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java를 사용하여 PDF에서 책갈피 만들기 및 개요 수준 설정 방법

## 소개
Word 문서를 PDF로 변환할 때 정리된 **책갈피 만들기**에 어려움을 겪은 적이 있다면, 여기가 바로 맞는 곳입니다. 이 튜토리얼에서는 책갈피가 포함된 PDF를 생성하고, 책갈피를 중첩하며, 개요 수준을 지정하는 전체 과정을 단계별로합니다. 최종적으로 모든 PDF 뷰어에서 작동하는 깔끔한 책갈피 계층 구조를 가진 **Word PDF Java**‑style 변환을 할 수 있게 됩니다.

### 배울 내용
- 개발 환경에 Aspose.Words for Java 설정하기.  
- **책갈피 만들기**를 프로그래밍 방식으로 수행하고 중첩하기.  
- 문서 구조를 반영하는 책갈피가 포함된 PDF를 생성하도록 책갈피 개요 수준을 구성하기.  
- 책갈피 계층 구조를 유지하면서 Word 파일을 PDF로 저장하기.

## 빠른 답변
- **문서를 빌드하기 위한 기본 클래스는 무엇인가요?** `DocumentBuilder`.  
- **책갈피 계층 구조를 제어하는 옵션은?** `PdfSaveOptions` 내부의 `BookmarksOutlineLevelCollection`.  
- **Maven 또는 Gradle을 사용할 수 있나요?** 예 – 아래에 모두 표시됩니다.  
- **라이선스가 필요합니까?** 테스트용으로는 무료 체험판으로 충분하지만, 운영 환경에서는 정식 라이선스가 필요합니다.  
- **이 방법이 대용량 문서에 적합한가요?** 예, 하지만 메모리 최적화 기법(예: 사용되지 않는 리소스 제거)을 고려하세요.

### 사전 요구 사항
시작하기 전에 다음을 확인하세요:

- **라이브러리 및 종속성** – Aspose.Words for Java (25.3 이상).  
- **환경** – JDK 8 이상, IntelliJ IDEA 또는 Eclipse와 같은 IDE.  
- **기본 지식** – Java 프로그래밍 기본 및 Maven 또는 Gradle 사용 경험.

## Aspose.Words 설정
프로젝트에 필요한 종속성을 포함합니다. Maven 또는 Gradle을 사용해 Aspose.Words를 추가하는 방법은 다음과 같습니다:

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

### 라이선스 획득
Aspose.Words는 상용 라이브러리이지만 무료 체험으로 시작할 수 있습니다:

1. **무료 체험** – [Aspose 릴리스 페이지](https://releases.aspose.com/words/java/)에서 다운로드합니다.  
2. **임시 라이선스** – 단기 키가 필요하면 [임시 라이선스 페이지](https://purchase.aspose.com/temporary-license/)에서 신청합니다.  
3. **정식 라이선스** – 운영용으로 [Aspose 구매 포털](https://purchase.aspose.com/buy)에서 구매합니다.

라이선스 파일을 얻은 후, 애플리케이션 시작 시 로드하여 모든 기능을 활성화합니다.

## Aspose.Words Java로 PDF에서 책갈피 만들기
아래에서는 구현을 명확한 번호 단계로 나눕니다. 각 단계는 간단한 설명과 원본 코드 블록(변경 없음)을 포함합니다.

### 단계 1: Document 및 DocumentBuilder 초기화
새 `Document` 인스턴스와 콘텐츠 및 책갈피 삽입을 가능하게 하는 `DocumentBuilder`를 시작합니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 단계 2: 첫 번째(부모) 책갈피 삽입
나중에 자식 책갈피를 포함할 최상위 책갈피를 생성합니다.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### 단계 3: 부모 안에 자식 책갈피 중첩
이제 첫 번째 책갈피 안에 두 번째 책갈피를 추가하여 중첩을 보여줍니다.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### 단계 4: 부모 책갈피 닫기
중첩된 콘텐츠 뒤에 외부 책갈피를 종료합니다.

```java
builder.endBookmark("Bookmark 1");
```

### 단계 5: 독립적인 세 번째 책갈피 추가
중첩되지 않은 추가 책갈피를 언제든지 추가할 수 있습니다.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## 책갈피 개요 수준 구성
책갈피가 배치된 후, Aspose.Words에 PDF 개요(왼쪽 탐색 창)에 책갈피가 어떻게 표시될지 알려줍니다.

### 단계 6: PdfSaveOptions 준비
`PdfSaveOptions`를 사용해 개요 설정에 접근합니다.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### 단계 7: 계층 수준 할당
각 책갈피에 정수 수준을 부여합니다; 숫자가 낮을수록 계층 상위에 위치합니다.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### 단계 8: 문서를 PDF로 저장
마지막으로 책갈피 개요를 유지하면서 Word 문서를 PDF로 내보냅니다.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## 이 방법으로 책갈피가 있는 PDF를 생성하는 이유
- **전문적인 탐색** – 독자는 섹션으로 바로 이동할 수 있어 대형 보고서나 법률 계약서의 사용성을 향상시킵니다.  
- **전체 제어** – 계층 구조는 PDF 뷰어가 아니라 사용자가 직접 결정합니다.  
- **크로스 플랫폼** – 순수 Java이므로 Windows, Linux, macOS에서 동일하게 동작합니다.  

## 일반적인 문제와 해결책

| 증상 | 가능한 원인 | 해결 방법 |
|---|---|---|
| PDF에 책갈피가 없음 | 매칭되는 `endBookmark` 없이 `startBookmark`만 존재 | 모든 `startBookmark`에 대응되는 `endBookmark`가 있는지 확인합니다. |
| 계층 구조 오류 | 개요 수준이 순서대로 지정되지 않음 | 부모 책갈피가 자식보다 낮은 수준 번호를 갖도록 합니다. |
| 라이선스 미적용 | 문서 생성 전에 라이선스 파일을 로드하지 않음 | 애플리케이션 시작 시 라이선스를 로드합니다 (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## 실용적인 적용 사례
1. **법률 문서** – 조항, 부록, 부속서를 빠르게 탐색합니다.  
2. **재무 보고서** – 손익계산서, 대차대조표, 주석 등 섹션 간 이동.  
3. **e‑러닝 자료** – PDF 개요와 일치하는 목차 제공.

## 성능 고려 사항
- **메모리 관리** – 매우 큰 Word 파일의 경우 저장 전에 `doc.cleanup()` 호출을 고려합니다.  
- **리소스 최적화** – 사용되지 않는 이미지나 스타일을 제거해 PDF 크기를 작게 유지합니다.

## 자주 묻는 질문

**Q: Aspose.Words for Java를 어떻게 설치하나요?**  
A: 앞서 보여준 Maven 또는 Gradle 의존성을 추가하고, 라이선스 파일을 클래스패스에 배치한 뒤 런타임에 로드합니다.

**Q: 개요 수준을 설정하지 않고도 책갈피를 만들 수 있나요?**  
A: 예, 하지만 PDF 뷰어는 이를 평면 목록으로 표시하므로 복잡한 문서에서는 탐색이 어려울 수 있습니다.

**Q: 책갈피를 얼마나 깊게 중첩할 수 있나요?**  
A: 기술적으로 제한은 없지만 대부분의 PDF 뷰어는 9단계까지 편안히 지원합니다. 독자를 위해 논리적인 계층 구조를 유지하세요.

**Q: Aspose는 매우 큰 Word 파일을 어떻게 처리하나요?**  
A: 라이브러리는 콘텐츠를 스트리밍하고 `Document.optimizeResources()`와 같은 메서드를 제공해 메모리 사용량을 줄입니다.

**Q: PDF 생성 후에 책갈피를 편집할 수 있나요?**  
A: 물론입니다 – 기존 PDF에서 책갈피를 추가, 제거 또는 이름 변경하려면 Aspose.PDF for Java를 사용할 수 있습니다.

## 리소스
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)  
- [Download Latest Releases](https://releases.aspose.com/words/java/)  
- [Purchase a License](https://purchase.aspose.com/buy)  
- [Free Trial](https://releases.aspose.com/words/java/)  
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2025-11-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose