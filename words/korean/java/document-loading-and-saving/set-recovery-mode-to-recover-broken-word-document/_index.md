---
category: general
date: 2026-02-15
description: 복구 모드를 설정하면 복구 기능으로 문서를 로드할 수 있어 손상된 Word 문서를 쉽게 복구하고 복구 오류를 수정할 수 있습니다.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: ko
og_description: 복구 모드를 설정하는 것이 복구 기능을 사용해 문서를 로드하는 핵심이며, 이를 통해 Java에서 손상된 Word 문서
  오류를 복구할 수 있습니다.
og_title: 복구 모드 설정 – 손상된 Word 문서 빠르게 복구
tags:
- Aspose.Words
- Java
- Document Recovery
title: 복구 모드를 설정하여 손상된 Word 문서 복구
url: /ko/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – 손상된 Word 문서를 Aspose.Words로 복구하는 방법

Word 파일을 열었는데 갑자기 로드가 거부되는 경우가 있나요? 손상된 *.docx* 파일을 바라보며 처음부터 다시 시작해야 할지 고민하고 있을 수도 있습니다. 좋은 소식은? Aspose.Words의 **set recovery mode**를 사용하면 *load document with recovery*를 통해 대부분의 내용을 유지하면서 문서를 부드럽게 복구할 수 있습니다.  

이 튜토리얼에서는 **set recovery mode**를 정확히 설정하는 방법, 손상된 파일에 대해 일반적으로 가장 좋은 선택인 *RELAXED* 옵션의 이유, 그리고 여전히 발생할 수 있는 *recover word document errors*를 처리하는 방법을 배웁니다. 외부 도구 없이 순수 Java와 몇 줄의 코드만으로 가능합니다.

> **What you’ll walk away with:** 손상된 Word 파일을 로드하고 읽을 수 없는 부분을 건너뛰며, 추가 처리를 위해 사용할 수 있는 `Document` 객체를 얻는 완전한 실행 예제.

---

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- **Aspose.Words for Java** (v24.9 이상) 를 Maven 또는 수동 JAR을 통해 프로젝트에 추가.
- 테스트할 **corrupted .docx** 파일 (`Corrupted.docx` 라고 부르겠습니다).
- 기본 Java 지식 – Word‑processing 전문가일 필요는 없으며 `main` 메서드만 사용할 수 있으면 됩니다.

