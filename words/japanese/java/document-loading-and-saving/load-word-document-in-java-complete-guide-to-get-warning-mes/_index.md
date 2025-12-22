---
category: general
date: 2025-12-22
description: JavaでWord文書を読み込み、警告メッセージの取得方法、特にフォントが欠落している場合の対処方法を学びます。このステップバイステップのチュートリアルでは、警告、フォント置換、ベストプラクティスについて解説します。
draft: false
keywords:
- load word document
- get warning messages
- handle missing fonts
- Aspose.Words warnings
- font substitution warning
language: ja
og_description: JavaでWord文書を読み込み、警告メッセージを即座に取得します。実践的なコード例で欠落フォントの対処方法を学びましょう。
og_title: JavaでWord文書を読み込む – 警告取得と欠落フォントの管理
tags:
- Java
- Aspose.Words
- Document Processing
title: JavaでWord文書を読み込む – 警告メッセージの取得と欠落フォントの処理完全ガイド
url: /ja/java/document-loading-and-saving/load-word-document-in-java-complete-guide-to-get-warning-mes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java で Word 文書を読み込む – 警告メッセージ取得とフォント欠損への対処完全ガイド

Word 文書を **Java で読み込む** 必要があって、フォントが消えてしまったり、謎の警告が出続けたりしたことはありませんか？ 多くのプロジェクトで、特に文書が別のマシンへ渡るとき、フォントが欠損すると `FontSubstitutionWarning` が発生し、レイアウトが崩れることがあります。  

このチュートリアルでは **Word 文書の読み込み方法**、**警告メッセージの取得方法**、そして **フォント欠損への優雅な対処法** を紹介します。最後まで読むと、すべての警告を出力する実行可能なコードスニペットが手に入り、フォントを埋め込むか置換えるか、あるいは後で確認できるようにログに残すかを選択できるようになります。

> **学べること**
> - Aspose.Words for Java を使って **Word 文書を読み込む** 正確なコード  
> - `document.getWarnings()` を走査し `FontSubstitutionWarning` をフィルタリングする方法  
> - フォント欠損への対処法（フォント埋め込みやフォールバックの提供）  

## 前提条件

- Java 8 以上がインストールされていること。  
- Maven（または Gradle）で依存関係を管理できること。  
- Aspose.Words for Java ライブラリ（デモ用に無料トライアルで可）。  

まだプロジェクトに Aspose.Words を追加していない場合は、以下の Maven 依存を追加してください。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

*(Gradle 用の記述でも同様に使用できます – API は同一です。)*  

## 手順 1: 読み込みオプションの準備 – Word 文書を読み込むための出発点

実際に **Word 文書を読み込む** 前に、欠損リソースの取り扱いを微調整したい場合があります。`LoadOptions` を使うとフォント置換や画像読み込みなどを制御できます。

```java
import com.aspose.words.*;

public class LoadDocumentDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Prepare load options (default options are fine for most cases)
        LoadOptions loadOptions = new LoadOptions();

        // Optional: Force the library to use a specific font folder
        // loadOptions.setFontSettings(new FontSettings());
        // loadOptions.getFontSettings().setFontsFolder("C:/MyFonts", true);
```

> **なぜ重要か:**  
> `LoadOptions` を使用すると、**Word 文書の読み込み** 時に欠損フォントが見つかった場合、ライブラリが置換フォントを探す場所を指定できます。この手順を省くと、予期しない大量の `FontSubstitutionWarning` が発生する可能性があります。

## 手順 2: 指定したオプションで Word 文書を読み込む

ここで実際にディスク上の **Word 文書を読み込む** ことになります。コンストラクタにはファイルパスと先ほど設定した `LoadOptions` を渡します。

```java
        // Step 2: Load the Word document with the specified options
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

> **ヒント:**  
> ファイルが JAR に埋め込まれている、またはネットワークストリームから取得する場合は、`Document` コンストラクタの `InputStream` オーバーロードを使用してください。警告処理ロジックは同じです。

## 手順 3: 警告メッセージを取得・フィルタリング – 欠損フォントに注目

Aspose.Words は読み込み中に発生した問題を `WarningInfoCollection` に格納します。これをループで走査し、`FontSubstitutionWarning` を探して各メッセージを出力します。

```java
        // Step 3: Retrieve any warnings generated during loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 4: Identify font substitution warnings and display their messages
            if (warning instanceof FontSubstitutionWarning) {
                System.out.println("[Font Warning] " + warning.getMessage());
            } else {
                // Optionally handle other warning types
                System.out.println("[Other Warning] " + warning.getMessage());
            }
        }
    }
}
```

**期待される出力**（例）:

```
[Font Warning] Font 'Calibri' not found. Substituted with 'Arial'.
[Font Warning] Font 'Times New Roman' not found. Substituted with 'Liberation Serif'.
```

これで欠損フォントに関する **警告メッセージ取得** が明確に確認でき、次の対策を検討できます。

## 手順 4: 欠損フォントの対処 – 実践的な戦略

フォント警告は有益ですが、最終的に文書が作者の意図通りに表示されるよう **欠損フォントを処理** したいでしょう。

### 4.1 フォントを文書に直接埋め込む

ソースの `.docx` を管理できる場合は、保存時にフォント埋め込みを有効にします。

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setEmbedTrueTypeFonts(true);
document.setFontSettings(fontSettings);
document.save("output.docx");
```

