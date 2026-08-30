---
category: general
date: 2026-06-27
description: Aspose.Words를 사용하여 Java에서 글꼴 대체 경고를 캡처하는 방법을 배웁니다. 이 단계별 튜토리얼에서는 경고 콜백
  및 LoadOptions 사용법도 다룹니다.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: ko
og_description: Aspose.Words를 사용하여 Java에서 글꼴 대체 경고를 포착합니다. 이 가이드를 따라 경고 콜백을 설정하고,
  LoadOptions를 사용하며, 누락된 글꼴을 처리하세요.
og_title: Java에서 글꼴 대체 경고 캡처 – Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Aspose.Words를 사용한 Java에서 글꼴 대체 경고 캡처 – 완전 가이드
url: /ko/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 Aspose.Words를 사용하여 폰트 대체 경고 캡처 – 완전 가이드

이국적인 서체를 사용하는 DOCX를 로드할 때 **폰트 대체 경고를 캡처**해야 했던 적이 있나요? 당신만 그런 것이 아닙니다. 많은 실제 프로젝트—예를 들어 자동 보고서 생성기나 배치 문서 변환기—에서 누락된 폰트는 레이아웃 정확성을 해칠 수 있는 무음 대체를 일으킵니다.  

다행히도 Aspose.Words는 이러한 경고를 수신할 수 있는 깔끔한 방법을 제공합니다. 이 튜토리얼에서는 **LoadOptions** 설정, **Aspose.Words warning callback** 연결, 그리고 *폰트 대체* 알림을 콘솔에 출력하는 과정을 단계별로 살펴봅니다. 마지막까지 진행하면 폰트가 언제 교체되는지 정확히 알 수 있고, 프로그래밍적으로 어떻게 대응해야 하는지도 이해하게 됩니다.

> **얻을 수 있는 것:** 완전 실행 가능한 Java 코드 스니펫, 각 구성 요소가 중요한 이유에 대한 설명, 그리고 사용자 정의 폰트 디렉터리와 같은 엣지 케이스를 처리하는 팁.

## 전제 조건 및 필요 사항

시작하기 전에 아래 항목을 준비하세요:

- Java 8 이상 설치 (코드는 Java 11+에서도 동작합니다).
- 최신 Aspose.Words for Java JAR (공식 사이트 또는 Maven Central에서 다운로드).
- 머신에 설치되지 않은 폰트를 참조하는 DOCX 파일 (예: Aspose 데모 세트에 있는 *font‑rich.docx*).
- 적당한 IDE (IntelliJ IDEA, Eclipse, 혹은 Java 확장 기능이 포함된 VS Code).

Aspose.Words 외에 추가 라이브러리는 필요 없으며, 예제는 순수 `main` 메서드에서 실행됩니다.

## Step 1: Set Up LoadOptions – The Entry Point for Custom Loading

`LoadOptions`는 Aspose.Words의 설정 컨테이너로, 라이브러리에게 문서를 *어떻게* 읽을지 알려줍니다. 기본적으로 누락된 폰트를 무음으로 대체하지만, 경고 콜백을 지정하면 동작을 바꿀 수 있습니다.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**왜 중요한가:** `LoadOptions` 없이 문서를 로드하면 조용히 로드되고, 누락된 폰트에 대한 가시성을 잃게 됩니다. 인스턴스를 생성하면 경고 시스템에 훅을 연결할 수 있습니다.

## Step 2: Define a Warning Callback to *Capture Font Substitution Warnings*

Aspose.Words는 `IWarningCallback` 인터페이스를 통해 경고 이벤트를 전달합니다. 인라인(또는 별도 클래스)으로 구현하고 `WarningType.FONT_SUBstitution`을 필터링하세요.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**설명:**  
- `info.getWarningType()` 은 경고의 카테고리를 알려줍니다.  
- `WarningType.FONT_SUBSTITUTION` 은 우리가 관심 있는 열거형 값입니다.  
- `info.getDescription()` 은 인간이 읽을 수 있는 메시지를 포함합니다. 예: *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

설명을 출력함으로써 **폰트 대체 경고를 실시간으로 캡처**할 수 있습니다.

## Step 3: Load the Document Using the Configured LoadOptions

이제 콜백이 설정되었으니 DOCX를 로드합니다. 경고 콜백은 파싱 중 자동으로 발생합니다.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

`YOUR_DIRECTORY` 를 실제 테스트 파일 경로로 바꾸세요. `Document` 생성자가 실행될 때 누락된 폰트가 있으면 앞서 정의한 콜백이 호출되고, 콘솔에 대체 메시지가 표시됩니다.

