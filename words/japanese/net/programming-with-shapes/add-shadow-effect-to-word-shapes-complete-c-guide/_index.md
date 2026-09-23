---
category: general
date: 2026-02-10
description: C# を使用して Word の図形に影効果を追加します。影の色の変更、透明度の設定、図形への影の適用を数ステップで学びましょう。
draft: false
keywords:
- add shadow effect
- change shadow color
- how to set transparency
- add shape shadow
- apply shadow color
language: ja
og_description: C# を使用して Word の図形に影効果を追加します。影の色の変更、透明度の設定、図形への影の適用方法を数ステップで学びましょう。
og_title: Wordの図形に影効果を追加 – 完全C#ガイド
tags:
- Aspose.Words
- C#
- Document Automation
title: Wordの図形に影効果を追加する – 完全C#ガイド
url: /ja/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word シェイプに影効果を追加する – 完全 C# ガイド

Word のシェイプに **影効果を追加** したいけど、どこから始めればいいか分からないことはありませんか？開発者の間でも「シェイプをもう少し立体的に見せるにはどうすればいいのか？」という質問はよくあります。良いニュースは、数行の C# で影の色を変更したり、透明度を設定したり、見た目を微調整できることです。このチュートリアルでは、まさにそれを実現する完全な実行可能サンプルと、事前に知っておきたかったヒントをいくつか紹介します。

取り上げる内容:

* 既にシェイプが含まれている DOCX ファイルの読み込み  
* シェイプの検索（グループ内にあっても）  
* 影の適用 – 距離、ぼかし、色、透明度  
* 結果を保存して確認  

外部ドキュメントは不要です。必要なものはすべてここにあります。前提条件は **Aspose.Words for .NET**（または `Shape.ShadowFormat` を公開している互換ライブラリ）への参照だけです。NuGet を使用している場合は `Install-Package Aspose.Words` を実行してください。準備はいいですか？さっそく始めましょう。

---

## Prerequisites

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 以降 | 最新 API とパフォーマンス向上 |
| Aspose.Words for .NET（または同等） | `Document`、`Shape`、`ShadowFormat` クラスを提供 |
| シェイプが少なくとも 1 つ含まれる DOCX ファイル (`input.docx`) | 本チュートリアルは既存シェイプを操作します。必要なら Word で手動で矩形を作成して保存してください |

> **Pro tip:** シェイプが手元にない場合は、Word でシンプルな矩形を挿入し、`input.docx` として保存し、プロジェクトの `Resources` フォルダーに配置しましょう。

---

## Step 1 – Load the Word Document and Locate the Shape {#add-shadow-effect-step1}

まず最初に、ソースファイルを指す `Document` オブジェクトが必要です。その後、再帰検索で最初のシェイプを取得し、シェイプがグループ内にあっても対応できるようにします。

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Step 1: Load the Word document that contains a shape
        Document doc = new Document("Resources/input.docx");

        // Step 2: Retrieve the first shape in the document (searches recursively)
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Continue with shadow settings...
```

**Why we do this:**  
* `Document` は任意の Word ファイルへのエントリーポイントです。  
* `GetChild(NodeType.Shape, 0, true)` はノードツリー全体を走査し、入れ子になったシェイプも見逃しません。  
* null チェックは、シェイプが存在しないファイルで `NullReferenceException` が発生するのを防ぎます。これは初心者が見落としがちなエッジケースです。

---

## Step 2 – Set the Shadow Distance and Blur {#add-shadow-effect-step2}

影は単なる色だけでなく、オフセットと柔らかさも重要です。影を数ポイント離し、微妙なぼかしを加えてみましょう。

```csharp
        // Step 3: Set how far the shadow is offset from the shape
        targetShape.ShadowFormat.Distance = 4.0;   // 4 points offset

        // Step 4: Define the softness of the shadow edges
        targetShape.ShadowFormat.BlurRadius = 2.0; // 2 points blur
```

**Explanation:**  
* **Distance** は X/Y のオフセットを制御します。`4.0` の値は影を下方向と右方向に移動させ、左上から光が当たっているように見せます。  
* **BlurRadius** はエッジの羽根の程度を決めます。数値が低いと影はくっきりし、高いと柔らかい光のように見えます。

別の光源方向が必要な場合は、`ShadowFormat.Angle`（デフォルトは 45°）も調整できます。

---

## Step 3 – Change Shadow Color and Set Transparency {#add-shadow-effect-step3}

いよいよ楽しいパートです。色を変えて影を半透明にします。ここが **change shadow color** と **how to set transparency** のキーワードが活きるところです。

```csharp
        // Step 5: Choose a colour for the shadow
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color here

        // Step 6: Make the shadow partially transparent (30 % transparent)
        targetShape.ShadowFormat.Transparency = 0.3; // Value between 0 (opaque) and 1 (fully transparent)
