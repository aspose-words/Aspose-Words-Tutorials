---
category: general
date: 2026-11-25
description: Aspose.Words를 사용해 docx를 pdf로 저장하고, docx를 pdf로 변환하며, 부동형 도형을 인라인 태그로 한
  번에 내보내는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx as pdf
- convert docx to pdf
- how to export shapes
- convert word to pdf
- aspose docx to pdf
language: ko
lastmod: 2026-11-25
og_description: Aspose.Words를 사용하여 docx를 pdf로 저장하고, docx를 pdf로 변환하며, 완벽한 PDF 출력을 위해
  도형을 인라인 태그로 내보내는 방법을 배워보세요.
og_image_alt: Screenshot showing a DOCX file being saved as PDF with shapes preserved
og_title: Aspose.Words로 docx를 PDF로 저장 – 도형을 올바르게 내보내기
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  headline: How to save docx as pdf with Aspose.Words while exporting shapes
  type: TechArticle
- description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  name: How to save docx as pdf with Aspose.Words while exporting shapes
  steps:
  - name: Converting multiple DOCX files in a batch
    text: 'When you need to **convert docx to pdf** for many files, wrap the three
      steps in a loop:'
  - name: Dealing with very large documents
    text: For large Word files, consider enabling `pdf_opts.save_format = aw.SaveFormat.PDF`
      (the default) and adjusting `pdf_opts.compliance` if you need PDF/A compliance.
      These options do not affect shape export but improve compatibility with archival
      systems.
  - name: When shapes should remain floating
    text: If a specific document requires floating shapes to stay floating (e.g.,
      a design‑heavy brochure), set the flag to `False`. The PDF will then render
      shapes as separate drawing objects, which may be preferable for precise graphic
      positioning.
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- Word automation
title: Aspose.Words를 사용하여 도형을 내보내면서 docx를 PDF로 저장하는 방법
url: /ko/python/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-while-exporting-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 도형을 내보내면서 docx를 pdf로 저장하는 방법

**docx를 pdf로 저장**하고 모든 떠 있는 도형을 정확히 제자리에 유지해야 할 때, 이 가이드는 전체 과정을 보여줍니다. 튜토리얼을 마치면 Word 문서를 PDF 파일로 변환하고, 도형을 올바르게 내보내며, 각 설정이 왜 중요한지 이해할 수 있습니다.

Word 파일을 PDF로 변환하는 것은 청구서 생성, 보고서 발행, 문서 보관 등에서 일반적인 요구 사항입니다. 이 튜토리얼은 **convert docx to pdf** 워크플로우를 다루고, **how to export shapes**를 인라인으로 표시하도록 설명하며, Aspose.Words 라이브러리를 사용한 **convert word to pdf** 작업을 시연합니다. Aspose.Words for Python via .NET 패키지 외에 별도의 도구가 필요하지 않습니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* 개발 머신에 Python 3.9+가 설치되어 있어야 합니다.  
* `aspose-words` 패키지(`pip install aspose-words`로 설치 가능).  
* 떠 있는 도형(텍스트 상자, 그림, SmartArt 등)이 포함된 DOCX 파일.  
* 출력 디렉터리에 대한 쓰기 권한.

위 전제 조건은 모두 자유 형식이며, 튜토리얼은 Windows, macOS, Linux에서 모두 동작합니다.

## Step 1: Load the source document

첫 번째 작업은 DOCX 파일을 `aw.Document` 객체에 로드하는 것입니다. 이 객체는 메모리 내에서 전체 Word 문서를 나타내며, 섹션, 단락, 그림 객체 등에 접근할 수 있게 해줍니다.

```python
import aspose.words as aw

# Step 1: Load the source document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

**Why this step matters:**  
파일을 로드하면 Aspose.Words가 조작할 수 있는 구조화된 객체 모델이 생성됩니다. 이 모델이 없으면 이후 PDF 변환 단계에서 읽을 소스가 없습니다.

## Step 2: Configure PDF save options and enable inline export for floating shapes

Aspose.Words는 출력 PDF를 미세 조정할 수 있는 `PdfSaveOptions` 클래스를 제공합니다. `export_floating_shapes_as_inline_tag` 속성은 떠 있는 도형을 인라인 `<w:wrap>` 태그(텍스트 흐름의 일부로 처리)로 렌더링할지, 별도의 그림 객체로 렌더링할지를 제어합니다.

```python
# Step 2: Create PDF save options and enable inline export for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
```

**Why this setting is important:**  
**how to export shapes**를 올바르게 설정하면 도형이 사라지거나 PDF에서 예상치 못한 위치로 이동하는 일반적인 문제를 방지할 수 있습니다. 플래그를 `True`로 설정하면 렌더러가 각 떠 있는 도형을 인라인에 고정된 것처럼 처리하여 레이아웃 정확성을 유지합니다. 이는 대부분의 비즈니스 문서에 권장되는 접근 방식입니다.

## Step 3: Save the document as a PDF using the configured options

문서를 로드하고 저장 옵션을 준비했으니 이제 PDF 파일을 디스크에 기록할 수 있습니다.

```python
# Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

