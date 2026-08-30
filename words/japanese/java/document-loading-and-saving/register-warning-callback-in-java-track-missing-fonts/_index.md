---
category: general
date: 2026-05-30
description: Javaで警告コールバックを登録し、欠落フォントを追跡し、Aspose.Wordsでドキュメントの読み込みをカスタマイズします。完全なステップバイステップのソリューションをご覧ください。
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: ja
og_description: Javaで警告コールバックを登録し、欠落フォントを追跡してドキュメントの読み込みをカスタマイズする。コードと解説付きの完全ガイド。
og_title: Javaで警告コールバックを登録 – 欠落フォントを追跡
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Javaで警告コールバックを登録 – 欠落フォントを追跡
url: /ja/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで警告コールバックを登録 – 欠落フォントを追跡

Word 文書を Aspose.Words for Java で読み込む際に **欠落フォントを追跡** したいと思ったことはありませんか？ 静かなフォント置換を見て「レイアウトがどうなったんだ？」と感じたことがあるかもしれません。良いニュースは、推測する必要がなくなったことです。 **警告コールバックを登録** することで、文書が読み込まれた瞬間にすべてのフォント置換イベントを捕捉でき、さらに **文書の読み込みをカスタマイズ** してパイプラインに合わせることができます。

このチュートリアルでは、コールバックの設定方法、その重要性、そして処理パイプラインをクリーンに保つ方法を実例を交えて解説します。最後まで読むと、欠落フォントの警告をすべて出力し、処理済みの文書を保存する実行可能な Java クラスが手に入ります。外部参照は不要、純粋な実行可能コードだけです。

> **得られるもの:**  
> • Aspose.Words を使用した完全な Java プログラム  
> • 各行のステップバイステップ解説  
> • 暗号化ファイルや大量バッチなどのエッジケース処理のヒント  
> • 任意の `.docx` ファイルで実行できる簡易サニティチェック  

## 前提条件

- **Java 17**（または最近の JDK）をインストールし、`JAVA_HOME` を設定済み。  
- **Aspose.Words for Java** の JAR をクラスパスに追加。最新バージョンは Maven Central リポジトリから取得できます：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- フォントがインストールされていない可能性のあるサンプル Word 文書（`input.docx`）。  
- お好みの IDE またはコマンドラインビルドツール（Maven/Gradle）。

以上です。余分なフォントやサービスは不要、純粋な Java と Aspose.Words だけです。

## なぜ警告コールバックを登録するのか？

**警告コールバック** を文書読み込みプロセスの監視カメラと考えてください。Aspose.Words が欠落したグリフに遭遇すると例外はスローせず、静かに代替フォントに置き換えます。この静かな置換は、特にブランドロゴが重要な PDF や請求書などでレイアウトを崩す原因となります。コールバックを登録すると次のことが可能になります。

1. **リアルタイムの洞察取得** – すべての `FONT_SUBSTITUTION` 警告が即座に通知されます。  
2. **ログやリアクション** – ファイルにログを書き出したり、アラートを発したり、プログラムでフォントを置き換えることも可能です。  
3. **クリーンな出力維持** – 欠落フォントが分かれば、公開前に元文書を修正できます。

要するに、コールバックは隠れた問題を可視化し、文書パイプラインの信頼性を大幅に向上させます。

## Step 1 – `LoadOptions` を作成して文書読み込みをカスタマイズ

最初に `LoadOptions` をインスタンス化します。このオブジェクトは、パスワード処理から **警告コールバック登録** 機能まで、読み込み時に必要なすべての調整へのゲートウェイです。

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

`new Document("file.docx")` だけではなぜだめなのか？ `LoadOptions` がなければ読み込みイベントにフックする機会を失います。`LoadOptions` は Aspose.Words が **文書読み込みをカスタマイズ** できる唯一の場所です。

## Step 2 – 欠落フォントを追跡する警告コールバックを登録

本題の主役です。`IWarningCallback` を実装した **警告コールバックを登録** します。`warning` メソッド内で `WarningType.FONT_SUBSTITUTION` をフィルタリングし、役立つメッセージを出力します。

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

注意すべき点は次のとおりです。

