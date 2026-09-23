---
category: general
date: 2026-02-13
description: C#でPNGを高速にBase64に変換 – 画像のBase64エンコード方法、HTMLへのBase64画像埋め込み方法、そしてWebプロジェクト向けにストリームをメモリへコピーする方法を学びましょう。
draft: false
keywords:
- convert png to base64
- base64 encode image
- embed image html base64
- image stream to base64
- copy stream to memory
language: ja
og_description: C#でPNGをすばやくBase64に変換します。このチュートリアルでは、画像をBase64エンコードする方法、HTMLにBase64画像を埋め込む方法、ストリームをメモリにコピーする方法を紹介します。
og_title: C#でPNGをBase64に変換する – 完全ガイド
tags:
- C#
- image-processing
- data-uri
title: C#でPNGをBase64に変換する – 完全ガイド
url: /ja/net/basic-conversions/convert-png-to-base64-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でPNGをBase64に変換する – 完全ガイド

**PNGをBase64に変換**したいけど、どこから始めればいいかわからないことはありませんか？同じ壁にぶつかる開発者は多いです。画像をHTMLやCSSに直接埋め込む際にこの作業が必要になります。正しい手順さえ分かれば、解決はとてもシンプルです。

このチュートリアルでは、**画像をBase64エンコード**する完全な実行可能サンプルを通して、**データURIで画像をHTMLに埋め込む**方法や、**ストリームをメモリにコピー**してリソースリークを防ぐベストプラクティスを解説します。最後まで読めば、任意の.NETプロジェクトに貼り付けられる再利用可能なスニペットが手に入ります。

## 学べること

- 大文字小文字を区別せずにファイル拡張子を検証する方法。  
- `MemoryStream` を使った **画像ストリームをBase64に変換**する最も安全なパターン。  
- ブラウザが理解できる正しいデータURIの作り方。  
- 元のストリームをクリーンアップして、アプリを軽量に保つ方法。  

外部ライブラリは不要です。 .NET に同梱されている BCL クラスだけで完結します。C# の基本が分かっていて、すでにファイルアップロードを扱うプロジェクトがあればすぐに実装可能です。

---

