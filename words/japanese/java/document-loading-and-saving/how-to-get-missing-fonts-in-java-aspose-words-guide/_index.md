---
category: general
date: 2026-02-15
description: Aspose.Words を使用して Java で Word 文書を読み込む際に、欠落しているフォントを取得する方法を学びます。警告コールバックとフォント置換の処理も含まれます。
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: ja
og_description: Aspose.Words を使用した Java で欠落フォントを取得する方法。警告コールバック、フォント置換の処理、ドキュメント処理のベストプラクティスをご紹介します。
og_title: Javaで欠損フォントを取得する方法 – Aspose.Words ガイド
tags:
- Aspose.Words
- Java
- Font Management
title: Javaで欠損フォントを取得する方法 – Aspose.Words ガイド
url: /ja/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで欠落フォントを取得する方法 – Aspose.Words ガイド

JavaでWord文書を開いたときに、奇妙なフォント置換が表示されて「**欠落フォントを取得する方法**」が気になったことはありませんか？ あなただけがこの驚きを経験したわけではありません。多くのエンタープライズアプリケーションでは、欠落フォントの警告がレポートや契約書、マーケティング資料の視覚的忠実度を損なうことがあります。

良いニュースは、Aspose.Words がコールバックを通じてこれらの警告を取得するシンプルな方法を提供してくれることです。これにより、ドキュメントがレンダリングされる前にログを記録したり、置換したり、ユーザーに通知したりできます。本チュートリアルでは、**欠落フォントを取得する方法**を示す完全な実行可能サンプルを順に解説し、コールバックが重要な理由と、実際のプロジェクトで役立ついくつかのエッジケースのテクニックを紹介します。

> **プロのコツ:** すでに Aspose.Words 22.12 以降を使用している場合、以下の API は追加設定なしでそのまま動作します。

---

![Aspose.Words の警告コールバックを使用して欠落フォントを取得する方法を示す図](how-to-get-missing-fonts-diagram.png "欠落フォント取得図")

## 本チュートリアルでカバーする内容

- **Java LoadOptions 警告コールバック** を設定してフォント置換警告を取得する。  
- 警告をフィルタリングし、欠落フォントに関するものだけを表示する。  
- 置換されたフォントと置換先フォントを示す、分かりやすい人間可読レポートを出力する。  
- 大規模文書の処理、警告レベルのカスタマイズ、ソリューションを大規模な処理パイプラインに統合するためのヒント。

本ガイドの最後までに、**欠落フォントを取得する方法**という質問に対して、すぐに実行できるコードスニペットと、背後にある仕組みの確かな理解を持って答えられるようになります。

### 前提条件

- Java 8 以上がインストールされていること。  
- Aspose.Words for Java ライブラリ（公式サイトからダウンロードするか、Maven/Gradle で追加）。  
- マシンにインストールされていないフォントを参照している Word 文書（例: `MissingFont.docx`）。

上記のいずれかが不足している場合は、今すぐライブラリを取得してください。Maven に追加するのは以下のように簡単です：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## 手順 1: フォント置換警告用コレクションの準備

ドキュメントをロードする前に、Aspose.Words が出す警告を保存する場所が必要です。`ArrayList<WarningInfo>` は順序を保持し、後で反復処理できるため便利です。

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*なぜ重要か:* 警告コールバックは単一ファイルで何十回も発火する可能性があります—欠落したグリフや埋め込み画像の問題などを想像してください。最初に収集しておくことで、ロード段階を高速に保ち、処理を制御されたループに遅らせることができます。

---

## 手順 2: 警告コールバック付き LoadOptions の設定

Aspose.Words は `IWarningCallback` を差し込むことができます。コールバック内で、Step 1 のリストにすべての `WarningInfo` を追加します。

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*説明:* `warning` メソッドはドキュメントロード中に **同期的に** 呼び出されます。`WarningInfo` を `fontWarnings` に単にプッシュするだけで、ロードを遅くする可能性のある重い I/O（ファイルへのログ出力など）を回避できます。この「収集→処理」パターンは、大量の警告を扱う際に推奨される方法です。

