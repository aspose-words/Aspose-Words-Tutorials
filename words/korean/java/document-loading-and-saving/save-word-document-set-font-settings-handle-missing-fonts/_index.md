---
category: general
date: 2026-04-24
description: Aspose.Words를 사용하여 글꼴 설정을 적용하고 누락된 글꼴을 처리하면서 Word 문서를 저장하는 방법을 쉬운 Java
  코드로 배워보세요.
draft: false
keywords:
- save word document
- set font settings
- how to set font settings
- aspose words font substitution
- handle missing fonts
language: ko
og_description: Aspose.Words를 사용해 글꼴 설정을 지정하고 누락된 글꼴을 처리하면서 Word 문서를 저장합니다. 개발자를 위한
  완전한 Java 가이드.
og_title: Word 문서 저장 – 글꼴 설정 및 누락된 글꼴 처리
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: 워드 문서 저장 – 글꼴 설정 및 누락된 글꼴 처리
url: /ko/java/document-loading-and-saving/save-word-document-set-font-settings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서 저장 – 글꼴 설정 지정 및 누락된 글꼴 처리

소스 파일에 사용된 글꼴이 서버에 없을 때 **Word 문서를 저장**해야 했던 적이 있나요? 자동화 파이프라인을 원활하게 진행하던 중 흔히 겪는 문제입니다.  

좋은 소식은? Aspose.Words를 사용하면 **글꼴 설정을 동적으로 지정**하고, 누락된 글꼴 경고를 포착하며, 여전히 완벽하게 저장된 Word 문서를 얻을 수 있습니다. 이번 튜토리얼에서는 **글꼴 설정을 지정하는 방법**, 끔찍한 *글꼴 대체* 경고를 처리하는 방법, 그리고 최종적으로 **Word 문서를 저장**하는 전체 Java 예제를 단계별로 살펴보겠습니다.

## 배울 내용

- 사용자 정의 `FontSettings` 객체를 사용해 `LoadOptions`를 구성하는 방법.  
- **aspose words font substitution** 이벤트를 보고하는 경고 콜백을 등록하는 방법.  
- DOCX를 로드하고 Aspose가 누락된 글꼴을 대체하도록 한 뒤, **Word 문서를 저장**하여 새 위치에 저장하는 방법.  
- 암호화된 파일이나 임베디드 글꼴이 포함된 문서와 같은 예외 상황을 처리하는 팁.  

Aspose.Words 외에 추가 라이브러리는 필요 없으며, 코드는 최신 24.x 릴리스(2026년 4월 기준)와 호환됩니다.  

---

![Diagram illustrating the save word document workflow with font settings and warning callback](font-workflow.png "Diagram showing save word document workflow")

## 사용자 정의 글꼴 설정으로 Word 문서 저장

첫 번째 단계는 Aspose.Words에게 소스 문서가 참조하는 글꼴을 찾지 못했을 때 어떻게 할지를 알려주는 것입니다. 여기서 **글꼴 설정 지정**이 필요합니다.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 1: Prepare LoadOptions with a fresh FontSettings instance.
        // -----------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        // By default FontSettings uses system fonts, but we can add folders later.
        loadOptions.setFontSettings(new FontSettings());

        // -----------------------------------------------------------------
        // Step 2: Register a warning callback to catch FONT_SUBSTITUTION alerts.
        // -----------------------------------------------------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about missing‑font warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // -----------------------------------------------------------------
        // Step 3: Load the source document using the configured options.
        // -----------------------------------------------------------------
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // -----------------------------------------------------------------
        // Step 4: Save the processed document – fonts have been substituted.
        // -----------------------------------------------------------------
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**동작 원리:**  
- `LoadOptions`는 파일을 파싱할 때 제공된 `FontSettings`를 사용하도록 Aspose.Words에 지시합니다.  
- `IWarningCallback`은 **aspose words font substitution** 메시지를 가로채어 어떤 글꼴이 누락되었는지 실시간 로그를 제공합니다.  
- `document.save(...)`를 호출하면 Aspose가 시스템 또는 `FontSettings`에 추가한 폴더에서 가장 근접한 글꼴로 자동 대체합니다.

