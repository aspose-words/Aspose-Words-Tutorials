---
category: general
date: 2026-04-04
description: Aspose.Words LoadOptions を使用して、警告の取得方法、欠落フォントの検出方法、置換イベントのログ記録方法を学びましょう。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: ja
og_description: Aspose.Words の LoadOptions を使用して C# で警告を取得し、欠落フォントを検出し、置換イベントをログに記録する方法。
og_title: C#で警告をキャプチャする方法 – 欠落フォントの検出と置換のログ記録
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: C#で警告を取得する方法 – 欠落フォントを検出し、置換をログに記録する
url: /ja/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で警告を取得する方法 – 欠落フォントの検出と置換のログ記録

Word 文書を読み込む際に、欠落フォントが原因で表示される **警告の取得方法** を知りたくありませんか？実際のプロジェクトでは、移行時にフォントが失われ、サイレントなフォールバックがレイアウトを壊すことがあります。朗報です！Aspose.Words では、これらの警告を簡単にリッスンし、欠落フォントを検出し、置換ごとにログを残すクリーンな方法が提供されています。

このチュートリアルでは、**警告の取得方法** を示す完全に実行可能なソリューションを順に解説し、**欠落フォントの検出** と **置換イベントのログ記録** を実演します。最後まで読むと、再利用可能な警告ハンドラ、完全に設定された `LoadOptions` オブジェクト、そして確認用のサンプルコンソール出力が手に入ります。

> **前提条件:** NuGet で Aspose.Words for .NET (v24.x 以降) をインストールし、基本的な C# 開発環境（Visual Studio 2022 または VS Code）を用意してください。

---

## ドキュメント読み込み時の警告取得方法

ソリューションの核心は `IWarningCallback` を実装したクラスです。Aspose.Words はドキュメント読み込み中に生成されるすべての警告に対して自動的にこのコールバックを呼び出します（フォント置換警告も含む）。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **この手順の目的**  
> `WarningType.FontSubstitution` でフィルタリングすることで、不要な警告（例: 非推奨機能）によるノイズを排除できます。これにより、関心のある「欠落フォント」だけにログを絞り込めます。

---

## Aspose.Words で欠落フォントを検出する

ドキュメントがインストールされていないフォントを参照すると、Aspose.Words は最も近いフォントに置換し、警告を発生させます。上記ハンドラが各置換を捕捉するため、**欠落フォントの検出** が可能になります。

この動作を確認するには、`LoadOptions` を設定しハンドラを接続します。

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **ヒント:** 後で処理したい場合は警告を蓄積したいのであれば、`Console.WriteLine` の代わりにメッセージを `List<string>` に追加するコードに置き換えてください。

---

## 置換イベントのログ記録方法

ログは警告出力を永続ストアに送るだけで簡単に実装できます。以下は各置換警告を `font-warnings.log` というテキストファイルに書き込むサンプルです。

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **ファイルにログを残す理由**  
> 永続的なログがあれば、複数回の実行にわたってフォント問題を監査したり、アラートを自動化したり、ビルドパイプラインのチェックにデータを流し込んだりできます。

---

## 完全動作サンプル

すべてを統合した、コピー＆ペーストで実行できるコンソールアプリケーションです。**警告の取得**, **欠落フォントの検出**, **置換のログ記録** を一度に実演します。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### 期待されるコンソール出力

`input.docx` がインストールされていないフォントを参照している場合、次のような出力が表示されます。

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

`FileLoggingWarningHandler` に切り替えると、同じ行がタイムスタンプ付きで `font-warnings.log` に出力されます。

![警告取得コンソール出力](image-placeholder.png)

---

## よくある質問とエッジケース

### すべての警告（フォント置換だけでなく）を取得したい場合は？

`if (info.Type == WarningType.FontSubstitution)` のチェックを削除してください。コールバックはすべての警告タイプ（`WarningType.DegradedDocument`, `WarningType.UnexpectedContent` など）を受け取ります。その後、`info.Type` に基づいて個別に処理を分岐させることができます。

### PDF でも同様に機能しますか？Word 文書だけですか？

`LoadOptions` と `IWarningCallback` は Aspose.Words の機能なので、Word 互換フォーマット（`.docx`, `.doc`, `.rtf`, `.html`）に適用されます。PDF の場合は Aspose.PDF の独自警告メカニズムを使用してください。

### 警告を記録せずに抑制したい場合は？

`LoadOptions.WarningCallback = null` と設定するか、コールバックを実装してもメソッド本体を空にしてください。ライブラリは置換をサイレントに実行します。

### スレッドセーフはどうですか？

コールバックはドキュメントを読み込んでいるスレッド上で呼び出されるため、特別な同期は不要です。ただし、ハンドラを並列ロードで共有する場合は、ログファイルなどの共有リソースに対してロックを掛けるか、Concurrent コレクションを使用してください。

---

## まとめ

Aspose.Words からの **警告取得** 方法を学び、**欠落フォントの検出** と **置換のログ記録** を実装しました。`IWarningCallback` のシンプルな実装を `LoadOptions` に組み込むだけで、フォント関連の問題をコードベースを汚さずにフル可視化できます。

次のステップは？ロガーを拡張してメール送信や Azure Monitor への統合、ビルドサーバー上での自動フォントインストールを試してみましょう。また、他の警告タイプ（例: `WarningType.DegradedDocument`）を調べれば、変換プロセスで失われた機能も検出できます。

フォント処理や Aspose.Words 全般についてさらに質問があれば、コメントを残すか Aspose フォーラムで新規スレッドを立ててください。コーディングを楽しんで、常に正しい書体で文書が表示されますように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}