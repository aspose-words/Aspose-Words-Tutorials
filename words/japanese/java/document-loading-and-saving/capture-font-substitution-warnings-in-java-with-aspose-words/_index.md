---
category: general
date: 2026-06-27
description: Aspose.Words を使用して Java でフォント置換警告を取得する方法を学びます。このステップバイステップのチュートリアルでは、警告コールバックと
  LoadOptions の使用方法もカバーしています。
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: ja
og_description: Aspose.Words を使用して Java でフォント置換の警告を取得します。このガイドに従って警告コールバックを設定し、LoadOptions
  を使用し、欠落フォントを処理してください。
og_title: Javaでフォント置換警告を取得する – Aspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Java と Aspose.Words でフォント置換警告を取得する完全ガイド
url: /ja/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでAspose.Wordsを使用したフォント置換警告の取得 – 完全ガイド

エキゾチックなフォントを使用したDOCXを読み込む際に、**フォント置換警告を取得**したことがありますか？ あなただけではありません。実務の多くのプロジェクト—たとえば自動レポートジェネレータやバッチドキュメント変換ツール—では、フォントが見つからないとサイレントに置換され、レイアウトの忠実度が損なわれることがあります。  

幸い、Aspose.Words にはこれらの警告を簡単に取得できる仕組みがあります。このチュートリアルでは **LoadOptions** の設定方法、**Aspose.Words の警告コールバック** の登録方法、そして *フォント置換* に関する通知をコンソールに出力する手順を解説します。最後まで読めば、フォントが置換された瞬間を正確に把握し、プログラムで適切に対処できるようになります。

> **得られるもの:** 完全に実行可能な Java スニペット、各要素が重要な理由の説明、カスタムフォントディレクトリなどのエッジケースへの対処法。

## 前提条件と必要なもの

始める前に以下を用意してください。

- Java 8 以降がインストール済み（コードは Java 11+ でも動作します）。
- 最新の Aspose.Words for Java JAR（公式サイトまたは Maven Central からダウンロード）。
- マシンにインストールされていないフォントを参照している DOCX ファイル（例: Aspose デモセットにある *font‑rich.docx*）。
- 好みの IDE（IntelliJ IDEA、Eclipse、あるいは Java 拡張機能付き VS Code）。

Aspose.Words 以外の外部ライブラリは不要で、サンプルはシンプルな `main` メソッドで動作します。

## 手順 1: LoadOptions の設定 – カスタムロードのエントリーポイント

`LoadOptions` は Aspose.Words の設定コンテナで、ライブラリに *どのように* ドキュメントを読み込むか指示します。デフォルトでは欠損フォントがサイレントに置換されますが、警告コールバックを設定すれば動作を変更できます。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**重要ポイント:** `LoadOptions` がなければドキュメントは静かにロードされ、欠損フォントの情報が得られません。インスタンスを作成することで警告システムへのフックを取得できます。

## 手順 2: フォント置換警告を取得する Warning Callback の定義

Aspose.Words は `IWarningCallback` インターフェイスを通じて警告イベントを通知します。インライン（または別クラス）で実装し、`WarningType.FONT_SUBSTITUTION` をフィルタリングします。

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**解説:**  
- `info.getWarningType()` は警告のカテゴリを返します。  
- `WarningType.FONT_SUBSTITUTION` が対象となる列挙値です。  
- `info.getDescription()` には人間が読めるメッセージが入ります。例: *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

この説明文を出力することで、**フォント置換警告をリアルタイムに取得**できます。

## 手順 3: 設定した LoadOptions でドキュメントをロード

コールバックが設定されたので、DOCX をロードします。パース中に自動的に警告コールバックが発火します。

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

`YOUR_DIRECTORY` を実際のテストファイルのパスに置き換えてください。`Document` コンストラクタが実行されると、欠損フォントが検出されるたびに先ほど定義したコールバックが呼び出され、コンソールに置換メッセージが表示されます。

## 手順 4: ロードしたドキュメントを検証（任意だが推奨）

