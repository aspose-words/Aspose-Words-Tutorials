---
date: '2025-11-13'
description: Aspose.Words for Java의 LayoutCollector와 LayoutEnumerator를 사용하여 페이지 범위를
  분석하고, 레이아웃 엔터티를 탐색하며, 콜백을 구현하고, 페이지 번호 매김을 효율적으로 재시작하는 방법을 배웁니다.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- page span analysis java
- traverse layout entities java
- page layout callbacks java
- restart page numbering java
- document pagination Java
- Aspose.Words layout API
- Java text processing
title: 'Aspose.Words Java: LayoutCollector 및 LayoutEnumerator 가이드'
url: /ko/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java 마스터하기: LayoutCollector 및 LayoutEnumerator를 활용한 텍스트 처리 완전 가이드

## 소개

Java 애플리케이션에서 복잡한 문서 레이아웃을 관리하는 데 어려움을 겪고 계신가요? 섹션이 차지하는 페이지 수를 파악하거나 레이아웃 엔터티를 효율적으로 순회하는 작업은 까다로울 수 있습니다. **Aspose.Words for Java**를 사용하면 `LayoutCollector`와 `LayoutEnumerator`와 같은 강력한 도구를 통해 이러한 과정을 간소화하고, 뛰어난 콘텐츠 제공에 집중할 수 있습니다. 이 포괄적인 가이드에서는 이러한 기능을 활용하여 문서 처리 능력을 향상시키는 방법을 살펴보겠습니다.

**배우게 될 내용:**
- Aspose.Words의 `LayoutCollector`를 사용해 정확한 페이지 범위 분석하기
- `LayoutEnumerator`로 문서를 효율적으로 순회하기
- 동적 렌더링 및 업데이트를 위한 레이아웃 콜백 구현하기
- 연속 섹션에서 페이지 번호 매기기를 효과적으로 제어하기

이 도구들이 문서 처리 프로세스를 어떻게 혁신할 수 있는지 알아보겠습니다. 시작하기 전에 아래 전제 조건 섹션을 확인해 주세요.

## 전제 조건

이 가이드를 따라하려면 다음이 필요합니다:

### 필수 라이브러리 및 버전
Aspose.Words for Java 버전 25.3이 설치되어 있는지 확인하십시오.

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

### 환경 설정 요구 사항
다음이 필요합니다:
- 머신에 설치된 Java Development Kit (JDK)
- 코드를 실행하고 테스트할 수 있는 IntelliJ IDEA 또는 Eclipse와 같은 IDE

### 지식 전제 조건
Java 프로그래밍에 대한 기본 이해가 있으면 보다 원활하게 따라갈 수 있습니다.

