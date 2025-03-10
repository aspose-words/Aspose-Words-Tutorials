---
title: जावा के लिए Aspose.Words में फ़ील्ड का उपयोग करना
linktitle: फ़ील्ड का उपयोग करना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: इस चरण-दर-चरण ट्यूटोरियल में जावा फ़ील्ड के लिए Aspose.Words का प्रभावी ढंग से उपयोग करना सीखें। आसानी से गतिशील Word दस्तावेज़ बनाएँ।
weight: 11
url: /hi/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में फ़ील्ड का उपयोग करना


इस चरण-दर-चरण ट्यूटोरियल में, हम आपको बताएंगे कि दस्तावेज़ों को आसानी से मैनिपुलेट करने के लिए Aspose.Words for Java में फ़ील्ड का उपयोग कैसे करें। Aspose.Words for Java एक शक्तिशाली API है जो आपको Word दस्तावेज़ों के साथ प्रोग्रामेटिक रूप से काम करने की अनुमति देता है, जिससे आपको उनकी सामग्री और फ़ॉर्मेटिंग पर पूरा नियंत्रण मिलता है।

## 1 परिचय

जावा के लिए Aspose.Words जावा अनुप्रयोगों में वर्ड दस्तावेज़ों से निपटने वाले किसी भी व्यक्ति के लिए एक आवश्यक उपकरण है। फ़ील्ड प्लेसहोल्डर हैं जो आपके दस्तावेज़ में गतिशील डेटा संग्रहीत कर सकते हैं। यह ट्यूटोरियल आपको दिखाएगा कि फ़ील्ड के साथ प्रभावी ढंग से कैसे काम किया जाए।

## 2. अपना वातावरण स्थापित करना

 शुरू करने से पहले, सुनिश्चित करें कि आपके पास Aspose.Words for Java इंस्टॉल है। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/java/)इसके अलावा, सुनिश्चित करें कि आपके सिस्टम पर जावा और एक एकीकृत विकास वातावरण (आईडीई) जैसे कि एक्लिप्स या इंटेलीज आईडिया स्थापित है।

## 3. वर्ड डॉक्यूमेंट लोड करना

अपने जावा एप्लिकेशन में, आपको वह वर्ड डॉक्यूमेंट लोड करना होगा जिसके साथ आप काम करना चाहते हैं। यहाँ आपको शुरू करने के लिए कोड का एक स्निपेट दिया गया है:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

 प्रतिस्थापित करें`"Your Document Directory"` और`"Your Output Directory"` उचित पथों के साथ.

## 4. मेल मर्ज को अनुकूलित करना

जावा के लिए Aspose.Words मेल मर्ज ऑपरेशन के लिए बेहतरीन सहायता प्रदान करता है। आप मेल मर्ज इवेंट हैंडलर सेट करके मेल मर्ज प्रक्रिया को कस्टमाइज़ कर सकते हैं। इसे करने का तरीका यहां बताया गया है:

```java
// कस्टम कार्य करने के लिए मेल मर्ज इवेंट हैंडलर सेटअप करें।
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// अंतिम और प्रारंभिक रिक्त स्थानों वाले मेल मर्ज मानों को काटें।
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

## 5. दस्तावेज़ को सहेजना

अपने दस्तावेज़ को अनुकूलित करने के बाद, आप इसे निम्नलिखित कोड का उपयोग करके सहेज सकते हैं:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

 प्रतिस्थापित करें`"Your Output Directory"` वांछित आउटपुट पथ के साथ.

## संपूर्ण स्रोत कोड
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// कस्टम कार्य करने के लिए मेल मर्ज इवेंट हैंडलर सेटअप करें।
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// अंतिम और प्रारंभिक रिक्त स्थानों वाले मेल मर्ज मानों को काटें।
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
क्लास HandleMergeField का स्रोत कोड

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <सारांश>
        /// यह हैंडलर दस्तावेज़ में पाए जाने वाले प्रत्येक मेल मर्ज फ़ील्ड के लिए बुलाया जाता है,
        /// डेटा स्रोत में पाए गए प्रत्येक रिकॉर्ड के लिए.
        /// </सारांश>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // हमने निर्णय लिया कि हम चाहते हैं कि सभी बूलियन मानों को चेक बॉक्स फॉर्म फ़ील्ड के रूप में आउटपुट किया जाए।
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                // "कर्सर" को वर्तमान मर्ज फ़ील्ड पर ले जाएँ।
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
        builder.writeln("{{#foreach example}}");
        builder.writeln("{{Image(126pt;126pt):stempel}}");
        builder.writeln("{{/foreach example}}");
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
            // कार्यान्वयन की आवश्यकता नहीं है.
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
        // IF फ़ील्ड के अंदर एक MERGEFIELD डालें।
        // चूँकि IF फ़ील्ड कथन गलत है, इसलिए आंतरिक MERGEFIELD का परिणाम प्रदर्शित नहीं किया जाएगा,
        //और MERGEFIELD को मेल मर्ज के दौरान कोई डेटा प्राप्त नहीं होगा।
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // यदि हम इस फ्लैग को सत्य पर सेट करते हैं, तो हम अभी भी गलत-कथन IF फ़ील्ड के अंदर MERGEFIELDs की गणना कर सकते हैं।
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // परिणाम दस्तावेज़ में दिखाई नहीं देगा क्योंकि IF फ़ील्ड गलत है,
        // लेकिन आंतरिक MERGEFIELD ने वास्तव में डेटा प्राप्त किया।
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeAndConditionalField.docx");
    }
    @Test
    public void mailMergeImageFromBlob() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind employees.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeImageFieldFromBlob());
        Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
        String connString = "jdbc:ucanaccess://" + getDatabaseDir() + "नॉर्थविंड.mdb";
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
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs args)
        {
            // कुछ भी नहीं है।
        }
        /// <सारांश>
        /// इसे तब बुलाया जाता है जब मेल मर्ज इंजन को दस्तावेज़ में Image:XXX मर्ज फ़ील्ड मिलती है।
        /// आपके पास एक इमेज ऑब्जेक्ट, फ़ाइल नाम, या एक स्ट्रीम जिसमें इमेज शामिल है, को वापस करने का अवसर है।
        /// </सारांश>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // फ़ील्ड मान एक बाइट सरणी है, बस इसे कास्ट करें और इस पर एक स्ट्रीम बनाएं।
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // अब मेल मर्ज इंजन स्ट्रीम से छवि पुनः प्राप्त करेगा।
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
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
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
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs args)
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
        /// <सारांश>
        /// दस्तावेज़ में पाए गए प्रत्येक मर्ज फ़ील्ड के लिए कॉल किया गया.
        /// हम या तो मेल मर्ज इंजन को कुछ डेटा लौटा सकते हैं या दस्तावेज़ के साथ कुछ और कर सकते हैं।
        /// इस मामले में हम सेल फ़ॉर्मेटिंग को संशोधित करते हैं।
        /// </सारांश>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // पंक्ति संख्या सम है या विषम, इसके आधार पर रंग का चयन करें।
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //इस समय पूरी पंक्ति के लिए कक्ष गुणधर्म निर्धारित करने का कोई तरीका नहीं है, इसलिए हमें पंक्ति के सभी कक्षों पर पुनरावृति करनी होगी।
                for (int colIdx = 0; colIdx < 4; colIdx++)
                {
                    mBuilder.moveToCell(0, mRowIdx, colIdx, 0);
                    mBuilder.getCellFormat().getShading().setBackgroundPatternColor(rowColor);
                }
                mRowIdx++;
            }
        }
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs args)
        {
            // कुछ भी नहीं है।
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <सारांश>
    /// यदि मान विषम है तो सत्य लौटाता है; यदि मान सम है तो असत्य लौटाता है।
    /// </सारांश>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <सारांश>
    /// डेटाटेबल बनाएं और उसे डेटा से भरें।
    /// वास्तविक जीवन में इस डेटाटेबल को डेटाबेस से भरा जाना चाहिए।
    /// </सारांश>
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

## 6. निष्कर्ष

बधाई हो! आपने सीखा है कि Word दस्तावेज़ों को गतिशील रूप से हेरफेर करने के लिए Aspose.Words for Java में फ़ील्ड का उपयोग कैसे करें। यह शक्तिशाली API आपको अपने दस्तावेज़ों पर पूर्ण नियंत्रण देता है, जिससे यह Java डेवलपर्स के लिए एक मूल्यवान संपत्ति बन जाती है।

## 7. अक्सर पूछे जाने वाले प्रश्न

### प्रश्न 1: मैं Java के लिए Aspose.Words कहां से डाउनलोड कर सकता हूं?
 आप Java के लिए Aspose.Words को यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/java/).

### प्रश्न 2: मैं Java के लिए Aspose.Words हेतु अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूँ?
 आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).

### प्रश्न 3: मुझे Java के लिए Aspose.Words का समर्थन कहां मिल सकता है?
 सहायता के लिए, आप Aspose.Words फ़ोरम पर जा सकते हैं[यहाँ](https://forum.aspose.com/).

### प्रश्न 4: क्या Java के लिए Aspose.Words Word दस्तावेज़ों में HTML सामग्री को संभालने के लिए उपयुक्त है?
हां, Java के लिए Aspose.Words Word दस्तावेज़ों में HTML सामग्री को संभालने के लिए उत्कृष्ट समर्थन प्रदान करता है।

### प्रश्न 5: क्या मैं Java के लिए Aspose.Words का निःशुल्क उपयोग कर सकता हूँ?
 Aspose.Words for Java एक व्यावसायिक उत्पाद है, लेकिन आप इसके फीचर्स को निःशुल्क परीक्षण के माध्यम से देख सकते हैं।[यहाँ](https://releases.aspose.com/).

आज ही Aspose.Words for Java के साथ शुरुआत करें और अपने Word दस्तावेज़ों पर पहले जैसा नियंत्रण रखें!


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