**Why this final step completes the workflow:**  
`PdfSaveOptions` 인스턴스를 사용해 `doc.save`를 호출하면 변환 파이프라인이 실행됩니다. Aspose.Words는 DOCX 구조를 읽고, 인라인‑도형 규칙을 적용한 뒤, 원본 레이아웃을 그대로 반영한 PDF를 작성합니다. 이 호출 이후 `output.pdf`는 원본 DOCX와 동일한 텍스트, 이미지, 도형을 포함합니다.

## Expected output

* `output.pdf`가 대상 폴더에 생성됩니다.  
* 모든 단락, 표, 떠 있는 도형(텍스트 상자, 그림, SmartArt)이 `input.docx`와 정확히 같은 위치에 배치됩니다.  
* 파일 크기는 도형 내보내기 조정 없이 일반 Word 문서에서 생성된 표준 PDF와 비슷합니다.

PDF를 Adobe Acrobat이나 최신 뷰어에서 열면 그래픽이 누락되거나 요소가 이동된 경우가 없어야 합니다.

## Common variations and edge cases

### Converting multiple DOCX files in a batch

많은 파일을 **convert docx to pdf**해야 할 때는 세 단계를 루프에 감싸면 됩니다:

```python
import pathlib

source_dir = pathlib.Path("YOUR_DIRECTORY")
for docx_path in source_dir.glob("*.docx"):
    doc = aw.Document(str(docx_path))
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True
    pdf_path = docx_path.with_suffix(".pdf")
    doc.save(str(pdf_path), pdf_opts)
```

### Dealing with very large documents

대용량 Word 파일의 경우 `pdf_opts.save_format = aw.SaveFormat.PDF`(기본값)를 활성화하고, PDF/A 호환성이 필요하면 `pdf_opts.compliance`를 조정하세요. 이러한 옵션은 도형 내보내기에 영향을 주지 않지만 아카이브 시스템과의 호환성을 향상시킵니다.

### When shapes should remain floating

특정 문서에서 도형이 떠 있는 상태를 유지해야 하는 경우(예: 디자인 중심 브로셔) 플래그를 `False`로 설정합니다. 그러면 PDF가 도형을 별도의 그림 객체로 렌더링하므로 정밀한 그래픽 배치에 유리할 수 있습니다.

## Pro tips

* **Pro tip:** PDF를 대상 뷰어(예: Chrome, Edge, Acrobat)에서 항상 테스트하세요. 일부 뷰어는 인라인 태그를 약간 다르게 해석할 수 있습니다.  
* **Watch out for:** 레거시 VML 그림 형식을 사용하는 문서; Aspose.Words는 VML을 최신 그림 객체로 자동 변환하지만 복잡한 VML은 추가 정리가 필요할 수 있습니다.  
* **Performance tip:** 다수의 파일을 처리할 때는 `PdfSaveOptions` 인스턴스를 재사용하여 객체 할당 오버헤드를 줄이세요.

## Full, runnable example

아래는 `docx_to_pdf.py`라는 파일에 복사‑붙여넣기 할 수 있는 전체 스크립트입니다. `YOUR_DIRECTORY`를 실제 경로로 교체하세요.

```python
import aspose.words as aw
import pathlib

def convert_docx_to_pdf(input_path: pathlib.Path, output_path: pathlib.Path):
    """
    Loads a DOCX file, configures PDF save options to export floating shapes as inline tags,
    and writes the result to a PDF file.
    """
    # Load the DOCX document
    doc = aw.Document(str(input_path))

    # Configure PDF options – export floating shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True

    # Save the PDF
    doc.save(str(output_path), pdf_opts)

if __name__ == "__main__":
    base_dir = pathlib.Path("YOUR_DIRECTORY")
    input_file = base_dir / "input.docx"
    output_file = base_dir / "output.pdf"

    convert_docx_to_pdf(input_file, output_file)
    print(f"Conversion complete: {output_file}")
```

`python docx_to_pdf.py`를 실행하면 모든 도형이 보존된 `output.pdf`가 생성됩니다. 이 스크립트는 **aspose docx to pdf** 기능을 깔끔하고 재사용 가능한 함수 형태로 보여줍니다.

## Conclusion

이제 Aspose.Words를 사용해 **save docx as pdf**하는 방법, **convert docx to pdf**하면서 도형 내보내기를 제어하는 방법, 그리고 `export_floating_shapes_as_inline_tag` 플래그가 레이아웃 보존에 핵심이라는 것을 알게 되었습니다. 이 접근 방식은 **convert word to pdf** 시나리오에 적용 가능하며, 배치 처리와 문서별 도형 처리 조정도 지원합니다.

다음으로 **PDF에 워터마크 추가**, **PDF 출력 압축**, 혹은 **DOCX를 HTML이나 EPUB 같은 다른 형식으로 변환**과 같은 관련 주제를 탐색해 보세요. 이들 기능은 여기서 사용한 `aw.Document` 객체 모델을 기반으로 하므로 자동화 파이프라인을 자신 있게 확장할 수 있습니다.

Happy coding, and enjoy the seamless PDF results!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [How to save docx as pdf with Aspose.Words in Python](/words/english/python-net/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-in-python/)
- [Save Word as PDF in C# – Full Guide to Convert DOCX to PDF with Shape Export](/words/english/net/programming-with-pdfsaveoptions/save-word-as-pdf-in-c-full-guide-to-convert-docx-to-pdf-with/)
- [Save docx as pdf & detect missing fonts using Aspose.Words](/words/english/net/working-with-fonts/save-docx-as-pdf-detect-missing-fonts-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}