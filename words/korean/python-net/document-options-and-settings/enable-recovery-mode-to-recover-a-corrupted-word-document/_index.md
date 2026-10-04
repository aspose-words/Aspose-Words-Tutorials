---
category: general
date: 2026-10-04
description: Aspose.Words에서 복구 모드를 활성화하여 손상된 Word 문서를 안전하게 복구하십시오. 전체 Python 코드와 설명이
  포함된 단계별 가이드를 따라 보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: ko
lastmod: 2026-10-04
og_description: Aspose.Words를 사용하여 손상된 Word 문서를 복구하려면 복구 모드를 활성화하십시오. 이 튜토리얼에서는 정확한
  Python 코드, 작동 원리 및 엣지 케이스 처리 방법을 보여줍니다.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: 손상된 Word 문서를 복구하기 위해 복구 모드 활성화 – 전체 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: 손상된 Word 문서를 복구하기 위해 복구 모드를 활성화하십시오
url: /ko/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 복구 모드를 활성화하여 손상된 Word 문서 복구

Word 파일을 로드할 때 **복구 모드를 활성화**해야 하는 경우, 이 가이드는 Aspose.Words for Python을 사용하여 정확히 수행하는 방법을 보여줍니다. 복구 모드를 켜면 예외가 발생할 수 있는 **손상된 Word 문서**를 **복구**할 수 있습니다.

다음 섹션에서는 다음을 배웁니다:

* 복구 동작을 제어하는 클래스와 속성.  
* 애플리케이션이 충돌하지 않도록 잠재적으로 손상된 `.docx` 파일을 로드하는 방법.  
* 일반적인 로드 문제를 해결하고 복구 전략을 사용자 정의하는 팁.

> **Prerequisite** – Aspose.Words for Python이 설치되어 있어야 합니다 (`pip install aspose-words`) 그리고 Python 파일 I/O에 대한 기본적인 이해가 필요합니다.

## 복구 모드가 하는 일과 활성화해야 하는 이유

Aspose.Words는 Word 파일의 내부 구조를 파싱한 뒤 `Document` 객체로 노출합니다. 파일이 손상된 경우(누락된 부분, 깨진 XML, 잘못된 관계) 파서는 다음 두 가지 중 하나를 수행할 수 있습니다:

| Mode | Behaviour |
|------|------------|
| `STRICT` | 손상이 감지되는 즉시 예외를 발생시킵니다. |
| `IGNORE_ERRORS` | 읽을 수 없는 부분을 건너뛰지만 내용이 조용히 손실될 수 있습니다. |
| `RECOVER` ( **복구 모드 활성화** 옵션) | 가능한 한 많은 내용을 보존하면서 문서를 재구성하려 시도하며, 선택된 모드는 `load_options.recovery_mode`를 통해 노출됩니다. |

`RECOVER`는 **손상된 Word 문서**를 텍스트 추출이나 PDF 변환과 같은 후속 처리에 사용해야 할 때 권장되는 선택입니다.

## 단계 1: LoadOptions 생성 및 복구 모드 활성화

첫 번째 단계는 `LoadOptions`를 인스턴스화하고 `recovery_mode` 속성을 `RecoveryMode.RECOVER`로 설정하는 것입니다. 이렇게 하면 파싱 중에 라이브러리가 복구 경로로 들어가게 됩니다.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**왜 중요한가:**  
이 단계를 건너뛰고 문서가 손상된 경우, 생성자 `aw.Document(...)`가 `InvalidOperationException`을 발생시킵니다. 복구 모드를 활성화하면 충돌을 방지하고 여전히 작업할 수 있는 부분적으로 복구된 `Document` 객체를 얻을 수 있습니다.

## 단계 2: 지정된 옵션으로 잠재적으로 손상된 문서 로드

`load_options` 인스턴스를 `Document` 생성자에 전달합니다. 로더는 이제 복구 알고리즘을 자동으로 적용합니다.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**팁:** `YOUR_DIRECTORY`를 런타임에서 접근 가능한 절대 경로나 상대 경로로 교체하십시오. 파일이 존재하지 않으면 Aspose.Words가 복구 로직에 도달하기 전에 `FileNotFoundError`를 발생시킵니다.

