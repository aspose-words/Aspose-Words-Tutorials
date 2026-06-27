---
category: general
date: 2026-06-27
description: Python을 사용하여 docx를 markdown으로 변환합니다. Word에서 이미지를 추출하고 사용자 정의 콜백으로 markdown
  출력을 저장하는 방법을 배웁니다.
draft: false
keywords:
- convert docx to markdown
- extract images from word
- convert word to markdown
- python docx to markdown
- save markdown output
language: ko
og_description: Python에서 docx를 markdown으로 변환하고, Word에서 이미지를 추출하며, 사용자 정의 리소스 콜백을 사용해
  markdown 출력을 저장합니다.
og_title: docx를 markdown으로 변환 – 이미지 추출이 포함된 파이썬 가이드
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  headline: Convert docx to markdown – Complete Python Guide with Image Extraction
  type: TechArticle
- description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  name: Convert docx to markdown – Complete Python Guide with Image Extraction
  steps:
  - name: Expected Output
    text: '```markdown # Sample Document'
  - name: Quick sanity check
    text: '```bash # On Unix/macOS cat YOUR_DIRECTORY/output.md ls YOUR_DIRECTORY/images/
      ```'
  - name: Dealing with duplicate image names
    text: 'Word sometimes reuses the same internal name for different pictures. To
      avoid overwriting, you can tweak `image_saver`:'
  - name: Converting large documents
    text: 'For multi‑megabyte documents, consider streaming the output to avoid memory
      spikes:'
  type: HowTo
tags:
- Python
- Aspose.Words
- Document Conversion
title: docx를 markdown으로 변환 – 이미지 추출을 포함한 파이썬 완전 가이드
url: /ko/python/document-conversion/convert-docx-to-markdown-complete-python-guide-with-image-ex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx를 markdown으로 변환 – 이미지 추출이 포함된 완전한 Python 가이드

Word 파일에 삽입된 그림을 잃지 않고 **docx를 markdown으로 변환**하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 변환 과정에서 이미지가 사라져 markdown에 깨진 링크가 남거나, 최악의 경우 이미지가 전혀 표시되지 않는 문제에 부딪히곤 합니다.  

좋은 소식은, 몇 줄의 Python 코드와 Aspose.Words만 있으면 `.docx` 파일을 깔끔한 markdown으로 **동시에** 모든 이미지를 원하는 폴더에 추출할 수 있다는 것입니다. 이번 튜토리얼에서는 라이브러리 설치부터 이미지 저장 콜백을 연결해 원하는 위치에 그림을 저장하는 전체 과정을 단계별로 살펴보겠습니다.

이 가이드를 끝까지 따라오면 **Word를 markdown으로 변환**하고, 모든 그래픽을 추출하며, 정적 사이트 생성기, 문서 파이프라인 또는 기타 markdown‑first 워크플로에 바로 사용할 수 있는 **markdown 출력**을 저장할 수 있게 됩니다.

## 준비 사항

- Python 3.8 이상 (코드는 3.9+에서도 동작)  
- `pip`를 이용한 서드파티 패키지 설치 권한  
- 유효한 Aspose.Words for Python 라이선스 (평가용 무료 체험 가능)  
- 텍스트와 최소 하나 이상의 이미지가 포함된 샘플 `input.docx`  

그 외에 별도의 무거운 Office 설치나 COM 연동이 필요하지 않습니다. 순수 Python만 있으면 됩니다.

## 1단계: Aspose.Words for Python 설치

먼저 라이브러리를 받아옵니다. 터미널을 열고 다음 명령을 실행하세요:

```bash
pip install aspose-words
```

권한 오류가 발생하면 `--user` 옵션을 앞에 붙이거나 가상 환경을 사용하세요. 설치가 완료되면 예제에서 `aw`로 임포트하는 `aspose.words` 패키지를 사용할 수 있게 됩니다.

> **Pro tip:** `requirements.txt`를 깔끔하게 관리하세요. `aspose-words==<latest-version>`을 추가하면 협업자가 정확히 같은 환경을 재현할 수 있습니다.

## 2단계: 커스텀 이미지 저장 콜백 설정

Aspose.Words는 *리소스 저장 콜백*을 통해 저장 파이프라인에 개입할 수 있습니다. 이는 각 이미지의 바이트 스트림을 받아 원하는 경로에 저장하도록 라이브러리에 알려주는 중간자 역할을 합니다.

콜백 핵심 코드는 다음과 같습니다:

```python
# Step 1: Define a callback to store extracted images in a custom folder
def image_saver(image_bytes, image_name):
    """
    Saves an image to YOUR_DIRECTORY/images/ and returns the relative path
    that will be placed in the markdown file.
    """
    # Ensure the target folder exists
    import os
    target_dir = os.path.join("YOUR_DIRECTORY", "images")
    os.makedirs(target_dir, exist_ok=True)

    # Build the full path on disk
    file_path = os.path.join(target_dir, image_name)

    # Write the raw image bytes to disk
    with open(file_path, "wb") as f:
        f.write(image_bytes)

    # Return the path that markdown will use (relative to the .md file)
    return os.path.join("images", image_name)
