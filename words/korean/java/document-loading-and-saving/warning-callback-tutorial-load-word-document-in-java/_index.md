---
category: general
date: 2026-03-25
description: Java에서 Word 문서를 로드하고 누락된 글꼴을 처리하기 위한 경고 콜백 튜토리얼. 사용자 정의 경고 콜백을 활용한 Word
  문서 로드 Java 접근 방식을 배워보세요.
draft: false
keywords:
- warning callback tutorial
- load word document java
- handle missing fonts
language: ko
og_description: 경고 콜백 튜토리얼은 사용자 정의 경고 콜백을 사용해 누락된 글꼴을 처리하면서 Java에서 Word 문서를 로드하는 방법을
  보여줍니다.
og_title: 경고 콜백 튜토리얼 – Java에서 Word 문서 로드
tags:
- java
- aspose-words
- document-processing
title: 경고 콜백 튜토리얼 – Java에서 Word 문서 로드
url: /ko/java/document-loading-and-saving/warning-callback-tutorial-load-word-document-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# warning callback tutorial – Load Word Document in Java

Java에서 **.docx** 파일을 로드하려고 했지만 누락된 글꼴에 대한 암호 같은 경고가 표시된 적이 있나요? 당신만 그런 것이 아닙니다. 이 **warning callback tutorial**에서는 Word 문서를 로드할 뿐만 아니라 글꼴 대체 경고를 포착하여 프로그래밍 방식으로 대응할 수 있는 완전하고 바로 실행 가능한 예제를 단계별로 살펴보겠습니다.

만약 **load word document java** 스타일로 로드하면서 *handle missing fonts* 알림을 주시하고 싶다면, 여기가 바로 맞는 곳입니다. 이 가이드를 끝까지 읽으면 Aspose.Words(또는 유사한 라이브러리)를 사용하는 모든 Java 프로젝트에 적용할 수 있는 재사용 가능한 패턴을 얻을 수 있으며, 경고 콜백이 글꼴 문제에 대해 정보를 얻는 가장 깔끔한 방법임을 이해하게 될 것입니다.

---

## What You’ll Learn

- Java에서 경고 콜백을 구성하는 데 필요한 정확한 코드.  
- 콜백이 글꼴 대체 경고를 다른 메시지 유형과 어떻게 구분하는지.  
- 누락된 글꼴을 실시간으로 기록, 억제 또는 교체하는 방법.  
- 사용 불가능한 글꼴을 참조하는 Word 문서를 로드할 때 흔히 발생하는 함정을 해결하기 위한 팁.

### Prerequisites

- 머신에 Java 17(또는 그 이상) 설치되어 있음.  
- Maven 또는 Gradle과 같은 빌드 도구(예제에서는 Maven 스니펫을 보여줌).  
- Aspose.Words for Java 라이브러리(무료 체험판으로 테스트 가능).  
- 누락된 글꼴을 사용하고 있어 경고를 유발하는 샘플 **input.docx** 파일.

> **Pro tip:** 아직 Aspose.Words가 없으시다면 아래에 표시된 의존성을 추가하고 Maven이 자동으로 다운로드하도록 하세요—수동으로 JAR 파일을 관리할 필요가 없습니다.

---

## Step 1: Set Up Your Project and Import Required Classes

먼저 올바른 Maven 좌표가 필요합니다. `pom.xml`에 다음을 추가하세요:

```xml
<!-- Maven dependency for Aspose.Words -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

그런 다음 `WordLoader.java`와 같은 새 Java 클래스를 만들고 필요한 타입을 가져옵니다:

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import com.aspose.words.WarningType;
```

이러한 import는 `LoadOptions`, `IWarningCallback` 인터페이스 및 어떤 문제가 발생했는지 알려주는 `WarningInfo` 객체에 접근할 수 있게 해줍니다.

---

## Step 2: Define the Warning Callback – The Heart of the Tutorial

**warning callback tutorial**는 글꼴 대체 이벤트를 가로채는 데 핵심이 됩니다. 아래는 간결하면서도 완전하게 동작하는 구현 예시입니다:

```java
// Step 2: Create a warning callback that prints font substitution messages
class FontSubstitutionCallback implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("⚠️ Font substituted: " + info.getDescription());
        }
    }
}
```

**왜 중요한가:**  
- `IWarningCallback`은 Aspose.Words가 주목할 만한 상황을 마주할 때마다 *매번* 호출됩니다.  
- `info.getWarningType()`을 확인함으로써 관련 없는 경고(예: 사용 중단된 기능)들을 필터링하고 **handle missing fonts** 시나리오에만 집중합니다.  
- 설명을 로그에 남기면 원본 글꼴 이름과 사용된 대체 글꼴을 확인할 수 있어 이후 레이아웃 검증에 필수적입니다.

---

## Step 3: Wire the Callback into LoadOptions

이제 콜백을 `LoadOptions` 인스턴스에 연결합니다. 여기서 **load word document java** 프로세스가 우리의 사용자 정의 핸들러를 인식하게 됩니다.

```java
// Step 3: Prepare LoadOptions with the custom warning callback
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontSubstitutionCallback());
```

여기서 `setPassword`(암호화된 파일용)나 `setLoadFormat`(특정 포맷 강제 지정)과 같은 다른 옵션도 설정할 수 있습니다. 콜백은 이러한 설정과 독립적으로 동작합니다.

---

