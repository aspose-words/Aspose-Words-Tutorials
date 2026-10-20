---
category: general
date: 2026-06-24
description: Markdown으로 저장할 때 DOCX에서 이미지를 내보내는 콜백을 설정하는 방법. 이미지 추출, Word에서 SVG 추출,
  그리고 사용자 정의 처리로 DOCX를 Markdown으로 저장하는 방법을 배워보세요.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: ko
og_description: DOCX를 Markdown으로 변환할 때 이미지 내보내기를 위한 콜백 설정 방법. 이 가이드는 이미지를 효율적으로 추출하고
  SVG를 추출하는 방법을 보여줍니다.
og_title: DOCX에서 이미지 내보내기를 위한 콜백 설정 방법
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: DOCX에서 이미지 내보내기를 위한 콜백 설정 방법
url: /ko/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX에서 이미지 내보내기를 위한 콜백 설정 방법

DOCX를 Markdown으로 변환하면서 **콜백을 설정**하고 **이미지를 내보내는 방법**이 궁금하셨나요? 당신만 그런 것이 아닙니다. 기본 변환이 모든 이미지를 일반 폴더에 덤프하거나, 더 나쁜 경우 SVG 그래픽을 완전히 잃어버리는 상황에 많은 개발자들이 부딪히곤 합니다.  

이 튜토리얼에서는 “콜백을 설정하는 방법” 질문에 답하고, **이미지를 추출하는 방법**을 보여주며, **Word에서 SVG를 추출하는 방법**까지 다루는 완전하고 바로 실행 가능한 솔루션을 단계별로 살펴봅니다. 최종적으로 **DOCX를 Markdown으로 저장**하면서 각 이미지 리소스에 대한 사용자 정의 명명 규칙을 적용할 수 있게 됩니다—수동으로 파일명을 바꿀 필요가 없습니다.

## 배울 내용

- 변환 중 이미지 파일명을 제어하는 가장 깔끔한 방법인 콜백이 왜 필요한지.  
- Aspose.Words의 `MarkdownSaveOptions.resource_saving_callback`에 어떻게 연결하는지.  
- **PNG**, **JPG**, **SVG** 및 기타 임베디드 리소스를 추출하는 단계별 코드.  
- 이름 충돌, 대용량 파일, 플랫폼 간 경로 차이 등을 처리하는 팁.  

> **프로 팁:** 이미 Aspose.Words를 더 큰 파이프라인에서 사용 중이라면, 나머지 코드를 건드리지 않고 이 콜백만 추가하면 됩니다.

---