---

## 手順 3: 設定したオプションでドキュメントをロード

ここで実際に Word ファイルを読み込みます。文書にインストールされていないフォントが含まれている場合、Aspose.Words は自動的に置換し、先ほど設定した警告コールバックを発火させます。

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*内部で何が起きているか？* Aspose.Words はファイルのフォントテーブルを解析し、ホスト OS に存在するフォントと比較します。欠落エントリごとに `WarningSource.FontSubstitution` を持つ `WarningInfo` を作成します。このソースが欠落フォント警告を特定する鍵となります。

---

## 手順 4: フォント置換警告のみをフィルタリングして表示

ロード後、`fontWarnings` にはさまざまなメッセージ（例: 非推奨機能、画像問題）が混在している可能性があります。欠落フォントだけが対象なので、リストをループして簡潔なレポートを出力します。

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**サンプル出力**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*なぜ便利か:* `description` フィールドは文書が要求したフォントを示し、`additionalInfo` は Aspose.Words が実際に使用したフォントを示します。このデータを元に以下が可能です:

- ユーザーに欠落フォントのインストールを促す。  
- プログラムで代替フォントを文書に埋め込む (`doc.getFontInfos().add(...)`)。  
- コンプライアンス監査のためにイベントをログに記録する。

---

## エッジケースと一般的なバリエーションの処理

### 1. フォント以外の警告を抑制する

フォント関連のメッセージだけが必要な場合は、コールバックを絞り込むことができます:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

大量バッチを処理する際のメモリ使用量を削減します。

### 2. 警告の重大度を調整する

Aspose.Words は警告を `WarningType` で分類します。欠落フォントの場合は通常 `WarningType.FontSubstitution` が出ます。これらをエラーとして扱いたい（例: ロード中止）場合は、コールバック内で例外をスローします:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. ファイルではなくストリームで作業する

文書がデータベースや HTTP リクエストから来ることがあります。同じ手法は `InputStream` でも機能します:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

ロード後にストリームを必ずクローズしてください。

### 4. カスタムフォントフォルダーを使用する

共有ドライブに企業フォントのコレクションがある場合、Aspose.Words にそのフォルダーを指定します:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

これにより、ライブラリはシステムフォントにフォールバックする前にまずそこを検索し、欠落フォント警告の数が大幅に減少します。

---

## 完全な動作例

すべてをまとめると、以下のような単体で動作するクラスを任意の Java プロジェクトに組み込めます:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

このプログラムを実行すると、Aspose.Words が置換したすべてのフォントの一覧が整然と表示されます。余計なライブラリや隠されたマジックは不要で、純粋な Java と **Aspose.Words missing font** API の力だけです。

---

## 結論

Aspose.Words を使用して Java 環境で **欠落フォントを取得する方法** という根本的な質問に答えました。`LoadOptions` の警告コールバックを設定し、`WarningInfo` オブジェクトを収集し、`FontSubstitution` ソースでフィルタリングすることで、レンダリングが始まる前にフォント関連の問題を完全に把握できます。この手法は単一ファイルのユーティリティから大規模バッチプロセッサまでスケールし、カスタムフォントフォルダー、重大度の取り扱い、ストリーム入力にも柔軟に対応できます。

次のステップは？ 置換したフォントを直接文書に埋め込んで（`doc.getFontInfos().add(...)`）最終ファイルを真に自己完結させるか、警告レポートを監視ダッシュボードに統合してみてください。また、**document processing Java**、**Aspose.Words font substitution warning**、**Java LoadOptions warning callback** などの関連トピックを調べて専門知識を深めることもおすすめです。

コーディングを楽しんで、文書が常に期待通りのフォントでレンダリングされますように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}