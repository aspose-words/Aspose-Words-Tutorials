---
"description": "Aspose.Words for Java の読み込みオプションをマスターしましょう。ドキュメントの読み込みをカスタマイズし、暗号化を処理し、図形を変換し、Word のバージョンを設定するなど、Java ドキュメントを効率的に処理する方法を学びます。"
"linktitle": "ロードオプションの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java の読み込みオプションの使用"
"url": "/ja/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java の読み込みオプションの使用


## Aspose.Words for Java のロード オプションの操作方法の概要

このチュートリアルでは、Aspose.Words for Java の Load Options の使い方を説明します。Load Options を使用すると、ドキュメントの読み込みと処理方法をカスタマイズできます。ダーティフィールドの更新、暗号化されたドキュメントの読み込み、図形を Office Math に変換する、MS Word のバージョン設定、一時フォルダーの指定、警告の処理、メタファイルから PNG への変換など、様々なシナリオを取り上げます。それでは、ステップバイステップで詳しく見ていきましょう。

## ダーティフィールドの更新

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

このコードスニペットは、ドキュメント内のダーティフィールドを更新する方法を示しています。 `setUpdateDirtyFields(true)` このメソッドは、ドキュメントの読み込み中にダーティ フィールドが更新されることを保証するために使用されます。

## 暗号化された文書を読み込む

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

ここでは、パスワードを使用して暗号化された文書を読み込みます。 `LoadOptions` コンストラクタはドキュメントのパスワードを受け入れ、また、ドキュメントを保存するときに新しいパスワードを指定することもできます。 `OdtSaveOptions`。

## 図形をOffice Mathに変換する

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

このコードは、ドキュメントの読み込み中に図形をOffice Mathオブジェクトに変換する方法を示しています。 `setConvertShapeToOfficeMath(true)` メソッドによりこの変換が可能になります。

## MS Wordのバージョンを設定する

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

ドキュメントを読み込む際にMS Wordのバージョンを指定できます。この例では、Microsoft Word 2010に設定しています。 `setMswVersion`。

## 一時フォルダを使用する

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

一時フォルダを設定することで `setTempFolder`、ドキュメント処理中に一時ファイルが保存される場所を制御できます。

## 警告コールバック

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // ドキュメントの読み込み中に発生した警告を処理します。
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

このコードは、ドキュメントの読み込み中に発生する警告を処理するための警告コールバックの設定方法を示しています。警告発生時のアプリケーションの動作はカスタマイズ可能です。

## メタファイルをPNGに変換する

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

ドキュメントの読み込み中にメタファイル（例：WMF）をPNG画像に変換するには、 `setConvertMetafilesToPng(true)` 方法。

## Aspose.Words for Java のロード オプションを操作するための完全なソース コード

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// 新しい LoadOptions オブジェクトを作成します。これは、デフォルトで MS Word 2019 仕様に従ってドキュメントをロードします。
	// 読み込みバージョンを Microsoft Word 2010 に変更します。
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// ドキュメントの読み込み中に発生した警告とその詳細を印刷します。
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## 結論

このチュートリアルでは、Aspose.Words for Java の Load Options の様々な側面について詳しく説明しました。Load Options は、ドキュメントの読み込みと処理方法をカスタマイズする上で重要な役割を果たし、特定のニーズに合わせてドキュメント処理をカスタマイズできます。このガイドで説明した主なポイントをまとめてみましょう。

## よくある質問

### ドキュメントの読み込み中に警告を処理するにはどうすればよいですか?

警告コールバックは次のように設定できます。 `warningCallback()` 上記の方法。カスタマイズ `DocumentLoadingWarningCallback` アプリケーションの要件に応じて警告を処理するクラス。

### ドキュメントを読み込むときに図形を Office Math オブジェクトに変換できますか?

はい、図形をOffice Mathオブジェクトに変換できます。 `loadOptions。setConvertShapeToOfficeMath(true)`.

### ドキュメントを読み込むための MS Word のバージョンを指定するにはどうすればよいですか?

使用 `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` ドキュメントを読み込むための MS Word のバージョンを指定します。

### の目的は何ですか？ `setTempFolder` ロード オプションの方法?

その `setTempFolder` このメソッドを使用すると、ドキュメント処理中に一時ファイルが保存されるフォルダーを指定できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}