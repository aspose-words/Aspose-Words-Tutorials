---
category: general
date: 2026-03-19
description: Aspose.Words と可変フォントを使用して Word 文書を作成します。C# でフォントの太さを変更し、幅を設定し、バリエーションを定義する方法を学びます。
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: ja
og_description: Aspose.Words を使用して可変フォントで Word 文書を作成します。このチュートリアルでは、フォントの読み込み、フォントウェイトの変更、フォント幅の設定、フォントバリエーションの定義方法を示します。
og_title: 可変フォントでWord文書を作成する – 完全ガイド
tags:
- Aspose.Words
- C#
- Variable Font
title: 可変フォントでWord文書を作成する – ガイド
url: /ja/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 変数フォントを使用したWord Documentの作成 – ガイド

モダンな変数フォントを使用した **Word Document** を作成したいと思ったことはありませんか？でも、どこから始めればいいか分からないことも多いでしょう。多くのプロジェクト—たとえば動的レポートやブランド一貫性のあるパンフレット—では、**フォントのウェイトをリアルタイムで変更**できることが大きなメリットになります。

このチュートリアルでは、変数フォントを Aspose.Words にロードし、ウェイトと幅を設定し、最終的に設計どおりの外観になる DOCX を保存するまでの全工程を順を追って解説します。曖昧な説明はなく、すぐに C# プロジェクトに貼り付けて実行できる具体的なコードだけを提供します。

## 本チュートリアルで学べること

- `FontSettings` を使用して Aspose.Words に **変数フォント** ファイルをロードする方法。
- `wght`（ウェイト）や `wdth`（幅）などの **フォントバリエーション** 軸を **定義** する構文。
- 単一の `Run` に対して **フォント幅を設定** し、**フォントウェイトを変更** する方法。
- 一般的な落とし穴（グリフ欠損、フォルダー パスの誤りなど）をトラブルシューティングするためのヒント。
- すぐにコピー＆ペーストしてテストできる、完全な実行可能サンプル。

> **前提条件**: .NET 6+（または .NET Framework 4.6+）、NuGet 経由でインストールされた Aspose.Words for .NET、そしてローカルの *Fonts* フォルダーに配置した *RobotoFlex.ttf* のような変数フォントファイル。

---

## ステップ 1 – 変数フォントを Aspose.Words にロードする

まず、Aspose.Words にカスタムフォントの検索場所を指定する必要があります。`FontSettings` クラスがその主要な役割を担います。  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**重要性**: フォルダーを登録しないと、Aspose.Words はシステムフォントにフォールバックし、後で適用しようとする OpenType バリエーション データを無視します。特定のディレクトリを指すことで、コード実行時に *RobotoFlex*（または他の変数フォント）が必ず見つかることが保証されます。

> **プロ・ティップ**: `SetFontsFolder` の第2引数を `true` に設定すると、Aspose がサブフォルダーも検索します。フォントをスタイルやウェイト別に整理している場合に便利です。

---

## ステップ 2 – 新しい Document を作成し、サンプルテキストを追加

フォントエンジンが検索場所を認識したので、空の `Document` を作成し、`Run` を含む段落を挿入します。  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**動作概要**: `Run` は均一な書式設定を持つ連続したテキスト片を表します。先に作成することで書式ロジックを分離でき、後で別々の `Run` に異なるバリエーション軸を適用する際に便利です。

---

## ステップ 3 – 目的のバリエーション軸（ウェイトと幅）を定義

変数フォントは実行時に調整できる *軸* を提供します。最も一般的なのは `wght`（フォントウェイト）と `wdth`（フォント幅）です。Aspose.Words はこれを `OpenTypeFontVariation` コレクションで表現します。  

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**数値の意味**: OpenType 仕様では、`wght` はフォントの最小から最大のウェイト（通常 100〜900）までの範囲です。**700** の値は太字に相当します。`wdth` も同様で、**100** がデフォルト（標準）幅を示し、100 未満の値は字形を狭めます。

> **エッジケース**: 一部の変数フォントは特定の軸をサポートしていません。未対応のタグを指定すると、Aspose は黙って無視します。フォントの仕様（通常は `.ttf` または `.otf` ファイルのメタデータに記載）を必ず確認してください。

---

## ステップ 4 – フォント名を使用して Run にバリエーションを適用

