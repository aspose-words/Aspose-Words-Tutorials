---
category: general
date: 2026-01-13
description: C# を使用してプログラムで Word 文書を作成し、OpenType バリエーションの設定方法を学び、docx として保存する。開発者向けの迅速で完全なチュートリアル。
draft: false
keywords:
- create word document
- save document as docx
- how to set opentype
language: ja
og_description: C# と Aspose.Words で Word 文書を作成し、OpenType バリエーション設定を行い、docx として保存します。完全なコードと解説付き。
og_title: Aspose.WordsでWord文書を作成する – 完全ガイド
tags:
- Aspose.Words
- C#
- OpenType
title: Aspose.WordsでWord文書を作成する – ステップバイステップガイド
url: /ja/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.WordsでWord文書を作成 – ステップバイステップガイド

コードから **create word document**（Word文書を作成）する必要があったが、どこから始めればよいかわからないことはありませんか？ あなただけではありません—多くの開発者が最初にプログラムでWordファイルを生成しようとしたときに同じ壁にぶつかります。このチュートリアルでは、新しい `.docx` を作成し、可変ウェイトフォントを適用し、最終的に **save document as docx**（文書をDOCXとして保存）する方法を汗ひとつかかずに示します。さらに、**how to set OpenType**（OpenTypeのバリエーション設定）を行う手順も解説し、夢見ていたヘビーコンデンスドな外観を実現します。

Aspose.Words for .NET ライブラリを使用します。このライブラリは低レベルの Office Open XML の詳細を抽象化し、コンテンツに集中できるようにします。このガイドの最後までに、Word 文書を作成し、OpenType を構成し、スタイル付きテキストの行を書き込み、ファイルをディスクに書き出す実行可能な C# コンソール アプリが手に入ります。外部ツールや手動の XML 操作は不要で、クリーンで読みやすいコードだけです。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）
- 有効な Aspose.Words for .NET ライセンスまたは無料評価キー
- C# の構文と Visual Studio（またはお好みの IDE）に関する基本的な知識
- 任意: **Roboto Flex** のような可変ウェイトフォントをマシンにインストール（例ではこれを使用）

> **Pro tip:** ライセンスをまだお持ちでない場合は、Aspose のウェブサイトから一時的な評価キーを取得できます—取得したキーをプロジェクトの `App.config` にドロップするか、プログラムで設定してください。

---

## ステップ 1 – Word文書の作成

最初に行うべきことは、空の `Document` オブジェクトをインスタンス化することです。これは、後で内容を埋め込むための新しい空の Word ファイルを開くイメージです。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Why this matters:** `Document` オブジェクトはメモリ上の Word ファイル全体を表します。これがあれば、段落、テーブル、画像、さらにはカスタム OpenType 設定さえも追加できます。これは Aspose で **create word document** 操作を行うすべての基盤です。

---

## ステップ 2 – DocumentBuilder の初期化

