---
category: general
date: 2025-12-23
description: 복구 모드를 설정하여 손상된 Word 문서를 복구합니다. DOCX 파일을 여는 방법, 복구 모드 사용법, 그리고 Java에서
  손상된 파일을 처리하는 방법을 배웁니다.
draft: false
keywords:
- set recovery mode
- recover damaged word
- how to open docx
- open corrupted word file
- use recovery mode
language: ko
og_description: 복구 모드를 설정하여 손상된 Word 문서를 복구합니다. 이 가이드는 DOCX 파일을 여는 방법, 복구 모드 사용 방법,
  그리고 Java에서 손상된 파일을 처리하는 방법을 보여줍니다.
og_title: 복구 모드 설정 – Java에서 손상된 Word 파일 열기
tags:
- Java
- Aspose.Words
- Document Recovery
title: 복구 모드 설정 – Java에서 손상된 Word 파일 열기 방법
url: /ko/java/document-loading-and-saving/set-recovery-mode-how-to-open-corrupted-word-files-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 복구 모드 설정 – Java에서 손상된 Word 파일 열기

Word 문서가 열리지 않을 때 **복구 모드 설정**을 시도해 본 적 있나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 DOCX 파일이 약간 손상되면 `new Document("file.docx")` 호출이 예외를 발생시키는 상황에 부딪히곤 합니다. 좋은 소식은? Aspose.Words for Java는 **복구 모드 사용**과 실제로 **손상된 Word 파일 복구**를 위한 내장 기능을 제공합니다.

이 튜토리얼에서는 `LoadOptions` 설정부터 일반적으로 문제가 되는 엣지 케이스 처리까지, **손상된 Word 파일** 객체를 안전하게 **열기** 위해 알아야 할 모든 것을 단계별로 안내합니다. 불필요한 내용은 없습니다—지금 바로 프로젝트에 붙여넣을 수 있는 실용적인 솔루션만 제공합니다.

> **프로 팁:** 사소한 결함(예: 푸터 누락)만 있는 경우 **Tolerant** 복구 모드면 충분합니다. 문서를 100 % 깨끗하게 유지해야 할 때는 **Strict** 모드를 사용하세요.

## 준비물

- **Java 17** (또는 최신 JDK; API는 동일하게 동작합니다)
- **Aspose.Words for Java** 23.9 (또는 최신) – `LoadOptions` 클래스를 제공하는 라이브러리
- 테스트용 **손상된 DOCX** 파일 (유효한 파일을 헥스 에디터로 잘라서 만들 수 있습니다)
- 선호하는 IDE (IntelliJ, Eclipse, VS Code 등)

그게 전부입니다. 별도의 Maven 플러그인이나 외부 유틸리티는 필요 없습니다. 핵심 라이브러리와 약간의 코드만 있으면 됩니다.

![복구 모드 설정](/images/set-recovery-mode-java.png){.align-center alt="복구 모드 설정"}

## Step 1 – `LoadOptions` 인스턴스 생성

먼저 `LoadOptions` 객체를 인스턴스화합니다. 이는 Aspose.Words에게 **입력 파일을 어떻게 처리할지** 알려주는 도구 상자와 같습니다.

```java
import com.aspose.words.LoadOptions;

// Step 1: Create LoadOptions with default settings
LoadOptions loadOptions = new LoadOptions();
```

왜 이 단계를 건너뛰면 안 될까요? `LoadOptions`가 없으면 라이브러리에 **복구 모드 사용** 여부를 전달할 수 없습니다. 기본 동작은 Strict 모드이며, 이는 어느 정도 손상이 있더라도 로드를 중단합니다.

## Step 2 – 올바른 복구 모드 선택

Aspose.Words는 두 가지 열거형 값을 제공합니다:

| Mode | 동작 설명 |
|------|-----------|
| `RecoveryMode.Tolerant` | 가능한 한 많이 복구하려 시도합니다. 스타일 누락이나 관계 손상 정도의 *손상된 Word 복구* 시나리오에 적합합니다. |
| `RecoveryMode.Strict`   | 문제가 발생하면 즉시 실패합니다. 문서를 완전히 깨끗하게 유지해야 할 때 사용합니다. |

한 줄로 모드를 설정합니다:

```java
import com.aspose.words.RecoveryMode;

// Step 2: Tell the loader to be forgiving
loadOptions.setRecoveryMode(RecoveryMode.Tolerant); // or RecoveryMode.Strict
```

**왜 중요한가:** **복구 모드**를 사용하면 라이브러리가 내부적으로 손상된 부분을 패치하고, 누락된 XML 노드를 재구성하여 사용 가능한 `Document` 객체를 반환합니다. *Strict* 모드에서는 대신 `InvalidFormatException`이 발생합니다.

## Step 3 – 옵션을 적용해 문서 로드

이제 `LoadOptions`를 전달하면서 파일을 Aspose.Words에 넘깁니다.

```java
import com.aspose.words.Document;

// Step 3: Load the (potentially corrupted) DOCX
String filePath = "C:/Documents/corrupted.docx";
Document doc = new Document(filePath, loadOptions);
```

파일이 약간만 손상된 경우 `doc`은 완전한 `Document` 객체가 됩니다. 이제 다음을 수행할 수 있습니다:

- 텍스트 읽기 (`doc.getText()`),
- 다른 형식으로 저장 (`doc.save("repaired.pdf")`),
- `Document` API를 통해 복구된 파트 목록을 검사

### 복구 확인

복구가 실제로 성공했는지 빠르게 확인하는 방법:

```java
if (doc.getSections().getCount() > 0) {
    System.out.println("Document loaded successfully – recovery mode worked!");
} else {
    System.out.println("No sections found – the file might be beyond repair.");
}
```

