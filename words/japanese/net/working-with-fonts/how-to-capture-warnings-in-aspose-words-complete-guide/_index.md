---
category: general
date: 2026-03-13
description: Aspose.Wordsで文書を読み込む際に警告を取得する方法、欠落フォントの対処法やカスタムフォント設定の設定に関するヒント。完全なC#ソリューションを学びましょう。
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: ja
og_description: Aspose.WordsでWordファイルを読み込む際の警告取得方法、欠落フォントへの実践的な対処法とカスタムフォント設定の設定方法。
og_title: Aspose.Wordsで警告を取得する方法 – 完全ガイド
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Wordsで警告を取得する方法 – 完全ガイド
url: /ja/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で警告を取得する方法 – 完全ガイド

Aspose.Words がドキュメントを読み込む際に表示される **警告の取得方法** を考えたことはありますか？実際のプロジェクトでは、フォント置換のアラートや非推奨機能の通知、さらにはセキュリティ関連のメッセージが出ることがあります。これらを無視するのは、フロントガラスが割れたまま運転するようなものです—目的地にはたどり着くかもしれませんが、何かが壊れそうになる瞬間を知ることはできません。

良いニュースは、Aspose.Words がこれらのメッセージをインターセプトするためのシンプルなコールバックベースの方法を提供していることです。このチュートリアルでは、警告を取得するだけでなく、**欠落フォントの処理**や**カスタムフォント設定の設定**方法も示す **完全な C# サンプル** を順を追って解説します。

---

## 学べること

- カスタム `FontSettings` オブジェクトを組み込むように `LoadOptions` を設定する。  
- `FontSubstitution` イベントをフィルタリングする警告コールバックを登録する。  
- 警告の詳細をコンソール（または任意のロガー）に出力する。  
- 異なるプラットフォーム間で欠落フォントを優雅に処理できるようにソリューションを拡張する。  

このガイドの最後までに、任意の .NET プロジェクトに貼り付けてすぐに実行できるスニペットと、一般的な落とし穴を回避するための実用的なヒントが手に入ります。

---

## 前提条件

| Requirement | Why It Matters |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 or later) | 使用する API（`LoadOptions`、`IWarningCallback`）がここにあります。 |
| **.NET 6+** (or .NET Framework 4.7.2+) | 最新の言語機能によりコードがすっきりします。 |
| **A sample DOCX** (named `input.docx`) placed in a known folder | 読み込んで警告を発生させるためのサンプルが必要です。 |
| **A console or logging framework** (optional) | 取得した警告を確認するために使用します。 |

Aspose.Words 以外に追加の NuGet パッケージは必要ありません。

---

## 手順 1: カスタムフォント設定を構成する  

ドキュメントを読み込む前に、Aspose.Words にフォントの検索場所を指示できます。これが **カスタムフォント設定の設定** 部分です。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**これが重要な理由:**  
DOCX がマシンにインストールされていないフォントを参照している場合、Aspose.Words は必要なフォントが入ったフォルダーを設定していない限り、バックアップフォントに静かに置き換えてしまいます。カスタムフォルダーを設定することで、最初から「フォント置換」警告が出る可能性を減らせます。

> **プロのコツ:** Linux では `fonts-dejavu-core` パッケージや、ドキュメントが依存する任意の TrueType コレクションを追加する必要があるかもしれません。

---

## 手順 2: 警告コールバックを登録する  

Aspose.Words は `IWarningCallback` を実装しています。ここでは、欠落フォントや置換フォントに関する警告だけを出力する小さなハンドラを作成します。

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**これが重要な理由:**  
**欠落フォントの処理** シナリオが可視化されます。どのフォントが置換されたかを推測する代わりに、たとえば “Font 'Calibri' was substituted with 'Arial'” のような明確な説明が得られます。生成された PDF や印刷レポートのレイアウト問題をデバッグする際に非常に役立ちます。

---

## 手順 3: 設定したオプションでドキュメントを読み込む  

いよいよ、先ほど準備した `LoadOptions` を使ってドキュメントをメモリに読み込みます。

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

ソースファイルが `C:\MyFonts` に存在しないフォントを使用している場合、以下のような出力が表示されます。

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

この行が、求めていた **警告の取得方法** の結果です。

---

## 手順 4: 完全動作サンプル（コピー＆ペースト可能）

以下はコンパイル可能な完全プログラムです。新しいコンソールプロジェクトに貼り付けて実行してください。パスが実際の環境に合わせて正しく設定されていることを確認してください。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**期待される出力:**  

- すべてのフォントが利用可能な場合:  
  `Document processed. Check console for any warning messages.`  

- フォントが欠落している場合:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## 手順 5: 一般的なバリエーションとエッジケース  

| Situation | What to Adjust |
|-----------|----------------|
| **Multiple font folders** | 各追加ロケーションに対して `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` を呼び出す。 |
| **Suppress all warnings** | `Warn` を実装して本体を空にするか、`loadOptions.WarningCallback = null;` に設定してすべての警告を抑制する。 |
| **Capture other warning types** | `info.WarningType` を `WarningType.DeprecatedFeature`、`WarningType.UnexpectedContent` などと比較して他の警告タイプを取得する。 |
| **Running on Linux/macOS** | フォントフォルダーに Linux 互換の `.ttf`/`.otf` ファイルが含まれていることを確認し、必要に応じて `libfontconfig` をインストールする。 |
| **Large documents** | メモリ負荷を減らすためにドキュメントをストリーミング（`LoadOptions.LoadFormat = LoadFormat.Docx;`）することを検討する。 |

これらのシナリオを事前に想定しておくことで、開発環境から CI パイプラインやクラウド VM へ移行した際の予期せぬ問題を回避できます。

---

## 手順 6: ビジュアルでの確認（オプション）

すぐに視覚的に確認したい場合は、取得した警告を小さな HTML レポートに出力できます。以下はメッセージを `warnings.html` に書き込む小さなスニペットです。

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

ドキュメントを読み込んだ後、`handler.WriteReport(@"C:\Docs\warnings.html");` を呼び出し、ブラウザーで開きます。下の画像はレポートのイメージ例です。

![警告取得方法のスクリーンショット](/images/capture-warnings.png)

*Alt text:* **警告取得方法** – コンソール出力と HTML レポートのスクリーンショット。

---

## 結論  

本稿では Aspose.Words における **警告の取得方法** を取り上げ、**欠落フォントの処理** の信頼できる手法と、決定的なレンダリングのための **カスタムフォント設定の設定** 方法を示しました。完全なサンプルは任意の .NET ソリューションにすぐに組み込め、モジュラーな `FontWarningHandler` はロギングやテレメトリ戦略に合わせて拡張可能です。

次のステップは？`Console.WriteLine` 呼び出しを Serilog のような構造化ロガーに置き換えるか、警告を Application Insights に送ってリアルタイムで監視してみてください。また、ロード後にドキュメントの内容を検査する必要がある場合は `DocumentVisitor` パターンの活用も検討できます。

他の警告タイプやフォント埋め込み戦略について質問がありますか？以下にコメントを残してください—ハッピーコーディング！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}