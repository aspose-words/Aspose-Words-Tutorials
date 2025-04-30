---
"description": "Aspose.Words for .NET を使用して Word 文書に OLE オブジェクトを挿入する方法を学びましょう。詳細なステップバイステップガイドに従って、シームレスにファイルを埋め込んでください。"
"linktitle": "Ole パッケージを使用して Word に Ole オブジェクトを挿入する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "Ole パッケージを使用して Word に Ole オブジェクトを挿入する"
"url": "/ja/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ole パッケージを使用して Word に Ole オブジェクトを挿入する

## 導入

Word文書にファイルを埋め込みたいと思ったことがあるなら、ここがまさにその場所です。ZIPファイル、Excelシート、その他どんなファイル形式でも、Word文書に直接埋め込めば非常に便利です。まるで文書の中に秘密の小部屋があり、そこに様々な宝物を隠しておけるようなものです。今日は、Aspose.Words for .NETを使ってこれを実現する方法を解説します。Wordを使いこなす準備はできましたか？さあ、始めましょう！

## 前提条件

始める前に、以下のものを用意してください。

1. Aspose.Words for .NET: まだダウンロードしていない場合は、こちらからダウンロードしてください。 [ここ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の .NET 開発環境。
3. C# の基本的な理解: 専門家である必要はありませんが、C# の使い方を知っておくと役立ちます。
4. ドキュメント ディレクトリ: ドキュメントを保存および取得できるフォルダー。

## 名前空間のインポート

まずは名前空間を整理しましょう。プロジェクトには以下の名前空間を含める必要があります。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

簡単に理解できるように、これを簡単な手順に分解してみましょう。

## ステップ1：ドキュメントを設定する

真っ白なキャンバスを持つアーティストだと想像してみてください。まず、真っ白なキャンバス、つまりWord文書が必要です。設定方法は以下の通りです。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

このコードは、新しい Word 文書を初期化し、文書にコンテンツを挿入するために使用する DocumentBuilder を設定します。

## ステップ2: Oleオブジェクトを読み込む

次に、埋め込みたいファイルを読み込みます。これは、秘密の部屋に隠したい宝物を拾い上げるようなものだと考えてください。

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

この行は、ZIP ファイルからすべてのバイトを読み取り、バイト配列に保存します。

## ステップ3: Oleオブジェクトを挿入する

いよいよ魔法のパートです。ファイルをWord文書に埋め込みます。

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

ここでは、バイト配列からメモリストリームを作成し、 `InsertOleObject` メソッドを使用してドキュメントに埋め込みます。また、埋め込まれたオブジェクトのファイル名と表示名も設定します。

## ステップ4: ドキュメントを保存する

最後に、私たちの傑作を保存しましょう。

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

これにより、埋め込まれたファイルを含むドキュメントが指定されたディレクトリに保存されます。

## 結論

これで完了です！Aspose.Words for .NET を使って、Word 文書に OLE オブジェクトを埋め込むことができました。まるで、いつでもその魅力を解き放つことができる、隠れた宝石を文書の中に埋め込んだようなものです。このテクニックは、技術文書から動的なレポートまで、様々な用途で非常に役立ちます。 

## よくある質問

### この方法を使用して他のファイルタイプを埋め込むことはできますか?
はい、Excel シート、PDF、画像など、さまざまなファイル形式を埋め込むことができます。

### Aspose.Words のライセンスは必要ですか?
はい、有効な免許証が必要です。 [一時ライセンス](https://purchase.aspose.com/temporary-license/) 評価のため。

### OLE オブジェクトの表示名をカスタマイズするにはどうすればよいですか?
設定できるのは `DisplayName` の財産 `OlePackage` カスタマイズします。

### Aspose.Words は .NET Core と互換性がありますか?
はい、Aspose.Words は .NET Framework と .NET Core の両方をサポートしています。

### Word 文書内に埋め込まれた OLE オブジェクトを編集できますか?
いいえ、Word内でOLEオブジェクトを直接編集することはできません。ネイティブアプリケーションで開く必要があります。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}