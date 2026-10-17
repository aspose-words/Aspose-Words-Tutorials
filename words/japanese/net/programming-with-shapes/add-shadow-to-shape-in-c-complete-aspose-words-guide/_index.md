---
category: general
date: 2026-03-14
description: このステップバイステップのC#チュートリアルで、図形に素早く影を追加し、影の角度の変更方法や影付きドキュメントの保存方法などを学びましょう。
draft: false
keywords:
- add shadow to shape
- change shadow angle
- how to add shape shadow
- save document with shadow
language: ja
og_description: シェイプにすばやく影を追加し、影の角度の変更方法を学び、Aspose.Words for .NET を使用して影付きのドキュメントを保存します。
og_title: C#で図形に影を追加 – 完全な Aspose.Words ガイド
tags:
- Aspose.Words
- C#
- Document Automation
title: C#でシェイプに影を追加 – 完全な Aspose.Words ガイド
url: /ja/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でシェイプに影を追加 – 完全な Aspose.Words ガイド

シェイプに **影を追加** したいと思ったことはありませんか？どのプロパティを調整すれば良いか分からないこともあるでしょう。これはあなただけの悩みではなく、Word 文書をプログラムでスタイリングする際に多くの開発者が直面する問題です。良いニュースは、Aspose.Words を使えばリアルな影を有効にし、角度を調整し、変更を一つのシンプルなワークフローで保存できるということです。

このチュートリアルでは、ドキュメントの読み込み、影の有効化、外観の微調整、そして最終的に **影付きでドキュメントを保存** するまでのすべての手順を解説します。最後まで読めば、散在するフォーラム投稿を探さずに「シェイプに影を追加する方法」を自信を持って答えられるようになります。

## 必要なもの

- **Aspose.Words for .NET**（v23.10 以降 – 本チュートリアルで使用する API はそれ以降変更されていません）
- .NET 対応の IDE（Visual Studio、Rider、または VS Code）
- 少なくとも 1 つのシェイプ（矩形、画像、または SmartArt など）が含まれたシンプルな Word ファイル（`input.docx`）
- 基本的な C# の知識 – 「Hello World」程度を書いたことがあれば問題ありません

> **プロのコツ:** 用意されたドキュメントがない場合は、Word で新規作成し *Insert → Shapes* からシェイプを挿入し、プロジェクトフォルダーに `input.docx` として保存してください。

## Step 1 – ドキュメントを読み込み、対象シェイプを取得

最初に Word ファイルをメモリに読み込み、装飾したいシェイプを見つけます。Aspose.Words はすべての描画要素を `Shape` ノードとして扱い、`GetChild` で取得できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the Word document that contains a shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Retrieve the first shape in the document (index 0). 
// If you have multiple shapes, change the index or loop through them.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

**重要ポイント:**  
`Document` はすべての操作のエントリーポイントです。`GetChild` はノードツリーを深さ優先で走査し、ヘッダー・フッター・本文のいずれにシェイプがあっても最初のシェイプを取得します。このステップを省いて直接 `shape` にアクセスすると `NullReferenceException` が発生します。

## Step 2 – 影効果を有効化

影はデフォルトでオフになっているため、視覚プロパティを調整する前にオンにする必要があります。1 行だけですが、これで多数のオプションが使用可能になります。

```csharp
// Turn the shadow on.
shape.Shadow.Enabled = true;
```

> **豆知識:** `Shadow` オブジェクトは機能が無効でも存在するため、事前に設定を行い、後から有効化しても追加コードは不要です。

## Step 3 – コア影プロパティを設定

ここからが本番です。色、透明度、ぼかし、距離、サイズを設定します。これらの値はポイントまたはパーセンテージで表され、Word の UI と同様です。

```csharp
// Basic visual settings
shape.Shadow.Color = Color.Black;          // Shadow colour
shape.Shadow.Transparency = 0.3f;          // 30 % transparent
shape.Shadow.BlurRadius = 5.0f;            // Softness of the edge
shape.Shadow.Distance = 3.0f;              // Gap between shape and shadow
shape.Shadow.Size = 100;                   // Scale of the shadow (percent)
```

**解説:**  
- **Color** は色相を決めます。ほとんどの場合は黒で問題ありませんが、ブランドカラーに合わせても構いません。  
- **Transparency** は `0`（不透明）から `1`（完全に透明）までの浮動小数点数です。  
- **BlurRadius** は影の「ぼやけ具合」を制御し、数値が大きいほど柔らかい印象になります。  
- **Distance** はシェイプから影をどれだけ離すかを決め、奥行きを演出します。  
- **Size** は影のサイズを比例的に拡大・縮小します。`100 %` はシェイプと同サイズを意味します。