```

**이 콜백이 중요한 이유:**  
- **제어** – 폴더 구조, 파일명 규칙, 필요 시 이미지 포맷 변환까지 직접 지정할 수 있습니다.  
- **이식성** – 반환된 상대 경로 덕분에 `images` 폴더만 함께 이동하면 markdown이 어느 머신에서도 정상 동작합니다.  
- **성능** – 각 이미지당 한 번만 실행돼 중복 쓰기를 방지합니다.

## 3단계: Markdown 저장 옵션 구성

이제 `MarkdownSaveOptions` 객체에 콜백을 연결합니다. 이렇게 하면 Aspose.Words가 이미지 리소스를 만나면 자동으로 `image_saver`를 호출합니다.

```python
# Step 2: Create Markdown save options and attach the callback
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = image_saver
```

여기서 `export_images_as_base64`를 `False`(별도 파일로 저장)로 설정하거나, 필요에 따라 `add_table_of_contents` 같은 옵션을 추가로 조정할 수 있습니다. 이번 가이드에서는 기본값을 그대로 사용합니다.

## 4단계: 원본 Word 문서 로드

`.docx` 로드는 매우 간단합니다. 파일 경로만 지정하면 됩니다:

```python
# Step 3: Load the source Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

문서가 매우 크다면 `aw.LoadOptions`와 스트리밍 로드를 고려할 수 있지만, 대부분의 경우 기본 생성자로 충분합니다.

## 5단계: Markdown으로 저장 – 콜백이 모든 작업을 수행

이제 Aspose.Words에 markdown 파일 작성을 요청합니다. 라이브러리는 모든 삽입 그림에 대해 `image_saver`를 호출해 파일을 저장하고, 적절한 markdown 이미지 링크를 삽입합니다.

```python
# Step 4: Save the document as Markdown, letting the callback handle image resources
doc.save("YOUR_DIRECTORY/output.md", md_options)
```

프로세스가 끝나면 두 가지 결과를 확인할 수 있습니다:

1. `output.md` – `![](images/image1.png)` 와 같은 이미지 링크가 포함된 markdown 텍스트  
2. `images` 하위 폴더 – 추출된 각 그림 파일이 들어 있음

### 기대 출력

```markdown
# Sample Document

This is a paragraph from the Word file.

![](images/image1.png)

Another paragraph follows the picture.
```

`output.md`를 VS Code, GitHub, MkDocs 등任意의 markdown 뷰어에서 열면 원본 Word 파일에 있던 이미지가 그대로 표시됩니다.

## 6단계: 결과 검증 및 예외 상황 처리

### 간단한 정상 확인

```bash
# On Unix/macOS
cat YOUR_DIRECTORY/output.md
ls YOUR_DIRECTORY/images/
```

이미지 파일명이 markdown에 기록된 경로와 일치하는지 확인하세요. 이미지가 누락된 경우 콜백이 **절대 경로**가 아닌 **상대 경로**를 반환했는지, `images` 폴더가 올바르게 참조되는지 점검합니다.

### 중복 이미지 이름 처리

Word는 서로 다른 그림에 동일한 내부 이름을 사용할 때가 있습니다. 덮어쓰기를 방지하려면 `image_saver`를 다음과 같이 수정합니다:

```python
import uuid

def image_saver(image_bytes, image_name):
    unique_name = f"{uuid.uuid4().hex}_{image_name}"
    # rest of the code uses unique_name instead of image_name
    ...
    return os.path.join("images", unique_name)
```

### 대용량 문서 변환

수 MB 규모의 문서를 다룰 때는 메모리 급증을 피하기 위해 출력 스트리밍을 고려하세요:

```python
with open("YOUR_DIRECTORY/output.md", "w", encoding="utf-8") as out_file:
    doc.save(out_file, md_options)
```

Aspose.Words가 내부적으로 스트리밍을 지원하므로 전체 markdown을 메모리에 올릴 필요가 없습니다.

## 7단계: 워크플로 자동화 (선택)

여러 Word 파일을 한 폴더에서 일괄 처리하려면 로직을 루프 안에 넣습니다:

```python
import glob

for doc_path in glob.glob("YOUR_DIRECTORY/*.docx"):
    doc = aw.Document(doc_path)
    base_name = os.path.splitext(os.path.basename(doc_path))[0]
    md_path = f"YOUR_DIRECTORY/{base_name}.md"
    doc.save(md_path, md_options)
    print(f"Converted {doc_path} → {md_path}")
```

이제 `.docx` 파일을 100개 정도 폴더에 넣어두면 스크립트가 자동으로 각각을 변환하고, 각 파일마다 별도의 `images` 하위 폴더를 생성합니다.

## 결론

이번 튜토리얼을 통해 **docx를 markdown으로 변환**하면서 모든 이미지를 보존하는 방법을 완전한 Python 스크립트와 Aspose.Words의 강력한 콜백 메커니즘을 활용해 익혔습니다. 이제 다음을 할 수 있습니다:

- 커스텀 `resource_saving_callback`을 이용해 **Word에서 이미지 추출**  
- 최소 설정으로 **Word를 markdown으로 변환**  
- 정돈된 이미지 폴더와 함께 **markdown 출력 저장**  

앞으로는 추가 markdown 확장(표, 각주) 등을 실험하거나 CI 파이프라인에 통합해 자동으로 문서를 빌드하는 작업을 진행해 보세요. 이미지 저장 로직만 유연하게 유지한다면 markdown은 언제나 깔끔하게 유지됩니다.

궁금한 점이나 라이선스 관련 문의가 있으면 아래 댓글로 남겨 주세요. Happy coding!

## 다음에 배울 내용

다음 튜토리얼들은 이번 가이드에서 다룬 기술을 기반으로 하며, 단계별 코드 예제와 자세한 설명을 제공해 추가 API 기능을 마스터하고 다양한 구현 방식을 탐색할 수 있도록 도와줍니다.

- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Convert Docx File To Markdown](/words/english/net/basic-conversions/docx-to-markdown/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}