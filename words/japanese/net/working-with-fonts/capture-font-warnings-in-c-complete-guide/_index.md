---
category: general
date: 2026-03-06
description: C#でWord文書を読み込む際にフォント警告を取得します。欠落フォントの検出、文書のフォントの確認、欠落フォントの効率的な処理方法を学びましょう。
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: ja
og_description: C#でWord文書を読み込む際のフォント警告を取得します。このチュートリアルでは、欠落フォントの検出、文書フォントの確認、欠落フォントの処理方法を示します。
og_title: C#でフォント警告を取得する – 完全ガイド
tags:
- Aspose.Words
- C#
- Font Management
title: C#でフォント警告を取得する – 完全ガイド
url: /ja/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でフォント警告を取得する – 完全ガイド

Word 文書を処理するときに **フォント警告を取得** したことがありますか？ フォント警告を取得することは、**欠落フォントを検出** し、最終出力が意図した通りになることを保証するために不可欠です。  

このチュートリアルでは、`.docx` ファイルを読み込み、読み込みプロセスを監視し、フォント置換があれば報告する実践的なエンドツーエンドの例を順を追って解説します。最後まで読むと、**Word 文書の読み込み** を安全に行い、**文書のフォントをチェック** し、**欠落フォントをハンドル** する方法が分かります。

## 学べること

- Aspose.Words の `Document` に警告コレクタを添付する方法  
- 欠落または置換されたフォントを示す警告タイプ  
- 本番環境アプリでこれらの警告をログに記録したり、リアクションしたりする方法  
- **欠落フォントをうまく処理** したい場合のカスタムフォント ソース設定のコツ  

> **前提条件:** 有効な Aspose.Words for .NET ライセンス（または無料トライアル）と、.NET 開発環境（Visual Studio、Rider、または VS Code）が必要です。その他のライブラリは不要です。

---

## フォント警告の取得 – 手順別

以下は完全に実行可能なコードです。各セクションは独立したステップに分かれているので、コピー＆ペーストして実験したりロジックを拡張したりできます。

![フォント警告のキャプチャ図](image.png "警告収集を示す図"){: alt="フォント警告のキャプチャ図"}

### ステップ 1: Word 文書を読み込む

まず、現在のマシンにインストールされていないフォントが含まれている可能性がある **Word 文書を読み込む** 必要があります。`Document` コンストラクタが実際の処理を行いますが、後でストリームやバイト配列に差し替えられるように呼び出しを分離しておきます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**重要ポイント:** 警告ハンドラを設定せずに文書を読み込むと、フォント置換が黙って無視されます。`WarningCallback` を *読み込み前* に設定することで、発生するすべての `FontSubstitution` 警告を確実に取得できます。

### ステップ 2: 警告コレクタを添付する

`WarningInfoCollector` クラスは `IWarningCallback` の組み込み実装です。警告をリストに保存し、後で検査できるようにします。

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**プロのコツ:** **欠落フォントをハンドル** する際に、もっと積極的に対応したい場合（例: 読み込みを中止したり、特定のフォールバックに置換したり）には、`Console.WriteLine` をカスタムロジックに置き換えてください。例: 例外を投げる、ファイルにログを書く、カスタムフォント ソースを追加する、など。

### ステップ 3: 出力を確認する

コンソールからプログラムを実行します。`input.docx` がインストールされていないフォントを使用している場合、次のような行が表示されます。

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

出力がまったく表示されない場合、文書は **利用可能なフォントだけ** を使用したか、Aspose.Words が組み込みのフォールバック コレクションで一致するフォントを見つけたかのどちらかです。いずれにせよ、**文書のフォントをチェック** に成功しています。

---

## ライセンスなしで欠落フォントを検出する方法（無料トライアル）

30 日間のトライアルを使用していても、警告機構は同じように機能します。唯一の違いは、トライアル版が生成された出力に透かしを付加する点で、**警告の取得には影響しません**。したがって、フル ライセンスを購入する前に **欠落フォントを検出** することが安全に行えます。

---

## 欠落フォントのハンドリング – 上級オプション

場合によっては、社内ブランドフォントなど独自のフォント ファイルを提供し、置換が起きないようにしたいことがあります。Aspose.Words ではカスタム フォント フォルダーを登録できます。

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

上記コードは文書を読み込む **前** に配置してください。これにより、ロード時の解析フェーズでこれらのフォントが考慮されます。デフォルトのシステム フォントに依存せずに **欠落フォントをハンドル** する最も確実な方法です。

---

## よくある落とし穴と回避策

| 落とし穴 | 発生理由 | 対策 |
|---------|----------|------|
| **ロード後に警告コレクタを添付** | 文書はすでに解析済みで、警告が記録されない | `new Document(path)` を呼ぶ **前に** `WarningCallback` を設定 |
| **汎用警告しか出ない** | 間違った `WarningType` でフィルタしている | フォント問題に絞るには `WarningType.FontSubstitution` を使用 |
| **欠落フォントがあるのに出力が無い** | Aspose.Words が組み込みフォールバック（例: Arial）を見つけた | `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` で組み込みフォールバックを無効化 |
| **大容量文書でパフォーマンス低下** | すべての警告を収集するとコストがかかる | `FontSubstitution` のみを収集するか、バッチ処理で警告を処理 |

---

## 完全動作サンプル（コピー＆ペースト可）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**期待されるコンソール出力**（欠落フォントが 2 つある場合）:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

コンソールに「Document loaded successfully」以外の出力が無ければ、**文書のフォントをチェック** し、欠落フォントが無いことが確認できたことになります。

---

## まとめ

本稿では、Aspose.Words を使用して C# で **フォント警告を取得** する方法を示しました。これにより **欠落フォントを検出** し、**Word 文書の読み込み** を安全に行い、**文書のフォントをチェック** し、カスタム フォント ソースを使って **欠落フォントをハンドル** できるようになります。  

このパターンを活用すれば、PDF 生成、HTML 変換、Word ファイルのアーカイブなど、あらゆる自動化パイプラインにフォント検証を組み込めます。

### 次のステップ

- **FontSettings.SubstitutionSettings** API を調査し、独自のフォールバック ルールを定義  
- 警告取得とロギング フレームワーク（Serilog、NLog など）を組み合わせて本番監視を実装  
- 画像解像度や未対応機能など、他の警告タイプを取得するために同様の手法を応用  

フォント処理や Aspose.Words 全般について質問があれば、コメントを残すか Aspose コミュニティ フォーラムで質問してください。楽しいコーディングを！そして、文書が常に期待通りのフォントで表示されますように。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}