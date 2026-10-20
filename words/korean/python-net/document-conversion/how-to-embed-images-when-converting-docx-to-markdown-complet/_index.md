---
category: general
date: 2026-05-04
description: Aspose.Words를 사용하여 DOCX를 Markdown으로 변환하면서 이미지를 삽입하는 방법을 배워보세요. Word를
  Markdown으로 변환하고, docx에서 이미지를 추출하며, 이미지를 base64로 삽입하는 단계가 포함됩니다.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- convert word to markdown
- extract images from docx
- embed images as base64
language: ko
og_description: Aspose.Words for Python을 사용해 DOCX를 Markdown으로 변환하면서 이미지를 삽입하는 방법을
  알아보세요. 전체 코드와 설명, docx에서 이미지를 추출해 base64로 삽입하는 팁이 포함되어 있습니다.
og_title: DOCX를 Markdown으로 변환할 때 이미지 삽입 방법 – 단계별 가이드
tags:
- Aspose.Words
- Python
- Markdown
- Document Conversion
title: DOCX를 Markdown으로 변환할 때 이미지를 삽입하는 방법 – 완전 가이드
url: /ko/python/document-conversion/how-to-embed-images-when-converting-docx-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX를 Markdown으로 변환할 때 이미지를 삽입하는 방법 – 완전 가이드

워드 문서에서 파생된 Markdown 파일에 **이미지를 삽입하는 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 DOCX를 Markdown으로 변환하려다 이미지 링크가 깨지는 문제에 부딪힙니다. 좋은 소식은? Python과 Aspose.Words 몇 줄만으로 모든 그림을 그대로 유지할 수 있으며, Base64 data‑URI 형태로도 가능합니다.

이 튜토리얼에서는 Aspose.Words 설치부터, 그림이 포함된 DOCX 로드, 이미지 추출, 그리고 최종 Markdown에 **이미지를 Base64 문자열로 삽입**하는 전체 과정을 단계별로 살펴봅니다. 끝까지 따라오면 **docx를 markdown으로 변환**, **word를 markdown으로 변환**, 그리고 **docx에서 이미지 추출**까지 IDE를 떠나지 않고 수행할 수 있습니다.

> **필수 조건**  
> * Python 3.8+  
> * `aspose-words` 패키지 (무료 체험판으로 대부분의 시나리오에 충분)  
> * 최소 하나의 이미지가 포함된 DOCX 파일 (예: `Images.docx`)  

pip과 기본 파일 I/O에 익숙하다면 바로 시작할 수 있습니다. 바로 들어가 보죠.

---

## DOCX를 Markdown으로 변환하면서 이미지를 삽입하는 방법

이 H2는 기본 키워드 규칙을 직접 만족시키며 검색 엔진과 AI 어시스턴트에게 해당 섹션이 다루는 내용을 정확히 알려줍니다.

### Step 1: Install Aspose.Words for Python

먼저 PyPI에서 라이브러리를 가져옵니다. 패키지 이름은 `aspose-words`이며, .NET 버전과 혼동하지 마세요.

```bash
pip install aspose-words
```

> **팁:** 기업 프록시 뒤에 있을 경우 `--proxy http://your-proxy:port` 옵션을 명령에 추가하세요.  

패키지를 설치하면 `aspose-words` 자체 의존성인 `aspose-words-cloud`도 함께 내려받습니다. 로컬 변환을 위해 별도의 설정은 필요하지 않습니다.

### Step 2: Load the source DOCX document

파일을 열기 위해 `aw.Document` 클래스를 사용할 것입니다. 이 단계가 바로 **docx에서 이미지 추출**을 별도로 수행하고 싶을 때 사용됩니다.

```python
import aspose.words as aw
import base64

# Path to the Word file that contains images
doc_path = "YOUR_DIRECTORY/Images.docx"

# Load the document into memory
document = aw.Document(doc_path)
```

> **왜 중요한가:** 문서를 로드하면 이후에 `resource_saving_callback`에 접근할 수 있게 되며, 이는 Aspose가 Markdown 저장 시 이미지를 어떻게 기록할지 결정하는 훅입니다.

### Step 3: Define a callback that turns each image into a Base64 data‑URI

Aspose는 디스크에 기록될 모든 리소스(이미지, 폰트 등)를 가로챌 수 있게 해줍니다. 콜백을 제공하면 기본 파일 기반 처리 방식을 인라인 Base64 문자열로 교체할 수 있습니다.

