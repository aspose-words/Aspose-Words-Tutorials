---
title: 新しい署名欄の作成と署名
linktitle: 新しい署名欄の作成と署名
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップのチュートリアルでは、Aspose.Words for .NET を使用して Word 文書に署名欄を作成し、デジタル署名する方法を学習します。文書の自動化に最適です。
weight: 10
url: /ja/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 新しい署名欄の作成と署名

## 導入

こんにちは! Word 文書に署名欄を追加してデジタル署名する必要があります。難しそうに聞こえますか? まったくそんなことはありません! Aspose.Words for .NET を使用すると、わずか数行のコードでこれをシームレスに実現できます。このチュートリアルでは、環境の設定から新しい署名で文書を保存するまでのプロセス全体を順を追って説明します。準備はできましたか? さあ始めましょう!

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。
1.  Aspose.Words for .NET - 次のようなことができます[ここからダウンロード](https://releases.aspose.com/words/net/).
2. .NET 開発環境 - Visual Studio を強くお勧めします。
3. 署名する文書 - 簡単な Word 文書を作成するか、既存の文書を使用します。
4. 証明書ファイル - これはデジタル署名に必要です。`.pfx`ファイル。
5. 署名行の画像 - オプションで、署名用の画像ファイル。

## 名前空間のインポート

まず、必要な名前空間をインポートする必要があります。この手順は、Aspose.Words 機能を使用するための環境を設定するため、非常に重要です。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## ステップ1: ドキュメントディレクトリの設定

すべてのプロジェクトは良いスタートが必要です。ドキュメント ディレクトリへのパスを設定しましょう。ドキュメントはここに保存され、取得されます。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: 新しいドキュメントを作成する

次に、Aspose.Words を使用して新しい Word 文書を作成します。これが署名行を追加するキャンバスになります。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ3: 署名欄の挿入

ここで魔法が起こります。`DocumentBuilder`クラス。

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## ステップ4: 署名欄付きの文書を保存する

署名欄が配置されたら、文書を保存する必要があります。これは、署名に進む前の中間ステップです。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## ステップ5: 署名オプションの設定

次に、ドキュメントに署名するためのオプションを設定しましょう。これには、署名行 ID と使用する画像の指定が含まれます。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## ステップ6: 証明書の読み込み

デジタル署名には証明書が必要です。ここでは、ドキュメントの署名に使用する証明書ファイルを読み込みます。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## ステップ7: 文書に署名する

これが最後のステップです。`DigitalSignatureUtil`クラスを使用してドキュメントに署名します。署名されたドキュメントは新しい名前で保存されます。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## 結論

これで完了です。これらの手順により、新しい Word 文書を作成し、署名欄を追加し、Aspose.Words for .NET を使用してデジタル署名することができました。これは、文書の自動化を簡単にする強力なツールです。契約書、合意書、その他の正式な文書を扱う場合でも、この方法により、安全に署名および認証されます。

## よくある質問

### 署名欄に他の画像形式を使用できますか?
はい、PNG、JPG、BMP などのさまざまな画像形式を使用できます。

### 使用する必要があるか`.pfx` file for the certificate?
はい、`.pfx`ファイルは、証明書や秘密鍵などの暗号化情報を保存するための一般的な形式です。

### 1 つの文書に複数の署名行を追加できますか?
もちろんです! 署名ごとに挿入手順を繰り返すことで、複数の署名行を挿入できます。

### デジタル証明書を持っていない場合はどうなりますか?
信頼できる証明機関からデジタル証明書を取得するか、OpenSSL などのツールを使用してデジタル証明書を生成する必要があります。

### 文書内のデジタル署名を検証するにはどうすればよいですか?
署名された文書を Word で開き、署名の詳細に移動して、署名の信頼性と整合性を確認できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
