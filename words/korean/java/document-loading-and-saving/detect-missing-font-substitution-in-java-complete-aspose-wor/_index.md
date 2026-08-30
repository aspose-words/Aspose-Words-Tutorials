---
category: general
date: 2026-06-05
description: Aspose.Words를 사용하여 Java에서 누락된 글꼴 대체를 감지합니다. 신뢰할 수 있는 문서 처리를 위해 LoadOptions,
  FontSettings 및 경고 콜백을 구성하는 방법을 배웁니다.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: ko
og_description: Aspose.Words를 사용한 Java에서 누락된 글꼴 대체를 감지합니다. 이 가이드는 LoadOptions, FontSettings
  및 경고 콜백을 설정하여 누락된 글꼴을 포착하는 방법을 단계별로 보여줍니다.
og_title: Java에서 누락된 글꼴 대체 감지 – 전체 Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: Java에서 누락된 글꼴 대체 감지 – 완전한 Aspose.Words 가이드
url: /ko/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 누락된 폰트 대체 감지 – 완전한 Aspose.Words 가이드

Java에서 Word 문서를 로드할 때 **누락된 폰트 대체를 감지**하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 누락된 폰트는 PDF나 렌더링된 페이지를 조용히 망칠 수 있으며, 이를 일찍 발견하면 디버깅에 드는 시간을 크게 절약할 수 있습니다. 이 튜토리얼에서는 문서를 로드할 뿐만 아니라 폰트 대체가 발생했을 때 정확히 알려주는 실용적인 솔루션을 단계별로 살펴보겠습니다.

우리는 `LoadOptions` 생성부터 누락된 폰트를 교체할 때마다 명확한 메시지를 출력하는 `WarningCallback` 연결까지 모든 과정을 다룰 것입니다. 끝까지 읽으면 어떤 `.docx` 파일에도 사용할 수 있는 재사용 가능한 코드 조각을 얻고, 각 부분이 왜 중요한지 이해하게 됩니다. 추가 라이브러리는 필요 없으며 순수 Java와 Aspose.Words만 사용합니다.

## 배울 내용

- 맞춤형 **FontSettings**를 사용하도록 **LoadOptions**를 구성하는 방법.  
- **IWarningCallback**을 구현하여 `FONT_SUBSTITUTION` 경고를 포착하는 방법.  
- 누락된 폰트를 안전하게 모니터링하면서 문서를 로드하는 방법.  
- 예상 콘솔 출력 및 코드를 로깅 프레임워크에 맞게 조정하는 방법.  

**전제 조건**: Java 8+ 설치, 클래스패스에 Aspose.Words for Java (v23.12 이상) 포함, 그리고 설치되지 않은 폰트를 참조하는 샘플 `.docx` 파일. 이 정도면 충분합니다—추가 빌드 도구는 필요 없습니다.

---

## 단계 1: 프로젝트 설정 및 Aspose.Words 추가

코드에 들어가기 전에 Aspose.Words가 사용 가능한지 확인하세요. Maven을 사용한다면 `pom.xml`에 다음 의존성을 추가합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle을 선호한다면 동등한 내용은 다음과 같습니다:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

라이브러리가 클래스패스에 추가되면, 이제 **누락된 폰트 대체 감지**를 한 번의 메서드 호출로 수행할 준비가 됩니다.

---

## 단계 2: LoadOptions 생성 및 FontSettings 연결

솔루션의 핵심은 폰트 문제를 감시할 수 있는 `LoadOptions` 인스턴스를 준비하는 것입니다. 아래는 코드를 한 줄씩 설명한 내용입니다.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**왜 중요한가**: `LoadOptions`는 Aspose.Words에게 들어오는 파일을 *어떻게* 해석할지 알려줍니다. 맞춤형 `FontSettings`를 연결함으로써 로더에 (`IWarningCallback`) 훅을 제공하여 **누락된 폰트가 대체될 때 정확히** 작동하도록 합니다. 이 콜백이 없으면 Aspose.Words는 폰트를 조용히 교체하고 사용자는 이를 알 수 없습니다.

---

## 단계 3: 구성된 옵션으로 문서 로드

이제 경고 시스템이 준비되었으니, 문서 로드는 간단해집니다.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

`new Document(...)` 호출이 실행되면 Aspose.Words는 파일을 읽고 각 폰트 참조를 확인한 뒤, 시스템에 일치하는 폰트를 찾지 못하면 앞서 정의한 `warning` 메서드를 트리거합니다. 콘솔에 즉시 다음과 같은 줄이 표시됩니다:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

