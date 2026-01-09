---
date: 2026-01-09
description: Aspose.Words for Java を使用して、OOXML 形式でドキュメントを保存する際に、パスワードで docx を暗号化し、圧縮レベルを変更する方法を学びます。
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: パスワードでdocxを暗号化 – Aspose.Words JavaによるOOXML保存
url: /ja/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# パスワードで docx を暗号化 – Aspose.Words Java で OOXML として保存

## Aspose.Words for Java でドキュメントを OOXML 形式で保存する概要

このガイドでは、**パスワードで docx を暗号化**し、Aspose.Words for Java を使用して OOXML 形式でドキュメントを保存する方法を学びます。OOXML（Office Open XML）は、Microsoft Word や多くのオフィスアプリケーションで使用されている最新のファイル形式です。パスワード保護、コンプライアンスレベル、プロパティ更新、レガシ文字の取り扱い、**圧縮レベルの変更方法**といった最も一般的なオプションを順に解説し、出力を正確にカスタマイズできるようにします。

## クイック回答
- **Word ファイルを保護するには？** 保存前に `OoxmlSaveOptions.setPassword("yourPassword")` を使用します。  
- **どの OOXML コンプライアンスレベルを選択すべき？** 最新の Office バージョンとの互換性を最大化するには ISO 29500 2008 Strict を選びます。  
- **レガシ制御文字を保持できますか？** はい、`setKeepLegacyControlChars(true)` を有効にします。  
- **圧縮レベルはどう変更しますか？** 必要に応じて `setCompressionLevel(CompressionLevel.SUPER_FAST)` または `MAXIMUM` を設定します。  
- **これらのオプションはファイルサイズに影響しますか？** 圧縮レベルとレガシ制御文字の取り扱いは、最終的な .docx のサイズに顕著な変化をもたらすことがあります。

## 「パスワードで docx を暗号化」とは？
DOCX ファイルを暗号化するということは、AES‑256 暗号化で保存され、Word や互換ビューアで開く際にパスワードが必要になることを意味します。メール、クラウドストレージ、イントラネットポータルなどで機密情報を共有する際に不可欠です。

## OOXML 保存オプションを使用する理由
- **セキュリティ:** パスワード保護により不正アクセスを防止します。  
- **互換性:** コンプライアンス設定により、さまざまな Word バージョンでファイルが正しく動作します。  
- **パフォーマンス:** 圧縮を調整することで保存速度を向上させたり、ファイルサイズを削減したりできます。  
- **保存性:** レガシ制御文字を保持することで、古い文書を変換した際の忠実度が保たれます。

## 前提条件
- プロジェクトに Aspose.Words for Java ライブラリが追加されていること（Maven/Gradle または手動 JAR）。  
- Java 8 以上。  
- 処理対象となるソース文書（`.docx` または `.doc`）。

## パスワード暗号化でドキュメントを保存する

パスワードを指定しながら OOXML 形式でドキュメントを暗号化して保存できます。手順は以下の通りです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **プロのヒント:** 強力なパスワードを選び、安全に保管してください。暗号化されたファイルからパスワードを復元することはできません。

## OOXML コンプライアンスの設定

保存時に OOXML コンプライアンスレベルを指定できます。たとえば ISO 29500:2008（Strict）に設定する例は次のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## 「最終保存時刻」プロパティの更新

保存時にドキュメントの「最終保存時刻」プロパティを更新するかどうか選択できます。設定例は以下です。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## レガシ制御文字の保持

文書にレガシ制御文字が含まれている場合、保存時にそれらを保持するか選択できます。設定例は次のとおりです。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## OOXML 保存時の圧縮レベル変更方法

保存時に圧縮レベルを調整できます。たとえば最小圧縮の `SUPER_FAST` や、最小ファイルサイズを目指す `MAXIMUM` を設定する例は以下です。

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

これらは Aspose.Words for Java を使用して OOXML 形式でドキュメントを保存する際に利用できる主要なオプションと設定の一部です。さらに多くのオプションを探求し、必要に応じて保存プロセスをカスタマイズしてください。

## OOXML 形式でドキュメントを保存する完全なサンプルコード（Aspose.Words for Java）

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

本包括的ガイドでは、**パスワードで docx を暗号化**し、Aspose.Words for Java を使用して OOXML 形式でドキュメントを保存する方法を解説しました。ファイル保護、厳格な OOXML コンプライアンスの確保、ドキュメントプロパティの更新、レガシ制御文字の保持、**圧縮レベルの変更**のいずれが必要でも、Aspose.Words は柔軟なツールセットを提供します。

## FAQ（よくある質問）

**Q: パスワードで保護された文書からパスワード保護を解除するには？**  
A: 正しいパスワードで文書を開き、`OoxmlSaveOptions` でパスワードを指定せずに保存します。これにより保護なしのコピーが作成されます。

**Q: OOXML 形式で保存する際にカスタムプロパティを設定できますか？**  
A: はい。`Document` オブジェクトの `BuiltInDocumentProperties` と `CustomDocumentProperties` を使用し、`save()` を呼び出す前に設定します。

**Q: OOXML 形式で保存する際のデフォルト圧縮レベルは？**  
A: デフォルトは `CompressionLevel.NORMAL` です。速度重視なら `SUPER_FAST`、最小サイズを狙うなら `MAXIMUM` に切り替えられます。

**Q: `keepLegacyControlChars` を有効にすると、最新の Word バージョンとの互換性に影響しますか？**  
A: 最新の Word はレガシ制御文字を含むファイルを開くことができますが、古い機能の一部が異なる表示になる可能性があります。元のコンテンツを正確に保持する必要がある場合にのみ使用してください。

**Q: 複数の保存オプション（例：パスワード + 圧縮）を同時に設定できますか？**  
A: もちろん可能です。`OoxmlSaveOptions` インスタンスにすべての必要なプロパティを設定し、`doc.save()` に渡すだけです。

---

**最終更新日:** 2026-01-09  
**テスト環境:** Aspose.Words for Java 24.12  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}