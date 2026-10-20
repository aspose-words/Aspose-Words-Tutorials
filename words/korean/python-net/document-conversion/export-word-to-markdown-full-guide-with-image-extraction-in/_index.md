---
category: general
date: 2026-06-21
description: Python을 사용하여 Word를 Markdown으로 내보내고 Word에서 이미지를 저장합니다. docx를 markdown으로
  변환하고, 파이썬으로 바이너리 파일을 작성하며, docx에서 이미지를 추출하는 방법을 배워보세요.
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- save images from word
- write binary file python
- how to extract images from docx
language: ko
og_description: Word를 Markdown으로 내보내고 Word에서 이미지를 자동으로 저장합니다. 이 단계별 가이드는 docx를 markdown으로
  변환하고, 파이썬으로 바이너리 파일을 작성하며, docx에서 이미지를 추출하는 방법을 보여줍니다.
og_title: 워드에서 마크다운으로 내보내기 – 완전한 파이썬 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  headline: Export Word to Markdown – Full Guide with Image Extraction in Python
  type: TechArticle
- description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  name: Export Word to Markdown – Full Guide with Image Extraction in Python
  steps:
  - name: Expected Output Example
    text: 'If `input.docx` contained a single picture named `image1.png`, the resulting
      `output.md` might look like:'
  - name: What if the document has duplicate image names?
    text: 'Aspose.Words will suggest the same name for identical images. Our callback
      uses the suggested name directly, which could cause overwrites. To avoid that,
      modify the callback to append a unique identifier:'
  - name: Can I change the image format during extraction?
    text: Absolutely. After writing the binary data, you could open it with Pillow
      (`PIL.Image`) and save it as a different format (e.g., JPEG). This is useful
      when you need to **convert docx to markdown** for a web‑optimized site.
  - name: Does this work on macOS/Linux as well as Windows?
    text: Yes. The code uses `os.path` and avoids hard‑coded path separators, so it’s
      cross‑platform. Just remember to grant the script write permissions to the target
      directory.
  - name: What if I need to export tables or footnotes too?
    text: '`MarkdownSaveOptions` supports a range of features—tables become markdown
      tables, footnotes become inline references. No extra code is required; just
      experiment with the generated markdown to see how it renders.'
  type: HowTo
tags:
- python
- docx
- markdown
- image-extraction
title: Word를 Markdown으로 내보내기 – 파이썬을 이용한 이미지 추출 포함 전체 가이드
url: /ko/python/document-conversion/export-word-to-markdown-full-guide-with-image-extraction-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 내보내기 – 이미지 추출까지 포함한 파이썬 전체 가이드

Word 문서에 삽입된 그림을 잃지 않고 **Word를 markdown으로 내보내는** 방법이 궁금하신가요? 여러분만 그런 것이 아닙니다—개발자들은 `.docx`를 깔끔한 markdown으로 변환하면서 모든 이미지를 그대로 유지할 수 있는 간편한 방법을 지속적으로 찾고 있습니다.  

이 튜토리얼에서는 **docx를 markdown으로 변환**하고 **Word 파일에서 이미지를 저장**하는 완전한 솔루션을 파이썬으로 구현하는 과정을 단계별로 안내합니다. 최종적으로 바이너리 파일을 파이썬 방식으로 쓰고 필요한 모든 그림을 추출하는 실행 가능한 스크립트를 얻게 됩니다.

## 이 가이드에서 다루는 내용

- 올바른 라이브러리 설치 (Aspose.Words for Python)  
- 바이너리 데이터를 디스크에 쓰는 콜백 정의  
- 이미지 처리를 포함한 Word 문서의 markdown 변환  
- 출력 결과 확인 및 흔히 발생하는 문제 해결  

외부 서비스 없이, 수동 복사‑붙여넣기 없이—단일, 독립형 스크립트 하나만 있으면 어떤 프로젝트에도 바로 적용할 수 있습니다.

## 사전 준비 사항

시작하기 전에 아래 항목을 확인하세요:

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | 최신 문법 및 타입 힌트 지원 |
| `pip` access | Aspose.Words 패키지 설치용 |
| Write permission to a folder | 콜백이 **write binary file python** 스타일로 파일을 기록합니다 |
| 이미지가 포함된 `.docx` 파일 | **save images from word** 기능을 직접 확인하기 위함 |

