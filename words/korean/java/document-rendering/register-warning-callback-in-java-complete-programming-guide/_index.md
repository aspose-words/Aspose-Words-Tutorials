---
category: general
date: 2026-05-23
description: Java에서 경고 콜백을 등록하여 누락된 폰트를 감지하고 폰트 대체를 처리합니다. 전체 예제를 통해 단계별로 배워보세요.
draft: false
keywords:
- register warning callback
- detect missing fonts
- Java font handling
- Aspose.Words warning callback
- font substitution detection
language: ko
og_description: Java에서 누락된 폰트를 감지하기 위해 경고 콜백을 등록합니다. 이 튜토리얼은 코드, 설명 및 모범 사례를 포함한 완전한
  솔루션을 보여줍니다.
og_title: Java에서 경고 콜백 등록 – 전체 가이드
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Register warning callback in Java to detect missing fonts and handle
    font substitutions. Learn step‑by‑step with a full example.
  headline: Register Warning Callback in Java – Complete Programming Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- FontSettings
- DocumentProcessing
title: Java에서 경고 콜백 등록 – 완전 프로그래밍 가이드
url: /ko/java/document-rendering/register-warning-callback-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 경고 콜백 등록 – 완전 프로그래밍 가이드

문서가 사용자 정의 글꼴에 의존할 때, 조용히 글꼴이 대체되어 레이아웃이 깨지는 경우가 있습니다. 이러한 문제를 감지하려면 경고를 수신해야 합니다. 이 가이드에서는 **경고 콜백을 등록**하고 **누락된 글꼴을 감지**하는 실용적인 솔루션을 단계별로 살펴봅니다.

Aspose.Words for Java는 글꼴 관리를 위한 깔끔한 API를 제공하지만, 많은 개발자가 경고 콜백 단계를 건너뛰어 원본 Word 파일과 전혀 다른 PDF를 만들곤 합니다. 이 튜토리얼을 마치면 바로 실행 가능한 코드 스니펫을 얻고, 각 라인의 의미를 이해하며, 더 복잡한 시나리오에 적용하는 방법을 알게 됩니다.

## 배울 내용

다음 섹션에서는 다음을 다룹니다:

* `LoadOptions`를 생성하고 사용자 정의 글꼴 처리를 활성화하는 방법.  
* `FONT_SUBSTITUTION` 이벤트를 포착하기 위해 **경고 콜백을 등록**하는 방법.  
* **누락된 글꼴을 감지**하고 디버깅에 유용한 정보를 로그에 남기는 방법.  
* 오늘 바로 IDE에 붙여넣을 수 있는 완전한 실행 가능한 Java 예제.

Aspose.Words 외에 추가 라이브러리는 필요 없으며, 코드는 Java 8+ 및 Aspose.Words 23.9(이후 버전)와 호환됩니다. 이미 `.docx` 파일을 로드하는 프로젝트가 있다면 몇 줄만 추가하면 됩니다—대규모 리팩터링은 필요 없습니다.

## 사전 요구 사항

* Java Development Kit (JDK) 8 이상.  
* Aspose.Words for Java(공식 사이트에서 다운로드하거나 Maven 의존성 추가).  
* 로드하려는 Word 문서가 들어 있는 디렉터리에 대한 접근 권한.  
* Java 람다 또는 익명 클래스에 대한 기본 지식(명확성을 위해 익명 클래스를 사용).

이 중 익숙하지 않은 부분이 있더라도 걱정 마세요—각 단계가 쉬운 영어로 설명되고, 코드 주석이 부족한 부분을 메워 줍니다.

---

## 1단계: Load Options 생성 및 사용자 정의 글꼴 처리 활성화

글꼴 관련 경고를 수신하려면 `FontSettings`를 사용하도록 Aspose.Words에 알려주는 `LoadOptions` 인스턴스가 필요합니다. `LoadOptions`는 문서 로더에 전달하는 “설정 가방”이라고 생각하면 됩니다.

