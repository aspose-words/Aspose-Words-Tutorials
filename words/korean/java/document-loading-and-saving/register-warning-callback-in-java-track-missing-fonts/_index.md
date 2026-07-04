---
category: general
date: 2026-05-30
description: Java에서 경고 콜백을 등록하여 누락된 글꼴을 추적하고 Aspose.Words로 문서 로드를 사용자 지정합니다. 전체 단계별
  솔루션을 확인하세요.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: ko
og_description: Java에서 경고 콜백을 등록하여 누락된 폰트를 추적하고 문서 로드를 맞춤 설정합니다. 코드와 설명이 포함된 완전 가이드.
og_title: Java에서 경고 콜백을 등록 – 누락된 폰트 추적
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Java에서 경고 콜백 등록 – 누락된 글꼴 추적
url: /ko/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 경고 콜백 등록 – 누락된 폰트 추적

Aspose.Words for Java로 Word 문서를 로드할 때 **누락된 폰트를 추적**하는 방법이 궁금하셨나요? 조용히 폰트가 대체되는 것을 보고 “레이아웃이 어떻게 변했지?”라고 생각한 적이 있을 겁니다. 좋은 소식은 추측할 필요가 없다는 것입니다. **경고 콜백을 등록**하면 문서를 읽는 순간마다 모든 폰트 대체 이벤트를 포착할 수 있으며, **문서 로딩을 맞춤화**하여 파이프라인에 맞출 수도 있습니다.

이 튜토리얼에서는 콜백을 설정하는 정확한 방법, 왜 중요한지, 그리고 나머지 처리 파이프라인을 깔끔하게 유지하는 방법을 실제 예제로 단계별로 살펴봅니다. 마지막까지 진행하면 누락된 폰트 경고를 모두 출력하고 문서의 처리된 복사본을 저장하는 실행 가능한 Java 클래스를 얻게 됩니다. 외부 참조는 필요 없으며, 순수하게 실행 가능한 코드만 제공됩니다.

> **얻을 수 있는 것:**  
> • Aspose.Words를 사용한 완전한 Java 프로그램  
> • 각 라인에 대한 단계별 설명  
> • 암호화된 파일이나 대용량 배치와 같은 엣지 케이스 처리 팁  
> • `.docx` 파일이면 언제든 실행할 수 있는 빠른 검증

## 사전 요구 사항

- **Java 17**(또는 최신 JDK) 설치 및 `JAVA_HOME` 설정  
- **Aspose.Words for Java** JAR를 클래스패스에 추가. 최신 버전은 Maven Central 저장소에서 받을 수 있습니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- 머신에 설치되지 않은 폰트가 포함되어 있을 것으로 의심되는 샘플 Word 문서(`input.docx`)  
- 익숙한 IDE 또는 명령줄 빌드 도구(Maven/Gradle)

그게 전부입니다. 추가 폰트나 서비스 없이 순수 Java와 Aspose.Words만 있으면 됩니다.

## 왜 경고 콜백을 등록해야 할까요?

**경고 콜백**을 문서 로딩 과정의 보안 카메라라고 생각하면 됩니다. Aspose.Words가 누락된 글리프를 만나면 예외를 발생시키지 않고 조용히 대체 폰트로 교체합니다. 이러한 조용한 대체는 레이아웃을 깨뜨릴 수 있으며, 특히 브랜드가 중요한 PDF나 청구서에서 문제가 됩니다. 콜백을 등록하면 다음을 할 수 있습니다:

1. **실시간 인사이트 확보** – 모든 `FONT_SUBSTITUTION` 경고가 즉시 전달됩니다.  
2. **로그 또는 반응** – 파일에 로그를 남기거나 알림을 발생시키거나, 프로그래밍적으로 폰트를 교체할 수 있습니다.  
3. **깨끗한 출력 유지** – 누락된 폰트를 알면 출판 전에 원본 문서를 수정할 수 있습니다.

요컨대, 콜백은 숨겨진 문제를 가시화하여 문서 파이프라인을 훨씬 더 신뢰할 수 있게 만들어 줍니다.

## Step 1 – `LoadOptions` 생성하여 문서 로딩 맞춤화

먼저 `LoadOptions`를 인스턴스화합니다. 이 객체는 비밀번호 처리부터 **경고 콜백 등록** 기능까지 로딩 시 필요한 모든 조정을 할 수 있는 관문 역할을 합니다.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

왜 그냥 `new Document("file.docx")`를 호출하지 않을까요? `LoadOptions` 없이 로딩 이벤트에 연결할 기회를 잃게 됩니다. `LoadOptions`는 Aspose.Words가 **문서 로딩을 맞춤화**할 수 있도록 허용하는 유일한 장소입니다.

## Step 2 – 누락된 폰트를 추적하기 위해 경고 콜백 등록

이제 쇼의 스타가 등장합니다: `IWarningCallback`을 구현한 **경고 콜백을 등록**합니다. `warning` 메서드 안에서 `WarningType.FONT_SUBSTITUTION`을 필터링하고 유용한 메시지를 출력합니다.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

주의할 점 몇 가지:

