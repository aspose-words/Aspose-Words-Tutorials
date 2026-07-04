---
category: general
date: 2026-05-01
description: C# を使用して Aspose.Words で図形の影を移動する方法。数分で図形に影を追加し、ぼかしを変更し、透明度を設定し、影を回転させる方法を学びましょう。
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: ja
og_description: C# を使用して Aspose.Words でシェイプの影を移動する方法。このチュートリアルでは、シェイプに影を追加し、ぼかしを変更し、透明度を設定し、影を回転させる方法を示します。
og_title: Aspose.Wordsで影を移動する方法 – 完全なC#ガイド
tags:
- Aspose.Words
- C#
- Document Automation
title: Aspose.Wordsで影を移動する方法 – 完全なC#ガイド
url: /ja/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で影を移動する方法 – 完全な C# ガイド

Word ドキュメント内のシェイプの **影の移動方法** を、手動で Word を開かずに知りたくありませんか？日常業務で、レポートを洗練させるためや動的テンプレートのために、シェイプの影をプログラムで微調整する必要が頻繁にありました。良いニュースは、Aspose.Words を使えば数行のコードで実現でき、**add shadow to shape**、**how to change blur**、**how to set transparency**、**how to rotate shadow** も同時に学べます。

このチュートリアルでは、既にシェイプが含まれている既存の DOCX を読み込み、影の位置、柔らかさ、不透明度、方向を調整し、最終的に保存する実践的シナリオを解説します。最後まで読めば、任意の .NET プロジェクトに貼り付け可能な再利用可能なスニペットが手に入り、各プロパティの重要性も理解できます。

## 前提条件 – 開始前に必要なもの

- **Aspose.Words for .NET**（バージョン 23.12 以降）。`Install-Package Aspose.Words` で NuGet から取得できます。
- .NET 6+ 開発環境（Visual Studio、VS Code、Rider など、お好みのもの）。
- 既に少なくとも 1 つのシェイプ（矩形、円、または画像）が含まれている入力 Word ファイル（`input.docx`）。
- 基本的な C# 文法に慣れていること—特別な知識は不要です。

これらが揃っていない場合は、一度止めてライブラリをインストールしてください。以降の手順はパッケージが参照済みであることを前提としています。

## ステップ 1: ドキュメントをロードし対象シェイプを取得 – **How to Move Shadow** がここから始まります

最初に行うのは、ソースドキュメントをロードし、変更したいシェイプを特定することです。Aspose.Words はすべてのオブジェクト（段落、テーブル、シェイプ）をツリー上のノードとして扱うため、直接クエリできます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Why this matters:** ドキュメントを一度だけロードし、同じ `Document` インスタンスを再利用することで効率的です。`GetChild` 呼び出しはインデックスが範囲外の場合 `null` を返すため、シェイプが存在しないケースも安全に処理できます。

## ステップ 2: ぼかし半径を調整 – Master **How to Change Blur**

柔らかい影はプロフェッショナルに見え、ハードなエッジは安っぽく感じられます。`BlurRadius` プロパティはポイント単位で柔らかさを制御します（1 pt ≈ 1/72 インチ）。ここでは 8 pt に上げてみましょう。

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Pro tip:** デフォルトのぼかしは 0.5 pt です。5 pt を超えるとほとんどの場合目立ちますが、あまり大きくしすぎるとシェイプがページから浮き上がって見えるので注意してください。

## ステップ 3: 透明度を設定 – The Answer to **How to Set Transparency**

透明度は影の透過度を決めます。`0` は完全に不透明、`1` は完全に見えなくなります。さりげない効果として `0.3`（30 % 透明）を使用します。

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Why you might care:** シェイプが濃い色の場合、完全に不透明な影は下のテキストを埋もれさせてしまいます。透明度を調整すれば、文書の可読性を保ちつつ奥行きを演出できます。

## ステップ 4: 影を移動 – The Core of **How to Move Shadow**

`Distance` プロパティは影がシェイプからどれだけ離れるかをポイントで指定します。距離が大きいほど影が遠くにずれ、ドラマチックな効果が得られます。

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **What if you need a tiny offset?** `Distance` を `0` に設定すると、影がシェイプのすぐ背後に重なります。エンボス効果などに便利です。

## ステップ 5: 光源を回転 – Solving **How to Rotate Shadow**

影は単に下向きだけでなく、光源の角度に従います。`Angle` プロパティ（度単位）で影をシェイプの周りに回転させます。ここでは 45° に傾けます。

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Quick experiment:** `90` にすると右側に影ができ、`-30` にすると左側に傾いた影になります。変化はすぐに視覚で確認できます。

## ステップ 6: ドキュメントを保存 – Seeing the Result of **Add Shadow to Shape**

影の調整が完了したら、ドキュメントをディスクに書き戻します。元ファイルを上書きするか新しいファイルを作成するかは自由です。例では新しい出力ファイルを使用します。

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Expected output:** `output.docx` を開くと、シェイプの影がより柔らかく、少しオフセットされ、半透明で、45° に傾いていることが確認できます。`input.docx` と並べて比較すれば違いは一目瞭然です。

### 完全動作サンプル（コピー＆ペースト用）

以下は 1 つのブロックにまとめた全プログラムです。新しいコンソールプロジェクトに貼り付け、`YOUR_DIRECTORY` を実際のフォルダー パスに置き換えて実行してください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## よくある質問とエッジケース

### ドキュメントに複数のシェイプがある場合は？

すべてのシェイプをループで処理できます：

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### 現在影が設定されていないシェイプに影を追加できますか？

もちろんです。`ShadowFormat` オブジェクトは常に存在しますので、有効化するだけです：

```csharp
shape.ShadowFormat.Enabled = true;
```

### 画像や SmartArt でも動作しますか？

はい。`Shape` を継承するノード（画像、チャート、SmartArt など）すべてが `ShadowFormat` を公開しています。同じプロパティが使用可能です。

### 影の色はどうやって制御しますか？

`Color` プロパティを使用します：

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### 互換性の懸念は？

Aspose.Words 23.12 以降は .NET 6、.NET Core 3.1、.NET Framework 4.6.2+ をサポートしています。ここで示した API はこれらのバージョン間で安定しています。

## 結論

Aspose.Words を使ってシェイプの **影の移動方法** を解説しながら、**add shadow to shape**、**how to change blur**、**how to set transparency**、**how to rotate shadow** も同時に実演しました。完全に実行可能なサンプルは、数秒で任意のシェイプの影を調整でき、Word を開かずに文書を洗練されたプロフェッショナルな外観にします。

次のステップに進みませんか？たとえば、見出しや一定サイズ以上のチャートにだけ深い影を適用する **conditional formatting** と組み合わせたり、シェイプ自体に **gradient fills** を適用して目を引くデザインを作り出したりしてみてください。

問題があればコメントで教えてください。コーディングを楽しみながら、影が思い通りの位置に落ちることを願っています！

![シェイプ上の影の移動効果を示す図 – 影の移動例](https://example.com/images/shadow-demo.png "影の移動例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}