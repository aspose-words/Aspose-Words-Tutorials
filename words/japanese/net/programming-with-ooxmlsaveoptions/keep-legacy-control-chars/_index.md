---
title: 従来の制御文字を保持する
linktitle: 従来の制御文字を保持する
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書内の従来の制御文字を保持する方法を学習します。
weight: 10
url: /ja/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 従来の制御文字を保持する

## 導入

Word 文書内の奇妙で目に見えない制御文字に困惑したことはありませんか? それらは、書式設定や機能を台無しにする小さな隠れたグレムリンのようなものです。幸いなことに、Aspose.Words for .NET には、文書を保存するときにこれらの従来の制御文字をそのまま維持する便利な機能があります。このチュートリアルでは、Aspose.Words for .NET を使用してこれらの制御文字を管理する方法について詳しく説明します。手順を 1 つ 1 つ説明し、すべての詳細を理解できるようにします。準備はできましたか? さあ、始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET: ダウンロードしてインストールする[ここ](https://releases.aspose.com/words/net/).
2. 有効なAsposeライセンス: 一時ライセンスを取得できます[ここ](https://purchase.aspose.com/temporary-license/).
3. 開発環境: Visual Studio または .NET をサポートするその他の IDE。
4. C# の基礎知識: C# プログラミング言語に精通していると役立ちます。

## 名前空間のインポート

コードを記述する前に、必要な名前空間をインポートする必要があります。C# ファイルの先頭に次の行を追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: プロジェクトの設定

まず、Visual Studio (またはお好みの IDE) でプロジェクトを設定する必要があります。 

1. 新しい C# プロジェクトを作成する: Visual Studio を開き、新しい C# コンソール アプリケーション プロジェクトを作成します。
2. Aspose.Words for .NET をインストールします。NuGet パッケージ マネージャーを使用して Aspose.Words for .NET をインストールします。ソリューション エクスプローラーでプロジェクトを右クリックし、[NuGet パッケージの管理] を選択して、「Aspose.Words」を検索し、インストールします。

## ステップ2: ドキュメントを読み込む

次に、従来の制御文字を含む Word 文書を読み込みます。

1. ドキュメント パスを指定します。ドキュメント ディレクトリへのパスを設定します。
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. ドキュメントをロードします。`Document`ドキュメントを読み込むためのクラス。

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## ステップ3: 保存オプションを設定する

ここで、従来の制御文字をそのまま維持するように保存オプションを構成しましょう。

1. 保存オプションの作成: インスタンスを初期化する`OoxmlSaveOptions`そして、`KeepLegacyControlChars`財産に`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## ステップ4: ドキュメントを保存する

最後に、設定した保存オプションを使用してドキュメントを保存します。

1. 文書を保存する:`Save`方法の`Document`指定された保存オプションでドキュメントを保存するクラス。

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## 結論

これで完了です。これらの手順に従うことで、Aspose.Words for .NET で Word 文書を操作するときに、従来の制御文字が保持されることが保証されます。この機能は、特に制御文字が重要な役割を果たす複雑な文書を扱うときに役立ちます。 

## よくある質問

### レガシー制御文字とは何ですか?

レガシー制御文字は、書式設定とレイアウトを制御するために古いドキュメントで使用される非印刷文字です。

### これらの制御文字を保持せずに削除することはできますか?

はい、必要に応じて Aspose.Words for .NET を使用してこれらの文字を削除または置換できます。

### この機能は Aspose.Words for .NET のすべてのバージョンで使用できますか?

この機能は最新バージョンで利用できます。すべての機能にアクセスするには、必ず最新バージョンを使用してください。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?

はい、有効なライセンスが必要です。評価目的で一時的なライセンスを取得できます。[ここ](https://purchase.aspose.com/temporary-license/).

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?

詳細なドキュメントは以下をご覧ください[ここ](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
