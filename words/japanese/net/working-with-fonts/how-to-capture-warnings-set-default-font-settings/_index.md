---
category: general
date: 2026-03-19
description: Aspose.Wordsで警告を取得し、デフォルトのフォント設定を行い、Word 文書の読み込み時にフォントの欠落を検出する方法を学びます。
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: ja
og_description: Aspose.Wordsで警告を取得し、デフォルトのフォント設定を行い、Word文書の読み込み時に欠落フォントを検出する方法。
og_title: 警告の取得方法 – デフォルトフォント設定
tags:
- Aspose.Words
- C#
- Document Processing
title: 警告を取得する方法 – デフォルトフォント設定
url: /ja/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 警告の取得方法 – デフォルトフォント設定の設定

**警告の取得方法**は、Aspose.Words を使用する際に特に重要です。特に、ドキュメントが特定のフォントに依存していて、対象マシンにそのフォントが存在しない場合に役立ちます。DOCX を開いたときにレイアウトが崩れていると感じたことはありませんか？その原因は、欠落フォントに関する警告に隠されています。  

このガイドでは、**警告の取得方法**を **Word 文書をロード** する際に **デフォルトフォント設定を行う** 方法と、最終的に **欠落フォントを検出** してプログラムで対処できるようにする手順を解説します。余計な説明は省き、完全に実行可能なサンプルと各行の意図を示します。

> *プロのコツ:* 警告を早期に取得しておくことで、後から発生する謎のレイアウト不具合のデバッグ時間を大幅に削減できます。

---

## 必要なもの

- **Aspose.Words for .NET**（2026 年時点の最新バージョン）。  
- .NET 開発環境（Visual Studio、Rider、または VS Code）。  
- インストールされていないフォントを参照しているサンプル DOCX（例: Linux 環境で *Comic Sans MS* を使用した文書）。  

以上だけです。Aspose.Words 以外に追加の NuGet パッケージは不要です。

---

## Step 1 – 警告取得が必要な理由を理解する

Aspose.Words が文書を解析するとき、ホストに存在しないフォントに出くわすことがあります。デフォルトではライブラリは静かに代替フォントに置き換えますが、これにより改行位置や行間が変わったり、テキストが消えてしまうことがあります。  

**WarningCallback** と **FontSettings** オブジェクトを組み合わせることで、次の 2 つが実現できます。

1. **可視化** – 置換が発生するたびに `WarningInfo` エントリが取得できます。  
2. **制御** – 事前にデフォルトフォントを設定して、予期しないビジュアルの変化を最小限に抑えられます。

エンジンがフードの下で部品を交換するたびに叫ぶ「監視犬」を設置するイメージです。

---

## Step 2 – デフォルトフォント設定を行う

ここが最初のサブキーワード、**set default font settings** が登場する箇所です。`FontSettings` インスタンスを作成し、必要に応じて代替フォントが格納されたフォルダーを指定します。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **なぜ必要か？**  
> フォールバックを指定しない場合、Aspose.Words はスタイルに合致する最初のシステムフォントを自動的に選択しますが、これが大きく異なる場合があります。既知のデフォルトを設定すれば、マシン間で一貫したレンダリングが保証されます。

---

## Step 3 – 警告コールバックを準備して警告を取得する

次に **how to capture warnings** を実装します。`WarningInfoCollection` をロードオプションに紐付けることで、ロード中に発生したすべての警告を保存できます。

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` は `IWarningCallback` を実装しているため、Aspose.Words が自動的に各警告を `warningInfos` にプッシュします。ポーリングは不要です。

---

## Step 4 – 設定したオプションで Word 文書をロードする

ここで二つ目のサブキーワード、**load word document** が活躍します。`FontSettings` と `WarningCallback` の両方を `LoadOptions` に渡して文書を読み込みます。

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

文書がインストールされていないフォントを参照している場合、警告コールバックは `WarningType.FontSubstitution` エントリを取得します。

---

## Step 5 – 収集した警告から欠落フォントを検出する

最後に三つ目のサブキーワード、**detect missing fonts** に答える形で、収集した警告を走査します。

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

典型的な出力例は次の通りです。

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

この行は、どのフォントが欠落していて、どの代替フォントが使用されたかを正確に示します。ログに記録したり、ユーザーに表示したり、カスタムのフォントインストール処理をトリガーしたりできます。

---

## 完全な実行可能サンプル

以下はコンソールアプリケーションにコピペできるフルプログラムです。**警告の取得方法**、**デフォルトフォント設定**、**Word 文書のロード**、**欠落フォントの検出** をすべて一連のフローで示しています。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**期待される結果:** 指定した DOCX がインストールされていないフォントを参照している場合、コンソールに置換ごとの警告が出力されます。すべてのフォントが揃っていれば、ループは何も出力しません。

---

## よくある落とし穴とエッジケース

| Situation | Why it Happens | How to Handle It |
|-----------|----------------|------------------|
| **警告が全く出ない** のにレイアウトが崩れている | 文書が *埋め込みフォント* を使用している可能性があり、Aspose.Words は置換せずにそのまま描画します。 | `Document.HasEmbeddedFonts` を確認し、別マシンで必要な場合は埋め込みフォントを抽出することを検討してください。 |
| **複数の警告が** |  |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}