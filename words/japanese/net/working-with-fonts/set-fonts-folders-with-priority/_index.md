---
title: フォントフォルダを優先的に設定
linktitle: フォントフォルダを優先的に設定
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書でフォント フォルダーを優先的に設定する方法を学びます。このガイドでは、文書が常に完璧にレンダリングされることを保証します。
weight: 10
url: /ja/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォントフォルダを優先的に設定

## 導入

ドキュメント操作の世界では、カスタム フォント フォルダーを設定すると、ドキュメントがどこで表示されても完璧にレンダリングされるかどうかに大きな違いが生じます。今日は、Aspose.Words for .NET を使用して Word ドキュメントでフォント フォルダーを優先的に設定する方法について詳しく説明します。この包括的なガイドでは、各手順を順を追って説明し、プロセスを可能な限りスムーズにします。

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。簡単なチェックリストを以下に示します。

-  Aspose.Words for .NET: このライブラリをインストールする必要があります。まだインストールしていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio などの .NET 開発環境が動作していることを確認します。
- ドキュメントディレクトリ: ドキュメント用のディレクトリがあることを確認してください。例では、`"YOUR DOCUMENT DIRECTORY"`このパスのプレースホルダーとして。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これらの名前空間は、Aspose.Words によって提供されるクラスとメソッドにアクセスするために不可欠です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

それでは、フォント フォルダーを優先的に設定する手順を詳しく説明します。

## ステップ1: フォントソースを設定する

まず、フォント ソースを定義します。ここで、Aspose.Words にフォントを検索する場所を指定します。複数のフォント フォルダーを指定したり、優先順位を設定したりすることもできます。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

この例では、2 つのフォント ソースを設定しています。
- SystemFontSource: これは、システムにインストールされているすべてのフォントを含むデフォルトのフォント ソースです。
-  FolderFontSource: これはカスタムフォントフォルダです。`C:\\MyFonts\\` 。`true`パラメータは、このフォルダを再帰的にスキャンすることを指定します。`1`優先順位を設定します。

## ステップ2: ドキュメントを読み込む

次に、作業するドキュメントを読み込みます。ドキュメントが指定したディレクトリにあることを確認します。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

このコード行は、`Rendering.docx`ドキュメント ディレクトリから。

## ステップ3: 新しいフォント設定でドキュメントを保存する

最後に、ドキュメントを保存します。ドキュメントを保存すると、Aspose.Words は指定したフォント設定を使用します。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

これにより、ドキュメントはPDFとしてドキュメントディレクトリに保存されます。`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## 結論

これで完了です。Aspose.Words for .NET を使用して、フォント フォルダーを優先順位付きで設定できました。カスタム フォント フォルダーと優先順位を指定することで、ドキュメントがどこで表示されても、一貫してレンダリングされることを保証できます。これは、特定のフォントが既定でインストールされていない環境で特に役立ちます。

## よくある質問

### カスタムフォントフォルダーを設定する必要があるのはなぜですか?
カスタム フォント フォルダーを設定すると、ドキュメントを表示するシステムにインストールされていないフォントが使用されている場合でも、ドキュメントが正しくレンダリングされるようになります。

### 複数のカスタムフォントフォルダーを設定できますか?
はい、複数のフォント フォルダーを指定できます。Aspose.Words では、各フォルダーの優先順位を設定できるため、最も重要なフォントが最初に見つかるようになります。

### 指定されたすべてのソースからフォントが見つからない場合はどうなりますか?
指定されたすべてのソースにフォントがない場合、Aspose.Words はフォールバック フォントを使用して、ドキュメントが引き続き読み取れる状態であることを確認します。

### システムフォントの優先順位を変更できますか?
システム フォントはデフォルトで常に含まれていますが、カスタム フォント フォルダーに対する優先順位を設定できます。

### カスタムフォントフォルダーにネットワークパスを使用することは可能ですか?
はい、ネットワーク パスをカスタム フォント フォルダーとして指定して、ネットワーク上の場所にフォント リソースを集中管理できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
