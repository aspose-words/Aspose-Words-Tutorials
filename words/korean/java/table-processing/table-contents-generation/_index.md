---
"description": "Aspose.Words for Java를 사용하여 동적 목차를 만드는 방법을 알아보세요. 단계별 안내와 소스 코드 예제를 통해 목차 생성을 마스터하세요."
"linktitle": "목차 세대"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "목차 세대"
"url": "/ko/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 목차 세대

## 소개

Word 문서에서 역동적이고 전문적인 목차(TOC)를 만드는 데 어려움을 겪어 보셨나요? 더 이상 고민하지 마세요! Aspose.Words for Java를 사용하면 전체 프로세스를 자동화하여 시간을 절약하고 정확성을 보장할 수 있습니다. 종합 보고서든 학술 논문이든, 이 튜토리얼은 Java를 사용하여 프로그래밍 방식으로 목차를 생성하는 방법을 안내합니다. 시작할 준비가 되셨나요? 시작해 볼까요!

## 필수 조건

코딩을 시작하기 전에 다음 사항이 있는지 확인하세요.

1. Java Development Kit(JDK): 시스템에 설치되어 있습니다. 다음에서 다운로드할 수 있습니다. [오라클 웹사이트](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words for Java 라이브러리: 다음에서 최신 버전을 다운로드하세요. [출시 페이지](https://releases.aspose.com/words/java/).
3. 통합 개발 환경(IDE): IntelliJ IDEA, Eclipse 또는 NetBeans 등.
4. 임시 라이센스: 평가 제한을 피하려면 임시 라이센스를 받으세요. [임시 면허](https://purchase.aspose.com/temporary-license/).

## 패키지 가져오기

Aspose.Words for Java를 효과적으로 사용하려면 필요한 클래스를 가져와야 합니다. 가져오는 클래스는 다음과 같습니다.

```java
import com.aspose.words.*;
```

Word 문서에서 동적 TOC를 생성하려면 다음 단계를 따르세요.

## 1단계: 문서 및 DocumentBuilder 초기화

첫 번째 단계는 새 문서를 만들고 사용하는 것입니다. `DocumentBuilder` 이를 조작할 클래스입니다.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Word 문서를 나타냅니다.
- `DocumentBuilder`: 문서를 쉽게 조작할 수 있는 도우미 클래스입니다.

## 2단계: 목차 삽입

이제 문서의 시작 부분에 TOC를 삽입해 보겠습니다.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: TOC 필드를 삽입합니다. 매개변수는 다음을 지정합니다.
  - `\o "1-3"`: 1~3레벨의 제목을 포함합니다.
  - `\h`: 항목을 하이퍼링크로 만듭니다.
  - `\z`: 웹 문서의 페이지 번호를 표시하지 않습니다.
  - `\u`: 하이퍼링크의 스타일을 유지합니다.
- `insertBreak`: TOC 뒤에 페이지 나누기를 추가합니다.

## 3단계: TOC를 채우기 위한 제목 추가

TOC를 채우려면 제목 스타일이 적용된 문단을 추가해야 합니다.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: 문단 스타일을 특정 제목 수준(예:)으로 설정합니다. `HEADING_1`, `HEADING_2`).
- `writeln`지정된 스타일로 문서에 텍스트를 추가합니다.

## 4단계: 중첩된 제목 추가

TOC 수준을 보여주려면 중첩된 제목을 포함합니다.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- TOC에 계층 구조를 표시하려면 더 깊은 수준의 제목을 추가합니다.

## 5단계: TOC 필드 업데이트

최신 제목을 표시하려면 TOC 필드를 업데이트해야 합니다.


```java
doc.updateFields();
```

- `updateFields`: 문서의 모든 필드를 새로 고쳐 TOC에 추가된 제목이 반영되도록 합니다.

## 6단계: 문서 저장

마지막으로, 원하는 형식으로 문서를 저장합니다.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`: 문서를 다음으로 내보냅니다. `.docx` 파일. 다음과 같은 다른 형식을 지정할 수 있습니다. `.pdf` 또는 `.txt` 필요한 경우.

## 결론

축하합니다! Aspose.Words for Java를 사용하여 Word 문서에 동적 목차를 성공적으로 만들었습니다. 몇 줄의 코드만으로 몇 시간씩 걸릴 수 있는 작업을 자동화했습니다. 이제 무엇을 해야 할까요? 다양한 제목 스타일과 형식을 실험하여 특정 요구 사항에 맞게 목차를 조정해 보세요.

## 자주 묻는 질문

### TOC 형식을 추가로 사용자 지정할 수 있나요?
물론입니다! 페이지 번호 포함, 텍스트 정렬, 사용자 지정 제목 스타일 사용 등 TOC 매개변수를 조정할 수 있습니다.

### Aspose.Words for Java를 사용하려면 라이센스가 필수인가요?
네, 모든 기능을 사용하려면 라이선스가 필요합니다. [임시 면허](https://purchase.aspose.com/temporary-license/).

### 기존 문서에 대한 TOC를 생성할 수 있나요?
네! 문서를 로드하세요 `Document` 객체를 삽입하고 TOC를 업데이트하려면 동일한 단계를 따르세요.

### PDF 내보내기에도 사용할 수 있나요?
예, 문서를 PDF로 저장하면 TOC가 PDF에 나타납니다. `.pdf` 체재.

### 더 많은 문서는 어디에서 찾을 수 있나요?
확인해 보세요 [Java 설명서를 위한 Aspose.Words](https://reference.aspose.com/words/java/) 더 많은 예와 자세한 내용은 여기를 참조하세요.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}