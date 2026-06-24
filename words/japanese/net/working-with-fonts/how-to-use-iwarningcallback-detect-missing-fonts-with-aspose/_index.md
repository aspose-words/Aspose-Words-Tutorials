---
category: general
date: 2026-06-24
description: Aspose.Words ドキュメントで欠落フォントを検出するために IWarningCallback を使用する方法。完全な実行可能サンプルとベストプラクティスを学びましょう。
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: ja
og_description: Aspose.Words で欠落フォントを検出するために IWarningCallback を使用する方法。完全で本番環境向けのソリューションを提供するステップバイステップガイドをご覧ください。
og_title: IWarningCallback の使用方法 – 欠落フォントの検出
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: IWarningCallback の使用方法 – Aspose.Words で欠落フォントを検出する
url: /ja/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で IWarningCallback を使用してフォント欠損を検出する方法

**IWarningCallback** の使い方は、Aspose.Words を使用して DOCX ファイル内の **欠損フォントを検出** する際に不可欠です。このガイドでは、フォント置換警告を捕捉するための IWarningCallback の使用方法、なぜ重要なのか、取得した後に何をすべきかを示す、完全なコピーペースト可能なサンプルを順を追って解説します。

カスタムフォントがインストールされていないために文字化けした経験がある方は、そのフラストレーションをご存知でしょう。このチュートリアルを終える頃には、問題をプログラム上で確実に検出し、ログに記録したり、フォールバックフォントを自動的に適用したりできるようになります。

## 学べること

- **IWarningCallback** の目的と使用すべきタイミング  
- **欠損フォント検出** イベントだけを抽出するカスタム警告コレクタの実装方法  
- **LoadOptions** にコレクタを組み込んで、すべてのドキュメント読み込みを監視する方法  
- 出力結果の確認方法と、複数フォント欠損やサイレント警告などのエッジケースへの対処  

### 前提条件

- .NET 6.0 以降（.NET Framework 4.6+ でも動作）  
- NuGet でインストールした Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- マシンに存在しないフォントを参照している DOCX ファイル（例: `DocumentWithMissingFont.docx`）  

追加のライブラリは不要です。すべて Aspose.Words 内に収まります。

---

## Aspose.Words で IWarningCallback を使用して欠損フォントを検出する方法

以下は **完全に実行可能なプログラム** です。新しいコンソールプロジェクトに貼り付け、ファイルパスを調整して実行してください。欠損フォントごとにコンソール出力が表示されます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### 期待される出力

`DocumentWithMissingFont.docx` がインストールされていないフォント *“MyFancyFont”* を参照している場合、次のような出力が得られます。

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

各行の先頭に **[Missing Font]** と付いているのは、我々の **IWarningCallback** 実装が生成したもので、**欠損フォントを検出** に成功したことを示しています。

---

## 手順 1: IWarningCallback インターフェイスの実装

なぜカスタムクラスが必要かというと、Aspose.Words は **警告** をさまざまな理由で発生させます（ファイル形式の問題、非推奨機能、そして本題のフォント置換）。`IWarningCallback` を実装すれば、警告が発生した瞬間にフックを受け取れます。`WarningType.FontSubstitution` をフィルタリングすることで、フォントが欠損しているシナリオだけを抽出できます。

**プロのコツ:** 診断目的で *すべて* の警告を取得したい場合は、`if` 文を削除して `info.Type` をそのままログに出力すれば OK です。

---

## 手順 2: LoadOptions にコールバックを組み込む

`LoadOptions` は、Aspose.Words に対して読み込むドキュメントの取り扱い方法を指示するゲートウェイです。`WarningCallback` にコレクタのインスタンスを設定すれば、ロード全体でコールバックが有効になります。同じ `LoadOptions` オブジェクトを複数のドキュメントで再利用できるため、バッチ処理パイプラインで便利です。

**よくある質問:** *LoadOptions を指定せずにドキュメントをロードしたらどうなるのか？*  
**回答:** Aspose.Words は内部で警告を発生させますが、コールバックが無い場合はサイレントに破棄され、**欠損フォントを検出** する機会を失います。

---

## 手順 3: ドキュメントをロードし、欠損フォント警告を捕捉

ファイルパスと `LoadOptions` を受け取る `Document` コンストラクタが実質的な処理を行います。ファイルが解析される間に、欠損フォントが検出されると `FontWarningCollector.Warning` メソッドが呼び出されます。コンソール出力でメカニズムが機能していることが確認できます。

**エッジケース:** 1 つのドキュメントが複数の欠損フォントを参照していることがあります。コールバックは欠損フォントごとに 1 回ずつ発火するため、複数行が出力され、包括的なレポート作成に最適です。

---

## なぜ IWarningCallback を手動のフォントチェックより使うべきか？

ドキュメントロード後に `Run.Font` プロパティを走査して手動でフォントを確認することも可能ですが、フォントが完全に存在しない場合はロード自体が失敗します。警告システムは **置換が行われる前** に作動し、実際に何が欠損しているかを正確に把握できます。

さらに、コールバックは **ロードパイプラインの一部として** 実行されるため、早期に処理を中断したり、オンザフライでフォントを差し替えたり、追加のドキュメントツリー走査なしで詳細な診断情報を記録したりできます。

---

## 複数欠損フォントをスマートに扱う

欠損フォントが多数想定される場合は、コレクタ内でそれらを集合にまとめることを検討してください。

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

ロード完了後に `MissingFonts` を走査し、たとえばデザインチーム向けに CSV ファイルへ書き出すといった活用が可能です。

---

## ボーナス: 警告をファイルへログ出力

デモではコンソール出力で十分ですが、実運用では永続ストアへログを残すのが一般的です。`Console.WriteLine` を次のように置き換えてみてください。

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

これで後から確認できる監査証跡が残り、コンプライアンス要件も満たせます。

---

## まとめ

本稿では **IWarningCallback の使い方** と **欠損フォントの検出** 方法を、コールバック実装から `LoadOptions` への組み込み、警告処理まで一連の流れで解説しました。この手法により、フォント関連の問題をリアルタイムで把握でき、ログ記録やフォント差し替え、ユーザーへのアラートをドキュメント描画前に実施できます。

次に試すべきこと:

- **フォールバックフォント:** 置換が発生した際にデフォルトフォントをプログラムで割り当てる  
- **バッチ処理:** フォルダ内の複数ドキュメントをループし、同一の `AggregatingFontCollector` を再利用する  
- **ユーザー通知:** コンソールではなく UI に欠損フォント警告を表示する  

ぜひ自分のプロジェクトで試してみてください。謎の文字化けはもう過去のもの、明確で実用的な診断情報が手に入ります。Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全な動作コードとステップバイステップの解説が含まれており、API の追加機能習得や代替実装アプローチの探求に役立ちます。

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}