---
"description": "تعرّف على كيفية استخدام علامات المستندات المنظمة (SDT) في Aspose.Words لـ Java من خلال هذا الدليل الشامل. أنشئ علامات المستندات المنظمة، وعدّلها، واربطها ببيانات XML مخصصة."
"linktitle": "استخدام علامات المستندات المنظمة (SDT)"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام علامات المستندات المنظمة (SDT) في Aspose.Words لـ Java"
"url": "/ar/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام علامات المستندات المنظمة (SDT) في Aspose.Words لـ Java


## مقدمة حول استخدام علامات المستندات المنظمة (SDT) في Aspose.Words لـ Java

علامات المستندات المنظمة (SDT) ميزة فعّالة في Aspose.Words لجافا، تُمكّنك من إنشاء محتوى منظم ومعالجته داخل مستنداتك. في هذا الدليل الشامل، سنشرح لك الجوانب المختلفة لاستخدام علامات المستندات المنظمة في Aspose.Words لجافا. سواءً كنت مبتدئًا أو مطوّرًا خبيرًا، ستجد في هذه المقالة رؤى قيّمة وأمثلة عملية.

## ابدء

قبل الخوض في التفاصيل، لنبدأ بإعداد بيئتنا وإنشاء SDT أساسي. في هذا القسم، سنتناول المواضيع التالية:

- إنشاء مستند جديد
- إضافة علامة مستند منظمة
- حفظ المستند

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إنشاء علامة مستند منظمة من نوع CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// حفظ المستند
doc.save("WorkingWithSDT.docx");
```

## التحقق من الحالة الحالية لـ Checkbox SDT

بعد إضافة مربع اختيار SDT إلى مستندك، قد ترغب في التحقق من حالته الحالية برمجيًا. قد يكون هذا مفيدًا عند الحاجة إلى التحقق من صحة إدخال المستخدم أو تنفيذ إجراءات محددة بناءً على حالة مربع الاختيار.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // تم تحديد مربع الاختيار
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## تعديل عناصر التحكم في المحتوى

في هذا القسم، سنستكشف كيفية تعديل عناصر تحكم المحتوى في مستندك. سنتناول ثلاثة أنواع من عناصر تحكم المحتوى: نص عادي، وقائمة منسدلة، وصورة.

### تعديل عنصر التحكم في محتوى النص العادي

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // مسح المحتوى الموجود
    sdtPlainText.removeAllChildren();

    // إضافة نص جديد
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### تعديل عنصر التحكم في محتوى القائمة المنسدلة

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // حدد العنصر الثاني من القائمة
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### تعديل عنصر التحكم في محتوى الصورة

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // استبدال الصورة بأخرى جديدة
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## إنشاء عنصر تحكم محتوى ComboBox

يتيح عنصر تحكم محتوى ComboBox للمستخدمين الاختيار من قائمة خيارات مُحددة مسبقًا. لنُنشئ واحدًا في مستندنا.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## العمل مع عنصر التحكم في محتوى النص الغني

عناصر التحكم في محتوى النص الغني مثالية لإضافة نص منسق إلى مستنداتك. لنقم بإنشاء عنصر تحكم وتحديد محتواه.

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## ضبط أنماط التحكم في المحتوى

يمكنك تطبيق أنماط على عناصر تحكم المحتوى لتحسين المظهر المرئي لمستندك. لنرَ كيفية ضبط نمط عنصر تحكم المحتوى.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// تطبيق نمط مخصص
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## ربط SDT ببيانات XML المخصصة

في بعض الحالات، قد تحتاج إلى ربط SDT ببيانات XML مخصصة لإنشاء محتوى ديناميكي. لنستكشف كيفية تحقيق ذلك.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## إنشاء جدول يحتوي على أقسام متكررة مرتبطة ببيانات XML مخصصة

يمكن أن تكون الجداول ذات الأقسام المتكررة مفيدة للغاية لعرض البيانات المنظمة. لنُنشئ جدولًا كهذا ونربطه ببيانات XML مخصصة.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## العمل مع علامات المستندات المنظمة متعددة الأقسام

يمكن أن تمتد علامات المستند المنظمة إلى عدة أقسام في المستند. في هذا القسم، سنستكشف كيفية استخدام علامات المستند المنظمة متعددة الأقسام.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## خاتمة

توفر علامات المستندات المنظمة في Aspose.Words لجافا طريقةً متعددة الاستخدامات لإدارة وتنسيق محتوى مستنداتك. سواءً كنت بحاجة إلى إنشاء قوالب أو نماذج أو مستندات ديناميكية، توفر لك علامات المستندات المنظمة المرونة والتحكم اللازمين. باتباع الأمثلة والإرشادات الواردة في هذه المقالة، يمكنك الاستفادة من قوة علامات المستندات المنظمة لتحسين مهام معالجة مستنداتك.

## الأسئلة الشائعة

### ما هو الغرض من علامات المستندات المنظمة (SDTs)؟

تخدم علامات المستندات المنظمة (SDTs) غرض تنظيم وتنسيق المحتوى داخل المستندات، مما يجعل من الأسهل إنشاء القوالب والنماذج والمستندات المنظمة.

### كيف يمكنني التحقق من الحالة الحالية لـ Checkbox SDT؟

يمكنك التحقق من الحالة الحالية لـ Checkbox SDT باستخدام `setChecked` الطريقة كما هو موضح في المقال.

### هل يمكنني تطبيق الأنماط على عناصر التحكم بالمحتوى؟

نعم، يمكنك تطبيق الأنماط على عناصر التحكم في المحتوى لتخصيص مظهرها في المستند.

### هل من الممكن ربط SDT ببيانات XML المخصصة؟

نعم، يمكنك ربط SDT ببيانات XML مخصصة، مما يسمح بإنشاء محتوى ديناميكي وتعيين البيانات.

### ما هي الأقسام المتكررة في SDTs؟

تتيح لك الأقسام المتكررة في SDTs إنشاء جداول تحتوي على بيانات ديناميكية، حيث يمكن تكرار الصفوف استنادًا إلى بيانات XML المرسومة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}