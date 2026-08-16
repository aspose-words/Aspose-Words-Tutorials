---
category: general
date: 2026-06-20
description: Aspose.Words Java에서 콜백을 설정하여 누락된 글꼴을 감지하고 문서 로드를 사용자 지정하는 방법. 글꼴 대체 경고를
  단계별로 처리하는 방법을 배워보세요.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: ko
og_description: Aspose.Words Java에서 콜백을 설정하여 누락된 글꼴을 감지하고, 대체를 처리하며, 문서 로드를 사용자 정의하는
  방법. 코드와 함께하는 완전 가이드.
og_title: 콜백 설정 방법 – Aspose.Words Java에서 누락된 글꼴 감지
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Aspose.Words Java에서 콜백 설정 방법 – 누락된 글꼴 감지 및 처리
url: /ko/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java에서 콜백 설정 방법 – 누락된 폰트 감지 및 처리

PDF나 DOCX가 폰트 문제로 깨지기 전에 누락된 폰트를 찾아낼 수 있도록 Aspose.Words Java에서 **콜백을 설정하는 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 누락된 폰트 경고는 레이아웃을 조용히 손상시킬 수 있으며, 적절한 경고 콜백이 없으면 최종 문서가 이상하게 보일 때까지 눈치채지 못할 수도 있습니다.

이 튜토리얼에서는 **누락된 폰트를 감지**하고, **누락된 폰트를 우아하게 처리**하며, 경고 콜백을 사용해 **문서 로딩을 사용자 정의**하는 완전한 실행 예제를 단계별로 살펴봅니다. 끝까지 따라오면 별도의 문서 검색 없이도 어떤 프로젝트에든 바로 넣어 사용할 수 있는 독립적인 Java 클래스를 얻게 됩니다.

## 필요 사항

- Java 8 이상 (코드는 Java 11+에서도 작동합니다)  
- Aspose.Words for Java 라이브러리 (버전 23.9 이상)  
- 설치되지 않은 폰트를 참조하는 DOCX 파일(예: 사용자 정의 기업 폰트)  

아직 Maven 프로젝트에 Aspose.Words를 추가하지 않았다면, 다음을 포함하면 됩니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

그게 전부—추가 플러그인이나 네이티브 종속성은 필요 없습니다.

---

## Step 1: WarningCallback 메커니즘 이해하기

**경고 콜백**은 문서를 로드하거나 저장하는 동안 예상치 못한 상황이 발생했을 때 Aspose.Words가 여러분에게 알리는 방식입니다. `IWarningCallback`을 구현하면 로그에 기록할지, 무시할지, 혹은 예외로 전환할지 완전히 제어할 수 있습니다.

> **왜 중요한가:**  
> 폰트가 누락되면 Aspose는 대체 폰트를 사용합니다. 시각적 결과는 특히 브랜드가 중요한 PDF에서 크게 달라질 수 있습니다. `WarningType.FONT_SUBSTITUTION`을 포착하면 정확한 폰트 이름을 로그에 남기고, 작업을 중단하거나 자체 커스텀 폰트를 프로그래밍 방식으로 대체할 수 있습니다.

## Step 2: LoadOptions 인스턴스 만들기

`LoadOptions`는 문서 로딩을 사용자 정의하는 진입점입니다. 파일을 실제로 로드하기 전에 이 객체에 콜백을 연결합니다.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

이 시점에서 `loadOptions`는 단순한 컨테이너일 뿐이며 아직 아무 일도 일어나지 않습니다. 실제 마법은 콜백을 연결할 때 시작됩니다.

## Step 3: 콜백 구현 및 연결하기

아래는 `IWarningCallback`을 구현한 간결한 익명 클래스 예시입니다. 폰트 대체가 발생할 때마다 콘솔에 친절한 메시지를 출력합니다.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **프로 팁:** 누락된 폰트를 직접 교체하고 싶다면 `LoadOptions`에 `FontSettings`를 설정하고 누락된 폰트를 알려진 대체 폰트에 매핑할 수 있습니다.

## Step 4: 사용자 정의 옵션으로 문서 로드하기

이제 콜백이 연결되었으니 문서를 로드합니다. 파일이 존재하지 않는 폰트를 참조하고 있다면 경고가 콘솔에 출력됩니다.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

