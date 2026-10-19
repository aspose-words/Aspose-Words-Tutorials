---
category: general
date: 2026-03-17
description: 전체 실행 가능한 예제를 통해 Java 문서에서 누락된 글꼴을 감지하고 추적하는 Aspose 경고 콜백 튜토리얼을 배워보세요.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: ko
og_description: Aspose 경고 콜백 튜토리얼을 숙달하여 Java 워드 프로세싱 워크플로우에서 누락된 글꼴을 감지하고 추적하세요.
og_title: Aspose 경고 콜백 튜토리얼 – 누락된 폰트 감지
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Aspose 경고 콜백 튜토리얼 – 누락된 글꼴 감지 및 추적
url: /ko/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – 누락된 글꼴 감지 및 추적

Aspose.Words 로 Word 파일을 변환하거나 편집할 때 **누락된 글꼴을 감지**하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 실제 프로젝트에서는 하나의 잘못된 글꼴 때문에 레이아웃이 깨지는 경우가 많으며, **누락된 글꼴을 추적**할 수 있는 신뢰할 만한 방법이 필요합니다.  

좋은 소식은? **aspose warning callback tutorial** 은 발생하는 글꼴 대체 경고를 정확히 출력해 주는 깔끔한 프로그래밍 훅을 제공합니다. 이 가이드에서는 콜백을 설정하고, 문서를 로드한 뒤, 경고가 어떻게 표시되는지 Java 로 직접 확인해 보겠습니다.

이 글을 끝까지 읽으면 누락된 글꼴을 자동으로 찾아내고, 로그에 기록하며, 대체 글꼴을 삽입하거나 원본 파일을 조정할지 결정할 수 있게 됩니다. 별도의 외부 도구는 필요하지 않습니다.

## 필수 조건

- **Java 8+** (코드는 최신 JDK에서 모두 컴파일됩니다)
- **Aspose.Words for Java** 버전 23.10 이상 – Aspose 포털에서 다운로드하거나 Maven 의존성을 추가하세요.
- 의도적으로 설치되지 않은 글꼴을 참조하는 샘플 DOCX (예: Linux 환경에서 “Comic Sans MS”).

그게 전부입니다—추가 라이브러리도 없고, 복잡한 빌드 단계도 없습니다.

## Step 1: Register a Warning Callback – aspose warning callback tutorial 의 핵심

튜토리얼이 처음 가르쳐 주는 내용은 경고 리스너를 연결하는 방법입니다. Aspose.Words 는 발생하는 모든 문제에 대해 `WarningInfo` 객체를 생성하고, `WarningSource.FONT_SUBSTITUTION` 플래그를 통해 언제 글꼴이 교체되는지 알려줍니다.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**왜 중요한가:** 콜백이 없으면 Aspose 가 조용히 누락된 글꼴을 대체하고, 어떤 글리프가 틀어졌는지 전혀 알 수 없습니다. 경고를 로그에 남기면 **누락된 글꼴을** 조기에 **감지**하고 올바른 글꼴을 삽입할지 결정할 수 있습니다.

> **Pro tip:** 나중에 보고하기 위해 경고를 수집해야 한다면, 바로 출력하지 말고 `List<WarningInfo>` 에 저장하세요.

## Step 2: Load the Document – 누락된 글꼴이 숨어 있을 수 있는 곳

이제 머신에 설치되지 않은 글꼴을 참조할 수 있는 DOCX 를 로드합니다. 로드 과정에서 누락된 글꼴이 있으면 경고 콜백이 트리거됩니다.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**배경에서 무슨 일이 일어나나요?** Aspose 가 문서의 스타일 정의를 파싱하고, 각 텍스트 런을 스캔하며 시스템 글꼴 저장소를 확인합니다. 정확한 매치를 찾지 못하면 대체 글꼴로 전환하고, 방금 연결한 경고를 발생시킵니다.

## Step 3: Save the Document – 경고 플러시하기

마지막으로 문서를 저장합니다. 저장 작업 역시 글꼴을 다시 평가하므로, 로드 시 발생하지 않은 경고도 이제 표시됩니다.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

