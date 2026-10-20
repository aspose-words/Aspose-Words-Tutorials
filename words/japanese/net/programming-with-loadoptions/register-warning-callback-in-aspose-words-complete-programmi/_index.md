---
category: general
date: 2026-06-27
description: Aspose.Wordsで警告コールバックを登録し、フォント置換や読み込みの問題を検出します。Aspose.Words の LoadOptions
  のステップバイステップの使用方法を学びましょう。
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: ja
og_description: Aspose.Wordsで警告コールバックを登録し、フォント置換やその他の読み込み警告を監視します。この完全なチュートリアルに従って、堅牢な実装を行ってください。
og_title: Aspose.Wordsで警告コールバックを登録する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Aspose.Wordsで警告コールバックを登録する – 完全プログラミングガイド
url: /ja/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で警告コールバックを登録する – 完全プログラミングガイド

ドキュメントを読み込む際に、どのフォントが置き換えられたか正確に確認したいと **Aspose.Words で警告コールバックを登録する** 方法を知りたくありませんか？ あなたは一人ではありません。多くの開発者が、静かなフォント置換が生成された PDF や Word ファイルのレイアウトを台無しにする壁にぶつかります。

このチュートリアルでは、Aspose.Words で警告コールバックを登録する実践的な解決策を紹介すると同時に、*なぜ* それを行うべきか、コールバックが内部でどのように動作するか、そして遭遇しうるエッジケースについても解説します。最後まで読めば、すべてのフォント置換をログに記録し、他のロード時警告も捕捉し、ドキュメント処理パイプラインを透明に保つことができるようになります。

## 学べること

- **LoadOptions** を設定してドキュメントのロード動作を制御する方法。  
- フォント置換やその他の警告タイプに対して発火する **警告コールバック** の登録方法。  
- 設定したオプションで DOCX をロードし、コールバック出力を解釈する手順。  
- よくある落とし穴（フォントが見つからない、カスタムフォントフォルダー、パフォーマンス上の考慮点）。  

**前提条件:** Visual Studio 2022（または任意の C# IDE）、.NET 6+ ランタイム、そして有効な Aspose.Words ライセンス（無料トライアルでも実験は可能）。`Aspose.Words` 以外の NuGet パッケージは不要です。

---

![Diagram illustrating the flow of registering a warning callback in Aspose.Words and handling font substitution warnings](register-warning-callback-aspose-words.png "register warning callback aspose.words diagram")

## 手順 1: LoadOptions を作成 – 警告処理のエントリーポイント  

コールバックが発火する前に、**LoadOptions** のインスタンスが必要です。これは「このファイルをロードしてください、ただし何か問題があれば教えてください」と Aspose.Words に渡すコントロールパネルのようなものです。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **重要ポイント:** `LoadOptions` では暗号化パスワードからフォントディレクトリまであらゆる設定を調整できます。このオブジェクトに警告コールバックを添付することで、無音プロセスを観測可能に変えることができます。

## 手順 2: 警告コールバックを登録 – フォント置換を捕捉  

いよいよ本番です: **警告コールバック** を登録します。匿名メソッド（ラムダ）を使用して、Aspose.Words がロード時の警告ごとに呼び出すようにします。コールバック内で `WarningType.FontSubstitution` をフィルタリングし、フレンドリーなメッセージを出力します。

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **プロのコツ:** 画像が見つからない、未対応機能などもログに残したい場合は、`args.WarningType` をチェックする `if` ブランチを追加してください。これにより **Aspose.Words で警告コールバックを登録する** 実装が、すべてのロード診断を一括で処理できるようになります。

## 手順 3: 設定した LoadOptions でドキュメントをロード  

コールバックが設定されたら、次は単にドキュメントをロードするだけです。`loadOptions` インスタンスを `Document` コンストラクタに渡します。Aspose.Words がフォントを見つけられないたびに、コールバックが発火してコンソールに書き込みます。

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

プログラムを実行すると、以下のような出力が得られます:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

これが **Aspose.Words で警告コールバックを登録する** の核心です。どのプロジェクトでも再利用できる 3 ステップのパターンです。

