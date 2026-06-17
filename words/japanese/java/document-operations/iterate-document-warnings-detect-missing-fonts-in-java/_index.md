---
category: general
date: 2026-04-28
description: Aspose.Words for Java を使用して、Word ファイルのドキュメント警告を反復処理し、欠落フォントを検出し、欠落フォント名を取得して、欠落フォントの詳細を出力します。
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: ja
og_description: ドキュメントの警告を反復処理して欠落フォントを見つけ、欠落フォント名を取得し、完全なJava例を用いて欠落フォントの詳細を出力します。
og_title: 'ドキュメント警告の反復: Javaで欠落フォントを検出'
tags:
- Aspose.Words
- Java
- Document Processing
title: ドキュメント警告を反復処理：Javaで欠落フォントを検出
url: /ja/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメント警告の反復 – Javaで欠落フォントを検出

Word ファイルを開くときに **iterate document warnings** が必要で、どのフォントが欠落しているのか気になったことはありませんか？ あなただけではありません。欠落フォントはレポートの外観を壊す可能性があり、見つける手段がなければ、元の見た目とは全く違うドキュメントを配布してしまうかもしれません。  

このチュートリアルでは、Word ドキュメントを読み込み、警告を反復し、欠落フォント名を取得し、最終的に欠落フォント情報を出力する方法を **detect missing fonts** という形で、Aspose.Words for Java を使って紹介します。  

コードの最初の一行から期待されるコンソール出力までをすべてカバーするので、今すぐプロジェクトにコピー＆ペーストできる動作するソリューションが手に入ります。追加のドキュメントは不要です。

## 前提条件

- Java 8 以上がインストールされていること。
- Aspose.Words for Java ライブラリ（2026‑04‑28 時点の最新バージョン）。
- マシンにインストールされていないフォントを含む可能性のある Word ファイル（例: `doc-with-missing-font.docx`）。

これらが揃っていれば、**load word document** してすぐに反復を開始できます。

## Step 1 – デフォルトオプションで Word ドキュメントを読み込む

**iterate document warnings** を行う前に、ファイルをメモリに読み込む必要があります。Aspose.Words ではコンストラクタ呼び出しだけでこれが可能です。通常はデフォルトの `LoadOptions` で十分ですが、明示的に作成する例を示します。

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Why this matters:**  
> ドキュメントの読み込みにより、Aspose.Words はローカルにインストールされていないフォントなど、解決できないリソースをスキャンします。これらの問題は **warnings** として保存され、次のステップで **iterate document warnings** します。

## Step 2 – ドキュメント警告を反復してフォント問題を検出

解決策の核心です。読み込み時にライブラリが収集したすべての警告をループします。`WarningInfo` オブジェクトは何が問題だったかを示し、`FontSubstitutionWarning` をフィルタリングして **detect missing fonts** します。

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Pro tip:** `instanceof` チェックにより、画像読み込みの問題など他の警告を無視し、フォント関連の警告だけを処理します。これによりループが効率的になり、実際に **retrieve missing font** 情報が必要なフォントに出力を絞れます。

### 期待されるコンソール出力

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

ドキュメントに欠落フォントがない場合、ループは何も出力せずに静かに終了します — **print missing font** するものはありません。

## Step 3 – 例外を捕捉するだけではダメな理由

「`new Document(...)` 呼び出しを try‑catch でラップして例外を探すだけでいいのでは？」と疑問に思うかもしれません。答えは二つです。

1. **詳細情報:** 例外は失敗したことだけを伝えますが、警告は正確なフォント名と Aspose.Words が選択したフォールバックを提供します。
2. **致命的でない問題:** 欠落フォントは通常致命的ではなく、ドキュメントはロードされますが視覚的忠実度が損なわれます。**iterate document warnings** することで、ファイルの残りの部分を引き続き処理できます。

## Step 4 – 例の拡張: 欠落フォントをリストに収集

欠落フォントをさらに処理したい場合があります — 例えば埋め込むか、UI でユーザーに通知するか。以下の簡単な変更で名前を `Set<String>` に集められます。

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

これでプログラムから **retrieve missing font** データを取得でき、レポートモジュールやフォントインストールウィザードに渡すことができます。

## Step 5 – 実務上の考慮点

- **複数の置換:** 1 つの欠落フォントが文書の異なる部分で別々のフォントに置換されることがあります。警告リストには各出現が含まれるため、重複した欠落フォントエントリが見られることがあります。
- **パフォーマンス:** 非常に大きなドキュメントを読み込むと、数千件の警告が生成されることがあります。フォントだけが必要な場合は、前述のように早期にフィルタリングしてループを高速化してください。
- **クロスプラットフォームフォント:** Linux ではデフォルトの置換フォントが *Liberation Sans* になることが多く、Windows では *Arial* になることがあります。フォールバックを把握しておくと、カスタムフォントをアプリに同梱すべきか判断しやすくなります。

## Step 6 – ビジュアルエイド

以下はコンソール出力のスクリーンショットです（SEO 用に主要キーワードを含む alt テキスト）。

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt text:* *iterate document warnings example displaying missing font names and substitution details.*

## 結論

これで Aspose.Words for Java における **iterate document warnings** の方法、**detect missing fonts**、安全な **load word document**、**retrieve missing font** 情報の取得、そしてコンソールへの **print missing font** 出力を習得しました。完全なコードスニペットはそのまま実行可能で、ファイルへのログ出力や UI ダイアログ表示、さらには欠落フォントを自動的に埋め込む処理へと拡張できます。

次のステップとして、カスタムフォントソース（例: 企業フォントフォルダー）を追加して **load word document** する方法や、欠落フォントを直接ファイルに埋め込んでマシン間でレイアウトを保持する方法を調べてみてください。どちらも本稿で扱った内容を自然に発展させたテーマです。

Happy coding, and may your PDFs always look exactly as you intended!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}