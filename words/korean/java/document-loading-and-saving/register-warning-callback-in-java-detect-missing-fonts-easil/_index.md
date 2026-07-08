---
category: general
date: 2026-07-03
description: Java에서 경고 콜백을 등록하여 Word 문서를 처리할 때 누락된 글꼴을 감지합니다. Aspose.Words 경고 처리 및
  글꼴 대체 감지를 배워보세요.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: ko
og_description: Java에서 경고 콜백을 등록하여 누락된 글꼴을 감지합니다. 이 가이드는 Aspose.Words를 사용해 글꼴 대체 경고를
  캡처하는 방법을 보여줍니다.
og_title: Java에서 경고 콜백 등록 – 누락된 폰트 감지
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Java에서 경고 콜백 등록 – 누락된 폰트를 쉽게 감지
url: /ko/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 경고 콜백 등록 – 누락된 글꼴을 쉽게 감지하기

워드 문서를 변환하거나 편집할 때 **경고 콜백을 등록**하여 **누락된 글꼴을 감지**하는 방법이 궁금하셨나요? 여러분만 그런 것이 아닙니다. 누락된 글꼴은 레이아웃을 조용히 손상시키고, 깔끔한 보고서를 뒤죽박죽으로 만들며, 대부분의 개발자는 최종 PDF가 이상하게 보일 때까지 이를 인식하지 못합니다.  

이 튜토리얼에서는 Aspose.Words for Java의 경고 시스템에 어떻게 연결하고, 성가신 글꼴 대체 알림을 포착하며, 이를 로그에 남기거나 필요에 따라 처리하는지 보여주는 완전한 실행 예제를 단계별로 살펴봅니다. “문서를 참고하세요” 같은 애매한 설명은 없습니다—그냥 복사‑붙여넣기 가능한 코드와 각 라인의 이유만을 제공합니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있어야 합니다:

* **Java 17**(또는 최신 JDK) 설치 및 `JAVA_HOME` 설정  
* **Aspose.Words for Java** JAR(공식 사이트에서 다운로드하거나 Maven으로 가져오기)  
* 머신에 설치되지 않은 글꼴을 참조하는 샘플 `.docx` 파일—이 파일이 경고를 트리거합니다  
* 좋아하는 IDE 또는 간단한 텍스트 편집기와 명령줄 빌드 도구

그게 전부입니다. 추가 프레임워크나 외부 서비스는 필요 없습니다. 준비되셨나요? 시작해 보겠습니다.

## 1단계: 프로젝트 설정 및 Aspose.Words 추가

Maven을 사용한다면 `pom.xml`에 다음 의존성을 추가하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Gradle을 사용한다면 `build.gradle`에 다음을 넣으세요:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

수동으로 진행하고 싶다면 `aspose-words-24.10.jar`를 클래스패스에 배치하면 됩니다.  
**팁:** JAR를 `src` 폴더 옆에 두면 나중에 `javac` 명령을 간단히 할 수 있습니다.

## 2단계: 누락된 글꼴이 있을 수 있는 문서 로드

먼저 `Document` 객체를 생성해 소스 파일을 가리키게 합니다. 이 단계는 간단하지만, 라이브러리가 파일을 스캔하고 *잠재적으로* 누락된 글꼴을 발견하는 시점이기도 합니다.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

여기서 `Document`는 Aspose.Words 모든 작업의 진입점입니다. 생성자가 실행될 때 라이브러리는 문서 XML을 파싱하고 글꼴을 해석하며, 사용 불가능한 글꼴이 있으면 나중에 포착할 수 있는 경고를 *큐*에 넣습니다.

## 3단계: 글꼴 대체 알림을 포착하기 위한 경고 콜백 등록

이제 쇼의 주인공인 **경고 콜백 등록**을 합니다. Aspose.Words는 `IWarningCallback` 인터페이스 구현을 연결할 수 있게 해줍니다. 엔진이 플래그를 달아야 할 상황(예: 누락된 글꼴)을 만나면 `warning` 메서드가 호출됩니다.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### 왜 중요한가

* **가시성:** 콜백이 없으면 대체가 조용히 이루어지고, 잘못된 모습의 문서를 배포할 수 있습니다.  
* **자동화:** 배치 파이프라인에서 모든 누락된 글꼴 사건을 로그에 남기고, 이후 글꼴 설치 스크립트에 전달할 수 있습니다.  
* **규정 준수:** 일부 산업(예: 법률)에서는 원본 글꼴이 사용되었거나 적절히 대체되었다는 증거가 필요합니다.