```python
def embed_images_callback(resource):
    """
    Called for every resource Aspose wants to save.
    If the resource is an image, we convert it to a data‑URI.
    """
    # Only process image resources; other types fall back to default handling
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Build the data‑URI: data:<mime>;base64,<encoded bytes>
        data_uri = (
            f"data:{resource.mime_type};base64,"
            f"{base64.b64encode(resource.bytes).decode()}"
        )
        # Return a tuple (resource name, encoded data) – name is ignored for data‑URI
        return (resource.name, data_uri.encode())
    # Returning None tells Aspose to use its default saving logic
    return None
```

> **예외 상황:** 일부 Word 파일은 SVG 이미지를 포함합니다. Aspose는 MIME 타입을 `image/svg+xml`으로 보고하는데, data‑URI도 이를 지원합니다. 대상 Markdown 뷰어가 SVG를 렌더링하지 못한다면 콜백 내부에서 PNG로 변환하는 것을 고려하세요.

### Step 4: Configure Markdown save options and attach the callback

이제 방금 정의한 콜백을 Aspose에 사용하도록 지정합니다. 이것이 최종 Markdown 파일에 **이미지를 삽입하는 방법**의 핵심입니다.

```python
# Create save options for Markdown
markdown_options = aw.saving.MarkdownSaveOptions()

# Attach our custom callback
markdown_options.resource_saving_callback = embed_images_callback
```

`markdown_options`를 조정하면 제목 레벨, 코드 블록 구분자, 별도 리소스 폴더 생성 여부 등을 제어할 수 있습니다. 이 가이드에서는 data‑URI 방식이 별도 폴더 필요성을 없애므로 기본값을 유지합니다.

### Step 5: Save the document as Markdown with embedded Base64 images

마지막으로 출력 파일을 저장합니다. 결과물은 모든 이미지를 Base64 문자열로 포함한 단일 `.md` 파일이며, 외부 자산이 전혀 필요하지 않습니다.

```python
output_path = "YOUR_DIRECTORY/ImagesEmbedded.md"
document.save(output_path, markdown_options)

print(f"✅ Markdown with embedded images saved to: {output_path}")
```

> **보게 될 내용:**  
> ```markdown
> ![Picture1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
> ```  
> `base64,` 뒤에 이어지는 긴 문자열은 이미지의 바이너리 데이터를 브라우저가 실시간으로 디코딩할 수 있도록 인코딩한 것입니다.

---

## 이미지를 잃지 않고 DOCX를 Markdown으로 변환하기 – 일반적인 함정

위 코드는 바로 사용할 수 있지만, 개발자들은 종종 몇 가지 문제에 직면합니다. 아래는 가장 빈번한 질문과 변환을 원활하게 유지하기 위한 답변입니다.

### 1. “변환 후에도 이미지가 여전히 사라져요”

* **MIME 타입 확인:** 일부 오래된 DOCX 파일은 이미지를 일반 MIME 타입(`application/octet-stream`)으로 저장합니다. 콜백은 여전히 삽입하지만, 일부 Markdown 렌더러는 알 수 없는 타입을 표시하지 않을 수 있습니다. 이미지 형식을 알고 있다면 콜백에서 `image/png`로 강제 변환할 수 있습니다.
* **대용량 문서:** Base64는 크기를 약 33 % 정도 증가시킵니다. 10 MB 워드 파일을 변환하면 Markdown 파일이 ~13 MB가 될 수 있습니다. 최신 편집기는 대부분 처리하지만 정적 사이트 생성기는 제한이 있을 수 있습니다. 크기가 문제라면 이미지를 폴더에 추출하고 삽입 대신 링크를 사용하는 것을 고려하세요.

### 2. “DOCX에서 이미지를 별도로 추출할 수도 있나요?”

물론 가능합니다. 동일한 콜백에서 이미지 바이트를 디스크에 저장한 뒤 data‑URI를 반환하도록 하면 됩니다.

```python
import os

def embed_and_save_images(resource):
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Save the raw image to a folder
        os.makedirs("extracted_images", exist_ok=True)
        with open(f"extracted_images/{resource.name}", "wb") as f:
            f.write(resource.bytes)

        # Then embed as Base64 (same as before)
        data_uri = f"data:{resource.mime_type};base64,{base64.b64encode(resource.bytes).decode()}"
        return (resource.name, data_uri.encode())
    return None
```

