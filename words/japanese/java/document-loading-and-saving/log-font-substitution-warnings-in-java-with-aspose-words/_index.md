---
category: general
date: 2026-06-17
description: Aspose.Words を使用した Java でフォント置換の警告をログに記録し、ドキュメント読み込み時に欠落フォントを検出して出力を一貫させます。
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: ja
og_description: Aspose.Words を使用して Java でフォント置換警告をログに記録しましょう。ドキュメントの読み込み時に欠落フォントの警告を取得し、PDF
  を完璧な状態に保つ方法を学びます。
og_title: Javaにおけるフォント置換警告のログ記録 – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Java と Aspose.Words におけるフォント置換警告のログ
url: /ja/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでフォント置換警告をログに記録する – 完全ガイド

サーバーにインストールされていないフォントがWord文書に取り込まれたときに、**フォント置換警告をログに記録**する方法を考えたことはありますか？ 静かに置き換えられる欠損フォントに頭を抱えているのはあなただけではありません。良いニュースは、Aspose.Words for Java が文書がロードされた瞬間にその置換を捕捉するクリーンな方法を提供してくれることです。

このチュートリアルでは、警告コールバックの登録方法、フォント置換アラートのフィルタリング方法、そしてそれらをコンソール（または好みのロガー）に書き出す方法を実例を交えて解説します。最後まで読むと、**Aspose.Words Java** を使用する任意の Java プロジェクトに貼り付け可能な再利用可能なスニペットが手に入ります。

## 学べること

- **LoadOptions** を設定して警告を取得する方法。
- **font substitution** イベントのみに反応する **IWarningCallback** の実装方法。
- 欠損フォントの監査トレイルを残しながら文書を安全にロードする方法。
- ソリューションをファイルベースのログや監視システムへ拡張するためのヒント。

### 前提条件

- Java 8 以上（コードは Java 11+ でも動作します）。
- Aspose.Words for Java ライブラリ（バージョン 23.10 以降を推奨）。
- インストールされていないフォントを参照しているサンプル `.docx`（例: `MissingFont.docx`）。

追加のフレームワークは不要です。純粋な Java と Aspose.JAR だけで動作します。

---

## Step 1: Configure LoadOptions for Aspose.Words Java

警告をインターセプトする前に、**LoadOptions** インスタンスが必要です。このオブジェクトは、Aspose.Words が受信ファイルを解析する際の動作を指示します。

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

この手順が重要な理由は何でしょうか？ `LoadOptions` オブジェクトが無いと、ライブラリは欠損フォントを黙って置換し、痕跡が残りません。明示的に作成することで、カスタム **warning callback** を設定し、関心のある情報だけをログに記録できるようになります。

> **Pro tip:** バッチで多数の文書をロードする場合は、`LoadOptions` インスタンスを再利用して不要なオブジェクト生成を避けましょう。

## Step 2: Implement a Warning Callback for Font Substitution

Aspose.Words には `IWarningCallback` インターフェイスが用意されています。これを実装することで、エンジンが `WarningInfo` を発生させたときの処理を自由に決められます。今回のケースでは `WarningType.FONT_SUBSTITUTION` のみを対象にします。

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

注意すべき点は以下の通りです：

1. **Filtering** – `if` 文でフォント置換以外の警告（レイアウト問題など）を除外し、ログをすっきり保ちます。
2. **Thread safety** – コールバックは文書をロードしたスレッド上で実行されるため、単純なコンソール出力なら追加の同期は不要です。共有ロガーに書き込む場合はスレッドセーフであることを確認してください。
3. **Extensibility** – ファイルに書き出したいですか？ `System.out.println` を `java.util.logging.Logger` やサードパーティ製ロギングフレームワークに置き換えるだけです。

## Step 3: Load the Document Using the Configured Options

コールバックが設定できたら、Word ファイルをロードします。Aspose.Words が文書を解析した瞬間に、欠損フォントがあれば上記で定義したコールバックが呼び出されます。

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

ソースファイルがインストールされていないフォントを参照している場合、以下のような出力が得られます：

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

この行が、探していた **log font substitution warnings** です。ここからユーザーへの通知やフォールバックスタイルシートへの切り替え、コンプライアンス用の記録保持など、自由に処理を続けられます。

## Step 4: Continue Normal Processing

ロード後は、`Document` オブジェクトは通常通り扱えます。セクションの検査、テキスト抽出、PDF 変換など自由に行ってください。警告のロギングはロード時に自動的に行われるため、追加のコードは不要です。

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

コンソールにはフォント置換警告（存在すれば）とセクション数の両方が表示され、文書が完全に機能していることが確認できます。

## Advanced Tips & Edge Cases

### Logging to a File Instead of the Console

永続的なログが必要な場合は、`System.out.println` を `FileWriter` に置き換えます：

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

本番コードでは `IOException` を適切にハンドリングすることを忘れないでください。

### Capturing Multiple Documents in a Loop

フォルダー内の多数の文書を処理する際は、同じコールバックを再利用できます：

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

コールバックは `loadOptions` に紐付いているため、各イテレーションでフォント置換イベントが自動的に記録されます。

### Dealing with Embedded Fonts

`LoadOptions` で埋め込みを有効にすれば、欠損フォントを文書に埋め込むことも可能です：

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

埋め込みを有効にしていても、警告コールバックは引き続き発火し、どのフォントが置換されたかを可視化できます。

## Full Working Example

以下は完全に動作するサンプルプログラムです。`FontSubstitutionDiagnostics.java` というクラスに貼り付け、ファイルパスを調整して実行してください。

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Expected output**（ソース文書が欠損フォントを参照している場合）：

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

コンソールと `font_substitution_log.txt` の両方に警告が記録され、信頼できる監査トレイルが得られます。

## Conclusion

ここでは Aspose.Words を使って Java で **フォント置換警告をログに記録**する方法を示しました。`LoadOptions` の設定、`IWarningCallback` の配線、そして文書のロードという手順で、見過ごされがちな欠損フォントイベントを完全に把握できます。今後は以下のように活用できます：

- 警告を中央ロギングサービスへ送信する。
- 品質管理パイプライン向けにアラートをトリガーする。
- PDF 変換やメールマージなど、他の **document loading** 戦略と組み合わせる。

ぜひ実験してみてください。コンソールロガーを SLF4J に置き換えたり、タイムスタンプを付与したり、監視ダッシュボードへプッシュしたりと、コアパターンは変わりません。これで Java ベースの文書ワークフローにおける堅牢なフォント処理の基盤が整いました。

何か独自の応用例がありますか？ Spring Boot やクラウドファンクションへの統合例など、ぜひコメントで共有してください。皆さんのコードがさらに豊かになることを願っています。ハッピーコーディング！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、代替実装アプローチを探求したりするのに役立ちます。

- [Java で Aspose.Words を使用したフォント置換警告の取得 – 完全ガイド](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Aspose.Words for Java のドキュメントオプションと設定の使用](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Aspose.Words でフォント置換警告を有効化 – 完全ガイド](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}