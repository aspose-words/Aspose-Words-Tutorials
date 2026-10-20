---
category: general
date: 2026-03-19
description: Aspose.Words for Java에서 경고를 캡처하고 누락된 글꼴을 감지하는 방법을 배웁니다. 이 단계별 가이드는 누락된
  글꼴을 우아하게 처리하는 방법도 보여줍니다.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: ko
og_description: Aspose.Words for Java에서 경고를 캡처하고, 누락된 글꼴을 감지하며, 누락된 글꼴을 처리하는 완전한 코드
  예제.
og_title: 경고 캡처 방법 – Aspose.Words에서 누락된 글꼴 감지
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: 경고 캡처 방법 – Aspose.Words에서 누락된 글꼴 감지
url: /ko/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 경고 캡처 방법 – Aspose.Words에서 누락된 폰트 감지

Word 문서를 로드할 때 일부 폰트가 시스템에 없을 경우 **경고를 캡처하는 방법**이 궁금하셨나요? 당신만 그런 것이 아닙니다. 실제 프로젝트에서 누락된 폰트는 조용히 레이아웃이 변형되는 원인이 되며, 어떤 일이 일어났는지 알 수 있는 유일한 방법은 Aspose.Words가 발생시키는 경고 스트림을 청취하는 것입니다.  

이 튜토리얼에서는 **누락된 폰트를 감지**하는 완전한 실행 가능한 예제를 단계별로 살펴보고, 프로그래밍 방식으로 **누락된 폰트를 감지하는 방법**을 보여주며, 출력이 예측 가능하도록 **누락된 폰트를 처리하는** 빠른 팁도 제공합니다.

> **빠른 참고:** 코드는 Aspose.Words 23.9(이상)에서 작동하며 Java 8+이 필요합니다.

---

## 필요 사항

- **Aspose.Words for Java** (Maven/Gradle 의존성 또는 클래스패스에 있는 JAR)  
- 시스템에 설치되지 않은 폰트를 참조하는 Word 파일(`input.docx`) (예: “Comic Sans MS”)  
- Java IDE 또는 간단한 `javac`/`java` 명령줄 설정  

다른 라이브러리는 필요하지 않습니다—모든 것이 Aspose.Words 패키지 내부에 포함되어 있습니다.

---

## 1단계 – LoadOptions 설정으로 경고 캡처  

경고를 청취하려면 먼저 `LoadOptions` 인스턴스를 생성해야 합니다. 이 객체는 로더에게 누락된 폰트와 같은 문제를 추적하도록 지시합니다.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**왜 중요한가:** `LoadOptions` 없이 로더는 누락된 폰트를 조용히 기본 시스템 폰트로 교체하므로 교체가 발생했는지 알 수 없습니다. 경고를 활성화하면 전체 상황을 확인할 수 있습니다.

---

## 2단계 – LoadOptions를 사용해 문서 로드  

이제 실제로 문서를 로드합니다. 방금 만든 `LoadOptions`를 생성자에 전달하면 파싱 중에 발생한 모든 경고가 캡처됩니다.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**프로 팁:** 배치로 많은 파일을 처리할 경우 불필요한 객체 생성을 피하기 위해 동일한 `LoadOptions` 인스턴스를 재사용하세요.

---

## 3단계 – 캡처된 경고 반복 처리  

Aspose.Words는 각 경고를 `WarningInfo` 객체로 저장합니다. 우리는 폰트와 관련된 경고만 필요하므로 `FontSubstitutionWarningInfo`로 필터링합니다.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**설명:**  
- `document.getWarnings()`는 로드 중 발생한 모든 경고의 목록을 반환합니다.  
- `FontSubstitutionWarningInfo`는 두 가지 중요한 데이터를 포함합니다: **요청된 폰트**(DOCX가 요구한 폰트)와 Aspose.Words가 대체한 **실제 폰트**.  
- 두 값을 출력하면 누락된 폰트와 어떤 대체가 이루어졌는지 즉시 확인할 수 있습니다.

---

## 4단계 – (선택) 누락된 폰트를 프로그래밍 방식으로 처리  

경고를 캡처하는 것만으로는 절반에 불과합니다. 폰트가 누락된 것을 알게 되면, 사용자 정의 대체를 제공하거나 나중에 검토할 수 있도록 문제를 로그에 기록하여 **누락된 폰트를 처리**하고 싶을 수 있습니다.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**왜 이렇게 해야 할까요?**  
- 머신 간 일관된 렌더링을 보장합니다.  
- 나중에 생성되는 PDF나 이미지에서 예상치 못한 레이아웃 변화를 방지합니다.  

