---
category: general
date: 2026-09-05
description: グループシェイプのdocxを作成し、ActiveXコマンドボタンを挿入し、MarkdownをWord文書に読み込む方法を、完全なC#サンプルと共に学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: ja
lastmod: 2026-09-05
og_description: グループシェイプのdocxを作成し、ActiveXコマンドボタンを挿入し、C#でMarkdownをWord文書に読み込む方法をご紹介します。ステップバイステップのチュートリアルをご覧ください。
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: グループシェイプのdocxを作成し、ActiveXコントロールを埋め込む – C# ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: How to create group shape docx and add interactive controls in C#
url: /ja/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でグループシェイプdocxを作成し、インタラクティブコントロールを追加する方法

プログラムで **create group shape docx** ファイルを作成する必要がある場合、本ガイドはその手順を詳しく解説します。また、**ActiveX コマンドボタン** コントロールの挿入方法や、アンダーライン書式を失わずに **Markdown を Word 文書にロード** する方法も紹介します。チュートリアルの最後まで実行すれば、ベクターグラフィック、インタラクティブ UI 要素、Markdown ベースのコンテンツを組み合わせた完全に機能する `.docx` が作成できます。

このチュートリアルは、基本的な C# 開発環境と Aspose.Words for .NET ライブラリがインストールされていることを前提としています。外部ツールは不要で、標準的な .NET コンソールまたはデスクトップ アプリケーション内で完結します。

## 前提条件

- .NET 6.0 SDK 以降（コードは .NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）
- 有効な X.509 証明書（`.pfx`）※署名ステップをテストする場合
- 画像ファイル（例: `logo.png`）と Markdown ファイル（`sample.md`）を既知のフォルダーに配置

> **プロのコツ:** すべての入力ファイルを単一の *resources* フォルダーにまとめておくと、相対パスがシンプルになります。

## 手順 1: プロジェクトをセットアップし、名前空間をインポート

新しいコンソール プロジェクトを作成し、必要な `using` ディレクティブを追加します。このブロックは、後で使用する Aspose.Words クラスへの参照方法も示しています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

`using` 文により、`Document`、`DocumentBuilder`、`GroupShape`、`Forms2OleControl` など、チュートリアル全体で使用する型に直接アクセスできるようになります。

## 手順 2: **Create group shape docx** – 子要素を持つグループ シェイプを追加

*グループ シェイプ* は、複数の描画オブジェクトを 1 つの単位として扱える機能です。関連するグラフィックをまとめて移動やサイズ変更したいときに便利です。

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**なぜグループ シェイプが必要か?**  
グループ化することで、ユーザーが Word 上で矩形と楕円をドラッグしたときに位置が揃ったままになります。また、共通の枠線を適用したり、プログラムから一括で操作したりする際にも手間が省けます。

## 手順 3: プレーンテキスト コンテンツ コントロール（ユーザー入力用プレースホルダー）を挿入

コンテンツ コントロールは、エンド ユーザーがテキストを入力できる構造化領域を提供します。プレースホルダー テキストは、ユーザーが入力を開始すると自動的に消えます。

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

`PlaceholderName` プロパティは、Word が薄いグレーで表示するヒントです。ユーザーが独自のテキストに置き換えても、基になる XML は正しく保たれます。

## 手順 4: **Insert ActiveX command button** – 文書にインタラクティブ UI を追加

ActiveX コントロールは、最新の Word ファイルでもまだサポートされており、マクロや外部自動化をトリガーできます。以下では *コマンド ボタン* を追加し、キャプションを設定します。

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**ActiveX ボタンを使うべきケース**  
社内で VBA マクロを前提とした文書を配布する場合、ActiveX ボタンでマクロや外部アプリケーションを起動できます。純粋に HTML ベースのインタラクティブ性が必要な場合は、*コンテンツ コントロール* と *Office.js* の組み合わせを検討してください。

## 手順 5: 隠し画像（例: ロゴ）を挿入し、ブランディングや後続スクリプトでのアクセスに利用