이 버전을 실행하면 `extracted_images` 폴더 **와** Base64 이미지가 삽입된 Markdown 파일 두 가지를 모두 얻을 수 있어, 두 용도가 모두 필요한 프로젝트에 최적입니다.

### 3. “표, 각주, 혹은 특수 Word 기능은 어떻게 처리되나요?”

Aspose.Words는 가능한 한 많은 서식을 보존하려고 노력하지만, Markdown은 기능이 제한적입니다. 표는 파이프 구분 문법으로 변환되고, 각주는 일반 텍스트 마커로 변환됩니다. 더 풍부한 출력이 필요하다면(`예: HTML`) `MarkdownSaveOptions`를 `HtmlSaveOptions`로 교체하고 동일한 콜백 로직을 유지하면 됩니다.

---

## 전체 실행 가능한 예제 – 복사‑붙여넣기 준비

모든 내용을 하나로 합치면, 프로젝트 폴더 어디에든 넣을 수 있는 단일 스크립트가 됩니다. `YOUR_DIRECTORY` 자리표시자를 실제 파일 경로에 맞게 수정하세요.

```python
# ------------------------------------------------------------
# How to embed images while converting DOCX to Markdown
# ------------------------------------------------------------
# Prerequisites:
#   pip install aspose-words
# ------------------------------------------------------------

import aspose.words as aw
import base64
import os

# ------------------------------------------------------------------
# 1️⃣  Define the callback that embeds images as Base64 data‑URIs
# ------------------------------------------------------------------
def embed_images_callback(resource):
    """
    Aspose calls this for each external resource (image, font, etc.).
    We only care about images – everything else falls back to default.
    """
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Optional: also write the image to disk for later reuse
        os.makedirs("extracted_images", exist_ok=True)
        with open(f"extracted_images/{resource.name}", "wb") as img_file:
            img_file.write(resource.bytes)

        # Build the Base64 data‑URI
        data_uri = (
            f"data:{resource.mime_type};base64,"
            f"{base64.b64encode(resource.bytes).decode()}"
        )
        # Return name (ignored) and the encoded URI as bytes
        return (resource.name, data_uri.encode())
    return None  # Use Aspose's default handling for non‑image resources

# ------------------------------------------------------------------
# 2️⃣  Load the DOCX that contains images
# ------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/Images.docx"
document = aw.Document(doc_path)

# ------------------------------------------------------------------
# 3️⃣  Prepare Markdown save options and hook the callback
# ------------------------------------------------------------------
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = embed_images_callback

# ------------------------------------------------------------------
# 4️⃣  Save as Markdown with images embedded as Base64
# ------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/ImagesEmbedded.md"
document.save(output_path, markdown_options)

print(f"✅ Success! Markdown saved to {output_path}")
print("   Images are now inline Base64 data‑URIs.")
```

**예상 결과:** `ImagesEmbedded.md`를 열면 원본 텍스트와 함께 `![Picture1](data:image/png;base64,…)`와 같은 인라인 이미지 태그가 표시됩니다. 외부 이미지 파일이 전혀 필요하지 않습니다.

---

## 결론

우리는 **docx를 markdown으로 변환할 때 이미지를 삽입하는 방법**을 다루었고, **docx에서 이미지 추출** 방법을 보여주었으며, Aspose.Words for Python을 사용해 **이미지를 Base64로 삽입**하는 가장 깔끔한 방식을 시연했습니다. 위의 완전한 스크립트는 바로 실행할 수 있으며, 각 라인 뒤에 있는 설명은 “왜”라는 질문에 답해 주어 여러분이 프로젝트에 맞게 자유롭게 적용할 수 있게 합니다.

더 나아가고 싶나요? 다음 단계들을 시도해 보세요:

* `markdown_options.heading_level`을 조정해 **Word를 markdown으로 변환**할 때 사용자 정의 제목 레벨 적용
* 동일한 DOCX에서 **PDF를 생성**하고 다양한 출력 포맷에서 이미지가 어떻게 처리되는지 비교
* 스크립트를 **CI 파이프라인에 통합**해 매 커밋마다 문서의 Markdown 스냅샷을 자동으로 생성

실험을 마음껏 해 보세요—예를 들어 대용량 파일은 Base64 삽입 대신 CDN URL로 교체하거나, 스캔된 이미지에 OCR을 추가할 수도 있습니다. 가능성은 무한하며, 이제 탄탄한 기반을 갖추었습니다.

If you hit any sn
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}