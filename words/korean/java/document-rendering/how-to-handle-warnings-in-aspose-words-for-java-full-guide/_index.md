---
category: general
date: 2026-06-24
description: Java에서 Word 파일을 처리할 때 경고를 다루는 방법. 글꼴을 캡처하고, 글꼴 메시지를 출력하며, 누락된 글꼴을 원활하게
  처리하는 방법을 배웁니다.
draft: false
keywords:
- how to handle warnings
- how to capture fonts
- print font messages
- handle missing fonts
language: ko
og_description: Aspose.Words for Java에서 경고를 처리하는 방법. 이 가이드는 글꼴을 캡처하고, 글꼴 메시지를 출력하며,
  누락된 글꼴을 효율적으로 관리하는 방법을 보여줍니다.
og_title: Aspose.Words에서 경고 처리 방법 – 완전한 Java 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  headline: how to handle warnings in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  name: how to handle warnings in Aspose.Words for Java – Full Guide
  steps:
  - name: The document actually references a missing font.
    text: The document actually references a missing font.
  - name: The path to `input.docx` is correct.
    text: The path to `input.docx` is correct.
  - name: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
    text: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Aspose.Words for Java에서 경고 처리 방법 – 전체 가이드
url: /ko/java/document-rendering/how-to-handle-warnings-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 경고를 처리하는 방법 – 전체 가이드

Aspose.Words로 Word 문서를 로드할 때 나타나는 **경고를 처리하는 방법**이 궁금했나요? 누락된 글꼴에 대한 난해한 메시지를 보고 “아, PDF가 가운데에서 벗어나 있네—이제 어떻게 하지?”라고 생각한 적이 있나요? 당신만 그런 것이 아닙니다. 실제 프로젝트에서 글꼴 대체 경고는 레이아웃 정확성을 망치는 조용한 원인입니다.

이 튜토리얼에서는 실용적인 해결책을 단계별로 살펴보겠습니다: 경고 콜백을 등록하고, 글꼴 관련 알림을 감지하며, **글꼴 메시지를 출력**하여 대체 글꼴을 삽입할지 혹은 사용자 정의 글꼴 파일을 제공할지 결정할 수 있습니다. 끝까지 읽으면 **글꼴을 캡처하는 방법**, 누락된 글꼴을 우아하게 **처리하는 방법**, 그리고 문서 변환 파이프라인을 견고하게 유지하는 방법을 알게 됩니다.

## 배울 내용

- Aspose.Words 경고 콜백의 목적.
- *글꼴 대체* 경고를 감지하고 필터링하는 방법.
- 디버깅을 위한 **글꼴 메시지 출력**을 로그하거나 표시하는 방법.
- 프로덕션 환경에서 **누락된 글꼴을 처리**하는 전략.
- Maven 또는 Gradle 프로젝트에 바로 넣어 사용할 수 있는 완전한 실행 가능한 Java 예제.

### 전제 조건

- Java 8 이상 (코드는 JDK 11에서도 작동합니다).
- Aspose.Words for Java 라이브러리 (Aspose 사이트에서 다운로드하거나 Maven/Gradle 의존성을 추가).
- 로컬에 설치되지 않은 글꼴을 참조하는 샘플 `input.docx` (콜백 테스트에 적합).

---

## Step 1: 프로젝트 설정 및 Aspose.Words 가져오기

경고를 **처리**하려면 Aspose.Words를 인식하는 Java 프로젝트가 필요합니다. Maven을 사용한다면 `pom.xml`에 다음 코드를 추가하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

Gradle의 경우 동일하게 다음과 같습니다:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

의존성이 해결되면 Java 소스 파일에 필요한 클래스를 import합니다:

```java
import com.aspose.words.*;
```

> **팁:** Aspose 라이브러리를 최신 상태로 유지하세요. 새 릴리스는 종종 경고 처리 기능을 개선하고 더 풍부한 `WarningInfo` 세부 정보를 추가합니다.

---

## Step 2: Word 문서를 로드하고 경고 콜백 등록하기