우리는 `WarningType.FONT_SUBSTITUTION`에만 필터링합니다. Aspose.Words는 레이아웃 오버플로, 사용 중단 기능 등 다양한 경고 타입을 내보내지만, 여기서는 글꼴이 누락되었음을 알려주는 것만 필요합니다. 이렇게 하면 콘솔이 깔끔해지고 **누락된 글꼴 감지** 목표에 집중할 수 있습니다.

## 4단계: 문서 저장 및 콜백 실행

마지막으로 `save`를 호출하면 엔진이 지연 로딩을 마무리하고 저장 과정에서 발견한 각 누락된 글꼴에 대해 경고 콜백을 트리거합니다.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### 예상 콘솔 출력

`input.docx`가 설치되지 않은 글꼴 *“Comic Sans MS”*를 참조하고 있다고 가정하면 다음과 같은 출력이 나타납니다:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

소스 문서에 설치된 글꼴만 포함되어 있다면 경고 라인은 전혀 나타나지 않으며, 이는 **누락된 글꼴 감지**가 조용히 성공했음을 의미합니다.

![Console output showing register warning callback in action and detect missing fonts](register-warning-callback-output.png)

*이미지 대체 텍스트: 경고 콜백이 작동하고 누락된 글꼴을 감지하는 콘솔 출력*

## 5단계: 엣지 케이스 처리 및 모범 사례 팁

### 여러 개의 누락된 글꼴

문서가 여러 개의 사용 불가능한 글꼴을 참조하면 콜백이 글꼴당 한 번씩 호출됩니다. 나중에 요약 보고서가 필요하면 메시지를 리스트에 모을 수 있습니다.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### 대체 동작 제어

특정 폴백 글꼴을 강제로 사용하고 싶을 때는 문서를 로드하기 전에 `FontSettings`를 사용하세요:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

이 경우 콜백은 여전히 호출되지만, 어떤 글꼴이 사용될지 정확히 알 수 있습니다.

### 성능 고려 사항

경고 콜백을 등록하면 경고당 몇 나노초 정도의 미세한 오버헤드가 발생합니다. 수천 개 문서를 시간당 변환하는 고처리량 서비스에서는 영향이 무시할 수준이지만, 수백만 건을 처리한다면 글꼴 세트가 완전함을 확인한 뒤 경고를 비활성화하는 것을 고려하세요:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### 크로스‑플랫폼 참고 사항

콜백은 Windows, macOS, Linux에서 동일하게 작동합니다. 차이점은 각 OS에 설치된 글꼴 집합뿐입니다. 여러 에이전트에서 동일 작업을 실행한다면 서로 다른 대체 메시지가 나타날 수 있습니다. 결과를 결정론적으로 유지하려면 **맞춤 글꼴 폴더**를 배포하고 `FontSettings.setFontsFolder("path/to/fonts", true);` 로 Aspose.Words에 지정하세요.

## 전체 실행 가능한 예제

아래는 `src/main/java/FontWarningDemo.java`에 복사‑붙여넣기 할 수 있는 전체 Java 클래스입니다. 모든 import, 오류 처리, 주석이 포함되어 바로 실행할 수 있습니다.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

컴파일 및 실행:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

경고 라인(있는 경우)과 성공 메시지가 표시됩니다.

## 결론

이제 **Java에서 경고 콜백을 등록**하여 Aspose.Words 사용 시 **누락된 글꼴을 감지**하는 방법을 배웠습니다. 라이브러리의 경고 시스템에 연결하면 글꼴 대체 이벤트를 완전히 가시화하고, 규정 준수를 위해 로그를 남기며, 필요 시 프로그래밍적으로 글꼴을 교체할 수도 있습니다.  

다음 단계로는:

* **누락된 글꼴**을 배치 파일에 대해 루프나 병렬 스트림으로 감지하기  
* 콜백을 로깅 프레임워크(SLF4J, Log4j)와 통합하여 프로덕션 수준 보고서 만들기  
* `FontSettings`를 사용해 기업 글꼴 팔레트를 강제하고 원치 않는 폴백을 방지하기

실제로 해보세요—입력 문서를 교체하고, 다양한 누락 글꼴 시나리오를 시험해 보며 콜백 동작을 확인해 보세요. 궁금한 점이 있으면 아래에 댓글을 남겨 주세요. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?


다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 관련된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Custom Savings](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}