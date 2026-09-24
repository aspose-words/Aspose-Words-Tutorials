---
category: general
date: 2026-02-18
description: Javaでロードオプションを作成し、欠落フォントを検出し、警告コールバック付きでDOCXファイルを読み込む方法を学ぶ。
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: ja
og_description: Javaでロードオプションを作成し、欠落フォントを検出し、警告コールバック付きでDOCXファイルを読み込む方法を学びましょう。
og_title: Javaでロードオプションを作成 – 欠落フォントの検出とDOCXの読み込み方法
tags:
- java
- aspose-words
- document-processing
title: Javaでロードオプションを作成 – 欠落フォントの検出とDOCXの読み込み方法
url: /ja/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

alt attribute but that's okay.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでロードオプションを作成 – 欠落フォントの検出とDOCXのロード方法

「DOCX を読むだけでなく、フォントが欠落していることを教えてくれる **create load options** があるか、考えたことはありませんか？」 あなただけではありません。欠落フォントは完璧にスタイルされた文書を文字化けした混乱に変えてしまい、早期に発見することでデバッグにかかる時間を何時間も節約できます。このチュートリアルでは、**欠落フォントを検出**する正確な手順を説明し、カスタム警告コールバックを使って **DOCX をロードする方法** を示します。

## 学べること

- `LoadOptions` をインスタンス化し、警告ハンドラを設定する方法。  
- フォント置換の問題を捕捉するために警告コールバックが不可欠な理由。  
- 安全に **DOCX をロード** するために必要な正確なコードと、実務プロジェクト向けの実用的なヒント。  
- 他の警告タイプの処理や同じアプローチで PDF をロードするなど、エッジケースの扱い方。

外部ドキュメントは不要です—必要なものはすべてここにあります。

## 前提条件

- Java 17 以降（API は古いバージョンでも動作しますが、17 が最適です）。  
- `aspose-words-x.x.jar` をプロジェクトに追加した Aspose.Words for Java ライブラリ。  
- Java の例外処理に関する基本的な理解。  

これらが揃っていれば、さっそく始めましょう。

![Diagram showing the flow of creating load options, setting a warning callback, and loading a DOCX file](/images/create-load-options-diagram.png){: .center-image alt="ロードオプション作成、警告コールバック設定、DOCX ファイルロードのフローダイアグラム"}

## ステップ 1: ロードオプションの作成（DOCX のロード方法）

最初に行うべきことは **create load options** です。このオブジェクトは Aspose.Words にファイルを開く際の動作を指示します。ライブラリが DOCX を見る前に渡す指示セットと考えてください。

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

`new Document("file.docx")` を呼び出すだけではなぜだめなのでしょうか？ `LoadOptions` がないと、警告（例えば欠落フォント）に対して文書がロードされた後まで反応できず、特定のワークフローでは手遅れになる可能性があります。

## ステップ 2: 欠落フォントを検出するための警告コールバックの設定

ここで、Aspose.Words が警告を出したい状況に遭遇したときに呼び出されるコールバックを設定します。今回対象とするのは `WarningType.FONT_SUBSTITUTION` です。

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

いくつか注意点があります:

- **なぜコールバックなのか？** ロード処理 *中* に実行され、文書が完全に生成される前にログを取ったり、操作を中止したりする機会を提供します。  
- **なぜ `WarningType.FONT_SUBSTITUTION` をチェックするのか？** これが欠落フォントシナリオで Aspose.Words が使用する正確な列挙値です。必要に応じて他の警告タイプ（例: `TABLE_STRUCTURE`）も同様にフィルタリングできます。  
- **パフォーマンスのヒント:** コールバックは軽量です。内部で重い I/O を行わないようにしましょう。ファイルへの書き込みが必要な場合は、メッセージをキューに入れ、ロード後にフラッシュしてください。

## ステップ 3: 設定したオプションで DOCX ファイルをロードする

オプションとコールバックの準備ができたら、いよいよ DOCX をロードできます。これが **DOCX のロード方法** に答える部分で、設定した警告を考慮します。

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**内部で何が起きているか？** ファイルがストリームされると、Aspose.Words は各フォント参照をチェックします。参照されたフォントがインストールされていない場合、先ほど定義した警告コールバックがトリガーされます。以下のような出力が得られます:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

サーバ上でファイルのバッチ処理を行う際、この即時フィードバックは非常に価値があります。

## 完全な動作例

すべてをまとめると、IDE にコピペできる自己完結型プログラムがこちらです。

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**期待される出力**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

ファイルに欠落フォントがない場合、コールバックは何も出力せず、"DOCX loaded" 行だけが表示されます。

## プロのコツとエッジケース

| シチュエーション | 対応策 |
|-----------|------------|
| **複数の欠落フォント** | コールバックはフォントごとに発火するので、フォントごとに1行が出力されます。後で要約が必要なら `List<String>` に集約してください。 |
| **他の警告も捕捉したい** | `WarningType.TABLE_STRUCTURE`、`WarningType.UNKNOWN_FILE_FORMAT` などの `else if` ブランチを追加します。 |
| **大容量 DOCX ファイルのロード** | `LoadOptions.setLoadFormat(LoadFormat.DOCX)` を使用してフォーマットをヒントし、検出を高速化します。 |
| **Web サービスで実行** | `System.out.println` を避け、コールバック内でロガー（`SLF4J`、`Log4j`）を注入します。 |
| **実行時にフォントをインストール** | 欠落フォントを検出した後、`GraphicsEnvironment.registerFont(...)` でプログラム的にロードし、文書を再ロードできます。 |

## なぜこのアプローチが “Try‑Catch のみ” の方法より優れているのか

多くの開発者は `new Document(...)` を try‑catch ブロックで囲み、例外が欠落フォントを教えてくれることを期待します。しかし、Aspose.Words はフォント置換を *警告* とみなすため例外は発生せず、エラーとは扱われません。**ロードオプションを作成**し、警告コールバックを添付することで、パフォーマンスを犠牲にせずフォント問題を確実に把握できます。

## 次のステップ

- **PDF の欠落フォントを検出** – 同じ `LoadOptions` パターンが PDF にも使えます。ファイルパスとロードフォーマットを変更するだけです。  
- **フォントインストールの自動化** – コールバックと、共有リポジトリから欠落フォントを取得するスクリプトを組み合わせます。  
- **他の警告タイプを調査** – Aspose.Words は非推奨タグや複雑なテーブルなどについても警告できます。  

自由に試してみてください。インメモリデータを扱う場合は `Document` コンストラクタをストリーム (`new Document(InputStream, loadOptions)`) に置き換えるか、または大規模処理パイプライン向けにコンポジットパターンで複数のコールバックをチェーンしてください。

---

### TL;DR

Java で **ロードオプションを作成**し、**欠落フォントを検出**するコールバックを設定し、最終的に **DOCX を安全にロード**する方法を示しました。たった3つの簡潔なステップで、任意の Aspose.Words プロジェクトに組み込める **再利用可能なパターン** が手に入ります。

他のファイル形式に関する質問や、特定の環境向けにコールバックを調整する手助けが必要ですか？下にコメントを残してください。ハッピーコーディング！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}