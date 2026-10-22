---
category: general
date: 2026-04-05
description: Aspose フォント置換ガイド：Word 文書の読み込み時に欠落フォントを検出する方法。フォント設定の構成と欠落フォントの効率的な処理方法を学びましょう。
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: ja
og_description: Aspose フォント置換ガイド：Word 文書の読み込み時に欠落フォントを検出する方法。フォント設定の構成と欠落フォントの効率的な処理方法を学びましょう。
og_title: Aspose フォント置換 – Word 文書の欠損フォントを検出
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose フォント置換 – Word 文書の欠損フォントを検出
url: /ja/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose フォント置換 – Word 文書で欠落フォントを検出する

あるマシンでは完璧に見える Word ファイルが、別のマシンでは奇妙なフォント変更が起きたことはありませんか？ それが典型的な **aspose font substitution** の問題で、通常は対象システムにフォントが欠落していることを意味します。このチュートリアルでは、**Word 文書をロードする際に欠落フォントを検出**する方法、**フォント設定を構成**する方法、そして **欠落フォントを優雅に処理**する方法をステップバイステップで解説します。

完全に実行可能な C# のサンプルを通して、各行が何を意味するのかを説明し、期待されるコンソール出力も示します。最後まで読めば、ドキュメントがロードされた瞬間にフォント置換を検出でき、推測に頼る必要はなくなります。

## 学べること

- Aspose.Words のフォント警告用診断コレクタを有効にする方法。  
- カスタム **font settings** を使用して **Word 文書をロード** するための正確なコード。  
- `WarningInfo` オブジェクトを列挙して、置換されたフォントをすべてリストアップする方法。  
- 不要な警告を抑制したり、フォールバックフォントを提供したりするコツ。  
- Visual Studio にコピペできる、すぐに実行可能なサンプル。

### 前提条件

- .NET 6.0 以降（API は .NET Framework でも同様に動作）。  
- Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）。  
- インストールされていないフォントを参照している Word ファイル（例：`MissingFont.docx`）。  

上記が揃っていれば、さっそく始めましょう。

## Step 1 – 診断コレクタを有効にする（フォント設定の構成）

まず最初に行うべきことは、Aspose.Words にフォント置換警告を記録させることです。これは `FontSettings` オブジェクトを作成し、`LoadOptions` インスタンスに割り当てることで実現します。フォント処理の「デバッグライト」をオンにするイメージです。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**なぜ必要か？**  
`FontSettings` オブジェクトが無いと警告コレクタは黙ってしまい、どのフォントが置換されたか分かりません。空の設定で初期化することで、Aspose はデフォルトのシステムフォントを使用しつつ、置換情報を追跡します。

> **プロのコツ:** 企業フォントが格納された特定フォルダーがある場合は、`SetFontsFolder("path")` で `FontSettings` に指定しましょう。これにより欠落フォント警告の数を減らせます。

## Step 2 – 設定したオプションで文書をロードする（Word 文書のロード）

コレクタが有効になったら、同じ `LoadOptions` を使って `.docx` ファイルをロードします。ここで Aspose は文書を走査し、すべてのフォント参照をチェックして置換が必要かどうかを判断します。

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**なぜ重要か？**  
単に `new Document("MissingFont.docx")` と呼び出すだけではデフォルト設定が適用され、警告リストは空のままです。`loadOptions` を渡すことで、診断コレクタがロードパイプラインにフックされます。

## Step 3 – フォント置換警告を取得して表示する（欠落フォントの検出）

文書がメモリ上にロードされたら、Aspose は警告を `document.WarningCallback.Warnings` に格納します。そのコレクションを走査し、`WarningType.FontSubstitution` でフィルタリングして説明文を出力します。各説明文は「どのフォントが欠落し、代わりに何が使用されたか」を示します。

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**期待されるコンソール出力**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

この出力は、コードを実行しているマシンで欠落しているフォントを正確に示します。これを元にフォントをインストールするか、文書に埋め込むか、置換のままにするかを判断できます。

![Console output showing aspose font substitution warnings](/images/aspose-font-substitution-console.png)

*画像の代替テキスト:* aspose font substitution – 置換されたフォントを一覧表示したコンソール出力

## Step 4 – 任意：置換動作をカスタマイズする（欠落フォントの処理）

単に置換が起きたことを知りたいだけでなく、**どのように**置換させるかを制御したい場合があります。Aspose.Words ではカスタム `IFontSubstitutionRule` を登録できます。以下は、欠落フォントがあればすべて `Tahoma` にフォールバックさせる簡単な例です。

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**いつ使うべきか？**  
Web サービスで PDF を生成し、クライアントがすべて `Tahoma` を表示できることが分かっている場合、フォールバックを強制することで多数のフォントファイルを配布せずに視覚的一貫性を保てます。

## 完全動作サンプル（全ステップ統合）

新しいコンソールプロジェクトに貼り付けてそのままコンパイルできる、全体プログラムです。Aspose.Words の NuGet パッケージをインストールしていることが前提です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

プログラムを実行し、コンソールを確認すれば、すべての欠落フォントイベントが出力されます。その後、フォントをインストールするか、埋め込むか、フォールバックのままにするかを決められます。

## Frequently Asked Questions

**Q: PDF 変換でも同様に機能しますか？**  
はい。後で `doc.Save("output.pdf")` を呼び出すと、ロード時に置換されたフォントが PDF に埋め込まれます。したがって、早期に警告を捕捉しておくことで、最終的な PDF で予期せぬフォント変更が起きるのを防げます。

**Q: 処理対象が多数の文書の場合はどうすれば良いですか？**  
ロードロジックを try‑catch ブロックで囲み、`FontSettings` インスタンスを文書間で再利用してください。これによりオーバーヘッドが削減され、各ファイルで警告コレクタが有効なままになります。

**Q: 警告を完全に抑制することは可能ですか？**  
`loadOptions.WarningCallback = null;` と設定すればロード時の警告は出ませんが、**欠落フォントの検出**ができなくなるため、通常は推奨されません。

## Conclusion

**aspose font substitution** をマスターするために必要なすべてを網羅しました：診断コレクタの有効化、カスタム **font settings** での Word ファイルのロード、欠落フォント一覧の抽出、そしてデフォルト置換ルールを上書きして **欠落フォントを自分流に処理**する方法です。数行の C# で、レイアウトの微妙な変化の背後に潜むフォント問題を完全に可視化できます。

次のステップは？ `FontSettings.SetFontsFolder` で元フォントを文書に埋め込んでみるか、`FontSourceBase` を使ってデータベースからフォントをロードする方法を探ってみてください。また、`Document.BuiltInStyle` コレクションを調べて、スタイルレベルでのフォント変更がどのように伝播するかを実験してみるのも面白いでしょう。

Aspose.Words やフォント管理についてさらに質問がありますか？ コメントを残すか、公式 Aspose ドキュメントを参照するか、新しいプロジェクトを立ち上げて上記コードを試してみてください。コーディングを楽しみながら、文書が常に意図した通りに表示されることを願っています！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}