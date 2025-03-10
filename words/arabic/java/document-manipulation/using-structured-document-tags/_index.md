---
title: استخدام علامات المستندات المنظمة (SDT) في Aspose.Words لـ Java
linktitle: استخدام علامات المستندات المنظمة (SDT)
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية استخدام علامات المستندات المنظمة (SDT) في Aspose.Words for Java من خلال هذا الدليل الشامل. قم بإنشاء علامات المستندات المنظمة وتعديلها وربطها ببيانات XML المخصصة.
weight: 19
url: /ar/java/document-manipulation/using-structured-document-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدام علامات المستندات المنظمة (SDT) في Aspose.Words لـ Java


## مقدمة حول استخدام علامات المستندات المنظمة (SDT) في Aspose.Words لـ Java

تُعد علامات المستندات المنظمة (SDT) ميزة قوية في Aspose.Words for Java تتيح لك إنشاء محتوى منظم داخل مستنداتك ومعالجته. في هذا الدليل الشامل، سنطلعك على الجوانب المختلفة لاستخدام علامات المستندات المنظمة في Aspose.Words for Java. سواء كنت مبتدئًا أو مطورًا متمرسًا، فستجد رؤى قيمة وأمثلة عملية في هذه المقالة.

## ابدء

قبل أن نتعمق في التفاصيل، دعنا نعد بيئتنا وننشئ SDT أساسيًا. في هذا القسم، سنغطي الموضوعات التالية:

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

بمجرد إضافة مربع اختيار SDT إلى مستندك، قد ترغب في التحقق من حالته الحالية برمجيًا. يمكن أن يكون هذا مفيدًا عندما تحتاج إلى التحقق من صحة إدخال المستخدم أو تنفيذ إجراءات محددة بناءً على حالة مربع الاختيار.

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

في هذا القسم، سنستكشف كيفية تعديل عناصر التحكم في المحتوى داخل المستند. وسنتناول ثلاثة أنواع من عناصر التحكم في المحتوى: النص العادي والقائمة المنسدلة والصورة.

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

يتيح عنصر التحكم في محتوى ComboBox للمستخدمين الاختيار من قائمة محددة مسبقًا من الخيارات. فلنقم بإنشاء عنصر تحكم في مستندنا.

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

تعتبر عناصر التحكم في محتوى النص الغني مثالية لإضافة نص منسق إلى مستنداتك. دعنا ننشئ عنصر تحكم ونحدد محتواه.

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

يمكنك تطبيق الأنماط على عناصر التحكم في المحتوى لتحسين المظهر المرئي لمستندك. دعنا نرى كيفية تعيين نمط عنصر التحكم في المحتوى.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// تطبيق نمط مخصص
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## ربط SDT ببيانات XML المخصصة

في بعض السيناريوهات، قد تحتاج إلى ربط SDT ببيانات XML مخصصة لإنشاء محتوى ديناميكي. دعنا نستكشف كيفية تحقيق ذلك.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## إنشاء جدول يحتوي على أقسام متكررة مرتبطة ببيانات XML مخصصة

يمكن أن تكون الجداول التي تحتوي على أقسام متكررة مفيدة للغاية لعرض البيانات المنظمة. دعنا ننشئ مثل هذا الجدول ونربطه ببيانات XML مخصصة.

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

يمكن أن تمتد علامات المستند المنظمة إلى أقسام متعددة في المستند. في هذا القسم، سنستكشف كيفية العمل مع علامات المستند المنظمة متعددة الأقسام.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## خاتمة

توفر علامات المستندات المنظمة في Aspose.Words for Java طريقة متعددة الاستخدامات لإدارة المحتوى وتنسيقه داخل مستنداتك. سواء كنت بحاجة إلى إنشاء قوالب أو نماذج أو مستندات ديناميكية، توفر لك علامات المستندات المنظمة المرونة والتحكم اللذين تحتاجهما. باتباع الأمثلة والإرشادات الواردة في هذه المقالة، يمكنك الاستفادة من قوة علامات المستندات المنظمة لتحسين مهام معالجة المستندات الخاصة بك.

## الأسئلة الشائعة

### ما هو الغرض من علامات المستندات المنظمة (SDTs)؟

تخدم علامات المستندات المنظمة (SDTs) غرض تنظيم وتنسيق المحتوى داخل المستندات، مما يجعل من الأسهل إنشاء القوالب والنماذج والمستندات المنظمة.

### كيف يمكنني التحقق من الحالة الحالية لـ Checkbox SDT؟

 يمكنك التحقق من الحالة الحالية لـ Checkbox SDT باستخدام`setChecked` الطريقة كما هو موضح في المقال.

### هل يمكنني تطبيق الأنماط على عناصر التحكم بالمحتوى؟

نعم، يمكنك تطبيق الأنماط على عناصر التحكم في المحتوى لتخصيص مظهرها في المستند.

### هل من الممكن ربط SDT ببيانات XML المخصصة؟

نعم، يمكنك ربط SDT ببيانات XML مخصصة، مما يسمح بإنشاء محتوى ديناميكي وتعيين البيانات.

### ما هي الأقسام المتكررة في SDTs؟

تتيح لك الأقسام المتكررة في SDTs إنشاء جداول تحتوي على بيانات ديناميكية، حيث يمكن تكرار الصفوف استنادًا إلى بيانات XML المحددة.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