```java
// Step 1: Create load options and enable custom font handling
LoadOptions loadOptions = new LoadOptions();               // Holds loading configuration
loadOptions.setFontSettings(new FontSettings());           // Attach a fresh FontSettings object
```

**이것이 중요한 이유:**  
`FontSettings`는 라이브러리가 글꼴을 처리하는 모든 경로—검색 경로, 대체 규칙, 그리고 무엇보다도 경고 콜백—의 관문입니다. 전용 `FontSettings` 객체를 만들면 누락된 글꼴을 어떻게 처리할지 완전하게 제어할 수 있으며, 라이브러리 기본값에 의존하지 않게 됩니다.

> **프로 팁:** 애플리케이션에서 이미 공유 `FontSettings`(예: PDF 변환용)를 사용하고 있다면 여기에서도 재사용하여 파이프라인 전체에서 글꼴 해석을 일관되게 유지하세요.

---

## 2단계: 누락된 글꼴을 감지하기 위해 경고 콜백 등록

이제 튜토리얼의 핵심 단계입니다. 방금 만든 `FontSettings`에 **경고 콜백을 등록**합니다. 콜백은 문서 로드 중 발생하는 모든 경고에 대해 `WarningInfo` 객체를 전달받습니다.

```java
// Step 2: Register a warning callback to be notified of font substitutions
loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter only font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // This is where we **detect missing fonts**
            System.out.println("Substituted: " + info.getDescription());
        }
    }
});
```

**로직 설명:**

* `setWarningCallback`은 사용자 정의 리스너를 연결합니다.  
* `warning(WarningInfo info)` 내부에서 `info.getWarningType()`을 확인합니다.  
* 타입이 `WarningType.FONT_SUBSTITUTION`이면 라이브러리가 원본 글꼴을 찾지 못해 다른 글꼴로 대체했음을 의미합니다.  
* `info.getDescription()`에는 *“Font 'MyCustomFont' not found, substituted with 'Arial'.”* 와 같은 사람이 읽을 수 있는 메시지가 들어 있습니다.  

이 설명을 출력함으로써 **누락된 글꼴을 즉시 감지**하고, 로그를 남기거나 경고가 허용되지 않을 경우 작업을 중단할 수 있습니다.

> **예외를 잡지 않는 이유는?**  
> 누락된 글꼴은 보통 예외를 발생시키지 않고 경고를 발생시킵니다. 콜백이 없으면 그 경고는 사라지고, 문서의 시각적 완전성이 손상된 사실을 알 수 없습니다.

### 선택 사항: 람다 사용(Java 8+)

더 간결한 구문을 원한다면 동일한 콜백을 람다식으로 표현할 수 있습니다:

```java
loadOptions.getFontSettings().setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        System.out.println("Substituted: " + info.getDescription());
    }
});
```

두 방법 모두 동일한 목표를 달성합니다—코드베이스에 맞는 스타일을 선택하세요.

---

## 3단계: 구성된 옵션으로 문서 로드

콜백을 설정했으니 마지막 단계는 문서를 로드하는 것입니다. `Document` 생성자는 파일 경로와 앞서 만든 `LoadOptions`를 인수로 받습니다.

