---
category: general
date: 2026-03-30
description: DOCX ファイルを読み込む際に警告を取得する方法 – 欠落フォントを検出し、フォント設定を構成し、C# でロードオプションを設定する方法を学びましょう。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: ja
og_description: DOCXファイルを読み込む際に警告を取得する方法 – 欠落フォントを検出し、C#でフォント設定を構成するステップバイステップガイド
og_title: 警告を取得する方法 – 欠損フォントのロードオプションを設定する
tags:
- Aspose.Words
- C#
- Font management
title: 警告を取得する方法 – 欠損フォントのロードオプションを設定する
url: /ja/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 警告の取得方法 – 欠落フォントのためのロードオプション設定

文書がインストールされていないフォントを使用しようとしたときに表示される **警告の取得方法** を考えたことはありますか？これは Word 処理ライブラリを使う多くの開発者が直面するシナリオで、特に **欠落フォントの検出** が PDF エクスポート パイプラインを壊す前に必要な場合に問題になります。

このチュートリアルでは、**フォント設定の構成**、**ロードオプションの設定**、そしてすべての置換警告をコンソールに出力する実用的で即実行可能なソリューションをご紹介します。最後まで読むと、アプリケーションを堅牢に保ち、ユーザーを満足させる形で **欠落フォントの処理** 方法が正確に分かります。

## 学べること

- ライブラリがフォント問題を黙って置き換えるのではなく、**ロードオプションを設定**して報告させる方法  
- 警告取得のための **フォント設定の構成** 手順  
- プログラムから **欠落フォントを検出**し、適切に対応する方法  
- 最新の Aspose.Words for .NET（執筆時点 v24.10）で動作する、完全なコピー＆ペースト可能な C# サンプル  
- ソリューションを拡張して警告をログに記録したり、カスタムフォントにフォールバックしたり、重要なフォントが欠けている場合に処理を中止するヒント  

> **前提条件:** Aspose.Words for .NET の NuGet パッケージがインストールされている必要があります（`Install-Package Aspose.Words`）。他の外部依存関係は不要です。

---

## Step 1: Import Namespaces and Prepare the Project

まず、必須の `using` ディレクティブを追加します。これは単なる定型文ではなく、`LoadOptions`、`FontSettings`、`Document` がどこにあるかコンパイラに伝えるために必要です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **プロのコツ:** .NET 6 以降を使用している場合は *global using* 文を有効にすると、各ファイルでこの行を繰り返す必要がなくなります。

---

## Step 2: Set Load Options and Enable Font‑Substitution Warnings

**警告の取得方法** の核心は `LoadOptions` オブジェクトです。新しい `FontSettings` インスタンスを作成し、`SubstitutionWarning` イベントハンドラを登録することで、要求されたフォントが見つからないたびにライブラリが警告を出すようになります。

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**重要なポイント:** イベントを購読しなければ、Aspose.Words はデフォルトフォントに黙ってフォールバックし、どの文字が置き換えられたか分かりません。`SubstitutionWarning` をリッスンすることで、完全な監査ログが取得でき、コンプライアンスが厳しい環境でも安心です。

---

## Step 3: Load the Document Using the Configured Options

警告ハンドラが設定されたので、先ほど作成した `loadOptions` を使って DOCX（またはサポートされている任意の形式）を読み込みます。`Document` コンストラクタがフォントチェックロジックを即座に実行します。

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

たとえば、マシンに **Arial** しかなく、ファイルが *“Comic Sans MS”* を参照している場合、次のような出力が得られます。

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

この行は、先ほど登録したハンドラのおかげでコンソールに直接出力されます。

---

## Step 4: Verify and React to Captured Warnings

警告を取得しただけでは不十分です。その後の処理を決める必要があります。以下は、警告をリストに保存して後で分析できるシンプルなパターンです。ファイルにログを書き込んだり、重要なフォントが欠けているときにインポートを中止したりするのに最適です。

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**エッジケースの取り扱い:**  
- **複数の欠落フォント:** リストには置換ごとに 1 件ずつエントリが入るので、イテレートして詳細レポートを作成できます。  
- **カスタムフォールバックフォント:** 独自のフォントファイルがある場合は、ロード前に `FontSettings` に追加します: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`。この場合、警告はシステムデフォルトではなくカスタムフォールバックが使用されたことを示します。  

---

## Step 5: Full Working Example (Copy‑Paste Ready)

すべてを統合した、すぐにコンパイルして実行できる自己完結型コンソール アプリの例です。

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**期待されるコンソール出力**（DOCX が欠落フォントを参照している場合）:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

たとえば “Times New Roman” のような *重要* フォントが欠けていると、代わりに中止メッセージが表示されます。

---

## Common Questions & Gotchas

| Question | Answer |
|----------|--------|
| **`SetFontsFolder` を呼び出さないと警告が取得できませんか？** | いいえ。警告イベントはデフォルトのシステムフォントでも機能します。`SetFontsFolder` は追加のフォールバックフォントを提供したいときだけ使用してください。 |
| **.NET Core / .NET 5+ でも動作しますか？** | 問題ありません。Aspose.Words 24.10 はすべての最新 .NET ランタイムをサポートしています。対象フレームワークに合わせて NuGet パッケージを選択してください。 |
| **警告をコンソールではなくファイルに記録したい場合は？** | `Console.WriteLine(msg);` を任意のロギング呼び出しに置き換えます。例: `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);` |
| **特定のフォントだけ警告を抑制できますか？** | はい。イベントハンドラ内でフィルタリングできます: `if (e.FontName == "SomeFont") return;`。これにより細かい制御が可能です。 |
| **欠落フォントをエラーとして扱う方法はありますか？** | ハンドラ内で条件を満たしたときに例外をスローするか、フラグを立てて `Document` の構築後に中止するロジックを追加してください（サンプル参照）。 |

---

## Conclusion

これで、欠落フォントを伴う文書を読み込む際に発生する **警告の取得方法** に関する、実践的で本番環境でも使えるパターンが手に入りました。**欠落フォントの検出**、**フォント設定の構成**、そして **ロードオプションの設定** を適切に行うことで、フォント置換イベントを完全に可視化でき、ログ記録、フォールバック、または処理中止のいずれかを自由に選択できます。

次のステップとして、このロジックを PDF 変換パイプラインに組み込んだり、カスタムフォールバックフォントを追加したり、警告リストを監視システムに送信したりしてください。小規模ユーティリティからエンタープライズ規模の文書処理サービスまで、スケールに応じて活用できます。

---

### Further Reading & Next Steps

- **FontSettings の詳細機能を探る** – カスタムフォントの埋め込み、フォールバック順序の制御、ライセンスに関する考慮点など。  
- **PDF 変換と組み合わせる** – 警告取得後に `doc.Save("output.pdf");` を呼び出し、PDF が期待通りのフォントを使用しているか確認します。  
- **テスト自動化** – 欠落フォントが既知の文書をロードし、警告リストに期待通りのメッセージが含まれることをアサートするユニットテストを作成します。  

問題が発生したり改善アイデアがあれば遠慮なくコメントしてください。Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}