隠しシェイプは印刷時には表示されませんが、XML には残ります。これにより、後からプログラムで取得できるようになります。

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## 手順 6: **Load markdown into a Word document** – アンダーライン書式を保持

Aspose.Words は Markdown を直接インポートできます。`ImportUnderlineFormatting` を有効にすると、Markdown のアンダーライン（`<u>` または `__text__`）が Word のアンダーライン スタイルに変換され、プレーンテキストになりません。

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**エッジケース:** Markdown にテーブルが含まれている場合、自動的に Word のテーブルに変換されます。独自のテーブル スタイルが必要な場合は、挿入後に `DocumentBuilder` でカスタマイズしてください。

## 手順 7: XAdES‑EPES で文書に署名（オプションのセキュリティ手順）

デジタル署名は文書の完全性を保証します。以下のコードは、**create group shape docx** ファイルに XAdES‑EPES プロファイルを使用して署名します。

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **セキュリティ上の注意:** 証明書のパスワードはソース管理に含めないでください。本番環境では環境変数や安全なボールトを使用しましょう。

## 完全な実行可能サンプル

すべての手順を統合すると、単一の自己完結型プログラムになります。ファイル名を `Program.cs` として保存し、コマンドラインから実行してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

プログラムを実行すると、`CompleteGroupShape.docx` が生成され、以下が含まれます。

- グループ化された矩形 + 楕円（**create group shape docx** のコア部分）
- プレーンテキスト コンテンツ コントロールとプレースホルダー テキスト
- 「Click Me」とラベル付けされた **insert ActiveX command button**
- 隠しロゴ画像
- アンダーラインが保持された Markdown コンテンツ
- （証明書が提供された場合）XAdES‑EPES デジタル署名

## よくある質問とトラブルシューティング

| 質問 | 回答 |
|---|---|
| **ActiveX ボタンは macOS の Word で動作しますか？** | macOS の Word は ActiveX コントロールをサポートしていません。ボタンは静的画像として表示されます。クロスプラットフォームのインタラクティブ性が必要な場合は、Office.js を使用したコンテンツ コントロールをご利用ください。 |
| **Markdown ファイルにカスタム CSS が含まれている場合は？** | Aspose.Words は CSS を無視し、標準的な Markdown 構文のみを処理します。CSS で装飾された要素は、インポート後に手動で Word スタイルに変換してください。 |
| **同じグループに後からシェイプを追加できますか？** | 可能です。名前またはインデックスで `GroupShape` を取得し、`AppendChild(newShape)` を呼び出します。変更後は必ず文書を再保存してください。 |
| **署名アルゴリズムを変更するには？** | `signature.SignatureAlgorithm` を `Sign` 呼び出し前に設定します。デフォルトは SHA‑256 で、ほとんどのコンプライアンス要件を満たします。 |
| **隠し画像は Word の UI に表示されますか？** | 表示されませんが、Word のオプションで *隠しテキストの表示* を有効にすれば確認できます。レイアウトを乱さずにメタデータを保存するのに便利です。 |

## 次のステップ

**create group shape docx**、**insert ActiveX command button**、**load markdown into a Word document** ができるようになったら、以下のような拡張を検討してください。

- ActiveX ボタンのクリックに反応する **VBA マクロ** を埋め込む
- Markdown から生成された段落に **カスタム スタイル** を適用する
- `doc.Save("output.pdf", SaveFormat.Pdf)` を使って **PDF** を生成する
- 複数の Markdown ファイルを一括処理し、単一のレポートにまとめる **バッチ処理** を自動化する

これらの拡張により、リッチなグラフィック、インタラクティブ コントロール、Markdown ベースの執筆を組み合わせた完全自動化ドキュメント パイプラインを C# だけで構築できます。

---

*Happy coding! If you found this tutorial*

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した、密接に関連するテーマを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれているので、API の追加機能をマスターしたり、別の実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create markdown from word – Complete C# Guide](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}