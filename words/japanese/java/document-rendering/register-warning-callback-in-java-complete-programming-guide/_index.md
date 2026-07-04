---
category: general
date: 2026-05-23
description: Javaで警告コールバックを登録し、欠損フォントを検出してフォント置換を処理します。完全な例でステップバイステップに学びましょう。
draft: false
keywords:
- register warning callback
- detect missing fonts
- Java font handling
- Aspose.Words warning callback
- font substitution detection
language: ja
og_description: Javaでフォントの欠落を検出するために警告コールバックを登録する。このチュートリアルでは、コード、解説、ベストプラクティスを含む完全なソリューションを示します。
og_title: Javaで警告コールバックを登録する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Register warning callback in Java to detect missing fonts and handle
    font substitutions. Learn step‑by‑step with a full example.
  headline: Register Warning Callback in Java – Complete Programming Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- FontSettings
- DocumentProcessing
title: Javaで警告コールバックを登録する – 完全プログラミングガイド
url: /ja/java/document-rendering/register-warning-callback-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで警告コールバックを登録する – 完全プログラミングガイド

カスタムフォントに依存する文書で、フォントが見つからない場合の警告を取得する方法が分からないことはありませんか？ あなただけではありません。文書がカスタム書体に依存していると、サイレントなフォント置換がレイアウトを崩すことがありますが、これを検出できる唯一の確実な方法は警告をリッスンすることです。このガイドでは、**警告コールバックを登録**し、**フォントが欠落していることを検出**する実用的な解決策を段階的に解説します。

実は、Aspose.Words for Java はフォント管理用のクリーンな API を提供していますが、多くの開発者が警告コールバックの設定を省略し、元の Word ファイルとは全く違う PDF を生成してしまいます。本チュートリアルを終える頃には、すぐに実行可能なスニペットを手に入れ、各行の意味を理解し、より複雑なシナリオへ拡張できるようになります。

## 学べること

この後のセクションでは以下をカバーします：

* `LoadOptions` を作成し、カスタムフォント処理を有効にする方法  
* `FONT_SUBSTITUTION` イベントを取得するための **警告コールバックの登録方法**  
* **欠落フォントを検出**し、デバッグに役立つ情報をログに出す方法  
* 今日すぐ IDE に貼り付けて実行できる、完全な Java サンプル

外部ライブラリは Aspose.Words だけで、コードは Java 8+ と Aspose.Words 23.9（以降）で動作します。既に `.docx` をロードするプロジェクトがある場合、数行追加するだけで済みます—大規模なリファクタリングは不要です。

## 前提条件

* Java Development Kit (JDK) 8 以上  
* Aspose.Words for Java（公式サイトからダウンロードまたは Maven 依存で追加）  
* 読み込む Word 文書が格納されたディレクトリへのアクセス権  
* Java ラムダまたは匿名クラスにある程度慣れていること（本稿では可読性のため匿名クラスを使用）

これらに心当たりがなくてもパニックになる必要はありません—各手順は平易な英語で説明され、コードコメントが不足分を補います。

---

## 手順 1: LoadOptions を作成しカスタムフォント処理を有効化

フォント関連の警告を受け取る前に、Aspose.Words に自前の `FontSettings` を使用させる `LoadOptions` インスタンスが必要です。`LoadOptions` は文書ローダーに渡す「設定バッグ」のようなものです。

```java
// Step 1: Create load options and enable custom font handling
LoadOptions loadOptions = new LoadOptions();               // Holds loading configuration
loadOptions.setFontSettings(new FontSettings());           // Attach a fresh FontSettings object
```

**重要ポイント:**  
`FontSettings` はライブラリがフォントに対して行うすべての操作（検索パス、置換ルール、そして警告コールバック）へのゲートウェイです。専用の `FontSettings` オブジェクトを作成することで、欠落フォントの扱いをデフォルトに任せず、完全にコントロールできます。

> **プロのコツ:** アプリケーションがすでに共有 `FontSettings`（例: PDF 変換用）を使用している場合は、ここでも再利用してパイプライン全体でフォント解決を一貫させましょう。

---

## 手順 2: 警告コールバックを登録して欠落フォントを検出

本チュートリアルの核心です。先ほど作成した `FontSettings` に **警告コールバックを登録**します。コールバックは文書ロード中に発生するすべての警告について `WarningInfo` オブジェクトを受け取ります。

```java
// Step 2: Register a warning callback to be notified of font substitutions
loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter only font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // This is where we **detect missing fonts**
            System.out.println("Substituted: " + info.getDescription());
        }
    }
});
```

**ロジックの説明:**

* `setWarningCallback` でカスタムリスナーを接続  
* `warning(WarningInfo info)` 内で `info.getWarningType()` をチェック  
* タイプが `WarningType.FONT_SUBSTITUTION` のとき、ライブラリは元のフォントが見つからず別のフォントに置換したことを通知  
* `info.getDescription()` には *“Font 'MyCustomFont' not found, substituted with 'Arial'.”* のような人間可読メッセージが格納  