라이브러리가 클래스패스에 추가되었으니 엔진이 교체하는 **글꼴을 캡처하는 방법**을 적용할 수 있습니다. 핵심은 `Document.setWarningCallback`이며, 이는 `IWarningCallback` 구현을 받아들입니다. 아래는 콘솔에 모든 글꼴 대체 경고를 출력하는 간결하면서도 완전한 예제입니다.

```java
public class FontWarningDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document (replace with your actual path)
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Register the warning callback – this is where we **handle warnings**
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                // Filter only font‑substitution warnings
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 3️⃣ **Print font messages** – you could also log to a file or monitoring system
                    System.out.println("Font substitution detected: " + warningInfo.getDescription());
                }
                // Optional: handle other warning types here
            }
        });

        // Trigger the warning processing by saving or converting the document
        // For demonstration, we’ll just save to PDF (you could save to any format)
        document.save("output.pdf");
    }
}
```

### 왜 이렇게 동작하나요

- **`Document.setWarningCallback`** 은 Aspose.Words에게 경고가 필요한 상황이 발생할 때마다 사용자의 코드를 호출하도록 지시합니다.
- **`WarningInfo.getWarningType()`** 은 `FONT_SUBSTITUTION`, `DEPRECATED_FEATURE` 등 다양한 카테고리를 구분할 수 있게 해줍니다. `FONT_SUBSTITUTION`에 집중함으로써 로그를 어지럽히지 않고 **누락된 글꼴을 처리**합니다.
- `System.out.println` 구문은 **글꼴 메시지를** 실시간으로 출력하여 개발 중이나 프로덕션 파이프라인 문제 해결 시 매우 유용합니다.

---

## Step 3: 누락된 글꼴로 콜백 테스트하기

콜백이 실제로 **글꼴을 캡처**하는지 확인하려면, 머신에 설치되지 않은 글꼴을 사용하는 Word 파일을 만드세요—예를 들어, “DejaVu Sans”만 설치된 Linux 서버에서 “Comic Sans MS”를 사용하는 경우입니다. 데모를 실행하면 다음과 유사한 출력이 표시됩니다:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

메시지가 보이지 않으면 다음을 다시 확인하세요:

1. 문서가 실제로 누락된 글꼴을 참조하고 있는지.
2. `input.docx` 경로가 올바른지.
3. 최신 버전의 Aspose.Words를 사용하고 있는지(구버전은 일부 경고를 억제할 수 있음).

---

## Step 4: 고급 처리 – 대체 글꼴 삽입

경고를 출력하는 것만으로도 충분하지만, 프로덕션 시스템에서는 **누락된 글꼴을** 자동으로 **처리**하고 싶을 수 있습니다. 일반적인 방법은 저장하기 전에 대체 글꼴(예: “Liberation Sans”)을 삽입하는 것입니다. 아래는 콜백을 확장하여 누락된 글꼴을 프로그래밍 방식으로 교체하는 방법입니다:

```java
document.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo warningInfo) {
        if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String missingFont = warningInfo.getDescription()
                .replaceAll(".*'([^']+)'.*", "$1"); // extract the font name
            System.out.println("Missing font: " + missingFont);

            // Load a fallback font from resources or a known location
            FontSettings fontSettings = document.getFontSettings();
            fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
            }});
        }
    }
});
```

**무슨 일이 일어나고 있나요?**

- 경고 설명을 파싱하여 누락된 글꼴 이름을 추출합니다.
- `FontSettings`를 사용해 Aspose.Words에 해당 글꼴이 나타날 때마다 “Liberation Sans”로 대체하도록 지시합니다.
- 문서가 다음에 렌더링되거나 저장될 때 대체 글꼴이 조용히 적용됩니다.

> **주의:** 자동 대체를 과도하게 사용하면 실제 디자인 문제를 가릴 수 있습니다. 대체를 로그에 남기고(이미 **글꼴 메시지를 출력**하고 있으므로) QA 단계에서 수동으로 결과를 검토하는 것이 좋습니다.

---

## Step 5: 출력 대신 로깅 – 프로덕션 준비하기