![How to set callback diagram](https://example.com/images/how-to-set-callback.png "how to set callback")

## 사전 요구 사항

- Python 3.8+ (예제는 f‑strings를 사용하므로 3.6 이상이면 충분합니다).  
- `aspose-words` 패키지 설치 (`pip install aspose-words`).  
- 래스터 이미지 **와** 벡터 그래픽(SVG)이 포함된 DOCX 파일.  
- Python 함수와 파일 I/O에 대한 기본적인 이해.

위 조건을 모두 갖췄다면, 바로 시작해봅시다.

---

## DOCX에서 이미지 내보내기를 위한 콜백 설정 방법

솔루션의 핵심은 **리소스 저장 콜백**에 있습니다. Aspose.Words는 `document.save`를 호출할 때 이미지나 SVG마다 이 델리게이트를 호출합니다. `(new_name, data)` 형태의 튜플을 반환하면 파일명과 바이트 데이터를 직접 지정할 수 있습니다.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### 왜 콜백이 필요한가?

콜백 없이 Aspose.Words는 `image1.png`, `image2.svg`와 같은 이름의 파일을 생성하고 Markdown 파일 옆 폴더에 저장합니다. 빠른 데모에는 괜찮지만, 실제 운영 환경에서는 다음과 같은 요구가 있습니다.

1. **결정론적인 이름** – 버전 관리나 CDN 배포에 유용합니다.  
2. **충돌 방지** – 원본 이름이 동일한 두 이미지가 서로 덮어쓰이지 않게 합니다.  
3. **맞춤 폴더 구조** – 예를 들어 모든 자산을 `/assets/docs/` 아래에 두고 싶을 때.  

콜백을 사용하면 이 세 가지 요구를 모두 완벽히 제어할 수 있습니다.

---

## 리소스 콜백을 이용한 DOCX 이미지 추출

아래는 콜백 구현 예시입니다. 바이너리 데이터를 해시하여 고유 접미사를 만들고, 원본 파일 확장자를 보존한 뒤 새 파일명과 원시 바이트를 반환합니다.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### 엣지 케이스 처리

- **대용량 파일:** SHA‑256은 크기에 관계없이 정상 작동합니다. 해시는 메모리에서 계산되므로, 매우 큰 PDF를 처리할 경우 메모리 사용량을 고려하세요.  
- **확장자 누락:** 오래된 Word 파일은 이미지에 명시적 확장자를 포함하지 않을 수 있습니다. 이 경우 `extension`이 비어 있으니 `.bin`으로 기본값을 지정하거나 처음 몇 바이트를 검사해 형식을 추정하세요.  
- **이미지가 아닌 리소스:** 콜백은 OLE 객체와 같은 모든 외부 리소스에 대해 호출됩니다. 이미지/SVG만 필요하다면 `resource.type`을 기준으로 필터링하면 됩니다.

---

## Word에서 이미지와 SVG 추출하기

이제 콜백을 Markdown 저장 파이프라인에 연결합니다. `MarkdownSaveOptions` 객체는 바로 이 목적을 위해 `resource_saving_callback` 속성을 제공합니다.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

`resource_folder` 설정은 선택 사항이지만 흔히 유용합니다. 지정하지 않으면 이미지가 Markdown 파일 옆에 저장돼 프로젝트 루트가 어수선해질 수 있습니다.

### 문서 저장

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

스크립트를 실행하면 다음과 같은 파일들이 생성됩니다:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

그리고 생성된 `output.md`에는 정확히 그 파일명을 가리키는 이미지 링크가 들어갑니다:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

이것이 **이미지 추출**이 실제로 동작하는 모습이며, 래스터든 벡터든 모든 그림이 이제 별도의 고유 파일로 저장됩니다.

---

## 사용자 정의 이미지 처리를 포함한 DOCX → Markdown 변환

전체 스크립트를 한 번에 정리하면 아래와 같습니다. 파일 이름은 `convert_docx_to_md.py`로 저장하면 됩니다:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**작동 원리:**  
- `resource_callback`은 모든 이미지에 고유하고 재현 가능한 이름을 부여합니다.  
- `resource_folder`는 자산을 별도 폴더에 두어 Markdown을 깔끔하게 유지합니다.  
- `os.makedirs` 호출은 새 머신에서 스크립트를 실행할 때 “폴더를 찾을 수 없음” 오류를 방지합니다.

---

## Word에서 SVG 추출 – 벡터 그래픽은 어떻게?

SVG는 콜백에서 PNG와 동일하게 처리됩니다. 왜냐하면 SVG도 또 다른 `resource`이기 때문이죠. 다만 일부 오래된 Word 버전은 SVG를 *OfficeArt* 객체로 임베드하는데, Aspose.Words는 기본적으로 이를 래스터 PNG로 변환합니다. **preserve SVG** 플래그를 명시적으로 활성화하면 SVG를 그대로 유지할 수 있습니다:

```python
md_options.export_svg = True  # Keep original SVG markup
```

저장 전에 위 코드를 추가하면 콜백이 `.svg` 확장자를 가진 리소스를 받게 되고, 선명한 벡터 데이터를 보존합니다—반응형 웹 문서에 최적입니다.

---

## 흔히 묻는 질문 및 주의점

| 질문 | 답변 |
|----------|--------|
| **두 이미지가 동일하면 어떻게 되나요?** | SHA‑256 해시가 동일해 파일명이 충돌합니다. 두 사본이 모두 필요하면 해시 계산에 원본 `resource.name`을 포함하세요(예: `hash(resource.name + resource.data)`). |
| **파일 유형별로 폴더를 다르게 지정할 수 있나요?** | 가능합니다. `resource_callback` 내부에서 `extension`을 검사하고 `f"png/{new_name}"`처럼 경로를 반환하면 래스터 이미지는 `png/`, 벡터는 `svg/` 폴더에 저장됩니다. |
| **Linux/macOS에서도 동작하나요?** | 물론입니다. 코드는 `os.path`를 사용해 경로 구분자를 추상화합니다. 유료 버전을 사용한다면 Aspose.Words 라이선스 파일(`aspose.words.lic`)이 접근 가능한지 확인하세요. |
| **대용량 문서의 메모리 사용량은 어떨까요?** | 콜백은 각 리소스에 대해 **전체 바이트 배열**을 전달하므로 이미지가 일시적으로 메모리에 로드됩니다. 수 기가바이트 규모 파일이라면 콜백 내부에서 데이터를 바로 디스크에 스트리밍하고 반환값을 `None`으로 처리하는 것이 좋습니다. |

---

## 결론

이제 **DOCX를 Markdown으로 저장**하면서 이미지 추출을 제어하는 **콜백 설정 방법**을 알게 되었습니다. 이 접근법을 통해 **DOCX에서 이미지 내보내기**, **Word에서 SVG 추출**, 그리고 깔끔하고 결정론적인 Markdown 파일을 만들 수 있습니다.  

단일 스크립트에서 문서 로드, 리소스 저장 콜백 정의, `MarkdownSaveOptions` 구성, 이름 충돌 및 벡터 그래픽 처리까지 모두 다루었습니다. 결과물은 고유한 파일명으로 된 자산 폴더와 완벽히 연결된 Markdown 파일이며, 정적 사이트 생성기, 문서 파이프라인, 혹은 재사용 가능한 자산이 필요한 모든 워크플로에 바로 적용할 수 있습니다.

**다음 단계**  
- MkDocs와 같은 정적 사이트 생성기와 연결해 Word 기반 문서를 자동으로 배포해 보세요.  
- 외부 파일 대신 인라인 이미지를 원한다면 `markdown_options.export_images_as_base64 = True` 옵션을 실험해 보세요.  
- Aspose.Words의 다른 콜백(`document_saving_callback` 등)을 탐색해 Markdown 출력 자체를 제어하는 방법도 살펴보세요.

다른 Office 형식에서 **이미지를 추출하는 방법**에 대한 추가 질문이 있거나, 특정 명명 규칙에 맞게 콜백을 조정하고 싶다면 아래 댓글로 알려 주세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 확장하고, 프로젝트에 적용할 수 있는 다양한 접근 방식을 제공합니다. 각각의 리소스에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 API 기능을 마스터하고 구현 방식을 다양화하는 데 도움이 됩니다.

- [DOCX를 Markdown으로 변환할 때 이미지 이름 바꾸기](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [DOCX에서 Markdown 저장 – 단계별 가이드](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}