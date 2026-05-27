---
category: general
date: 2026-05-26
description: Aspose.Words를 사용하여 Java에서 손상된 Word 문서를 엽니다. 복구 모드를 설정하고 손상된 Word 파일을
  신뢰성 있게 복구하는 방법을 배워보세요.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: ko
og_description: Aspose.Words를 사용하여 Java에서 손상된 Word 문서를 엽니다. 이 가이드는 복구 모드를 설정하고 손상된
  Word 파일을 효율적으로 복구하는 방법을 보여줍니다.
og_title: 손상된 워드 문서 열기 – Java에서 복구 모드 설정
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: 손상된 워드 문서 열기 – Java에서 복구 모드 설정
url: /ko/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 손상된 Word 문서 열기 – Java에서 복구 모드 설정

손상된 Word 문서를 열어보고 프로그램이 예외로 중단되는 것을 본 적이 있나요? 당신만 그런 것이 아닙니다—그런 .docx 파일은 정말 골칫거리일 수 있습니다. 좋은 소식은 Aspose.Words for Java가 세밀한 제어를 제공하여 **open corrupted word document** 없이 앱이 충돌하지 않게 하고, 경고를 표시할지, 조용히 복구할지, 혹은 강제 거부할지를 결정할 수 있다는 것입니다.

이 튜토리얼에서는 전체 과정을 단계별로 살펴보겠습니다: 올바른 `LoadOptions` 생성, 적절한 **set recovery mode** 값 선택, 그리고 문서가 실제로 로드되었는지 확인합니다. 마지막까지 진행하면 **how to recover corrupted word file**을 프로그래밍 방식으로 수행하는 방법을 알게 되며, 수동 복사‑붙여넣기는 필요하지 않습니다.

> **필요한 사항**  
> * Java 8 이상 (API는 Java 11 에서도 작동)  
> * Aspose.Words for Java 23.9 (또는 최신 버전)  
> * 샘플 손상된 .docx 파일 — 손상된 파일이 없으면 유효한 파일을 이름만 바꿔서 시뮬레이션할 수 있습니다  

시작해 보겠습니다.

## 손상된 Word 문서 열기 – 단계별 개요

아래는 구현할 고수준 흐름입니다:

1. **Create `LoadOptions`** – 이 객체는 Aspose.Words가 문제를 만나면 어떻게 행동할지를 알려줍니다.  
2. **Set recovery mode** – `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS`, 또는 `REJECT_CORRUPTED` 중 하나를 선택합니다.  
3. **Load the document** using the configured options.  
4. **Verify** the load succeeded (예: 페이지 수 출력).  

각 단계는 자세히 설명되며, IDE에 바로 복사‑붙여넣기 할 수 있는 코드 스니펫이 포함됩니다.

## 다양한 시나리오를 위한 복구 모드 설정

Aspose.Words는 `LoadOptions.RecoveryMode` 안에 세 가지 복구 전략을 정의합니다:

| 모드 | 동작 | 사용 시기 |
|------|-----------|-------------|
| `RECOVER_WITH_WARNINGS` | 문서를 로드하려 시도하지만, 발생한 문제를 콘솔에 경고로 표시합니다. | 중단 없이 *무엇이* 잘못됐는지 보고 싶을 때 |
| `RECOVER_WITHOUT_WARNINGS` | 가능한 부분을 조용히 복구하고 경고를 억제합니다. | 로그를 깔끔하게 유지해야 하는 프로덕션 환경 |
| `REJECT_CORRUPTED` | 손상이 감지되는 즉시 예외를 발생시킵니다. | 빠르게 실패해야 하는 엄격한 검증 파이프라인 |

올바른 모드를 선택하는 것이 **set recovery mode**를 정확히 설정하는 핵심입니다. 대부분의 디버깅 세션에서는 `RECOVER_WITH_WARNINGS`가 최적이며, 어떤 부분이 복구되었는지 정확히 알려줍니다.

## Aspose.Words를 사용하여 손상된 Word 파일 복구하기

