---
category: general
date: 2026-05-04
description: WordからMarkdownへエクスポートする際の解像度設定方法。Markdownの画像解像度、数式のエクスポート方法、そしてJavaでWordをMarkdownとして保存する方法を学びましょう。
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: ja
og_description: WordからMarkdownへエクスポートする際の解像度設定方法。このガイドでは、Markdownの画像解像度、数式のエクスポート、WordをMarkdownとして保存する方法を紹介します。
og_title: Word を Markdown に保存するときに解像度を設定する方法
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Word を Markdown に保存するときに解像度を設定する方法
url: /ja/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word を Markdown として保存する際の解像度設定方法

Ever wondered **解像度の設定方法** for images that appear in a Markdown file generated from a Word document? You're not the only one. Many developers hit a snag when the default rasterized math images look blurry, especially on high‑DPI screens.  

In this tutorial we’ll walk through the exact steps to control *markdown image resolution* while also showing **equations のエクスポート方法** as LaTeX, and finally how to **save Word as markdown** using Aspose.Words for Java. By the end you’ll have a crisp, production‑ready Markdown file that renders equations cleanly and images at the quality you need.

## 前提条件

- Java 17（または最近の JDK）  
- Aspose.Words for Java 23.6 以上 – Maven Central から取得できます  
- OfficeMath オブジェクト（数式）やラスタ画像を含む Word 文書（`.docx`）  
- Maven/Gradle と IDE（IntelliJ IDEA、Eclipse、VS Code など）の基本的な知識

追加のライブラリは必要ありません。その他はすべて Aspose.Words が処理します。

---

## Markdown エクスポート時の解像度設定方法

> **Pro tip:** 選択した解像度は生成される画像のファイルサイズに直接影響します。ほとんどのウェブベースの Markdown ビューアにとって **300 dpi** がバランスの取れた値です。

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

`setImageResolution(int dpi)` 呼び出しは **解像度の設定方法** の核心です。これにより、Aspose.Words はフォールバック画像（例: 数式が純粋な LaTeX で表現できない場合）を指定した DPI でラスタライズします。この行を省略すると、ライブラリはデフォルトの 220 dpi にフォールバックし、Retina ディスプレイではぼやけて見える可能性があります。

### なぜ数式に LaTeX を使用するのか？

LaTeX（`OfficeMathExportMode.LATEX`）として数式をエクスポートすると、生成された Markdown には `$…$` または `$$…$$` で囲まれた生の LaTeX コードが含まれます。ほとんどの最新の Markdown レンダラ（GitHub、GitLab、MathJax を使用した MkDocs など）は、これらを鮮明でスケーラブルなベクターグラフィックとして描画します—解像度の心配は不要です。解像度設定が重要になるのは、**markdown image resolution** が必要なラスタフォールバック画像（埋め込みチャートや Markdown がネイティブにサポートしない画像）に対してだけです。

---

## Markdown 画像解像度を効果的に使用する方法

Word ファイルに通常の画像（例: スクリーンショット）を埋め込む必要がある場合、Aspose.Words が PNG に変換します。同じ `setImageResolution` メソッドが適用され、指定した DPI が PNG に引き継がれます。簡単なチェックリストを示します:

1. **ターゲットプラットフォームに合わせた DPI を選択** – レガシー Web では 72 dpi、標準ディスプレイでは 150 dpi、印刷品質の PDF では 300 dpi。  
2. **出力をテスト** – 生成された `.md` ファイルを好みのビューアで開き、ズームして鮮明さを確認。  
3. **ファイルサイズを考慮** – DPI が高いほど PNG が大きくなります。帯域幅が問題なら 200 dpi で試して比較してください。

---

## 数式を LaTeX としてエクスポートする方法

`saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` 行は、Aspose.Words にすべての OfficeMath オブジェクトを LaTeX に変換するよう指示します。これが推奨されるアプローチです。その理由は:

- **スケーラビリティ** – LaTeX はサイズに関係なく品質を失わずにレンダリングできます。  
- **編集可能性** – 後で Markdown ファイル内の LaTeX を直接調整できます。  
- **互換性** – ほとんどの静的サイトジェネレータやドキュメントツールはすでに LaTeX レンダリングをサポートしています。

古い画像ベースのフォールバックが必要な場合は、単に `OfficeMathExportMode.IMAGE` に切り替えてください。その場合、設定した解像度はさらに重要になります。

---

## Word を Markdown として保存 – 完全なエンドツーエンド例

以下は、依存関係の宣言から実行までの全フローを示す、完全で実行可能な Maven プロジェクトのスニペットです。

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**期待される結果:** `MathExport.md` には各数式の LaTeX ブロックが含まれ、埋め込み画像は DPI が 300 の PNG リンクとして表示されます。MathJax をサポートする Markdown ビューア（例: Markdown Preview Enhanced 拡張機能付き VS Code）でファイルを開くと、数式も画像も完璧に鮮明に表示されます。

---

## よくある質問とエッジケース

### 特定の画像だけ別の DPI が必要な場合は？

Aspose.Words は `setImageResolution` により DPI をグローバルに適用します。画像ごとに異なる DPI を設定したい場合は、生成された Markdown を後処理し、PNG ファイルを高解像度版に差し替えて画像リンクを手動で調整する必要があります。理想的ではありませんが、少数の特別なケースでは実行可能です。

### Linux/macOS でも動作しますか？

もちろんです。このライブラリは純粋な Java なので、JDK が動作する環境ならどこでも同じコードが実行できます。ファイルパスはスラッシュ（/）を使用するか、`Paths.get(...)` を使ってプラットフォームに依存しない処理を行ってください。

### SVG 出力はどうですか？

チャートのベクター画像が好みの場合は、`saveOptions.setExportImagesAsSvg(true);` を設定できます。SVG は DPI を無視するため、**markdown image resolution** の問題はなくなります。ただし、すべての Markdown レンダラが SVG をうまく扱えるわけではないので、まず対象プラットフォームでテストしてください。

### 生成された Markdown を静的サイトジェネレータに埋め込めますか？

はい。出力は標準的な Markdown 構文と LaTeX デリミタを含む純粋な `.md` ファイルです。ほとんどのジェネレータ（Jekyll、Hugo、MkDocs）はそのまま受け入れます。サイト設定で MathJax または KaTeX を有効にすることを忘れないでください。

---

## 結論

本稿では、画像を **解像度の設定方法**（**Word を markdown として保存**）について説明し、**markdown image resolution** の微妙な点を検討し、**equations のエクスポート方法** を LaTeX で示し、完全な Java 実装を紹介しました。`setImageResolution` を調整し、適切な `OfficeMathExportMode` を選択することで、視覚的な忠実度とファイルサイズの両方を正確にコントロールできます。

次のステップに進む準備はできましたか？この手法を Aspose.PDF と組み合わせて同じ Word ソースを直接 PDF に変換したり、`setExportImagesAsSvg(true)` を試してベクトルベースのグラフィックを生成したりしてみてください。ここで学んだテクニックは、あらゆる自動化ドキュメントパイプラインの基礎となります。

このガイドが役立ったと思ったら、GitHub でスターを付けたり、チームメンバーと共有したり、以下にコメントであなたのヒントを投稿してください。ハッピーコーディング！  

![解像度設定例](resolution.png "Word を Markdown として保存する際の解像度設定")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}