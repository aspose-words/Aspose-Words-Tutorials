---
category: general
date: 2026-09-30
description: Aspose.Words를 사용하여 손상된 Word 문서를 열기 위해 복구 모드를 활성화하십시오. 손상된 docx 파일을 안전하고
  신뢰할 수 있게 복구하는 방법을 알아보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: ko
lastmod: 2026-09-30
og_description: Aspose.Words를 사용하여 손상된 Word 문서를 열기 위해 복구 모드를 활성화하십시오. 이 가이드는 손상된 docx
  파일을 복구하고 작업 흐름을 안정적으로 유지하는 방법을 단계별로 보여줍니다.
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: 복구 모드를 활성화하여 손상된 Word 문서 열기
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: 복구 모드를 활성화하여 손상된 Word 문서 열기
url: /ko/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 손상된 Word 문서를 열기 위해 복구 모드 활성화

손상된 Word 문서를 열 때 **복구 모드 활성화**가 필요하다면, 이 튜토리얼은 Aspose.Words for Python을 사용하여 정확히 수행하는 방법을 보여줍니다. 파일이 전송 중에 손상되었거나 호환되지 않는 프로그램으로 편집되었든, 복구 모드를 활성화하면 라이브러리가 예외를 발생시키는 대신 문서를 복구하려 시도합니다.

이 가이드에서는 **손상된 Word 문서 열기** 방법, **손상된 docx 복구** 방법을 배우고, **복구 모드로 문서 로드** 프로세스를 제어하는 옵션을 이해하게 됩니다. 단계는 Aspose.Words 23.10(작성 시 최신 릴리스)과 함께 작동하며 표준 Python 환경만 필요합니다.

## Prerequisites

시작하기 전에 다음이 설치되어 있는지 확인하십시오:

* Python 3.9 이상
* .NET용 Aspose.Words for Python (`aspose-words`) (`pip install aspose-words`) 설치
* 손상된 것으로 알려진 DOCX 파일(테스트용으로 유효한 `.docx` 파일을 `.zip`으로 이름을 바꾸고 XML을 수동으로 손상시켜도 됩니다)

> **Pro tip:** 원본 파일의 백업을 보관하십시오. 복구 모드는 메모리상의 문서를 수정하지만, 명시적으로 저장하지 않는 한 원본에 다시 쓰지 않습니다.

## Step 1: Import the library and create load options

먼저 `aspose.words`를 임포트하고 `LoadOptions` 객체를 인스턴스화해야 합니다. 이 객체는 파일을 읽는 방식을 제어하는 모든 설정을 보유합니다.

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*Why this matters:* `LoadOptions`는 파서의 세부 조정을 위한 관문입니다. 이를 사용하지 않으면 Aspose.Words는 기본 엄격 모드를 사용하여 구조적 오류가 발생하면 즉시 중단합니다.

## Step 2: Enable recovery mode

`recovery_mode` 속성을 `RecoveryMode.RECOVER`로 설정합니다. 이는 로더에게 누락된 XML 노드, 깨진 관계, 잘린 스트림 등 손상된 부분을 자동으로 복구하도록 지시합니다.

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

복구 모드를 활성화한다고 해서 완벽한 문서를 보장하는 것은 아니지만, 텍스트, 이미지 또는 표를 여전히 추출할 수 있는 가능성을 크게 높여줍니다.

## Step 3: Load the potentially corrupted DOCX with the configured options

이제 파일 경로와 `LoadOptions` 인스턴스를 모두 받아들이는 `Document` 생성자를 사용합니다.

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*Why this matters:* `try/except` 블록은 **손상된 docx를 안전하게 여는** 방법을 보여줍니다. 복구 모드가 없으면 동일한 호출이 즉시 예외를 발생시켜 프로그램이 중단됩니다.

## Step 4: Verify the recovered content (optional but recommended)

로드 후 문서에 의미 있는 내용이 포함되어 있는지 확인해야 합니다. 간단한 방법은 순수 텍스트를 추출하고 처음 몇 글자를 출력하는 것입니다.

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

출력이 합리적인 미리보기를 보여주면 문서를 계속 처리할 수 있습니다(예: PDF로 변환, 표 추출 등). 텍스트가 비어 있으면 파일이 복구 불가능할 수 있으므로 새 사본을 요청해야 할 수 있습니다.

## Step 5: Save the repaired document (if you want a clean copy)

복구된 내용에 만족한다면 새롭고 깨끗한 DOCX를 저장할 수 있습니다. 이 단계는 선택 사항이지만 다운스트림 워크플로에 종종 유용합니다.

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

저장은 복구 모드를 트리거한 손상이 더 이상 포함되지 않은 새로운 파일을 생성합니다.

## Edge cases and additional tips

| Situation                               | Recommended approach |
|----------------------------------------|----------------------|
| **File is not a DOCX** (e.g., `.doc`) | 로드하기 전에 `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC` 사용. |
| **Partial recovery only**              | 로드 후 `document.get_text()`와 `document.get_page_count()`를 검사합니다. 페이지 수가 0이면 문서를 복구할 수 없을 수 있습니다. |
| **Large documents**                    | 복구 중 RAM 사용량을 줄이려면 `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE`를 활성화합니다. |
| **Need to log what was repaired**      | `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER`를 설정하고, (가능하면) `document.get_last_save_options().recovery_log`를 읽어 상세 정보를 확인합니다. |

> **Watch out for:** 복구 모드는 지원되지 않는 요소(예: 누락된 글꼴)를 조용히 제거할 수 있습니다. 시각적 정확성이 중요한 경우 복구된 파일을 알려진 정상 버전과 비교하십시오.

## Full working example

모든 내용을 하나로 합치면 바로 실행할 수 있는 독립형 스크립트는 다음과 같습니다:

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

스크립트를 실행하면 성공 메시지와 짧은 텍스트 발췌가 출력되고, 동일한 폴더에 `repaired.docx`가 생성됩니다.

## Conclusion

이제 Aspose.Words for Python을 사용하여 **복구 모드 활성화**로 **손상된 Word 문서 열기**, **손상된 docx 복구**, 그리고 안전하게 **복구 모드로 문서 로드**하는 방법을 알게 되었습니다. `LoadOptions` 생성, `RecoveryMode.RECOVER` 활성화, 예외 처리라는 핵심 단계는 모든 자동화 파이프라인에서 재사용 가능한 신뢰할 수 있는 패턴을 형성합니다.

다음으로 **복구된 문서를 PDF로 변환**, **`DocumentVisitor`로 표 추출**, 혹은 **손상된 파일 폴더를 일괄 처리**와 같은 관련 주제를 탐색해 보세요. 모두 여기서 시연한 복구 모드 기반을 토대로 구축됩니다.

Happy coding, and may your documents stay healthy!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [docx 복구 방법 – 복구 모드 설정 및 손상된 Word 파일 열기](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Aspose.Words로 손상된 docx 복구 – 복구 모드 및 로드 옵션 설정](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Aspose.Words LoadOptions로 손상된 DOCX 복구 – 완전한 C# 가이드](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}