---
category: general
date: 2026-03-25
description: Word文書を編集するカスタムAIモデルを作成 – テキストをよりフォーマルにしたり、段落テキストを置換したり、Aspose.Words
  AIを使用してWordの段落を書き換える方法を学びます。
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: ja
og_description: Word文書を編集するカスタムAIモデルを作成します。テキストをよりフォーマルにする方法、段落テキストの置換、そして Aspose.Words
  AI を使用して Word の段落を書き換える方法を学びましょう。
og_title: カスタムAIモデルの作成 – JavaでWord段落を編集
tags:
- Aspose.Words
- Java
- AI integration
title: カスタムAIモデルの作成 – JavaでWordの段落を編集
url: /ja/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# カスタム AI モデルの作成 – Java で Word の段落を編集する

Word ファイル内の段落を磨き上げる **create custom AI model** が必要だったことはありませんか？たとえば、すべてが少しカジュアルすぎる契約書のバッチがあり、コード一行でテキストをよりフォーマルにしたいと考えているかもしれません。良いニュースは、外部サービスや重量級 SDK は不要で、Aspose.Words for Java と OpenAI 互換エンドポイントさえあれば、まさにそれが実現できるということです。

このチュートリアルでは、**create custom AI model** を作成し、ローカル LLM サーバーに接続し、*replace paragraph text* をよりフォーマルなバージョンに置き換える手順をすべて解説します。最後まで実行すれば、**edit paragraph with AI** で Word の段落を書き換え、結果をディスクに保存する実行可能な Java プログラムが手に入ります。余計な説明は省き、すぐに自分のプロジェクトにコピーペーストできる実用的なソリューションだけをご提供します。

> **What you’ll need**  
> • Java 17 以上（コードは以前のバージョンでもコンパイルできますが、17 が最適です）  
> • Aspose.Words for Java 23.9（または最新リリース）  
> • `http://localhost:8000/v1` で待ち受けている OpenAI 互換 LLM サーバー（例: Ollama、LocalAI）  
> • 任意のフォルダーに配置した入力 Word ドキュメント（`input.docx`）  

OpenAI を直接呼び出す代わりに **custom model** を構築する理由は柔軟性です。エンドポイントを自分で管理でき、コードを変更せずにモデルを差し替えられ、API キーをソースリポジトリに残す必要もありません。それでは始めましょう。

---

## Create Custom AI Model – Setup and Configuration

まず、Aspose.Words に LLM の所在を伝える必要があります。`AiModelEndpoint` クラスは URL とオプションの API キーを保持します。ローカルサーバーを使用しているためキーは空文字列でも構いませんが、パラメータは必須です。

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** ホスト型モデル（例: Azure OpenAI）に切り替える場合は、URL とキーを変更するだけで済みます。他のコード変更は不要です。

---

## Load the Word Document

次に、ソースファイルをメモリに読み込みます。`Document` は `.docx`、`.doc`、`.rtf` など多数の形式を読み取れますが、ここでは `.docx` のみを対象とします。

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

`YOUR_DIRECTORY` が実在するフォルダーを指すようにしてください。そうでないと `FileNotFoundException` が発生します。実際のアプリではコマンドライン引数や設定ファイルからパスを取得することが一般的です。

---

## Initialize the Custom AI Model

`CUSTOM` タイプの `AiModel` を作成し、先ほど定義したエンドポイントを渡します。これにより、Aspose.Words はすべての AI 呼び出しを自前のサーバー経由で行うようになります。

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

内部では Aspose.Words が小さな HTTP クライアントを構築し、標準的な OpenAI のチャット/コンプリーションスキーマで LLM と通信します。そのためエンドポイントは *OpenAI‑compatible* である必要があります。

---

## Retrieve and Rewrite the First Paragraph

ここで実際に **make text more formal** を行います。最初の段落を取得し、その生テキストをプロンプトと共にモデルに送信し、編集済みのバージョンを受け取ります。

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

第2引数（`"Make it more formal"`）がモデルへの指示です。任意の指示に置き換え可能で、**replace paragraph text**、**summarize**、**translate** などが利用できます。メソッドはプレーン文字列を返すので、後でドキュメントに挿入します。

> **Why this works:** `editText` は `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }` のような JSON ペイロードを送信します。LLM は元の段落と指示を受け取り、改訂テキストで応答します。

