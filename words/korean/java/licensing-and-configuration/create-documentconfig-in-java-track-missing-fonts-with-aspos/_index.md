---
category: general
date: 2026-07-06
description: Aspose.Words를 사용하여 누락된 글꼴을 추적하기 위해 Java에서 DocumentConfig 만들기 – 개발자를 위한
  완전한 단계별 가이드.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: ko
og_description: Aspose.Words를 사용하여 누락된 글꼴을 추적하기 위해 Java에서 DocumentConfig를 생성합니다. 설정부터
  경고 처리까지 전체 워크플로우를 배워보세요.
og_title: Java에서 DocumentConfig 만들기 – 누락된 글꼴 추적
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Java에서 DocumentConfig 만들기 – Aspose.Words로 누락된 폰트 추적
url: /ko/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 DocumentConfig 만들기 – Aspose.Words로 누락된 폰트 추적

**Create DocumentConfig in Java**를 사용해 Word 문서를 로드할 때 발생하는 폰트 대체 경고를 모니터링합니다. DOCX를 열었을 때 일부 문자가 이상하게 보인 적이 있나요? 원본 폰트가 머신에 없어서 Aspose.Words가 조용히 대체했을 가능성이 높습니다. 이 튜토리얼에서는 **누락된 폰트를 추적**하는 방법을 정확히 보여드려서 다시는 뜻밖의 글리프에 놀라지 않도록 합니다.

Maven/Gradle 설정, `DocumentConfig`를 생성하는 코드, 폰트 대체 알림만 필터링하는 커스텀 `IWarningCallback`, 그리고 해당 메시지를 빠르게 로그에 남기는 방법을 모두 안내합니다. 최종적으로 콘솔(또는 파일)에서 모든 누락된 폰트 경고를 출력하는 실행 가능한 예제를 얻을 수 있습니다.

---

## 배울 내용

- `DocumentConfig`가 폰트 대체 이벤트를 가로채기에 적합한 이유.  
- **누락된 폰트를 추적**하면서 관련 없는 경고로 로그가 오염되는 것을 방지하는 방법.  
- 기술을 그대로 복사·붙여넣기 할 수 있는 완전한 Java 프로그램.  
- 솔루션 확장 팁 – 예: 경고를 데이터베이스에 저장하거나 이메일 알림 전송.

### 전제 조건

| Requirement | Reason |
|-------------|--------|
| Java 8 이상 | Aspose.Words for Java는 JDK 8+를 지원합니다. |
| Aspose.Words for Java 라이브러리 (최신 버전) | `DocumentConfig`, `IWarningCallback` 등을 제공합니다. |
| IDE 또는 빌드 도구 (IntelliJ, Eclipse, Maven/Gradle) | 샘플을 컴파일하고 실행하기 위해 필요합니다. |
| 설치되지 않은 폰트를 참조하는 DOCX 파일 | 경고가 실제로 발생하는지 확인하기 위해 필요합니다. |

이미 프로젝트가 있다면 Aspose 의존성을 추가하고 바로 시작하면 됩니다.

---

## Step 1: Add Aspose.Words to Your Build

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Pro tip:** 무료 체험 버전은 테스트에 충분히 작동하지만, 프로덕션에서는 평가용 워터마크를 제거하기 위해 라이선스를 적용해야 합니다.

---

## Step 2: Create DocumentConfig and Register a Warning Callback

솔루션의 핵심은 다음 스니펫에 있습니다. **DocumentConfig**를 생성하고 커스텀 `IWarningCallback`을 연결한 뒤 **누락된 폰트**만 추적하도록 설정합니다.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**작동 원리:** Aspose.Words가 문서를 파싱할 때, 모든 비정상 상황에 대해 `WarningInfo` 객체를 발생시킵니다. 콜백을 제공하면 이러한 경고가 사라지기 전에 가로챌 수 있습니다. `if` 조건을 통해 **누락된 폰트** 경고만 추적하고, 사용되지 않는 태그나 지원되지 않는 기능 같은 다른 경고는 무시합니다.

---

