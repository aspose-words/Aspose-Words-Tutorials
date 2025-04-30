---
"description": "Aspose.Words for Java を使って、OOXML 形式でドキュメントを保存する方法を学びましょう。ファイルのセキュリティ保護、最適化、カスタマイズを簡単に実現できます。"
"linktitle": "ドキュメントをOOXML形式で保存する"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でドキュメントを OOXML 形式で保存する"
"url": "/ja/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントを OOXML 形式で保存する


## Aspose.Words for Java でドキュメントを OOXML 形式で保存する方法の紹介

このガイドでは、Aspose.Words for Java を使用してドキュメントを OOXML 形式で保存する方法を説明します。OOXML (Office Open XML) は、Microsoft Word などのオフィスアプリケーションで使用されるファイル形式です。OOXML 形式でドキュメントを保存するためのさまざまなオプションと設定について説明します。

## 前提条件

始める前に、プロジェクトに Aspose.Words for Java ライブラリが設定されていることを確認してください。

## パスワード暗号化による文書の保存

OOXML形式で保存する際に、ドキュメントをパスワードで暗号化することができます。手順は以下のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// ドキュメントを読み込む
Document doc = new Document("Document.docx");

// OoxmlSaveOptionsを作成し、パスワードを設定する
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// 文書を暗号化して保存する
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXMLコンプライアンスの設定

ドキュメントを保存する際に、OOXML準拠レベルを指定できます。例えば、ISO 29500:2008（Strict）に設定できます。手順は以下のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// ドキュメントを読み込む
Document doc = new Document("Document.docx");

// Word 2016向けに最適化
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// OoxmlSaveOptionsを作成し、コンプライアンスレベルを設定する
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// コンプライアンス設定でドキュメントを保存する
doc.save("ComplianceDoc.docx", saveOptions);
```

## 最終保存時刻プロパティの更新

ドキュメントを保存するときに、「最終保存日時」プロパティを更新するように選択できます。手順は以下のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// ドキュメントを読み込む
Document doc = new Document("Document.docx");

// OoxmlSaveOptionsを作成し、最終保存時刻プロパティの更新を有効にする
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// 更新されたプロパティでドキュメントを保存します
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## 従来の制御文字の保持

ドキュメントに従来の制御文字が含まれている場合は、保存時にそれらを保持するように選択できます。手順は以下のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// 従来の制御文字を含む文書を読み込む
Document doc = new Document("LegacyControlChars.doc");

// FLAT_OPC形式でOoxmlSaveOptionsを作成し、従来の制御文字を保持できるようにします。
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// 従来の制御文字を含む文書を保存する
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## 圧縮レベルの設定

ドキュメントを保存する際、圧縮レベルを調整できます。例えば、圧縮率を最低限に抑えたい場合は「SUPER_FAST」に設定できます。手順は以下のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// ドキュメントを読み込む
Document doc = new Document("Document.docx");

// OoxmlSaveOptionsを作成し、圧縮レベルを設定する
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// 指定した圧縮レベルでドキュメントを保存します
doc.save("FastCompressionDoc.docx", saveOptions);
```

Aspose.Words for Java を使用してドキュメントを OOXML 形式で保存する際に使用できる主要なオプションと設定の一部をご紹介します。必要に応じて、さらに多くのオプションを試して、ドキュメントの保存プロセスをカスタマイズしてください。

## Aspose.Words for Java でドキュメントを OOXML 形式で保存するための完全なソースコード

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

この包括的なガイドでは、Aspose.Words for Java を使用してドキュメントを OOXML 形式で保存する方法を詳しく説明しました。ドキュメントをパスワードで暗号化したり、特定の OOXML 標準に準拠させたり、ドキュメントのプロパティを更新したり、従来の制御文字を保持したり、圧縮レベルを調整したりする必要がある場合でも、Aspose.Words はさまざまなニーズに応える多彩なツールセットを提供します。

## よくある質問

### パスワードで保護されたドキュメントからパスワード保護を削除するにはどうすればよいですか?

パスワードで保護された文書のパスワード保護を解除するには、正しいパスワードで文書を開き、保存オプションでパスワードを指定せずに保存します。これにより、文書はパスワード保護なしで保存されます。

### ドキュメントを OOXML 形式で保存するときにカスタム プロパティを設定できますか?

はい、OOXML形式で保存する前に、ドキュメントのカスタムプロパティを設定できます。 `BuiltInDocumentProperties` そして `CustomDocumentProperties` 著者、タイトル、キーワード、カスタム プロパティなどのさまざまなプロパティを設定するクラス。

### ドキュメントを OOXML 形式で保存する場合のデフォルトの圧縮レベルは何ですか?

Aspose.Words for Javaを使用してOOXML形式でドキュメントを保存する場合のデフォルトの圧縮レベルは `NORMAL`圧縮レベルは次のように変更できます。 `SUPER_FAST` または `MAXIMUM` 必要に応じて。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}