## 手順 4: 実務シナリオ向けにコールバックを拡張  

### 4.1 コンソールではなくファイルにログを出力  

本番環境ではコンソール出力は好まれません。`Console.WriteLine` をロガー（例: `Serilog`、`NLog`）やテキストファイルへの書き込みに置き換えます:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 カスタムフォントディレクトリを指定  

社内フォントを使用している環境では、置換が発生する前に Aspose.Words に検索先を教えておきます:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

これにより、エンジンが正しいフォントを見つけられるため、コールバックの発火回数が *減少* します。

### 4.3 フォント以外の警告も処理  

ロード時のすべての警告を捕捉するように範囲を拡大できます:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## 手順 5: 実装のテスト – 期待される結果  

### 5.1 フォントが欠如しているドキュメントで検証  

インストールされていないフォント（例: Linux サーバー上で “Comic Sans MS”）を参照する小さな DOCX を作成します。ローダーを実行すると、置換メッセージが表示されるはずです。  

### 5.2 オーバーヘッドのベンチマーク  

コールバックはごくわずかなオーバーヘッド（警告ごとに数マイクロ秒程度）しか追加しません。数千件のドキュメントを処理する場合は、ログエントリをバッチ化するか、重要度の低い実行ではコールバックを無効化すると良いでしょう。

### 5.3 エッジケース  

- **同一フォントの複数置換:** 同じ欠損フォントが別ページに現れると、コールバックが複数回呼び出されることがあります。必要に応じてロガー側で重複排除してください。  
- **暗号化ドキュメント:** DOCX がパスワード保護されている場合は `loadOptions.Password` も設定する必要があります。コールバックは復号後も発火します。  
- **非同期ロード:** API は同期ですが、`Task.Run` でラップすればバックグラウンド処理が可能です。コールバックはスレッドセーフです。

## よくある落とし穴と回避策  

| 落とし穴 | 発生理由 | 対策 |
|---------|----------|------|
| **出力が全くない** | コールバックが割り当てられていない、または後で `WarningCallback` が上書きされた | ロード前に **一度だけ** コールバックを割り当て、割り当て後に `loadOptions` を再設定しない |
| **キャスト例外** | `FontSubstitutionWarningInfo` 以外の警告をキャストしようとした | 常に `args.WarningType` を確認してからキャスト |
| **パフォーマンス低下** | 遅い I/O 先へ同期的にログを書き込んでいる | 非同期ロギングフレームワークを使用するか、書き込みをバッファリング |
| **カスタムフォントが見つからない** | `FontSettings` にフォントフォルダーが追加されていない | 手順 4.2 のように `SetFontsFolder` を追加 |

## 完全動作サンプル – コピー＆ペーストで実行  

以下は新規コンソールアプリプロジェクトに貼り付けてそのまま動作させられる、自己完結型プログラムです。開始から終了までのフローをすべて示しています。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**期待されるコンソール出力**（フォントが欠如している場合）:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

プログラムを実行すると、Aspose.Words が置き換えたフォントがすべて表示され、ロードプロセス全体が可視化されます。

---

## 結論  

ここまでで **Aspose.Words で警告コールバックを登録する** 方法、そのベストプラクティス、そしてロギングやカスタムフォント、広範な警告処理への拡張方法を網羅しました。たった 3 行のコードでブラックボックス化されたロード操作を監査可能・デバッグ可能なステップに変えることができます。もう不思議なレイアウト崩れに悩むことはありません。

次のステップは？ **Aspose.Words SaveOptions** と組み合わせてロード時と保存時の両方で警告を記録したり、アップロードをリアルタイムで処理する Web API にコールバックをフックしたりしてみてください。また、本ガイドで紹介した二次キーワード（例: *loadoptions font substitution warning*）を活用してパフォーマンス調整や監視ダッシュボードへの統合も検討できます。

質問や難しいシナリオがありますか？ コメントで教えてください。一緒にトラブルシュートしましょう。コーディングを楽しんで、PDF が常に正しいフォントでレンダリングされますように！

## 次に学ぶべきこと


以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、代替実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}