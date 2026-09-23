---
category: general
date: 2026-01-13
description: ローカルの LLM エンドポイントを使用して C# から LLM を呼び出す方法、Word ファイルの編集、すべての内容の削除、そして docx
  の保存を、1つのチュートリアルで学びましょう。
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: ja
og_description: ローカルモデルを使用してC#からLLMを呼び出し、Word文書を編集し、すべてのコンテンツを削除し、docxを効率的に保存する方法。
og_title: C#でLLMを呼び出す方法 – ステップバイステップチュートリアル
tags:
- Aspose.Words
- C#
- LLM Integration
title: C#でLLMを呼び出す方法 – ローカルモデルを使った完全ガイド
url: /ja/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で LLM を呼び出す方法 – ローカルモデルを使った完全ガイド

.NET アプリケーションから **LLM を呼び出す** 方法で、データをクラウドに送信せずに済む方法をご存知ですか？ 同じ悩みを抱える開発者は多いです。特に機密テキストを扱う場合、プロンプトやドキュメントをオンプレミスに保ちたいというニーズがあります。このチュートリアルでは、実際のシナリオとして、自己ホスト型 LLM エンドポイントを利用して Word 文書を書き換え、すべてのコンテンツを削除し、ファイルを編集し、最後に **docx を保存** する手順を解説します。

また **ローカル LLM の使用** 方法を紹介し、Aspose.Words `Document` から **すべてのコンテンツを削除** する正確なコード例を示し、Word ファイルをプログラムで編集する際のポイントを説明します。最終的に、Aspose.Words 7+ と任意の OpenAI 互換ローカルモデルで動作する、コピー＆ペースト可能なソリューションが手に入ります。

## 前提条件 – 作業を始める前に必要なもの

- **.NET 6+**（または従来の .NET Framework 4.7.2）
- **Aspose.Words for .NET** NuGet パッケージ（`Aspose.Words` と `Aspose.Words.AI`）
- OpenAI 互換の `/v1` エンドポイントを公開している **ローカル LLM**（例: `http://localhost:8000/v1` 上の GPT‑Neo サーバー）
- 任意のフォルダーに配置したサンプル `input.docx`
- Visual Studio、Rider、またはお好みのエディタ – ここではスクリーンショットに VS Code を使用

> **プロのコツ:** まだローカルモデルを持っていない場合は、GPT‑Neo 2.7B 用の無料 Docker イメージを試してみてください。1 分未満で起動し、ここで使用する API 契約と同じものを提供します。

## Step 1 – ローカル LLM エンドポイントの設定（How to Call LLM）

