---
category: general
date: 2026-02-10
description: Aspose.Wordsでデフォルトフォントを設定し、デフォルトインポートフォントを指定する際に、フォントの変更を監視するための警告コールバックを設定します。完全なステップバイステップの解決策をご確認ください。
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: ja
og_description: デフォルトフォントを設定し、デフォルトインポートフォントを設定する際に、フォントの変更を監視するために警告コールバックを設定します。Aspose.Words
  の完全なチュートリアルをご覧ください。
og_title: C#で警告コールバックを設定する – 完全ガイド
tags:
- Aspose.Words
- C#
- Document Import
title: C#で警告コールバックを設定する – フォント処理の完全ガイド
url: /ja/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で警告コールバックを設定する – フォント処理の完全ガイド

Word ドキュメントを読み込む際に **警告コールバックを設定** したり、同時に *デフォルトフォントを構成* したりする必要があったことはありませんか？ あなたは一人ではありません。自動レポートジェネレータやドキュメント変換パイプラインなど、実際のプロジェクトではフォントが欠如するとレイアウトが静かに崩れ、これらの問題を検出する唯一の方法は警告コールバックを通じて **フォント変更を監視** することです。

このチュートリアルでは、Aspose.Words for .NET を使用して **警告コールバックを設定**、**デフォルトフォントを構成**、さらには **デフォルトインポートフォントを設定** するハンズオン例を順に解説します。最後まで読むと、すぐに実行できるコードスニペットを手に入れ、各要素が重要な理由を理解し、カスタムフォントフォルダーやサイレント置換といったエッジケースに合わせて調整する方法が分かります。

---

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）  
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）  
- 使用したいフォールバックフォントが入っているフォルダー（例: `fonts/Arial.ttf`）  
- C# コンソールアプリの基本的な知識  

追加のライブラリは必要ありません。

---

## 手順 1: LoadOptions を作成し **デフォルトフォントを構成**

フォント処理を制御したいときに最初に行うことは、`LoadOptions` インスタンスを作成することです。このオブジェクトはインポート時に欠損フォントをどのように扱うかを Aspose.Words に指示します。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**これが重要な理由:**  
ソースドキュメントがサーバーにインストールされていないフォントを参照している場合、Aspose.Words は指定したフォルダーを参照します。これが **デフォルトインポートフォントを設定** の核心であり、警告が発生する前に置換フォントの場所を明示的にライブラリに伝えることになります。

---

## 手順 2: **警告コールバックを設定**して **フォント変更を監視**

Aspose.Words はフォントを置換する必要があるたびに（他の情報も含めて）`WarningInfoCollection` を発行します。ハンドラを添付することで、各置換をログに記録したり、リアクションを取ったりできます。

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**これが重要な理由:**  
単に **デフォルトフォントを構成** するだけでは、実際にどのフォントが置換されたかを監査するには不十分です。コールバックはリアルタイムのログを提供し、**フォント変更を監視** の要件を満たし、CI パイプラインで予期しないフォールバックを早期に検出するのに役立ちます。

---

## 手順 3: 用意したオプションでドキュメントをロード

ロードオプションが完全に準備できたので、任意の `.docx` ファイルを安全にロードできます。置換が発生するとコールバックが自動的に呼び出されます。

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**期待される出力:**  
ソースが存在しないフォントを使用している場合、コンソールに次のような出力が表示されます：

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

この出力により、**警告コールバックを設定** に成功し、**デフォルトインポートフォント** が有効になったことが確認できます。

---

## 手順 4: （オプション）フォント置換動作を微調整

場合によっては、元の要求に関係なく *すべて* の欠損フォントを単一のファミリーに置換したいことがあります。Aspose.Words では *フォールバックフォント* をグローバルに設定できます。

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**使用シーン:**  
ブランドが限定されたフォントセットしか許可していない場合に PDF を生成すると、ソースが珍しいフォントを使用しようとしても、すべてのドキュメントで一貫性が保たれます。

---

## 手順 5: ドキュメントを保存またはさらに処理

ロード後は、編集、PDF への変換、テキスト抽出など、必要な処理を続けられます。以下は、置換されたフォントを保持したままドキュメントを PDF として保存する簡単な例です。

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

生成された PDF は、置換が行われた箇所すべてでフォールバックフォントが表示され、**警告コールバックを設定** が期待通りに機能したことを視覚的に確認できます。

---

## よくある落とし穴とプロのコツ

| 落とし穴 | 発生理由 | 対策 |
|---------|----------|------|
| **コールバックが発火しない** | `LoadOptions.WarningCallback` がドキュメントをロードする *前に* 設定されていませんでした。 | 常に `new Document(...)` を呼び出す **前に** コールバックを添付してください。 |
| **フォントフォルダーが間違っている** | パスのタイプミスまたは読み取り権限がありません。 | フォルダーが存在し、アプリが `Read` アクセス権を持っていることを確認してください。信頼性のために絶対パスを使用します。 |
| **複数の置換が発生し、出力が騒がしい** | 欠損フォントが多数ある大規模ドキュメント。 | `WarningType.FontSubstitution` で警告をフィルタリング（上記参照）するか、コンソールではなくログファイルに書き出してください。 |
| **フォールバックフォントが適用されない** | フォールバックフォントがマシンにインストールされていません。 | `SetFontsFolder` に渡したフォルダーに `.ttf`/`.otf` ファイルを配置してください。Aspose.Words は直接ロードするため、OS にインストールする必要はありません。 |

**プロのコツ:** CI/CD パイプラインで実行する場合、コンソール出力をビルド成果物にリダイレクトしてください。これにより、ビルド中に発生したすべてのフォント置換の監査ログが残ります。

---

## 完全動作例（コピー＆ペースト可能）

以下は新しいコンソールアプリプロジェクトに貼り付けられる完全なプログラムです。すべての手順、using 文、コメントが含まれています。

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**期待されるコンソール出力**（`Times New Roman` が欠如していると仮定）

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

プログラムを実行し、`output.pdf` を開くと、必要な箇所すべてでフォールバックフォントが適用されたドキュメントが表示されます。

---

## 結論

これで、Aspose.Words を使用する際に C# で **警告コールバックを設定**、**デフォルトフォントを構成**、**フォント変更を監視**、そして **デフォルトインポートフォントを設定** するための、堅牢で本番環境向けのパターンが手に入りました。ロード前に警告コレクタを添付し、`FontSettings` を信頼できるフォントフォルダーに指し、必要に応じてグローバルフォールバックを強制することで、フォント置換に対する完全な可視性と制御が得られます。これは堅実なドキュメント処理パイプラインに必須です。

次のステップに進みませんか？このアプローチを以下と組み合わせてみてください：

- **データベースからの動的フォントロード**（実行時に `FontSettings.SetFontsFolder` を使用）  
- **構造化ログ（JSON または CSV）に書き込むカスタム警告ハンドラ**（分析用）  
- **並列ドキュメント処理**（各スレッドが独自の `LoadOptions` を持ち、相互干渉を防止）  

自由に実験し、コードを自分のアーキテクチャに合わせて調整し、コメントで発見を共有してください。コーディングを楽しんで！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}