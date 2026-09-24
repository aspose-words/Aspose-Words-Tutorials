---
date: 2025-12-27
description: Aspose.Words for JavaでLoadOptionsを設定する方法を学び、テンポラリフォルダーの指定、Wordバージョンの設定、メタファイルをPNGに変換、シェイプを数式に変換する方法を習得し、柔軟な文書処理を実現します。
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for JavaでLoadOptionsを設定する方法
url: /ja/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for JavaでLoadOptionsを設定する方法

このチュートリアルでは、Aspose.Words for Java を使用するさまざまな実務シナリオにおいて **LoadOptionsの設定方法** を順を追って解説します。LoadOptions を使用すると、ドキュメントの開き方を細かく制御できます。たとえば、ダーティフィールドの更新、暗号化ファイルの取り扱い、シェイプを Office Math に変換、または一時データの保存場所を指定することが可能です。最後まで読むと、アプリケーションの正確な要件に合わせてロード動作をカスタマイズできるようになります。

## クイック回答
- **LoadOptionsとは？** Aspose.Words がドキュメントをロードする方法に影響を与える構成オブジェクトです。  
- **ロード中にフィールドを更新できますか？** はい—`setUpdateDirtyFields(true)` を設定します。  
- **パスワードで保護されたファイルを開くには？** パスワードを `LoadOptions` コンストラクタに渡します。  
- **一時フォルダーを変更できますか？** `setTempFolder("path")` を使用します。  
- **どのメソッドがシェイプをOffice Mathに変換しますか？** `setConvertShapeToOfficeMath(true)`。

## LoadOptionsを使用する理由
LoadOptions を使用すると、ロード後の処理ステップを回避でき、メモリ使用量を削減し、ドキュメントが必要通りに解釈されることを保証できます。たとえば、ロード時にメタファイルを PNG に変換すれば後続のラスタライズ問題を防げますし、MS Word のバージョンを指定することでレガシーファイルのレイアウト忠実度を保てます。

## 前提条件
- Java 17 以降  
- Aspose.Words for Java（最新バージョン）  
- 本番環境で使用する有効な Aspose ライセンス  

## ステップバイステップガイド

### ダーティフィールドの更新

ドキュメントに編集済みだが更新されていないフィールドが含まれている場合、ロード時に Aspose.Words に自動で更新させることができます。

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*`setUpdateDirtyFields(true)` の呼び出しにより、ダーティフィールドはドキュメントが開かれた瞬間に再計算されます。*

### 暗号化ドキュメントのロード

ソースファイルがパスワードで保護されている場合、`LoadOptions` インスタンスを作成するときにパスワードを提供します。別形式で保存する際に新しいパスワードを設定することも可能です。

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### シェイプをOffice Mathに変換

一部のレガシードキュメントは数式を描画シェイプとして保存しています。このオプションを有効にすると、シェイプがネイティブな Office Math オブジェクトに変換され、後で編集しやすくなります。

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### MS Word バージョンの設定

対象となる Word バージョンを指定すると、特に古いファイル形式を扱う際に、ライブラリが適切な描画ルールを選択できるようになります。

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### 一時フォルダーの使用

大容量ドキュメントは一時ファイル（例: 画像抽出時）を生成することがあります。これらのファイルを任意のフォルダーに誘導できるため、サンドボックス環境で便利です。

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### 警告コールバック

ロード中に Aspose.Words は警告（例: 未対応機能）を発生させることがあります。コールバックを実装することで、これらのイベントをログに記録したり、適切に対処したりできます。

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### メタファイルをPNGに変換

WMF などのメタファイルはロード時に PNG にラスタライズでき、プラットフォーム間で一貫した描画が保証されます。

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Aspose.Words for JavaでLoad Optionsを使用する完全なサンプルコード

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## 一般的な使用例とヒント
- **バッチ変換パイプライン** – `setTempFolder` とスケジュールジョブを組み合わせ、システムの一時ディレクトリを埋めることなく数百ファイルを処理します。  
- **レガシードキュメントの移行** – `setMswVersion` と `setConvertShapeToOfficeMath` を併用し、古い技術文書を数式を保持したまま最新フォーマットに変換します。  
- **安全なドキュメント処理** – `loadEncryptedDocument` と `OdtSaveOptions` を組み合わせ、別形式で新しいパスワードで再暗号化します。  

## よくある質問

**Q: ドキュメントロード時の警告はどのように処理すればよいですか？**  
A: カスタム `IWarningCallback`（*警告コール の例を参照）を実装し、`loadOptions.setWarningCallback(...)` で登録します。これにより、警告の重大度に応じてログ記録、無視、または中止が可能です。

**Q: ドキュメントロード時にシェイプを Office Math オブジェクトに変換できますか？**  
A: はい—`Document` を構築する前に `loadOptions.setConvertShapeToOfficeMath(true)` を呼び出します。ライブラリは互換性のあるシェイプを自動的にネイティブな Office Math オブジェクトに置き換えます。

**Q: ドキュメントロード時に MS Word バージョンを指定するには？**  
A: `loadOptions.setMswVersion(MsWordVersion.WORD_2010)`（または他の enum 値）を使用して、Aspose.Words に適用すべき Word バージョンの描画ルールを指示します。

**Q: LoadOptions の `setTempFolder` メソッドの目的は何ですか？**  
A: ロード中に生成されるすべての一時ファイル（抽出された画像など）を、制御可能なフォルダーへ誘導します。システムの一時ディレクトリが制限された環境で特に重要です。

**Q: WMF などのメタファイルをロード時に PNG に変換できますか？**  
A: もちろんです—`loadOptions.setConvertMetafilesToPng(true)` を有効にすれば、ラスタ画像が PNG として保存され、最新ビューアとの互換性が向上します。

## 結論

**LoadOptionsの設定方法** に関する重要なテクニックを網羅しました。ダーティフィールドの更新、暗号化ファイルの取り扱い、シェイプ変換、Word バージョン指定、一時ストレージの指定など、これらのオプションを活用すれば、さまざまな入力シナリオに適応できる堅牢で高性能なドキュメント処理パイプラインを構築できます。

---

**最終更新日:** 2025-12-27  
**テスト環境:** Aspose.Words for Java 24.11  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}