## 단계 3: 복구 모드가 적용되었는지 확인

`load_options.recovery_mode`를 검사하여 현재 모드를 확인할 수 있습니다. 이는 로깅이나 파이프라인 후속 단계에서 조건부 처리를 할 때 유용합니다.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**예상 출력**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

출력에 `RECOVER`가 표시되면 **복구 모드가 성공적으로 활성화**된 것이며, 이제 문서를 추가 처리(예: 텍스트 추출, PDF 변환 또는 복구된 복사본 저장)할 준비가 된 것입니다.

## 단계 4 (선택): 향후 사용을 위해 복구된 사본 저장

로드 후 복구된 문서를 지속적으로 보관하면 복구 단계를 반복할 필요가 없습니다.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

저장은 Aspose.Words가 유효하다고 판단하는 새로운 `.docx` 파일을 생성하며, Microsoft Word에서 경고 없이 열 수 있습니다.

## 일반적인 질문 및 엣지 케이스 처리

| Question | Answer |
|----------|--------|
| **문서를 완전히 읽을 수 없는 경우는?** | `RECOVER` 모드에서도 복구할 수 없는 파일이 있습니다. `Document` 객체는 생성되지만 단일 빈 페이지만 포함될 수 있습니다. `doc.get_page_count()`로 내용을 확인하십시오. |
| **로드 후 `IGNORE_ERRORS` 로 전환할 수 있나요?** | 아니요. 복구 모드는 `Document` 생성자가 실행되기 **이전**에 설정되어야 합니다. 다른 전략이 필요하면 새로운 `LoadOptions` 인스턴스를 만들어야 합니다. |
| **복구 모드가 성능에 영향을 줍니까?** | 예, 깨진 부분을 재구성하려고 시도하기 때문에 약간의 오버헤드가 발생합니다. 대부분의 파일(< 2 MB)에서는 영향이 미미합니다. |
| **이 접근 방식은 언어에 구애받지 않나요?** | 동일한 개념이 .NET, Java, Node.js API(`LoadOptions.RecoveryMode`)에도 존재합니다. 코드 문법은 다르지만 로직은 동일합니다. |

## 전문가 팁: 상세 복구 정보 로깅

Aspose.Words는 각 복구 단계에 대한 상세 메시지를 전달하는 `LoadOptions.recovery_callback`을 제공합니다. 이를 연결하면 특정 문서가 실패한 이유를 진단하는 데 도움이 됩니다.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

이제 “Removed duplicate relationship”와 같은 내부 수정 사항이 콘솔에 출력됩니다.

## 전체 실행 가능한 예제

모든 요소를 합친 자체 포함 스크립트는 다음과 같습니다. 복사‑붙여넣기 후 바로 실행할 수 있습니다:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

스크립트를 실행하면 복구 모드, 페이지 수, 복구된 문서에서 추출된 단어 목록이 출력됩니다. `save_repaired=True`로 설정하면 원본 옆에 새 깨끗한 파일이 생성됩니다.

## 결론

이제 Aspose.Words for Python에서 **복구 모드를 활성화**하고 **손상된 Word 문서**를 안정적으로 **복구**하는 방법을 알게 되었습니다. 핵심 단계는 다음과 같습니다:

1. `LoadOptions`를 생성하고 `recovery_mode`를 `RECOVER`로 설정.  
2. 해당 옵션으로 `.docx`를 로드.  
3. 모드를 확인하고 필요 시 복구된 사본을 저장.

이후에는 **복구된 문서에서 텍스트 추출**, **PDF 변환**, 혹은 **대규모 문서 라이브러리의 배치 복구**와 같은 추가 주제를 탐색할 수 있습니다.

---


## 다음에 배워야 할 내용은?


다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 포함하여 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있도록 돕습니다.

- [Recover Corrupted DOCX – Complete Guide to Enable Recovery Mode & Get Page](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}