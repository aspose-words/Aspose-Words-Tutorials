---
category: general
date: 2026-03-04
description: LLM を Document AI に設定し、AI を使用して DOCX のテキストを置換する方法 – 完全な Java コード付きステップバイステップガイド.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: ja
og_description: How to configure LLM for Document AI and replace text in DOCX using
  AI – complete guide with runnable Java code.
og_title: How to Configure LLM – Replace Text in DOCX with AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: LLMの設定方法 – AIでDOCXのテキストを置換する
url: /ja/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# LLM の設定方法 – AI で DOCX のテキストを置換する

LLM を **どのように設定**すれば Word ファイルを編集できるか、考えたことはありませんか？ あなただけではありません。Microsoft Word を開かずに `.docx` 内のフレーズをプログラムで置換する必要があると、多くの開発者が壁にぶつかります。良いニュースは、ローカル LLM と小さな Document AI ラッパーさえあれば、数行の Java で DOCX ファイルのテキストを入れ替えることができるということです。

このチュートリアルでは、LLM 接続の設定、DOCX の読み込み、**Document AI** を使って対象フレーズを置換するまでの全プロセスを順を追って解説します。最後には、Maven でも Gradle でも組み込める自己完結型の実行例が手に入ります。外部 API キーもクラウド料金も不要—`http://localhost:8080/v1` で待ち受けている自前のモデルだけで完結します。

> **Quick win:** すでにローカル LLM（Llama 3 や Mistral など）で OpenAI 互換エンドポイントを公開している場合、以下のコードはそのまま動作します。

---

![Diagram of how to configure LLM for Document AI](/images/configure-llm-diagram.png){: .center-image alt="LLM を Document AI 用に設定する方法の図"}

## 必要なもの

- **Java 17**（または最近の JDK）  
- OpenAI スタイルの `/v1` エンドポイントを公開している **ローカル LLM**（例: Ollama、LMStudio）  
- **Document AI Java ライブラリ**（Maven Central の `com.example:document-ai:1.2.0` を想定）  
- 既知のフォルダーに配置したサンプル DOCX ファイル（`input.docx`）  

これらが揃っていない場合は、すぐに Ollama を起動してください：

```bash
ollama serve &
ollama run llama3
```

これにより、リクエストを受け付けるサーバーが `http://localhost:8080/v1` で起動します。

---

## Document AI 用に LLM を設定する方法

最初に行うのは、`DocumentAi` クライアントにモデルの場所と使用するモデル名を伝えることです。これは多くのチュートリアルで省略されがちな **LLM の設定方法** のステップです。

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Why this matters:*  
`AiModelConfig` オブジェクトは HTTP の詳細を抽象化し、`DocumentAi` がコンテンツに集中できるようにします。ホスト型プロバイダーに切り替える場合は、`baseUrl` と `apiKey` だけを変更すればよく、コード本体はそのままです。

---

## DOCX ドキュメントの読み込みと準備

次に Word ファイルをメモリに取り込みます。`Document` クラスは内部で `.docx` と `.pdf` の両方を扱えますが、ここでは DOCX のみを対象とします。

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Pro tip:* デバッグ時は絶対パスを使用して「ファイルが見つからない」エラーを回避しましょう。確認できたら、可搬性のために相対パスに戻してください。

---

## AI を使って DOCX のテキストを置換する

いよいよチュートリアルの核心—**AI を使って DOCX のテキストを置換する方法**です。`replaceText` メソッドはドキュメント内容を LLM に送信し、置換を依頼して修正後のテキストを返します。

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*What’s happening behind the scenes?*  
`DocumentAi` は DOCX をプレーンテキストにシリアライズし、次のようなプロンプトを構築します：

> “以下のドキュメントで、‘old phrase’ のすべての出現箇所を ‘new phrase’ に置き換え、更新されたテキストだけを返してください。”

LLM がリクエストを処理し、修正されたコンテンツを返します。この手法はフレーズが複数のランや段落にまたがっている場合でも機能し、単純な文字列置換では見落としがちなケースをカバーします。

---

## 修正されたテキストの検証と出力

最後に、AI が修正したテキストをコンソールに出力します。実際のアプリでは新しい DOCX に書き戻すことが多いですが、ここではすぐに確認できるように出力だけにしています。

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Expected output**（元の DOCX に “This is the old phrase we want to change.” が含まれていると仮定）：

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

新しいフレーズが表示されたら、成功です—**Document AI を使ってフレーズを AI で置換する方法を習得しました**。

---

## 完全な動作例

すべてをまとめた、すぐに実行できる Java クラスを以下に示します。`src/main/java/com/example/ReplaceInDocx.java` にコピー＆ペーストして使用してください。

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### How to Run

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

プログラムを実行する前に LLM サーバーが起動していることを確認してください。起動していないと接続タイムアウトになります。

---

## エッジケースと一般的な落とし穴

| 状況 | 注意点 | 推奨修正 |
|-----------|-------------------|---------------|
| **フレーズが見つからない** | LLM が元のテキストを変更せずに返す。 | スペルと大文字小文字を再確認してください。ラッパーがサポートしていれば、プロンプトに `ignoreCase:true` を追加できます。 |
| **大きなドキュメント（>5 MB）** | プロンプトサイズがモデルのトークン上限を超える可能性があります。 | DOCX をセクションに分割し、個別に処理してから結果を結合してください。 |
| **ローカル LLM がエラーを返す** | モデル名が一致しないことが原因であることが多いです。 | LLM の UI（`ollama list`）でモデル名が `modelConfig.setModelName` と一致しているか確認してください。 |
| **Unicode 文字が文字化けする** | DOCX 読み取り時のエンコーディング問題です。 | Java ランタイムが UTF‑8 を使用していることを確認してください（JVM 引数に `-Dfile.encoding=UTF-8` を追加）。 |

---

## 次のステップ

AI で **DOCX のテキストを置換する方法** を習得したので、次は以下を検討してみてください：

- **Document AI の使い方** を、テーブル抽出やスタイル保持など、より複雑なタスクに活用する方法。  
- PDF で **AI によるフレーズ置換** を行うには、`Document` コンストラクタの引数を変更します。  
- **バッチ処理**：DOCX ファイルが入ったディレクトリをループし、同じ置換を適用する。  

これらはすべて同じ `AiModelConfig` と `DocumentAi` の基盤上に構築できるので、ゼロから始める必要はありません。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}