## Aspose.Words 설정
먼저 프로젝트에 Aspose.Words 라이브러리를 통합했는지 확인하십시오. 무료 체험 라이선스는 [여기](https://releases.aspose.com/words/java/)에서 받거나 필요에 따라 임시 라이선스를 사용할 수 있습니다. Java에서 Aspose.Words를 사용하려면 다음과 같이 초기화합니다:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

설정이 완료되었으니 `LayoutCollector`와 `LayoutEnumerator`의 핵심 기능을 살펴보겠습니다.

## 구현 가이드

### 기능 1: 페이지 범위 분석을 위한 LayoutCollector 사용
`LayoutCollector` 기능을 사용하면 문서 내 노드가 페이지에 걸치는 범위를 파악할 수 있어 페이지 매김 분석에 도움이 됩니다.

#### 개요
`LayoutCollector`를 활용하면任意의 노드에 대해 시작 페이지와 종료 페이지 인덱스를 확인하고, 해당 노드가 차지하는 전체 페이지 수를 알 수 있습니다.

#### 구현 단계

**1. Document 및 LayoutCollector 초기화**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. 문서 채우기**
다음 예제에서는 여러 페이지에 걸치는 콘텐츠를 추가합니다:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. 레이아웃 업데이트 및 메트릭 가져오기**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### 설명
- **`DocumentBuilder`**: 문서에 콘텐츠를 삽입하는 데 사용됩니다.
- **`updatePageLayout()`**: 정확한 페이지 메트릭을 보장합니다.

### 기능 2: LayoutEnumerator를 이용한 순회
`LayoutEnumerator`는 문서 레이아웃 엔터티를 효율적으로 순회할 수 있게 하며, 각 요소의 속성 및 위치에 대한 상세 정보를 제공합니다.

#### 개요
이 기능은 레이아웃 구조를 시각적으로 탐색하는 데 유용하며, 렌더링 및 편집 작업에 활용됩니다.

#### 구현 단계

**1. Document 및 LayoutEnumerator 초기화**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. 앞뒤로 순회하기**
문서 레이아웃을 순회하려면 다음과 같이 합니다:
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### 설명
- **`moveParent()`**: 상위 엔터티로 이동합니다.
- **순회 메서드**: 재귀적으로 구현되어 포괄적인 탐색을 수행합니다.

### 기능 3: 페이지 레이아웃 콜백
이 기능은 문서 처리 중 페이지 레이아웃 이벤트를 모니터링하기 위한 콜백 구현 방법을 보여줍니다.

#### 개요
`IPageLayoutCallback` 인터페이스를 사용해 섹션이 재배치되거나 변환이 완료되는 등 특정 레이아웃 변경에 반응할 수 있습니다.

#### 구현 단계

**1. 콜백 설정**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. 콜백 메서드 구현**
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

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### 설명
- **`notify()`**: 레이아웃 이벤트를 처리합니다.
- **`ImageSaveOptions`**: 렌더링 옵션을 구성합니다.

### 기능 4: 연속 섹션에서 페이지 번호 재시작
이 기능은 연속 섹션에서 페이지 번호 매기기를 제어하여 문서 흐름을 매끄럽게 유지하는 방법을 보여줍니다.

#### 개요
`ContinuousSectionRestart`를 사용해 다중 섹션 문서에서 페이지 번호를 효과적으로 관리합니다.

#### 구현 단계

**1. 문서 로드**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. 페이지 번호 매기기 옵션 구성**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### 설명
- **`setContinuousSectionPageNumberingRestart()`**: 연속 섹션에서 페이지 번호가 재시작되는 방식을 설정합니다.

## 실무 적용 사례
다음은 이러한 기능을 실제로 적용할 수 있는 시나리오입니다:
1. **문서 페이지 매김 분석:** `LayoutCollector`를 사용해 레이아웃을 분석하고 최적의 페이지 매김을 위해 콘텐츠를 조정합니다.
2. **PDF 렌더링:** `LayoutEnumerator`를 활용해 PDF를 정확히 탐색·렌더링하여 시각적 구조를 보존합니다.
3. **동적 문서 업데이트:** 콜백을 구현해 특정 레이아웃 변경 시 동작을 트리거하여 실시간 문서 처리를 강화합니다.
4. **다중 섹션 문서:** 연속 섹션이 포함된 보고서나 책에서 페이지 번호를 제어해 전문적인 포맷을 구현합니다.

## 성능 고려 사항
최적의 성능을 유지하려면:
- 레이아웃 분석 전에 불필요한 요소를 제거해 문서 크기를 최소화합니다.
- 효율적인 순회 방법을 사용해 처리 시간을 단축합니다.
- 특히 대용량 문서를 다룰 때 리소스 사용량을 모니터링합니다.

## 결론
`LayoutCollector`와 `LayoutEnumerator`를 마스터함으로써 Aspose.Words for Java에서 강력한 기능을 활용할 수 있게 되었습니다. 이 도구들은 복잡한 문서 레이아웃을 단순화할 뿐만 아니라 텍스트를 효과적으로 관리·처리하는 능력을 크게 향상시킵니다. 이제 이 지식을 바탕으로 고급 텍스트 처리 과제에 자신 있게 도전할 수 있습니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}