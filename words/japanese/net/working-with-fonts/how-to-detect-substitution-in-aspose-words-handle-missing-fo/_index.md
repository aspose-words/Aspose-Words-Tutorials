---
category: general
date: 2026-04-24
description: C# を使用して Aspose.Words で欠落フォントの置換を検出する方法。このガイドでは、FontSettings の警告を利用して欠落フォントを確実に処理する方法を示します。
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: ja
og_description: C# で Aspose.Words の欠落フォントの置換を検出する方法。FontSettings の警告を使用して欠落フォントを処理する方法を学びましょう。
og_title: Aspose.Wordsで置換を検出する方法 – 完全ガイド
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Aspose.Wordsで置換を検出する方法 – 欠落フォントへの対処
url: /ja/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words での置換検出方法 – 欠落フォントの処理

サーバーにインストールされていないフォントを文書が使用しようとしたとき、**置換検出方法**を知りたくありませんか？ 特に自動化パイプラインで PDF や Word ファイルを生成する場合、よくある悩みです。 良いニュースは、Aspose.Words がその状況を検出する組み込みフックを提供しており、**欠落フォントの処理**も優雅に行えることです。

このチュートリアルでは、`FontSettings.Warning` イベントを使って **置換検出方法** を実演し、**欠落フォントの処理** 方法を解説します。 最後まで読むと、すぐに実行できるコードスニペットと、各行が何を意味するかの明確な理解、そして典型的な落とし穴を回避するコツが得られます。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework でも動作します）
- Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`） – バージョン 23.11 以上
- インストールされていないフォントを参照しているサンプル文書（例：`MissingFont.docx`）
- Visual Studio、VS Code、またはお好みの C# IDE  

NuGet パッケージを追加する以外に特別な設定は必要ありません。

---

## FontSettings を使用した置換検出方法

**置換検出方法** の核心は `FontSettings.Warning` イベントです。Aspose.Words が要求されたフォントを見つけられないと、`WarningType.FontSubstitution` 警告が発生します。このイベントに登録すると、元のフォント名と代替として使用されたフォント名がリアルタイムで通知されます。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**この仕組みが機能する理由:**  
- `LoadOptions.FontSettings` により、作成した `FontSettings` オブジェクトを Aspose.Words に使用させます。  
- `Warning` に登録することで、欠落フォントだけでなく *すべて* のフォント関連問題を一元的に監視できます。  
- `WarningType.FontSubstitution` フィルタにより、関心のあるシナリオ（置換）だけに反応でき、**置換検出方法** の本質を捉えます。

### 期待される出力

存在しないフォントを参照している文書で上記コードを実行すると、次のような出力が得られます:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

文書がインストール済みフォントのみを使用している場合、コンソールは何も出力せず、**置換検出方法** が誤検知なしに成功したことを示します。

---

## 欠落フォントを優雅に処理する

置換を検出するだけでは不十分です。最終的な出力が期待通りになるよう、**欠落フォントの処理** 戦略も必要です。以下に、組み合わせて使える実用的な 3 つのアプローチを示します。

### 1. フォールバックフォントフォルダーを提供する

Aspose.Words は追加のフォントディレクトリを検索できます。最も一般的に使用するフォントを格納したフォルダーを指定すれば、置換の可能性を大幅に減らせます。

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**理由:** 元のフォントが見つからないとき、Aspose.Words は既知の代替フォントセットを参照できるため、視覚的に予測しやすい結果が得られます。

### 2. プログラムで欠落フォントを置換する

完全にコントロールしたい場合は、検出後に欠落フォントを特定のフォントに置き換えることができます。

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**理由:** エンジンに使用すべきフォントを明示できるため、企業のブランディングやアクセシビリティ基準を強制できます。

### 3. ログ記録と中止（置換が許容できない場合）

場合によっては、欠落フォントが文書の有効性を損なうことがあります（例：法的文書）。そのようなシナリオでは、置換が発生した瞬間に例外をスローして処理を中止します。

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**理由:** 直ちに失敗させることで、テーブルのずれや署名の破損といった下流エラーを防げます。

---

## 完全動作例 – すべての手順を統合

以下は、**置換検出方法** と **欠落フォントの処理** を同時に示す、コピー＆ペーストだけで動作する単一プログラムです。不要なセクションはコメントアウトして構いません。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**期待される結果:**  
- `MissingFont.docx` がマシンに存在しないフォントを参照している場合、コンソールに置換警告が表示されます。  
- 保存された `Processed.docx` は設定したフォールバックフォント（またはライブラリのデフォルト）を使用します。  
- 明示的に中止を指示しない限り、未処理の例外は発生しません。

---

## よくある質問とエッジケース

| 質問 | 回答 |
|----------|--------|
| *文書に多数の欠落フォントが含まれている場合は？* | 警告イベントは **各** 置換ごとに発生するため、複数行が出力されます。リストに集約してサマリーレポートを作成できます。 |
| *PDF 変換でも同様に機能しますか？* | はい。`doc.Save("out.pdf")` を呼び出す際も同じ `FontSettings` が適用され、置換警告は引き続き発生します。 |
| *文書読み込み後に置換を検出できますか？* | 直接はできません。警告は **読み込みまたは保存中** に発生します。ロードフェーズで警告をコレクションに保存すれば、後から分析可能です。 |
| *DOCX に埋め込まれたカスタムフォントは？* | 埋め込みフォントは「存在する」とみなされ、置換は起きません。埋め込みフォントが破損している場合も、同様に警告が発生し捕捉できます。 |
| *パフォーマンスへの影響は？* | 最小です。警告チェック自体は軽量で、実際のコストは文書のロードにあります。フォントフォルダーを追加すると、最初のロード時に検索時間が若干増える程度です。 |

---

## プロのコツと回避すべき落とし穴

- **コツ:** フォントが多数あるフォルダーを指定する場合は `recursive: true` を必ず設定してください。サブフォルダーが無視されます。  
- **注意点:** Linux では大文字小文字が区別されます。Windows はケースインセンシティブですが、Linux では正確な名前、または両方のバリエーションを用意してください。  
- **覚えておくべきこと:** コンテナ環境で実行する場合、フォントフォルダーをイメージに含めるか、実行時にマウントしてください。  
- **ヒント:** 警告を `List<string>` に格納すれば、エンドユーザー向けのサマリーレポートや監視システムへのログ出力が容易になります。  

---

## 結論

Aspose.Words における欠落フォントの **置換検出方法** を解説し、**欠落フォントの処理** 方法をいくつか提示しました。`FontSettings.Warning` イベントを活用すればフォント問題をリアルタイムで把握でき、フォールバックフォルダーや明示的な置換ルールを組み合わせることで、期待通りの出力を維持できます。

次のステップに進みませんか？ フォールバックフォントを自動的に PDF に埋め込む処理を追加したり、警告ハンドラを集中ロギングサービスに接続して大規模文書パイプラインで活用したりしてみてください。今回紹介した「イベント駆動の検出」「優雅なフォールバック」「明示的なエラーハンドリング」のパターンは、他の Aspose API にも応用できるので、フォント関連の課題全般に自信を持って取り組めるようになります。

フォント処理、PDF 変換、または Aspose.Words のテクニックについてさらに質問があれば、下のコメント欄に書き込んでください。 happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}