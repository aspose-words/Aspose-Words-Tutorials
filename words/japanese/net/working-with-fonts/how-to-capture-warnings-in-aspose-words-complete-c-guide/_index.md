---
category: general
date: 2026-03-28
description: Aspose.WordsでDOCXを読み込む際に警告を取得し、欠落フォントに関する警告メッセージを取得する方法。欠落フォントを効率的に処理する方法を学びましょう。
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: ja
og_description: Aspose.WordsでDOCXを読み込む際の警告を取得し、警告メッセージを取得、欠落フォントを実用的なコード例で処理する方法。
og_title: Aspose.Wordsで警告を取得する方法 – 完全なC#ガイド
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Wordsで警告を取得する方法 – 完全なC#ガイド
url: /ja/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で警告を取得する方法 – 完全 C# ガイド

Word 文書を Aspose.Words で読み込むときに **警告を取得する方法** が気になったことはありませんか？ フォントが奇妙に変わってしまい、正確な原因を知りたいときに役立ちます。簡単に言えば、ライブラリの警告システムにフックし、**警告メッセージを取得** し、レイアウトを壊す前に **欠落フォントを処理** できます。  

このチュートリアルでは、実際のシナリオとして DOCX を読み込み、エンジンが出すすべての警告を収集し、フォント置換が発生した場合の詳細を出力する手順を解説します。最後まで読めば、すぐに実行可能なコードサンプルが手に入り、各ステップの「なぜ」も理解でき、独自プロジェクトへの拡張方法も把握できます。

## 学べること

- 警告を自動的に取得できるよう `LoadOptions` を設定する方法。  
- `WarningInfoCollection` から **警告メッセージを取得** する正確な手順。  
- `WarningType.FontSubstitution` フラグを使って **欠落フォントを特定・対応** する方法。  
- 埋め込みフォントやカスタムフォントフォルダーを使用したドキュメントのトラブルシューティングのコツ。  

外部参照は不要です – 必要な情報はすべてここにあります。

---

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）。  
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）。  
- フォントが不足しているか、マシンにインストールされていないフォントを使用しているサンプル DOCX（`input.docx`）。  

以上です。C# と Visual Studio に慣れていれば、コードをコピー＆ペーストしてすぐに実行できます。

---

## 手順 1: Load Options と警告コールバックの準備

`new Document(path, loadOptions)` を呼び出すと、Aspose.Words は最初にファイルを解析します。解析中に欠落フォントや未対応機能、非推奨マークアップに遭遇することがあります。これらのイベントを捕捉するには **警告コールバック** オブジェクトが必要です。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**重要ポイント:** コールバックが無いと、Aspose.Words は警告をコンソールに静かに出力（または破棄）するだけで、レイアウトに影響を与えるフォント置換に気付くことができません。`WarningInfoCollection` を提供することで、完全な可視性が得られます。

> **プロのコツ:** フォント関連の警告だけが必要な場合は後でフィルタリングすれば OK ですが、*すべて* の警告を収集しておくと将来的な問題に対する安全網になります。

---

## 手順 2: 設定したオプションでドキュメントを読み込む

コールバックの準備ができたら、ファイルをロードします。`Document` コンストラクタは問題が見つかるたびに自動的にコールバックを呼び出します。

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**内部で何が起きているか?** Aspose.Words は Open XML を解析し、スタイルを解決し、各フォント参照をシステムにインストールされているフォントにマッピングしようとします。マッチが見つからない場合、`FontSubstitution` タイプの `WarningInfo` が作成されます。

---

## 手順 3: 収集した警告を取得・検査する

ロードが完了すると、`warningCollector` には発生したすべての警告が格納されています。ここから取り出し、フォント置換メッセージに注目しましょう。

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**サンプル出力**（コンソールは次のようになる場合があります）:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

すべての警告が欲しい場合は `if` 条件を削除するか、各エントリの `warning.Type` をログに出力してください。

---

## 手順 4: 欠落フォントの処理 – ログだけでなく

