---
category: general
date: 2026-05-04
description: Aspose.Words を使用して Java で Word 文書を作成し、カスタム LLM による文法チェックの方法を学びましょう。Java
  開発者向けのステップバイステップガイド。
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: ja
og_description: JavaでWord文書を作成し、カスタムLLMを使用して文法チェックする方法を確認しましょう。実行可能なコード付きの完全なJavaチュートリアルです。
og_title: カスタムLLM文法チェック付きのJavaでWord文書を作成
tags:
- Java
- Aspose.Words
- LLM
title: カスタムLLM文法チェックを使用したJavaでWord文書を作成
url: /ja/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# カスタム LLM 文法チェックで word document java を作成する

自分で校正も行う **create word document java** プロジェクトを作りたいと思ったことはありませんか？ あなた一人ではありません—多くの開発者が、複数のツールを使い分けずに洗練された *.docx* ファイルを出力する単一のパイプラインを求めています。このチュートリアルでは、Aspose.Words を使って **how to create docx** ファイルを作成し、ローカルでホストした LLM を接続し、最後に **how to check grammar** を自動で行う方法を順を追って説明します。最後までで、Word ドキュメントを書き込み、検証し、保存する自己完結型の Java プログラムが手に入り、**using custom LLM** エンドポイントを自分でコントロールできます。

## 必要なもの

本格的に始める前に、作業環境に以下が揃っていることを確認してください：

| 前提条件 | 重要な理由 |
|--------------|----------------|
| Java 17+（または最新の JDK） | 最新の言語機能とモジュールサポートの向上 |
| Aspose.Words for Java（最新バージョン） | プログラムから **create word document java** ファイルを作成できるライブラリ |
| ローカルでホストされた LLM サーバー（例: Ollama、LMStudio）で `http://localhost:11434/api/generate` をリッスン | 文法チェックを実行する **use custom llm** 手順に必要 |
| Maven または Gradle（例では Maven を使用） | 依存関係の管理を簡素化 |
| IDE またはテキストエディタ（IntelliJ IDEA、VS Code など） | コーディングとデバッグが容易になる |

これらの項目が馴染みがなくても心配しないでください—すべて無料、または学習目的に最適なコミュニティエディションが利用できます。

## ステップ 1 – Maven プロジェクトのセットアップ

**create word document java** プロジェクトを素早く作成するには、最小限の Maven `pom.xml` から始めます。このファイルは Aspose.Words ライブラリと、好みの HTTP クライアント（ここでは Apache HttpClient を使用）を取り込みます。

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Gradle を使用している場合、同じ依存関係は `build.gradle` の `implementation` に記述します。

`mvn clean install` を実行して jar を取得します。ビルドが成功したら、**creates word document java** ファイルを書く準備が整います。

## ステップ 2 – **Creates word document java** クラスを書く

以下は完全な実行可能なソースファイルです。全体の流れを示します：空白のドキュメントを初期化し、カスタム LLM エンドポイントを設定し、文法チェックを呼び出し、最後に結果を保存します。

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Why this works:**  
> * `Document` はメモリ上の *.docx* を表す Aspose.Words のコアクラスです。  
> * `AiEndpoint` は Aspose の AI モジュールにプロンプト送信先を指示します。`localhost:11434` を指定することで、クラウドサービスの代わりに **use custom llm** を利用します。  
> * `checkGrammar` と `AiModelType.CUSTOM` を使うと、ドキュメントのテキストを LLM に転送し、修正されたテキストを受け取り、基盤となる Word ノードを書き換えます。  
> * 最後に `save` を呼び出してファイルをディスクに書き出し、洗練された Word ファイルを得られます。

### 期待される出力

`mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` を実行すると、次のように表示されます：

```
Document saved to output/GrammarChecked.docx
```

生成された `GrammarChecked.docx` を Microsoft Word（または LibreOffice）で開きます。元の文 *“Ths sentence has a typo and a grammer error.”* は *“This sentence has a typo and a grammar error.”* に変わります—**how to check grammar** 手順が成功した証拠です。

## ステップ 3 – 異なるコンテンツで docx を作成する方法（オプション）

よりリッチなドキュメント（テーブル、画像、スタイル付きテキスト）を生成したい場合は、`DocumentBuilder` を引き続き使用してください。以下は見出しとテーブルを追加する簡単なコードスニペットです：

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

このコードはドキュメント作成ブロック（ステップ 2.1）と文法チェック呼び出し（ステップ 2.3）の間の任意の場所に挿入できます。LLM は全文を受け取るため、テーブルはそのままに自然言語部分だけを修正できます。

## ステップ 4 – エンドポイント問題への対処（カスタム LLM の安全な使用）

**using custom llm** エンドポイントを使用する際、いくつかの一般的な問題があります：

| 症状 | 考えられる原因 | 対策 |
|---------|--------------|-----|
| `Connection refused` エラー | LLM サーバーが起動していない、またはポートが間違っている | `ollama serve` を実行し、`curl` で `http://localhost:11434/api/generate` が動作することを確認してください。 |
| レスポンス JSON に `completion` フィールドがない | モデル名の不一致 | 設定したモデル（`llama3.1:8b`）がインストールされていることを確認してください（`ollama list`）。 |
| 文法チェックが元のテキストを変更せずに返す | プロンプトが LLM に認識されない | モデルのシステムプロンプトを調整してください。 |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}