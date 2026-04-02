---
category: general
date: 2026-04-02
description: Aspose.Words を使用して C# ドキュメント内のフォントを検出する方法。フォント設定の構成方法と、欠落フォントを効率的に処理する方法を学びます。
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: ja
og_description: Aspose.Words を使用して C# ドキュメント内のフォントを検出する方法。このガイドでは、フォント設定の構成方法と欠落フォントの処理方法を示します。
og_title: C#でフォントを検出する方法 – 完全ガイド
tags:
- C#
- Aspose.Words
- Document Processing
title: C#でフォントを検出する方法 – 完全ガイド
url: /ja/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でフォントを検出する方法 – 完全ガイド

.NET で Word 文書を読み込む際に、**フォントが見つからない、または置き換えられた**ことを検出したいことはありませんか？ 開発者は文書が参照しているフォントがサーバーにインストールされていないときに壁にぶつかることが頻繁にあります。 良いニュースは、Aspose.Words がそのギャップを見つけるためのクリーンでプログラム的な方法を提供してくれることです。

このチュートリアルでは、**フォント検出の方法**を示すだけでなく、**フォント設定の構成**や**欠損フォントの優雅なハンドリング**も実演します。 最後まで読むと、フォント置換警告をすべて出力する実行可能なコードスニペットが手に入り、ログに記録したり、アラートを出したり、必要に応じてフォントを置き換えることができるようになります。

---

## 必要なもの

- **Aspose.Words for .NET**（最新バージョンがベストです。以下のコードは .NET 6+ を対象にしています）
- .NET 開発環境（Visual Studio、Rider、または VS Code）
- インストールされていないフォントを参照しているサンプル `.docx`（テストに最適）

Aspose.Words 以外に追加の NuGet パッケージは不要で、ソリューションは Windows、Linux、macOS すべてで動作します。

---

## 手順 1: Aspose.Words をインストールして参照設定

まず、プロジェクトにライブラリを追加します。NuGet コマンドはシンプルです。

```bash
dotnet add package Aspose.Words
```

> **プロのコツ:** CI サーバー上でビルドする場合は、予期せぬ破壊的変更を防ぐためにパッケージバージョンを固定してください。

---

## 手順 2: フォント設定を構成（ロードオプションの準備）

文書を開く前に、Aspose.Words にフォントのフォールバック先を教えることができます。これが **フォント設定の構成** 部分で、エンジンが不要なフォント置換を黙って行うのを防ぎます。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

なぜ必要かというと、文書が *Comic Sans* を参照しているのにサーバーに *Calibri* しかない場合、Aspose.Words は *Calibri* に置換し警告を出します。検索パスを設定すれば、予期しない置換を減らせます。

---

## 手順 3: 用意したオプションで文書をロード

ここで実際にファイルを開きます。前ステップで作成した `LoadOptions` を `Document` コンストラクタに直接渡します。

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

ファイルが見つからない、または破損している場合は例外がスローされます。実運用コードでは try/catch で包むことを検討してください。

---

## 手順 4: フォント置換に関する警告をスキャン

Aspose.Words は解析中に警告リストを収集します。その中の `FontSubstitutionWarning` が、どのフォントが置換されたかを正確に教えてくれます。

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

`Warnings` コレクションには他の項目（例: `DocumentStructureWarning`）も含まれることがあります。`FontSubstitutionWarning` のみをフィルタリングすることで、**欠損フォントのハンドリング** シナリオに絞って報告できます。

---

## 手順 5: 完全版・実行可能サンプルを作成

以下がフルプログラムです。新しいコンソールアプリに貼り付けて実行すれば、欠損フォントがコンソールに出力されます。

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**期待される出力**（例）:

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

マシンにすべてのフォントが揃っている場合は、「No font substitutions detected」という行が表示されます。

---

## エッジケースとよくある質問

### 文書に **警告が全く出ない** 場合は？

これは、参照されたすべてのフォントが設定した検索フォルダー内で見つかったことを意味します。サンプルコードの `anySubstitutions` フラグがこのケースをカバーしています。

### 警告をコンソールではなくファイルに **ログ** したい？

もちろん可能です。`Console.WriteLine` をお好みのロガー（Serilog、NLog など）に置き換えてください。`WarningInfo` オブジェクトは `WarningType` と `WarningMessage` も提供しているので、詳細情報が必要なときに活用できます。

### 企業ブランドフォントなど、**特定のフォントは絶対に置換したくない** 場合は？

カスタム置換ルールを追加できます。

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

これで Aspose.Words は *MyBrandFont* を指定した代替フォントにだけ置換し、置換が発生した際には警告が出ます。

### **Linux** コンテナ上でも動作しますか？

はい。必要な `.ttf`/`.otf` ファイルを格納したフォルダーをマウントし、`SetFontsFolder` でそのパスを指すだけです。Aspose.Words は OS にインストールされたフォントに依存しません。

---

## ビジュアル概要

![フォント検出フローチャート](detect-fonts.png "文書内でフォントを検出する手順を示す図")

*画像代替テキスト:* **フォント検出** フローチャート – 設定、ロード、警告検査の流れを示す図。

---

## まとめ – 学んだこと

- Aspose.Words の警告を利用して、**欠損または置換されたフォントを検出**する方法。  
- カスタムフォントフォルダーとデフォルトフォールバックを指す **フォント設定の構成** 方法。  
- ログ出力からカスタム置換ルールまで、**欠損フォントのハンドリング** 戦略。

これらはすべて、任意の .NET ソリューションに組み込めるコンパクトなコンソールアプリに凝縮されています。

---

## 次のステップと関連トピック

- **フォント埋め込み** – 出力文書にフォントを直接埋め込んで将来の置換を防止（`SaveOptions` の `EmbedFullFonts`）。  
- **プログラムによるフォント置換** – 保存前に欠損フォントを特定の代替フォントに置き換える方法。  
- **パフォーマンスチューニング** – バッチ処理時に `FontSettings` をキャッシュして高速化。

これらのトピックに興味がある場合は、*configure font settings* と *handle missing fonts* を検索すると、Aspose.Words におけるフォント管理の深掘り情報が見つかります。

---

Happy coding! 変わったフォントのエッジケースがありますか？ コメントで教えてください。一緒にトラブルシュートしましょう。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}