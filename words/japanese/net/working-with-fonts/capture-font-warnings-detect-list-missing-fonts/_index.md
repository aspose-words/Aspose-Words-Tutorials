---
category: general
date: 2025-12-31
description: Aspose.Words のフォント警告を取得して欠落フォントを検出し、.NET アプリで欠落フォントを一覧表示します。ステップバイステップの
  C# ソリューションをご紹介します。
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: ja
og_description: Aspose.Words でフォント警告を取得し、欠落しているフォントを検出して一覧表示します。コードとヒントを含む完全な C# ガイド。
og_title: フォント警告の取得 – 欠損フォントを検出・一覧表示
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: フォント警告の取得 – 欠落フォントを検出・一覧表示
url: /ja/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォント警告の取得 – 欠損フォントを検出・一覧化

Word 文書を読み込む際に **フォント警告を取得** したいが、欠損フォントの詳細をどのように取得すればよいか分からないことはありませんか？ 多くの実務プロジェクトで、欠損フォントがレイアウトの乱れを引き起こし、適切な警告がなければ原因不明のバグを追いかけることになります。

このチュートリアルでは、Aspose.Words for .NET を使用して **欠損フォントを検出** し、**欠損フォントを一覧化** する方法を紹介します。最後まで読むと、すべての置換警告を出力する C# スニペットが完成し、ログに記録したり、アラートを送ったり、フォントを自動的に置き換えることができるようになります。

---

## フォント警告を取得する重要性

Aspose.Words がサーバーにインストールされていないフォントを参照する DOCX を開くと、デフォルトでフォールバックフォントに静かに置換されます。文書は見た目上問題ないように見えますが、視覚的な忠実度が損なわれます――たとえば、企業ロゴが誤った書体で表示されるようなケースです。

これらの警告を取得することで次のことが可能になります。

* **ブランド一貫性の維持** – どのフォントが欠損しているか正確に把握できます。
* **自動修正** – 欠損フォントをプログラムで置換できます。
* **コンプライアンス監査** – 法務やデザインレビュー用のレポートを生成できます。

要するに、**フォント警告を取得** することは、サイレントなフォント置換に対する第一の防御策です。

---

## 欠損フォントを検出するための LoadOptions 設定

警告を表面化させる鍵は `LoadOptions.FontSubstitutionWarning` プロパティです。デフォルトは `None` で、Aspose.Words はメッセージを無視します。これを `All` に変更すると、すべての置換イベントが記録されます。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **プロのコツ:** カスタムフォントフォルダーが既にある場合は、文書を読み込む前に `FontSettings.SetFontsFolder("path")` で設定してください。これにより、システムディレクトリに存在しない **欠損フォント** を検出できます。

---

## 文書を読み込み、欠損フォントを一覧化

`LoadOptions` の準備ができたら、次は Word ファイルを読み込みます。コンストラクターにオプションオブジェクトを渡すことで、置換は文の `WarningInfoCollection` に記録されます。

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

利用できないフォントが参照されている場合、欠損フォントごとに `WarningInfo` エントリが生成されます。`WarningInfoCollection` を走査することで **欠損フォントを一覧化** できます。

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

典型的な出力例は次のとおりです。

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

各行はどのフォントが欠損していたかを正確に示し、**欠損フォント一覧** の要件を満たします。

---

## WarningInfoCollection の読み取りと解釈

`WarningInfoCollection` にはさまざまな警告タイプ（例: `DocumentStructure`、`ImageLoading`）が含まれます。フォント問題だけに絞り込むには `WarningType.FontSubstitution` でフィルタリングします。

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

なぜフィルタリングが必要かというと、大規模文書では画像破損や未対応機能に関する警告も多数発生するためです。コレクションを絞り込むことでノイズを排除し、**フォント警告取得** の出力をクリーンに保てます。

---

## 完全動作サンプル – フォント警告取得の実装例

以下は、任意の .NET コンソールプロジェクトに貼り付け可能な、完全かつ自己完結型のプログラムです。`LoadOptions` の設定から欠損フォントの整然とした一覧出力までのすべての手順を示しています。

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**期待されるコンソール出力**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

文書に欠損フォントが全くない場合は次のように表示されます。

```
All referenced fonts are available – no warnings captured.
```

---

## よくあるエッジケースと対処法

| 状況 | 発生理由 | 推奨対策 |
|-----------|----------------|-----------------|
| **埋め込み OpenType フォントを使用している文書** | Aspose.Words は埋め込みフォントを読み取れますが、ファイルが破損している場合は失敗します。 | まず Word で DOCX を確認し、必要に応じてフォントを再埋め込みしてください。 |
| **警告が大量に出る**（例: 200 件以上の欠損フォント） | レガシーシステムからの一括インポートで、広範なフォントパレットが参照されることが原因です。 | 警告をバッチ処理し、データベースに保存した上でフォントインストールスクリプトを実行します。 |
| **WarningInfoCollection が空** | 文書にすべてのフォントが揃っているか、`FontSubstitutionWarning` が `None` のままになっているかのどちらかです。 | `LoadOptions` の設定を再確認し、正しいファイルパスで読み込んでいるか確認してください。 |
| **カスタムフォントがネットワーク共有にある** | ネットワーク遅延によりフォント検索がタイムアウトすることがあります。 | `FontSettings` の `SetFontsFolder` でフォントを事前ロードし、`CacheFontData = true` を設定します。 |

これらのヒントにより、**欠損フォントの検出** を信頼性高く実施でき、複雑な環境でも対応可能です。

---

## 画像イラスト

![capture font warnings example](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*コンソール実行時に 2 つの欠損フォントが報告されているスクリーンショットです。*

---

## 次のステップ – 単なるレポート以上の活用

**フォント警告を取得** できたら、次は自動修正を検討しましょう。

1. **自動フォント置換** – `FontSettings.SubstitutionSettings` を変更して、欠損フォントを社内承認済みのフォールバックに置き換えます。  
2. **監視システムへのログ出力** – 警告メッセージを Serilog、ELK、Azure Application Insights などにパイプします。  
3. **ユーザー向けレポート** – デザイナーが確認できるよう、HTML または PDF のサマリを生成します。

これらの拡張はすべて、今回学んだ `LoadOptions` の設定、文書の読み込み、`WarningInfoCollection` の読み取りという基盤の上に構築されます。

---

## 結論

Aspose.Words で **フォント警告を取得** し、**欠損フォントを検出**、**欠損フォントを一覧化** する方法を学びました。数行の C# コードで実装でき、Aspose.Words 23.x 以降をサポートする任意の .NET バージョンで動作します。

意図的にアンインストールしたフォントを参照するサンプル DOCX で試してみてください。警告が即座に表示されます。その後、フォントをインストールするか、プログラムで置換するか、あるいは後でレビューするためにログに残すかを選択できます。

Happy coding, and may your documents always render with the right fonts!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}