이 중 익숙하지 않은 것이 있더라도 걱정 마세요—다음 단계에서 설정 방법을 알려드리겠습니다.

## Step 1: Aspose.Words for Python을 pip로 설치

Aspose.Words는 임베디드 미디어를 포함한 전체 Word 문서 포맷을 이해하는 강력한 라이브러리입니다. 한 줄 명령으로 설치하세요:

```bash
pip install aspose-words
```

> **Pro tip:** 가상 환경(`python -m venv venv`)을 사용하면 의존성을 깔끔하게 관리할 수 있습니다. 다른 프로젝트와의 버전 충돌도 방지됩니다.

## Step 2: 리소스 저장 콜백 만들기 (Write Binary File Python)

솔루션의 핵심은 각 바이너리 리소스(예: 이미지)를 받아 저장 위치를 결정하는 콜백입니다. 여기서 **write binary file python** 스타일로 파일을 씁니다.

```python
def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save a binary resource (e.g., an image) to a custom folder and
    return the relative path for markdown linking.

    :param resource: Raw binary data of the resource.
    :param suggested_name: A filename suggested by Aspose.Words.
    :return: Relative path to be used in the markdown file.
    """
    # Build a relative path inside a custom folder.
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)          # Ensure the folder exists.
    file_path = os.path.join(folder, suggested_name)

    # Write the binary data to disk – classic write binary file python.
    with open(file_path, "wb") as f:
        f.write(resource)

    # Return the path so the Markdown writer can reference it.
    return file_path
```

**왜 콜백이 필요할까요?**  
Aspose.Words는 이미지가 어디에 저장될지 모릅니다. `my_resource_saver`를 제공하면 파일명, 폴더 구조, 심지어 이미지 압축 같은 후처리까지 완전히 제어할 수 있습니다.

## Step 3: 원본 Word 문서 로드

이제 변환하려는 `.docx` 파일을 라이브러리에 전달합니다.

```python
import aspose.words as aw
import os

# Adjust the path to your actual file location.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

파일을 찾을 수 없으면 경로를 다시 확인하고 스크립트에 읽기 권한이 있는지 점검하세요. Windows에서는 슬래시와 역슬래시 혼용이 흔한 실수인데, `os.path.join`이 이를 자동으로 처리합니다.

## Step 4: Markdown 저장 옵션 설정 및 콜백 연결

이 단계에서 모든 것이 연결됩니다. Aspose.Words에 markdown을 출력 포맷으로 지정하고 이미지가 발견될 때마다 `my_resource_saver`를 호출하도록 합니다.

```python
# Create Markdown save options.
md_save = aw.saving.MarkdownSaveOptions()

# Attach the resource‑saving callback.
md_save.resource_saving_callback = my_resource_saver
```

여기서 markdown 출력을 세부 조정할 수 있습니다(예: `md_save.export_images_as_base64 = False` 로 이미지 삽입 방식을 변경). **docx에서 이미지 추출** 목적이라면 별도 파일로 저장하는 것이 보통 더 깔끔합니다.

## Step 5: 문서 내보내기 – 최종 Export Word to Markdown 호출

이제 무거운 작업을 수행하는 한 줄 코드만 남았습니다.

```python
output_md = "YOUR_DIRECTORY/output.md"
doc.save(output_md, md_save)
print(f"✅ Markdown saved to {output_md}")
print(f"🖼️ Images stored in ./custom_images/")
```

스크립트를 실행하면 `output.md` 파일과 함께 `custom_images` 폴더가 생성되고, 원본 Word 파일에 있던 모든 그림이 들어갑니다. markdown은 상대 경로로 이미지를 참조하므로 정적 사이트 생성기나 GitHub 렌더링에 바로 사용할 수 있습니다.

### 기대 출력 예시

`input.docx`에 `image1.png`라는 그림 하나만 들어 있었다면, 생성된 `output.md`는 다음과 비슷할 것입니다:

```markdown
# Sample Document

Here is an illustration:

![image1.png](custom_images/image1.png)

More text follows...
```

그리고 폴더 구조는 다음과 같습니다:

```
/YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ custom_images/
   └─ image1.png
```

## 흔히 묻는 질문 및 예외 상황

### 문서에 중복된 이미지 이름이 있을 경우?

Aspose.Words는 동일한 이미지에 대해 같은 이름을 제안합니다. 콜백이 제안된 이름을 그대로 사용하면 파일이 덮어써질 수 있습니다. 이를 방지하려면 콜백에 고유 식별자를 추가하도록 수정하세요:

```python
import uuid

