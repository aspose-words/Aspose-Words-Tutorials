---
category: general
date: 2026-04-10
description: Aspose.Words の LoadOptions を使用して、ドキュメントの読み込み時にフォント置換警告を取得する方法。ステップバイステップの
  C# ソリューションと完全なコード例を学びましょう。
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: ja
og_description: Aspose.Words の LoadOptions を使用して、ドキュメントの読み込み時にフォント置換警告を取得する方法。このガイドでは、完全な
  C# 実装を順を追って説明します。
og_title: Aspose.WordsでLoadOptionsを使用する方法 – 完全なC#ガイド
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Aspose.Words の LoadOptions の使い方 – 完全 C# ガイド
url: /ja/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で LoadOptions を使用する方法 – 完全な C# ガイド

Aspose.Words で LoadOptions を使用することは、ドキュメントの読み込みを細かく制御する必要があるときによくあるハードルです。このチュートリアルでは、**LoadOptions の使用方法**を正確に示し、フォント置換の警告を捕捉して C# で対処する方法を紹介します。  

もし、欠落したフォントを参照している DOCX を開いたときに、出力が変に見える理由がわからなかったことがあるなら、ここが適切な場所です。  
作成した `LoadOptions` インスタンスからコンソールへの警告詳細の出力まで、全工程を順に解説します。最後まで読むと、任意の .NET プロジェクトにすぐ組み込める実行可能なコードスニペットが手に入ります。

## 学べること

- `LoadOptions` が信頼性の高いドキュメントインポートに重要な理由。  
- **WarningCallback** を組み込み、特に **フォント置換警告** を監視する方法。  
- これらのオプションを有効にして Word ファイルを読み込むために必要な正確なコード。  
- 複数の欠落フォントを含むドキュメントなど、エッジケースを処理するためのヒント。  

外部ドキュメントは不要です—必要な情報はすべてここにあります。

## 前提条件

| 要件 | 理由 |
|------|------|
| .NET 6.0 以降 | 例で使用されている C# 10 構文の実行環境を提供します。 |
| Aspose.Words for .NET（最新バージョン） | `LoadOptions` と警告インフラストラクチャを提供するライブラリです。 |
| インストールされていないフォントを参照している可能性のある DOCX ファイル | 警告コールバックの動作を確認するために使用します。 |
| Visual Studio 2022（またはお好みの IDE） | デバッグやテストを簡単に行える環境です。 |

これらがすでに揃っているなら、さっそく始めましょう。

## ステップ 1 – LoadOptions オブジェクトを作成し WarningCallback を設定する

**LoadOptions** を使用する際に最初に行うことは、インスタンスを生成することです。重要なのは `WarningCallback` にデリゲートを割り当てることです。このデリゲートは、Aspose.Words が何らかの状況（特に欠落フォント）を通知したいときに毎回呼び出されます。

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Why this matters:** コールバックが無いと、Aspose.Words は欠落フォントをデフォルトフォントに静かに置き換えてしまい、視覚的な変化に気付かないことがあります。`WarningCallback` を登録することで、置換が発生するたびにリアルタイムでログが取得でき、品質保証されたドキュメントパイプラインにとって不可欠です。

## ステップ 2 – フォント置換警告のみに反応する

コールバックが無関係な警告（例：非推奨機能）で氾濫しないか心配になるかもしれません。答えは *はい* ですが、フィルタリングできます。上記のスニペットですでに `args.WarningType == WarningType.FontSubstitution` をチェックしています。この行が **フォント置換警告** のガードとなり、出力を目的のものだけに絞ります。

他の警告タイプも処理したい場合は、`if` ブロックを拡張するだけです：

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

このパターンは **warningcallback** メカニズムの柔軟性を示しており、関心のあるシナリオに合わせて応答をカスタマイズできます。

## ステップ 3 – 設定した LoadOptions を使用してドキュメントを読み込む

