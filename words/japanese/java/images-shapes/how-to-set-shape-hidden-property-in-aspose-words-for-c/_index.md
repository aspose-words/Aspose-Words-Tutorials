---
category: general
date: 2026-08-20
description: Aspose.Words for C#でシェイプの非表示プロパティを設定する方法を学びましょう。このガイドでは画像を挿入し、シェイプを非表示にして
  UI や印刷出力に決して表示されないようにする手順を示します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: ja
lastmod: 2026-08-20
og_description: C# を使用して Aspose.Words のシェイプの hidden プロパティを設定します。画像を挿入し、シェイプを非表示にして、UI
  や印刷出力に決して表示されないようにします。
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Aspose.Wordsでシェイプの非表示プロパティを設定する – 完全なC#ガイド
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Aspose.Words for C# でシェイプの非表示プロパティを設定する方法
url: /ja/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for C#でシェイプの非表示プロパティを設定する方法

Word文書で **シェイプの非表示プロパティを設定** する必要がある場合、このチュートリアルでは Aspose.Words for .NET を使用した正確な手順を示します。テンプレートエンジンの構築、レポートの生成、または非表示にすべきロゴの埋め込みなど、画像を挿入しシェイプを非表示にして UI や印刷出力に現れないようにする方法を学べます。

このガイドでは **画像を文書に挿入** する方法もカバーし、シェイプを非表示にすることが印刷時に重要な理由を説明し、完全な実行可能コードを順に解説します。外部参照は不要です—コピーして貼り付け、実行するだけです。

## 前提条件

開始する前に、以下を用意してください：

* .NET 6.0 以降（最新の Aspose.Words バージョンは .NET 6+ を対象）
* 有効な Aspose.Words for .NET ライセンス（または無料評価モード）
* Visual Studio 2022 またはお好みの C# IDE
* 画像ファイル（例：`logo.png`）をコードから参照できるフォルダーに配置

## Step 1: 新しい Document と DocumentBuilder を作成

`DocumentBuilder` クラスは、プログラムで Word コンテンツを構築するためのエントリーポイントです。段落、テーブル、画像などのシェイプを挿入できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step?*  
`Document` を作成すると .docx ファイルのメモリ上表現が得られ、`DocumentBuilder` がオブジェクトを挿入するためのフルエント API を提供します。これらがなければ文書にシェイプを配置できません。

## Step 2: 画像をシェイプとして挿入

Aspose.Words はすべての画像を `Shape` として扱います。`InsertImage` メソッドはその `Shape` インスタンスを返し、後で操作できます。

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Why this step?*  
`InsertImage` を使用すると画像がテキストのフローに追加されるだけでなく、設定可能な参照（`picture`）が得られます。これは次に設定する **C# シェイプの非表示プロパティ** に不可欠です。

## Step 3: シェイプの非表示プロパティを設定

`Hidden` プロパティはシェイプが UI と印刷に参加するかどうかを制御します。`true` に設定すると、Word の UI でシェイプが見えず、印刷されることもありません。

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Why this step?*  
シェイプが非表示としてマークされると、Word はそれをコメントのように扱い、文書構造には残りますが描画されません。これが **シェイプの非表示プロパティを設定** する核心です。

## Step 4: 文書を保存

最後に、文書をディスクに書き出します。Aspose.Words がサポートする任意の形式（`.docx`、`.pdf`、`.html` など）を選択できます。

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Why this step?*  
保存によりメモリ上の変更が確定します。生成された `.docx` を Microsoft Word で開くと画像は表示されず、PDF へのエクスポートでもシェイプは印刷に現れません。

## 完全な実行可能サンプル

すべてをまとめると、以下がコンパイルして実行できる完全なプログラムです：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**期待される結果**

* Microsoft Word で `HiddenImageDocument.docx` を開くと画像が表示されません。
* 文書をエクスポートまたは印刷（PDF を開く）しても画像は表示されません。
* 非表示シェイプは文書 XML に残っており、`.docx` を zip として展開し `word/document.xml` を確認すると `<w:pict>` 要素に `w:hidden="true"` が付いていることが分かります。

## よくあるバリエーションとエッジケース

| 状況 | 対処方法 | なぜ重要か |
|-----------|------------|----------------|
| **画像ファイルが見つからない** | `InsertImage` を `try/catch` でラップし、`FileNotFoundException` を処理する。 | アプリケーションのクラッシュを防ぎ、明確なエラーログを記録できる。 |
| **複数の非表示シェイプ** | 挿入する各 `Shape` に対して `picture.Hidden = true` を呼び出すか、`doc.GetChildNodes(NodeType.Shape, true)` を反復処理する。 | 望ましくないすべてのビジュアル要素が確実に非表示になる。 |
| **編集モードだけでシェイプを表示したい** | 編集後に `picture.Hidden = false` に設定し、保存前に再度 `true` に戻す。 | UI でシェイプを操作しつつ、最終出力はクリーンに保てる。 |
| **古い Word バージョンでの印刷** | Word 2010 以降で文書を確認する。非表示フラグはすべてのモダンバージョンでサポートされている。 | ユーザー基盤全体での互換性が確保できる。 |
| **別のファイル形式（例：直接 PDF）を使用** | `Hidden` フラグは同様に機能し、Aspose.Words は PDF 変換時にそれを尊重する。 | **シェイプの印刷防止** がすべてのエクスポート先で機能することを確認できる。 |

## プロのコツ：プログラムで非表示フラグを検証

保存前にシェイプが非表示かどうか確認したい場合、プロパティをチェックできます：

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

このシンプルなチェックは、ドキュメント生成ポリシーへの準拠を保証しなければならない自動化パイプラインで役立ちます。

## 結論

これで Aspose.Words for C# で **シェイプの非表示プロパティを設定** する方法が分かりました。画像を挿入し、`picture.Hidden = true` を適用して文書を保存すれば、シェイプは UI にも印刷にも現れません。この手法は、プレースホルダーや透かし、ブランディング要素など、エンドユーザーに見せたくない要素が必要な場合に不可欠です。

### 次は何をすべき？

* `picture.WrapType`、`picture.Rotation`、`picture.RelativeHorizontalPosition` など、他のシェイププロパティを探求する。  
* ユーザー入力や設定に基づいて **Aspose.Words でシェイプを非表示** にする方法を学ぶ。  
* 非表示シェイプと **画像を文書に挿入** ループを組み合わせ、後処理用の動的な見えないマーカー（例：差し込み印刷フィールド）を生成する。

さまざまな画像形式、文書レイアウト、エクスポート先を自由に試してみてください。シェイプを非表示にすることで、読者が実際に目にするものと、裏で静かに動作するものを細かく制御できます。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの説明と完全な動作コード例が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}