프로그램을 실행하면 콘솔에 다음과 같은 내용이 표시될 수 있습니다:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

이 라인은 **누락된 폰트를 성공적으로 감지**했으며, 이제 **누락된 폰트를 원하는 방식으로 처리**할 수 있음을 증명합니다.

## Step 5: 선택 사항 – 누락된 폰트를 알려진 폰트로 교체하기

예를 들어 누락된 모든 폰트를 `Times New Roman`으로 자동 교체하고 싶다면 `FontSettings` 객체를 추가합니다:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

이제 문서가 로드될 때 `MyCustomFont`에 대한 모든 참조가 조용히 `Times New Roman`으로 교체됩니다. 콘솔에는 여전히 교체된 내용이 표시되어 상황을 파악할 수 있습니다.

## Full Working Example

아래는 앞서 설명한 모든 단계를 하나의 Java 클래스로 통합한 예시입니다. IDE에 복사‑붙여넣기하고 `docPath`만 조정한 뒤 실행하면 됩니다.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**예상 출력**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

이제 **누락된 폰트를 감지**, **누락된 폰트를 처리**, **문서 로딩을 사용자 정의**하는 재현 가능한 방법을 갖게 되었으며, **콜백을 올바르게 설정**하는 방법을 배웠습니다.

## Frequently Asked Questions

### 폰트가 누락될 때 프로그램이 로딩을 중단하도록 하려면 어떻게 해야 하나요?

`warning` 메서드 내부에서 예외를 발생시키면 됩니다:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

아래쪽의 `catch` 블록이 이를 포착하고, 로그를 남기거나 사용자에게 알리는 방식을 선택할 수 있습니다.

### DOCX에서 생성된 PDF에도 적용되나요?

물론입니다. 콜백은 **로드** 단계에서 발생하므로 출력 형식(`PDF`, `DOCX`, `HTML` 등)과 관계없이 동일하게 동작합니다. 동일한 `LoadOptions`로 소스 문서를 로드하면 최종 PDF에 영향을 주기 전에 누락된 폰트를 잡아낼 수 있습니다.

### 이미지 변환 같은 다른 경고 유형도 포착할 수 있나요?

네. `WarningInfo.getWarningType()`을 사용해 `WarningType.IMAGE_CONVERSION` 같은 다른 열거형과 비교하면 됩니다. 콜백에 추가 `if` 분기를 넣기만 하면 됩니다.

### 성능에 영향을 미치나요?

거의 없습니다. 콜백은 로딩 중 동기식으로 실행되며 추가 검사는 가볍습니다. 수천 개의 문서를 로드한다면 `loadOptions.setWarningCallback(null);` 로 프로덕션 환경에서 경고를 비활성화하는 것이 좋습니다.

## Visual Overview

![Aspose.Words Java에서 콜백 설정 예시](https://example.com/images/callback-diagram.png "콜백 설정 방법")

*다이어그램은 흐름을 보여줍니다: `LoadOptions` → `IWarningCallback` → 문서 로딩 → 폰트 대체 처리.*

## Wrap‑Up

우리는 Aspose.Words Java에서 **콜백을 설정하는 방법**을 다루고, **누락된 폰트를 감지**하며, **누락된 폰트를 처리**하는 실용적인 방법을 보여주었고, `LoadOptions`를 사용해 **문서 로딩을 사용자 정의**하는 방법을 설명했습니다.

이 지식을 바탕으로 이제 문서 파이프라인에서 조용한 폰트 교체를 방지하고, 브랜드 일관성을 유지하며, 문제가 발생했을 때 사용자에게 명확한 피드백을 제공할 수 있습니다.

### 다음 단계는?

- 많은 누락된 폰트를 일괄 매핑할 수 있는 **font substitution tables** 탐색하기.  
- 이 콜백을 **document validation**과 결합해 스타일 가이드를 강제 적용하기.  
- `System.out` 대신 로그 파일이나 모니터링 시스템에 기록하는 **custom warning callbacks** 시도하기.  

자유롭게 실험해 보고, 여러분만의 프로젝트에 맞게 콜백을 어떻게 커스터마이징했는지 알려 주세요. 즐거운 코딩 되세요!

---

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 연관된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for Java에서 LoadOptions 설정 방법](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words에서 폰트 감지 – 경고 및 설정 처리](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words에서 폰트 캡처 – 완전 가이드](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}