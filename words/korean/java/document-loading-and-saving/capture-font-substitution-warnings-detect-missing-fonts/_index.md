---
category: general
date: 2026-04-04
description: Aspose.Words for Java를 사용하여 Word 문서를 로드할 때 폰트 대체 경고를 포착하고 누락된 폰트를 자동으로
  감지합니다. 단계별 가이드를 따라 보세요.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: ko
og_description: Aspose.Words for Java를 사용하여 Word 문서를 로드할 때 글꼴 대체 경고를 포착하고, 몇 가지 간단한
  단계로 누락된 글꼴을 감지합니다.
og_title: 폰트 대체 경고 캡처 – 누락된 폰트 감지
tags:
- Aspose.Words
- Java
- Document Processing
title: 폰트 대체 경고 캡처 – 누락된 폰트 감지
url: /ko/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 폰트 대체 경고 캡처 – 누락된 폰트 감지

Word 파일을 열 때 **폰트 대체 경고를 캡처**해야 했지만, 중요한 서체가 없다는 사실을 뒤늦게 알게 된 적이 있나요? 여러분만 그런 것이 아닙니다. 많은 기업 워크플로우에서 누락된 폰트는 완벽하게 포맷된 보고서를 엉망으로 만들 수 있으며, 대부분의 개발자는 거의 보지 못하는 조용한 경고만을 받게 됩니다.

좋은 소식은 Aspose.Words for Java가 로딩 과정에 훅을 걸어 **누락된 폰트를 감지**할 수 있게 해준다는 점입니다. 이 튜토리얼에서는 모든 대체 경고를 콘솔에 바로 출력하는 완전하고 실행 가능한 예제를 단계별로 살펴보겠습니다. 이를 통해 올바른 폰트를 포함하거나, 교체하거나, 사용자에게 알릴지 결정할 수 있습니다.

이 가이드를 마치면 다음을 할 수 있게 됩니다:

* 사용자 정의 경고 콜백이 포함된 `LoadOptions` 객체 설정하기
* 콜백을 필터링하여 폰트‑대체 이벤트에만 반응하도록 만들기
* 任意의 `.docx` 파일을 로드하고 즉시 경고 확인하기
* 솔루션을 확장하여 경고를 로그에 남기거나, 예외를 발생시키거나, 누락된 폰트를 자동으로 설치하기

외부 문서는 필요 없습니다—몇 줄의 Java 코드와 Aspose.Words JAR만 있으면 됩니다.

## 사전 요구 사항

진행하기 전에 다음이 준비되어 있는지 확인하세요:

* Java 8 이상 (최신 LTS 버전 권장)
* Aspose.Words for Java 23.11 이상 – Maven 아티팩트 또는 Aspose 웹사이트에서 제공되는 일반 JAR 중 하나를 사용하세요
* 개발 머신에 설치되지 않은 폰트를 참조하는 Word 문서 (예: “MyFancyFont”)  
* 원하는 IDE 또는 텍스트 편집기 – 저는 IntelliJ IDEA를 사용하지만 Eclipse나 VS Code도 충분합니다

위 항목 중 익숙하지 않은 것이 있다면 먼저 설치하고 진행하세요; 나머지 튜토리얼은 준비가 완료된 상태를 전제로 합니다.

---

## Aspose.Words를 사용해 폰트 대체 경고 캡처하기

솔루션의 핵심은 `LoadOptions` 인스턴스에 있습니다. `IWarningCallback`을 지정하면 로드 단계에서 라이브러리가 발생시키는 모든 경고를 가로챌 수 있습니다.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**작동 원리:**  
`LoadOptions`는 Aspose.Words에게 들어오는 파일을 어떻게 처리할지 알려줍니다. `IWarningCallback` 인터페이스는 *모든* 경고에 대해 `WarningInfo` 객체를 전달받는 훅입니다. `info.getWarningType()`을 확인해 `SUBSTITUTED_FONT` 외의 모든 항목을 걸러냅니다. `description` 속성에는 “Font 'MyFancyFont' was substituted with 'Arial'”와 같은 사람이 읽을 수 있는 메시지가 들어 있습니다.

### 예상 콘솔 출력

문서가 설치되지 않은 폰트를 참조하고 있다면 다음과 같은 메시지를 볼 수 있습니다:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

문서가 머신에 존재하는 폰트만 사용할 경우 콜백은 조용히 동작하고 최종적으로 “Document loaded successfully.” 라인만 출력됩니다.

---

## 문서에서 누락된 폰트 감지하기