```java
// Step 3: Load the document using the configured options
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**내부에서 무슨 일이 일어나나요?**  
이 호출 동안 Aspose.Words는 `.docx` 파일을 파싱하고, 각 글꼴을 해석하며, 누락된 글꼴이 있으면 우리 콜백을 트리거합니다. 모든 글꼴이 존재하면 콘솔 출력이 없고, 그렇지 않으면 다음과 같은 라인이 표시됩니다:

```
Substituted: Font 'OpenSans-Regular' not found, substituted with 'Times New Roman'.
Substituted: Font 'CustomIconFont' not found, substituted with 'Arial'.
```

이 출력은 **경고 콜백을 성공적으로 등록**했고 **누락된 글꼴을 감지**하고 있음을 구체적으로 증명합니다.

---

## 전체 작동 예제

아래는 `Main.java` 파일에 복사·붙여넣기만 하면 바로 실행할 수 있는 완전한 Java 프로그램입니다. Aspose.Words JAR가 클래스패스에 포함되어 있는지 확인하세요.

```java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions and enable custom font handling
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setFontSettings(new FontSettings());

            // 2️⃣ Register warning callback to detect missing fonts
            loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("Substituted: " + info.getDescription());
                    }
                }
            });

            // 3️⃣ Load the document using the configured options
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // Optional: Save as PDF to verify visual fidelity
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**예상 출력**(글꼴이 누락된 경우):

```
Substituted: Font 'MyCustomFont' not found, substituted with 'Arial'.
Document loaded and saved successfully.
```

모든 글꼴이 존재하면 성공 메시지만 표시됩니다.

---

## 엣지 케이스 및 흔히 발생하는 함정

| 상황 | 주의할 점 | 권장 해결책 |
|-----------|-------------------|---------------|
| **여러 개의 누락된 글꼴** | 콜백이 여러 번 호출되어 로그가 어수선해질 수 있음 | 메시지를 집계하거나 파일에 기록해 나중에 분석 |
| **성능 영향** | 과도한 로그가 대용량 배치 로드 시 속도를 저하할 수 있음 | 경고 심각도별로 필터링하거나 프로덕션에서는 콘솔 출력을 비활성화 |
| **사용자 정의 글꼴 디렉터리** | `FontSettings`는 기본적으로 시스템 글꼴만 사용 | 콜백 등록 전에 `fontSettings.setFontsFolder("path/to/custom/fonts", true);` 호출 |
| **조용한 대체** | 일부 글꼴은 유사하다고 판단돼 경고 없이 대체될 수 있음 | `fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());` 로 대체 규칙을 세밀하게 조정 |

이러한 시나리오를 미리 대비하면 애플리케이션을 견고하게 유지하고 로그를 의미 있게 만들 수 있습니다.

---

## 솔루션 확장하기

이제 **경고 콜백을 등록**하고 **누락된 글꼴을 감지**하는 방법을 알았으니 다음과 같은 확장을 고려해 보세요:

* **중요한 글꼴이 누락되면 로딩 중단**(콜백 내부에서 예외 발생).  
* **누락된 글꼴 이름을 `Set<String>`에 수집**해 문서 로드 후 요약 보고서 작성.  
* **모니터링 시스템과 연동**(예: Slack이나 Azure Monitor에 알림 전송).  

모두 앞서 보여드린 콜백 패턴을 기반으로 구현할 수 있습니다.

---

## 결론

우리는 Java에서 **경고 콜백을 등록**하고, 문서가 로드되는 순간 **누락된 글꼴을 감지**하는 완전한 생산 환경 예제를 살펴보았습니다. 핵심 포인트는 다음과 같습니다:

* 사용자 정의 `FontSettings`와 함께 `LoadOptions`를 생성.  
* `FONT_SUBSTITUTION` 경고만 필터링하는 `IWarningCallback`을 연결.  
* 해당 옵션으로 문서를 로드하고 누락된 글꼴 이벤트에 대응.

이 지식을 활용하면 문서 처리 파이프라인의 시각적 일관성을 보장하고, 사용자에게 명확한 진단 정보를 제공할 수 있습니다.  

다음 단계가 궁금하신가요? 글꼴 폴더를 추가해 보거나, 다양한 대체 정책을 실험하거나, 콜백을 기존 로깅 프레임워크에 연결해 보세요. 관리하는 글꼴 라이브러리만큼 다양한 가능성이 열려 있습니다.

행복한 코딩 되시고, PDF가 언제나 의도한 대로 렌더링되길 바랍니다!

## Related Tutorials

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}