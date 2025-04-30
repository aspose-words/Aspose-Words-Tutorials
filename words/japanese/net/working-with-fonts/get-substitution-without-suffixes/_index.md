---
"description": "Aspose.Words for .NET でサフィックスなしでフォント置換を管理する方法を学びましょう。ステップバイステップのガイドに従って、ドキュメントを常に完璧な状態に仕上げましょう。"
"linktitle": "接尾辞なしの置換を取得する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "接尾辞なしの置換を取得する"
"url": "/ja/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 接尾辞なしの置換を取得する

## 導入

Aspose.Words for .NET を使ったフォント置換の管理に関する包括的なガイドへようこそ。ドキュメントでフォントが正しく表示されないことにお困りの方は、ぜひこのガイドをご覧ください。このチュートリアルでは、サフィックスなしでフォント置換を効率的に行う方法を、ステップバイステップで解説します。

## 前提条件

チュートリアルに進む前に、次のものを用意してください。

- C# の基本知識: C# プログラミングを理解すると、手順の実行と実装が容易になります。
- Aspose.Words for .NET ライブラリ: ライブラリを以下のサイトからダウンロードしてインストールします。 [ダウンロードリンク](https://releases。aspose.com/words/net/).
- 開発環境: コードを記述して実行するための Visual Studio などの開発環境をセットアップします。
- サンプル文書: サンプル文書（例： `Rendering.docx`) を使用します。

## 名前空間のインポート

まず、Aspose.Words によって提供されるクラスとメソッドにアクセスするために必要な名前空間をインポートする必要があります。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## ステップ1: ドキュメントディレクトリを定義する

まず、ドキュメントが保存されているディレクトリを指定します。これにより、作業したいドキュメントを見つけやすくなります。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: 置換警告ハンドラを設定する

次に、ドキュメント処理中にフォントの置換が発生した際に通知する警告ハンドラを設定する必要があります。これは、フォントに関する問題を検出して対処するために不可欠です。

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## ステップ3: カスタムフォントソースを追加する

このステップでは、Aspose.Words が正しいフォントを見つけて使用できるように、カスタムフォントソースを追加します。これは、特定のフォントをカスタムディレクトリに保存している場合に特に便利です。

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

このコードでは:
- 現在のフォントソースを取得し、新しいフォントを追加します `FolderFontSource` カスタムフォントディレクトリ（`C:\\MyFonts\\`）。
- 次に、この新しいリストを使用してフォント ソースを更新します。

## ステップ4: ドキュメントを保存する

最後に、フォント置換設定を適用した後、ドキュメントを保存します。このチュートリアルでは、PDF形式で保存します。

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## ステップ5: 警告ハンドラクラスを作成する

警告を効果的に処理するには、 `IWarningCallback` インターフェース。このクラスはフォント置換の警告をキャプチャして記録します。

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

このクラスでは:
- その `Warning` メソッドは、フォントの置換に関連する警告をキャプチャします。
- その `FontWarnings` コレクションには、さらに検査したりログに記録したりするためにこれらの警告が保存されます。

## 結論

Aspose.Words for .NET を使って、サフィックスなしのフォント置換処理をマスターしました。この知識があれば、システムで利用可能なフォントの種類に関わらず、ドキュメントの見た目を意図した通りに維持できます。Aspose.Words のパワーを最大限に活用するために、様々な設定やソースを試し続けてください。

## よくある質問

### 複数のカスタム ディレクトリのフォントを使用するにはどうすればよいですか?

複数追加できます `FolderFontSource` インスタンスを `fontSources` それに応じてフォント ソースをリストし、更新します。

### Aspose.Words for .NET の無料試用版はどこからダウンロードできますか?

無料トライアルは以下からダウンロードできます。 [Aspose無料トライアルページ](https://releases。aspose.com/).

### 複数の種類の警告を処理できますか？ `IWarningCallback`？

はい、 `IWarningCallback` インターフェースを使用すると、フォントの置換だけでなく、さまざまな種類の警告を処理できます。

### Aspose.Words のサポートはどこで受けられますか?

サポートについては、 [Aspose.Words サポートフォーラム](https://forum。aspose.com/c/words/8).

### 一時ライセンスを購入することは可能ですか？

はい、臨時免許証は取得できます。 [一時ライセンスページ](https://purchase。aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}