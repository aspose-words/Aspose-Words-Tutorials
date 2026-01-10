---
category: general
date: 2026-01-10
description: Aspose.Wordsで欠落フォントを処理するためのLoadOptionsの使い方を学びましょう。ステップバイステップのコード、ヒント、そして堅牢なドキュメント読み込みのベストプラクティスをご紹介します。
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: ja
og_description: Aspose.Words で欠落フォントを処理するための LoadOptions の使用方法。説明と実践的なヒントが付いた、完全な実行可能サンプルを入手できます。
og_title: Aspose.WordsでLoadOptionsを使用する方法 – 完全ガイド
tags:
- Aspose.Words
- C#
- .NET
title: Aspose.Words の LoadOptions の使い方 – 完全ガイド
url: /ja/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で LoadOptions の使用方法 – 完全ガイド

Word 文書を読み込む際にフォントが不足している可能性がある場合、**how to use LoadOptions** が気になったことはありませんか？ 同じ悩みを抱えている人は他にもいます。実際のプロジェクトでは、文書が別のマシン間を行き来し、対象システムに作者が使用した正確なフォントがインストールされていないことがよくあります。その結果、レイアウトが崩れたり、重要な文字が表示されなかったり、ブランドイメージと合わないフォント置換が発生したりします。  

幸い、Aspose.Words は *handle missing fonts* 用のクリーンな方法を提供してくれます。`LoadOptions` オブジェクトに警告コールバックを設定するだけです。このチュートリアルでは、フォント置換の警告を取得し、ログに記録し、処理パイプラインを堅牢に保つための **how to use LoadOptions** の具体的な手順を学びます。

以下をカバーします：

* 警告コールバッククラスの作成  
* そのコールバックを使用した `LoadOptions` の設定  
* フォントが不足している状態で文書を読み込む方法  
* トラブルシューティングのヒントと拡張方法  

外部ドキュメントは不要です—必要な情報はすべてここにあります。

---

## 必要なもの

作業を始める前に、以下を用意してください：

* **Aspose.Words for .NET**（2026 年時点の最新バージョン）を NuGet でインストール  
* .NET 開発環境（Visual Studio、Rider、または VS Code）  
* インストールされていないフォントを参照しているサンプル DOCX（ここでは `input.docx` と呼びます）  

以上です—追加のライブラリは不要です。

---

## Step 1 – Define a Warning Callback to Capture Font Substitution

パズルの最初のピースは、`IWarningCallback` を実装したクラスです。Aspose.Words は、何か注目すべきこと（例：フォントが見つからない）に遭遇すると `Warning` メソッドを呼び出します。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**この重要性:**  
`WarningType.FontSubstitution` でフィルタリングすることで、不要な警告（例：非推奨機能）で雑音が増えるのを防げます。コールバックは完全に制御可能です—ファイルにログを書き込んだり、例外を投げたり、プログラムで代替フォントを埋め込んだりできます。

---

## Step 2 – Configure LoadOptions with the Callback

ハンドラができたので、Aspose.Words にそれを使用させる必要があります。ここで **how to use LoadOptions** の実践例を示します。

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Tip:** `LoadOptions` には他にも多数のスイッチ（例：`Password`、`LoadFormat`、`Encoding`）があります。必要に応じてチェーンできますが、フォント不足を扱う場合は `WarningCallback` が主役です。

---

## Step 3 – Load the Document Using the Configured Options

`LoadOptions` が準備できたら、文書の読み込みはシンプルです。Aspose.Words は見つからないフォントがあるたびに自動的にコールバックを呼び出します。

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**期待される出力:**  

`input.docx` がインストールされていないフォント *“GothicBold”* を使用している場合、次のような出力が得られます：

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

警告行は **フォントが見つからない瞬間に正確に表示** され、即座にフィードバックが得られます。

---

## Step 4 – (Optional) Continue Processing the Document

通常、ファイルを読み込むだけでなく、さらに処理を行いたいものです。以下は、警告設定とシームレスに連携できる一般的なロード後アクションです。

### 4.1 Save the Document as PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Replace Missing Fonts with a Known Fallback