CI/CD 파이프라인에서는 콘솔 출력이 필요 없을 수 있습니다. `System.out.println`을 적절한 로거(예: SLF4J)로 교체하세요. 아래는 간단한 예시입니다:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

// ...

private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

// Inside the callback:
logger.warn("Font substitution: {}", warningInfo.getDescription());
```

이제 경고가 기존 로그 집계 도구(ELK, Splunk 등)와 통합되어 다수의 작업에서 **누락된 글꼴을 처리**하기가 쉬워집니다.

---

## Step 6: 흔히 발생하는 문제와 회피 방법

| 문제점 | 발생 원인 | 해결책 |
|---------|----------------|-----|
| 경고가 나타나지 않음 | 글꼴이 시스템에 실제로 존재하거나 문서가 내장 글꼴을 사용함. | 테스트 문서가 실제로 사용 불가능한 글꼴을 참조하는지 확인하세요. |
| 콜백이 호출되지 않음 | `setWarningCallback`을 문서를 이미 로드한 **후**에 호출함. | 경고를 유발할 수 있는 작업(예: `Document.save` 이전) 전에 콜백을 **등록**하세요. |
| 다수의 경고가 로그를 채움 | 큰 문서가 많은 대체를 발생시킴. | 로깅 전에 제한 메커니즘을 추가하거나 메시지를 집계하세요. |
| 대체가 적용되지 않음 | `FontSettings`가 문서 인스턴스에 연결되지 않음. | 저장하는 동일한 `Document` 객체에 `FontSettings`를 설정했는지 확인하세요. |

---

## Step 7: 완전한 실행 예제

아래는 복사‑붙여넣기 가능한 완전한 프로그램입니다. import, 콜백, 로깅, 대체 글꼴 전략이 포함되어 있습니다.

```java
import com.aspose.words.*;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class FontWarningDemo {

    private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

    public static void main(String[] args) throws Exception {
        // Load the document – adjust the path as needed
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Register warning callback to capture and log font substitution warnings
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Extract missing font name (optional, for advanced handling)
                    String missingFont = warningInfo.getDescription()
                        .replaceAll(".*'([^']+)'.*", "$1");

                    // Log the warning – this **prints font messages** in your log files
                    logger.warn("Font substitution detected: {}", warningInfo.getDescription());

                    // OPTIONAL: automatically substitute with a known fallback
                    FontSettings fontSettings = document.getFontSettings();
                    fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                        getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
                    }});
                }
            }
        });

        // Save to PDF (or any other format). This triggers the warning processing.
        document.save("output.pdf");
        logger.info("Document conversion completed. Check logs for any font substitution warnings.");
    }
}
```

**예상 콘솔/로그 출력** (“Comic Sans MS”가 누락된 경우):

```
WARN  FontWarningDemo - Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
INFO  FontWarningDemo - Document conversion completed. Check logs for any font substitution warnings.
```

추가한 자동 대체 덕분에 결과 `output.pdf`는 “Comic Sans MS”가 참조된 모든 곳에서 “Liberation Sans”를 사용하게 됩니다.

---

## 결론

우리는 이제 Aspose.Words for Java에서 **경고를 처리하는 방법**을 처음부터 끝까지 다루었습니다. 경고 콜백을 등록하고, **글꼴 대체** 알림을 필터링하며, **글꼴 메시지를 출력**함으로써 누락된 글꼴 상황을 완전히 파악할 수 있습니다. `FontSettings`를 통해 대체 글꼴을 추가하면 **누락된 글꼴을** 수동 개입 없이 처리할 수 있으며, 적절한 로깅 프레임워크를 사용하면 솔루션을 프로덕션 수준으로 만들 수 있습니다.

다음 단계는 이 접근 방식을 Aspose.PDF와 결합하여 임베드된 글꼴이 변환 후에도 유지되는지 확인하거나, 다른 경고 유형(예: `DEPRECATED_FEATURE`)을 탐색하여 코드를 미래에 대비하는 것입니다. 그리고 원격 스토리지 버킷에서 **글꼴을 캡처하는 방법**이 궁금하다면

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 자료에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}