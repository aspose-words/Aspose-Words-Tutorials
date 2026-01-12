---
category: general
date: 2026-01-11
description: Aspose.Words を使用して C# で破損したドキュメントを復元します。復元モードの設定方法、復元付きで docx を読み込む方法、エラー時にユーザーへ通知する方法を、簡単な手順で学びましょう。
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: ja
og_description: C#で回復モードを設定し、回復付きでDOCXを読み込み、エラー時にユーザーに通知して破損したドキュメントを復元する。完全なステップバイステップチュートリアル。
og_title: C#で破損したドキュメントを復元する – クイックガイド
tags:
- Aspose.Words
- C#
- Document Recovery
title: C#で破損した文書を復元 – リカバリーモードを設定し、ユーザーに促す
url: /ja/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で破損したドキュメントを復元する – 完全ガイド

Word では問題なく開けるのに、コード内で例外が発生する DOCX を開いたことはありませんか？おそらく **recover corrupted document** のシナリオに直面しています。良いニュースは、Aspose.Words がそれらの厄介なファイルの処理方法を細かく制御できることです—静かに修正するか、例外をスローするか、ユーザーにどうするか尋ねるかを選べます。

このチュートリアルでは、**recover corrupted document** ファイルを扱うために必要なすべてを解説します。ライブラリのインストールから **set recovery mode** オプションの選択、**load docx with recovery**、そして何か問題が起きたときに **prompt user on error** する方法まで。余計な説明は省き、任意の .NET プロジェクトにそのまま貼り付けて実行できる完全なサンプルを提供します。

> **クイックプレビュー:** 最終的に、破損の可能性がある `corrupt.docx` を読み込み、警告をログに記録し、復元に失敗した場合はユーザーに続行するかどうか尋ねるコンソールアプリが完成します。

---

## 必要なもの

- **.NET 6.0** 以降（コードは .NET Framework 4.6+ でも動作します）。  
- **Aspose.Words for .NET** – NuGet でインストール (`Install-Package Aspose.Words`)。  
- テスト用の **corrupt DOCX** ファイル（HEX エディタで破損させるか、拡張子を変更して意図的に壊すことができます）。  
- お好きな IDE（Visual Studio、Rider、あるいは VS Code でも可）。

> *プロチップ:* 元のファイルは必ずバックアップしておきましょう。復元処理はドキュメントの一部を書き換える可能性があり、良好な部分を失いたくはありません。

---

## Step 1 – Install Aspose.Words and Add Namespaces

まずは NuGet からライブラリを取得し、必要な名前空間をインポートします。

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

これだけで本ガイドの残りの手順に必要な準備は完了です。`Aspose.Words.Loading` 名前空間にある `LoadOptions` クラスが **set recovery mode** の鍵となります。

---

## Step 2 – Choose a Recovery Mode (Primary H2 with Keyword)

### Recover Corrupted Document – Setting the Right Recovery Mode

Aspose.Words には 3 つの復元動作が用意されています。

| Mode | What Happens | When to Use |
|------|--------------|------------|
| **PromptUser** | ダイアログを表示（または独自のプロンプトを実装）し、ファイルの修復を試みます。 | ユーザーが判断できるインタラクティブなツールに最適です。 |
| **Silent** | 自動的に修復を試み、UI を表示しません。 | バッチジョブやサービス向けに適しています。 |
| **ThrowException** | 処理を中止し、例外をスローします。 | 厳格なバリデーションが必要な場合に使用します。 |

以下は **set recovery mode** を `PromptUser` に設定する例です。サイレント処理にしたい場合は列挙子の値を入れ替えるだけです。

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **なぜ重要か:** 明示的に **set recovery mode** を指定することで、Aspose.Words に対してどれだけ積極的に復元すべきかを指示できます。デフォルトは `PromptUser` ですが、明示することで将来の保守者やコードをクロールする検索エンジンに対して意図がはっきり伝わります。

---

## Step 3 – Load the DOCX with Recovery

