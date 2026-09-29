---
title: Aspose.Words for .NET을 사용하여 Word 문서에 DataMatrix 바코드 삽입
weight: 210
limit:
description: Aspose.Words for .NET을 사용하여 프로그래밍 방식으로 Word 문서에 DataMatrix 바코드를 추가합니다.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET을 사용하여 프로그래밍 방식으로 Word 문서에 DataMatrix 바코드를 추가합니다.
  headline: Aspose.Words for .NET을 사용하여 Word 문서에 DataMatrix 바코드 삽입
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 프로그래밍 방식으로 Word 문서에 DataMatrix 바코드를 추가합니다.
  name: Aspose.Words for .NET을 사용하여 Word 문서에 DataMatrix 바코드 삽입
  steps:
  - name: 새 빈 Word Document를 만들고 이를 편집하기 위한 DocumentBuilder를 생성합니다.
    text: 새 빈 Word Document를 만들고 이를 편집하기 위한 DocumentBuilder를 생성합니다.
  - name: 현재 커서 위치에 DISPLAYBARCODE 필드를 삽입하면 문서에 필드 자리표시자가 추가됩니다.
    text: 현재 커서 위치에 DISPLAYBARCODE 필드를 삽입하면 문서에 필드 자리표시자가 추가됩니다.
  - name: 필드의 BarcodeType을 DataMatrix로 설정하고 인코딩할 데이터 문자열을 제공합니다.
    text: 필드의 BarcodeType을 DataMatrix로 설정하고 인코딩할 데이터 문자열을 제공합니다.
  - name: 선택적으로 바코드의 배경색과 전경색을 정의할 수 있습니다.
    text: 선택적으로 바코드의 배경색과 전경색을 정의할 수 있습니다.
  - name: 문서에서 UpdateFields를 호출하여 필드 내부에 바코드 이미지를 렌더링합니다.
    text: 문서에서 UpdateFields를 호출하여 필드 내부에 바코드 이미지를 렌더링합니다.
  - name: 문서를 .docx 파일로 저장합니다.
    text: 문서를 .docx 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: 필드는 삽입되지만 `document.UpdateFields()`를 실행하면 바코드가 비어 있게 되고 Aspose.Words는
      잘못된 바코드 유형임을 나타내는 `FieldException`을 발생시킵니다.
    question: '`displayBarcodeField.BarcodeType`에 지원되지 않는 값을 할당하면 어떻게 되나요?'
  - answer: '`UpdateFields()`는 바코드 이미지를 렌더링하므로 여러 개의 `FieldDisplayBarcode` 객체를 삽입한
      뒤 마지막에 한 번만 `document.UpdateFields()`를 호출하면 모두 렌더링됩니다.'
    question: 각 바코드 삽입 후마다 `document.UpdateFields()`를 호출해야 하나요, 아니면 모든 필드를 추가한 뒤 한
      번만 호출해도 되나요?
  - answer: '두 속성 모두 `0x` 접두사가 붙은 16진수 RGB 문자열을 기대합니다(예: 빨강은 \"0xFF0000\"); 다른 형식은
      무시되고 기본 색상이 사용됩니다.'
    question: '`BackgroundColor`와 `ForegroundColor`에 사용할 색상 문자열은 어떤 형식이어야 하나요?'
  - answer: 예—`displayBarcodeField.BarcodeValue`를 새로운 문자열로 설정하고 `document.UpdateFields()`를
      다시 호출하면 렌더링된 이미지가 갱신됩니다.
    question: 필드를 삽입한 후에도 바코드 페이로드를 변경할 수 있나요?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Aspose.Words를 사용하여 DataMatrix 바코드 삽입
og_description: .NET 코드 몇 줄만으로 Word 파일에 DataMatrix 바코드를 추가하는 방법을 배워보세요.
og_image_alt: Aspose.Words for .NET을 사용하여 Word 문서에 DataMatrix 바코드를 삽입하고 렌더링하는 방법을 보여주는 가이드
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 DataMatrix 바코드 삽입
Aspose.Words for .NET을 사용하면 프로그래밍 방식으로 Word 문서에 DataMatrix 바코드를 추가할 수 있습니다. 이 튜토리얼에서는 새 문서를 만들고, DISPLAYBARCODE 필드를 삽입하고, 유형을 DataMatrix로 설정한 뒤, Document 및 DocumentBuilder 클래스를 사용하여 바코드 이미지를 렌더링하는 방법을 보여줍니다. 단계별로 따라 하면 .docx 파일 내부에 바로 인쇄 가능한 바코드를 생성할 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `displayBarcodeField.BarcodeType`에 지원되지 않는 값을 할당하면 어떻게 되나요?**  
A: 필드는 삽입되지만 `document.UpdateFields()`를 실행하면 바코드가 비어 있게 되고 Aspose.Words는 잘못된 바코드 유형임을 나타내는 `FieldException`을 발생시킵니다.

**Q: 각 바코드 삽입 후마다 `document.UpdateFields()`를 호출해야 하나요, 아니면 모든 필드를 추가한 뒤 한 번만 호출해도 되나요?**  
A: `UpdateFields()`는 바코드 이미지를 렌더링하므로 여러 개의 `FieldDisplayBarcode` 객체를 삽입한 뒤 마지막에 한 번만 `document.UpdateFields()`를 호출하면 모두 렌더링됩니다.

**Q: `BackgroundColor`와 `ForegroundColor`에 사용할 색상 문자열은 어떤 형식이어야 하나요?**  
A: 두 속성 모두 `0x` 접두사가 붙은 16진수 RGB 문자열을 기대합니다(예: 빨강은 \"0xFF0000\"); 다른 형식은 무시되고 기본 색상이 사용됩니다.

**Q: 필드를 삽입한 후에도 바코드 페이로드를 변경할 수 있나요?**  
A: 예—`displayBarcodeField.BarcodeValue`를 새로운 문자열로 설정하고 `document.UpdateFields()`를 다시 호출하면 렌더링된 이미지가 갱신됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}