- **왜 `IWarningCallback`인가?** 모든 경고 유형에 대해 Aspose.Words가 사용하는 인터페이스이며, 다양한 문제에 대한 단일 진입점을 제공합니다.  
- **필터링은 필수** – `if` 검사를 빼면 누락된 이미지, 사용 중단된 기능 등 다른 경고까지 모두 표시되어 로그가 어수선해집니다.  
- **스레드 안전** – 콜백은 문서를 로드하는 동일한 스레드에서 실행되므로, 나중에 결과를 집계해야 할 경우 공유 구조를 안전하게 업데이트할 수 있습니다.

이 스니펫은 **경고 콜백을 등록**하며, 이제부터 모든 누락된 폰트 이벤트가 `stdout`에 출력됩니다. 이것이 **누락된 폰트 추적**의 핵심입니다.

## Step 3 – 구성된 `LoadOptions`로 문서 로드

콜백을 설정했으니 이제 파일을 로드합니다. 문서가 존재하지 않는 폰트를 참조하면, 문서 객체가 완전히 구성되기 전에 콜백이 실행됩니다.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

`YOUR_DIRECTORY`를 실제 머신 경로로 바꾸세요. `Document` 생성자는 파일을 읽고, `loadOptions`에 비밀번호가 설정돼 있다면 적용하며, 누락된 폰트마다 경고 콜백을 트리거합니다. 다음과 같은 출력이 나타납니다:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

이 라인은 **누락된 폰트 추적**에 성공했음을 증명합니다.

## Step 4 – 문서 추가 처리 (선택 사항)

이 단계에서는 문서를 자유롭게 조작할 수 있습니다—텍스트 교체, 이미지 삽입, 혹은 대체된 폰트를 프로그래밍적으로 교체하는 등. 콜백이 이미 문제 폰트 목록을 제공했으므로, 예를 들어 대체 폰트를 임베드할 수 있습니다:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

**누락된 폰트만 추적**하면 이 블록을 건너뛰어도 됩니다. 핵심은 이제 정보를 가지고 있어 합리적인 결정을 내릴 수 있다는 점입니다.

## Step 5 – 처리된 문서 저장

마지막으로 문서를 영구 저장합니다. 원본을 덮어쓰거나 새 위치에 저장하거나 PDF로 내보낼 수 있으며, 앞서 캡처한 경고 데이터는 그대로 유지됩니다.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

전체 클래스를 실행하면 모든 누락된 폰트에 대한 콘솔 출력과 동일 폴더에 `processed.docx`라는 새 파일이 생성됩니다.

## 완전한 작업 예제

아래는 IDE에 복사‑붙여넣기 할 수 있는 전체 Java 클래스입니다. 앞서 논의한 모든 내용과 작은 `main` 메서드 래퍼가 포함되어 있습니다.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### 예상 출력

시스템에 설치되지 않은 폰트를 사용하는 문서에 대해 프로그램을 실행하면 다음과 같은 출력이 나타납니다:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

문서에 **누락된 폰트가 전혀 없**다면, 콘솔은 최종 “Document saved successfully.” 라인까지 조용히 유지됩니다—이는 잘 동작하는 **경고 콜백 등록** 구현에서 기대할 수 있는 정확한 동작입니다.

## Pro Tips & Common Pitfalls

- **여러 콜백?** Aspose.Words는 경고 핸들러를 하나만 허용합니다. 파일과 콘솔 모두에 로그를 남겨야 한다면, 경고를 여러 대상에 전달하는 복합 콜백을 구현하세요.  
- **대용량 배치** – 수백 개 파일을 처리할 때는 `LoadOptions` 인스턴스를 재사용하는 것이 좋습니다. 파일당 새로 생성하면 불필요한 오버헤드가 발생합니다.  
- **암호화된 문서** – 로드하기 전에 `LoadOptions`에 비밀번호를 설정하지 않으면, 콜백이 실행되기 전에 `IncorrectPasswordException`이 발생합니다.  
- **성능** – 콜백은 동기식으로 실행됩니다. 원격 서비스에 로그를 남겨야 한다면, 메시지를 버퍼링하고 로드가 끝난 뒤 플러시하여 I/O 병목을 피하세요.  
- **폰트 폴백** – 시스템 폰트에 앞서 고려하도록 자체 `FontSource` 컬렉션을 제공할 수도 있습니다.

## 결론

이제 Java에서 **경고 콜백을 등록**하고, **누락된 폰트를 효과적으로 추적**하며, Aspose.Words로 **문서 로딩을 맞춤화**하는 방법을 배웠습니다. 솔루션은 단일 `main` 메서드로 실행 가능한 독립형이며, 눈에 띄지 않던 폰트 대체를 즉시 확인할 수 있게 해 줍니다.

다음 단계는 무엇일까요? 콜백을 확장해 경고를 CSV 파일에 기록하거나, 누락된 폰트를 자동으로 임베드하는 배치 프로세서와 결합해 보세요. `IMAGE_SUBSTITUTION`이나 `DEPRECATED_FEATURE`와 같은 다른 경고 유형도 동일한 패턴으로 탐색할 수 있습니다.

행복한 코딩 되시고, 문서가 언제나 의도한 대로 정확히 렌더링되길 바랍니다!

![경고 콜백 등록 다이어그램](register-warning-callback.png "경고 콜백 등록 흐름")

## 다음에 배울 내용

- [Word 문서에서 경고 콜백](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose.Words Java에서 테마 색상 및 폰트 맞춤화: 종합 가이드](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Aspose.Words Java를 사용한 Word 문서 변경 추적: 문서 개정에 대한 완전 가이드](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}