### 예상 결과

프로그램을 실행하면 다음과 같은 라인이 출력됩니다:

```
Font substitution: Font 'Calibri' was not found. Substituted with 'Arial'.
Font substitution: Font 'Cambria' was not found. Substituted with 'Times New Roman'.
```

그리고 `output.docx` 파일은 원본과 거의 동일하게 보이지만, 누락된 글꼴이 대체되고 파일이 정상적으로 **saved word document**됩니다.

## Aspose.Words에서 글꼴 설정 지정하기

더 많은 제어가 필요하다면—예를 들어 사용자 정의 글꼴 폴더를 지정하거나 대체 글꼴을 임베드하고 싶다면—`LoadOptions`에 할당하기 전에 `FontSettings` 객체를 조정하면 됩니다.

```java
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder that contains your private fonts.
fontSettings.setFontsFolder("C:/MyCustomFonts", true);

// Optionally, set a default substitution font (e.g., "Arial").
fontSettings.setDefaultFontName("Arial");

// Attach the configured FontSettings to LoadOptions.
loadOptions.setFontSettings(fontSettings);
```

**사용 시점:**  
- 컨테이너에 최소한의 시스템 글꼴만 포함된 경우.  
- 기업 브랜드 글꼴이 보안 네트워크 공유에 저장된 경우.  
- 특정 대체 글꼴(예: “Arial”)을 항상 사용하도록 보장하여 예측하지 못한 대체를 방지하고 싶은 경우.

## 누락된 글꼴 처리 – 글꼴 대체 콜백

앞서 등록한 경고 콜백은 **handle missing fonts** 로직의 핵심입니다. 이를 확장하여 다음을 수행할 수 있습니다:

1. **경고를 리스트에 수집**하여 나중에 보고.  
2. 중요한 글꼴이 누락된 경우(예: 로고 글꼴) **예외 발생**.  
3. **모니터링 시스템**(Splunk, ELK 등)에 로그를 남겨 감사 추적 확보.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    private final List<String> missingFonts = new ArrayList<>();

    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String msg = "Missing font: " + info.getDescription();
            System.out.println(msg);
            missingFonts.add(msg);
        }
    }

    // Helper to retrieve all missing‑font messages after loading.
    public List<String> getMissingFonts() {
        return missingFonts;
    }
});
```

**프로 팁:** 특정 글꼴이 없을 때 작업을 중단하려면 `info.getDescription()`을 화이트리스트와 비교하고 일치하지 않을 경우 `RuntimeException`을 발생시키세요.

## 전체 Java 예제 – 시작부터 끝까지

모든 내용을 종합한, IDE에 복사‑붙여넣기만 하면 되는 독립 실행형 프로그램입니다. 클래스패스에 Aspose.Words for Java JAR가 포함되어 있는지 확인하세요.

```java
import com.aspose.words.*;
import java.util.*;

public class SaveWordWithFontHandling {
    public static void main(String[] args) throws Exception {
        // ------------------- Configure FontSettings -------------------
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains any custom fonts you might need.
        fontSettings.setFontsFolder("C:/CustomFonts", true);
        // Ensure a safe fallback.
        fontSettings.setDefaultFontName("Arial");

        // ------------------- Prepare LoadOptions -------------------
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setFontSettings(fontSettings);

        // ------------------- Warning callback (handle missing fonts) -------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            private final List<String> missing = new ArrayList<>();

            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBstitution) {
                    String msg = "Font substitution: " + info.getDescription();
                    System.out.println(msg);
                    missing.add(msg);
                }
            }

            public List<String> getMissing() {
                return missing;
            }
        });

        // ------------------- Load the source DOCX -------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ------------------- Save the result -------------------
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

프로그램을 실행하고 콘솔에 표시되는 **font

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}