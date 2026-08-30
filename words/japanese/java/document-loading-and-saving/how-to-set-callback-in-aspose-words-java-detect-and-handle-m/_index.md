---
category: general
date: 2026-06-20
description: Aspose.Words Javaでコールバックを設定し、欠落フォントを検出して文書の読み込みをカスタマイズする方法。フォント置換警告のステップバイステップの処理方法を学びましょう。
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: ja
og_description: Aspose.Words Javaでフォントが見つからない場合を検出し、置換を処理し、ドキュメントの読み込みをカスタマイズするコールバックの設定方法。コード付きの完全ガイド。
og_title: コールバックの設定方法 – Aspose.Words Javaで欠落フォントを検出
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Aspose.Words Javaでコールバックを設定する方法 – 欠落フォントの検出と処理
url: /ja/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Javaでコールバックを設定する方法 – 欠落フォントの検出と処理

Ever wondered **how to set callback** in Aspose.Words Java so you can spot missing fonts before they ruin your PDF or DOCX? You're not the only one. Missing font warnings can silently corrupt layout, and without a proper warning callback you might never notice until the final document looks off.  

このチュートリアルでは、**欠落フォントを検出**し、**欠落フォントを適切に処理**し、警告コールバックを使用して **ドキュメントの読み込みをカスタマイズ** する、完全に実行可能なサンプルを順に解説します。最後まで読むと、任意のプロジェクトに組み込める自己完結型のJavaクラスが手に入り、追加のドキュメントを探す手間が不要になります。

## 必要なもの

- Java 8 以降（コードは Java 11+ でも動作します）  
- Aspose.Words for Java ライブラリ（バージョン 23.9 以降）  
- インストールされていないフォントを参照している DOCX ファイル（例：カスタム社内フォント）  

If you haven’t added Aspose.Words to your Maven project yet, just include:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

That’s it—no extra plugins, no native dependencies.

## ステップ 1: WarningCallback メカニズムを理解する

**警告コールバック** は、ドキュメントの読み込みや保存中に予期しない事象が発生したときに Aspose.Words が通知する仕組みです。`IWarningCallback` を実装することで、ログに記録するか無視するか、あるいは例外に変換するかを完全に制御できます。

> **なぜ重要か:**  
> フォントが欠落している場合、Aspose は代替フォントに置き換えます。特にブランド重視の PDF では視覚的な違いが大きくなります。`WarningType.FONT_SUBSTITUTION` を捕捉すれば、正確なフォント名をログに記録したり、処理を中止したり、独自のフォントにプログラムで置き換えることができます。

## ステップ 2: LoadOptions インスタンスを作成する

`LoadOptions` はドキュメント読み込みをカスタマイズするためのエントリーポイントです。ファイルを実際に読み込む前に、このオブジェクトにコールバックを設定します。

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

この時点では `loadOptions` は単なるコンテナで、まだ何も起きていません。コールバックを差し込んだ瞬間に本当の魔法が始まります。

## ステップ 3: コールバックを実装してアタッチする

以下は `IWarningCallback` を実装したコンパクトな匿名クラスです。フォント置換が発生するたびにコンソールへフレンドリーなメッセージを出力します。

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **プロのコツ:** **欠落フォントを処理**したい場合は、`LoadOptions` に `FontSettings` を設定し、欠落フォントを既知の代替フォントにマッピングすることもできます。

## ステップ 4: カスタムオプションでドキュメントを読み込む

コールバックが設定されたので、ドキュメントを読み込みます。ファイルが存在しないフォントを参照している場合、警告がコンソールに出力されます。

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

プログラムを実行すると、コンソールに次のように表示されることがあります:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

この行は、**欠落フォントを検出** に成功し、**欠落フォントを好きな方法で処理** できる状態になったことを示しています。

## ステップ 5: オプション – 欠落フォントを既知のフォントに置き換える

欠落フォントを自動的に `Times New Roman` などのフォントに置き換えたい場合は、`FontSettings` オブジェクトを追加できます:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

これでドキュメントが読み込まれ、`MyCustomFont` への参照はすべて静かに `Times New Roman` に置き換えられます。コンソールには置き換えられたフォント名が依然として表示され、状況を把握できます。

## 完全動作サンプル

以下は、上記のすべての手順を組み込んだ単一の Java クラスです。IDE にコピーペーストし、`docPath` を調整して実行してください。

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**期待される出力**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

これで **欠落フォントを検出**、**欠落フォントを処理**、そして **ドキュメントの読み込みをカスタマイズ** する再現可能な方法が手に入りました—すべて **コールバックの設定方法** を正しく学ぶことで実現できます。

## よくある質問

### フォントが欠落したときにプログラムの読み込みを停止させたい場合は？

`warning` メソッド内で例外をスローします:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

下部の catch ブロックで例外を捕捉でき、ログ出力やユーザーへの通知方法を決められます。

### DOCX から生成された PDF でも動作しますか？

もちろんです。コールバックは **読み込み** フェーズで発火し、すべての出力形式（PDF、DOCX、HTML など）で同じです。ソースドキュメントを同じ `LoadOptions` で読み込めば、最終的な PDF に影響が出る前に欠落フォントを捕捉できます。

### 画像変換など、他の警告タイプも取得できますか？

はい。`WarningInfo.getWarningType()` を `WarningType.IMAGE_CONVERSION` などの他の列挙値と比較できます。コールバック内に `if` 分岐を追加するだけです。

### パフォーマンスへの影響はありますか？

影響はほとんどありません。コールバックは読み込み中に同期的に実行され、追加チェックは軽量です。数千件のドキュメントを処理する場合は、本番環境で `loadOptions.setWarningCallback(null);` と設定して警告を無効化することも検討してください。

## ビジュアル概要

![Aspose.Words Javaでのコールバック設定例](https://example.com/images/callback-diagram.png "コールバック設定例")

*この図はフローを示しています: `LoadOptions` → `IWarningCallback` → ドキュメント読み込み → フォント置換処理*

## まとめ

本稿では Aspose.Words Java における **コールバックの設定方法** を取り上げ、**欠落フォントの検出** を実演し、**欠落フォントの処理** の実用的な方法を示し、`LoadOptions` を用いた **ドキュメント読み込みのカスタマイズ** について解説しました。  

この知識を活用すれば、サイレントなフォント置換からドキュメントパイプラインを保護し、ブランドの一貫性を保ち、問題が発生した際にユーザーへ明確なフィードバックを提供できます。

### 次にやること

- 多数の欠落フォントを一括マッピングするための **フォント置換テーブル** を調査する。  
- このコールバックを **ドキュメント検証** と組み合わせて、スタイルガイドを強制する。  
- `System.out` の代わりにログファイルや監視システムへ書き込む **カスタム警告コールバック** を試す。  

ぜひ試してみて、独自プロジェクトでどのようにコールバックをカスタマイズしたか教えてください。コーディングを楽しんで！

## 次に学ぶべきこと

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words for JavaでLoadOptionsを設定する方法](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Wordsでフォントを検出する方法 – 警告と設定の処理](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Wordsでフォントを取得する完全ガイド](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}