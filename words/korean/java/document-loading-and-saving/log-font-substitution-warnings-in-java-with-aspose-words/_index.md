---
category: general
date: 2026-06-17
description: Aspose.Words를 사용하여 Java에서 글꼴 대체 경고를 기록하고, 문서 로드 중에 누락된 글꼴을 포착하여 출력 결과를
  일관되게 유지하세요.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: ko
og_description: Aspose.Words를 사용하여 Java에서 글꼴 대체 경고를 기록하십시오. 문서 로드 중에 누락된 글꼴 알림을 캡처하고
  PDF를 완벽하게 유지하는 방법을 알아보세요.
og_title: Java에서 글꼴 대체 경고 로그 기록 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Aspose.Words와 Java에서 글꼴 대체 경고 로그
url: /ko/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 글꼴 대체 경고 로그 기록 – 완전 가이드

서버에 설치되지 않은 글꼴을 Word 문서가 가져올 때 **글꼴 대체 경고를 로그**하는 방법이 궁금하셨나요? 조용히 교체되는 누락된 글꼴 때문에 머리를 싸매는 분은 당신뿐만이 아닙니다. 좋은 소식은? Aspose.Words for Java를 사용하면 문서가 로드되는 순간 바로 그 대체를 포착할 수 있는 깔끔한 방법을 제공합니다.

이 튜토리얼에서는 경고 콜백을 등록하고, 글꼴 대체 알림만 필터링하며, 이를 콘솔(또는 원하는 로거)으로 출력하는 실습 예제를 단계별로 살펴봅니다. 마지막까지 따라오시면 **Aspose.Words Java**를 사용하는 모든 Java 프로젝트에 바로 삽입할 수 있는 재사용 가능한 스니펫을 얻게 됩니다.

## 배울 내용

- **LoadOptions**를 구성하여 경고를 캡처하는 방법
- **글꼴 대체** 이벤트에만 반응하는 **IWarningCallback** 구현 방법
- 누락된 글꼴에 대한 명확한 감사 로그를 남기면서 문서를 안전하게 로드하는 방법
- 파일 기반 로그 또는 모니터링 시스템으로 확장하는 팁

### 사전 요구 사항

- Java 8 이상 (코드는 Java 11+에서도 동작합니다)
- Aspose.Words for Java 라이브러리 (버전 23.10 이상 권장)
- 머신에 설치되지 않은 글꼴을 참조하는 샘플 `.docx` 파일 (예: `MissingFont.docx`)

추가 프레임워크는 필요 없습니다—순수 Java와 Aspose.JAR만 있으면 됩니다.

---

## 1단계: Aspose.Words Java용 LoadOptions 구성

경고를 가로채기 전에 **LoadOptions** 인스턴스가 필요합니다. 이 객체는 Aspose.Words가 파일을 파싱하는 동안 어떻게 동작할지를 지정합니다.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

왜 이 단계가 중요한가요? `LoadOptions` 객체가 없으면 라이브러리는 누락된 글꼴을 조용히 대체하고, 여러분은 그 흔적을 전혀 보지 못합니다. 명시적으로 객체를 생성함으로써, 관심 있는 내용만 정확히 로그할 수 있는 **경고 콜백**을 연결할 수 있게 됩니다.

> **프로 팁:** 배치로 많은 문서를 로드한다면, 불필요한 객체 생성을 피하기 위해 단일 `LoadOptions` 인스턴스를 재사용하세요.

---

## 2단계: 글꼴 대체용 경고 콜백 구현

Aspose.Words는 `IWarningCallback` 인터페이스를 제공합니다. 이를 구현하면 엔진이 `WarningInfo`를 발생시킬 때 수행할 작업을 직접 정의할 수 있습니다. 여기서는 `WarningType.FONT_SUBSTITUTION`에만 반응하도록 합니다.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

주의할 점 몇 가지:

1. **필터링** – `if` 문을 통해 레이아웃 문제와 같은 무관한 경고는 무시하고, 로그를 깔끔하게 유지합니다.  
2. **스레드 안전성** – 콜백은 문서를 로드하는 동일한 스레드에서 실행되므로, 간단한 콘솔 출력에는 별도 동기화가 필요 없습니다. 공유 로거에 기록한다면 스레드‑안전한지 확인하세요.  
3. **확장성** – 파일에 기록하고 싶나요? `System.out.println`을 `java.util.logging.Logger` 혹은 서드파티 로깅 프레임워크로 교체하면 됩니다.