リスナーの準備ができたら、最後のステップは `LoadOptions` インスタンスを `Document` コンストラクタに渡すことです。ここが **Aspose.Words LoadOptions example** が真価を発揮する瞬間です。

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**What you’ll see:** DOCX がマシンにインストールされていないフォントを参照している場合、コンソールに次のような行が出力されます：

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

この出力により、フォント問題を監視するために **LoadOptions の使用方法** が正しく機能していることが確認できます。

## 完全動作例（コピー＆ペースト可能）

以下はすぐにコンパイルして実行できる完全プログラムです。3 つのステップをすべてまとめ、フレンドリーバナーなどのちょっとした工夫とエラーハンドリングのデモを加えています。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### 期待される出力

`input.docx` が参照しているフォントがマシンに存在しない環境でプログラムを実行すると、次のような出力が得られます：

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

すべてのフォントが揃っている場合は、成功メッセージだけが表示され、警告行は出力されません。

## よくある落とし穴とプロのコツ

- **Pitfall:** `WarningCallback` の設定を忘れること。コードはロードしますが、置換の詳細が取得できません。  
  **Pro tip:** `LoadOptions` を作成した直後に必ずコールバックを割り当てましょう。コストは低く、後々大きな効果があります。

- **Pitfall:** 間違ったフォルダーを指す相対パスを使用すること。  
  **Pro tip:** `Path.Combine(Environment.CurrentDirectory, "input.docx")` を使って、より堅牢なファイル検索を行いましょう。

- **Pitfall:** 警告がロードを停止すると想定すること。  
  **Pro tip:** フォント置換警告は *情報提供* 用であり、ロード自体は中断されません。置換が発生したときに例外をスローすれば、より厳格な検証が可能です。

- **Pitfall:** フォントが全くインストールされていないサーバー（例：最小構成の Docker イメージ）で実行すること。  
  **Pro tip:** 必要なフォントを事前にインストールするか、アプリに同梱し、コールバックで置換が発生していないことを本番環境で確認しましょう。

## LoadOptions とロード後検査の使い分け

「ロード後にドキュメントを検査すればいいのでは？」と疑問に思うかもしれません。答えはパフォーマンスと正確性にあります。ロード **中** に警告を処理することで、レイアウト計算や PDF 変換が行われる前に問題を早期に捕捉できます。バッチ処理パイプラインでは、余分なステップが時間増加につながるため、特に有用です。

## 例の拡張：置換されたフォントのレポートを保存する

永続的な記録（コンプライアンス目的など）が必要な場合は、コールバックでメッセージをリストに収集し、ロード完了後にファイルへ書き出すように変更します：

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

これでコンソールへのフィードバックに加えて、耐久性のあるログが得られます。

## 次に探求できる関連トピック

- **Aspose.Words でカスタムフォントを埋め込む方法** – 置換を完全に防止します。  
- **LoadOptions を使用してドキュメントサイズを制限する方法** – 悪意のある巨大ファイルから保護します。  
- **Word を PDF に変換し、タイポグラフィを保持する方法** – 警告コールバックアプローチと相性抜群です。  

これらはすべて、`LoadOptions` で築いた基盤の上に構築できます。

## 結論

Aspose.Words における **LoadOptions の使用方法** を最初から最後までカバーしました：オプションを作成し、**フォント置換警告** に特化した `WarningCallback` を設定し、自信を持ってドキュメントをロードする方法です。完全な例はそのまま実行可能で、追加のコツにより一般的な落とし穴を回避できます。  

ぜひ試してみてください—コールバックを他の警告タイプに置き換えたり、データベースへログしたり、アップロードされた Word ファイルを検証する Web サービスに組み込んだりできます。このパターンは柔軟で信頼性が高く、何よりも隠れたフォント置換プロセスを可視化してくれるので、ドキュメントのレンダリングが思わぬ形で崩れることを防げます。

Happy coding, and may your documents always render exactly as intended! 

![Diagram showing the flow of using LoadOptions with a warning callback in Aspose.Words](https://example.com/images/loadoptions-flow.png "How to use LoadOptions diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}