![PNGファイルからBase64データURIへのフローを示す図 – PNGをBase64に変換](https://example.com/convert-png-to-base64-diagram.png "PNGをBase64に変換する例")

## PNGをBase64に変換 – 手順別解説

以下の5つの論理的ステップに分けて解説します。各見出しはパズルのピースに対応しているので、必要な部分をすぐに見つけられます（AIアシスタントでも同様です）。

### 手順 1: リソースがPNGかどうかを大文字小文字無視で確認

メモリを無駄に消費しないよう、まず受信したファイルが本当にPNGかどうかを確認します。`StringComparison.OrdinalIgnoreCase` フラグを使えば、拡張子の大小文字の組み合わせをすべて処理できます。

```csharp
// Step 1: Verify that the resource is a PNG image (case‑insensitive)
if (args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Continue with conversion...
}
else
{
    // Not a PNG – you might log or throw here
    throw new InvalidOperationException("Only PNG files are supported.");
}
```

*重要ポイント:* JPEG など画像以外を PNG としてエンコードしようとすると、出力が壊れ、後で埋め込むデータURI が機能しなくなります。

### 手順 2: ストリームをメモリにコピー

アップロードハンドラから渡される `Stream` を全体的に読み取る必要があります。`using var` 文を使うことでバッファが自動的に破棄され、**ストリームをメモリにコピー**する処理がクリーンに保たれます。

```csharp
using var memory = new MemoryStream();
args.Stream.CopyTo(memory);
```

*プロのコツ:* 非常に大きなファイルを扱う場合は、`CopyToAsync` を適切なバッファサイズで使用し、スレッドのブロックを回避しましょう。

### 手順 3: 画像をBase64エンコード

画像バイトが `memory` に格納されたら、Base64 文字列に変換します。これが **画像をBase64エンコード**する核心部分です。

```csharp
// Step 3: Encode the buffered bytes as a Base64 string
string base64Data = Convert.ToBase64String(memory.ToArray());
```

*何が起きているか？* `Convert.ToBase64String` はバイト配列を受け取り、ブラウザがバイナリデータに復元できるテキスト表現を返します。

### 手順 4: HTML/CSS 用データURIを構築

データURI を使うと、画像をマークアップに直接埋め込めるため、余計な HTTP リクエストが不要になります。形式は `data:[<mediatype>][;base64],<data>` です。

```csharp
// Step 4: Build a data‑URI that embeds the PNG directly in HTML/CSS
args.ResourceFilePath = $"data:image/png;base64,{base64Data}";
```

後で `<img src="...">` タグ内に `args.ResourceFilePath` を出力すれば、ブラウザは PNG を即座に表示します。

### 手順 5: 元のストリームを解放

画像がデータURIで表現されたので、元の `Stream` は不要になります。`null` に設定しておくと、ガベージコレクタが基になるソケットやファイルハンドルを回収しやすくなります。

```csharp
// Step 5: Release the original stream because the resource is now embedded
args.Stream = null;
```

*エッジケース:* 後で元ファイルをディスクに保存したい場合は、このステップをスキップして別途参照を保持してください。

---

## 完全動作サンプル

すべてのパーツを組み合わせると、アップロードされたリソースを処理する任意のクラスに貼り付けられるコンパクトなメソッドが完成します。

```csharp
using System;
using System.IO;

public class ResourceProcessor
{
    public void ProcessPng(ResourceArgs args)
    {
        // Verify extension (primary check)
        if (!args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
        {
            throw new InvalidOperationException("Only PNG files can be converted to Base64.");
        }

        // Copy the incoming stream into a memory buffer (copy stream to memory)
        using var memory = new MemoryStream();
        args.Stream.CopyTo(memory);

        // Encode the buffered bytes as a Base64 string (base64 encode image)
        string base64Data = Convert.ToBase64String(memory.ToArray());

        // Build a data‑URI that embeds the PNG directly in HTML/CSS (embed image html base64)
        args.ResourceFilePath = $"data:image/png;base64,{base64Data}";

        // Release the original stream because the resource is now embedded (image stream to base64)
        args.Stream = null;
    }
}

// Helper class to mimic incoming arguments
public class ResourceArgs
{
    public string ResourceFileExtension { get; set; }   // e.g., ".png"
    public Stream Stream { get; set; }                 // original file stream
    public string ResourceFilePath { get; set; }       // will hold the data‑URI
}
```

**期待される出力:** `ProcessPng` が実行された後、`args.ResourceFilePath` には次のような文字列が格納されます。

```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

この文字列をそのまま `<img>` タグに貼り付ければ：

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." alt="Converted PNG">
```

画像が即座に表示され、余計なネットワークトラフィックは発生しません。

---

## よくある質問とエッジケース

### PNG が非常に大きい場合は？

画像全体を `MemoryStream` に保持するため、メモリ使用量が急増します。数メガバイトを超えるファイルでは、チャンク単位で Base64 変換をストリーミングするか、エンコード前にリサイズすることを検討してください。

### 非同期にしたい？

もちろん可能です。`CopyTo` を `CopyToAsync` に置き換え、メソッドを `async Task` にすれば、I/O 中に ASP.NET のリクエストスレッドを解放できます。

```csharp
await args.Stream.CopyToAsync(memory);
```

### 他の画像形式でも使える？

コード自体はフォーマットに依存しません。データURI の MIME タイプを `image/jpeg`、`image/gif` などに変更し、拡張子チェックも同様に調整すれば OK です。

### エラー処理はどうすれば？

全体を `try/catch` で囲み、例外をログに記録します。Web API であれば、400 Bad Request と共に分かりやすいメッセージを返すと良いでしょう。

---

## まとめ

これで **C#でPNGをBase64に変換**する手順を最初から最後までマスターしました。チュートリアルでは、ファイルタイプの検証、ストリームの安全なメモリコピー、**画像をBase64エンコード**、正しい **HTMLに埋め込むBase64データURI** の構築、そしてリソースのクリーンアップを網羅しました。

ここからは、オンザフライでの画像リサイズや、生成したデータURI のキャッシュ、SVG プレースホルダーの生成などに挑戦できます。どのシナリオでも、**画像ストリームをBase64に変換してマークアップに直接埋め込む** パターンは堅実な基盤となります。

ワークフローに独自の工夫があればぜひコメントで共有してください。WebAssembly や Blazor での実装例も歓迎です。Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}