先ほど設定した `LoadOptions` を使って **load docx with recovery** を実行します。ファイルが破損している場合、モードに応じて修復または警告が発生します。

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

`Document` コンストラクタが実際の処理を行います。**PromptUser** モードではコンソールプロンプト（または `LoadOptions` のイベントにフックしたカスタム UI）が表示され、続行するかどうかを尋ねます。**Silent** モードでは自動的にベストを尽くして処理が進みます。

---

## Step 4 – Inspect Warnings and Prompt the User

Aspose.Words は検出した問題を `Warnings` コレクションに記録します。これを列挙してユーザーに次のアクションを選ばせましょう。

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

上記のスニペットはコンソール向けに **prompt user on error** を実装した例です。Windows Forms や WPF アプリの場合は `Console.ReadLine` を `MessageBox` やカスタムダイアログに置き換えてください。

---

## Step 5 – Work With the Recovered Document

ここまででドキュメントはメモリ上に復元されました。あとは内容を読み取ったり、クリーンなコピーとして保存したり、必要な操作を自由に行えます。

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

破損したファイルでプログラムを実行すると、以下のようなコンソール出力が得られます。

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

ファイルが実際には問題なければ「Document loaded without any warnings.」と表示され、クリーンコピーは元ファイルと同一になります。

---

## Full Working Example

以下が全体のプログラムです。新しいコンソールプロジェクトに貼り付けて **F5** キーで実行してください。

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

実行し、テスト用ファイルを意図的に破損させて復元の様子を確認しましょう。 🎉

---

## Edge Cases & Variations

| Scenario | What to Change | Why |
|----------|----------------|-----|
| **Batch processing** (no user interaction) | `RecoveryMode = RecoveryMode.Silent` に設定し、コンソールプロンプトを削除する。 | パイプラインを自動的に進めるため。 |
| **Strict validation** (fail fast) | `RecoveryMode.ThrowException` を使用し、ロード呼び出しを try/catch で囲んで例外をログに記録する。 | 部分的に修復されたファイルで作業しないことを保証。 |
| **Custom UI** (WinForms/WPF) | `LoadOptions.LoadingProgress` や `Document.LoadOptions` のイベントに登録してダイアログを表示する。 | コンソール以上のリッチなユーザー体験を提供。 |
| **Large documents** (memory constraints) | `LoadOptions.LoadFormat = LoadFormat.Docx` を指定し、`Document.SaveOptions` でストリーミング出力を検討する。 | OutOfMemory 例外を回避。 |

---

## Practical Tips (E‑E‑A‑T Signals)

- **必ずバックアップ** を取ってから復元を試みましょう。処理中にファイルの一部が上書きされる可能性があります。  
- **警告はファイルに記録** して後で分析できるようにしましょう。多くの場合、根本原因（欠落パーツ、XML の破損など）を示唆しています。  
- **複数の破損パターンでテスト** してください。ファイルを切り詰める、XML タグを壊す、ZIP 構造を変更するなど、各モードの挙動を確認します。  
- **Aspose.Words は定期的にアップデート** してください。新しいバージョンは復元アルゴリズムが改善され、警告タイプも増えます。  
- **復元後にバリデーション** を組み合わせましょう。`document.UpdateFields()` と `document.Save()` を実行して、ドキュメントが完全に機能することを確認します。

---

## Conclusion

これで **recover corrupted document** ファイルを C# で **set recovery mode**、**load docx with recovery**、そして **prompt user on error** とともに扱う方法がマスターできました。完全なサンプルはコンソールアプリ、サービス、UI プロジェクトのいずれでも動作するエンドツーエンドのフローを示しています。

次のステップは？コンソールのプロンプトを WinForms のモーダルダイアログに置き換えてみたり、バックグラウンドジョブ向けに **Silent** モードを試したり、ASP.NET のファイルアップロードエンドポイントに復元ロジックを組み込んで、ユーザーが破損した DOCX をアップロードした際に即座に修復版を返す仕組みを作ってみましょう。

Happy coding, and may your documents stay whole!  

---

![破損したドキュメントの復元例](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}