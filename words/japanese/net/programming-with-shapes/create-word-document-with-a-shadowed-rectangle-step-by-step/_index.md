---
category: general
date: 2026-01-13
description: Aspose.Words を使用して Word 文書を作成し、長方形の図形の挿入方法、影の付け方、図形に影を追加する方法を C# で学びます。完全なサンプルが含まれています。
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: ja
og_description: Aspose.WordsでWord文書を作成し、長方形の図形の挿入方法と影の付け方を確認してください。完全なC#サンプルに従ってください。
og_title: 影付き長方形でWord文書を作成 – 完全チュートリアル
tags:
- Aspose.Words
- C#
- Document Automation
title: 影付き長方形でWord文書を作成する – ステップバイステップガイド
url: /ja/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 影付き長方形でWord文書を作成する – ステップバイステップガイド

きれいにシェードされた長方形を含む **create word document** が必要だったことはありませんか？しかし、どこから始めればよいか分からなかったことはありませんか？あなただけではありません—多くの開発者が Aspose.Words を初めて使うときに同じ壁にぶつかります。

このチュートリアルでは、プログラムで **create word document** を行うために必要なすべて、**insert rectangle shape**、そして形状を際立たせる **how to add shadow** の方法を順に解説します。最後までに、任意の .NET プロジェクトに組み込める実行可能な C# スニペットが手に入ります。

## 学べること

- Word ファイルに (長方形) を **how to insert shape** するための正確なコード。  
- **add shape shadow** を調整し、外観を制御するために必要なプロパティ。  
- 結果を保存し、影が表示されていることを確認する方法。  
- 後で頭痛になるのを防ぐ実用的なヒントやエッジケースの注意点。  

外部ドキュメントは不要です—すべてここにあります。

## 前提条件

始める前に、以下が揃っていることを確認してください：

1. **.NET 6.0**（または最新の .NET バージョン）をインストールしてください。  
2. Aspose.Words for .NET の **license**、またはテスト用の無料評価モードを使用できます。  
3. 開発環境—Visual Studio 2022 が最適ですが、C# をコンパイルできるエディタであれば何でも構いません。  

以上です。`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## ステップ 1 – プロジェクトを設定し Aspose.Words を参照する

まず、新しいコンソール アプリを作成し、Aspose.Words パッケージを追加します：

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** 無料トライアルを使用している場合は、ライセンス ファイルで `License.SetLicense` を呼び出すことを忘れないでください。そうしないと、ライブラリが透かしを追加します。

## ステップ 2 – Document Builder を初期化する

これから実際の **create word document** プロセスを開始します。`Document` クラスは空のキャンバスを提供し、`DocumentBuilder` でその上に描画できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

なぜ Builder が必要なのでしょうか？低レベルの OpenXML の詳細を抽象化するため、ファイルの構造 *どうやって* ではなく、*何を* したいかに集中できます。これが **how to insert shape** を迅速に行う核心です。

## ステップ 3 – 長方形シェイプを挿入する

ここで実際に **insert rectangle shape** を行います。長方形は 150 × 100 ポイント（約 2 インチ × 1.3 インチ）です。

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

`InsertShape` メソッドは `Shape` オブジェクトを返し、さらにカスタマイズできます。この時点では、長方形は単なる白い実体のボックスで、まだ影はありません。

## ステップ 4 – 影を追加する方法 (Add Shape Shadow)

影を追加するのは、どのプロパティを操作すればよいか分かれば驚くほど簡単です。`ShadowFormat` オブジェクトは可視性、色、ぼかし、オフセット、サイズを制御します。

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

このブロックは **how to add shadow** を平易に説明しています：有効にし、色を選び、透明度、オフセット、ぼかし、サイズを調整します。これらの数値を試すことで、濃いドロップシャドウやかすかな薄い影を得られます。

### 一般的なバリエーション

- **Different colours:** クラシックなドロップシャドウには `Color.Black`、スタイリッシュな効果には `Color.BlueViolet` を使用します。  
- **Zero blur:** 鮮明でシャープなエッジにするには `BlurRadius = 0` を設定します。  
- **Larger offsets:** `OffsetX`/`OffsetY` を増やすと、シェイプから影をさらに遠ざけられます。

## ステップ 5 – ドキュメントを保存して確認する

最後に、ドキュメントをディスクに書き込みます。ファイルは標準的な `.docx` で、最新の Word プロセッサで開くことができます。

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

生成された *ShadowRectangle.docx* を Microsoft Word で開きます。右下にオフセットされた柔らかいグレーの影が付いた長方形が表示されるはずです—コードが指定した通りです。

> **Expected output:** 150 × 100 ポイントの長方形に、30 % 透明のグレー影が付いた、1 ページの Word ファイルです。影は 5 ポイントオフセット、4 ポイントぼかし、サイズはシェイプの 75 % です。

## 完全な動作例

すべてをまとめると、以下が完全で実行可能なプログラムです：

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

プログラムを実行（`dotnet run`）すると、影付きの長方形が入った新しい Word ファイルが作成されます—レポート、証明書、または必要なビジュアル要素に最適です。

## よくある質問 (FAQs)

**Q: 他の形状（楕円、星形）を挿入しても同じ影のコードを使えますか？**  
A: もちろんです。`InsertShape` メソッドは任意の `ShapeType` 列挙値を受け取ります。`Shape` インスタンスを取得すれば、`ShadowFormat` のプロパティは同様に機能するため、**how to add shadow** は形状に依存しません。

**Q: シェイプの両側に影が必要な場合はどうすればよいですか？**  
A: Aspose.Words はシェイプごとに単一のドロップシャドウしかサポートしていません。両側の効果をシミュレートするには、シェイプを複製し、各コピーを異なるオフセットで配置し、一方の `ShadowFormat.Visible` を `false` に、もう一方の影は有効にします。

**Q: .NET Framework 4.8 でも動作しますか？**  
A: はい。API はバージョンに依存せず、対象フレームワークに合わせた Aspose.Words DLL を参照すれば動作します。

## ヒントと落とし穴

- **Don’t forget to set `Visible = true`**—そうしないと影のプロパティは無視されます。  
- **Transparency values range from 0.0 (opaque) to 1.0 (fully transparent).** よくあるミスは `0.3` の代わりに `30` を使用することです。  
- **Saving to a read‑only folder throws an exception.** 出力ディレクトリが書き込み可能であることを確認してください。

## 次のステップ

これで **how to insert shape**、**add shape shadow**、そして Aspose.Words を使った **create word document** が分かったので、以下を検討してみてください：

- シェイプを挿入する前に `builder.InsertParagraph()` を使用して **text inside the rectangle** を追加する。  
- **gradient fills** または **patterned borders** を適用して、よりリッチなビジュアルスタイリングを行う。  
- 複数ページの生成を自動化し、各ページに異なるシェーディングシェイプを配置して動的レポートを構築する。  

自由に試してみてください—影の色、ぼかし、サイズを変更すると、ドキュメントの見た目が劇的に変わります。

---

*本番環境で使用する準備はできましたか？コードを取得し、パラメータを調整すれば、数秒で Word ファイルがプロフェッショナルな仕上がりになります。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}