---
date: '2025-11-12'
description: Aspose.Words for Java의 LayoutCollector와 LayoutEnumerator를 사용하여 페이지 매김을
  분석하고, 문서 레이아웃을 탐색하며, 레이아웃 콜백을 구현하고, 연속 섹션에서 페이지 번호를 다시 시작하는 방법을 배웁니다.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: ko
title: Aspose.Words 레이아웃 도구를 사용한 Java 페이지 매김 분석
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words 레이아웃 도구를 사용한 Java 페이지 매김 분석

## Introduction  

Java 애플리케이션에서 **페이지 매김을 분석**하거나 **문서 레이아웃을 순회**해야 할 경우, Aspose.Words for Java는 두 가지 강력한 API인 **`LayoutCollector`**와 **`LayoutEnumerator`**를 제공합니다. 이 클래스들을 사용하면 노드가 차지하는 페이지 수를 확인하고, 모든 레이아웃 엔터티를 탐색하며, 레이아웃 이벤트에 반응하고, 연속 섹션에서 페이지 번호를 다시 시작할 수 있습니다. 이 가이드에서는 각 기능을 단계별로 살펴보고 실제 코드 예제를 보여주며 예상 결과를 설명하여 바로 적용할 수 있도록 합니다.

배우게 될 내용:

* **LayoutCollector**를 사용하여任意 노드의 시작 페이지와 종료 페이지를 가져오기 (layoutcollector 페이지 범위 사용)  
* **LayoutEnumerator**로 문서 레이아웃 순회하기 (문서 레이아웃 순회)  
* 페이지 매김 이벤트에 반응하는 **레이아웃 콜백** 구현하기 (레이아웃 콜백 구현)  
* 연속 섹션에서 **페이지 번호 다시 시작**하기 (페이지 번호 다시 시작 섹션)  

시작해 보겠습니다.

## Prerequisites  

### Required Libraries  

| 빌드 도구 | 종속성 |
|------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Note:** 호환성을 위해 버전 번호가 유지됩니다; 코드는 최신 Aspose.Words for Java 릴리스와 모두 작동합니다.

### Environment  

* JDK 8 이상  
* IntelliJ IDEA 또는 Eclipse와 같은 IDE  

### Knowledge  

기본 Java 프로그래밍과 Maven/Gradle에 대한 이해만 있으면 예제를 따라 할 수 있습니다.

## Setting Up Aspose.Words  

레이아웃 API를 호출하기 전에 라이브러리를 라이선스(또는 평가 모드)로 설정해야 합니다. 아래 스니펫은 최소 초기화 코드를 보여줍니다.

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*이 코드는 문서를 수정하지 않으며, 단지 Aspose 환경을 준비합니다.*  

이제 핵심 기능을 살펴보겠습니다.

## Feature 1: Using **LayoutCollector** to Analyze Pagination  

`LayoutCollector`는 `Document`의 모든 노드를 해당 노드가 차지하는 페이지와 매핑합니다. 이는 페이지 매김 분석을 위해 **layoutcollector 페이지 범위 사용**하는 가장 신뢰할 수 있는 방법입니다.

### Step‑by‑step implementation  

1. **새 문서를 만들고 LayoutCollector를 연결**합니다.  
2. **페이지 매김을 강제하는 내용**을 삽입합니다(예: 페이지 나누기, 섹션 나누기).  
3. `updatePageLayout()`으로 **레이아웃을 새로 고침**합니다.  
4. **시작 페이지, 종료 페이지 및 전체 페이지 수**를 컬렉터에 질의합니다.

#### 1️⃣ Initialize Document and LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Populate the Document  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Update Layout and Retrieve Metrics  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Expected output**

```
Document spans 5 pages.
```

> **Why it works:** `updatePageLayout()`은 Aspose.Words가 레이아웃을 다시 계산하도록 강제하고, 이후 `LayoutCollector`가 정확한 페이지 범위를 보고할 수 있게 합니다.

## Feature 2: Traversing Document Layout with **LayoutEnumerator**  

**문서 레이아웃을 순회**해야 할 때(예: 사용자 정의 렌더링 또는 분석) `LayoutEnumerator`는 페이지, 단락, 줄, 단어를 트리 형태로 보여줍니다.

### Step‑by‑step implementation  

1. 레이아웃 엔터티가 포함된 기존 문서를 로드합니다.  
2. `LayoutEnumerator` 인스턴스를 생성합니다.  
3. 루트 `PAGE` 엔터티로 이동합니다.  
4. 재귀 헬퍼 메서드를 사용해 레이아웃을 앞·뒤로 탐색합니다.

#### 1️⃣ Load Document and Create Enumerator  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Position on the Page Level  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Forward Traversal (Depth‑First)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Backward Traversal  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Helper methods**(`traverseLayoutForward` / `traverseLayoutBackward`)는 재귀적으로 모든 자식 엔터티를 방문하고 타입과 페이지 인덱스를 출력하도록 구현됩니다. 통계 수집, 그래픽 렌더링, 레이아웃 속성 수정 등에 맞게 조정할 수 있습니다.

## Feature 3: Implementing **Layout Callbacks**  

때때로 Aspose.Words가 문서의 일부 레이아웃을 완료했을 때 반응해야 할 필요가 있습니다. `IPageLayoutCallback`을 구현하면 **레이아웃 콜백 구현** 로직(예: 각 페이지를 이미지로 저장)을 작성할 수 있습니다.

### Step‑by‑step implementation  

1. 문서의 `LayoutOptions`에 콜백 인스턴스를 할당합니다.  
2. 콜백 내부에서 `PART_REFLOW_FINISHED`와 `CONVERSION_FINISHED` 이벤트를 처리합니다.  
3. `ImageSaveOptions`를 사용해 현재 페이지를 PNG로 렌더링합니다.

#### 1️⃣ Register the Callback  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Callback Class  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**What happens:** 레이아웃 파트가 재배치될 때마다 콜백이 해당 페이지를 PNG