경고 세부 정보를 데이터베이스에 저장하거나, 콘텐츠 팀에 이메일을 보내거나, 중요한 폰트가 누락된 경우 프로세스를 중단할 수도 있습니다.

---

## 전체 작동 예제  

아래는 완전한 실행 가능한 프로그램입니다. `YOUR_DIRECTORY/input.docx`를 테스트 파일 경로로 교체하고, Aspose.Words JAR를 클래스패스에 추가한 뒤 실행하면 됩니다.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**예상 출력** (“Comic Sans MS”가 없을 때):

```
Requested: Comic Sans MS → Substituted: Arial
```

선택적 대체 코드가 실행된 후 저장된 `output.docx`는 “Comic Sans MS”가 원래 참조된 모든 위치에서 **Arial**을 사용해 렌더링됩니다.

---

## 일반적인 질문 및 엣지 케이스  

| 질문 | 답변 |
|----------|--------|
| *문서에 여러 개의 누락된 폰트가 있는 경우는 어떻게 되나요?* | 루프는 각각에 대해 경고를 발생시킵니다. 배치 처리를 위해 `Map<String, String>`에 수집할 수 있습니다. |
| *문서에서 생성된 PDF에도 적용되나요?* | 네, 확실히 적용됩니다. 폰트 대체는 로드 단계에서 이루어지므로 이후의 내보내기(PDF, HTML, 이미지)에서는 해결된 폰트를 사용합니다. |
| *경고를 캡처하는 대신 억제할 수 있나요?* | 예—`loadOptions.setWarningCallback(null);` 로 설정하면 경고를 억제할 수 있지만 누락된 폰트에 대한 가시성을 잃게 됩니다. |
| *저장 후 경고 목록이 초기화되나요?* | `Document` 인스턴스에 경고 컬렉션이 속합니다. `document.save()`를 호출한 후에도 새 `Document`를 만들지 않는 한 목록은 그대로 유지됩니다. |
| *DOCX에 포함된 사용자 정의 폰트는 어떻게 되나요?* | 내장된 폰트는 사용 가능한 것으로 간주되며, 호스트 시스템에 설치되지 않아도 Aspose.Words가 이를 사용합니다. |

---

## 프로덕션 사용을 위한 팁  

- **FontSettings 캐시:** 수백 개의 파일을 처리하는 경우, 선호하는 대체 폰트를 지정한 단일 `FontSettings`를 생성하고 재사용하여 오버헤드를 줄이세요.  
- **구조화된 데이터 로그:** 일반 `System.out` 대신 경고를 JSON 로그에 기록하면(예: “가장 많이 누락된 폰트”) 하위 분석이 간단해집니다.  
- **조기 검증:** 무거운 처리를 시작하기 전에 `LoadOptions`로 빠른 “드라이 로드”를 실행하고, 중요한 폰트가 누락된 경우 조기에 중단하세요.  
- **스레드 안전성:** `Document` 객체는 스레드에 안전하지 않습니다. 각 파일 처리를 별도 스레드에서 수행하거나 스레드‑로컬 `LoadOptions`를 사용하세요.  

---

## 결론  

이제 Java용 Aspose.Words에서 **경고를 캡처하는 방법**, **누락된 폰트를 감지하는 방법**, 그리고 깔끔한 대체 전략으로 **누락된 폰트를 처리하는 방법**을 알게 되었습니다. `LoadOptions`와 `document.getWarnings()` 반복을 활용하면 폰트 대체 이벤트를 완전히 파악할 수 있어, 생성된 문서가 모든 환경에서 의도한 대로 정확히 표시됩니다.

다음 단계가 준비되셨나요? 이 패턴을 확장하여 **누락된 이미지 감지**, **지원되지 않는 기능 추적**, 혹은 **누락된 폰트를 자동으로 내장**하도록 시도해 보세요. 동일한 경고 캡처 접근 방식은 다른 많은 문서 처리 시나리오에서도 작동하므로 코드를 견고하고 미래에도 안전하게 만들 수 있습니다.

코딩을 즐기세요, 그리고 여러분의 문서가 언제나 아름답게 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}