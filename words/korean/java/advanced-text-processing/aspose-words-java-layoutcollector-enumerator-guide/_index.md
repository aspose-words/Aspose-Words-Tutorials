---
date: '2025-11-12'
description: Aspose.Words for Java의 LayoutCollector와 LayoutEnumerator를 사용하여 페이지 범위를
  결정하고, 레이아웃 엔터티를 탐색하며, 연속 섹션에서 페이지 번호를 재시작하는 방법을 배웁니다.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- determine page span
- analyze document pagination
- restart page numbering
language: ko
title: 'Aspose.Words Java: LayoutCollector 및 LayoutEnumerator 가이드'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: LayoutCollector 및 LayoutEnumerator 가이드

## 소개  

복잡한 Java 문서에서 **페이지 범위 확인**, 페이지 매김 분석, 페이지 번호 재시작에 어려움을 겪고 계신가요? **Aspose.Words for Java**를 사용하면 `LayoutCollector`와 `LayoutEnumerator`를 통해 이러한 문제를 빠르게 해결할 수 있습니다. 이 가이드에서는 **LayoutCollector 사용 방법**, **LayoutEnumerator 탐색 방법**, 그리고 연속 섹션에서 페이지 번호를 제어하는 방법을 단계별 코드와 함께 보여드립니다.

배우게 될 내용:

1. `LayoutCollector`를 사용해 **노드의 페이지 범위**를 확인하는 방법.  
2. `LayoutEnumerator`로 **레이아웃 엔터티를 순회**하는 방법.  
3. 동적 렌더링을 위한 레이아웃 콜백 구현.  
4. 연속 섹션에서 **페이지 번호 재시작** 설정 방법.  

먼저 환경이 준비되었는지 확인해 보겠습니다.

## 필수 조건  

### 필수 라이브러리  

> **Note:** The code works with the latest Aspose.Words for Java release (no version number needed).  

**Maven**

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest</version>
</dependency>
```

**Gradle**

```gradle
implementation 'com.aspose:aspose-words:latest'
```

### 환경  

- JDK 17 이상.  
- IntelliJ IDEA, Eclipse 또는 선호하는 Java IDE.  

### 지식  

Java 문법과 객체 지향 개념에 대한 기본적인 이해가 있으면 예제를 따라가기 쉽습니다.

## Aspose.Words 설정  

먼저 프로젝트에 Aspose.Words 라이브러리를 추가하고 라이선스를 적용합니다(또는 평가판 사용). 아래 코드는 라이선스를 로드하고 라이브러리가 정상 작동하는지 확인하는 예시입니다:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file (skip this line for a trial)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

> **Tip:** 라이선스 파일은 버전 관리 시스템 밖에 보관하여 자격 증명을 보호하세요.

이제 두 가지 핵심 기능을 살펴보겠습니다.

## 1. LayoutCollector를 사용한 페이지 범위 분석 방법  

`LayoutCollector`를 사용하면 문서 내任意 노드의 **페이지 범위**를 확인할 수 있어 페이지 매김 분석에 필수적입니다.

### 단계별 구현  

1. **새 Document와 LayoutCollector 인스턴스를 생성합니다.**  
2. **여러 페이지에 걸치는 콘텐츠를 추가합니다.**  
3. **레이아웃을 새로 고치고 페이지 범위 메트릭을 조회합니다.**  

```java
// 1. Initialize Document and LayoutCollector
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);

// 2. Populate the Document with multi‑page content
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);

// 3. Update layout and retrieve page‑span information
layoutCollector.clear();          // Reset any previous state
doc.updatePageLayout();           // Force layout calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected number of pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Explanation**

- `DocumentBuilder`를 이용해 텍스트와 페이지 구분자를 삽입하면 문서가 자동으로 여러 페이지에 걸칩니다.  
- `updatePageLayout()`은 Aspose.Words에게 레이아웃을 계산하도록 강제하여 정확한 페이지 번호를 얻을 수 있게 합니다.  
- `getNumPagesSpanned()`는 전달된 노드가 차지하는 전체 페이지 수를 반환합니다(여기서는 전체 문서).

## 2. LayoutEnumerator 탐색 방법  

`LayoutEnumerator`는 **레이아웃 엔터티(페이지, 단락, 런 등)의 구조화된 뷰**를 제공하며, 이를 앞·뒤로 이동하면서 탐색할 수 있습니다.

### 단계별 구현  

1. 레이아웃 엔터티가 포함된 기존 문서를 로드합니다.  
2. `LayoutEnumerator` 인스턴스를 생성합니다.  
3. 페이지 레벨로 이동한 뒤, 헬퍼 메서드를 사용해 앞·뒤로 순회합니다.  