`DocumentBuilder` は Aspose が提供するコンテンツ書き込み用のフレンドリーなラッパーです。文書内の現在のカーソル位置を把握しており、シンプルなメソッド呼び出しでテキストやシェイプなどを追加できます。

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);
```

> **What’s happening under the hood?** ビルダーは内部で `Node` 参照を保持しているため、`Writeln` のような呼び出しは自動的に新しい段落を作成し、カーソルを前方に移動します。これにより、文書のノードツリーを手動で管理する手間が省けます。

---

## ステップ 3 – OpenType バリエーション設定の方法

ここからが本題です：可変ウェイトフォントの設定です。`wght`（ウェイト）や `wdth`（幅）といった OpenType バリエーション軸を使うと、複数の静的フォントをロードする代わりに単一のフォントファイルを細かく調整できます。

```csharp
// Step 3: Set a variable‑weight font and specify OpenType variation settings
builder.Font.Name = "Roboto Flex";
builder.Font.OpenTypeFontVariationSettings = new OpenTypeFontVariationSettings
{
    { "wght", 800 }, // bold weight
    { "wdth", 75 }   // condensed width
};
```

> **How this works:** `OpenTypeFontVariationSettings` は辞書型コレクションで、キーは 4 文字の OpenType タグ、値は数値設定です。これを `builder.Font` に割り当てると、以降に書き込むすべてのテキストがそのバリエーションを継承します。これが Aspose.Words で段落に対して **how to set OpenType** を行うコアです。

---

## ステップ 4 – 設定したフォントでテキストを書き込む

フォントとそのバリエーションが準備できたので、ヘビーコンデンスドスタイルを示すテキスト行を追加できます。

```csharp
// Step 4: Write a line of text using the configured font variations
builder.Writeln("Heavy‑condensed text using OpenType variations.");
```

> **Result you’ll see:** 文は Roboto Flex、ウェイト 800、幅 75 % で表示されます—実質的に太くて狭い外観で、文書内で目立ちます。

---

## ステップ 5 – DOCXとして文書を保存

最後に、メモリ上の文書を実際の `.docx` ファイルとして永続化します。ここで **save document as docx** というフレーズが本格的に登場します。

```csharp
// Step 5: Save the document to a file
document.Save("YOUR_DIRECTORY/VarFont.docx");
```

> **Why you should care:** DOCX 形式で保存すると、Microsoft Word、Google Docs、その他 Office Open XML を理解するツールとの互換性が最大化されます。Aspose は PDF、HTML、プレーンテキストへのエクスポートもサポートしていますが、DOCX は後からの編集に最も柔軟です。

![Create word document example – 生成された Word ファイルでヘビーコンデンスドテキストを示すスクリーンショット](/images/create-word-document-example.png)

*Image alt text*: **OpenType スタイルのテキストを示す create word document の例**

---

## 完全な動作例

すべてをまとめた完全なプログラムを以下に示します。新しいコンソール アプリ プロジェクトにコピー＆ペーストして使用できます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace WordVarFontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document document = new Document();

            // 2️⃣ Initialize a DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Configure OpenType variation settings (how to set OpenType)
            builder.Font.Name = "Roboto Flex";
            builder.Font.OpenTypeFontVariationSettings = new OpenTypeFontVariationSettings
            {
                { "wght", 800 }, // bold weight
                { "wdth", 75 }   // condensed width
            };

            // 4️⃣ Write styled text
            builder.Writeln("Heavy‑condensed text using OpenType variations.");

            // 5️⃣ Save the file (save document as docx)
            string outputPath = @"C:\Temp\VarFont.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document created and saved to: {outputPath}");
        }
    }
}
```

**コンソールの期待出力**

```
Document created and saved to: C:\Temp\VarFont.docx
```

生成された `VarFont.docx` を Microsoft Word で開くと、太くて狭いスタイルでレンダリングされた行が表示されます—OpenType 設定が要求した通りの結果です。

---

## よくある質問とエッジケース

### 可変ウェイトフォントがインストールされていない場合は？

Aspose.Words はデフォルトフォントにフォールバックし、バリエーション軸を無視します。その結果、通常のウェイトで表示されることがあります。確実に効果を得るには、フォントファイルをアプリに同梱して `FontSettings` で登録するか、対象マシンにフォントをインストールしてください。

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true);
document.FontSettings = fontSettings;
```

### 複数の OpenType 軸を設定できますか？

もちろん可能です。`OpenTypeFontVariationSettings` コレクションは任意の数のタグ（`ital`、`opsz`、`GRAD` など）を保持できます。キー/バリューのペアを追加するだけです。

```csharp
builder.Font.OpenTypeFontVariationSettings.Add("ital", 1); // italic
builder.Font.OpenTypeFontVariationSettings.Add("opsz", 14); // optical size
```

### 古い .NET Framework バージョンでも動作しますか？

はい。API は .NET Framework 4.5+ と .NET Core/5/6 全体で安定しています。対象フレームワークに合わせた Aspose.Words DLL を参照すれば問題ありません。

---

## 結論

これで、Aspose.Words for .NET を使用して **create word document** をプログラムで行い、正確な **OpenType** バリエーション設定を適用し、**save document as docx** するエンドツーエンドの実例が手に入りました。手順はシンプルです：`Document` をインスタンス化し、`DocumentBuilder` を接続し、フォントの OpenType 軸を調整し、コンテンツを書き込み、ファイルを永続化するだけです。

ここからはさらに実験できます—テーブルを追加したり、画像を埋め込んだり、データをループして複数ページのレポートを生成したりしてください。同じパターンは請求書、証明書、動的契約書の作成にも適用できます。必要なカスタムフォントは必ず登録し、使用しているバリエーションタグに注意してください。これが可変フォントの真の力を引き出す鍵です。

コーディングを楽しんでください。問題が発生したり、独自の工夫を見つけた場合は遠慮なくコメントを残してください！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}