```

**Why it matters:**  
* `Color.DarkGray` は明暗どちらの背景でも安全に使えるデフォルトです。純黒にしたい場合は `Color.FromArgb(255, 0, 0, 0)`、あるいは任意の ARGB 値に置き換えて構いません。  
* `Transparency` を `0.3` に設定すると 30 % の透過効果が得られ、深みを示しつつシェイプ自体を隠さない程度になります。

**Edge case:** 古いバージョンの Word は特定のシェイプ種別（例: WordArt）で透明度を無視することがあります。その場合は、シェイプを画像に変換してから適用してみてください。

---

## Step 4 – Save and Verify the Result {#add-shadow-effect-step4}

影の調整が終わったら、ドキュメントをディスクに書き戻します。Word でファイルを開くと、シェイプの周りに微妙な色付き半透明の影が表示されます。

```csharp
        // Step 7: Save the modified document
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

**Verification checklist:**

1. `output_with_shadow.docx` を Microsoft Word で開く。  
2. シェイプを選択 → **Format** → **Shape Effects** → **Shadow**。  
3. 約 4 pt のオフセット、ぼかしがかかり、30 % 透明なダークグレーの影が見えるはずです。

見た目が期待と違う場合は、`ShadowFormat` のプロパティ、特に `Distance` と `Transparency` を再確認してください。

---

## Common Variations and What‑If Scenarios {#add-shadow-effect-variations}

### Adding a Shadow to Multiple Shapes

ドキュメント内のすべてのシェイプに **add shape shadow** を適用したい場合は、単一シェイプ取得をループに置き換えます。

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Distance = 5.0;
            shp.ShadowFormat.BlurRadius = 3.0;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.4;
        }
```

### Using a Custom Colour with Alpha

影の色自体を半透明にしたいこともあります。その場合は `Color.FromArgb` と `Transparency` を組み合わせてレイヤード効果を作ります。

```csharp
        // Semi‑transparent blue shadow
        targetShape.ShadowFormat.Color = Color.FromArgb(180, 0, 0, 255); // 180/255 ≈ 70% opacity
        targetShape.ShadowFormat.Transparency = 0.2; // Additional 20% transparency
```

### Handling Shapes Inside a Group

グループ化されたシェイプは `GroupShape` ノードとして格納されます。先ほど使用した再帰検索（`true` フラグ）は既にグループ内部まで潜りますが、グループ全体を単一エンティティとして扱いたい場合は `GroupShape` にキャストし、`ChildNodes` を走査してください。

```csharp
        GroupShape group = targetShape.ParentNode as GroupShape;
        if (group != null)
        {
            foreach (Shape inner in group.GetChildNodes(NodeType.Shape, true))
            {
                // Apply same shadow settings to each inner shape
                inner.ShadowFormat = targetShape.ShadowFormat.Clone();
            }
        }
```

---

## Pro Tips & Pitfalls {#add-shadow-effect-tips}

* **Pro tip:** 実験中は `ShadowFormat.Visible = true` を明示的に設定すると便利です。一部 API はプロパティが変わるまで影を非表示にします。  
* **Watch out for:** Word の「枠線なし」設定は影が浮いて見える原因になります。影を補完させたい場合はシェイプの線スタイルを表示させてください。  
* **Performance note:** 大規模ドキュメントで数千のシェイプを更新すると遅くなることがあります。変更はバッチ処理し、最後に `doc.UpdatePageLayout()` を一度だけ呼び出すようにしましょう。  
* **Compatibility:** Aspose.Words 23.10 以降は DOCX の影プロパティを完全にサポートしていますが、古いバージョンは `BlurRadius` を無視することがあります。配布するライブラリのバージョンで必ずテストしてください。

---

## Full Working Example {#add-shadow-effect-complete}

以下はコピー＆ペーストでそのまま使える完全版プログラムです。`using` ディレクティブ、エラーハンドリング、コメントをすべて含んでいます。

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the document that already contains a shape.
        Document doc = new Document("Resources/input.docx");

        // Retrieve the first shape (recursively searches groups).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Apply shadow distance and blur.
        targetShape.ShadowFormat.Distance = 4.0;      // Offset from shape
        targetShape.ShadowFormat.BlurRadius = 2.0;   // Soft edges

        // Change shadow color and set transparency.
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;     // How to set transparency (30%)

        // Save the modified document.
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

このプログラムを実行すると、**add shadow effect** が適用された `output_with_shadow.docx` が生成されます。ファイルを開くと、プロフェッショナルなプレゼンテーションで期待される、30 % 透明なダークグレーのぼかし影がシェイプに付いているのが確認できます。

---

## Conclusion

今回は C# を使って Word シェイプに **add shadow effect** を加える方法を実演しました。ドキュメントを読み込み、シェイプを特定し、`ShadowFormat` プロパティを調整して保存するだけで、**change shadow color**、**how to set transparency**、**add shape shadow** を数分で自在にコントロールできます。

次のステップとしては、**apply shadow color** を条件付きで設定してみるのも面白いでしょう。たとえば、シェイプが大きいほど濃い影にしたり、ユーザー入力に応じて色を変えたり。さらに、光彩、反射、3‑D ベベルといった他のビジュアルエフェクトにも同じ `ShadowFormat` パターンが応用できますので、ぜひ拡張してみてください。

質問や予期せぬエッジケースに遭遇したら、下のコメント欄で教えてください。一緒にトラブルシュートしましょう。Happy coding、そしてあなたのドキュメントが常に奥行きを持つように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}