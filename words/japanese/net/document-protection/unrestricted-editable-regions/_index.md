---
title: Word 文書内の無制限の編集可能領域
linktitle: Word 文書内の無制限の編集可能領域
second_title: Aspose.Words ドキュメント処理 API
description: この包括的なステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書に制限のない編集可能な領域を作成する方法を学習します。
weight: 10
url: /ja/net/document-protection/unrestricted-editable-regions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書内の無制限の編集可能領域

## 導入

Word 文書を保護しながら、特定の部分を編集可能にしたい場合、このガイドは最適です。このガイドでは、Aspose.Words for .NET を使用して Word 文書に制限のない編集可能な領域を設定する手順を説明します。前提条件から詳細な手順まですべてをカバーし、スムーズな操作を実現します。準備はできましたか? さあ、始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET: まだダウンロードしていない場合はダウンロードしてください[ここ](https://releases.aspose.com/words/net/).
2. 有効なAsposeライセンス: 一時ライセンスを取得できます[ここ](https://purchase.aspose.com/temporary-license/).
3. Visual Studio: 最新バージョンであれば問題なく動作するはずです。
4. C# と .NET の基本的な知識: コードを理解するのに役立ちます。

準備が整いましたので、楽しい部分に進みましょう。

## 名前空間のインポート

Aspose.Words for .NET の使用を開始するには、必要な名前空間をインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Editing;
```

## ステップ1: プロジェクトの設定

まず最初に、Visual Studio で新しい C# プロジェクトを作成しましょう。

1. Visual Studio を開く: まず、Visual Studio を開いて、新しいコンソール アプリ プロジェクトを作成します。
2. Aspose.Words をインストールします。NuGet パッケージ マネージャーを使用して Aspose.Words をインストールします。パッケージ マネージャー コンソールで次のコマンドを実行すると、これを実行できます。
   ```sh
   Install-Package Aspose.Words
   ```

## ステップ2: ドキュメントの読み込み

次に、保護したい文書を読み込みます。ディレクトリに Word 文書が準備されていることを確認してください。

1. ドキュメント ディレクトリを設定する: ドキュメント ディレクトリへのパスを定義します。
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```
2. ドキュメントを読み込む:`Document` Word 文書を読み込むためのクラス。
   ```csharp
   Document doc = new Document(dataDir + "Document.docx");
   ```

## ステップ3: ドキュメントを保護する

次に、ドキュメントを読み取り専用に設定します。これにより、パスワードなしでは変更ができなくなります。

1.  DocumentBuilderの初期化: インスタンスを作成する`DocumentBuilder`ドキュメントに変更を加えます。
   ```csharp
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```
2. 保護レベルの設定: パスワードを使用してドキュメントを保護します。
   ```csharp
   doc.Protect(ProtectionType.ReadOnly, "MyPassword");
   ```
3. 読み取り専用テキストの追加: 読み取り専用となるテキストを挿入します。
   ```csharp
   builder.Writeln("Hello world! Since we have set the document's protection level to read-only, we cannot edit this paragraph without the password.");
   ```

## ステップ4: 編集可能な範囲を作成する

ここで魔法が起こります。全体的に読み取り専用保護がかかっているにもかかわらず、編集可能なセクションをドキュメント内に作成します。

1. 編集可能範囲の開始: 編集可能範囲の開始を定義します。
   ```csharp
   EditableRangeStart edRangeStart = builder.StartEditableRange();
   ```
2. 編集可能な範囲オブジェクトの作成:`EditableRange`オブジェクトは自動的に作成されます。
   ```csharp
   EditableRange editableRange = edRangeStart.EditableRange;
   ```
3. 編集可能なテキストを挿入: 編集可能な範囲内にテキストを追加します。
   ```csharp
   builder.Writeln("Paragraph inside first editable range");
   ```

## ステップ5: 編集可能な範囲を閉じる

編集可能な範囲は終了点がないと完了しません。次に終了点を追加しましょう。

1. 編集可能範囲の終了: 編集可能範囲の終了を定義します。
   ```csharp
   EditableRangeEnd edRangeEnd = builder.EndEditableRange();
   ```
2. 範囲外に読み取り専用テキストを追加する: 保護を示すために、編集可能な範囲外にテキストを挿入します。
   ```csharp
   builder.Writeln("This paragraph is outside any editable ranges, and cannot be edited.");
   ```

## ステップ6: ドキュメントを保存する

最後に、保護と編集可能な領域を適用したドキュメントを保存しましょう。

1. ドキュメントを保存する:`Save`変更したドキュメントを保存する方法。
   ```csharp
   doc.Save(dataDir + "DocumentProtection.UnrestrictedEditableRegions.docx");
   ```

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書に制限のない編集可能な領域を作成することができました。この機能は、文書の特定の部分をそのままにして、他の部分を編集する必要がある共同作業環境で非常に役立ちます。 

より複雑なシナリオやさまざまな保護レベルを試して、Aspose.Wordsを最大限に活用してください。質問や問題がある場合は、[ドキュメント](https://reference.aspose.com/words/net/)または連絡する[サポート](https://forum.aspose.com/c/words/8).

## よくある質問

### つのドキュメントに複数の編集可能な領域を設定できますか?
はい、ドキュメントの異なる部分で編集範囲を開始および終了することにより、複数の編集領域を作成できます。

### Aspose.Words では他にどのような保護タイプが利用できますか?
Aspose.Words は、AllowOnlyComments、AllowOnlyFormFields、NoProtection などのさまざまな保護タイプをサポートしています。

### ドキュメントの保護を解除することは可能ですか?
はい、保護を解除するには`Unprotect`方法と正しいパスワードを入力してください。

### セクションごとに異なるパスワードを指定できますか?
いいえ、ドキュメント レベルの保護では、ドキュメント全体に 1 つのパスワードが適用されます。

### Aspose.Words のライセンスを申請するにはどうすればよいですか?
ライセンスは、ファイルまたはストリームからロードして適用できます。詳細な手順については、ドキュメントを確認してください。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