警告を取得するだけでも有用ですが、実務では **欠落フォントをプログラム上で処理** したいことが多いです。代表的な 2 つの戦略を紹介します。

### 4.1 欠落フォントを特定のフォールバックに置き換える

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

これで、欠落フォントはライブラリ既定のフォールバックではなく *Calibri* に置き換えられます。

### 4.2 置換フォントを動的に埋め込む

カスタムフォントファイル（例: `MyFallback.ttf`）がある場合、実行時に登録できます:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

この方法は、アプリケーションと一緒に特定の社内フォントを配布したいときに便利です。

> **エッジケース:** 必要なフォントがすでに DOCX に埋め込まれている場合、システムの置換ルールは無視されます。その場合、該当フォントに対する警告は空になるので、期待通りの動作です。

---

## 手順 5: 完全動作サンプル（コピー＆ペースト可能）

以下は、最初から最後までを網羅した自己完結型プログラムです。`YOUR_DIRECTORY/input.docx` をテストファイルのパスに置き換えるだけで動作します。

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**期待される結果**

- コンソールにフォント置換警告がすべて表示され、視認性向上のために警告絵文字が付与されます。  
- 出力 DOCX（`output.docx`）は、欠落フォントが検出された箇所すべてで *Calibri* が使用されます。  
- 例外は発生せず、警告システムが未知のフォントも優雅に処理します。

---

## よくある質問 & 回答

**Q: Word から生成した PDF でも動作しますか？**  
A: はい。Aspose.Words は PDF を別の出力形式として扱います。警告取得は *ロード* フェーズで行われるため、最終エクスポートとは独立しています。

**Q: すべてのドキュメント操作（保存、変換など）で警告を取得したい場合は？**  
A: `Document` インスタンス化後に `Document.WarningCallback` に同じ `WarningInfoCollection` を再設定すれば、以降のすべての操作で新しいエントリが同じコレクションに追加されます。

**Q: 警告コールバックはパフォーマンスに影響しますか？**  
A: 影響はごくわずかです。コレクションは単にオブジェクトを保持するだけなので、数千件規模の警告を高速ループで処理しない限り、遅延はほとんど感じません。

**Q: 不要な警告は抑制したいです。**  
A: `IWarningCallback` を継承したカスタムクラスを実装し、`Warning` メソッド内でフィルタリングすれば可能です。組み込みの `WarningInfoCollection` は保存のみを行い、フィルタは行いません。

---

## プロのコツ & 落とし穴

- **プロのコツ:** `Warning.Description` を必ず確認してください。欠落したフォント名が正確に記載されているので、フォントをアプリに同梱すべきか判断できます。  
- **埋め込みフォントに注意:** ソース DOCX に必要なフォントが埋め込まれている場合、ローカルにインストールされていなくても置換警告は出ません。  
- **スレッド安全性:** `WarningInfoCollection` はスレッドセーフではありません。複数ドキュメントを同時にロードする場合は、各スレッドに個別のコレクションを割り当ててください。  
- **バージョン確認:** 警告 API は Aspose.Words 20.8 以降で安定しています。最新バージョンを使用すれば、新しい警告タイプが欠落する心配はありません。

---

## 結論

Aspose.Words から **警告を取得** する方法を学び、**警告メッセージの取得** と **欠落フォントの実践的な処理**（フォールバックフォントやカスタムフォントフォルダー）を実演しました。完全なサンプルは任意の .NET プロジェクトにすぐに組み込め、概念は大規模な自動化パイプラインにも拡張可能です。

次に試すべきこと:

- `Document.WarningCallback` を利用して **保存** 時の警告も取得する。  
- 警告をファイルやテレメトリシステムに記録し、プロダクションでの監視に活用する。  
- コールバックを拡張し、ブランド固有の書体で欠落フォントを自動置換する。

ぜひ実験してみてください – フォールバックフォントを変えてみたり、バッチ処理に複数文書を追加したり、CI パイプラインに警告コレクターを組み込んでフォント関連のリグレッションを検出したり。楽しいコーディングを！ ドキュメントが常に期待通りにレンダリングされますように。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}