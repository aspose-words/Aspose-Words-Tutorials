---
category: general
date: 2026-04-04
description: Aspose.Words for Java を使用して Word 文書を読み込む際にフォント置換の警告を取得し、欠落しているフォントを自動的に検出します。ステップバイステップのガイドに従ってください。
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: ja
og_description: Aspose.Words for JavaでWord文書を読み込む際のフォント置換警告を取得し、簡単な手順で欠落フォントを検出します。
og_title: フォント置換警告を取得 – 欠落フォントを検出
tags:
- Aspose.Words
- Java
- Document Processing
title: フォント置換警告の取得 – 欠損フォントの検出
url: /ja/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォント置換警告の取得 – 欠落フォントを検出する

Word ファイルを開くときに **フォント置換警告を取得** したいが、重要なフォントが欠けていることに気付いたことはありませんか？ あなたは一人ではありません。多くのエンタープライズワークフローでは、欠落フォントが完璧にフォーマットされたレポートを文字化けさせ、開発者のほとんどが目にしない静かな警告だけが手がかりとなります。

良いニュースは、Aspose.Words for Java がロードプロセスにフックし、**欠落フォントを検出** できるようにしてくれることです。このチュートリアルでは、すべての置換警告をコンソールに直接出力する完全な実行可能サンプルを順を追って説明します。これにより、適切なフォントを埋め込むか、置き換えるか、ユーザーに通知するかを判断できます。

このガイドを読み終えると、以下ができるようになります。

* カスタム警告コールバック付きの `LoadOptions` オブジェクトを設定する方法
* コールバックをフィルタリングしてフォント置換イベントのみに反応させる方法
* 任意の `.docx` ファイルをロードし、警告を即座に確認する方法
* ソリューションを拡張して警告をログに記録したり、例外をスローしたり、欠落フォントを自動インストールしたりする方法

外部ドキュメントは不要です—数行の Java と Aspose.Words JAR だけで完結します。

## 前提条件

本題に入る前に、以下が揃っていることを確認してください。

* Java 8 以上がインストール済み（最新の LTS バージョンがベストです）。
* Aspose.Words for Java 23.11 以降 – Maven アーティファクトまたは Aspose のウェブサイトから入手できます。
* 開発マシンにインストールされていないフォント（例: “MyFancyFont”）を参照している Word 文書。  
* お好みの IDE またはテキストエディタ – ここでは IntelliJ IDEA を使用していますが、Eclipse や VS Code でも問題ありません。

これらに心当たりがない場合は、まずインストールしてから続行してください。残りのチュートリアルはそれらが準備できていることを前提としています。

---

## Aspose.Words を使用したフォント置換警告の取得

解決策の核は `LoadOptions` インスタンスです。`IWarningCallback` を割り当てることで、ロードフェーズ中にライブラリが発行するすべての警告をインターセプトできます。

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**動作の理由:**  
`LoadOptions` は Aspose.Words に対し、受け取るファイルの取り扱い方法を指示します。`IWarningCallback` インターフェイスは、*すべての* 警告に対して `WarningInfo` オブジェクトを受け取るフックです。`info.getWarningType()` をチェックして `SUBSTITUTED_FONT` 以外を除外します。`description` プロパティには “Font 'MyFancyFont' was substituted with 'Arial'” のような人間可読のメッセージが入ります。

### 期待されるコンソール出力

ソース文書がインストールされていないフォントを参照している場合、次のような出力が得られます。

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

文書がマシンに存在するフォントだけを使用している場合、コールバックは黙っており、最終的に “Document loaded successfully.” のみが表示されます。

---

## 文書内の欠落フォントを検出する

「置換警告は欠落フォントと同じか？」と疑問に思うかもしれません。ほとんどの場合、はい—Aspose.Words は欠落フォントをフォールバックフォントに置き換え、`SUBSTITUTED_FONT` として報告します。ただし、フォント自体は存在しても特定のスタイル（太字‑斜体、特定の OpenType 機能）が欠けているケースもあり、微妙な置換が発生します。

すべてのギャップを確実に捕捉するには、警告コールバックに加えてロード後の検査を組み合わせます。

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**プロのコツ:** 欠落フォントを参照しているランが残っている場合は、その場で置き換えることができます。

```java
font.setName("Arial"); // fallback
```

これにより、元の警告が抑制されていた場合でも、一貫したビジュアル結果が保証されます。

---

## よくある落とし穴と回避策

| 落とし穴 | 発生理由 | 対策 |
|---------|----------|------|
| **コールバック設定を忘れる** | `LoadOptions` のデフォルトは No‑Op コールバックで、警告が消えてしまう。 | `loadOptions.setWarningCallback(...)` をロード前に必ず呼び出す。 |
| **間違った警告タイプを使用** | `WarningType.SUBSTITUTED_FONT` だけが欠落フォントを示す列挙子。 | 正確に `WarningType.SUBSTITUTED_FONT` でフィルタリングする。他のタイプ（例: `UNKNOWN_FILE_FORMAT`）は無関係。 |
| **ファイルパスをハードコーディング** | ローカルでは動くが CI/CD パイプラインで失敗する。 | 相対パスを使用するか、コマンドライン引数でファイル位置を渡す。 |
| **Unicode フォントを無視** | 特定文字だけが欠落フォントの問題になることがある。 | サポート対象の全文字セットを含む文書でテストする。 |
| **ヘッドレスサーバーでフォント設定なしで実行** | サーバーにフォールバックフォントが無く、予期せぬ置換が起きる。 | サーバーに最小限の共通フォント（Arial、Times New Roman 等）をインストールする。 |

---

## ソリューションの拡張

**フォント置換警告を取得** できたので、次のような拡張が考えられます。

* **警告をファイルにログ出力** – `System.out.println` を SLF4J などのロガーに置き換える。
* **例外をスロー** – ビルドを失敗させたい自動化パイプラインで有用:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **欠落フォントを自動インストール** – 実行時に必要な TTF/OTF をダウンロードし、Java の `GraphicsEnvironment` に追加する。高度なシナリオですが実現可能です。

---

## 図 (任意)

![LoadOptions → WarningCallback → コンソール出力 を示すフォント置換警告のフローダイアグラム](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Aspose.Words が欠落フォント警告をカスタムコールバックにルーティングする様子を示すフォント置換警告のフローダイアグラム”。

---

## 結論

ここでは、Aspose.Words for Java で Word 文書をロードする際に **フォント置換警告を取得** し、**欠落フォントを検出** する方法を解説しました。`LoadOptions` オブジェクトを設定し、軽量な `IWarningCallback` を実装するだけで、フォントフォールバックプロセス全体を可視化でき、警告のログ記録、フォントの置換、ビルド失敗など柔軟に対応できます。

要点をまとめると、コールバックを設定し、`SUBSTITUTED_FONT` でフィルタリングし、文書をロードして、アプリケーションの要件に合わせて出力を処理するだけです。ここからはロギングフレームワークへの統合、CI チェック、あるいは自動フォントプロビジョニングへと拡張できます。

さらに踏み込むなら、次のことに挑戦してみてください。

* **フォントを埋め込む** – `doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` に `FontEmbeddingMode.EMBED_ALL` を指定。
* **PDF を生成** – フォント修正後に PDF に変換し、最終出力が期待通りになることを確認。
* **フォルダ全体をスキャン** – 複数文書の欠落フォントを検出し、サマリーレポートを作成。

以上です。コーディングを楽しんで、常に正しいフォントで文書が表示されますように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}