この説明文を出力することで、ロード段階で **欠落フォントを即座に検出**し、ログに残したりアラートを出したり、場合によっては処理を中止することが可能です。

> **例外を捕捉すべきでない理由は？**  
> 欠落フォントは例外を投げることは稀で、代わりに警告として通知されます。コールバックが無ければこれらの警告は捨てられ、文書の視覚的忠実度が損なわれたままになります。

### オプション: ラムダを使用 (Java 8+)

より簡潔な構文が好みなら、同じコールバックをラムダで記述できます。

```java
loadOptions.getFontSettings().setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        System.out.println("Substituted: " + info.getDescription());
    }
});
```

どちらの方法でも同じ目的が達成できます—コードベースに合った方を選んでください。

---

## 手順 3: 設定済みオプションで文書をロード

コールバックを設定したら、最後に文書をロードします。`Document` コンストラクタはパスと先ほど用意した `LoadOptions` を受け取ります。

```java
// Step 3: Load the document using the configured options
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**内部で何が起きているか？**  
この呼び出しにより Aspose.Words は `.docx` を解析し、参照される各フォントを解決し、欠落フォントがあれば警告コールバックを発火します。すべてのフォントが揃っていればコンソール出力はありませんが、欠落があれば次のような行が表示されます。

```
Substituted: Font 'OpenSans-Regular' not found, substituted with 'Times New Roman'.
Substituted: Font 'CustomIconFont' not found, substituted with 'Arial'.
```

この出力が **警告コールバックが正しく登録され、欠落フォントが検出できている** 証拠です。

---

## 完全動作サンプル

以下は `Main.java` に貼り付けてそのまま実行できる、自己完結型 Java プログラムです。Aspose.Words の JAR がクラスパスに含まれていることを確認してください。

```java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions and enable custom font handling
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setFontSettings(new FontSettings());

            // 2️⃣ Register warning callback to detect missing fonts
            loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("Substituted: " + info.getDescription());
                    }
                }
            });

            // 3️⃣ Load the document using the configured options
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // Optional: Save as PDF to verify visual fidelity
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**期待される出力**（フォントが欠落している場合）:

```
Substituted: Font 'MyCustomFont' not found, substituted with 'Arial'.
Document loaded and saved successfully.
```

すべてのフォントが利用可能であれば、成功メッセージだけが表示されます。

---

## エッジケースとよくある落とし穴

| 状況 | 注意点 | 推奨対策 |
|-----------|-------------------|---------------|
| **複数のフォントが欠落** | コールバックが多数発火し、ログが散乱しやすい | メッセージを集約するか、後で分析できるファイルに書き出す |
| **パフォーマンスへの影響** | 大量のログ出力がバッチ処理を遅延させる可能性 | 警告の重要度でフィルタリングする、または本番環境ではコンソール出力を無効化 |
| **カスタムフォントディレクトリ** | `FontSettings` はデフォルトでシステムフォントのみを参照 | コールバック登録前に `fontSettings.setFontsFolder("path/to/custom/fonts", true);` を呼び出す |
| **サイレント置換** | 類似フォントと見なされる場合、警告が出ないことがある | `fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());` を設定し、置換ルールを細かく調整 |

これらのシナリオを事前に想定すれば、アプリケーションは堅牢に保たれ、ログも有用な情報源となります。

---

## ソリューションの拡張

**警告コールバックを登録**し **欠落フォントを検出**できるようになったので、次のような拡張が考えられます：

* 重要なフォントが欠落した場合に **ロードを中止**（コールバック内で例外をスロー）  
* 欠落フォント名を `Set<String>` に収集し、ロード完了後にサマリーレポートを作成  
* 監視システムと連携（例: Slack や Azure Monitor へアラート送信）  

これらすべては本稿で示したコールバックパターンを基に実装できます。

---

## 結論

本稿では、Java で **警告コールバックを登録**し、文書ロード時に **欠落フォントを検出**する完全な実装例を示しました。重要なポイントは次の通りです：

* カスタム `FontSettings` を持つ `LoadOptions` を作成  
* `FONT_SUBSTITUTION` 警告をフィルタリングする `IWarningCallback` を添付  
* それらのオプションで文書をロードし、欠落フォントイベントに即座に対応

この知識を活用すれば、ドキュメント処理パイプラインの信頼性を高め、視覚的忠実度を保証し、エンドユーザーへ明確な診断情報を提供できます。

次のステップに進みましょう—フォントフォルダーを追加したり、置換ポリシーを試したり、既存のロギングフレームワークにコールバックを組み込んだりしてみてください。管理するフォントライブラリが増えるほど、可能性は広がります。

Happy coding, and may your PDFs always render exactly as intended!

## 関連チュートリアル

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}