아래는 전체 실행 가능한 Java 프로그램 **전체 실행 가능한 Java 프로그램**의 예시입니다. `RecoveryModeDemo.java` 파일에 붙여넣고, 경로만 조정한 뒤 실행해 보세요.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### 각 라인의 의미

* **`LoadOptions loadOptions = new LoadOptions();`** – 이 객체가 없으면 Aspose.Words는 기본 복구 방식을 사용해 손상된 파일을 *거부*합니다. 객체를 생성하면 동작을 변경할 수 있는 후크가 생깁니다.
* **`setRecoveryMode(...)`** – 경고를 표시할지, 숨길지, 혹은 예외를 발생시킬지를 결정하는 **set recovery mode** 호출입니다.
* **`new Document(path, loadOptions);`** – 생성자는 방금 설정한 `LoadOptions`를 받아들여, 라이브러리가 처음부터 손상된 파일을 어떻게 처리할지 알게 됩니다.
* **`doc.getPageCount()`** – 간단한 정상 확인. 문서가 로드되고 페이지 수가 반환되면 **how to recover corrupted word file**에 성공한 것입니다.
* **`doc.save(...)`** – 선택 사항이지만 유용합니다; 복구된 버전을 디스크에 저장해 나중에 사용할 수 있습니다.

## 일반적인 엣지 케이스 처리

### 1. 파일을 찾을 수 없음

경로가 잘못되면 `Document`가 `FileNotFoundException`을 발생시킵니다. 로드를 try‑catch 블록으로 감싸고 친절한 메시지를 로그에 남기세요:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. 복구 불가능한 손상

`RECOVER_WITH_WARNINGS`를 사용하더라도 일부 구조는 복구할 수 없습니다. 이 경우 Aspose.Words는 가능한 부분만 로드하지만 “Cannot read paragraph properties”와 같은 경고가 콘솔에 표시됩니다. 이러한 경고는 누락된 섹션을 수동으로 재구성해야 할 가능성을 알려줍니다.

### 3. 대용량 파일 및 성능

복구 과정은 파일을 두 번 파싱하기 때문에 약간의 오버헤드가 발생합니다—한 번은 문제를 감지하고, 다시 한 번은 재구성합니다. 수기가바이트 규모의 문서라면 파일 스트리밍을 고려하거나 JVM 힙을 (`-Xmx2g`) 늘려 `OutOfMemoryError`를 방지하세요.

## 전문가 팁 – 복구를 견고하게 만들기

* **경고를 파일에 기록** – `System.err`를 로거로 리다이렉트해 어떤 부분이 수정됐는지 감사 로그를 남깁니다.  
* **복구 후 검증** – `doc.updatePageLayout();`을 실행한 뒤 페이지 수를 다시 확인합니다; 깨진 섹션을 고친 뒤 레이아웃이 변경될 수 있습니다.  
* **배치 복구 자동화** – 데모 코드를 루프로 감싸 폴더에 있는 손상된 파일들을 한 번에 처리하고, 매번 동일한 `LoadOptions`를 재사용합니다.

## 결론

이제 Aspose.Words for Java를 사용해 **how to recover corrupted word file**을 정확히 수행하는 방법을 알게 되었습니다. `LoadOptions` 인스턴스를 만들고, 상황에 맞는 **set recovery mode**를 설정한 뒤 해당 옵션으로 문서를 로드하면 애플리케이션이 중단되지 않고 **open corrupted word document**를 열 수 있습니다. 위 샘플 코드는 페이지 수를 출력하고 정리된 복사본을 저장하는 완전한 실행 가능한 솔루션입니다.

다음은? 복구 모드를 `RECOVER_WITHOUT_WARNINGS`로 바꿔 콘솔 출력을 비교해 보거나, 암호화된 문서를 로드해 보는 실험을 해보세요(비밀번호는 ...

## 관련 튜토리얼

- [Aspose.Words Java: Word 문서 처리 종합 가이드](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Aspose.Words for Java를 사용하여 Word를 PDF로 변환하는 방법](/words/english/java/document-converting/using-document-converting/)
- [Aspose.Words for Java로 두 Word 파일 비교하는 방법](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}