def my_resource_saver(resource, suggested_name):
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    # rest of the code unchanged...
```

### 추출 중에 이미지 포맷을 바꿀 수 있나요?

가능합니다. 바이너리 데이터를 쓴 뒤 Pillow(`PIL.Image`)로 열어 JPEG 등 다른 포맷으로 저장하면 됩니다. 이는 **docx를 markdown으로 변환**하면서 웹에 최적화된 이미지를 원할 때 유용합니다.

### macOS/Linux에서도 동일하게 동작하나요?

네. 코드가 `os.path`를 사용하고 경로 구분자를 하드코딩하지 않으므로 크로스 플랫폼입니다. 대상 디렉터리에 쓰기 권한만 부여하면 됩니다.

### 표나 각주도 내보내고 싶다면?

`MarkdownSaveOptions`는 다양한 기능을 지원합니다—표는 markdown 표로, 각주는 인라인 참조로 변환됩니다. 별도 코딩 없이 옵션만 조정하면 됩니다. 생성된 markdown을 확인하면서 원하는 형태로 렌더링되는지 실험해 보세요.

## 전체 스크립트 – 복사·붙여넣기 바로 가능

아래는 지금까지 설명한 모든 내용을 포함한 완전 실행 예제입니다. `export_word_to_md.py`라는 파일명으로 저장하고 `python export_word_to_md.py`를 실행하세요.

```python
import os
import uuid
import aspose.words as aw

def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save binary resources (images) to a custom folder and return
    the relative path for markdown references.
    """
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)

    # Ensure unique filenames to avoid collisions.
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    file_path = os.path.join(folder, unique_name)

    with open(file_path, "wb") as f:
        f.write(resource)

    return file_path

def main():
    # ------------------------------------------------------------------
    # 1️⃣ Load the Word document you want to convert.
    # ------------------------------------------------------------------
    doc_path = "YOUR_DIRECTORY/input.docx"
    if not os.path.isfile(doc_path):
        raise FileNotFoundError(f"❌ {doc_path} does not exist.")
    doc = aw.Document(doc_path)

    # ------------------------------------------------------------------
    # 2️⃣ Set up markdown options and plug in the image callback.
    # ------------------------------------------------------------------
    md_save = aw.saving.MarkdownSaveOptions()
    md_save.resource_saving_callback = my_resource_saver

    # ------------------------------------------------------------------
    # 3️⃣ Perform the export – this is the core **export word to markdown** step.
    # ------------------------------------------------------------------
    output_md = "YOUR_DIRECTORY/output.md"
    doc.save(output_md, md_save)

    print(f"✅ Markdown exported to: {output_md}")
    print(f"🖼️ Extracted images are in the folder: ./custom_images/")

if __name__ == "__main__":
    main()
```

실행 후 `output.md`를 어떤 markdown 뷰어에서 열어 보면 원본 Word 내용—텍스트, 헤딩, **save images from word**, 그리고 모든 요소—가 충실히 재현된 것을 확인할 수 있습니다.

## 결론

우리는 **word를 markdown으로 내보내면서** 모든 삽입 그림을 보존하는 견고한 방법을 보여주었습니다. Aspose.Words와 맞춤형 **resource‑saving 콜백**을 활용하면 **docx를 markdown으로 변환**, **write binary file python**, 그리고 고전적인 **docx에서 이미지 추출** 질문을 하나의 재사용 가능한 스크립트로 해결할 수 있습니다.

다음 단계는? Pillow를 이용해 이미지 압축을 추가하거나, CI 파이프라인에 통합해 문서를 자동으로 정적 사이트용 markdown으로 변환해 보세요. 가능성은 무궁무진하며, 이제 탄탄한 기반을 갖추었습니다.

피드백이나 문제 발생 시 아래에 댓글을 남겨 주세요—행복한 코딩 되세요!

## 다음에 배울 내용은?


아래 튜토리얼들은 이번 가이드에서 다룬 기술을 확장하여 추가 API 기능을 마스터하고, 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다. 각각 완전한 코드 예제와 단계별 설명을 포함하고 있습니다.

- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Recover Corrupted DOCX & Convert Word to Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)
- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}