그 줄이 바로 여러분이 찾던 **누락된 폰트 대체 감지** 출력입니다.

---

## 단계 4: 결과 확인 및 콜백 조정 (고급)

### 4.1 빠른 검증

IDE에서 또는 `java -cp .;aspose-words-23.12.jar MissingFontDetector` 명령으로 프로그램을 실행하세요. 문서가 설치되지 않은 폰트를 참조하면 경고 메시지가 출력됩니다. 콘솔에 아무 메시지도 나타나지 않으면, 해당 폰트가 시스템에 존재하거나 문서가 누락된 폰트를 요청하지 않은 것입니다.

### 4.2 `System.out` 대신 로깅 사용

프로덕션 코드에서는 로거를 사용하는 것이 좋습니다:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

이 작은 변경으로 **누락된 폰트 대체 감지** 메커니즘이 기존 로깅 파이프라인과 원활히 동작합니다.

### 4.3 다른 경고 유형 처리

콜백은 폰트 문제뿐만 아니라 *모든* 경고를 받습니다. 다른 문제(e.g., `UNKNOWN_STYLE`)를 감시하고 싶다면 추가 `if` 분기를 넣으세요. 간단한 예시를 보이겠습니다:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## 단계 5: 흔히 발생하는 문제와 전문가 팁

| 문제점 | 발생 원인 | 해결 방법 |
|--------|----------------|-----|
| **경고가 나타나지 않음** | 폰트가 실제로 OS에 존재하거나, 문서가 Aspose.Words가 “찾음”으로 간주하는 대체 폰트를 사용합니다. | 시스템에서 해당 폰트를 일시적으로 삭제하거나 소스 문서에 실제로 존재하지 않는 폰트 이름을 사용하세요. |
| **콜백이 호출되지 않음** | `setWarningCallback`이 `LoadOptions`에 연결된 `FontSettings`와 *다른* 인스턴스에 호출되었습니다. | 콜백을 구성한 **후에** `loadOptions.setFontSettings(fontSettings)`를 호출했는지 확인하세요. |
| **성능 저하** | 콜백을 사용해 많은 대형 문서를 로드하면 오버헤드가 발생할 수 있습니다. | 배치 처리를 할 경우 단일 `FontSettings` 인스턴스를 캐시하여 로드에 재사용하세요. |
| **다중 스레드** | `FontSettings`는 기본적으로 스레드 안전하지 않습니다. | 스레드당 별도의 `FontSettings`를 만들거나 접근을 동기화하세요. |

**전문가 팁**: 웹 서비스용 PDF를 생성한다면, 모든 대체 경고를 리스트에 수집하여 콘솔에 출력하는 대신 API 응답에 포함시키는 것이 좋습니다.

---

## 전체 작동 예제 (복사‑붙여넣기 가능)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**예상 콘솔 출력** (파일이 누락된 폰트를 참조한다고 가정):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

누락된 폰트가 없으면 마지막 “Document loaded successfully.” 줄만 표시됩니다.

---

## 결론

우리는 Java에서 Aspose.Words를 사용해 **누락된 폰트 대체를 감지**하는 방법을 보여주었습니다. `LoadOptions`를 구성하고 `FontSettings` 인스턴스를 만든 뒤 `IWarningCallback`을 연결하면 라이브러리가 배경에서 교체하는 모든 폰트를 완전히 파악할 수 있습니다. 이 접근 방식은 조용한 렌더링 오류를 방지할 뿐 아니라 로깅, 알림, 혹은 자동 폰트 대체 삽입을 위한 훅도 제공합니다.

다음과 같이 활용할 수 있습니다:

- 콜백을 확장하여 경고를 리스트에 수집하고 API 응답에 포함시키기.  
- 이 기술을 **LoadOptions 구성**과 결합해 다른 시나리오(예: 맞춤 리소스 로딩)에도 적용하기.  
- 더 넓은 **Java Aspose.Words** 생태계 탐색: PDF 변환, 텍스트 추출, 메일 머지 수행 등.

시도해 보고, 로거를 조정하여 폰트가 누락될 때 애플리케이션이 알리도록 하세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Java에서 Aspose.Words를 사용한 폰트 대체 경고 캡처 – 완전 가이드](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Aspose.Words for Java에서 문서 옵션 및 설정 사용](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}