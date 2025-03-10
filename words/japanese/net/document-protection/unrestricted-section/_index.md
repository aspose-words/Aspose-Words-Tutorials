---
title: Word 文書の制限なしセクション
linktitle: Word 文書の制限なしセクション
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドに従って、Aspose.Words for .NET を使用して Word 文書内の特定のセクションのロックを解除します。機密コンテンツを保護するのに最適です。
weight: 10
url: /ja/net/document-protection/unrestricted-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書の制限なしセクション

## 導入

こんにちは! Aspose.Words for .NET の世界に飛び込む準備はできていますか? 今日は、非常に実用的なことに取り組みます。Word 文書の特定のセクションのロックを解除しながら、他の部分を保護したままにする方法です。文書の一部のセクションを保護しながら、他のセクションは編集できるようにしておく必要がある場合は、このチュートリアルが役立ちます。さっそく始めましょう!

## 前提条件

細かい点に入る前に、必要なものがすべて揃っていることを確認してください。

-  Aspose.Words for .NET: まだお持ちでない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
- Visual Studio: またはその他の .NET 互換 IDE。
- C# の基本的な理解: C# に少し精通していれば、このチュートリアルを簡単に理解できるようになります。
-  Asposeライセンス:[無料トライアル](https://releases.aspose.com/)または[一時ライセンス](https://purchase.aspose.com/temporary-license/)テストに必要な場合。

## 名前空間のインポート

コーディングを開始する前に、C# プロジェクトに必要な名前空間がインポートされていることを確認してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

それでは、ステップごとに解説していきましょう。

## ステップ1: プロジェクトを設定する

### ドキュメントディレクトリを初期化する

まず最初に、ドキュメント ディレクトリへのパスを設定する必要があります。ここに Word ファイルが保存されます。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメントを保存する実際のパスを入力します。これは、ファイルが正しい場所に保存されることを保証するため、非常に重要です。

### 新しいドキュメントを作成する

次に、Aspose.Words を使用して新しいドキュメントを作成します。このドキュメントは、魔法を適用するキャンバスになります。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

の`Document`クラスは新しいドキュメントを初期化し、`DocumentBuilder`ドキュメントにコンテンツを簡単に追加するのに役立ちます。

## ステップ2: セクションを挿入する

### 保護されていないセクションを追加

まず、保護されない最初のセクションを追加してみましょう。

```csharp
builder.Writeln("Section 1. Unprotected.");
```

このコード行は、ドキュメントに「セクション 1. 保護されていません。」というテキストを追加します。簡単ですよね?

### 保護されたセクションを追加

次に、2 番目のセクションを追加し、最初のセクションと区切るためにセクション区切りを挿入します。

```csharp
builder.InsertBreak(BreakType.SectionBreakContinuous);
builder.Writeln("Section 2. Protected.");
```

の`InsertBreak`メソッドは連続したセクション区切りを挿入し、セクションごとに異なる設定を行うことを可能にします。

## ステップ3: ドキュメントを保護する

### ドキュメント保護を有効にする

文書を保護するために、`Protect`メソッド。このメソッドは、特に指定がない限り、フォーム フィールドのみが編集可能であることを保証します。

```csharp
doc.Protect(ProtectionType.AllowOnlyFormFields, "password");
```

ここでは、文書はパスワードで保護されており、フォームフィールドのみが編集可能です。`"password"`ご希望のパスワードを入力してください。

### 特定のセクションの保護を解除

デフォルトでは、すべてのセクションが保護されています。最初のセクションの保護を選択的にオフにする必要があります。

```csharp
doc.Sections[0].ProtectedForForms = false;
```

この行により、ドキュメントの最初のセクションは保護されず、残りのセクションは保護されます。

## ステップ4: ドキュメントを保存して読み込む

### ドキュメントを保存する

次に、保護設定を適用したドキュメントを保存します。

```csharp
doc.Save(dataDir + "DocumentProtection.UnrestrictedSection.docx");
```

指定されたディレクトリに文書を次の名前で保存します。`DocumentProtection.UnrestrictedSection.docx`.

### ドキュメントを読み込む

最後に、ドキュメントをロードして、すべてが正しく設定されていることを確認します。

```csharp
doc = new Document(dataDir + "DocumentProtection.UnrestrictedSection.docx");
```

この手順により、ドキュメントが適切に保存され、保護設定を失うことなく再読み込みできるようになります。

## 結論

これで完了です。これらの手順に従うことで、Aspose.Words for .NET を使用して、保護されたセクションと保護されていないセクションが混在する Word 文書を正常に作成できました。この方法は、文書の特定の部分をロックダウンし、他の部分は編集可能にする必要がある場合に非常に便利です。

## よくある質問

### 複数のセクションを保護できますか?
はい、必要に応じて複数のセクションを選択的に保護したり保護解除したりできます。

### ドキュメントを保存した後に保護タイプを変更することは可能ですか?
はい、ドキュメントを再度開き、必要に応じて保護設定を変更できます。

### Aspose.Words では他にどのような保護タイプが利用できますか?
 Aspose.Wordsは、以下の保護タイプをサポートしています。`ReadOnly`, `Comments` 、 そして`TrackedChanges`.

### パスワードなしで文書を保護できますか?
はい、パスワードを指定せずにドキュメントを保護することができます。

### セクションが保護されているかどうかを確認するにはどうすればよいですか?
確認するには`ProtectedForForms`セクションのプロパティを調べて、保護されているかどうかを判断します。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
