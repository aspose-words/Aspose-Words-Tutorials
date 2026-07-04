---
category: general
date: 2026-05-26
description: C# と Aspose.Words を使用して Word 文書を作成し、長方形の図形を挿入、塗りつぶし色を設定し、影効果を追加する – ステップバイステップガイド.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: ja
og_description: Aspose.Words を使用して C# で Word ドキュメントを作成します。矩形シェイプの挿入方法、塗りつぶし色の設定、影効果の追加方法を学びましょう。
og_title: Wordドキュメントを作成 – C#で長方形の図形と影を挿入
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Word文書の作成 – C#で長方形の図形と影を挿入
url: /ja/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word ドキュメントの作成 – C# で矩形シェイプと影を挿入

Microsoft Word を開かずに **Word ドキュメントを作成** できるか気になったことはありませんか？ 請求書、契約書、または大量のレポート生成といった自動化シナリオでは、.docx ファイルを作成し、シェイプを配置し、色を付け、場合によっては影を付けて仕上げる信頼できる方法が必要です。

このチュートリアルでは、Aspose.Words for .NET を使用して **Word ドキュメントを作成**、**矩形シェイプを挿入**、塗りつぶしを適用し、**影を追加** する手順を詳しく解説します。最後まで実行すれば、任意の downstream ワークフローに流し込める保存可能なファイルが手に入ります。

また、**シェイプの挿入方法** を柔軟に行うコツや、**塗りつぶしの設定** が視覚的一貫性に与える影響についても触れます。余計な説明は省き、コピー＆ペーストしてすぐに動かせるコードだけを提供します。

## Prerequisites

始める前に以下を用意してください。

- .NET 6 以上（または .NET Framework 4.7 以上）をインストール
- 有効な Aspose.Words for .NET ライセンス（または一時的な評価キー）
- Visual Studio、Rider、またはお好みの C# IDE
- C# の基本構文に慣れていること（特別な知識は不要）

準備はできましたか？ それでは始めましょう。

## Step 1 – Create Word Document

最初に必要なのは空の Document オブジェクトです。これがすべてのコンテンツのキャンバスになります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` はメモリ上の .docx ファイルを表し、`DocumentBuilder` はテキスト、テーブル、シェイプを挿入するための便利な API を提供します。**Word ドキュメントをこの方法で作成** すると、UI や COM インタープロの必要がなく、純粋な .NET だけで即座に完了します。

## Step 2 – Insert Rectangle Shape

ドキュメントが用意できたので、**矩形シェイプを挿入** します。`InsertShape` メソッドは `ShapeType` 列挙体、幅、そして高さ（ポイント単位）を受け取ります。ここでは幅 150 ポイント、高さ 80 ポイント（約 2 × 1 インチ）の矩形を使用します。

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

内部では Aspose が `Shape` オブジェクトを生成し、現在の段落に追加し、スタイル設定用の参照を返します。これが **シェイプの挿入方法** の核心で、たった一行のコードで非常に強力です。

## Step 3 – How to Set Fill

塗りつぶしのないシェイプは白紙上で見えません。ここでは淡い水色の背景を設定します。

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

グラデーション、テクスチャ、画像塗りつぶしも可能ですが、サンプルはシンプルさを保つために単色にしています。これが **塗りつぶしの設定方法** で、読者が期待する視覚的手がかりを提供します。

## Step 4 – How to Add Shadow

影を付けると奥行きが生まれ、シェイプが際立ちます。Aspose.Words は `ShadowFormat` オブジェクトを公開しており、可視化の切り替え、色選択、ぼかし・距離・角度の微調整が可能です。

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

なぜこの値なのか？ 45° の角度は自然な右上からの光源を表し、ほどほどのぼかしで影を控えめに、短い距離でシェイプが浮きすぎないようにしています。自由に実験してみてください。たとえば角度を 135° に変えると、影は左下に落ちます。

## Step 5 – Save the Document

すべての処理が完了したら、ファイルをディスクに書き出します。好きなパスを指定してください。ただし、フォルダーが存在していることを確認してください。

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

`ShadowShape.docx` を Microsoft Word で開くと、淡い水色の矩形に柔らかなグレーの影が付いた状態が確認できます—まさにスクリプト通りです。

## Full Working Example

以下に、すべてをまとめたコピー＆ペースト可能な完全プログラムを示します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Expected Result

- **ShadowShape.docx** という名前のファイルが対象フォルダーに作成されます。
- Word で開くと、1 ページ目の中央に淡い水色の矩形が表示されます。
- 矩形は 45° の角度でグレーの影を落としており、控えめな 3‑D 効果が得られます。

## Common Questions & Edge Cases

**別のシェイプが必要な場合は？**  
`ShapeType.Rectangle` を `Ellipse`、`Star`、`Arrow` など他の列挙値に置き換えるだけです。残りのコードはそのまま使えます。

**シェイプ内にテキストを入れられますか？**  
はい。シェイプ作成後に `shape.AppendChild(new Paragraph(doc))` を呼び、続いて `Run` にテキストを挿入します。テキストの折り返しが必要な場合は `shape.TextBox` プロパティを設定してください。

**DPI や測定単位は？**  
Aspose はポイント単位で動作します（1 pt = 1/72 インチ）。センチメートルで指定したい場合は、28.35 を掛け算してください（1 cm ≈ 28.35 pt）。

**ライセンスは必須ですか？**  
評価版を使用すると、最初のページに透かしが入ります。正式ライセンスを取得すれば透かしが除去され、全 API が利用可能になります。

## Tips & Gotchas

- **プロのコツ:** シェイプを文書の最後に配置したい場合は、`builder.MoveToDocumentEnd()` を呼んでから挿入してください。
- **注意点:** 読み取り専用フォルダーに保存しようとすると `UnauthorizedAccessException` がスローされます。書き込み権限があることを確認しましょう。
- **パフォーマンス:** 大量生成（数百件）の場合は、テンプレートとして単一の `Document` インスタンスを再利用し、`doc.Clone(true)` でクローンすると初期化コストを削減できます。

## Conclusion

これで **Word ドキュメントを作成**、**矩形シェイプを挿入**、**塗りつぶしを設定**、そして **影を追加** する方法がマスターできました。上記のスニペットは、コンソールアプリ、Web API、バックグラウンドサービスなど、あらゆる C# プロジェクトに組み込める自己完結型ソリューションです。

次に挑戦できること例：

- 色やサイズが異なる複数シェイプの追加
- グラデーションや画像塗りつぶし（`shape.FillColor = ...` → `shape.FillPattern`）の活用
- テーブルと組み合わせた複雑なレポートレイアウトの構築

ぜひ試してパラメーターを調整し、数行のコードで自動生成された Word ファイルをよりプロフェッショナルに見せてみてください。Happy coding!

## Related Tutorials

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}