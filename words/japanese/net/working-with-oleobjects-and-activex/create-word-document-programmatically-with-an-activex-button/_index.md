---
category: general
date: 2026-10-20
description: Aspose.Words を使用してプログラムで Word ドキュメントを作成し、コマンド ボタンを追加します。ActiveX コントロールの挿入方法とボタンのキャプション設定方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: ja
lastmod: 2026-10-20
og_description: プログラムでWord文書を作成し、ActiveXコマンドボタンを埋め込みます。このチュートリアルでは、コントロールの挿入方法とAspose.Wordsを使用したキャプションの設定方法を説明します。
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Word文書をプログラムで作成 – ActiveXボタンを追加
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: ActiveX ボタンでプログラム的に Word 文書を作成する
url: /ja/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ActiveX ボタンで Word ドキュメントをプログラムから作成する

Aspose.Words を使用してプログラムから Word ドキュメントを作成し、ユーザーがクリックできるコマンド ボタンを追加します。このガイドでは、ActiveX コントロールの挿入、プロパティの設定、そして結果を **.docx** ファイルとして保存する手順を説明します。

コンソール アプリケーションにコピーできる完全な実行可能サンプルが表示されます。チュートリアルの最後までに、完全に機能するコマンド ボタンを含む Word ファイルを生成でき、C# コードから抜けることなく **add command button**、**add activex control**、**insert activex button**、**set button caption** の方法が理解できるようになります。

## 前提条件

* .NET 6.0 SDK 以降がインストールされていること  
* Visual Studio 2022（または任意の C# 対応 IDE）  
* Aspose.Words for .NET のライセンス ファイル（無料トライアルでもこの例は動作します）  
* C# と .NET プロジェクト システムの基本的な知識  

ActiveX のサポートはライブラリに組み込まれているため、**Aspose.Words** 以外に追加の NuGet パッケージは必要ありません。

## 手順 1: プロジェクトをセットアップし Aspose.Words を追加する

1. ターミナルまたは Visual Studio を開き、新しいコンソール プロジェクトを作成します:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Aspose.Words パッケージを追加します:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (オプション) ライセンス ファイルがある場合はプロジェクトのルートに配置し、評価用の透かしを除去するために `Program.cs` の先頭に次の行を追加します:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## 手順 2: Word ドキュメントをプログラムから作成 – ドキュメントの初期化

最初の操作は **create Word document programmatically** です。`Document` オブジェクトと、ドキュメントの内容を編集できる `DocumentBuilder` をインスタンス化して実行します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` はファイル全体を表し、`DocumentBuilder` はドキュメント内の任意の位置に移動できるカーソルを保持します。この分離により API がすっきりし、後で **add activex control** を行う際に低レベル構造を手動で管理する必要がなくなります。

## 手順 3: コマンド ボタンを追加 – ActiveX コントロールの挿入

ここでは `OleControlType.CommandButton` タイプの ActiveX コントロールを挿入して **add command button** を行います。`InsertForms2OleControl` メソッドはコントロールの種類、位置 (`Point`) およびサイズ (`Size`) を指定する必要があります。

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

上記の呼び出しは、指定した正確な座標に **insert activex button** をドキュメントに挿入します。座標はポイント単位で測定されます (1 pt ≈ 1/72 in)。特定の段落にボタンを配置したい場合は、まずビルダーのカーソルを移動させます:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## 手順 4: ボタンのキャプションを設定 – コマンド ボタンのテキストをカスタマイズする

ラベルのないボタンは分かりにくいため、**set button caption** で意味のあるテキストを設定します。`Caption` プロパティはボタンに表示されるテキストを定義し、`Name` はコントロールにプログラム上の識別子を付与します。

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

後でドキュメントをマクロ有効形式 (`.docm`) にエクスポートする場合、`OnClick` の値は VBA マクロ名と一致している必要があります。普通の `.docx` の場合、このプロパティは保存されますが実行はされず、ほとんどの自動化シナリオでは問題ありません。

## 手順 5: ActiveX ボタンを含むドキュメントを保存する

コントロールの設定が完了したら、**save the document** が可能です。書き込み権限のあるディレクトリを選択し、最大の互換性を得るために `.docx` 拡張子を使用します。

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

生成されたファイルを Microsoft Word で開くと、指定した座標に **Submit** とラベル付けされたボタンが表示されます。デスクトップ クライアントでボタンをクリックすると、`SubmitForm` マクロが存在すれば実行を試みます。

## 手順 6: 結果を確認し、一般的な問題をトラブルシュートする

1. Microsoft Word で `ActiveXCommandButton.docx` を開きます。  
2. **Design Mode**（開発タブ → **Design Mode**）に切り替えて、ボタンの枠線を確認します。  
3. ボタンが表示されない場合は、**Developer** タブが有効になっているか、使用している Word バージョンが ActiveX コントロールをサポートしているかを確認してください。  
4. マクロ有効ファイル (`.docm`) の場合、`OnClick` のマクロ名が VBA ルーチンと一致していることを確認してください。そうでないと Word がセキュリティ警告を表示します。

### プロのコツ

ActiveX コントロールは Windows のみで利用可能です。クロスプラットフォームでのインタラクティブ性が必要な場合は、ActiveX ボタンの代わりに **Content Controls**（`RichTextContentControl`）の使用を検討してください。

## 完全なソースコード

以下は完全な実行可能プログラムです。`Program.cs` にコピーし、`dotnet run` を実行してください。



## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [ActiveX ボタンで Word ドキュメントを作成 – C# ガイド](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Aspose.Words で Word ドキュメントにコマンド ボタンを追加 – 完全ガイド](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Aspose.Words で Word ドキュメント ボタンを作成 – 完全コード例](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}