C# から **LLM を呼び出す** 最初のステップは、自己ホスト型サービスを指すクライアントオブジェクトを作成することです。Aspose.Words.AI には、HTTP 呼び出しを抽象化した `LocalLargeLanguageModel` ヘルパーが用意されています。

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Configure the self‑hosted LLM endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",   // your local server
    ModelName = "my-gpt-neo"                // name as registered in the server
};
```

> **重要ポイント:** エンドポイントを自分で設定することで、リクエストペイロード、認証、レイテンシを完全にコントロールできます。これが **LLM を呼び出す** 際に外部サービスに依存しない核心です。

## Step 2 – ソース Word 文書の読み込み（How to Edit Word）

次に、元の `.docx` を Aspose の `Document` に読み込みます。これは典型的な **Word を編集する** 手順で、ファイルがメモリ上にある状態でクエリ、変更、または完全に置き換えることが可能です。

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

ファイルが存在しない場合は `FileNotFoundException` がスローされるので、パスが正しいことを確認してください。アップロードなどで `Stream` から読み込むこともできます。

## Step 3 – ローカル LLM を使って改訂テキストを生成（How to Call LLM）

ここからが本番です。LLM に対して、テキスト全体をフォーマルなトーンで書き直すよう指示します。プロンプトは、短い指示文と `document.GetText()` で取得した生テキストを連結して作成します。

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **エッジケース:** ソース文書が非常に大きく（10 k トークン超）なると、モデルのコンテキスト上限に達する可能性があります。その場合は段落単位に分割し、各チャンクに対して `GenerateText` を呼び出してください。

## Step 4 – 既存コンテンツのすべてを削除（Remove All Content）

新しいテキストを挿入する前に、文書をクリアする必要があります。Aspose の `RemoveAllChildren()` は、セクション、段落、テーブルなどすべてを一括で削除します。これが Word ファイルから **すべてのコンテンツを削除** する標準的な方法です。

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **ヘッダーは残したい場合は？** `document.Sections.Clear()` を使用し、その後必要なセクションだけを再構築します。

## Step 5 – 改訂テキストの挿入（How to Edit Word）

クリーンな状態になったら、LLM が生成したテキストを書き戻します。`DocumentBuilder` は段落、テーブル、画像などを追加できる便利なラッパーです。ここでは文字列全体を単一の段落として書き込みます。

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

リッチな書式（太字、見出し）を付けたい場合は、LLM の出力に含まれる Markdown 記号を解析し、`builder.Font` 設定を適用してください。

## Step 6 – 更新された文書の保存（How to Save Docx）

最後に、変更を新しいファイルに永続化します。これで **docx を保存** する方法が示されました。

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

`Save` メソッドは拡張子からフォーマットを自動判別するため、1 行変更するだけで PDF、HTML、ODT へのエクスポートも可能です。

### 期待される結果

`output.docx` を開くと、元のコンテンツ全体が洗練されたフォーマルな文体に書き換えられているはずです。元のテーブル、ヘッダー、フッターは残っておらず、LLM が生成した新しいテキストだけが表示されます。

---

![Screenshot of output.docx opened in Word, showing formal rewritten text – how to call llm](/images/output-docx.png "how to call llm example")

*画像代替テキスト:* **how to call llm の例 – 書き換えられた Word 文書を表示**

## よくある質問とトラブルシューティング

### 1. 「LLM がエラーを返したらどうする？」

`GenerateText` メソッドは 2xx 以外のレスポンスで `HttpRequestException` をスローします。呼び出しを `try/catch` で囲み、`ex.Message` を確認してください。多くの場合、API キーヘッダーが欠如しているか、トークン上限を超えていることが原因です。

```csharp
try
{
    string revisedText = llm.GenerateText(prompt);
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"LLM call failed: {ex.Message}");
    // fallback logic, e.g., return the original text
}
```

### 2. 「文書全体を削除せずに特定の部分だけ編集したい」

もちろん可能です。`document.GetChildNodes(NodeType.Paragraph, true)` で段落を列挙し、必要な箇所だけ `Paragraph.Text` を置き換えます。この方法なら **Word を編集する** 作業を細かく制御しつつ、スタイルを保持できます。

### 3. 「元の書式を残したままにしたい」

書式を保持したい場合は、LLM の出力をプレーンテキストとして受け取り、テンプレートに合わせて `builder.Font.StyleIdentifier` を各段落に適用します。あるいは、LLM が HTML を出力できるなら `DocumentBuilder.InsertHtml()` を利用してください。

### 4. 「大きな文書はどう扱う？」

文書をセクション (`document.Sections`) に分割し、個別に処理します。これによりトークン上限を回避でき、メモリ使用量も抑えられます。

## パフォーマンス向上のヒント

- **`LocalLargeLanguageModel` インスタンスを再利用** すると、内部の `HttpClient` が接続を維持します。
- 同じプロンプトを頻繁に使用する場合は、**改訂テキストをキャッシュ** しておくと、ローカルハードウェアでも LLM 呼び出しコストを削減できます。
- マルチコア CPU とスレッドセーフな LLM クライアントがある場合は、`Parallel.ForEach` でセクション処理を並列化してください。

## 次のステップ – ワークフローの拡張

**LLM を呼び出す**、**ローカル LLM を使用する**、**すべてのコンテンツを削除する**、**Word を編集する**、**docx を保存する** 方法が分かったので、以下のような拡張を検討できます。

- **バッチ処理**: フォルダー内の `.docx` を一括で走査し、同じ書き換えロジックを適用。
- **カスタムプロンプト**: 要約、箇条書き、翻訳など目的に合わせた指示文を作成。
- **ASP.NET Core との統合**: ファイルアップロードを受け取り、LLM を実行し、編集済み文書を返す HTTP エンドポイントを公開。
- **高度なスタイリング**: LLM の Markdown 出力を解析し、`DocumentBuilder` で Word スタイルにマッピング。

これらの拡張は本ガイドで示したコアパターンに基づくため、最小限の手間で実装できます。

---

## 結論

本ガイドでは、自己ホスト型エンドポイントを利用した **C# からの LLM 呼び出し** 方法、**ローカル LLM の使用**、Word ファイルから **すべてのコンテンツを削除** する正しい手順、**Word をプログラムで編集** する方法、そして **docx を保存** する具体例を網羅しました。完成したサンプルは任意の .NET プロジェクトにそのまま組み込め、各ステップの「なぜ」を理解した上で自由に調整・拡張・デバッグが可能です。

ぜひ試してみて、プロンプトを変えて実験し、ローカル LLM に文書自動化の重荷を任せてみてください。問題が発生したらトラブルシューティングセクションが道しるべになります。コーディングを楽しみ、オンプレミス LLM の力を存分に活用しましょう！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}