## Step 4 – 影の角度を変更（Secondary Keyword）

光源の方向を変えたい場合は `Angle` プロパティを調整します。ここが **change shadow angle** キーワードの出番です。

```csharp
// Rotate the light source – 45 degrees is a common default.
shape.Shadow.Angle = 45;   // Angle in degrees (0‑360)
```

> **劇的な効果を出したいときは?** 左から右への光なら `0`、上から下への光なら `90`、逆方向の影なら `180` を試してみてください。角度は 360 で一周するため、`360` は `0` と同等です。

## Step 5 – 影付きでドキュメントを保存

影の見た目が決まったら、変更を永続化します。`Save` メソッドは元ファイルを残したまま新しいファイルを書き出します。

```csharp
// Save the modified document.
doc.Save("YOUR_DIRECTORY/output.docx");
```

これで `output.docx` にはシェイプに洗練された影が付いた状態が保存されました。Word で開いて確認すると、設定した角度に応じた微妙で半透明のハローが表示されているはずです。

## 完全動作サンプル

以下はコンソールアプリにそのまま貼り付け可能なフルプログラムです。各ブロックにコメントを入れてあります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Grab the first shape (adjust index if needed).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable shadow.
        shape.Shadow.Enabled = true;

        // 4️⃣ Set visual properties.
        shape.Shadow.Color = Color.Black;
        shape.Shadow.Transparency = 0.3f;
        shape.Shadow.BlurRadius = 5.0f;
        shape.Shadow.Distance = 3.0f;
        shape.Shadow.Size = 100;

        // 5️⃣ Change shadow angle (how to add shape shadow from a different direction).
        shape.Shadow.Angle = 45; // Try 0, 90, 180, etc.

        // 6️⃣ Save the result – this is the step that lets you **save document with shadow**.
        doc.Save("YOUR_DIRECTORY/output.docx");

        System.Console.WriteLine("Shadow applied and document saved successfully!");
    }
}
```

### 期待される結果

- `output.docx` を開くと、元のシェイプが柔らかい黒い影で囲まれていることが確認できます。  
- `Angle` を `90` に変更すると、影がシェイプの真下に表示され、上からの照明を模倣します。  
- `Transparency` を `0.0f` にすると不透明な影になり、`1.0f` にすると影が見えなくなります（トグル用に便利です）。

## よくある落とし穴と回避策

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **`shape` が `null`** | ドキュメントにシェイプが無い、またはインデックスが間違っている | Word ファイルにシェイプが含まれているか確認するか、`doc.GetChildNodes(NodeType.Shape, true)` をループして正しいシェイプを取得 |
| **Word で影が表示されない** | `Shadow.Enabled` が `false` のまま、またはシェイプの種類が影に対応していない（例: 純テキスト） | `Shape` オブジェクト（画像、図形、SmartArt など）を使用し、`Enabled = true` に設定 |
| **予期しない色になる** | テーマの上書きにより `Color` が Word 側で変換される | 純黒は `Color.FromArgb(0,0,0)` を使用するか、`shape.Shadow.ThemeColor` でドキュメントテーマに合わせる |
| **パフォーマンス低下** | 大規模ドキュメントで多数のシェイプを個別に変更している | 変更を `doc.BeginUpdateWords()` / `doc.EndUpdateWords()` でバッチ処理（Aspose.Words v24+） |

## サンプルの拡張例

- **複数シェイプ:** すべてのシェイプをループして統一した影を付与、またはシェイプごとに `Angle` を変えて 3‑D 効果を演出。  
- **動的カラー:** 設定ファイルからカラー値を取得し、企業ブランディングに合わせる。  
- **条件付き影:** シェイプの幅が一定以上の場合にのみ影を付与 – 大きな図表を強調するのに便利。

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.Width > 200) // width in points
    {
        s.Shadow.Enabled = true;
        s.Shadow.Color = Color.Gray;
        s.Shadow.Angle = 30;
    }
}
```

## 結論

Aspose.Words for .NET を使った **シェイプに影を追加** の全工程を網羅しました：ドキュメントの読み込み、影の有効化、色・ぼかし・距離・**影の角度変更** のカスタマイズ、そして最終的に **影付きでドキュメントを保存**。コードは自己完結型で、最新の Aspose.Words バージョンで動作し、各プロパティの「やり方」と「理由」の両方を示しています。

次のステップに進む準備はできましたか？グラデーション影に挑戦したり、テキスト効果と組み合わせて目を引くレポートを作成してみてください。ヘッダーやフッター内のシェイプなど特殊ケースに遭遇したら、今回説明したノードツリー走査テクニックを思い出してください。

Happy coding, and may your documents always have the perfect depth!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}