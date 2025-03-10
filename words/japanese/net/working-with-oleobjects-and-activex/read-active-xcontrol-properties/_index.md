---
title: Word ファイルから Active XControl プロパティを読み取る
linktitle: Word ファイルから Active XControl プロパティを読み取る
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word ファイルから ActiveX コントロールのプロパティを読み取る方法をステップ バイ ステップ ガイドで学習します。ドキュメント自動化スキルを強化します。
weight: 10
url: /ja/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word ファイルから Active XControl プロパティを読み取る

## 導入

今日のデジタル時代では、自動化が生産性向上の鍵となります。ActiveX コントロールを含む Word 文書で作業している場合、さまざまな目的でそのプロパティを読み取る必要がある場合があります。チェックボックスやボタンなどの ActiveX コントロールには重要なデータが保持されている場合があります。Aspose.Words for .NET を使用すると、このデータをプログラムで効率的に抽出し、操作できます。

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NETライブラリ:以下からダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. Visual Studio または任意の C# IDE: コードを記述して実行します。
3. ActiveX コントロールを含む Word 文書: たとえば、「ActiveX controls.docx」。
4. C# の基礎知識: この手順を実行するには、C# プログラミングの知識が必要です。

## 名前空間のインポート

まず、Aspose.Words for .NET を操作するために必要な名前空間をインポートしましょう。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## ステップ1: Word文書を読み込む

まず、ActiveX コントロールを含む Word 文書を読み込む必要があります。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## ステップ 2: プロパティを保持する文字列を初期化する

次に、ActiveX コントロールのプロパティを格納するために空の文字列を初期化します。

```csharp
string properties = "";
```

## ステップ3: ドキュメント内の図形を反復処理する

ActiveX コントロールを見つけるには、ドキュメント内のすべての図形を反復処理する必要があります。

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // ActiveXコントロールを処理する
    }
}
```

## ステップ4: ActiveXコントロールからプロパティを抽出する

ループ内で、コントロールが Forms2OleControl であるかどうかを確認します。そうである場合は、コントロールをキャストしてプロパティを抽出します。

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## ステップ5: ActiveXコントロールの合計数を数える

すべての図形を反復処理した後、見つかった ActiveX コントロールの合計数をカウントします。

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## ステップ6: プロパティを表示する

最後に、抽出されたプロパティをコンソールに出力します。

```csharp
Console.WriteLine("\n" + properties);
```

## 結論

これで完了です。Aspose.Words for .NET を使用して Word 文書から ActiveX コントロールのプロパティを読み取る方法を学習しました。このチュートリアルでは、文書の読み込み、図形の反復処理、ActiveX コントロールからのプロパティの抽出について説明しました。これらの手順に従うことで、Word 文書からの重要なデータの抽出を自動化し、ワークフローの効率を高めることができます。

## よくある質問

### Word 文書の ActiveX コントロールとは何ですか?
ActiveX コントロールは、チェックボックス、ボタン、テキスト フィールドなど、Word 文書に埋め込まれたインタラクティブ オブジェクトであり、フォームの作成やタスクの自動化に使用されます。

### Aspose.Words for .NET を使用して ActiveX コントロールのプロパティを変更できますか?
はい、Aspose.Words for .NET を使用すると、ActiveX コントロールのプロパティをプログラムで変更できます。

### Aspose.Words for .NET は無料で使用できますか?
 Aspose.Words for .NETは無料トライアルを提供していますが、継続して使用するにはライセンスを購入する必要があります。無料トライアルは[ここ](https://releases.aspose.com/).

### Aspose.Words for .NET を C# 以外の他の .NET 言語で使用できますか?
はい、Aspose.Words for .NET は、VB.NET や F# を含むあらゆる .NET 言語で使用できます。

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?
詳細なドキュメントは以下をご覧ください[ここ](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