---

## Replace the Original Paragraph Content

Word オブジェクトモデル内の **replace paragraph text** を実行します。既存の Run（テキストの低レベル要素）をすべてクリアし、AI が生成した文字列を含む新しい `Run` を挿入します。

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

`firstParagraph.setText()` を呼び出さないよう注意してください。このメソッドは書式情報をすべて削除してしまいます。`Run` を使用すれば、段落のスタイル（見出し、箇条書きなど）は保持したまま文字だけを入れ替えられます。

---

## Save the Edited Document

最後に、変更済みドキュメントをディスクに書き出します。元ファイルを上書きすることもできますが、ここでは新しいコピーを作成しています。

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

`output.docx` を開くと、最初の段落がかなりフォーマルになっているはずです。LLM が指示を完全に満たさなかった場合は、プロンプトを調整するか別バージョンのモデルを試してください。

---

## Full Working Example

以下が完全なプログラムです。`LlmDemo.java` に貼り付け、パスを調整したうえで `javac` + `java` で実行してください。

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** `output.docx` を開くと、元の段落が変換されているのが確認できます。たとえばカジュアルな文「We’ll get the thing done soon.」は「We shall complete the task promptly.」のように変わります。正確な表現は使用するモデルに依存します。

---

## Common Questions & Edge Cases

### What if my document has multiple sections?

上記コードは *first* セクションの *first* 段落だけを対象にしています。ファイル全体で **edit paragraph with AI** を行うには、`document.getSections()` をループし、各 `section.getBody().getParagraphs()` を走査してください。空段落はスキップしないと、LLM に空文字列が送られ何も返ってきません。

### How do I handle large paragraphs that exceed token limits?

多くの LLM は入力を約 4 000 トークンで制限します。段落が異常に長い場合は、`editText` を呼び出す前に小さなチャンクに分割してください。同じ `AiModel` インスタンスを再利用できますが、ローカルサーバーのレートリミットには注意が必要です。

### Can I use a different instruction, like “summarize” or “translate to French”?

もちろんです。`editText` の第2引数は自由形式です。要約したい場合は `"Summarize in one sentence"`、翻訳したい場合は `"Translate to French, keep the tone formal"` などと渡せば動作します。この柔軟性により、コードを変更せずにさまざまなシナリオで **replace paragraph text** が可能です。

### Does the model preserve paragraph styling (fonts, colors)?

`Paragraph` オブジェクト内の `Run` だけを置き換えているため、見出しレベルや箇条書き、インデントといった既存のスタイルはそのまま残ります。スタイル自体を変更したい場合は、置換後に `Paragraph.getParagraphFormat()` を操作してください。

### What if my LLM server requires HTTPS with a self‑signed certificate?

`AiModelEndpoint` は `https://` の URL を受け付けます。証明書が信頼されていない場合は、Java の SSL コンテキストを設定して自己署名証明書を信頼させるか、サーバー側で有効な証明書を使用してください。この設定は本チュートリアルの範囲外ですが、Java SSL ガイドに詳しく記載されています。

---

## Tips for Production‑Ready Integration

| Tip | Why it matters |
|-----|----------------|
| **Cache the endpoint** | 毎回 `AiModelEndpoint` を再生成するとオーバーヘッドが増加します。 |
| **Batch edits** | 多数の段落がある場合、単一リクエスト（例: JSON 配列）でまとめて送信するとレイテンシが低減します。 |
| **Validate LLM output** | 挿入前に返却された文字列が null または空でないか必ずチェックしてください。 |
| **Log prompts and responses** | デバッグや、法的文書を書き換える際のコンプライアンス確認に役立ちます。 |
| **Graceful fallback** | LLM がダウンした場合は、元の段落を使用するかシンプルなヒューリスティックで書き換えるようフォールバックしてください。 |

---

## Conclusion

本稿では Aspose.Words を使って **create custom AI model** を構築し、OpenAI 互換エンドポイントに接続して **edit paragraph with AI** によりテキストをよりフォーマルに書き換える方法を示しました。エンドポイントの定義、ドキュメントの読み込み、モデルの初期化、段落取得と書き換え、保存という 6 ステップを順に実行すれば、実用的な AI 補助編集ツールが完成します。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}