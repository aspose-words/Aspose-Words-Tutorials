---
category: general
date: 2026-05-04
description: Aspose のフォント置換機能を使用して、Word 文書を読み込む際に欠落フォントを検出し、欠落フォントの詳細を取得する方法をステップバイステップで学びましょう。
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: ja
og_description: Aspose のフォント置換をマスターし、Word 文書の読み込み時に欠落フォントを検出し、完全な C# コードで欠落フォント情報を取得する。
og_title: Aspose フォント置換 – Word 文書の欠損フォントを検出
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose フォント置換: Word 文書の欠損フォントを検出'
url: /ja/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Word 文書で欠落フォントを検出する

別のマシンで Word 文書の表示が崩れる理由を考えたことはありませんか？多くの場合、その原因は欠落フォントです。**Aspose font substitution** は、視覚的な災害になる前にそのギャップを見つけることができるツールです。このチュートリアルでは、**Word 文書をロードした瞬間に欠落フォントを検出**し、**欠落フォントの詳細を取得**して修正または置き換える方法を順を追って説明します。

警告コールバックの設定から欠落フォントのクリーンなリスト取得まで、すべてカバーします。最後までに、どのフォントが見つからなかったか正確に教えてくれる実行可能な C# スニペットが手に入り、なぜこれが文書の忠実性に重要なのかが理解できるようになります。

---

## 前提条件 – 開始前に必要なもの

- **Aspose.Words for .NET** (v23.12 以降推奨)。  
- .NET 開発環境 (Visual Studio、Rider、または `dotnet` CLI)。  
- 意図的にインストールされていないフォントを使用したサンプル DOCX（例: `DocumentWithMissingFont.docx`）。  
- 基本的な C# の知識 – 特別なことは不要で、コンソール アプリを実行できれば OK。

これらのいずれかに心当たりがなければ、まず NuGet パッケージをインストールしてください：

```bash
dotnet add package Aspose.Words
```

以上です。追加のフォントや外部サービスは不要です。

---

## ステップ 1: Word 文書をロードする（フォントチェックをトリガー）

最初に行うことは **Word 文書をロード** することです。Aspose.Words はファイルを解析し、参照されたフォントが見つからない場合は *FontSubstitution* 警告をキューに入れます。以下がロード処理のコードです：

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **なぜ重要か:** 文書を早期にロードすることで、Aspose はテキスト、スタイル、埋め込みオブジェクトのすべてのランをスキャンする機会が得られます。システムやカスタムフォントフォルダーにフォントが見つからない場合、後で警告が出ます。

---

## ステップ 2: 警告コールバックを添付して置換イベントを取得する

Aspose.Words は、欠落フォントなどの問題を通知するためにコールバック機構を使用します。`IWarningCallback` の実装を `doc.WarningCallback` に割り当てることで、発生する各警告をインターセプトできます。

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **プロのコツ:** 複合パターンでラップすれば複数のコールバック（例: ロギング、UI 更新）を添付できますが、このチュートリアルでは単一のコールバックでシンプルに保ちます。

---

## ステップ 3: フォント置換警告コールバックを実装する

ここで実際に処理を行うクラスを定義します。コールバックは `WarningInfo` オブジェクトを受け取り、`WarningType.FontSubstitution` をフィルタリングして、後で使用するために説明を保存します。

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **何が起きているか:** Aspose が欠落フォントに遭遇すると、たとえば “Font substitution: 'Comic Sans MS' が見つからなかったため、代わりに 'Arial' を使用しました。” のような警告を作成します。コールバックはその行を出力し、保存します。

---

## ステップ 4: 文書を処理（オプション）し、欠落フォントを収集する

**欠落フォントを検出**するだけであれば、ロード段階だけで十分です—警告は自動的に発生します。ただし、多くの開発者は何らかの操作（例: 保存、変換）を行った後に **欠落フォント情報を取得**する必要があります。以下では、すべての警告が出力されるように PDF への保存という小さな操作を強制し、収集したメッセージを取得します。

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **期待されるコンソール出力**（例）:
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

各行が元のフォントと Aspose が選択した代替フォントを明確に示していることに注目してください。これが **aspose font substitution** レポートの核心です。

---

## ステップ 5: 上級編 – カスタムフォントソースを使用して置換を減らす

時には欠落フォントが実際に存在するが、デフォルトのシステムフォルダーにないことがあります。Aspose.Words は `FontSettings` を介してカスタムディレクトリを指定できます。この手順を追加すると、置換警告の数を大幅に減らすことができます。

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **なぜ追加するか:** 複数のマシンに文書を配布する場合、必要なフォントを既知のフォルダーにバンドルすれば、どこでも同じ視覚的外観が保証されます。また、Aspose がフォールバックする前にそのフォルダーをチェックするため、**欠落フォント検出**の手順がより正確になります。

---

## 完全な動作例

すべてをまとめると、以下はコピー＆ペーストで実行できるコンソール プログラムです。`Program.cs` として保存し、`dotnet run` で実行してください。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**期待される出力:** ソース DOCX が存在しないフォントを参照している場合、コンソールに各置換行と簡潔なサマリーが表示されます。すべてのフォントが揃っていれば “No missing fonts were detected.” というメッセージが表示されます。

---

## よくある落とし穴と回避策

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **警告が表示されない** | 文書がシステムフォントのみを使用しているか、欠落フォントを含むカスタムフォルダーをすでに追加しているためです。 | DOCX が本当に利用できないフォントを参照しているか確認してください。Word で段落を稀なフォント（例: “Papyrus”）に変更すると確認できます。 |
| **重複メッセージ** | 同じフォントが複数のランで使用されているため、警告が複数回出ます。 | ユニークなセットだけが必要な場合は、`Distinct()` でリストの重複を除去してください。 |
| **大規模文書でのパフォーマンス低下** | 各警告が UI スレッドで処理されるためです。 | ロードをバックグラウンドタスクで実行するか、ポストプロセスに `Parallel.ForEach` を使用してください。 |
| **誤ったフォールバックフォント** | Aspose のデフォルトフォールバックがブランドに合わない可能性があります。 | `FontSettings.SubstitutionSettings.DefaultFontName` を好みのフォールバックフォント（例: “Calibri”）に設定してください。 |

---

## 拡張編 – 欠落フォントを JSON にエクスポートする

クライアントに欠落フォントを報告する必要がある Web サービスを構築する場合、リストのシリアライズは簡単です：

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

これで API は、他システムが利用できるクリーンな JSON ペイロードを返すことができます。

---

## 結論

本ガイドでは、**Aspose font substitution** を最初から最後まで実演しました。Word 文書のロード、警告コールバックの添付、各 *欠落フォント検出* イベントの取得、そして最終的に **欠落フォント情報の取得** を行い、レポートや修正に活用します。オプションのカスタムフォントフォルダーを追加すれば置換リストを縮小でき、数行追加するだけで結果を JSON にエクスポートすることも可能です。

文書の視覚的完全性は使用するフォントに依存します。この手法を使えば、予期しないフォールバックに驚くことはなくなります。  

次のステップへ進む準備はできましたか？このロジックをより大規模な文書処理パイプラインに統合したり、フォント埋め込み（`doc.FontSettings.EmbeddedFonts`）など Aspose.Words の他の機能を探求してみてください。可能性は無限大で、ユーザーは洗練された出力に感謝するでしょう。

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}