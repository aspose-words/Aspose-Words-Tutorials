---
category: general
date: 2026-01-14
description: Aspose.WordsでWord文書を読み込む際にフォント置換の警告をログに記録します。欠落フォントを検出する方法と、C#で欠落フォントを取得する方法を学びます。
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: ja
og_description: Aspose.WordsでWord文書を読み込む際にフォント置換の警告をログに記録します。欠落フォントを検出し、C#で欠落フォントを取得する方法をご紹介します。
og_title: フォント置換警告のログ – 完全な Aspose.Words ガイド
tags:
- Aspose.Words
- C#
- Document Processing
title: フォント置換警告のログ – 完全な Aspose.Words ガイド
url: /ja/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォント置換警告のログ記録 – 完全な Aspose.Words ガイド

フォント置換警告をログに記録することは、Aspose.Words で Word 文書を読み込んだ後も外観がまったく同じであることを保証するために不可欠です。**detect missing fonts** の方法や **how to capture missing fonts** を知りたいと思ったことがあるなら、ここが正しい場所です。  

このチュートリアルでは、実際のシナリオを順に解説し、完全な C# コードを示し、各行がなぜ重要かを説明します。最後まで読めば、すべてのフォント置換イベントをログに記録し、対処できるようになります—謎の警告は残りません。

![Log font substitution warnings example](/images/font-warnings.png "Screenshot showing console output of log font substitution warnings")

## 学べること

- Aspose.Words がフォント置換のために型付き警告を発生させるように `LoadOptions` を設定する方法。  
- ドキュメントの読み込み中に **detect missing fonts** を行う正確な手順。  
- **capture missing fonts** をクリーンに取得し、独自のログや監視システムに書き込む方法。  
- エッジケースの処理（例：サーバーにインストールされていないフォントが文書に含まれている場合）。

### 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.6 以降でも動作します）。  
- 有効な Aspose.Words for .NET ライセンス（または無料トライアル）。  
- C# とコンソールアプリケーションの基本的な知識。  

これらが揃っているなら、さっそく始めましょう。

## ステップ 1 – 型付き警告を発生させるように LoadOptions を設定する

解決策の核心は `LoadOptions.FontSubstitutionWarning` にあります。これを `RaiseTypedWarnings` に切り替えることで、要求した正確なフォントが見つからないたびに Aspose.Words がイベントを発火させます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Why this matters:**  
> デフォルトの動作では、欠損フォントが静かに最も近いフォントに置き換えられ、予期しないレイアウトの乱れを招くことがあります。型付き警告を上げることで、完全な可視性が得られます。

## ステップ 2 – 警告イベントを購読する

今度は `loadOptions.FontSubstitutionWarning` にフックします。ラムダ式は `e` オブジェクトを受け取り、どのフォントが欠損し、代わりにどのフォントが使用されたかを正確に教えてくれます。

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** Web サーバー上で実行する場合は、`Console.WriteLine` を構造化ロガー（Serilog、NLog など）に置き換えて、後でデータをクエリできるようにしましょう。

## ステップ 3 – 設定したオプションでドキュメントを読み込む

警告メカニズムが整ったら、通常通りドキュメントを読み込むだけです。欠損フォントがあるたびにイベントが自動的に発火します。

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### 期待されるコンソール出力

`input.docx` がインストールされていない *MyFancyFont* を参照している場合、次のように表示されます：

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

各行は **detect missing fonts** イベントに対応しており、完全な監査トレイルを提供します。

## ステップ 4 – エッジケースと高度なシナリオの処理

### 4.1 置換が発生しない場合

時々、文書がすでに存在するシステムフォントだけを使用していることがあります。その場合、警告イベントは発生せず、出力のないクリーンなコンソールが得られます。これは、環境に必要なフォントがすべて揃っていることを示す良いサインです。

### 4.2 後で分析するための警告の取得

夜間レポート用に警告を保存したい場合は、リストに収集します：

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

読み込み後、`missingFonts` を JSON にシリアライズしたり、データベースに書き込んだり、サマリーをメールで送信したりできます。

### 4.3 PDF やその他のフォーマットでの使用

同じ `LoadOptions` アプローチは、PDF、RTF、さらには HTML ファイルの `Load` 呼び出しでも機能します。同じオプションインスタンスを渡すだけで、Aspose.Words は一致しないフォントに対して警告を上げます。

## ステップ 5 – プログラムで結果を検証する

コンソールを目視で確認する代わりに自動テストを好む場合は、リストに期待通りのエントリが含まれているかアサートします：

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

このスニペットは、コード内で **how to capture missing fonts** を実演しており、単なるログに留まりません。

## よくある落とし穴と回避方法

| 落とし穴 | 発生理由 | 対策 |
|---------|----------|------|
| `RaiseTypedWarnings` を設定し忘れる | デフォルトは `DoNotRaise` で、イベントが発生しません。 | ステップ 1 で示したように `FontSubstitutionWarning` を明示的に設定してください。 |
| Web アプリで `Console.WriteLine` を使用する | IIS/ASP.NET Core ではコンソール出力が消えてしまいます。 | 永続的なロガー（例: Serilog）に切り替えてください。 |
| 相対パスでドキュメントを読み込む | 実行時に作業ディレクトリが異なる可能性があります。 | 絶対パスを使用するか、`Path.Combine(AppContext.BaseDirectory, "input.docx")` を使用してください。 |
| `SubstitutedFontName` を無視する | どの代替フォントが選択されたかの情報が失われます。 | `FontName` と `SubstitutedFontName` の両方を必ずログに記録してください。 |

## ボーナス: フォントインストールの自動化

デプロイ環境を管理できる場合、PowerShell スクリプトで欠損フォントを事前にインストールできます：

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

アプリケーション起動前にこれを実行すれば、ほとんどの **detect missing fonts** 警告が完全に解消されます。

## 結論

Aspose.Words で Word 文書を読み込む際に **log font substitution warnings** を行うために必要なすべてを網羅しました。`LoadOptions` を設定し、警告イベントを購読し、必要に応じて結果を永続化すれば、任意の .NET プロジェクトで **detect missing fonts** を確実に行い、**how to capture missing fonts** を理解できます。

コードを取り入れ、ロガーを自分のスタックに合わせて調整すれば、サイレントなフォント置換に驚くことはなくなります。次のステップとしては、例えば:

- 重要なフォントが欠如している場合にビルドを失敗させるため、警告リストを CI/CD パイプラインに統合する。  
- 多数の文書に対するフォント使用状況を監視するようにアプローチを拡張する。  
- カスタム代替フォントを提供するために Aspose.Words の `FontSettings` API を検討する。

質問や難しいシナリオがありますか？コメントを残してください。一緒にトラブルシューティングしましょう。ハッピーコーディング！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}