위 항목 중 하나라도 없으면 [공식 사이트](https://products.aspose.com/words/java)에서 최신 Aspose.Words JAR를 다운로드하여 클래스패스에 추가하세요. 그뿐입니다—추가 의존성은 없습니다.

---

## Step 1: Understand the Recovery Modes

Aspose.Words는 두 가지 복구 전략을 제공합니다:

| Mode | Behavior | When to use |
|------|----------|------------|
| **RELAXED** | 읽을 수 없는 부분을 건너뛰고 나머지는 유지합니다. | 대부분의 손상된 파일 – 예외 없이 **recover broken word document**를 원할 때. |
| **STRICT** | 오류가 발생하면 예외를 발생시킵니다. | 완벽하고 오류 없는 로드가 반드시 보장되어야 할 경우 (손상된 소스에서는 드물게 사용). |

> **Pro tip:** *RELAXED*는 “뭐든지 되찾아라” 시나리오의 기본값이며, *STRICT*는 실패 시 파이프라인을 중단해야 하는 자동화된 흐름에 유용합니다.

---

## Step 2: Create a `LoadOptions` Object and **set recovery mode**

코드에서 핵심 키워드가 등장하는 부분입니다. 파일을 로드하기 전에 `LoadOptions` 인스턴스에 **set recovery mode**를 명시적으로 설정합니다.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Why this matters:** `setRecoveryMode`를 호출하면 Aspose.Words에 파일을 얼마나 적극적으로 복구할지 알려줍니다. 이 호출이 없으면 라이브러리는 기본값인 *STRICT*를 사용해 첫 번째 문제 발생 시 바로 중단하므로 *recover broken word document* 워크플로의 목적에 맞지 않습니다.

---

## Step 3: Verify the Load – Did We Really **recover broken word document**?

로드 후 `Document` 객체를 검사할 수 있습니다:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

콘솔에 합리적인 섹션 수가 표시되면 *load document with recovery*에 성공한 것입니다. 실제로 대부분의 텍스트, 표, 이미지가 유지되고 손상된 부분은 사라집니다.

---

## Step 4: Handle Remaining **recover word document errors** Gracefully

*RELAXED* 모드에서도 일부 엣지 케이스는 경고를 발생시킬 수 있습니다. 앱이 중단되지 않도록 로드를 try‑catch 블록으로 감싸세요:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**When would this happen?** 파일이 너무 손상되어 완화된 파서조차 유효한 문서 구조를 식별하지 못할 경우 Aspose.Words는 여전히 예외를 발생시킵니다. 이런 드문 상황에서는 사용자가 다른 복사본을 제공하도록 요청해야 할 수 있습니다.

---

## Step 5: Save the Recovered File (Optional)

대부분의 개발자는 다운스트림 시스템에 전달할 깨끗한 버전을 원합니다. 아래 `save` 호출은 손상된 조각이 포함되지 않은 새로운 `.docx` 파일을 작성합니다.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

이제 **recover broken word document**가 Microsoft Word, Google Docs 또는 기타 뷰어에서 오류 대화상자 없이 열 수 있습니다.

---

## Visual Overview (Image)

![Diagram showing set recovery mode flow – from corrupted file to recovered document](https://example.com/images/recovery-flow.png "set recovery mode flow diagram")

*The alt text explicitly contains the primary keyword, helping both search engines and screen readers.*

---

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| *What if I need to keep the corrupted parts for forensic analysis?* | `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)`를 사용하고 예외를 잡으세요. 예외 메시지에 문제 부분에 대한 상세 정보가 포함됩니다. |
| *Can I switch between RELAXED and STRICT at runtime?* | 물론입니다—각 로드 전에 원하는 모드로 새로운 `LoadOptions` 인스턴스를 생성하면 됩니다. |
| *Does this work with older .doc files?* | 네. 동일한 `LoadOptions`가 `.doc`와 `.docx` 형식 모두에 적용됩니다. |
| *Is there a performance penalty?* | 최소 수준입니다. 추가 파싱 오버헤드는 전체 문서 로드 비용에 비해 무시할 수 있을 정도입니다. |

---

## Full Working Example (Copy‑Paste Ready)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

프로그램을 실행하고 손상된 파일을 지정하면 출력 결과를 확인할 수 있습니다. 모든 것이 정상적으로 진행되면 페이지 수가 출력되고 원본 옆에 새로운 `Recovered.docx` 파일이 생성됩니다.

---

## Conclusion

우리는 Aspose.Words에서 **set recovery mode**를 설정하는 모든 방법—올바른 `RecoveryMode` 열거형 선택부터 남아 있을 수 있는 *recover word document errors* 처리까지—을 다루었습니다. 위 단계를 따르면 **load document with recovery**를 신뢰성 있게 수행하고 손상된 파일의 유용한 부분을 유지하면서 깨끗한 버전을 출력해 다운스트림 처리에 바로 사용할 수 있습니다.

다음 도전 과제가 준비되셨나요? **set recovery mode**를 Aspose.Words의 **document cleaning** API와 결합해 숨겨진 단락을 제거하고, 깨진 하이퍼링크를 수정하거나 복구된 파일을 PDF로 변환하는 등 한 번에 처리해 보세요. 가능성은 무궁무진하며, 이제 손상된 Word 파일을 정면으로 맞설 탄탄한 기반을 갖추었습니다.

Happy coding, and may your documents stay healthy!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}