ここでバリエーション データを実際のテキストに結び付けます。`FontInfo` クラスはフォントファミリ名と軸コレクションを保持します。  

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**解説**: `FontInfo` を設定することで、通常の `Font.Name` プロパティをバイパスし、エンジンに完全修飾されたフォント構成を渡します。これが、カスタム軸付きの変数フォントを Aspose.Words に使用させる唯一の方法です。

> **よくあるミス**: フォントファイル内の正確なファミリ名（この例では `RobotoFlex`）と一致させないことです。タイプミスがあると Aspose はデフォルトフォントにフォールバックし、バリエーションが失われます。

---

## ステップ 5 – Document を保存し、結果を確認

最後に、Document をディスクに書き出します。生成された DOCX には変数フォントの指示が含まれ、Microsoft Word（2016 以降）で正しくレンダリングされます。  

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Word で生成されたファイルを開き、テキストを選択して **フォント** ダイアログを確認してください。*Roboto Flex* が一覧に表示され、テキストは周囲の内容よりも太字で表示されるはずです—まさに `wght = 700` の設定通りです。

> **検証のコツ**: テキストに変化が見られない場合は、フォントファイルが本当に `wght` 軸をサポートしているか再確認してください。中には `ital`（イタリック）や `opsz`（光学サイズ）だけを提供する“変数”フォントもあります。

---

## オプション: さらにバリエーションを追加 – 幅を動的に変更

別の段落で *フォント幅を設定* したい場合は、ステップ 3‑4 を新しい `OpenTypeFontVariation` コレクションで繰り返すだけです。  

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

これで 2 つの Run ができます—1 つは太字、もう 1 つはやや幅が広い—同一文書内で **フォントウェイトの変更** と **フォント幅の設定** の両方を示しています。

---

## 完全な動作例

以下のスニペットを新しいコンソール アプリ（`Program.cs`）にコピーして実行してください。`Fonts` フォルダーに `RobotoFlex.ttf`（またはお好みの変数フォント）が含まれていることを確認してください。  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**期待される出力**: `VariableFont.docx` ファイルで、フレーズ “Variable‑weight text” が `wght = 700` 軸のおかげで太字になり、幅はデフォルトのままです。

---

## よくある質問 & エッジケース

| Question | Answer |
|----------|--------|
| *フォントが見つからない場合はどうすればいいですか？* | フォルダー パスを確認し、ファイル名が一致していること、プロセスに読み取り権限があることを確認してください。また `fontSettings.GetFonts()` を呼び出して検出されたフォントを一覧表示することもできます。 |
| *異なるバリエーションを持つ複数の Run を組み合わせられますか？* | もちろん可能です。各 `Run` はそれぞれ独自の `FontInfo` を持てます。各 Run に対してステップ 3‑4 を繰り返すだけです。 |
| *古いバージョンの Word は変数フォントをサポートしていますか？* | Word 2016（Build 16.0.8001）で基本的なサポートが導入されました。古いバージョンを対象とする場合、文書は最も近い静的フォントにフォールバックします。 |
| *設定できる軸の数に制限はありますか？* | フォントが定義する任意の数の軸を設定できます。一般的なタグは `wght`、`wdth`、`ital`、`opsz`、`GRAD` です。未対応のタグを指定しても効果はありません。 |
| *欠損したグリフをデバッグするには？* | `FontSettings.GetFontSources()` でロードされたフォントを確認し、`FontInfo.HasGlyph(char)` で個々の文字をテストできます。 |

---

## 結論

数ステップで、変数フォントの力を活用した **Word Document** ファイルの作成方法を示しました。これにより **フォントウェイトの変更**、**フォント幅の設定**、**変数フォントのロード**、**フォントバリエーション軸の定義** がすべて Aspose.Words for .NET で実現できます。

基本的な考え方はシンプルです。フォントフォルダーを登録し、目的の軸を記述し、`Run` に付与して保存するだけです。ここからはこの手法をセクション全体やテーブル、さらにはブランド固有のレポートをプログラムで生成するまで拡張できます。

**次のステップ**: `RobotoFlex` を別の変数フォントに置き換えてみたり、`ital`（イタリック）軸を試したり、同じ文書の PDF バージョンを Aspose.PDF で生成してみてください。同じパターン、すなわちロード → 定義 → 適用 → 保存 が適用されます。

コーディングを楽しんで、変数フォントがもたらす柔軟性を Word 自動化プロジェクトで活かしてください！  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}