---
category: general
date: 2026-09-21
description: C# を使用して、隠し楕円が入った空白の Word ドキュメントを作成します。Word で図形を非表示にする方法と、プログラムで非表示の図形を生成する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: ja
lastmod: 2026-09-21
og_description: C# を使用して、非表示の楕円が含まれる空白の Word ドキュメントを作成します。このガイドでは、Word で図形を非表示にする方法と、プログラムで非表示の図形を作成する方法を示します。
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: C#で非表示の楕円形が入った空白のWord文書を作成する
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: C#で空白のWord文書を作成し、非表示の楕円形を追加する方法
url: /ja/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#で空白のWord文書を作成し、非表示の楕円形を追加する方法

空白のWord文書に見えないグラフィックを含める必要がある場合、このガイドがその手順を正確に示します。チュートリアルの最後までに、.docx ファイルは見た目は空ですが、レイアウトからは隠された楕円形が格納されている状態になります。

Aspose.Words for .NET を使用して文書を作成し、楕円形を挿入、非表示に設定し、ファイルを保存します。手順には **楕円形オブジェクトの作成方法**、**Word でシェイプを非表示にする正しい方法**、そして任意の .NET プロジェクトで動作する **非表示シェイプの作成コード** が含まれます。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0 SDK 以降  
* Visual Studio 2022（または任意の C# エディタ）  
* Aspose.Words for .NET のライセンスまたは無料評価版  
* C# の基本的な構文に関する知識  

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## Aspose.Words で空白の Word 文書を作成する

最初のステップは空の Word ファイルを生成することです。これにより、後で非表示グラフィックを挿入できるクリーンなキャンバスが得られます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**空白の文書から開始する理由** – 空のファイルから始めることで、不要なコンテンツが非表示シェイプに干渉することを防ぎます。また、ファイルサイズを最小限に抑えられるため、後でテンプレートとして使用する際に便利です。

## 空白文書内に楕円形を作成する方法

次に `DocumentBuilder` を取得してコンテンツを追加します。ビルダーを使うと、シェイプを正確な位置に配置できます。

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**解説** – `ShapeType.Ellipse` は Aspose.Words に円形に近い図形を描画させます。幅と高さはポイント単位で指定します（1 pt ≈ 1/72 インチ）。デザイン要件に合わせてこれらの値を調整してください。

## Word でシェイプを非表示にしてレイアウトに現れないようにする

非表示のシェイプは文書の XML に残ります。メタデータや条件付き書式、後からのプログラムによる変更に利用できます。非表示にするには `Hidden` プロパティを `true` に設定します。

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**シェイプを非表示にする理由** – 非表示シェイプはレイアウトエンジンに無視されるため、ページは完全に空白に見えます。しかしシェイプデータは残るため、マーカーやブックマーク、カスタム XML などを格納するのに有用です。

## 非表示シェイプ付き文書を保存する

最後にファイルをディスクに書き出します。保存された `.docx` は Microsoft Word で開くと見えるコンテンツはありませんが、非表示の楕円形は依然として存在します。

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**検証方法** – 生成されたファイルを Word で開き、`Alt+F9` でフィールドコードの表示切替、`Ctrl+A` → `Ctrl+Shift+F9` で非表示オブジェクトを表示します。ページ上には何も表示されませんが、文書の XML（`word/document.xml`）内に楕円形の `<w:pict>` 要素が存在することが確認できます。

---

## 完全な実行可能サンプル

以下は新しいコンソールプロジェクトにコピー＆ペーストできる完全プログラムです。`using` ディレクティブと `Main` メソッドをすべて含んでいるので、追加のスキャフォールディングは不要です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**期待される出力** – プログラム実行時にコンソールにファイルパスが表示され、生成された Word ファイルには可視オブジェクトがありません。`.docx` は zip アーカイブであるため、zip ツールで展開し `word/document.xml` を確認すると、楕円形を記述した `<w:pict>` 要素が見つかります。

---

## よくあるバリエーションとエッジケース

| シナリオ | 変更点 | 重要な理由 |
|----------|--------|------------|
| **別のシェイプ** | `ShapeType.Ellipse` を `ShapeType.Rectangle`、`ShapeType.Line` などに置き換える | 同じワークフローで他のグラフィックを非表示にできる |
| **複数の非表示シェイプ** | `InsertShape` を複数回呼び出し、各シェイプの `Hidden = true` を設定 | マーカーやプレースホルダーのコレクションを埋め込むのに便利 |
| **条件付き表示** | `shape.Visible = false` と `shape.Hidden = true` を併用 | 古い Word バージョンは `Visible` の扱いが異なる場合があるため、両方設定するとすべてのケースをカバー |
| **ストリームへの保存** | `doc.Save(path)` を `doc.Save(stream, SaveFormat.Docx)` に置き換える | HTTP で直接送信したり、データベースに保存したりできる |
| **スタイルの適用** | 挿入後に `ellipse.FillColor`、`ellipse.LineWeight` などを変更してから非表示にする | シェイプのスタイル情報は XML に保持され、後で非表示を解除したときに活用できる |

**プロのコツ**：対象となる Word バージョン（例：Word 2019、Word 365）で必ず非表示シェイプをテストしてください。複雑なページレイアウトと組み合わせた際に、描画の微妙な差異が発生することがあります。

---

## FAQ（よくある質問）

**Q: シェイプを非表示にすると文書サイズは変わりますか？**  
A: シェイプの XML は数百バイト程度の増加にとどまるため、ほとんどのユースケースで無視できるサイズです。実質的には空の文書と同等のサイズです。

**Q: 後からプログラムでシェイプを再表示できますか？**  
A: はい。文書をロードし、`doc.GetChildNodes(NodeType.Shape, true)` でシェイプを取得し、`shape.Hidden = false` と設定すれば再表示できます。

**Q: 非表示シェイプは印刷時に表示されますか？**  
A: いいえ。非表示オブジェクトは印刷レイアウトから除外されるため、印刷されたページは空白のままです。

**Q: この手法は Office Open XML（OOXML）専用ですか？**  
A: `Hidden` プロパティは OOXML 仕様の一部です。OOXML を完全に実装している Word、LibreOffice、Google Docs などのワードプロセッサはこのフラグを尊重します。

---

## 結論

これで **空白の Word 文書の作成**、**楕円形の作成**、**Word でシェイプを非表示にする**、そして **Aspose.Words for .NET を使った非表示シェイプの作成** ができるようになりました。チュートリアルでは、空ファイルの初期化からシェイプの挿入・非表示・保存までの全ライフサイクルを網羅し、検証手順や一般的なバリエーションも紹介しました。

次に試してみると良いでしょう：

* メタデータ用の非表示テキストボックスを追加（`hide shape in word` 手法をテキストに適用）  
* カスタム XML パートを使用して、非表示シェイプと共に構造化データを格納  
* 非表示シェイプを含む文書を PDF に変換し、非表示要素を保持したまま出力  

さまざまなシェイプや可視性設定を実験し、Word ファイル内の軽量データストアとして非表示コンテンツを活用してください。

Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、代替実装アプローチを自プロジェクトで試したりするのに役立ちます。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}