---
"description": "このステップバイステップのチュートリアルで、Aspose.Words for Java のフィールドを効果的に使用する方法を学びましょう。動的な Word 文書を簡単に作成できます。"
"linktitle": "フィールドの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でのフィールドの使用"
"url": "/ja/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのフィールドの使用


このステップバイステップのチュートリアルでは、Aspose.Words for Java のフィールドを使ってドキュメントを簡単に操作する方法を解説します。Aspose.Words for Java は、Word ドキュメントをプログラムで操作し、コンテンツと書式を完全に制御できる強力な API です。

## 1. はじめに

Aspose.Words for Javaは、JavaアプリケーションでWord文書を扱うすべての人にとって必須のツールです。フィールドは、文書内の動的なデータを保存できるプレースホルダーです。このチュートリアルでは、フィールドを効果的に操作する方法を説明します。

## 2. 環境の設定

始める前に、Aspose.Words for Javaがインストールされていることを確認してください。こちらからダウンロードできます。 [ここ](https://releases.aspose.com/words/java/)また、Java と、Eclipse や IntelliJ IDEA などの統合開発環境 (IDE) がシステムにインストールされていることを確認してください。

## 3. Word文書の読み込み

Javaアプリケーションでは、作業対象のWord文書を読み込む必要があります。まずは、以下のコードをご覧ください。

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

交換する `"Your Document Directory"` そして `"Your Output Directory"` 適切なパスを使用します。

## 4. 差し込み印刷のカスタマイズ

Aspose.Words for Java は、差し込み印刷操作を強力にサポートします。差し込み印刷イベントハンドラーを設定することで、差し込み印刷プロセスをカスタマイズできます。設定方法は以下の通りです。

```java
// カスタム作業を実行するために、メール マージ イベント ハンドラーを設定します。
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// 差し込み印刷値の末尾と先頭の空白をトリミングします。
doc.getMailMerge().setTrimWhitespaces(false);

String[] fieldNames = {
    "RecipientName", "SenderName", "FaxNumber", "PhoneNumber",
    "Subject", "Body", "Urgent", "ForReview", "PleaseComment"
};

Object[] fieldValues = {
    "Josh", "Jenny", "123456789", "", "Hello",
    "<b>HTML Body Test message 1</b>", true, false, true
};

doc.getMailMerge().execute(fieldNames, fieldValues);
```

## 5. ドキュメントの保存

ドキュメントをカスタマイズしたら、次のコードを使用して保存できます。

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

交換する `"Your Output Directory"` 希望する出力パスを指定します。

## 完全なソースコード
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// カスタム作業を実行するために、メール マージ イベント ハンドラーを設定します。
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// 差し込み印刷値の末尾と先頭の空白をトリミングします。
doc.getMailMerge().setTrimWhitespaces(false);
String[] fieldNames = {
	"RecipientName", "SenderName", "FaxNumber", "PhoneNumber",
	"Subject", "Body", "Urgent", "ForReview", "PleaseComment"
};
Object[] fieldValues = {
	"Josh", "Jenny", "123456789", "", "Hello",
	"<b>HTML Body Test message 1</b>", true, false, true
};
doc.getMailMerge().execute(fieldNames, fieldValues);
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```
HandleMergeFieldクラスのソースコード

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <要約>
        /// このハンドラは文書内の差し込み印刷フィールドごとに呼び出されます。
        //データ ソース内で見つかったすべてのレコードに対して / を実行します。
        /// </サマリー>
        public void /*IFieldMergingコールバック。*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // すべてのブール値をチェック ボックス フォーム フィールドとして出力することにしました。
            if (e.getFieldValue() instanceof /*ブール値*/Boolean)
            {
                // 「カーソル」を現在の差し込みフィールドに移動します。
                mBuilder.moveToMergeField(e.getFieldName());
                String checkBoxName = MessageFormat.format("{0}{1}", e.getFieldName(), e.getRecordIndex());
                mBuilder.insertCheckBox(checkBoxName, (Boolean) e.getFieldValue(), 0);
                return;
            }
            switch (e.getFieldName())
            {
                case "Body":
                    mBuilder.moveToMergeField(e.getFieldName());
                    mBuilder.insertHtml((String) e.getFieldValue());
                    break;
                case "Subject":
                {
                    mBuilder.moveToMergeField(e.getFieldName());
                    String textInputName = MessageFormat.format("{0}{1}", e.getFieldName(), e.getRecordIndex());
                    mBuilder.insertTextInput(textInputName, TextFormFieldType.REGULAR, "", (String) e.getFieldValue(), 0);
                    break;
                }
            }
        }
        public void imageFieldMerging(ImageFieldMergingArgs args)
        {
            args.setImageFileName("Image.png");
            args.getImageWidth().setValue(200.0);
            args.setImageHeight(new MergeFieldImageDimension(200.0, MergeFieldImageDimensionUnit.PERCENT));
        }
        private DocumentBuilder mBuilder;
    }
    @Test
    public void mailMergeImageField() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("
{{#foreach example}}");
        builder.writeln("
{{Image(126pt;126pt):stempel}}");
        builder.writeln("
{{/foreach example}}");
        doc.getMailMerge().setUseNonMergeFields(true);
        doc.getMailMerge().setTrimWhitespaces(true);
        doc.getMailMerge().setUseWholeParagraphAsRegion(false);
        doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS
                | MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS
                | MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS
                | MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);
        doc.getMailMerge().setFieldMergingCallback(new ImageFieldMergingHandler());
        doc.getMailMerge().executeWithRegions(new DataSourceRoot());
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeImageField.docx");
    }
    private static class ImageFieldMergingHandler implements IFieldMergingCallback
    {
        public void fieldMerging(FieldMergingArgs args)
        {
            //  実装は必須ではありません。
        }
        public void imageFieldMerging(ImageFieldMergingArgs args) throws Exception
        {
            Shape shape = new Shape(args.getDocument(), ShapeType.IMAGE);
            {
                shape.setWidth(126.0); shape.setHeight(126.0); shape.setWrapType(WrapType.SQUARE);
            }
            shape.getImageData().setImage("Your Directory Path" + "Mail merge image.png");
            args.setShape(shape);
        }
    }
    public static class DataSourceRoot implements IMailMergeDataSourceRoot
    {
        public IMailMergeDataSource getDataSource(String s)
        {
            return new DataSource();
        }
        private static class DataSource implements IMailMergeDataSource
        {
            private boolean next = true;
            private String tableName()
            {
                return "example";
            }
            @Override
            public String getTableName() {
                return tableName();
            }
            public boolean moveNext()
            {
                boolean result = next;
                next = false;
                return result;
            }
            public IMailMergeDataSource getChildDataSource(String s)
            {
                return null;
            }
            public boolean getValue(String fieldName, Ref<Object> fieldValue)
            {
                fieldValue.set(null);
                return false;
            }
        }
    }
    @Test
    public void mailMergeAndConditionalField() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // IF フィールド内にネストされた MERGEFIELD を挿入します。
        // IFフィールドステートメントが偽であるため、内部のMERGEFIELDの結果は表示されません。
        // MERGEFIELD は、差し込み印刷中にデータを一切受信しません。
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // このフラグを true に設定すると、偽ステートメントの IF フィールド内の MERGEFIELD をカウントすることができます。
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // IFフィールドが偽であるため、結果は文書に表示されません。
        // しかし、内部の MERGEFIELD は確かにデータを受信しました。
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeAndConditionalField.docx");
    }
    @Test
    public void mailMergeImageFromBlob() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind employees.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeImageFieldFromBlob());
        Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
        String connString = "jdbc:ucanaccess://" + getDatabaseDir() + "Northwind.mdb";
        Connection connection = DriverManager.getConnection(connString, "Admin", "");
        Statement statement = connection.createStatement();
        ResultSet resultSet = statement.executeQuery("SELECT * FROM Employees");
        DataTable dataTable = new DataTable(resultSet, "Employees");
        IDataReader dataReader = new DataTableReader(dataTable);
        doc.getMailMerge().executeWithRegions(dataReader, "Employees");
        connection.close();
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeImageFromBlob.docx");
    }
    public static class HandleMergeImageFieldFromBlob implements IFieldMergingCallback
    {
        public void /*IFieldMergingコールバック。*/fieldMerging(FieldMergingArgs args)
        {
            // 何もしないでください。
        }
        /// <要約>
        /// これは、差し込み印刷エンジンがドキュメント内で Image:XXX 差し込み印刷フィールドに遭遇したときに呼び出されます。
        /// Image オブジェクト、ファイル名、または画像を含むストリームを返すことができます。
        /// </サマリー>
        public void /*IFieldMergingコールバック。*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // フィールド値はバイト配列なので、それをキャストしてストリームを作成するだけです。
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // これで、差し込み印刷エンジンはストリームから画像を取得します。
            e.setImageStream(imageStream);
        }
    }
    @Test
    public void handleMailMergeSwitches() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Field sample - MERGEFIELD.docx");
        doc.getMailMerge().setFieldMergingCallback(new MailMergeSwitches());
        final String HTML = "<html>\r\n                    <h1>Hello world!</h1>\r\n            </html>";
        doc.getMailMerge().execute(new String[] { "htmlField1" }, new Object[] { HTML });
        doc.save("Your Directory Path" + "WorkingWithFields.HandleMailMergeSwitches.docx");
    }
    public static class MailMergeSwitches implements IFieldMergingCallback
    {
        public void /*IFieldMergingコールバック。*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (e.getFieldName().startsWith("HTML"))
            {
                if (e.getField().getFieldCode().contains("\\b"))
                {
                    FieldMergeField field = e.getField();
                    DocumentBuilder builder = new DocumentBuilder(e.getDocument());
                    builder.moveToMergeField(e.getDocumentFieldName(), true, false);
                    builder.write(field.getTextBefore());
                    builder.insertHtml(e.getFieldValue().toString());
                    e.setText("");
                }
            }
        }
        public void /*IFieldMergingコールバック。*/imageFieldMerging(ImageFieldMergingArgs args)
        {
        }
    }
    @Test
    public void alternatingRows() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeFieldAlternatingRows());
        DataTable dataTable = getSuppliersDataTable();
        doc.getMailMerge().executeWithRegions(dataTable);
        doc.save("Your Directory Path" + "WorkingWithFields.AlternatingRows.doc");
    }
    private static class HandleMergeFieldAlternatingRows implements IFieldMergingCallback
    {
        /// <要約>
        /// ドキュメント内で検出されたすべてのマージ フィールドに対して呼び出されます。
        /// 差し込み印刷エンジンにデータを返すか、ドキュメントに対して他の処理を実行することができます。
        /// この場合は、セルの書式を変更します。
        /// </サマリー>
        public void /*IFieldMergingコールバック。*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // 行番号が偶数か奇数かに応じて色を選択します。
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // 現時点では行全体のセルのプロパティを設定する方法はないため、行内のすべてのセルを反復処理する必要があります。
                for (int colIdx = 0; colIdx < 4; colIdx++)
                {
                    mBuilder.moveToCell(0, mRowIdx, colIdx, 0);
                    mBuilder.getCellFormat().getShading().setBackgroundPatternColor(rowColor);
                }
                mRowIdx++;
            }
        }
        public void /*IFieldMergingコールバック。*/imageFieldMerging(ImageFieldMergingArgs args)
        {
            // 何もしないでください。
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <要約>
    /// 値が奇数の場合は true を返し、偶数の場合は false を返します。
    /// </サマリー>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <要約>
    /// DataTable を作成し、データを入力します。
    /// 実際には、この DataTable にはデータベースからデータが入力される必要があります。
    /// </サマリー>
    private DataTable getSuppliersDataTable()
    {
        DataTable dataTable = new DataTable("Suppliers");
        dataTable.getColumns().add("CompanyName");
        dataTable.getColumns().add("ContactName");
        for (int i = 0; i < 10; i++)
        {
            DataRow datarow = dataTable.newRow();
            dataTable.getRows().add(datarow);
            datarow.set(0, "Company " + i);
            datarow.set(1, "Contact " + i);
        }
        return dataTable;
	}
}
```

## 6. 結論

おめでとうございます！Aspose.Words for Javaのフィールドを使ってWord文書を動的に操作する方法を学習しました。この強力なAPIは文書を完全に制御できるため、Java開発者にとって貴重な資産となります。

## 7. よくある質問

### Q1: Aspose.Words for Java はどこからダウンロードできますか?
Aspose.Words for Javaは以下からダウンロードできます。 [ここ](https://releases。aspose.com/words/java/).

### Q2: Aspose.Words for Java の一時ライセンスを取得するにはどうすればよいですか?
臨時免許証は以下から取得できます。 [ここ](https://purchase。aspose.com/temporary-license/).

### Q3: Aspose.Words for Java のサポートはどこで受けられますか?
サポートについては、Aspose.Words フォーラムをご覧ください。 [ここ](https://forum。aspose.com/).

### Q4: Aspose.Words for Java は Word 文書内の HTML コンテンツの処理に適していますか?
はい、Aspose.Words for Java は、Word 文書内の HTML コンテンツの処理に優れたサポートを提供します。

### Q5: Aspose.Words for Java を無料で使用できますか?
Aspose.Words for Javaは商用製品ですが、無料トライアルでその機能を試すことができます。 [ここ](https://releases。aspose.com/).

今すぐ Aspose.Words for Java を使い始めて、これまでにない方法で Word 文書を制御しましょう。




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}