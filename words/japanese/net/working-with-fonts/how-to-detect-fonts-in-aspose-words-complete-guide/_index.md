---
category: general
date: 2026-04-21
description: Aspose.Words for C# を使用して、フォントの検出、警告の取得、コールバックの設定、警告の列挙方法を学びましょう。信頼性の高いフォント処理のためのステップバイステップガイド。
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: ja
og_description: Aspose.Wordsでフォントを検出する方法は？このチュートリアルでは、警告を取得し、コールバックを設定し、C#で警告を列挙する方法を示します。
og_title: Aspose.Wordsでフォントを検出する方法 – 完全ガイド
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Wordsでフォントを検出する方法 – 完全ガイド
url: /ja/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Wordsでフォントを検出する方法 – 完全ガイド

Word 文書を読み込む際に、欠落している **フォントを検出する方法** を考えたことはありませんか？これは、レガシーファイルやクロスプラットフォーム展開を扱うときに、思った以上に頻繁に発生するシナリオです。このチュートリアルでは、**警告を取得**し、**コールバックを設定**し、**警告を列挙**する完全な実行可能サンプルを通して、どのフォントが置き換えられたかを常に把握できるようにします。

使用するのは Aspose.Words for .NET（執筆時点 v24.9）と純粋な C# です。外部サービスや魔法は不要—API と数行のコードだけです。最後まで読めば、すべてのフォント置換を検出し、ログに記録し、重要なフォントが欠けている場合はロードを中止するかどうかを判断できるようになります。

### 必要なもの
- **Aspose.Words for .NET**（NuGet でインストール: `Install-Package Aspose.Words`）
- .NET 6.0 以降（.NET Framework でも動作します）
- フォントがマシンに存在しない DOCX サンプル（例: “MyCustomFont.ttf” を参照しているもの）
- Visual Studio、Rider、またはお好みの C# エディタ

> **プロのコツ:** 欠落フォントを含む文書が手元にない場合は、システム上のフォントファイルの名前を変更するか、DOCX の XML を編集して存在しないフォントファミリを参照させてください。

---

## Aspose.Wordsでフォントを検出する方法

基本的な考え方は、Aspose.Words の警告システムにフックすることです。ライブラリが要求されたフォントを見つけられないと、`WarningType.FontSubstitution` 警告が発行されます。カスタムの `IWarningCallback` 実装を提供することで、ロードプロセス中に置き換えられた **フォントを検出** できます。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **なぜこれが機能するのか:** Aspose.Words は重大でない問題ごとに `Warning` メソッドを呼び出します。`WarningInfo` オブジェクトを保存すれば、タイプ、メッセージ、コンテキストにフルアクセスでき、**置き換えられたフォントを検出**するのに必要な情報がすべて手に入ります。

---

## ドキュメント読み込み時に警告を取得する方法

コレクタができたので、`LoadOptions` にそれを使用するよう指示します。これが **警告を取得する** パズルの鍵です。

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **エッジケース:** ストリームからドキュメントを読み込む場合（`new Document(stream, loadOptions)`）でも同じコールバックが機能します—ファイルパスの代わりにストリームを渡すだけです。

この時点でドキュメントは完全にロードされますが、フォント置換に関する警告はすべて `warningCollector.Warnings` に安全に格納されています。

---

## 警告を列挙し、フォント置換をレポートする方法

最後に、収集した警告を走査し、フォント置換に関するものだけを **列挙** します。このステップで生データを読みやすいレポートに変換します。

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**期待される出力**（例）:

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

ドキュメントに欠落フォントがなければ、ループは何も出力せずに終了します—心配無用です。

---

## 完全動作サンプル（すべての手順を 1 ファイルにまとめた例）

以下はコンソールプロジェクトにコピペできる完全プログラムです。**フォントを検出する方法**、**警告を取得する方法**、**コールバックを設定する方法**、そして **警告を列挙する方法** を一つの流れにまとめています。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**このプログラムを実行**すると、Aspose.Words が置き換えたすべてのフォントがコンソールに表示されます。出力をログファイルにリダイレクトしたり、アラートを発生させたり、重要なフォントが欠けている場合はロード自体を中止したりすることも可能です。

---

## よくある質問と落とし穴

### 必要なフォントが欠けているときにロードを停止したい場合は？
コールバック内で `WarningInfo` オブジェクトをチェックし、特定のフォント名が現れたら例外をスローすれば、ロードが中止されます。これにより完全な制御が可能です。

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### PDF や他の形式でも同様に機能しますか？
はい。Aspose.Words は PDF、RTF、HTML でも同じ警告インフラを使用します。ファイル拡張子を置き換えるだけで、コードはそのまま動作します。

### コンソールではなくファイルに警告を記録したい場合は？
`Console.WriteLine` をお好みのロギングフレームワーク（`Serilog`、`NLog` など）に置き換えてください。`WarningInfo` クラスは `Message`、`Source`、`Exception` を公開しているので、詳細なログが簡単に作れます。

### パフォーマンスへの影響はありますか？
オーバーヘッドはごくわずかです—Aspose.Words は内部で既に警告を生成しています。コールバックはそれらをリストに保存するだけで、警告数に対して O(n) の処理です。通常の文書であれば、総ロード時間の 1 % 未満の影響にとどまります。

---

## ビジュアルサマリー

![Aspose.Wordsでフォントを検出する方法 – 警告フロー図](https://example.com/images/font-detection-diagram.png "フォント検出")

*代替テキスト:* **フォント検出** – 警告コールバック、コレクション、列挙ステップを示す図。

---

## まとめ

本稿では **フォントを検出する方法** を、**警告を取得**、**コールバックを設定**、**警告を列挙** する手順で解説しました。完全なコードサンプルは、任意の .NET アプリケーションにすぐに組み込める実装パターンを示しています。

次に試したいこと:

- **他の問題**（例: 画像変換エラー）に対する **警告取得** 方法
- カスタムロギングフレームワーク向けの **コールバック設定** 方法
- バッチジョブで **複数文書の警告列挙** 方法
- **Aspose.Words.Fonts.FontSettings** を使ってフォールバックフォントフォルダを設定し、置換回数自体を減らす

ぜひコレクタを自分のロギングスタイルに合わせて調整し、予期しないフォント置換に驚かされることがなくなったかどうか、コメントで教えてください。ハッピーコーディング！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}