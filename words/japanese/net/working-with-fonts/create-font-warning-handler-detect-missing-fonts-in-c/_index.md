---
category: general
date: 2026-02-12
description: Aspose.Words でフォントが欠如していることを検出し、欠如したフォントを追跡するためのフォント警告ハンドラを作成します。警告を効率的にログに記録する方法を学びましょう。
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: ja
og_description: C#でフォント警告ハンドラを作成し、欠落しているフォントを検出し、Aspose.Wordsがフォントを置き換える際の警告をログに記録する方法を学びます。
og_title: フォント警告ハンドラを作成 – 欠落フォントを検出
tags:
- Aspose.Words
- C#
- Document Processing
title: フォント警告ハンドラの作成 – C#で欠落フォントを検出
url: /ja/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォント警告ハンドラの作成 – C#で欠落フォントを検出する

期待しないフォントに置き換えられたことに気付かずに Word 文書が静かに失敗した経験はありませんか？ あなただけではありません。Aspose.Words がサーバー上に存在しないフォントを参照する DOCX を読み込むと、デフォルトフォントに静かにフォールバックし、レイアウトが微妙に崩れます。  

このチュートリアルでは、**欠落フォントを検出**し、**欠落フォントを追跡**し、**警告をログに記録**する方法を正確に示します。最終的に、すべてのフォント置換イベントをコンソール（または任意のロガー）に出力する再利用可能な警告ハンドラが手に入ります。ミステリーはなく、明確で実用的なコードだけです。

## 前提条件

- .NET 6.0 以上（API は .NET Framework 4.6+ でも同じです）
- Aspose.Words for .NET がインストール済み（`dotnet add package Aspose.Words`）
- マシンにインストールされていないフォントを参照している Word ファイル（例: `MissingFont.docx`）

これらがすでに揃っているなら、さっそく始めましょう。

## 手順 1: Warning コールバック付き LoadOptions を設定する  

**フォント警告ハンドラを作成**したいときに最初に行うことは、問題が発生したときに Aspose.Words がコールバックを発火するよう指示することです。`LoadOptions` がその設定コンテナになります。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**重要ポイント:**  
`LoadOptions` は `IWarningCallback` を差し込める唯一の場所です。これがなければ、Aspose.Words は内部で警告を記録しますが、あなたはそれを見ることができません。`FontWarningHandler` を割り当てることで、欠落フォントが置換されたときの挙動を完全に制御できます。

## 手順 2: FontWarningHandler クラスを実装する  

ここで実際に **フォント警告ハンドラを作成**します。クラスは `IWarningCallback` を実装し、Aspose.Words が発生させる各警告について `WarningInfo` オブジェクトを受け取ります。

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**解説:**  
- `info.Type` は警告のカテゴリを示します。欠落フォントを示す `WarningType.FontSubstitution` に注目します。  
- `info.Description` には *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* のような人間が読めるメッセージが入ります。  
- `Console.WriteLine` で **警告をログに記録**しています。実際のアプリでは `ILogger`、ファイルライター、テレメトリサービスなどに置き換えることができます。

> **プロのコツ:** 後でレポートするためにすべての欠落フォントを収集したい場合は、`Console.WriteLine` の代わりに `info.Description` を `List<string>` に格納してください。

## 手順 3: 設定した LoadOptions でドキュメントを読み込む  

コールバックが設定された状態でドキュメントを読み込むと、フォントが欠落しているたびにハンドラが自動的に呼び出されます。

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**期待される出力:**  
プログラムを実行すると、以下のような内容がコンソールに表示されます。

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

この行は、**欠落フォントを検出**し、リアルタイムで **欠落フォントを追跡**できていることを示しています。

## 手順 4: 異なるシナリオでハンドラが動作することを確認する  

ハンドラが DOCX のみで動作すると想定しがちですが、Aspose.Words は多数のフォーマットをサポートしています。埋め込みフォントを参照する PDF や、古い `.doc` ファイルを読み込んでみてください。同じコールバックがフォント解決パイプラインを通過するすべての形式で発火します。

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

PDF がインストールされていないフォントを参照していれば、同じコンソール出力が得られます。これにより、**フォント警告ハンドラの作成**ソリューションがフォーマットに依存しないことが実証されます。

## 手順 5: ハンドラを拡張 – ファイルへのログ出力  

コンソール出力はデモには便利ですが、本番コードでは通常ログファイルに書き込みます。以下は簡単な変更例です。

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

これでフォントが置換されるたびに、メッセージが `font-warnings.log` に追記されます。これにより **警告のログ方法** が満たされ、永続的な監査トレイルが得られます。

## 手順 6: すべてをまとめる – 完全実行可能サンプル  

以下はコンソールアプリにコピペできる完全プログラムです。欠けている部分はありません。ファイルパスだけご自身のドキュメントに置き換えてください。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**期待される結果:**  

- コンソールに各置換行が表示されます。  
- `font-warnings.log` にタイムスタンプ付きで全欠落フォントイベントが記録されます。  
- `output.pdf` が置換フォントで作成され、元のフォントが利用できなくても変換が成功します。

## よくある質問とエッジケース  

| 質問 | 回答 |
|------|------|
| *特定のフォントだけ無視したい場合は？* | `Warning` 内で `info.Description` をチェックし、対象フォント名であれば `return;` で早期抜けします。 |
| *埋め込みフォントでもハンドラは発火しますか？* | いいえ。埋め込みフォントは常にドキュメントに存在するため、置換警告は発生しません。 |
| *他の警告タイプ（例: 画像解像度の問題）も取得できますか？* | 可能です。`if (info.Type == WarningType.FontSubstitution)` ガードを削除するか、`WarningType.ImageResolution` 用の `if` ブロックを追加してください。 |
| *ハンドラはスレッドセーフですか？* | 示したデフォルト実装は同期なしでファイルに書き込みます。マルチスレッド環境では、ファイル書き込みをロックで保護するか、同時実行ロガーを使用してください。 |

## 次のステップ  

**欠落フォントの警告をログに記録**できるようになったので、以下のような拡張を検討してください。

- バッチインポート時に **欠落フォントを検出**し、サマリーレポートを生成する。  
- 複数ドキュメントにわたって **欠落フォントを追跡**し、特定のフォントが頻繁に出現したときにメール通知を送る。  
- 監視システム（例: Azure Application Insights）と **統合**し、時間経過によるフォント置換トレンドを可視化する。  

これらすべては、今回作成した `IWarningCallback` の基盤の上に構築できます。

---

*Happy coding! If you run into quirks—maybe a custom font folder or a network share—drop a comment below. The community (and I) are always happy to help you fine‑tune your font‑warning strategy.* 

![フォント警告ハンドラ作成例](image-placeholder.png "フォント警告ハンドラ作成例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}