- **なぜ `IWarningCallback` か？** すべての警告タイプに対して Aspose.Words が使用するインターフェイスで、さまざまな問題に対する単一のエントリーポイントを提供します。  
- **フィルタリングは必須** – `if` チェックがなければ、画像欠落や非推奨機能などの警告も出てきてログが散らかります。  
- **スレッド安全性** – コールバックは文書を読み込むスレッド上で実行されるため、後で結果を集計したい場合でも共有構造体を安全に更新できます。

このスニペットは **警告コールバックを登録** し、以降は欠落フォントのイベントがすべて `stdout` に出力されます。これが **欠落フォントを追跡** するコア部分です。

## Step 3 – 設定した `LoadOptions` で文書を読み込む

コールバックが設定されたら、いよいよファイルを読み込みます。文書が存在しないフォントを参照している場合、文書オブジェクトが完全に構築される前にコールバックが発火します。

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

`YOUR_DIRECTORY` を実際のパスに置き換えてください。`Document` コンストラクタはファイルを読み込み、`loadOptions` にパスワードが設定されていれば適用し、欠落フォントごとに警告コールバックをトリガーします。出力例は次のとおりです。

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

この行が **欠落フォントを追跡** に成功したことを示しています。

## Step 4 – 文書の処理を続行（任意）

この段階で文書を自由に操作できます—テキスト置換、画像挿入、あるいは置換されたフォントをプログラムで差し替えることも可能です。コールバックで取得した問題フォントのリストを利用して、たとえば代替フォントを埋め込むことができます。

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

**欠落フォントの追跡** のみが目的であれば、このブロックはスキップして構いません。重要なのは、意思決定に必要な情報が手に入ったことです。

## Step 5 – 処理済み文書を保存

最後に文書を永続化します。元ファイルを上書きしたり、別の場所に保存したり、PDF にエクスポートしたりできます—以前に取得した警告データは失われません。

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

クラス全体を実行すると、欠落フォントごとのコンソール出力と、同じフォルダーに `processed.docx` という新しいファイルが生成されます。

## 完全動作サンプル

以下は IDE にコピペできる完全な Java クラスです。これまで説明したすべての要素に加えて、簡易的な `main` メソッドラッパーが含まれています。

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### 期待される出力

システムにインストールされていないフォントを使用した文書でプログラムを実行すると、次のような出力が得られます。

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

文書に **欠落フォントがない** 場合、コンソールは「Document saved successfully.」という最終行まで静かです—これは **警告コールバックを登録** した実装が正しく動作している証拠です。

## Pro Tips & Common Pitfalls

- **複数のコールバックは？** Aspose.Words は警告ハンドラを 1 つしか許可しません。ファイルとコンソールの両方にログを出したい場合は、警告を複数の宛先に転送する複合コールバックを実装してください。  
- **大量バッチ処理** – 数百ファイルを処理する際は、`LoadOptions` インスタンスを再利用するとオーバーヘッドを削減できます。  
- **暗号化文書** – 読み込む前に `LoadOptions` にパスワードを設定しないと、コールバックが発火する前に `IncorrectPasswordException` がスローされます。  
- **パフォーマンス** – コールバックは同期的に実行されます。リモートサービスへのログ送信が必要な場合は、メッセージをバッファリングし、ロード完了後にフラッシュして I/O ボトルネックを回避してください。  
- **フォントフォールバック** – システムフォントにフォールバックする前に、独自の `FontSource` コレクションを提供して Aspose.Words に認識させることも可能です。

## 結論

Java で **警告コールバックを登録** し、効果的に **欠落フォントを追跡**、さらに **文書読み込みをカスタマイズ** する方法を学びました。このソリューションは単一の `main` メソッドで完結し、見逃されがちなフォント置換を即座に可視化します。

次のステップは？ コールバックを拡張して警告を CSV ファイルに書き出す、あるいは欠落フォントを自動埋め込みするバッチプロセッサと組み合わせるなどです。また、`IMAGE_SUBSTITUTION` や `DEPRECATED_FEATURE` といった他の警告タイプも同様のパターンで扱えます。

Happy coding, and may your documents always render exactly as you intended!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")

## 次に学ぶべきこと

- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}