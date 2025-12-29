---
date: 2025-12-29
description: Aspose.Words for Java の保存オプションを使用して、パスワードで docx を暗号化する方法を学びましょう。OOXML
  ファイルを簡単に保護、最適化、カスタマイズできます。
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用して DOCX をパスワードで暗号化する方法
url: /ja/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用してパスワードで DOCX を暗号化する方法

このガイドでは、Aspose.Words for Java を使用して OOXML 形式でドキュメントを保存する際に **パスワードで docx を暗号化する方法** を紹介します。機密レポートの保護や契約書ドラフトの安全確保など、以下の手順でパスワード保護の適用方法やその他の OOXML 保存オプションの細かい調整方法を確認できます。

## Quick Answers
- **DOCX ファイルをパスワードで暗号化できますか？** はい、保存前に `OoxmlSaveOptions.setPassword()` を使用します。  
- **OOXML 保存設定を制御するクラスはどれですか？** `OoxmlSaveOptions`（Aspose.Words の一部）。  
- **パスワード保護にライセンスは必要ですか？** 本番環境で使用する場合は有効な Aspose.Words ライセンスが必要です。  
- **暗号化とコンプライアンス設定を組み合わせられますか？** もちろんです。同じ `OoxmlSaveOptions` インスタンスで `setPassword` と `setCompliance` の両方を設定できます。  
- **利用できる圧縮レベルは何ですか？** `CompressionLevel` を通じて `NORMAL`、`SUPER_FAST`、`MAXIMUM` が利用可能です。

## “encrypt docx with password” とは？
DOCX ファイルを暗号化するとは、ファイルの内容が暗号化された形で保存され、正しいパスワードを入力しない限り開くことができない状態を指します。これにより、機密情報への不正アクセスを防ぎつつ、パスワードを入力すれば標準の Word ツールでファイルを開くことができます。

## なぜ Aspose.Words の保存オプションで暗号化を行うのか？
Aspose.Words は **aspose words save options** と呼ばれる豊富な保存オプションを提供し、暗号化だけでなくコンプライアンスレベル、圧縮、レガシ文字の取り扱いなどを Java コードだけで制御できます。これにより、手動の後処理やサードパーティツールが不要になります。

## 前提条件
- Java Development Kit (JDK 8 以上)  
- プロジェクトに追加された Aspose.Words for Java ライブラリ（Maven/Gradle または JAR）  
- 本番環境用の有効な Aspose.Words ライセンス（評価版はオプション）

## パスワード暗号化付きでドキュメントを保存する

OOXML 形式で保存する際に、パスワードでドキュメントを暗号化できます。手順は以下の通りです。

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

## OOXML コンプライアンスの設定

ドキュメント保存時に OOXML コンプライアンスレベルを指定できます。たとえば、ISO 29500:2008 (Strict) に設定する例は次のとおりです。

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

## 「最終保存日時」プロパティの更新

保存時にドキュメントの「最終保存日時」プロパティを更新するかどうか選択できます。設定方法は以下の通りです。

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

ドキュメントにレガシ制御文字が含まれている場合、保存時にそれらを保持するかどうか選択できます。設定例は次のとおりです。

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

## 圧縮レベルの設定

保存時の圧縮レベルを調整できます。たとえば、最小圧縮の **SUPER_FAST** に設定する例は以下です。

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

これらは Aspose.Words for Java を使用して OOXML 形式でドキュメントを保存する際に利用できる主要なオプションと設定の一部です。さらに多くのオプションを探求し、必要に応じてドキュメント保存プロセスをカスタマイズしてください。

## OOXML 形式でドキュメントを保存するための完全なサンプルコード

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

本包括的ガイドでは、**パスワードで docx を暗号化する方法** と、Aspose.Words for Java を使用した OOXML 保存オプションの細かい調整方法を解説しました。機密コンテンツの保護、厳格な ISO コンプライアンスへの対応、レガシ文字の保持、圧縮の制御など、`OoxmlSaveOptions` API を通じて粒度の高い制御が可能です。

## Frequently Asked Questions

**Q: パスワードで保護されたドキュメントのパスワード保護を解除するには？**  
A: 正しいパスワードでドキュメントを開き、`setPassword` を呼び出さずに再度保存します。新しいファイルは保護が解除された状態になります。

**Q: OOXML 形式で保存する際にカスタムプロパティを設定できますか？**  
A: はい。`Document` オブジェクトの `BuiltInDocumentProperties` または `CustomDocumentProperties` を使用して、`save` を呼び出す前に設定できます。

**Q: OOXML 形式でドキュメントを保存する際のデフォルト圧縮レベルは？**  
A: デフォルトは `NORMAL` です。速度重視なら `SUPER_FAST`、サイズ削減なら `MAXIMUM` に切り替えられます。

**Q: aspose words save options は古い Word バージョンでも動作しますか？**  
A: はい。`MsWordVersion` とコンプライアンス設定を調整することで、Word 2007‑2019 までのバージョンに対応できます。

**Q: 複数の保存オプションを一度に組み合わせることは可能ですか？**  
A: もちろんです。`OoxmlSaveOptions` インスタンスを1つ作成し、必要なすべてのプロパティ（パスワード、コンプライアンス、圧縮など）を設定してから `doc.save()` に渡します。

---

**最終更新日:** 2025-12-29  
**テスト環境:** Aspose.Words for Java 24.12  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}