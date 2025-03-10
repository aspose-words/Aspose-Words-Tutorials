---
title: Aspose.Words for Java でドキュメントを OOXML 形式で保存する
linktitle: ドキュメントをOOXML形式で保存する
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用して OOXML 形式でドキュメントを保存する方法を学びます。ファイルを簡単に保護、最適化、カスタマイズできます。
weight: 20
url: /ja/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントを OOXML 形式で保存する


## Aspose.Words for Java でドキュメントを OOXML 形式で保存する方法の紹介

このガイドでは、Aspose.Words for Java を使用して OOXML 形式でドキュメントを保存する方法について説明します。OOXML (Office Open XML) は、Microsoft Word やその他のオフィス アプリケーションで使用されるファイル形式です。OOXML 形式でドキュメントを保存するためのさまざまなオプションと設定について説明します。

## 前提条件

始める前に、プロジェクトに Aspose.Words for Java ライブラリが設定されていることを確認してください。

## パスワード暗号化による文書の保存

OOXML 形式で保存する際に、ドキュメントをパスワードで暗号化することができます。手順は次のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

//ドキュメントを読み込む
Document doc = new Document("Document.docx");

//OoxmlSaveOptionsを作成し、パスワードを設定する
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

//文書を暗号化して保存する
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXMLコンプライアンスの設定

ドキュメントを保存するときに、OOXML 準拠レベルを指定できます。たとえば、ISO 29500:2008 (厳密) に設定できます。手順は次のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

//ドキュメントを読み込む
Document doc = new Document("Document.docx");

// Word 2016 向けに最適化
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

//OoxmlSaveOptionsを作成し、コンプライアンスレベルを設定する
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

//コンプライアンス設定でドキュメントを保存する
doc.save("ComplianceDoc.docx", saveOptions);
```

## 最終保存時刻プロパティの更新

ドキュメントを保存するときに、その「最終保存時刻」プロパティを更新することを選択できます。手順は次のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

//ドキュメントを読み込む
Document doc = new Document("Document.docx");

// OoxmlSaveOptionsを作成し、最終保存時刻プロパティの更新を有効にする
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

//更新されたプロパティでドキュメントを保存します
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## 従来の制御文字の保持

ドキュメントに従来の制御文字が含まれている場合は、保存時にそれらを保持するように選択できます。手順は次のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//従来の制御文字を含む文書を読み込む
Document doc = new Document("LegacyControlChars.doc");

//FLAT_OPC 形式で OoxmlSaveOptions を作成し、従来の制御文字を保持できるようにします。
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

//従来の制御文字を使用して文書を保存する
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## 圧縮レベルの設定

ドキュメントを保存するときに圧縮レベルを調整できます。たとえば、圧縮を最小限に抑えるには SUPER_FAST に設定できます。手順は次のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

//ドキュメントを読み込む
Document doc = new Document("Document.docx");

// OoxmlSaveOptionsを作成し、圧縮レベルを設定する
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

//指定した圧縮レベルで文書を保存する
doc.save("FastCompressionDoc.docx", saveOptions);
```

これらは、Aspose.Words for Java を使用して OOXML 形式でドキュメントを保存するときに使用できる主要なオプションと設定の一部です。必要に応じて、さらに多くのオプションを調べて、ドキュメントの保存プロセスをカスタマイズしてください。

## Aspose.Words for Java でドキュメントを OOXML 形式で保存するための完全なソース コード

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## 結論

この包括的なガイドでは、Aspose.Words for Java を使用してドキュメントを OOXML 形式で保存する方法について説明しました。ドキュメントをパスワードで暗号化したり、特定の OOXML 標準に準拠したり、ドキュメントのプロパティを更新したり、従来の制御文字を保持したり、圧縮レベルを調整したりする必要がある場合でも、Aspose.Words は要件を満たす多目的なツール セットを提供します。

## よくある質問

### パスワードで保護されたドキュメントからパスワード保護を削除するにはどうすればよいですか?

パスワードで保護されたドキュメントからパスワード保護を削除するには、正しいパスワードを使用してドキュメントを開き、保存オプションでパスワードを指定せずに保存します。これにより、ドキュメントはパスワード保護なしで保存されます。

### ドキュメントを OOXML 形式で保存するときにカスタム プロパティを設定できますか?

はい、OOXML形式で保存する前に、ドキュメントのカスタムプロパティを設定できます。`BuiltInDocumentProperties`そして`CustomDocumentProperties`著者、タイトル、キーワード、カスタム プロパティなどのさまざまなプロパティを設定するクラス。

### ドキュメントを OOXML 形式で保存する場合のデフォルトの圧縮レベルは何ですか?

 Aspose.Words for Javaを使用してOOXML形式で文書を保存する場合のデフォルトの圧縮レベルは`NORMAL`圧縮レベルを変更できます`SUPER_FAST`または`MAXIMUM`必要に応じて。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
