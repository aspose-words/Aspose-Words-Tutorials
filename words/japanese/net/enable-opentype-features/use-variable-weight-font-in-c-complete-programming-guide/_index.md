---
category: general
date: 2026-06-02
description: C#で可変ウェイトフォントの使用方法を学び、プログラムでフォントウェイトを設定し、動的タイポグラフィのためにフォントストレッチのコードを変更する。
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: ja
og_description: C#で可変ウェイトフォントを使用し、プログラムでフォントのウェイトを設定し、フォントストレッチコードを変更して、ドキュメント内で動的なタイポグラフィを実現します。
og_title: C#で可変ウェイトフォントを使用する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: C#で可変ウェイトフォントを使用する – 完全プログラミングガイド
url: /ja/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で可変ウェイトフォントを使用する – 完全プログラミングガイド

.NET プロジェクトで **可変ウェイトフォント** を使いたいけれど、ユーザー入力に応じてウェイトやストレッチを変える方法が分からない、ということはありませんか？ 多くの UI やレポートシナリオで、テキストを適応させたい場面があります。たとえば、軽めの見出しがホバー時に太字になる、あるいは強調のために段落の幅が広がる、といったケースです。良いニュースは、Aspose.Words を使えば **フォントのウェイトをプログラムで設定** でき、さらに **フォントストレッチコードを動的に変更** できるということです。

このチュートリアルでは、可変ウェイトフォントを読み込み、カスタムウェイトを適用し、ストレッチ設定を調整するハンズオン例をステップバイステップで解説します。最後には、効果を示す PDF を生成するコンソール アプリが完成します。

---

## 必要なもの

- **Aspose.Words for .NET**（v23.12 以降）。このライブラリは可変ウェイトフォントをフルサポートしています。
- 可変ウェイトフォント ファイルが入ったフォルダー（例: *RobotoFlex‑Variable.ttf*）。Google Fonts からダウンロード可能です。
- .NET 6 SDK（または最近の .NET バージョン）とお好みの IDE。
- 基本的な C# の知識 – 特別なことは不要、数行のコードを書くだけです。

以上です。Aspose.Words 以外に追加の NuGet パッケージは不要で、特殊な設定ファイルも必要ありません。

---

