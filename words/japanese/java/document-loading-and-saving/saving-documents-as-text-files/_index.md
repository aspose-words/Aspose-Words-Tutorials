---
title: Aspose.Words for Java でドキュメントをテキスト ファイルとして保存する
linktitle: 文書をテキストファイルとして保存する
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java でドキュメントをテキスト ファイルとして保存する方法を学びます。Java コード例を使用したステップバイステップのガイドに従ってください。
weight: 24
url: /ja/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントをテキスト ファイルとして保存する


## Aspose.Words for Java でドキュメントをテキスト ファイルとして保存する方法の紹介

このチュートリアルでは、Aspose.Words for Java ライブラリを使用してドキュメントをテキスト ファイルとして保存する方法について説明します。Aspose.Words は、Word ドキュメントを操作するための強力な Java API であり、プレーン テキストを含むさまざまな形式でドキュメントを保存するためのさまざまなオプションを提供します。これを実現するための手順を説明し、その過程でサンプル Java コードを提供します。

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

- システムに Java 開発キット (JDK) がインストールされています。
-  Aspose.Words for Javaライブラリがプロジェクトに統合されます。ダウンロードはこちらから[ここ](https://releases.aspose.com/words/java/).
- Java プログラミングの基礎知識。

## ステップ1: ドキュメントを作成する

ドキュメントをテキスト ファイルとして保存するには、まず Aspose.Words を使用してドキュメントを作成する必要があります。以下は、コンテンツを含むドキュメントを作成するための簡単な Java コード スニペットです。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

このコードでは、新しいドキュメントを作成し、さまざまな言語のテキストを含むテキストを追加します。

## ステップ2: テキスト保存オプションを定義する

次に、ドキュメントをテキスト ファイルとして保存する方法を指定するテキスト保存オプションを定義する必要があります。bidi マークの追加、リストのインデントなど、さまざまな設定を構成できます。2 つの例を見てみましょう。

### 例1: Bidiマークの追加

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

この例では、`TxtSaveOptions`オブジェクトを設定し、`AddBidiMarks`財産に`true`テキスト出力に bidi マークを含めます。

### 例 2: リストのインデントにタブ文字を使用する

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

ここでは、リストのインデントにタブ文字を 1 個使用するように保存オプションを構成します。

## ステップ3: 文書をテキストとして保存する

テキスト保存オプションを定義したので、ドキュメントをテキスト ファイルとして保存できます。次のコードは、その方法を示しています。

```java
doc.save("output.txt", saveOptions);
```

交換する`"output.txt"`テキスト ファイルを保存する目的のファイル パスを入力します。

## Aspose.Words for Java でドキュメントをテキスト ファイルとして保存するための完全なソース コード

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
        // 段階のインデントを持つリストを作成します。
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
        // 段階のインデントを持つリストを作成します。
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

## 結論

このチュートリアルでは、Aspose.Words for Java でドキュメントをテキスト ファイルとして保存する方法を学習しました。ドキュメントの作成、テキスト保存オプションの定義、ドキュメントをテキスト形式で保存する手順について説明しました。Aspose.Words はドキュメントの保存に関して非常に柔軟であり、特定の要件に合わせて出力をカスタマイズできます。

## よくある質問

### テキスト出力に bidi マークを追加するにはどうすればよいですか?

テキスト出力に双方向マークを追加するには、`AddBidiMarks`の所有物`TxtSaveOptions`に`true`。 例えば：

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### リストのインデント文字をカスタマイズできますか?

はい、リストのインデント文字は、`ListIndentation`の所有物`TxtSaveOptions`たとえば、リストのインデントにタブ文字を使用するには、次のようにします。

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java は多言語テキストの処理に適していますか?

はい、Aspose.Words for Java は多言語テキストの処理に適しています。さまざまな言語と文字エンコードをサポートしているため、さまざまな言語のドキュメントを扱うための多目的な選択肢となります。

### Aspose.Words for Java の詳細なドキュメントやリソースにアクセスするにはどうすればいいですか?

 Aspose.Words for Java の包括的なドキュメントとリソースは、Aspose ドキュメント Web サイトで見つかります。[Aspose.Words for Java ドキュメント](https://reference.aspose.com/words/java/).

### Aspose.Words for Java はどこからダウンロードできますか?

 Aspose.Words for Java ライブラリは、Aspose の Web サイトからダウンロードできます。[Aspose.Words for Java をダウンロード](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