## Step 4: Load the Document and Observe the Callback in Action

모든 설정이 완료되면 문서를 로드하는 코드는 한 줄입니다:

```java
// Step 4: Load the .docx file using the configured LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

파일이 누락된 글꼴을 참조하면 다음과 유사한 출력이 표시됩니다:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

문서의 모든 글꼴이 존재한다면 콜백은 조용히 동작합니다—즉, **handling missing fonts**를 우아하게 처리한 결과와 같습니다.

---

## Step 5: Verify the Result and Optional Post‑Processing

로드가 끝난 뒤 문서가 정상적으로 사용 가능한지 확인하고 싶을 수 있습니다. 예를 들어 PDF로 변환하거나 텍스트를 추출해 볼 수 있습니다:

```java
// Optional: Save as PDF to verify visual fidelity
document.save("output.pdf");

// Or extract plain text to a console for quick inspection
System.out.println(document.getText());
```

두 작업 모두 앞서 발생한 대체를 그대로 반영하므로, 누락된 글꼴이 최종 출력에 어떤 영향을 미쳤는지 직접 확인할 수 있습니다.

---

## Edge Cases & Common Pitfalls

| Situation | What Happens | How to Handle |
|-----------|--------------|---------------|
| **Multiple missing fonts** | 콜백이 누락된 글꼴마다 한 번씩 호출됩니다. | 콜백을 가볍게 유지하고 `warning()` 내부에서 무거운 I/O 작업을 피하세요. |
| **Custom font directory** | 기본 검색 경로에 글꼴이 없으면 Aspose.Words가 여전히 대체를 보고합니다. | `loadOptions.setFontSettings(FontSettings.getDefaultInstance())`를 사용하고 `FontSettings.getDefaultInstance().setFontsFolder("path", true)`로 폰트 폴더를 추가하세요. |
| **Performance‑critical apps** | 과도한 로깅이 배치 처리 속도를 저하시킬 수 있습니다. | 로그 레벨을 `WARN`으로 설정하고 프로덕션에서는 콘솔 출력을 비활성화하세요. |
| **Non‑font warnings** | 콜백이 `DEPRECATED_FEATURE`와 같은 다양한 경고 유형을 받습니다. | 예시와 같이 `WarningType`으로 필터링하고, 필요하면 다른 경고를 진단 보고서에 수집하세요. |

---

## Full Working Example

아래는 IDE에 복사‑붙여넣기 할 수 있는 완전한 독립 프로그램입니다. 모든 import, 콜백 클래스 및 간단한 `main` 메서드를 포함하고 있습니다.

```java
import com.aspose.words.*;

public class WordLoader {
    // Custom warning callback – only cares about font substitution
    static class FontSubstitutionCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("⚠️ Font substituted: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with our callback
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setWarningCallback(new FontSubstitutionCallback());

            // 2️⃣ Load the document – this triggers the callback if needed
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 3️⃣ Optional verification – save as PDF and print text
            doc.save("output.pdf");                     // visual check
            System.out.println("--- Extracted Text ---");
            System.out.println(doc.getText());          // quick sanity check
        } catch (Exception e) {
            // In real apps, use proper logging instead of printStackTrace
            e.printStackTrace();
        }
    }
}
```

**예상 콘솔 출력** (누락된 글꼴이 감지될 때):

```
⚠️ Font substituted: Font 'Times New Roman' was not found. Substituted with 'Liberation Serif'.
--- Extracted Text ---
[Document text appears here...]
```

누락된 글꼴이 없으면 추출된 텍스트 헤더만 표시됩니다.

---

## Visual Overview

![LoadOptions → IWarningCallback → 콘솔 출력 흐름을 보여주는 warning callback tutorial 다이어그램](/images/warning-callback-tutorial.png "warning callback tutorial 다이어그램")

*다이어그램은 문서 로드 과정에서 경고 콜백이 글꼴 대체 이벤트를 어떻게 가로채는지를 시각화합니다.*

---

## Recap & Next Steps

우리는 **warning callback tutorial**을 통해 **load word document java** 스타일로 **handle missing fonts**를 우아하게 수행하는 방법을 살펴보았습니다. 핵심 포인트는 다음과 같습니다:

1. `IWarningCallback`을 구현하고 `WarningType.FONT_SUBSTITUTION`을 필터링합니다.  
2. 문서를 로드하기 전에 콜백을 `LoadOptions`에 연결합니다.  
3. 저장하거나 텍스트를 추출하여 결과를 확인하고, 필요에 따라 글꼴 검색 경로를 미세 조정합니다.

다음 단계로 고려해볼 수 있는 내용:

- **Custom font substitution**: 누락된 글꼴을 프로그램matically 원하는 글꼴로 교체합니다.  
- **Batch processing**: 폴더에 있는 여러 문서를 순회하면서 모든 대체 경고를 CSV 보고서로 수집합니다.  
- **Integration with logging frameworks**: Log4j 또는 SLF4J와 연동해 프로덕션 수준의 진단 로깅을 구현합니다.

위 아이디어들을 시도해 보세요. 실제 문서 파이프라인에서 잘 배치된 경고 콜백이 얼마나 강력한지 곧 체감하실 겁니다.

---

### Got Questions?

아래에 댓글을 남기시거나 GitHub에서 저에게 ping 주세요. 즐거운 코딩 되시고, 문서가 언제나 기대한 글꼴로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}