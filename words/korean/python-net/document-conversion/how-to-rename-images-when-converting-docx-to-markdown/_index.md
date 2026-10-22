---
category: general
date: 2026-06-30
description: DOCX를 마크다운으로 변환하면서 이미지 이름을 바꾸는 방법. 이미지 이름을 변경하고 Word를 사용자 지정 이미지 파일명으로
  마크다운으로 저장하는 방법을 배워보세요.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: ko
og_description: DOCX를 마크다운으로 변환하면서 이미지 이름을 바꾸는 방법. 이 가이드는 이미지 이름을 변경하고, 워드를 마크다운으로
  저장하며, 사용자 지정 이미지 파일명을 사용하는 방법을 보여줍니다.
og_title: DOCX를 Markdown으로 변환할 때 이미지 이름을 바꾸는 방법
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: DOCX를 Markdown으로 변환할 때 이미지 이름 바꾸는 방법
url: /ko/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX를 Markdown으로 변환할 때 이미지 이름 바꾸는 방법

DOCX 파일을 Markdown으로 변환할 때 **이미지 이름 바꾸는 방법**을 자동으로 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 많은 문서 파이프라인에서 기본 이미지 이름(`image1.png` 등)은 추적하기가 악몽이 되는데, 특히 같은 Markdown이 팀 간에 버전 관리될 때 더욱 그렇습니다.  

좋은 소식은 Aspose.Words for Python을 사용하면 **이미지 이름 변경**을 즉시 처리할 수 있어, Markdown을 깔끔하게 유지하면서 사용자 지정 이름의 자산 폴더를 정돈된 상태로 보관할 수 있다는 점입니다.  

이 튜토리얼에서 배우게 될 내용:

* Python에서 Word 문서(`.docx`)를 로드합니다.  
* 각 이미지에 GUID 기반 파일명을 부여하는 콜백을 사용해 Markdown 저장 프로세스에 연결합니다.  
* 문서를 Markdown으로 저장하여 생성된 파일이 새 이름의 이미지를 참조하도록 합니다.  

기본 Python 사용에 익숙하고 Aspose.Words가 설치되어 있다면 5분 이내에 바로 실행할 수 있습니다. 외부 스크립트도, 수동 이름 변경도 필요 없습니다—무거운 작업을 대신해 주는 단일, 독립형 프로그램만 있으면 됩니다.

---

## Prerequisites — 시작하기 전에 필요한 것

| 요구 사항 | 이유 |
|-------------|----------------|
| **Python 3.7+** | 예제는 3.6에 도입된 f‑strings와 타입 힌트를 사용하지만, 3.7+에서는 `os.path.splitext` 편의 기능을 제공합니다. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | 이 라이브러리는 `aw.Document` 클래스와 우리가 의존하는 `MarkdownSaveOptions`를 제공합니다. |
| **출력 폴더에 대한 쓰기 권한** | 콜백이 새 이미지 파일을 생성하므로 스크립트가 이를 쓸 수 있어야 합니다. |
| **변환하려는 DOCX 파일** | 간단한 보고서부터 복잡한 매뉴얼까지 모두 적용 가능합니다. |

> **Pro tip:** 가상 환경을 사용 중이라면 Aspose.Words를 설치하기 전에 해당 환경을 활성화하세요. 이렇게 하면 의존성을 격리하고 버전 충돌을 방지할 수 있습니다.

---

## Step 1: Word 문서 로드  

**docx를 markdown으로 변환**하려면 먼저 원본 파일을 여는 것이 첫 번째 단계입니다. Aspose.Words는 저수준 OPC 처리를 추상화하므로 한 줄만으로 작업을 수행할 수 있습니다.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Why this matters:* 문서를 로드하지 않으면 리소스를 검사할 수 없으며, Markdown 내보내기는 쓸 것이 없게 됩니다. `aw.Document` 객체는 전체 Word 패키지를 메모리에 보관하므로 저장하기 전에 안전하게 조작할 수 있습니다.

---