ロード後にページ数やテキスト抽出などでドキュメントの整合性を確認したい場合があります。このステップは警告取得に必須ではありませんが、置換がレイアウトに与える影響を把握するのに役立ちます。

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

フォントが置換されるとレイアウトが若干ずれることがあります。ページ数の変化でその影響を検出できます。

## 手順 5: 高度な活用 – 置換フォントをプログラムで処理

単に警告をログに残すだけでなく、フォールバックフォントを埋め込んだりスタイルを調整したりしたいケースもあります。以下はそのための簡易パターンです。

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Aspose.Words に元フォントが格納されたフォルダを指定すれば、置換自体を防げます。フォルダが存在しない場合でも、警告コールバックがイベントを捕捉するのでフォールバック戦略を取れます。

## 完全動作サンプル

すべてを組み合わせた、すぐに実行できるプログラムは以下の通りです。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**期待されるコンソール出力**（欠損フォントが見つかった場合）:

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

すべてのフォントが揃っていればコールバックは何も出力せず、静かに終了します。これが期待通りの動作です。

## よくある落とし穴とプロのコツ

| 落とし穴 | 発生理由 | 対策 |
|---------|----------|------|
| **コールバックが呼び出されない** | `LoadOptions` にコールバックを設定し忘れた **または** `loadOptions` を渡さずに `Document` のデフォルトコンストラクタを使用した | 常に `loadOptions.setWarningCallback(...)` を呼び、`new Document(path, loadOptions)` オーバーロードを使用する |
| **警告が多すぎてログが埋まる** | 大規模文書で欠損フォントが多数あると置換ごとに警告が生成される | `info.getDescription()` で特定フォント名を絞り込む、あるいは警告をリストに集約して後で処理する |
| **置換フォントがレイアウトに影響** | フォールバックフォントのメトリック（サイズ、字間）が元と異なる | Step 5 のようにカスタムフォントフォルダを提供するか、ロード後にスタイルを調整する |
| **ヘッドレスサーバーで実行** | デフォルトのフォントフォールバックがサーバーにインストールされていないシステムフォントに依存している | 必要なフォントをアプリケーションに同梱し、`FontSettings` でそのフォルダを指すようにする |

## FAQ（よくある質問）

**Q: PDF や他の形式でも同様に動作しますか？**  
A: はい。警告コールバックはフォーマットに依存せず、Aspose.Words がロードできる任意のドキュメントタイプ（DOC、DOCX、RTF、HTML など）で発火します。表示される警告の種類が異なるだけです。

**Q: 画像解像度警告など、他の警告タイプも取得できますか？**  
A: もちろんです。`warning` メソッド内で `info.getWarningType()` をチェックし、`WarningType.IMAGE_RESOLUTION` などの列挙値に応じて処理を分岐させれば取得できます。

**Q: ドキュメントロード後に置換されたフォントの一覧が欲しい場合は？**  
A: コールバック内で `info.getDescription()` を `List<String>` に格納しておきます。ロード完了後にそのコレクションをログ出力したり、監視サービスへ送信したり、フォントダウンロード処理をトリガーしたりできます。

## 結論

Java で Aspose.Words を使用し、**フォント置換警告を取得**する方法、各構成要素の重要性、実務シナリオへの拡張方法が理解できたはずです。`LoadOptions`、`Aspose.Words 警告コールバック`、必要に応じた `FontSettings` を組み合わせることで、欠損フォントを完全に可視化し、ドキュメント変換パイプラインの信頼性を高められます。

次のステップに進みましょう。`System.out.println` を SLF4J などのロガーに置き換える、警告リストを UI に統合してバッチ変換前にユーザーへ通知する、あるいは **Aspose.Words 警告コールバック** を使って *未対応機能* や *高解像度画像* 警告にも対応してみてください。  

Happy coding, and may your PDFs never suffer from unexpected font swaps again! 

![フォント置換警告が取得されたコンソール出力のスクリーンショット](image-placeholder.png "フォント置換警告の取得")

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能をマスターしたり、独自の実装アプローチを探求したりするのに役立ちます。

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}