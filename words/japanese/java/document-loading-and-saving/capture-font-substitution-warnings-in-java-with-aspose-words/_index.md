---
category: general
date: 2026-01-11
description: Aspose.Words for Java を使用してフォント置換警告を取得する方法を学びます。このステップバイステップのチュートリアルでは、LoadOptions
  と警告コールバックについても解説します。
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: ja
og_description: Aspose.Words for Javaでフォント置換の警告を取得します。このガイドに従ってLoadOptionsと警告コールバックを設定し、信頼性の高いドキュメント読み込みを実現してください。
og_title: Javaでフォント置換警告を取得する – 完全チュートリアル
tags:
- Aspose.Words
- Java
- Document Processing
title: Java と Aspose.Words でフォント置換警告を取得する – 完全ガイド
url: /ja/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォント置換警告の取得 – 完全な Java チュートリアル

Word 文書を開く際にフォントが欠損していると **フォント置換警告を取得** したことがありますか？PDF を生成したり、すべての書体がインストールされていないサーバーで印刷したりする場合、よくある頭痛の種です。朗報です！Aspose.Words for Java を使えば簡単に実現できます—`LoadOptions` オブジェクトを設定し、警告コールバックを組み込むだけです。このガイドでは、具体的な手順、重要性、警告が発生したときに期待できることを詳しく解説します。

また、**Aspose.Words フォント置換**、**Java 警告コールバック** の使用方法、**LoadOptions の使用ベストプラクティス** など関連トピックにも触れます。最後まで読めば、欠損フォントイベントをすべてログに記録する実行可能なスニペットが手に入り、下流の処理で予期せぬサプライズに悩まされることはなくなります。

## 前提条件

- Java 17（または最近の JDK）をインストールし、設定済み。
- クラスパスに Aspose.Words for Java 23.10（またはそれ以降）を配置。
- ローカルに存在しないフォントを参照している Word 文書（例: `DocWithMissingFont.docx`）。
- Java の try/catch ブロックの基本的な知識—特別なものは不要。

これらに心当たりがない場合は、少し止めて Maven Central からライブラリをインストールしてください:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

基礎が整ったので、コードに入りましょう。

## 手順 1: **フォント置換警告を取得** するための警告コールバックを設定

最初に必要なのは、欠損フォントに遭遇したときに Aspose.Words が呼び出すコールバックです。ここで **フォント置換警告を取得** します。コールバックは `IWarningCallback` インターフェイスを実装し、`WarningType` をチェックします。

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Why this matters:** コールバックがなければ、Aspose.Words は欠損フォントをデフォルトフォントに静かに置き換えてしまい、視覚的な出力が変わったことに気付くことはありません。警告を取得することで、ログに記録したり、アラートを出したり、重要なフォントが欠損している場合はロード自体を中止したりできます。

## 手順 2: **LoadOptions** を構成し、コールバックを登録

次に `LoadOptions` インスタンスを作成し、`FontWarningCallback` を添付します。この手順は **LoadOptions の使用** に不可欠で、すべての文書ロードが同じ警告フィルタを通過することを保証します。

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Tip:** 同じ `LoadOptions` オブジェクトを複数の文書で再利用できるため、ボイラープレートが数行削減でき、アプリケーション全体で一貫した **document loading warnings** の取り扱いが保証されます。

## 手順 3: 文書をロードして出力を確認

コールバックが設定されたら、Word ファイルを単にロードするだけです。文書がインストールされていないフォントを参照している場合、コールバックが発火し、コンソールに詳細が出力されます。

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### 期待されるコンソール出力

`DocWithMissingFont.docx` が欠損フォント *“Comic Sans MS”* を参照していると仮定すると、次のような出力が得られます:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

文書に **欠損フォントがない** 場合、コンソールには最終行だけが表示され、コールバックが誤検知していないことが確認できます。

## 手順 4: エッジケースと一般的な落とし穴の対処

### 複数の欠損フォント

文書が複数の利用できないフォントを使用している場合、コールバックはフォントごとに一度ずつ実行されます。各メッセージはそれぞれ `source` と `description` を持ちます。追加のコードは不要ですが、ロギングシステムが連続呼び出しに対応できるようにしておいてください。

### 警告の抑制

稀に特定の置換を無視したいケースがあります（例: 特定のフォールバックが許容できると分かっている場合）。その場合はコールバックロジックを拡張します:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### スレッド安全性

Aspose.Words の `LoadOptions` はデフォルトでスレッドセーフではありません。並列で文書をロードする場合は、スレッドごとに別々の `LoadOptions` インスタンスを作成するか、コールバックを同期化して競合状態を回避してください。

## 手順 5: 結果文書で置換されたフォントを検証

ロード後、置換が実際に行われたか確認したくなることがあります。API を使えばすべての Run を走査し、実際に使用されたフォント名を調べられます:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

このスニペットは各テキスト Run と最終フォントを出力します。自動化された PDF 変換パイプラインを構築する際の便利なサニティチェックです。

## 完全な動作例

すべてをまとめると、以下が完全な実行可能プログラムです:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

`FontSubstitutionInfo.java` として保存し、`javac` でコンパイル、`java FontSubstitutionInfo` で実行してください。警告メッセージ（存在すれば）と、Run の一覧および最終フォントが表示されます。

## ビジュアルエイド

![フォント置換警告を示すコンソール出力のスクリーンショット](/images/font-substitution-warning.png "フォント置換警告の例")

*Alt text:* **フォント置換警告** – 欠損フォントを含む文書をロードした後のコンソール出力。

## 結論

これで Aspose.Words for Java を使用した **フォント置換警告を取得** 方法が分かりました。`LoadOptions` オブジェクトを構成し、カスタム `IWarningCallback` を提供することで、文書の外観に静かに影響を与える可能性のある欠損フォントイベントを完全に可視化できます。この手法は **Aspose.Words フォント置換** の処理に直接組み込め、信頼性の高い **document loading warnings** を保証し、ビジネスルールに基づいてログ記録、アラート、またはロード中止の柔軟な制御が可能です。

### 次にやること

- 他の警告タイプ（例: `DEPRECATED_FEATURE`）に対する **Java warning callback** パターンを調査する。
- **PDF 変換** と組み合わせて、置換されたフォントがレイアウトを壊さないことを保証する。
- **LoadOptions** の使用法をさらに深掘りし、`Password`、`Encoding`、`ResourceLoadingCallback` を試して高度なシナリオに対応する。

コールバックを自由に調整し、警告をロギングフレームワークへ送る、あるいは重要なフォントが欠損している場合はカスタム例外をスローするなど、可能性は無限です。これでしっかりとした基盤ができましたので、ぜひ活用してください。

Happy coding, and may your documents always render just the way you expect!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}