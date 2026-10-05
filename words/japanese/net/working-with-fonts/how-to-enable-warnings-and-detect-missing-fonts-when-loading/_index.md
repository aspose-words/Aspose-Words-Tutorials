---
category: general
date: 2026-02-21
description: Aspose.Words for C# を使用して、警告を有効にする方法、フォントの欠落を検出する方法、そして docx を安全にロードする方法を学びましょう。ステップバイステップのガイドに従ってください。
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: ja
og_description: 警告を有効にし、欠落フォントを検出し、Aspose.Wordsでdocxファイルを正しく読み込む方法。完全なコード例が含まれています。
og_title: DOCX を読み込む際に警告を有効にし、欠落フォントを検出する方法
tags:
- C#
- Aspose.Words
- Document processing
title: DOCX ファイルを読み込む際に警告を有効にし、欠落フォントを検出する方法
url: /ja/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX ファイルの読み込み時に警告を有効にし、欠落フォントを検出する方法

欠落フォントが静かに文書のレンダリングを乱す前に、**警告を有効にする方法**を疑問に思ったことはありませんか？ あなたは一人ではありません—多くの開発者はライブラリが自動的に「正しく」処理してくれると想定し、後でフォントが何の手がかりもなく置き換えられていたことに気づきます。

このチュートリアルでは、**警告を有効にする方法**、**欠落フォントを検出する方法**、そして Aspose.Words for .NET を使用した **docx の正しい読み込み方法** を正確に示します。最後までに、コンソールにすべてのフォント置換警告を出力する実行可能なサンプルが手に入り、ファイル内部で何が起こったかを推測する必要がなくなります。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）  
- Visual Studio 2022 またはお好みの C# IDE  
- **Aspose.Words** NuGet パッケージ (`Install-Package Aspose.Words`)  
- マシンにインストールされていないフォントが含まれている可能性のある DOCX ファイル（ここでは `input.docx` と呼びます）

> **プロのコツ:** テストファイルがない場合は、カスタムの社内フォントを使用した Word 文書を開き、`input.docx` として保存してください。これにより、取得したい警告が発生します。

## ソリューションの概要

1. `FontSubstitutionWarnings` を有効にした `LoadOptions` オブジェクトを **作成** する。  
2. そのオプションを使用して DOCX ファイルを **ロード** する。  
3. `WarningCallback` コレクションを調べ、`FontSubstitution` エントリがあるか **検査** する。  
4. **リアクション** – ログに記録したり、表示したり、欠落フォントをプログラムで置き換えることもできます。

以下では各ステップを分解し、*なぜ*重要なのかを説明し、完全な実行可能コードスニペットを提供します。

---

## ステップ 1: Aspose.Words をインストールし、プロジェクトを設定する

警告を有効にする **方法** を実行する前に、それを実際にサポートするライブラリが必要です。

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

または、Visual Studio のパッケージ マネージャ コンソールで:

```powershell
Install-Package Aspose.Words
```

> **このステップの理由**  
> パッケージがなければ、`LoadOptions`、`Document`、警告インフラストラクチャは存在しません。NuGet 参照を追加することで、最新の安定版（執筆時点では 24.5）を取得できるようになります。

## ステップ 2: フォント置換警告を有効にするロード オプションを作成する

**警告を有効にする方法** の核心は `LoadOptions` クラスにあります。`FontSubstitutionWarnings` を `true` に設定すると、欠落フォントを置き換えるたびにエンジンが記録するようになります。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **なぜこのフラグを有効にするのか?**  
> デフォルトでは Aspose.Words は欠落フォントをサイレントにフォールバック（通常は Arial）に置き換えます。これによりレイアウトのずれ、見えない文字、ブランド違反が発生する可能性があります。フラグをオンにすると、完全に可視化できます。

## ステップ 3: 設定したオプションを使用して DOCX ファイルをロードする

警告が有効な状態で **docx の読み込み方法** が分かったので、実際にロードを行います。

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **内部で何が起きているか?**  
> DOCX を解析する際、Aspose.Words はすべての `<w:rFonts>` 要素をチェックします。指定されたフォントがインストールされていない場合、`FontSubstitution` 警告を記録し、デフォルトフォントにフォールバックします。警告を有効にしたため、これらのエントリは `document.WarningCallback.Warnings` に格納されます。

## ステップ 4: フォント置換警告を取得して表示する

`WarningCallback` プロパティは `WarningInfoCollection` を保持しています。これをループし、`WarningType.FontSubstitution` をフィルタリングしてメッセージを出力します。

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**期待される出力**（例）:

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **これらのメッセージはどうするか?**  
> ファイルにログを書き込んだり、UI に表示したり、カスタムのフォントフォールバック処理をトリガーしたりできます。重要なのは、後で推測するのではなく、*欠落フォントを検出できる* ことです。

## ステップ 5: （オプション）欠落フォントを特定のフォールバックに置き換える

社内で統一したいフォントがある場合、警告を処理してリアルタイムで置き換えることができます。

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **なぜこれを検討するか?**  
> すべての生成ドキュメントで視覚的一貫性を保証し、ブランド遵守にとって重要です。

## 完全な実行可能サンプル

以下はコンソール アプリにコピー＆ペーストできる単一の C# ファイルです。パッケージのインストールから警告の出力まで、すべてを網羅しています。

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**実行方法**: プロジェクト フォルダーで `dotnet run` を実行します。フォントが欠落している場合、警告が出力され、オプションの置換がファイル保存前に適用されます。

## よくある質問

### PDF 変換でも機能しますか？

はい。警告を処理した後、`doc.Save("output.pdf")` を呼び出すと、置換されたフォントが DOCX と同様に PDF に反映されます。

### 特定のフォントに対して警告を抑制したい場合は？

ループ内でフィルタリングできます—無視したいフォント名が `Message` に含まれる `WarningInfo` をスキップすればよいです。

### 古い Aspose.Words バージョンでも `FontSubstitutionWarnings` は利用できますか？

バージョン 20.5 で導入されました。古いバージョンを使用している場合は、NuGet 経由でアップグレードしてください。API の変更は下位互換です。

## 結論

**警告を有効にする方法** を順に説明し、**欠落フォントを検出する方法** を示し、Aspose.Words を使用してフォント置換を完全に可視化しながら **docx の正しい読み込み方法** を実演しました。`document.WarningCallback.Warnings` を検査することで、信頼できる監査ログが得られ、サイレントなフォールバックはなくなります。

次のステップは？ 警告ロジックを Serilog などのロギング フレームワークに組み込んだり、ユーザーに配布する前に欠落フォントをハイライトする UI を構築したりしてみてください。また、`FontSettings` クラスを調べてフォント置換ポリシーをより細かく制御することもできます。

コーディングを楽しんで、ドキュメントが常に意図した通りにレンダリングされますように！ 

![DOCX ファイルの読み込みからフォント置換警告の取得までのフローを示す図 – Aspose.Words で警告を有効にする方法](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}