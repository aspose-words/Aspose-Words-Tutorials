---
title: データテーブルからテーブルを生成する
linktitle: データテーブルからテーブルを生成する
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用して DataTable からテーブルを生成する方法を学びます。フォーマットされたテーブルを含むプロフェッショナルな Word 文書を簡単に作成します。
weight: 11
url: /ja/java/table-processing/generate-table-from-datatable/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# データテーブルからテーブルを生成する

## 導入

データ ソースから動的にテーブルを作成することは、多くのアプリケーションで一般的なタスクです。レポート、請求書、データ サマリーなどを生成する場合でも、プログラムでテーブルにデータを入力できれば、時間と労力を大幅に節約できます。このチュートリアルでは、Aspose.Words for Java を使用して DataTable からテーブルを生成する方法について説明します。プロセスを管理しやすいステップに分割し、各部分を明確に理解できるようにします。

## 前提条件

コードに進む前に、開始するために必要なものがすべて揃っていることを確認しましょう。

1.  Java開発キット（JDK）：マシンにJDKがインストールされていることを確認してください。[Oracleのウェブサイト](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2.  Aspose.Words for Java: Aspose.Wordsライブラリが必要です。最新バージョンは以下からダウンロードできます。[Aspose のリリース ページ](https://releases.aspose.com/words/java/).

3. IDE: IntelliJ IDEA や Eclipse などの統合開発環境 (IDE) を使用すると、コーディングが容易になります。

4. Java の基礎知識: Java プログラミングの概念を理解しておくと、コード スニペットをよりよく理解するのに役立ちます。

5. サンプル データ: このチュートリアルでは、「List of people.xml」という名前の XML ファイルを使用してデータ ソースをシミュレートします。テスト用にサンプル データを使用してこのファイルを作成できます。

## ステップ1: 新しいドキュメントを作成する

まず、テーブルを配置する新しいドキュメントを作成する必要があります。これが作業のキャンバスになります。

```java
Document doc = new Document();
```

ここで、新しいインスタンスを作成します`Document`オブジェクト。これは、テーブルを構築する作業ドキュメントとして機能します。

## ステップ2: DocumentBuilderを初期化する

次に、`DocumentBuilder`クラスを使用すると、ドキュメントをより簡単に操作できます。

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

の`DocumentBuilder`オブジェクトは、ドキュメントに表、テキスト、その他の要素を挿入するためのメソッドを提供します。

## ステップ3: ページの向きを設定する

テーブルの幅が広くなることが予想されるため、ページの向きを横向きに設定します。

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

この手順は、テーブルがページ上で切り取られることなく適切に収まるようにするために重要です。

## ステップ4: XMLからデータを読み込む

さて、XMLファイルからデータをロードする必要があります`DataTable`ここから私たちのデータが出てきます。

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

ここでは、XMLファイルを読み込み、データセットから最初のテーブルを取得します。`DataTable`ドキュメントに表示するデータを保持します。

## ステップ5: DataTableからテーブルをインポートする

ここで、データをテーブルとしてドキュメントにインポートするという、興味深い部分が始まります。

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

このメソッドは`importTableFromDataTable`、通過`DocumentBuilder`、 私たちの`DataTable`、および列見出しを含めるかどうかを示すブール値。

## ステップ6: テーブルのスタイルを設定する

テーブルが完成したら、見栄えを良くするためにスタイルを適用できます。

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

このコードは、定義済みのスタイルをテーブルに適用し、視覚的な魅力と読みやすさを向上させます。

## ステップ7: 不要なセルを削除する

画像列など、表示したくない列がある場合は、簡単に削除できます。

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

この手順により、テーブルには関連する情報のみが表示されるようになります。

## ステップ8: ドキュメントを保存する

最後に、生成されたテーブルを含むドキュメントを保存します。

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

この行は、指定されたディレクトリにドキュメントを保存し、結果を確認できるようにします。

## importTableFromDataTable メソッド

詳しく見てみましょう`importTableFromDataTable`メソッド。このメソッドは、テーブル構造を作成し、そこにデータを入力する役割を担います。

### ステップ1: テーブルを開始する

まず、ドキュメント内に新しい表を作成する必要があります。

```java
Table table = builder.startTable();
```

これにより、ドキュメント内の新しいテーブルが初期化されます。

### ステップ2: 列見出しを追加する

列見出しを含める場合は、`importColumnHeadings`フラグ。

```java
if (importColumnHeadings) {
    //元の書式を保存
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    //見出しの書式を設定する
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    //列名を挿入する
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    //元の書式を復元する
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

このコードブロックは見出し行をフォーマットし、`DataTable`.

### ステップ3: テーブルにデータを入力する

さて、各行をループして`DataTable`テーブルにデータを挿入します。

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

このセクションでは、さまざまなデータ型を処理し、日付を適切にフォーマットしながら、他のデータをテキストとして挿入します。

### ステップ4: テーブルを終了する

最後に、すべてのデータが挿入されたらテーブルを完成します。

```java
builder.endTable();
```

この行はテーブルの終わりを示し、`DocumentBuilder`このセクションが完了したことを確認します。

## 結論

これで完了です。Aspose.Words for Java を使用して DataTable からテーブルを生成する方法を学習しました。これらの手順に従うことで、さまざまなデータ ソースに基づいてドキュメント内に動的なテーブルを簡単に作成できます。レポートを作成する場合でも、請求書を作成する場合でも、この方法によりワークフローが合理化され、ドキュメント作成プロセスが強化されます。

## よくある質問

### Aspose.Words for Java とは何ですか?
Aspose.Words for Java は、Word 文書をプログラムで作成、操作、変換するための強力なライブラリです。

### Aspose.Words を無料で使用できますか?
はい、Asposeは無料試用版を提供しています。こちらからダウンロードできます。[ここ](https://releases.aspose.com/).

### Aspose.Words でテーブルにスタイルを設定するにはどうすればよいですか?
ライブラリによって提供される定義済みのスタイル識別子とオプションを使用してスタイルを適用できます。

### テーブルに挿入できるデータの種類は何ですか?
テキスト、数値、日付など、さまざまなデータ型を挿入でき、それに応じて書式設定できます。

### Aspose.Words のサポートはどこで受けられますか?
サポートを見つけたり質問したりできます[Aspose フォーラム](https://forum.aspose.com/c/words/8/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
