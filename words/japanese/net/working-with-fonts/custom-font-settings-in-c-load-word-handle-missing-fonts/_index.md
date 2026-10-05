---
category: general
date: 2026-03-08
description: カスタムフォント設定を使用すると、フォント設定を行い、Word 文書を安全に読み込み、Aspose.Words で欠落フォントを処理できます。
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: ja
og_description: カスタムフォント設定により、フォント設定を行い、Word 文書を安全に読み込み、欠落フォントを Aspose.Words で処理できます。
og_title: C# のカスタムフォント設定 – Word の読み込みと欠落フォントの処理
tags:
- Aspose.Words
- C#
- Font Management
title: C# のカスタムフォント設定 – Word の読み込みと欠損フォントの処理
url: /ja/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# におけるカスタムフォント設定 – Word の読み込みと欠損フォントの処理

Word ファイルがインストールされていないフォントを参照しているとき、**カスタムフォント設定**はどのように機能するか疑問に思ったことはありませんか？よくある問題として、あるマシンでは文書が正常に表示されても、別のマシンではすべての段落がフォールバックフォントに置き換わってしまいます。  

良いニュースです！Aspose.Words を使えば、**フォント設定を行い**、**Word 文書を読み込み**、**欠損フォントを処理**する一連の流れをすっきりと実装できます。以下に、完全に実行可能なサンプルと各手順の「なぜ」を示します。

## 学べること

このガイドでは次の内容を扱います：

* `LoadOptions` オブジェクトを作成し、`FontSettings` インスタンスを添付する方法。  
* 警告コールバックを登録して、どのフォントが置き換えられたかを確認できるようにする方法。  
* フォントが欠損している可能性のある DOCX ファイルを読み込み、置き換え情報をコンソールに出力する方法。  

最後まで読めば、欠損フォントのシナリオがすべてログに記録され、後から対処できる自信を持って C# アプリを出荷できるようになります。

> **前提条件:** NuGet 経由でインストールした Aspose.Words for .NET（v23.12 以降）と、C# コンソールアプリの基本的な知識。

---

## カスタムフォント設定 – LoadOptions の構成

最初に必要なのは `LoadOptions` オブジェクトです。これにより Aspose.Words が受け取るファイルの取り扱い方法を指示します。新しい `FontSettings` インスタンスを割り当てることで、カスタムフォントの検索場所をライブラリに提供します。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**重要なポイント:**  
`FontSettings` を省略すると、Aspose.Words はシステム既定のフォントコレクションにフォールバックします。その結果、欠損フォントは黙って置き換えられ、どのフォントが置き換えられたか分からなくなります。明示的に `FontSettings` コンテナを作成すれば、検索プロセスを完全にコントロールできます。

---

## LoadOptions にフォント設定を適用

`FontSettings` オブジェクトができたら、次はそれをどこに指し示すかです。通常は、アプリに同梱するフォントが入ったフォルダーを追加します：

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*プライベートフォルダーがない場合は、このブロックを省略しても構いません。Aspose.Words は警告コールバックを通じて欠損フォントを報告します。*

**プロのコツ:** フォントがサブフォルダーに散在している場合は `recursive: true` フラグを使用してください。個別にパスを追加する手間が省けます。

---

## カスタムフォント設定で Word 文書を読み込む

オプションが整ったら、文書の読み込みはとても簡単です。`Document` コンストラクタはファイルパスと先ほど作成した `LoadOptions` を受け取ります。

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**内部で何が起きているか:**  
Aspose.Words は DOCX を解析し、すべての `<w:font>` 参照をチェックし、提供された `FontSettings` を参照します。フォントが見つからない場合、`FontSubstitution` タイプの警告が発生します。次に示すカスタムハンドラがその警告を捕捉します。

---

## 警告コールバックで欠損フォントを処理

`IWarningCallback` インターフェイスを使うと、読み込み中に発生した問題に対処できます。実装はシンプルです：

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

文書が読み込まれると、欠損フォントごとに次のような行が出力されます：

```
Font substituted: Arial -> Liberation Sans
```

**ログに残すべき理由:**  
本番環境ではこれらのメッセージをファイルやテレメトリシステムに転送すれば、どのフォントをバンドルまたはライセンス取得すべきかすぐに把握できます。

---

## 完全動作サンプル

以下は、すべてをひとつにまとめたコンソールプログラムです。新規 .NET Core コンソールプロジェクトに貼り付けて **Run** してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**期待される出力**（`input.docx` が未インストールのフォントを使用している場合）：

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

すべてのフォントが揃っていれば、最終確認行だけが表示されます。

---

## よくある質問とエッジケース

| 質問 | 回答 |
|----------|--------|
| **欠損フォントを PDF に埋め込むにはどうすればよいですか？** | 読み込み後に `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` を呼び出し、`doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;` で埋め込みを有効にします。 |
| **警告を記録せずに抑制したい場合は？** | `loadOptions.WarningCallback = null;` と設定するか、フォント以外の警告を無視するようコールバックを実装します。 |
| **`.doc` や `.rtf` ファイルでも同様に機能しますか？** | はい。`LoadOptions` は Aspose.Words がサポートするすべての形式で共通に使用できます。 |
| **コールバックはスレッドセーフですか？** | コールバックは文書を読み込むスレッド上で実行されるため、コンソールへの書き込みは安全です。マルチスレッド環境では、Concurrent コレクションやロギングフレームワークを利用してください。 |

---

## プロのコツ & 落とし穴

* **プロのコツ:** ターゲットマシンにインストールされていないフォントを同梱する場合は、`SetFontsFolder` に渡すフォルダーにそのフォントを入れておくと、描画が決定的になります。 |
* **ライセンスに注意:** フォントによっては埋め込みに商用ライセンスが必要です。バンドル前に必ずフォントの EULA を確認してください。 |
* **パフォーマンス注意点:** 大量のフォントをロードすると文書解析が遅くなることがあります。必要なフォントだけをフォルダーに残すようにしましょう。 |
* **エッジケース:** 文書がフォントを *PostScript 名* で参照している場合でも、検索パスにフォントファイルがあれば Aspose.Words は正しく解決します。 |

---

## 結論

これで **カスタムフォント設定** を C# で使用するための、実践的かつ本番環境向けのパターンが完成しました。`LoadOptions` を構成し、警告コールバックを登録し、必要に応じてプライベートフォントフォルダーを指定すれば、**フォント設定を行い**、**Word 文書を確実に読み込み**、欠損フォントを適切に処理できます。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}