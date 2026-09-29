---
title: Aspose.Words for .NET を使用して Word ドキュメントに DataMatrix バーコードを挿入する
weight: 210
limit:
description: Aspose.Words for .NET を使用して、プログラムで Word ドキュメントに DataMatrix バーコードを追加します。
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET を使用して、プログラムで Word ドキュメントに DataMatrix バーコードを追加します。
  headline: Aspose.Words for .NET を使用して Word ドキュメントに DataMatrix バーコードを挿入する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、プログラムで Word ドキュメントに DataMatrix バーコードを追加します。
  name: Aspose.Words for .NET を使用して Word ドキュメントに DataMatrix バーコードを挿入する
  steps:
  - name: 新しい空の Word Document を作成し、編集用に DocumentBuilder を作成します。
    text: 新しい空の Word Document を作成し、編集用に DocumentBuilder を作成します。
  - name: 現在のカーソル位置に DISPLAYBARCODE フィールドを挿入します。これにより、ドキュメントにフィールドのプレースホルダーが追加されます。
    text: 現在のカーソル位置に DISPLAYBARCODE フィールドを挿入します。これにより、ドキュメントにフィールドのプレースホルダーが追加されます。
  - name: フィールドの BarcodeType を DataMatrix に設定し、エンコードするデータ文字列を指定します。
    text: フィールドの BarcodeType を DataMatrix に設定し、エンコードするデータ文字列を指定します。
  - name: 必要に応じて、バーコードの背景色と前景色を定義します。
    text: 必要に応じて、バーコードの背景色と前景色を定義します。
  - name: ドキュメントで UpdateFields を呼び出し、フィールド内にバーコード画像をレンダリングします。
    text: ドキュメントで UpdateFields を呼び出し、フィールド内にバーコード画像をレンダリングします。
  - name: ドキュメントを .docx ファイルとして保存します。
    text: ドキュメントを .docx ファイルとして保存します。
  type: HowTo
- questions:
  - answer: フィールドは挿入されますが、`document.UpdateFields()` はバーコードを空白のままにし、Aspose.Words は無効なバーコードタイプであることを示す
      `FieldException` をスローします。
    question: '`displayBarcodeField.BarcodeType` にサポートされていない値を割り当てた場合、どうなりますか？'
  - answer: '`UpdateFields()` はバーコード画像をレンダリングするため、複数の `FieldDisplayBarcode` オブジェクトを挿入し、最後に一度だけ
      `document.UpdateFields()` を呼び出してすべてをレンダリングできます。'
    question: 各バーコード挿入後に `document.UpdateFields()` を呼び出す必要がありますか？それとも、すべてのフィールドを追加した後に一度だけ更新すればよいですか？
  - answer: '両プロパティは `0x` プレフィックスが付いた 16 進数 RGB 文字列（例: 赤の場合は "0xFF0000"）を期待します。その他の形式は無視され、デフォルトの色が使用されます。'
    question: '`BackgroundColor` と `ForegroundColor` のカラー文字列はどの形式で指定すべきですか？'
  - answer: はい。`displayBarcodeField.BarcodeValue` に新しい文字列を設定し、`document.UpdateFields()`
      を再度呼び出すだけで、レンダリングされた画像を更新できます。
    question: フィールドを挿入した後にバーコードのペイロードを変更できますか？
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Aspose.Words で DataMatrix バーコードを挿入する
og_description: .NET コード数行で Word ファイルに DataMatrix バーコードを追加する方法を学びましょう。
og_image_alt: Aspose.Words for .NET を使用して Word ドキュメントに DataMatrix バーコードを挿入およびレンダリングする方法を示すガイド
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word ドキュメントに DataMatrix バーコードを挿入する
Aspose.Words for .NET を使用すれば、プログラムから Word ドキュメントに DataMatrix バーコードを追加できます。このチュートリアルでは、新しいドキュメントを作成し、DISPLAYBARCODE フィールドを挿入し、そのタイプを DataMatrix に設定し、Document と DocumentBuilder クラスを使用してバーコード画像をレンダリングする方法を示します。手順に従って、.docx ファイル内に直接印刷可能なバーコードを生成しましょう。

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

**Q: `displayBarcodeField.BarcodeType` にサポートされていない値を割り当てた場合、どうなりますか？**  
A: フィールドは挿入されますが、`document.UpdateFields()` はバーコードを空白のままにし、Aspose.Words は無効なバーコードタイプであることを示す `FieldException` をスローします。

**Q: 各バーコード挿入後に `document.UpdateFields()` を呼び出す必要がありますか？それとも、すべてのフィールドを追加した後に一度だけ更新すればよいですか？**  
A: `UpdateFields()` はバーコード画像をレンダリングするため、複数の `FieldDisplayBarcode` オブジェクトを挿入し、最後に一度だけ `document.UpdateFields()` を呼び出してすべてをレンダリングできます。

**Q: `BackgroundColor` と `ForegroundColor` のカラー文字列はどの形式で指定すべきですか？**  
A: 両プロパティは `0x` プレフィックスが付いた 16 進数 RGB 文字列（例: 赤の場合は "0xFF0000"）を期待します。その他の形式は無視され、デフォルトの色が使用されます。

**Q: フィールドを挿入した後にバーコードのペイロードを変更できますか？**  
A: はい。`displayBarcodeField.BarcodeValue` に新しい文字列を設定し、`document.UpdateFields()` を再度呼び出すだけで、レンダリングされた画像を更新できます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}