프로그램을 실행하면 다음과 유사한 콘솔 출력이 나타납니다:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

이 출력은 **aspose warning callback tutorial** 이 정상적으로 동작함을 증명하며, **누락된 글꼴을 감지**하고 로그를 통해 **누락된 글꼴을 추적**하고 있음을 보여줍니다.

## How to Detect Missing Fonts in a Word Document – 기본을 넘어

콜백 방식은 일회성 실행에 적합하지만, 재사용 가능한 유틸리티가 필요할 때도 있습니다. 아래와 같이 간단한 래퍼를 프로젝트에 추가해 보세요:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

사용 예시:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

이제 CI 파이프라인이나 UI 에 전달할 수 있는 **detect missing fonts** 메서드를 재사용할 수 있습니다.

## Tracking Missing Fonts with Aspose.Words – 팀을 위한 보고

대규모 팀에서는 여러 문서에 걸친 누락된 글꼴을 CSV 보고서로 만들고 싶을 수 있습니다. 앞서 만든 유틸리티에 파일 순회 로직을 결합하면 됩니다:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

이 스크립트를 실행하면 모든 개발자가 문서를 프로덕션에 커밋하기 전에 확인할 수 있는 **track missing fonts** CSV 가 생성됩니다.

## Common Pitfalls & How to Avoid Them

| 함정 | 발생 원인 | 해결 방법 |
|------|-----------|----------|
| **Callback not firing** | 문서를 로드하기 **앞서** 콜백을 설정하는 것을 잊었습니다. | `Document.setWarningCallback` 을 `main` 메서드 최상단에 배치하세요. |
| **Only first warning appears** | Aspose 가 `Document` 인스턴스당 경고를 캐시합니다. | 파일마다 새로운 `Document` 객체를 사용하거나, 실행 사이에 콜백을 재설정하세요. |
| **Wrong font name in log** | 설명에 추가 텍스트(예: “Font … not found”)가 포함됩니다. | CSV 예시와 같이 정규식으로 문자열을 정리하세요. |
| **Performance hit on large batches** | 콜백이 모든 텍스트 런마다 실행돼 비용이 많이 듭니다. | 사전 검사 단계로 체크를 제한하고, 감지만 필요하면 저장을 건너뛰세요. |

## Expected Results & Verification

1. **Console output** – 누락된 각 글꼴마다 최소 하나의 “Font substitution warning” 라인이 표시되어야 합니다.  
2. **CSV report** – 배치 스크립트가 완료된 후 `missing-fonts-report.csv` 를 열어 각 행에 문서 이름과 정확한 누락 글꼴이 기록되어 있는지 확인하세요.  
3. **Saved document** – 출력된 DOCX 는 대체 글꼴로 렌더링되지만, 시각적 레이아웃이 원본과 다를 수 있습니다.

위 단계 중 어느 하나라도 기대한 대로 동작하지 않으면 Aspose.Words JAR 가 클래스패스에 포함되어 있는지, `input.docx` 가 실제로 OS 에 설치되지 않은 글꼴을 참조하고 있는지 다시 확인하세요.

## Conclusion

당신은 이제 **aspose warning callback tutorial** 을 완료했으며, Java 애플리케이션에서 **누락된 글꼴을 감지**하고 **누락된 글꼴을 추적**하는 방법을 익혔습니다. 경고 리스너를 등록하고, 문서를 로드하며, 필요에 따라 결과를 내보내면 프로덕션에 문제가 발생하기 전에 글꼴 관련 이슈를 완전히 파악할 수 있습니다.

다음으로 살펴볼 내용:

- `LoadOptions.setFontSubstitution` 으로 누락된 글꼴을 직접 삽입하기
- `FontSettings` 클래스를 사용해 누락된 글꼴을 특정 대체 글꼴에 매핑하기
- CSV 보고서를 CI/CD 파이프라인에 통합해 문서에 미등록 글꼴이 나타날 경우 빌드를 실패시키기

한 번 실행해 보고, 로깅 프레임워크에 맞게 콜백을 조정해 보세요. 그러면 문서 워크플로가 훨씬 견고해질 것입니다. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}