## Step 4 – 엣지 케이스 처리

### 4.1 Tolerant 모드만으로는 부족할 때

파일이 너무 심하게 손상되어 **Tolerant** 모드조차 조각을 맞출 수 없는 경우(예: 핵심 XML 누락) 다음을 시도할 수 있습니다:

1. **`RecoveryMode.Strict`로 두 번째 로드**를 시도해 오류 메시지에서 추가 정보를 얻습니다.
2. **zip 유틸리티**를 사용해 XML 파트를 수동으로 추출하고 복구합니다.
3. **예외를 로그**하고 사용자가 문서를 복구할 수 없음을 알립니다.

```java
try {
    loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
    Document doc = new Document(filePath, loadOptions);
    // proceed with doc
} catch (Exception e) {
    System.err.println("Tolerant mode failed: " + e.getMessage());
    // optional: retry with Strict or alert the user
}
```

### 4.2 메모리 고려사항

복구를 활성화한 상태로 대용량 DOCX 파일을 로드하면 Aspose.Words가 원본과 복구된 구조를 모두 메모리에 보관하기 때문에 일시적으로 메모리 사용량이 두 배가 될 수 있습니다. 대량 배치를 처리할 때는:

- **같은 `LoadOptions` 인스턴스 재사용** 대신 매번 새로 만들지 않기
- **`Document`를 즉시 해제** (`doc.close()`)하기
- **충분한 힙을 가진 JVM**에서 실행 (`-Xmx2g` 이상, 멀티 기가바이트 파일 기준)

### 4.3 복구된 파일 저장

로드가 성공하면 **정리된 버전을 저장**해 두어 다음에 복구 과정을 다시 거치지 않도록 할 수 있습니다.

```java
String repairedPath = "C:/Documents/repaired.docx";
doc.save(repairedPath);
System.out.println("Repaired file saved to: " + repairedPath);
```

이제 `repaired.docx`를 열 때 **복구 모드 사용** 단계를 완전히 건너뛸 수 있습니다.

## Frequently Asked Questions

**Q: 오래된 `.doc` 파일에도 적용되나요?**  
A: 네. 동일한 `LoadOptions` 접근 방식이 `.doc`와 `.rtf`에도 적용됩니다. 파일 확장자만 바꾸면 됩니다.

**Q: `setRecoveryMode`를 다른 로드 옵션(예: 비밀번호)과 함께 사용할 수 있나요?**  
A: 물론입니다. `LoadOptions`에는 `setPassword`와 `setLoadFormat` 같은 속성이 있습니다. `setRecoveryMode`를 호출하기 전에 이들을 설정하면 됩니다.

**Q: 성능에 영향을 주나요?**  
A: 약간 있습니다—복구 과정이 파싱 오버헤드를 추가합니다. 벤치마크에 따르면 5 MB 손상 파일을 **Tolerant** 모드로 로드하면 깨끗한 파일을 Strict 모드로 로드할 때보다 약 30 % 느립니다. 대부분의 배치 작업에서는 여전히 허용 가능한 수준입니다.

## Full Working Example

아래는 **docx 열기**, **복구 모드 사용**, **복구된 사본 저장**을 보여주는 완전한 실행 가능한 Java 클래스입니다.

```java
package com.example.recovery;

import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        // Path to the possibly corrupted DOCX
        String inputPath = "C:/Documents/corrupted.docx";
        // Where the repaired file will be saved
        String outputPath = "C:/Documents/repaired.docx";

        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose recovery mode – Tolerant is usually enough
        loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
        // If you need strict validation, switch to RecoveryMode.Strict

        try {
            // 3️⃣ Load the document with the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Quick sanity check
            if (doc.getSections().getCount() > 0) {
                System.out.println("✅ Document loaded – recovery succeeded.");
            } else {
                System.out.println("⚠️ No sections found – the file may be beyond repair.");
            }

            // 4️⃣ (Optional) Save a clean copy for future use
            doc.save(outputPath);
            System.out.println("💾 Repaired file saved to: " + outputPath);
        } catch (Exception e) {
            // Handle cases where even tolerant mode fails
            System.err.println("❌ Failed to load document: " + e.getMessage());
            // You could retry with Strict or log for further analysis
        }
    }
}
```

프로젝트 클래스패스에 Aspose.Words for Java JAR를 추가한 뒤 이 클래스를 실행하세요. 입력 파일이 약간만 손상된 경우 **✅** 메시지와 함께 새 `repaired.docx` 파일이 디스크에 생성됩니다.

## Conclusion

Java에서 **복구 모드 설정**과 손상된 Word 파일을 성공적으로 **열기** 위해 필요한 모든 것을 다루었습니다. `LoadOptions` 객체를 만들고, 적절한 `RecoveryMode`를 선택하고, 가끔 발생하는 엣지 케이스를 처리함으로써 “파일이 열리지 않는다”는 좌절을 원활한 복구 워크플로우로 바꿀 수 있습니다.

기억하세요:

- 대부분의 *손상된 Word 복구* 시나리오에는 **Tolerant**가 기본 선택입니다.  
- 절대적인 확신이 필요할 때는 **Strict**를 사용해 즉시 실패하도록 합니다.  
- 로드된 문서를 항상 검증하고, 가능하면 향후 사용을 위해 정리된 사본을 저장하세요.

이제 “**로드되지 않는 docx**를 어떻게 열까?”라는 질문에 구체적인 코드 스니펫과 명확한 설명으로 자신 있게 답변할 수 있습니다. 즐거운 코딩 되시고, 문서가 항상 건강하길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}