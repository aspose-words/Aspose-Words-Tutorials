---
title: Aspose.Words for Java でドキュメントを ODT 形式で保存する
linktitle: ドキュメントをODT形式で保存する
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用してドキュメントを ODT 形式で保存する方法を学びます。オープンソースのオフィス スイートとの互換性を確保します。
weight: 19
url: /ja/java/document-loading-and-saving/saving-documents-as-odt-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントを ODT 形式で保存する


## Aspose.Words for Java でドキュメントを ODT 形式で保存する方法の紹介

この記事では、Aspose.Words for Java を使用してドキュメントを ODT (Open Document Text) 形式で保存する方法について説明します。ODT は、OpenOffice や LibreOffice などのさまざまなオフィス スイートで使用される、一般的なオープン スタンダード ドキュメント形式です。ドキュメントを ODT 形式で保存すると、これらのソフトウェア パッケージとの互換性を確保できます。

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

1. Java 開発環境: システムに Java 開発キット (JDK) がインストールされていることを確認します。

2.  Aspose.Words for Java: Aspose.Words for Javaライブラリをダウンロードしてインストールします。ダウンロードリンクは[ここ](https://releases.aspose.com/words/java/).

3. サンプル ドキュメント: ODT 形式に変換するサンプルの Word ドキュメント (例: 「Document.docx」) を用意します。

## ステップ1: ドキュメントを読み込む

まず、Aspose.Words for Java を使用して Word 文書を読み込みます。

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
```

ここ、`"Your Directory Path"`ドキュメントが保存されているディレクトリを指す必要があります。

## ステップ2: ODT保存オプションを指定する

ドキュメントを ODT として保存するには、ODT 保存オプションを指定する必要があります。さらに、ドキュメントの測定単位を設定できます。Open Office ではセンチメートルが使用され、MS Office ではインチが使用されます。ここではインチに設定します。

```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES);
```

## ステップ3: ドキュメントを保存する

次に、ドキュメントを ODT 形式で保存します。

```java
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

ここ、`"Your Directory Path"`変換された ODT ファイルを保存するディレクトリを指定する必要があります。

## Aspose.Words for Java でドキュメントを ODT 形式で保存するための完全なソース コード

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
//Open Officeでは、長さ、幅、その他の測定可能な書式を指定するときにセンチメートルを使用します。
// MS Office ではインチが使用されますが、ドキュメント内のコンテンツ プロパティではインチが使用されます。
OdtSaveOptions saveOptions = new OdtSaveOptions(); { saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES); }
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

## 結論

この記事では、Aspose.Words for Java を使用してドキュメントを ODT 形式で保存する方法を学びました。これは、OpenOffice や LibreOffice などのオープンソース オフィス スイートとの互換性を確保する必要がある場合に特に役立ちます。

## よくある質問

### Aspose.Words for Java をダウンロードするにはどうすればいいですか?

 Aspose.Words for JavaはAsposeのWebサイトからダウンロードできます。[このリンク](https://releases.aspose.com/words/java/)ダウンロードページにアクセスします。

### ドキュメントを ODT 形式で保存する利点は何ですか?

ドキュメントを ODT 形式で保存すると、OpenOffice や LibreOffice などのオープンソース オフィス スイートとの互換性が確保され、これらのソフトウェア パッケージのユーザーがドキュメントにアクセスして編集しやすくなります。

### ODT 形式で保存するときに測定単位を指定する必要がありますか?

はい、測定単位を指定することをお勧めします。Open Office ではデフォルトでセンチメートルが使用されるため、インチに設定すると一貫した書式が確保されます。

### 複数のドキュメントをバッチ処理で ODT 形式に変換できますか?

はい、Aspose.Words for Java を使用してドキュメント ファイルを反復処理し、変換プロセスを適用することで、複数のドキュメントを ODT 形式に変換する処理を自動化できます。

### Aspose.Words for Java は最新の Java バージョンと互換性がありますか?

Aspose.Words for Java は、最新の Java バージョンをサポートするために定期的に更新され、互換性とパフォーマンスの向上が保証されます。最新情報については、ドキュメントのシステム要件を確認してください。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