---

## 3단계: 구성한 옵션으로 문서 로드

이제 콜백이 준비됐으니 Word 파일을 로드합니다. Aspose.Words가 문서를 파싱하는 순간, 누락된 글꼴이 있으면 위에서 정의한 콜백이 호출됩니다.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

소스 파일이 설치되지 않은 글꼴을 참조하고 있다면, 다음과 유사한 출력이 표시됩니다:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

이 라인이 바로 여러분이 찾던 **글꼴 대체 경고 로그**입니다. 이제 이를 활용해 사용자에게 알리거나, 대체 스타일시트를 적용하거나, 규정 준수를 위해 기록을 남길 수 있습니다.

---

## 4단계: 정상적인 처리 계속 진행

로드가 끝난 뒤, 문서는 일반 `Document` 객체와 동일하게 동작합니다. 섹션을 검사하거나 텍스트를 추출하거나 PDF로 변환하는 등 자유롭게 작업하세요. 경고 로그는 로드 단계에서 자동으로 발생하므로 추가 코드는 필요 없습니다.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

콘솔에는 글꼴 대체 경고(존재한다면)와 섹션 수가 모두 표시되어, 문서가 정상적으로 작동함을 확인할 수 있습니다.

---

## 고급 팁 & 엣지 케이스

### 콘솔 대신 파일에 로그 기록

지속적인 로그가 필요하다면 `System.out.println` 호출을 `FileWriter`로 교체합니다:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

운영 코드에서는 `IOException`을 적절히 처리하는 것을 잊지 마세요.

### 루프에서 여러 문서 처리

폴더에 있는 문서를 일괄 처리할 때는 동일한 콜백을 재사용할 수 있습니다:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

콜백이 `loadOptions`에 연결돼 있기 때문에, 각 반복마다 글꼴 대체 이벤트가 자동으로 로그됩니다.

### 임베디드 글꼴 처리

Aspose.Words는 옵션을 켜면 누락된 글꼴을 임베드할 수 있습니다:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

임베드가 활성화돼도 경고 콜백은 계속 호출되어, 어떤 글꼴이 대체되었는지 가시성을 제공합니다.

---

## 전체 작동 예제

아래는 완전한 실행 가능한 프로그램입니다. `FontSubstitutionDiagnostics.java`라는 클래스에 복사하고, 파일 경로만 수정한 뒤 실행하세요.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**예상 출력** (소스 문서가 누락된 글꼴을 참조하는 경우):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

콘솔과 `font_substitution_log.txt` 모두에 경고가 기록되어, 신뢰할 수 있는 감사 로그를 제공합니다.

---

## 결론

우리는 Aspose.Words를 활용해 Java에서 **글꼴 대체 경고를 로그**하는 방법을 살펴보았습니다. `LoadOptions`를 설정하고, `IWarningCallback`을 연결한 뒤 문서를 로드하면, 눈에 띄지 않을 수 있는 누락된 글꼴 이벤트를 완전히 파악할 수 있습니다. 이제 다음과 같은 작업을 진행할 수 있습니다:

- 경고를 중앙 로깅 서비스로 라우팅
- 품질 관리 파이프라인을 위한 알림 트리거
- PDF 변환이나 메일 머지와 같은 다른 **문서 로딩** 전략과 결합

콘솔 로거를 SLF4J로 교체하거나, 타임스탬프를 추가하거나, 모니터링 대시보드로 푸시하는 등 자유롭게 실험해 보세요. 핵심 패턴은 동일하며, 이제 Java 기반 문서 워크플로우에서 견고한 글꼴 처리를 위한 탄탄한 기반을 갖추게 되었습니다.

특별히 적용한 사례가 있나요? Spring Boot나 클라우드 함수와 통합한 경험을 공유하고 싶다면 아래에 댓글을 남겨 주세요. 함께 이야기를 나눠요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하여, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 도와줍니다.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}