## Step 4: Verify the Loaded Document (Optional but Helpful)

로드 후에는 문서 무결성(페이지 수, 텍스트 추출 등)을 확인하고 싶을 수 있습니다. 이 단계는 경고 캡처에 필수는 아니지만, 대체가 레이아웃에 미치는 영향을 파악하는 데 도움이 됩니다.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

폰트가 대체되면 레이아웃이 약간 변할 수 있습니다; 페이지 수를 확인하면 이러한 변화를 감지할 수 있습니다.

## Step 5: Advanced – Handling Substituted Fonts Programmatically

경고를 단순히 로그에 남기는 것 이상으로, 대체 폰트를 임베드하거나 스타일을 조정해야 할 수도 있습니다. 아래는 빠르게 적용할 수 있는 패턴입니다.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Aspose.Words에 원본 폰트가 들어 있는 폴더를 지정하면 *대체를 완전히 방지*할 수 있습니다. 폴더가 없을 경우에도 경고 콜백이 이벤트를 캡처하므로 대체 전략을 마련할 수 있습니다.

## Full Working Example

모든 코드를 합치면 다음과 같은 완전 실행 가능한 프로그램이 됩니다:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**예상 콘솔 출력** (폰트가 누락된 경우):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

모든 폰트가 존재하면 콜백은 조용히 동작합니다—출력이 없으며, 이것이 기대되는 동작입니다.

## Common Pitfalls & Pro Tips

| 문제점 | 발생 원인 | 해결 방법 |
|---------|----------------|-----|
| **Callback never fires** | `LoadOptions`에 콜백을 연결하지 않았거나 `Document` 생성 시 `loadOptions`를 전달하지 않았음. | 항상 `loadOptions.setWarningCallback(...)` 를 호출하고 `new Document(path, loadOptions)` 오버로드를 사용하세요. |
| **Too many warnings clutter the log** | 많은 누락 폰트가 있는 대형 문서는 대체당 하나씩 경고를 생성합니다. | `info.getDescription()` 에서 특정 폰트명을 확인하거나, 경고를 리스트에 모아 나중에 처리하도록 필터링하세요. |
| **Substituted fonts affect layout** | 대체 폰트는 메트릭(크기, 간격)이 다를 수 있습니다. | 사용자 정의 폰트 폴더를 제공하거나(5단계 참조) 로드 후 문서 스타일을 조정하세요. |
| **Running on a headless server** | 기본 폰트 대체가 서버에 설치되지 않은 시스템 폰트에 의존할 수 있습니다. | 필요한 폰트를 애플리케이션에 포함하고 `FontSettings` 를 해당 폴더로 지정하세요. |

## Frequently Asked Questions

**Q: Does this work with PDF or other formats?**  
A: Yes. The warning callback is format‑agnostic; it fires for any document type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference is the set of warnings that may appear.

**Q: Can I capture other warning types, like *image resolution* warnings?**  
A: Absolutely. Inside the `warning` method, inspect `info.getWarningType()` for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them accordingly.

**Q: What if I need the list of substituted fonts after the document loads?**  
A: Store each `info.getDescription()` in a `List<String>` inside the callback. After loading, you’ll have a collection you can log, send to a monitoring service, or use to trigger a font‑download routine.

## Conclusion

이제 Java에서 Aspose.Words를 사용해 **폰트 대체 경고를 캡처**하는 방법, 각 구성 요소가 중요한 이유, 그리고 실제 시나리오에 적용하는 방법을 알게 되었습니다. `LoadOptions`, `Aspose.Words warning callback`, 그리고 선택적인 `FontSettings` 를 활용하면 누락된 폰트를 완전히 가시화하고 문서 변환 파이프라인을 안정적으로 유지할 수 있습니다.

다음 단계가 준비되셨나요? `System.out.println` 을 SLF4J와 같은 로거로 교체하거나, 경고 리스트를 UI에 통합해 배치 변환을 최종 확정하기 전에 사용자에게 알릴 수 있습니다. 또한 **Aspose.Words warning callback** 을 활용해 *지원되지 않는 기능*이나 *고해상도 이미지* 경고와 같은 다른 유형의 경고도 탐색해 보세요.  

행복한 코딩 되시길 바라며, PDF가 예기치 않은 폰트 교체로 고통받지 않기를 바랍니다! 

![Screenshot showing console output of captured font substitution warnings](image-placeholder.png "capture font substitution warnings")

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 연관된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}