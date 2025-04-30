---
"description": "Aspose.Words for Javaでドキュメントをテキストファイルとして保存する方法を学びましょう。Javaコード例を使ったステップバイステップガイドをご覧ください。"
"linktitle": "文書をテキストファイルとして保存する"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でドキュメントをテキストファイルとして保存する"
"url": "/ja/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントをテキストファイルとして保存する


## Aspose.Words for Java でドキュメントをテキストファイルとして保存する方法の紹介

このチュートリアルでは、Aspose.Words for Javaライブラリを使用してドキュメントをテキストファイルとして保存する方法を説明します。Aspose.WordsはWord文書を扱うための強力なJava APIであり、プレーンテキストを含む様々な形式でドキュメントを保存するための様々なオプションを提供しています。このチュートリアルでは、その手順を説明し、サンプルJavaコードも紹介します。

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

- Java Development Kit (JDK) がシステムにインストールされています。
- Aspose.Words for Javaライブラリをプロジェクトに統合します。ダウンロードはこちらから。 [ここ](https://releases。aspose.com/words/java/).
- Java プログラミングの基礎知識。

## ステップ1：ドキュメントを作成する

ドキュメントをテキストファイルとして保存するには、まずAspose.Wordsを使ってドキュメントを作成する必要があります。以下は、コンテンツを含むドキュメントを作成するための簡単なJavaコードスニペットです。

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

次に、ドキュメントをテキストファイルとして保存する方法を指定するテキスト保存オプションを定義する必要があります。bidiマークの追加、リストのインデントなど、さまざまな設定が可能です。2つの例を見てみましょう。

### 例1: Bidiマークの追加

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

この例では、 `TxtSaveOptions` オブジェクトを設定し、 `AddBidiMarks` 財産に `true` テキスト出力に bidi マークを含めます。

### 例2: リストのインデントにタブ文字を使用する

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

ここでは、リストのインデントにタブ文字を 1 個使用する保存オプションを構成します。

## ステップ3: 文書をテキストとして保存する

テキスト保存オプションを定義したので、ドキュメントをテキストファイルとして保存できます。以下のコードは、その方法を示しています。

```java
doc.save("output.txt", saveOptions);
```

交換する `"output.txt"` テキスト ファイルを保存する目的のファイル パスを入力します。

## Aspose.Words for Java でドキュメントをテキストファイルとして保存するための完全なソースコード

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

このチュートリアルでは、Aspose.Words for Java でドキュメントをテキストファイルとして保存する方法を学びました。ドキュメントの作成、テキスト保存オプションの定義、そしてドキュメントをテキスト形式で保存する手順を説明しました。Aspose.Words はドキュメントの保存に関して非常に柔軟性が高く、特定の要件に合わせて出力をカスタマイズできます。

## よくある質問

### テキスト出力に bidi マークを追加するにはどうすればよいですか?

テキスト出力に双方向マークを追加するには、 `AddBidiMarks` の所有物 `TxtSaveOptions` に `true`。 例えば：

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### リストのインデント文字をカスタマイズできますか?

はい、リストのインデント文字は、 `ListIndentation` の所有物 `TxtSaveOptions`たとえば、リストのインデントにタブ文字を使用するには、次のようにします。

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java は多言語テキストの処理に適していますか?

はい、Aspose.Words for Javaは多言語テキストの処理に適しています。様々な言語と文字エンコーディングをサポートしているため、異なる言語で書かれたドキュメントを扱う際に幅広い選択肢となります。

### Aspose.Words for Java の詳細なドキュメントやリソースにアクセスするにはどうすればよいでしょうか?

Aspose.Words for Java に関する包括的なドキュメントとリソースは、Aspose ドキュメント Web サイトで見つかります。 [Aspose.Words for Java ドキュメント](https://reference。aspose.com/words/java/).

### Aspose.Words for Java はどこからダウンロードできますか?

Aspose.Words for Java ライブラリは、Aspose の Web サイトからダウンロードできます。 [Aspose.Words for Javaをダウンロード](https://releases。aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}