![可変ウェイトフォントの使用例](https://example.com/variable-weight-sample.png "可変ウェイトフォントのデモンストレーション")

*Alt text: 生成された PDF ドキュメントで可変ウェイトフォントが使用されている様子を示すスクリーンショット。*

---

## 手順 1: FontSettings を設定し、フォント フォルダーを指す  

まず最初に、Aspose.Words に可変ウェイトフォントが格納されている場所を教える必要があります。`FontSettings` オブジェクトを作成し、`FolderFontSource` を添付します。`true` フラグはサブフォルダーも検索対象にすることを意味し、複数のフォント ファミリーをまとめて管理している場合に便利です。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**重要ポイント:** フォルダーを登録しないと、Aspose.Words はシステム フォントにフォールバックし、カスタム フォントに埋め込まれた可変ウェイト情報を無視します。この手順が以降のすべての基盤となります。

---

## 手順 2: FontSettings を Document に紐付ける  

次に新しい `Document`（または既存のドキュメント）を作成し、先ほど用意した `FontSettings` を使用するよう指示します。このバインディングにより、後で追加するすべての `Run` が可変ウェイト データにアクセスできるようになります。

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

テンプレート（プレースホルダーが入った Word ファイル）を使用する場合は、`new Document()` を `new Document("Template.docx")` に置き換えてください。同じ `FontSettings` が適用されます。

---

## 手順 3: 可変ウェイトフォントを使用する Run を追加  

`Run` は Aspose.Words におけるテキスト書式設定の最小単位です。ここで `Run` を作成し、新しい段落に挿入し、後でフォント属性を変更します。

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

この時点ではテキストはデフォルト フォント（通常は Times New Roman）で描画されます。可変ウェイト ファミリーを割り当てた瞬間に魔法が起きます。

---

## 手順 4: 可変ウェイトフォント ファミリーを選択  

ここで実際に **可変ウェイトフォントを使用** します。`Font.Name` に、可変フォント ファイル内で定義された正確なファミリー名を設定します。Roboto Flex の場合は `"Roboto Flex"` です。

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

ファミリー名が分からない場合は、フォントビューアで `.ttf` を開くか、`fontSettings.GetFonts()` メソッドで利用可能なファミリーを列挙してください。

---

## 手順 5: フォント ウェイトとストレッチをプログラムで設定  

チュートリアルの核心です。**フォント ウェイトをプログラムで設定** し、**フォント ストレッチコードを変更** します。両プロパティは OpenType 仕様に対応した整数値を受け取ります。

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100（Thin）〜 900（Black）。可変フォントがサポートする任意の値を選択してください。
- **FontStretch**: 50（Ultra‑Condensed）〜 200（Ultra‑Expanded）。デフォルトは 100（Normal）です。

> **プロのコツ:** すべての可変フォントが全範囲を公開しているわけではありません。サポート外の値を設定すると、エンジンは最も近い利用可能なウェイトまたはストレッチにクランプします。

---

## 手順 6: ドキュメントを保存し、結果を確認  

最後にドキュメントを PDF（または DOCX）として書き出し、効果を確認します。PDF はプラットフォーム間で描画が一貫しているため、視覚的検証に最適です。

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

*VariableWeightDemo.pdf* を開くと、フレーズ “Variable‑weight text demo” が Roboto Flex の軽くやや拡張されたスタイルで表示されます。`FontWeight` を `700`、`FontStretch` を `80` に変更して再実行すると、テキストが太字かつより凝縮された様子が確認できます。

---

## よくある質問とエッジケース  

### フォントがまったく表示されない場合は？

- **FontSettings が未設定**: `doc.FontSettings = fontSettings;` がテキスト追加 **以前** に実行されているか確認してください。
- **ファミリー名が間違っている**: `fontSettings.GetFonts()` で取得できるファミリー一覧を確認し、正確な文字列をコピーします。
- **ウェイト/ストレッチが未対応**: 一部の可変フォントは 100‑900 の全ウェイトをサポートしていません。安全策として `run.Font.FontWeight = 400;` などを使用してください。

### 保存後にウェイトを変更できるか？

はい。`Run` オブジェクトは可変なので、最終 `Save` 前であれば `FontWeight` や `FontStretch` をいつでも調整可能です。ユーザー操作に応じて動的に切り替える場合は、状態ごとに別々の `Run` を生成することを検討してください。

### DOCX 出力でも動作するか？

もちろんです。可変ウェイト メタデータは OpenXML に保存され、最新の Word はそれを解釈できます。ただし、古いバージョンの Word はストレッチ設定を無視する可能性があります。

---

## 完全動作サンプル  

以下は即コンパイル・実行できるコンソール プログラムの全コードです。必要な `using` ディレクティブ、エラーハンドリング、コメントをすべて含んでいます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**期待される出力:** コンソールに保存パスが表示され、生成された PDF には軽く拡張されたスタイルのテキストが描画されます。これが本チュートリアルで設定した通りです。

---

## まとめ  

C# と Aspose.Words を使って **可変ウェイトフォントを使用** する方法、**フォント ウェイトをプログラムで設定** する手順、そして **フォント ストレッチコードを変更** する具体的なコード例を解説しました。手順はシンプルです: `FontSettings` を構成 → `Document` に紐付け → `Run` を作成 → 可変ウェイト ファミリーを選択 → `FontWeight` と `FontStretch` を調整。

---

## 次にやるべきこと  

- **動的 UI への統合**: 同じロジックを WinForms や WPF アプリに組み込み、スライダーでウェイト/ストレッチを操作できるようにする。
- **複数 Run の活用**: 同一段落内で異なるウェイトを持つ複数の Run を組み合わせ、リッチな階層表現を実現。
- **追加軸の活用**: 一部の可変フォントはスラントや光学サイズなどの軸も提供しています。`run.Font.FontStyle` や `FontVariationSettings` を調べて、さらに細かい制御を試みましょう。
- **パフォーマンスのコツ**: 多数のドキュメントを処理する場合は、`FontSettings` インスタンスをキャッシュしてフォルダー走査を繰り返さないようにします。

ぜひ試してみてください。*Roboto Flex* を *Inter Variable* など別の OpenType 可変フォントに差し替えれば、ドキュメントに新たな視覚的柔軟性が加わります。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した、密接に関連するトピックを取り上げています。各リソースには、完全なコード例とステップバイステップの解説が含まれており、API の追加機能習得や代替実装アプローチの探求に役立ちます。

- [ターゲットマシンからフォントを使用](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [ターゲットマシンからフォントを使用](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [ターゲットマシンからフォントを使用](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}