## Step 3: Run the Example and Observe the Output

누락된 폰트를 참조하는 DOCX(예: Linux 환경에서 “Comic Sans MS”)를 배치하고 프로그램을 실행합니다:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

다음과 비슷한 출력이 나타납니다:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

각 라인은 Aspose가 자동으로 교체한 누락된 폰트 하나에 해당합니다. 누락된 폰트가 없으면 프로그램은 조용히 동작합니다 – 깨끗한 로그를 원하는 경우 이상적입니다.

---

## Step 4: Persist the Missing‑Font List (Optional)

콘솔 출력은 데모에 편리하지만, 실제 서비스에서는 데이터를 저장하는 것이 일반적입니다. 경고를 텍스트 파일에 기록하는 간단한 방법을 소개합니다.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

이제 모든 누락된 폰트 이벤트가 `missing-fonts.log`에 한 줄씩 추가됩니다. 이후 파일을 파싱해 모니터링 대시보드에 연결하거나, 중요한 폰트가 서버에서 사라졌을 때 알림을 트리거할 수도 있습니다.

---

## Step 5: Common Pitfalls and How to Avoid Them

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| No warnings appear even though the DOCX uses unknown fonts | Callback not registered or `setWarningCallback` called after loading the document | Ensure `config.setWarningCallback(...)` is executed **before** creating the `Document` instance. |
| Application crashes with `NullPointerException` | `info.getDescription()` returns `null` for some rare warning types | Guard against null: `String desc = info.getDescription(); if (desc != null) …` |
| Too many unrelated warnings flood the console | Callback filters only `FONT_SUBSTITUTION`? | Double‑check the `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)` condition. |
| Performance slowdown on large batches | Writing to file synchronously for each warning | Batch writes or use a `BufferedWriter` to reduce I/O overhead. |

---

## Step 6: Extending the Solution – From Console to Enterprise

- **Database logging:** `FileWriter`를 JDBC 삽입으로 교체하고 `documentName`, `missingFont`, `timestamp`를 저장합니다.  
- **Email alerts:** JavaMail과 연동해 문서 배치 처리 후 요약을 전송합니다.  
- **Custom substitution logic:** Aspose가 자동으로 폰트를 선택하도록 두는 대신 `FontSettings.setFontsFolder()`로 로컬 폰트 컬렉션을 로드하고, 대체가 발생하면 다시 로드하도록 구현합니다.

이러한 확장은 핵심 아이디어—**DocumentConfig 생성** 및 **누락된 폰트 추적**—를 유지하면서 프로덕션 요구에 맞게 확장할 수 있게 해줍니다.

---

## Conclusion

이제 **Java에서 DocumentConfig를 생성하고 Aspose.Words로 누락된 폰트를 추적**하는 완전한 복사·붙여넣기 가능한 패턴을 확보했습니다. 이 접근 방식은 가볍고 몇 줄의 코드만 필요하며, 폰트 대체 경고를 처리하는 방식을 완전히 제어할 수 있습니다. 문서 변환 서비스, 자동 보고서 생성기, 혹은 규정 준수 감사 도구를 구축하든, 어떤 폰트가 누락됐는지 정확히 아는 것은 디버깅 시간을 크게 절감합니다.

다음 단계는? 콘솔 출력을 구조화된 JSON 로그로 바꾸거나, 실시간 업로드를 처리하는 Spring Boot 마이크로서비스에 콜백을 통합해 보세요. 그리고 맞닥뜨린 특수 케이스—예를 들어 Aspose가 파싱하지 못하는 커스텀 OpenType 폰트—가 있다면 아래에 댓글을 남겨 주세요. 함께 해결해 보겠습니다.

Happy coding, and may your PDFs always render with the fonts you expect!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하여 관련 주제를 심도 있게 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하므로, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for Java에서 폰트 사용하기](/words/english/java/using-document-elements/using-fonts/)
- [Aspose.Words Java에서 테마 색상 및 폰트 사용자 지정: 종합 가이드](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Aspose.Words for Java로 PDF 문서 만들기 | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}