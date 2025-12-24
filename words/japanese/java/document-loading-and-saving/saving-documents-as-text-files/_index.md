---
date: 2025-12-24
description: Aspose.Words for Java を使用して Word ドキュメントからプレーンテキストファイルを作成する方法を学びます。このガイドでは、Word
  を txt に変換し、タブインデントを使用し、Word を txt として保存する方法を示します。
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Javaでプレーンテキストファイルを作成する方法
url: /ja/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用してプレーンテキストファイルを作成する方法

## Aspose.Words for Java で文書をテキストファイルとして保存する概要

このチュートリアルでは、Aspose.Words for Java ライブラリを使用して **Word 文書からプレーンテキストファイルを作成する方法** を学びます。**word を txt に変換** したい場合や、レポート生成を自動化したい場合、あるいは生テキストを抽出してさらに処理した場合でも、本ガイドは文書作成から **タブインデント** の使用や **bidi マーク** の追加といった保存オプションの微調整まで、全工程を丁寧に解説します。さっそく始めましょう！

## Quick Answers
- **文書を作成する主なクラスは何ですか？** Aspose.Words の `Document`。
- **右から左の言語用に bidi マークを追加するオプションは？** `TxtSaveOptions.setAddBidiMarks(true)`。
- **リスト項目をタブでインデントするには？** `ListIndentation.Character` に `'\t'` を設定。
- **開発用にライセンスは必要ですか？** テスト目的なら無料トライアルで可。製品環境ではライセンスが必要です。
- **カスタム名とパスでファイルを保存できますか？** はい、`doc.save()` にフルパスを渡すだけです。

## 前提条件

開始する前に、以下の前提条件が整っていることを確認してください。

- システムに Java Development Kit (JDK) がインストールされていること。  
- プロジェクトに Aspose.Words for Java ライブラリが組み込まれていること。ダウンロードは [here](https://releases.aspose.com/words/java/) から可能です。  
- Java プログラミングの基本知識があること。

## 手順 1: 文書を作成する

**word を txt に保存** するには、まず `Document` インスタンスが必要です。以下は、複数言語のテキストを数行書き込むシンプルな Java スニペットです。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

このコードでは新しい文書を作成し、英語、ヘブライ語、アラビア語のテキストを追加し、ヘブライ語段落に右から左の書式設定を有効にしています。

## 手順 2: テキスト保存オプションを定義する

次に、文書をプレーンテキストファイルとして保存する方法を設定します。Aspose.Words の `TxtSaveOptions` クラスを使えば、bidi マークからリストインデントまで細かく制御できます。

### 例 1: Bidi マークの追加（RTL 対応の txt 保存方法）

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

`AddBidiMarks` を `true` に設定すると、右から左の文字が **プレーンテキストファイル** 内で正しく表現されます。

### 例 2: タブ文字によるリストインデント（タブインデントの使用）

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

ここでは、各リストレベルの前にタブ文字 (`'\t'`) を付加するよう Aspose.Words に指示し、テキスト出力を見やすくしています。

## 手順 3: 文書をテキストとして保存する

保存オプションの設定が完了したら、**プレーンテキストファイル** として文書を永続化します。

```java
doc.save("output.txt", saveOptions);
```

`"output.txt"` を、保存したいフルパスに置き換えてください。

## Aspose.Words for Java で文書をテキストファイルとして保存する完全ソースコード

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## よくある問題と解決策

| Issue | Solution |
|-------|----------|
| **Bidi 文字が文字化けして表示される** | `setAddBidiMarks(true)` が有効か確認し、出力ファイルを UTF‑8 エンコーディングで開く。 |
| **リストインデントが期待通りにならない** | `ListIndentation.Count` と `Character` が目的の値（タブ `'\t'` またはスペース `' '`）に設定されているか確認。 |
| **ファイルが作成されない** | ディレクトリパスが存在し、アプリケーションに書き込み権限があるかチェック。 |

## FAQ

### テキスト出力に bidi マークを追加する方法は？

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### リストインデント文字をカスタマイズできますか？

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java は多言語テキストの処理に適していますか？

はい。Aspose.Words for Java は多数の言語と文字エンコーディングをサポートしており、マルチリンガルコンテンツをプレーンテキストとして抽出・保存するのに最適です。

### Aspose.Words for Java のドキュメントやリソースはどこで入手できますか？

包括的なドキュメントとリソースは Aspose.Words for Java の公式ページで確認できます: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)。

### Aspose.Words for Java のダウンロード先は？

公式サイトからダウンロードできます: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)。

### バッチ処理で **word を txt に変換** したい場合は？

上記コードをループで囲み、各 `.docx` ファイルを読み込んで同じ `TxtSaveOptions` を適用し、`.txt` として保存します。各イテレーション後に `Document` オブジェクトを破棄してリソースを管理してください。

### API でファイルではなくストリームに直接保存できますか？

はい。`doc.save(outputStream, saveOptions)` に `OutputStream` を渡すことで、メモリ内処理や Web サービスとの統合が可能です。

---

**最終更新日:** 2025-12-24  
**テスト環境:** Aspose.Words for Java 24.12 (最新)  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}