## Step 2: **이미지 리소스 이름 바꾸기** 콜백 작성  

Aspose.Words는 `MarkdownSaveOptions`에 `resource_saving_callback`을 연결할 수 있게 해줍니다. 콜백은 각 리소스(이미지, CSS 등)가 디스크에 기록되기 직전에 호출됩니다. `resource.file_name`을 변경함으로써 **사용자 지정 이미지 파일명**을 강제할 수 있습니다.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### GUID를 사용하는 이유

* **고유성** – GUID(`uuid4`)는 두 이미지가 절대 충돌하지 않도록 보장합니다, 여러 번 실행해도 마찬가지입니다.  
* **추적성** – 나중에 디버깅이 필요할 경우, GUID를 원본 Word 단락 번호와 함께 로그에 남길 수 있습니다.  
* **이식성** – 원본 Word 이름 체계에 의존하지 않으므로, 공백이나 특수 문자가 포함돼 Markdown 링크가 깨지는 문제를 방지합니다.

---

## Step 3: Markdown 저장 옵션에 콜백 연결  

이제 이미지가 출력 폴더에 기록될 때마다 우리 이름 바꾸기 로직을 사용하도록 Aspose에 지시합니다.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Explanation:* `MarkdownSaveOptions` 클래스는 줄 바꿈부터 이미지 폴더 위치까지 모든 것을 제어합니다. `resource_saving_callback`을 설정하면 각 임베디드 리소스에 대해 **후크**가 작동하여 파일이 디스크에 기록되기 전에 **이미지 이름을 변경**할 수 있는 기회를 제공합니다.

---

## Step 4: Markdown으로 문서 저장 – 최종 단계  

콜백이 설정되었으니 마지막 단계는 매우 간단합니다.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

스크립트가 끝나면 다음을 확인할 수 있습니다:

* `CustomResources.md` – Word 파일의 Markdown 표현입니다.  
* `images/` 폴더(또는 지정한 폴더) 안에 `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`와 같은 파일이 들어 있습니다.  

Markdown 파일은 새 GUID 기반 파일명을 참조하므로, GitHub, MkDocs 등 하위 프로세서가 올바른 이미지를 자동으로 인식합니다. 수동으로 이름을 바꿀 필요가 없습니다.

### Expected Output (excerpt)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

GUID는 매 실행마다 달라지지만 패턴은 동일합니다.

---

## Handling Edge Cases and Common Questions  

### 문서에 이미지가 아닌 리소스가 포함된 경우는?

우리 콜백은 파일 확장자를 이미 검사하고 이미지가 아닌 경우 `True`를 반환합니다. 따라서 CSS 파일, 폰트, 임베디드 OLE 객체 등은 원래 이름을 유지하게 되며, 이는 **save word as markdown**할 때 일반적으로 원하는 동작입니다.

### GUID 대신 사용자 지정 이름 규칙을 사용할 수 있나요?

물론 가능합니다. `uuid.uuid4()` 호출을 문자열을 반환하는任意 함수로 교체하면 됩니다. 예를 들어 원본 단락 인덱스를 앞에 붙일 수 있습니다:

```python
new_name = f"para{resource.resource_id}{ext}"
```

단, 결과 이름이 문서 전체에서 고유하도록 해야 합니다.

### 대용량 문서에서 성능에 어떤 영향을 미치나요?

콜백은 리소스당 한 번씩 실행되므로 오버헤드는 최소합니다—주로 GUID를 생성하는 시간 정도입니다. 수십 개의 이미지가 포함된 200페이지 보고서도 최신 노트북에서는 1초 미만에 완료됩니다.

### 이미지 파일명을 결정론적으로 만들어야 할 경우(CI 빌드 등)는?

`uuid.uuid4()` 대신 원본 이미지 바이트의 해시를 사용하면 됩니다:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

이렇게 하면 동일한 소스 이미지를 대상으로 스크립트를 실행할 때마다 같은 파일명이 생성됩니다.

---

## Full Working Script – Copy, Paste, Run  



## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}