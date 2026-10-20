---
category: general
date: 2026-05-26
description: Aspose.Words を使用して Java で破損した Word ドキュメントを開く。リカバリーモードの設定方法と、破損した Word
  ファイルを確実に復元する方法を学びましょう。
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: ja
og_description: Aspose.Words を使用して Java で破損した Word ドキュメントを開く。このガイドでは、リカバリモードの設定方法と破損した
  Word ファイルを効率的に復元する方法を示します。
og_title: 破損したWord文書を開く – Javaでリカバリモードを設定
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: 破損したWord文書を開く – Javaでリカバリモードを設定する
url: /ja/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 破損した Word ドキュメントを開く – Java でリカバリモードを設定する

破損した Word ドキュメントを開こうとして例外でプログラムがクラッシュするのを見たことがありますか？ あなた一人ではありません—壊れた .docx ファイルは本当に頭痛の種です。 良いニュースは、Aspose.Words for Java が細かい制御を提供してくれるので、アプリがクラッシュせずに **open corrupted word document** が可能になり、警告を表示するか、サイレントリカバリにするか、あるいはハードリジェクトにするかを選べます。

このチュートリアルでは、正しい `LoadOptions` の作成から、適切な **set recovery mode** の値の選択、そしてドキュメントが実際にロードされたことの確認まで、完全なプロセスを順を追って説明します。最後まで読むと、手動でコピー＆ペーストすることなく、**how to recover corrupted word file** をプログラムで実行できるようになります。

> **必要な環境**  
> * Java 8 以降（API は Java 11 でも動作します）  
> * Aspose.Words for Java 23.9（または最新バージョン）  
> * サンプルの破損 .docx ファイル—手元にない場合は、任意の有効なファイル名を変更して破損をシミュレートしてください  

さっそく始めましょう。

## 破損した Word ドキュメントを開く – ステップバイステップ概要

以下は実装する高レベルのフローです：

1. **Create `LoadOptions`** – このオブジェクトは、問題に遭遇したときに Aspose.Words がどのように振る舞うかを指示します。  
2. **Set recovery mode** – `RECOVER_WITH_WARNINGS`、`RECOVER_WITHOUT_WARNINGS`、または `REJECT_CORRUPTED` のいずれかを選択します。  
3. **Load the document** – 設定したオプションを使用してドキュメントをロードします。  
4. **Verify** – ロードが成功したかを確認します（例：ページ数を出力）。  

各ステップは詳細に説明し、IDE に直接コピー＆ペーストできるコードスニペットを添えています。

## 異なるシナリオ向けのリカバリモード設定

Aspose.Words は `LoadOptions.RecoveryMode` 内に 3 つのリカバリ戦略を定義しています：

| モード | 動作 | 使用するタイミング |
|------|-----------|-------------|
| `RECOVER_WITH_WARNINGS` | ドキュメントの読み込みを試みますが、問題をコンソールに警告として表示します。 | アプリが中断せずに *何が* 問題だったかを確認したいとき。 |
| `RECOVER_WITHOUT_WARNINGS` | 可能な限り静かに修復し、警告を抑制します。 | ログをクリーンに保つ必要がある本番環境。 |
| `REJECT_CORRUPTED` | 破損が検出された瞬間に例外をスローします。 | 失敗を速やかに検出すべき厳格なバリデーションパイプライン。 |

正しいモードを選択することが **set recovery mode** を正しく設定する本質です。デバッグ時の多くのケースでは `RECOVER_WITH_WARNINGS` が最適で、修復された部分を正確に教えてくれます。

## Aspose.Words を使用した破損した Word ファイルのリカバリ方法

以下は **完全かつ実行可能な Java プログラム** で、全プロセスをデモします。`RecoveryModeDemo.java` ファイルに貼り付け、パスを調整して実行してください。

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### 各行の重要ポイント

* **`LoadOptions loadOptions = new LoadOptions();`** – このオブジェクトがないと Aspose.Words はデフォルトでリカバリを行わず、破損ファイルを *reject* します。作成することで動作を変更できるフックが得られます。  
* **`setRecoveryMode(...)`** – これが **set recovery mode** の呼び出しで、警告を表示するか隠すか、例外を発生させるかを決定します。  
* **`new Document(path, loadOptions);`** – コンストラクタは先ほど設定した `LoadOptions` を受け取り、ライブラリが最初から破損ファイルの扱い方を把握します。  
* **`doc.getPageCount()`** – 簡易的なサニティチェックです。ドキュメントがロードされページ数が返ってくれば、**how to recover corrupted word file** に成功したことになります。  
* **`doc.save(...)`** – 任意ですが便利です。修復されたバージョンをディスクに書き出して後で利用できます。

## 一般的なエッジケースの処理

### 1. ファイルが見つからない

パスが間違っていると `Document` は `FileNotFoundException` をスローします。ロード処理を try‑catch で囲み、フレンドリーなメッセージをログに出しましょう：

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. 修復不可能な破損

`RECOVER_WITH_WARNINGS` を使用していても、構造が修復不能な場合があります。その場合 Aspose.Words は可能な部分だけをロードしますが、 “Cannot read paragraph properties” のような警告がコンソールに表示されます。これらの警告は、手動で再構築が必要な欠落セクションを指し示すことが多いので注意してください。

### 3. 大容量ファイルとパフォーマンス

リカバリは、ライブラリがファイルを 2 回解析する（問題検出と再構築）ため、若干のオーバーヘッドが発生します。マルチギガバイトのドキュメントの場合は、ストリーミングで処理するか、JVM ヒープを `-Xmx2g` などに増やして `OutOfMemoryError` を回避してください。

## プロのコツ – リカバリを堅牢にする方法

* **警告をファイルに記録** – `System.err` をロガーにリダイレクトして、何が修正されたかの監査ログを残します。  
* **リカバリ後に検証** – `doc.updatePageLayout();` を実行し、再度ページ数をチェックします。破損したセクションを修正した後、レイアウトが変わることがあります。  
* **バッチリカバリを自動化** – デモをループでラップし、フォルダ内の破損ファイルをすべて同じ `LoadOptions` で処理します。

## 結論

これで Aspose.Words for Java を使って **how to recover corrupted word file** を正確に実行できるようになりました。`LoadOptions` インスタンスを作成し、シナリオに合った **set recovery mode** を設定してそのオプションでドキュメントをロードすれば、アプリケーションをクラッシュさせることなく **open corrupted word document** が可能です。上記のサンプルコードは、ページ数を出力し、クリーンアップされたコピーを保存する完全な実行可能ソリューションです。

次は何をしますか？リカバリモードを `RECOVER_WITHOUT_WARNINGS` に切り替えてコンソール出力を比較するか、暗号化されたドキュメントのロードを試してみてください（パスワードは別途指定する必要があります）。

## 関連チュートリアル

- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [How to Compare Two Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}