> **結果:** 生成された `output.docx` に必要なフォントが埋め込まれ、下流マシンでの置換警告がほとんど解消されます。

### 4.2 カスタムフォントフォルダーを指定する

埋め込みが不可能（ライセンス制限など）な場合は、欠損フォントが格納されたフォルダーを Aspose.Words に教えます。

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setFontsFolder("C:/SharedFonts", true); // true = scan subfolders
loadOptions.setFontSettings(fontSettings);
```

これで **Word 文書を読み込む** ときにライブラリが欠損フォントを見つけ、警告の出力を止めます。

### 4.3 監査用に警告をログへ記録する

本番環境では、コンソールへの出力ではなくログファイルに警告を保存したいことがあります。

```java
import java.io.FileWriter;
import java.io.PrintWriter;

PrintWriter logger = new PrintWriter(new FileWriter("load-warnings.log", true));
for (WarningInfo warning : document.getWarnings()) {
    logger.println("[Warning] " + warning.getMessage());
}
logger.close();
```

この方法は、欠損フォントが検出・処理されたことを証明するコンプライアンス要件を満たします。

## 手順 5: 完全動作サンプル – すべてをひとつにまとめた例

以下は **Word 文書を読み込む**、**警告メッセージを取得**、そして **カスタムフォントフォルダーで欠損フォントを処理** する完全な実装例です。

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.PrintWriter;

public class WordLoadWithWarnings {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // 👉 Optional: point to a custom font folder
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("C:/SharedFonts", true);
        loadOptions.setFontSettings(fontSettings);

        // 2️⃣ Load the document
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Open a log file for warning capture
        PrintWriter logger = new PrintWriter(new FileWriter("load-warnings.log", true));

        // 4️⃣ Iterate through warnings
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                System.out.println("[Font Warning] " + warning.getMessage());
                logger.println("[Font Warning] " + warning.getMessage());
            } else {
                System.out.println("[Other Warning] " + warning.getMessage());
                logger.println("[Other Warning] " + warning.getMessage());
            }
        }

        // 5️⃣ (Optional) Save with embedded fonts
        FontSettings embedSettings = new FontSettings();
        embedSettings.setEmbedTrueTypeFonts(true);
        doc.setFontSettings(embedSettings);
        doc.save("output-with-embedded-fonts.docx");

        logger.close();
    }
}
```

**このサンプルの流れ:**
1. `LoadOptions` を設定し、欠損フォントが格納されたフォルダーを指すようにエンジンを構成。  
2. **Word 文書を読み込み**、同時に警告を収集。  
3. 各警告を出力・ログに記録し、`FontSubstitutionWarning` に注目。  
4. フォントを埋め込んだ新しいコピーを保存し、将来の警告を防止。  

## よくある質問 (FAQ)

**Q: 古い `.doc` ファイルでも動作しますか？**  
A: はい。Aspose.Words は `.doc` と `.docx` の両方をサポートしており、同じ警告処理ロジックが適用されます。

**Q: ライセンス上の理由でフォントを埋め込めない場合は？**  
A: カスタムフォントフォルダー方式（手順 4.2）を使用してください。ライセンスを遵守しつつ、視覚的忠実度を保てます。

**Q: 警告コレクションはパフォーマンスに影響しますか？**  
A: 影響は極めて小さいです。警告は軽量なコレクションに格納されます。数千件の文書を処理する場合は `LoadOptions` で警告コールバックを無効化（`loadOptions.setWarningCallback(null)`）できますが、その場合 **警告メッセージ取得** ができなくなります。

## 結論

Java で **Word 文書を読み込む**、**警告メッセージを取得する**、そして **欠損フォントを効果的に処理する** ためのすべての手順を解説しました。`LoadOptions` の設定、`document.getWarnings()` の走査、フォント埋め込みまたはカスタムフォントフォルダーのいずれかを適用することで、欠損フォントが出力に与える影響を完全にコントロールできます。

これで、バッチ変換サービス、文書ビューア、サーバーサイドのレポートジェネレータなど、あらゆる Java アプリケーションで自信を持って Word ファイルを処理できるようになります。次のステップとして、**欠損フォントをプログラムで置換** する方法や、**レイアウトを保持したまま PDF へ変換** する方法を探求してみてください。可能性は無限です。

*Happy coding, and may your documents never lose a font again!*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}