```java
// 1. Load the document containing layout entities
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");

// 2. Initialize LayoutEnumerator
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);

// 3. Position the enumerator at the page level
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Forward traversal
traverseLayoutForward(layoutEnumerator, 1);

// Backward traversal
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Note:** `traverseLayoutForward`와 `traverseLayoutBackward` 메서드는 레이아웃 트리를 재귀적으로 탐색하는 헬퍼이며, 경계 상자, 글꼴 정보, 사용자 메타데이터 등을 수집하도록 커스터마이즈할 수 있습니다.

## 3. 페이지 레이아웃 콜백 구현 방법  

때때로 레이아웃 이벤트에 반응해야 할 때가 있습니다(예: 섹션이 재배치될 때 또는 다른 형식으로 변환이 완료될 때). `IPageLayoutCallback` 인터페이스를 구현하면 이러한 알림을 받을 수 있습니다.

### 단계별 구현  

1. 문서의 레이아웃 옵션에 콜백 인스턴스를 설정합니다.  
2. `PART_REFLOW_FINISHED`와 `CONVERSION_FINISHED` 이벤트를 처리하는 로직을 정의합니다.  

```java
// 1. Register the callback
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();   // Triggers the callback during layout processing

// 2. Callback implementation
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs args) throws Exception {
        if (args.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            renderPage(args, args.getPageIndex());
        } else if (args.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            System.out.println("Document conversion finished.");
        }
    }

    private void renderPage(PageLayoutCallbackArgs args, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            args.getDocument().save(stream, saveOptions);
        }
    }
}
```

**Explanation**

- `notify()`는 모든 레이아웃 이벤트를 수신합니다. 우리는 관심 있는 이벤트만 필터링합니다.  
- 섹션이 재배치된 후 `renderPage()`가 호출되어 해당 페이지를 PNG 이미지로 저장합니다.  

## 4. 연속 섹션에서 페이지 번호 재시작 방법  

문서에 연속 섹션이 포함된 경우, 새로운 물리적 페이지가 나타날 때만 페이지 번호를 재시작하도록 설정할 수 있습니다. 이는 `ContinuousSectionRestart` 옵션으로 제어합니다.

### 단계별 구현  

1. 대상 문서를 로드합니다.  
2. `ContinuousSectionPageNumberingRestart` 옵션을 설정합니다.  
3. 변경 사항을 적용하기 위해 레이아웃을 새로 고칩니다.  

```java
// 1. Load the multi‑section document
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");

// 2. Configure page‑numbering restart behavior
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);

// 3. Update layout to reflect the new numbering scheme
doc.updatePageLayout();
System.out.println("Page numbering restart configured for continuous sections.");
```

**Explanation**

- `FROM_NEW_PAGE_ONLY` 옵션은 새로운 물리적 페이지가 나타날 때만 번호를 재시작하도록 Aspose.Words에 지시하여, 연속 섹션 간에 매끄러운 흐름을 유지합니다.

## 실용적인 적용 사례  

| 시나리오 | 적용 기능 | 이점 |
|----------|-----------|------|
| **문서 페이지 매김 감사** | `LayoutCollector` | 페이지를 초과하는 섹션을 빠르게 찾을 수 있습니다. |
| **정확한 시각적 일치를 요구하는 PDF 렌더링** | `LayoutEnumerator` + 콜백 | 레이아웃 세부 정보를 활용해 정밀하게 렌더링합니다. |
| **각 페이지 레이아웃 후 워터마크 자동 삽입** | 페이지 레이아웃 콜백 | 페이지가 배치될 때 즉시 반응하여 워터마크를 추가합니다. |
| **맞춤 번호 매김이 필요한 다섹션 보고서** | 연속 섹션 번호 재시작 | 수동 편집 없이 전문적인 페이지 번호를 유지합니다. |

## 성능 팁  

- `updatePageLayout()` 호출 전에 **사용되지 않는 노드**를 정리해 메모리 사용량을 최소화합니다.  
- 여러 쿼리를 수행할 때는 **LayoutCollector 인스턴스를 재사용**하여 객체 생성 비용을 절감합니다.  
- 매우 큰 문서에서는 **재귀 깊이**를 제한해 스택 오버플로우를 방지합니다.  

## 결론  

**LayoutCollector 사용법**, **LayoutEnumerator 탐색법**, 그리고 **연속 섹션에서 페이지 번호 재시작**을 마스터함으로써 Aspose.Words for Java를 활용한 고급 텍스트 처리 도구 상자를 갖추게 되었습니다. 이제 **페이지 범위 확인**, **문서 페이지 매김 분석**, **레이아웃 동작 제어**를 자신 있게 수행할 수 있습니다. 이 기술을 보고서, 전자책, 자동화된 문서 워크플로 등에 적용하면 정확도와 생산성이 크게 향상될 것입니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}