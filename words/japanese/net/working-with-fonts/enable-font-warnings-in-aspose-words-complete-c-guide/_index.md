---
category: general
date: 2026-04-01
description: Aspose.WordsでWord文書を読み込む際にフォント警告を有効にします。C# の LoadOptions と Font Settings
  を使用してフォント置換イベントを取得する方法を学びましょう。
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: ja
og_description: Aspose.WordsでWord文書を読み込む際にフォント警告を有効にします。このチュートリアルでは、C#でフォント置換イベントを取得する方法を示します。
og_title: Aspose.Wordsでフォント警告を有効にする – 完全なC#ガイド
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose.Wordsでフォント警告を有効にする – 完全なC#ガイド
url: /ja/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words でフォント警告を有効にする – 完全 C# ガイド

プログラムで Word ドキュメントを読み込んだときに、なぜ突然見た目が変わるのか疑問に思ったことはありませんか？ **Enable Font Warnings** を有効にすると、Aspose.Words が欠損フォントを代替フォントに置き換えた瞬間がすぐに分かります。このチュートリアルでは、置き換えを検出するだけでなく、なぜそれが起こるのかも説明する実践的な例を順に解説します。

必要な NuGet パッケージ、正確な `LoadOptions` の設定、そして置き換えられたフォントを示す整ったコンソール出力など、すぐに始められるために必要なすべてをカバーします。最後まで読むと、**C# ドキュメント処理** 用の堅牢で再利用可能なパターンが手に入り、どのバージョンの Aspose.Words でも動作します。

## 学べること

- `LoadOptions` インスタンスを作成し、フォント変更を追跡する方法。  
- `SubstitutionWarning` イベントの目的とそのフック方法。  
- コンソールに明確な警告を出力する、完全で実行可能なコードサンプル。  
- 標準フォントのみを含むドキュメントなど、エッジケースの処理に関するヒント。  

Aspose.Words の事前経験は不要です—C# と .NET の基本的な知識があれば十分です。

---

![欠損フォントが置き換えられたときのイベントフローを示すフォント警告図](placeholder-image.png "フォント警告図")

*Alt text: 欠損フォントが置き換えられたときのイベントフローを示すフォント警告図*

## Step 1: LoadOptions の設定とフォント警告の有効化

最初に必要なのは `LoadOptions` オブジェクトです。このコンテナは Aspose.Words に、読み込もうとしているファイルをどのように扱うかを指示します。新しい `FontSettings` インスタンスを割り当てることで、フォント関連のイベントへの道が開かれます。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**この重要性:**  
`FontSettings` の割り当てを省略すると、Aspose.Words は依然として欠損フォントを置き換えますが、通知は受け取れません。警告機構は `FontSettings` 内にあるため、初期化は私たちの目的にとって *重要* です。

> **Pro tip:** `SetFontsFolder` を使用して `FontSettings` をカスタムフォントフォルダーに指定することもできます。これにより、欠損フォントが実際に見つかるため、警告の数が減ります。

## Step 2: SubstitutionWarning イベントへのサブスクライブ (フォント置換)

`FontSettings` オブジェクトが存在するので、その `SubstitutionWarning` イベントにフックします。このイベントは Aspose.Words が要求されたフォントを別のものに置き換えるたびに **毎回** 発生します。

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**この重要性:**  
このリスナーがなければ、置換プロセスを把握できません。コンソール出力は迅速な監査トレイルを提供し、特に自動ビルド時やコンプライアンス重視の業界向けに PDF を生成する際に便利です。

> **Common question:** *警告を抑制したい場合はどうすればいいですか？*  
> ハンドラをデタッチするか、`FontSettings.SubstitutionWarning += null;` と設定すれば簡単に抑制できます。ただし、警告を保持しておく方が安全です。なぜなら、無音の置換はレイアウトの不具合を引き起こす可能性があるからです。

## Step 3: 設定したオプションでドキュメントをロード (C# ドキュメント処理)

警告システムの準備ができたら、ドキュメントのロードは簡単です。`LoadOptions` インスタンスを `Document` コンストラクタに渡すだけで、残りは Aspose.Words が処理します。

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**この重要性:**  
`LoadOptions` オブジェクトは、生のファイルと警告インフラストラクチャの橋渡しです。これを省略すると、ドキュメントは無音でロードされ、欠損フォントは痕跡なしに置き換えられます。

> **Edge case:** 一部のドキュメントは必要なフォントファイルを埋め込んでいます。その場合、Aspose.Words が埋め込みフォントを見つけるため警告は表示されません。上記のコードは依然として機能しますが、コンソール出力は空になります。

## Step 4: 出力の確認と一般的な落とし穴

コマンドプロンプトまたは IDE のデバッガからプログラムを実行します。ソースドキュメントに、マシンにインストールされていないフォント（またはカスタムフォントフォルダーに存在しないフォント）が含まれている場合、次のような行が表示されます：

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

何も出力されない場合は、以下のいずれかです：

1. すべてのフォントが見つかった、**または**  
2. `SubstitutionWarning` ハンドラが正しくアタッチされていない（Step 2 を再確認）。

### フォント置換が起こる理由

- **Missing system font:** OS に要求された書体が存在しません。  
- **Unsupported font format:** Aspose.Words は TrueType と OpenType を読み取れますが、すべての独自形式には対応していません。  
- **License restrictions:** 一部の商用フォントは埋め込みをブロックし、代替フォントを強制します。

*なぜ* を理解することで、欠損フォントをアプリに同梱すべきか、ドキュメントのスタイルを調整すべきかを判断できます。

## ボーナス: フォールバックフォントの制御

すべての欠損フォントを特定のファミリー（例: “Calibri”）にフォールバックさせたい場合、グローバル置換ルールを設定できます：

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

これでコンソールは依然として警告を出しますが、視覚的な結果はすべての欠損フォントで一貫します。

---

## まとめ

- **Enable Font Warnings** を、`FontSettings` を新規作成した `LoadOptions` で有効にする。  
- フォントが置き換えられるたびにリアルタイムで警告を受け取るために `SubstitutionWarning` イベントをフックする。  
- 設定したオプションでドキュメントをロードし、必要に応じて PDF に保存して視覚効果を確認する。  
- 置換が発生した理由を診断し、必要なら特定のフォールバックフォントを強制する。  

これで **Aspose.Words** のワークフローにサイレントなレイアウト変更を防ぐ安全ネットが追加されました。次は `DefaultFontName` などの **フォント設定** を調査したり、**ドキュメントレンダリング** オプションを掘り下げて PDF 出力を微調整したりすると良いでしょう。

---

### 次に試すことは？

- **他の FontSettings 機能を探る**: `SetFontsFolder`、`LoadFontSources`、`DefaultFontName`。  
- **警告をロギングフレームワークと組み合わせる**（Serilog、NLog など）ことで本番レベルの診断が可能に。  
- **さまざまなドキュメント形式で実験する**（`.doc`、`.rtf`、`.html`）と、各形式が欠損フォントをどのように処理するかを見る。  

質問や変わったシナリオがありますか？下にコメントを残してください。ハッピーコーディング！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}