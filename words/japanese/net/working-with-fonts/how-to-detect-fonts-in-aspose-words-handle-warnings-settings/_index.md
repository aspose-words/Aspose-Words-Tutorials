---
category: general
date: 2026-01-03
description: Aspose.Wordsでフォントを検出し、Asposeフォント設定を使用して警告を処理する方法 – 開発者向けステップバイステップガイド
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: ja
og_description: Aspose.Wordsでフォントを検出し、Asposeのフォント設定で警告を構成する方法。数分でフルワークフローを学びましょう。
og_title: Aspose.Wordsでフォントを検出する方法 – 警告の処理
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Wordsでフォントを検出する方法 – 警告と設定の処理
url: /ja/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words でフォントを検出する方法 – 警告と設定の扱い方

本番環境に投入する前に **フォントを検出** したいと思ったことはありませんか？ あなただけではありません。フォントが欠けているとレイアウトが崩れ、適切な警告が出なければ壊れた PDF や DOCX を気付かずに出荷してしまうことがあります。  

このチュートリアルでは **Aspose.Words を使ってフォントを検出** する方法を解説し、 **警告の扱い方** を示し、 **Aspose のフォント設定** を調整して **警告を必要な形で構成** できるようにします。最後まで読むと、Aspose が実行したすべての置換を出力するスニペットが手に入り、独自プロジェクトへの適用方法も分かります。

## 前提条件

- .NET 6+（または .NET Framework 4.6+）。  
- NuGet でインストールした Aspose.Words for .NET（`Install-Package Aspose.Words`）。  
- 故意に欠損フォントを参照している Word ファイル（例：*DocumentWithMissingFonts.docx*）。  

上記が揃っていれば、さっそく始めましょう。

![フォント検出のスクリーンショット](https://example.com/detect-fonts.png "フォント検出の例出力")

## Aspose.Words でフォントを検出する手順

最初のステップは、フォント置換イベントに関心があることを Aspose.Words に伝えることです。これは **Aspose のフォント設定** を通じてカスタム警告コールバックを提供することで実現します。コールバックは置換ごとに `WarningInfo` オブジェクトを受け取り、実行時に **フォントを検出** できます。

### 手順 1: 警告コールバック クラスを作成

`IWarningCallback` インターフェイスを実装します。`Warning` メソッド内で `WarningType.FontSubstitution` をフィルタし、詳細をログに記録します。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **プロのコツ:** `info.Description` 文字列には、欠損フォント名と Aspose が選択した代替フォントの両方が含まれます。構造化レポートが必要な場合はここからパースできます。

### 手順 2: Aspose フォント設定で LoadOptions を構成

`LoadOptions` インスタンスを作成し、新しい `FontSettings` オブジェクトを添付、先ほど作ったハンドラを `WarningCallback` に設定します。これにより Aspose に **警告の構成方法** を指示できます。

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

プライベートフォント フォルダーがある場合は、次のように追加できます。

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

この行は **Aspose のフォント設定** の別の側面を示しています。置換を行う前に Aspose がフォントを検索する場所を正確に制御できます。

### 手順 3: ドキュメントをロードしてコールバックをトリガー

`loadOptions` を使って対象ドキュメントをロードします。Aspose がファイルを解析する際、欠損フォントが検出されるたびに警告ハンドラが呼び出され、**リアルタイムでフォントを検出** します。

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

プログラムを実行すると、以下のような出力が得られます。

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### 手順 4: （任意）警告を後で利用できるように収集

レポート用に置換データを保存したい場合は、ハンドラを修正してメッセージをリストに蓄積します。

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

後で `handler.Substitutions` を JSON ファイルに書き出したり、ロギングサービスへ送信したり、UI に表示したりできます。

### 手順 5: 結果をプログラム上で検証

CI ビルドなどで **置換が一切発生しなかった** ことをアサートしたいことがあります。簡単なチェックは次の通りです。

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

このスニペットは **警告の扱い方** を決定的に制御し、ビルドパイプライン全体に対するフルコントロールを提供します。

## FAQ とエッジケース

**特定の置換を無視したい場合は？**  
`Warning` 内で条件分岐を入れ、許容できるフォントに対しては何もせずに戻ります。

**すべての警告を抑制してブール結果だけ取得したい場合は？**  
`loadOptions.WarningCallback = null` とし、ロード後に `doc.FontInfo` を確認します（ただし詳細ログは失われます）。

**PDF 変換でも同様に機能しますか？**  
もちろんです。`doc.Save("out.pdf")` を呼び出す際にも同じ警告メカニズムが発火し、変換ステップ中のフォント置換がコールバックで捕捉されます。

**パフォーマンスへの影響は？**  
オーバーヘッドは最小です。欠損フォントごとに数回のメソッド呼び出しが増える程度です。大量バッチ処理の場合は結果をキャッシュすると良いでしょう。

## まとめ：本稿でカバーした内容

- カスタム `IWarningCallback` を実装して **フォントを検出** する方法。  
- `LoadOptions.WarningCallback` を通じて **警告を扱う** 方法。  
- **Aspose のフォント設定** を調整（カスタムフォントフォルダーの追加、警告の有効化/無効化）。  
- 即時コンソール出力と後日分析の両方に対応する **警告の構成** 方法。  

これらを組み合わせれば、Word ドキュメントを自信を持って処理でき、欠損フォントが確実にフラグ付けされ、環境間で出力の一貫性を保てます。

## 次のステップ

- `FontSettings.SubstitutionSettings` を調査し、欠損フォントごとに特定の代替フォントをマッピングするなど、より細かい制御を行う。  
- この手法と Aspose.PDF を組み合わせ、正確なタイポグラフィを保持した PDF を生成する。  
- CI/CD パイプラインに警告チェックを自動化し、フォント問題を含むリリースをブロックする。品質ゲートの一部として **警告を扱う** チームに最適です。

**Aspose のフォント設定** に関する質問や、より大規模なサービスへの統合支援が必要な場合は、下のコメント欄にご記入ください。 happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}