“대체 경고가 누락된 폰트와 동일한가?” 라고 궁금할 수 있습니다. 대부분의 경우 그렇습니다—Aspose.Words는 누락된 폰트를 대체 폰트로 교체하고 `SUBSTITUTED_FONT`를 통해 이를 보고합니다. 다만, 폰트 자체는 존재하지만 정확한 스타일(볼드‑이탤릭, 특정 OpenType 기능)이 없을 경우 미묘한 대체가 발생할 수 있습니다.

모든 빈틈을 확실히 잡아내려면 경고 콜백과 로드 후 검사를 결합하면 됩니다:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**팁:** 아직도 누락된 폰트를 참조하는 런이 있다면 즉시 교체할 수 있습니다:

```java
font.setName("Arial"); // fallback
```

이렇게 하면 원래 경고가 억제되었더라도 시각적으로 일관된 결과를 보장할 수 있습니다.

---

## 흔히 저지르는 실수와 해결 방법

| 실수 | 발생 원인 | 해결 방법 |
|------|----------|----------|
| **콜백 설정을 잊음** | `LoadOptions`는 기본적으로 No‑op 콜백을 사용하므로 경고가 사라짐 | 로드하기 전에 항상 `loadOptions.setWarningCallback(...)`를 호출 |
| **잘못된 경고 유형 사용** | `WarningType.SUBSTITUTED_FONT`만이 누락된 폰트를 나타냄 | 정확히 `WarningType.SUBSTITUTED_FONT`로 필터링; `UNKNOWN_FILE_FORMAT` 등 다른 타입은 무관 |
| **파일 경로를 하드코딩** | 로컬에서는 동작하지만 CI/CD 파이프라인에서는 실패 |
| | | 상대 경로나 커맨드라인 인수로 파일 위치 전달 |
| **Unicode 폰트를 무시** | 일부 누락된 폰트는 특정 문자에만 문제를 일으킴 | 지원하려는 전체 문자 집합을 포함한 문서로 테스트 |
| **폰트 설정이 없는 헤드리스 서버에서 실행** | 서버에 폰트가 없으면 예기치 않은 대체가 발생 |
| | | 서버에 최소한의 일반 폰트(Arial, Times New Roman 등) 설치 |

---

## 솔루션 확장하기

이제 **폰트 대체 경고를 캡처**했으니 다음과 같은 작업을 고려해 보세요:

* **경고를 파일에 기록** – `System.out.println`을 SLF4J 같은 로거로 교체
* **예외 발생** – 자동화 파이프라인에서 누락된 폰트가 빌드 실패로 이어지게 할 때 유용:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **누락된 폰트 자동 설치** – 런타임에 필요한 TTF/OTF를 다운로드하고 Java `GraphicsEnvironment`에 추가. 고급 시나리오이지만 충분히 구현 가능.

---

## 다이어그램 (선택)

![Capture font substitution warnings flow diagram showing LoadOptions → WarningCallback → Console output](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Aspose.Words가 누락된 폰트 경고를 사용자 정의 콜백으로 라우팅하는 흐름을 보여주는 폰트 대체 경고 캡처 다이어그램”

---

## 결론

이번 글에서는 Aspose.Words for Java로 Word 문서를 로드할 때 **폰트 대체 경고를 캡처**하고 **누락된 폰트를 감지**하는 방법을 살펴보았습니다. `LoadOptions` 객체를 구성하고 작은 `IWarningCallback`을 구현함으로써 폰트‑대체 프로세스를 완전히 가시화할 수 있으며, 이를 통해 로그를 남기거나, 교체하거나, 빌드를 중단시킬 수 있습니다.

요약하면: 콜백을 설정하고, `SUBSTITUTED_FONT`를 필터링하고, 문서를 로드한 뒤 애플리케이션 요구에 맞게 출력을 처리하면 됩니다. 여기서부터 로깅 프레임워크 연동, CI 체크, 자동 폰트 프로비저닝 등으로 확장할 수 있습니다.

다음 단계로 시도해 보세요:

* **폰트를 문서에 직접 포함** (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))`와 `FontEmbeddingMode.EMBED_ALL` 사용)
* **폰트를 수정한 뒤 PDF 생성** – 최종 출력이 정확히 보이도록 보장
* **전체 폴더를 스캔**해 누락된 폰트를 찾아 요약 보고서 생성

지금까지 읽어 주셔서 감사합니다. 즐거운 코딩 되시고, 문서가 항상 올바른 서체로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}