特定の代替フォント（例：*“Calibri”*）を使用したい場合は、保存前に `FontSettings` を調整します：

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Log All Warnings to a File

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

これらのスニペットは **how to use LoadOptions** を基本ケース以外でも活用できることを示しており、プロダクション向けの柔軟性を提供します。

---

## 一般的な落とし穴と **Handle Missing Fonts** の対処法

| Pitfall | Why it Happens | How to Fix / Mitigate |
|---------|----------------|-----------------------|
| **No callback attached** | `WarningCallback` を設定し忘れたため。 | `LoadOptions` インスタンスを必ず作成し、ロード前にハンドラを割り当ててください。 |
| **Callback only prints, never stores** | Web サービスではコンソール出力が消えてしまうため。 | `Console.WriteLine` をロガー（Serilog、NLog など）に置き換えるか、永続ストアに書き込んでください。 |
| **Multiple missing fonts, only first reported** | コールバックが最初の警告で例外を投げてしまうため。 | コールバックは軽量に保ち、終了させたいとき以外は例外を投げないようにしてください。 |
| **Substituted font looks wrong** | デフォルトの置換が視覚的に異なるフォントを選んでしまうため。 | `FontSettings.SubstitutionSettings.FontSubstitutionRules` を使用して、好みの代替フォントを優先させてください。 |
| **Performance hit on huge documents** | 警告コールバックが何千回も呼び出されるため。 | 警告をバッチ化してリストに蓄積し、ロード後にまとめて処理するか、ユニークなフォント名だけをフィルタしてください。 |

---

## Full Working Example – All Pieces Together

以下は、全体の流れを示す完全な実行可能プログラムです。コンソールプロジェクトに貼り付け、Aspose.Words NuGet パッケージを追加すればすぐに動作します。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**このプログラムを実行すると**:

1. フォント置換の警告がコンソールに出力されます。  
2. 元のレイアウトを `output.pdf` として保存します。  
3. 代替フォント（*Calibri* または *Arial*）を強制した `output-with-fallback.pdf` を保存します。

---

## Frequently Asked Questions (FAQs)

**Q: Does this work for DOC, RTF, or HTML files?**  
A: はい。`LoadOptions` はフォーマットに依存せず、正しいファイルパスを渡すだけで、すべてのサポート対象フォーマットでフォント不足の警告コールバックが発火します。

**Q: Can I suppress the warnings entirely?**  
A: `new IWarningCallback { Warning = _ => {} }` のように何もしないコールバックを割り当てるか、`LoadOptions.WarningCallback = null` に設定すれば警告を抑制できます。ただし、可視性が失われると重要なフォント問題を見逃す可能性があります。

**Q: What if I need to replace missing fonts with embedded ones?**  
A: `FontSettings` に代替フォントファイルを追加する（`AddFontSource`）ことで埋め込みフォントに置き換えることができます。置換ルールと組み合わせればシームレスに実現できます。

**Q: Is the callback thread‑safe?**  
A: 大規模文書を並列でロードする場合、コールバックは複数スレッドから呼び出される可能性があります。共有リソース（例：ログファイル）は適切に同期してください。

---

## Conclusion

本稿では **how to use LoadOptions** を活用して **Handle Missing Fonts** をエレガントに処理する方法を解説しました。`IWarningCallback` を実装し、`LoadOptions` に紐付けて文書を読み込むだけで、フォント置換イベントをリアルタイムに取得できます。その後、ログに記録したり、代替フォントを埋め込んだりして、期待通りの出力を実現できます。

重要なステップは次の通りです：

1. `WarningType.FontSubstitution` に焦点を当てた警告コールバックを実装する。  
2. そのコールバックを `LoadOptions` オブジェクトに設定する。  
3. そのオプションで文書を読み込む。  
4. （任意）さらにフォント置換ルールやロギングを追加する。

ぜひ試してみてください—コンソールロガーを構造化ロガーに置き換えたり、重要なフォント欠如時にメール通知を送ったり、ドキュメント処理パイプライン全体に組み込んだりすると、単一ファイルから数千ファイルのバッチ処理までスムーズに拡張できます。

Happy coding, and may your documents always render with the right typefaces!  

---

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}