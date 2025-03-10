---
title: การโคลนและการรวมเอกสารใน Aspose.Words สำหรับ Java
linktitle: การโคลนและการรวมเอกสาร
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีโคลนและรวมเอกสารใน Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ดต้นฉบับ
weight: 27
url: /th/java/document-manipulation/cloning-and-combining-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การโคลนและการรวมเอกสารใน Aspose.Words สำหรับ Java


## บทนำเกี่ยวกับการโคลนและการรวมเอกสารใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะศึกษาวิธีการโคลนและรวมเอกสารโดยใช้ Aspose.Words สำหรับ Java เราจะครอบคลุมสถานการณ์ต่างๆ รวมถึงการโคลนเอกสาร การแทรกเอกสารที่จุดแทนที่ การคั่นหน้า และระหว่างการดำเนินการผสานจดหมาย

## ขั้นตอนที่ 1: การโคลนเอกสาร

 ในการโคลนเอกสารใน Aspose.Words สำหรับ Java คุณสามารถใช้`deepClone()` วิธีการนี้ เป็นตัวอย่างง่ายๆ ดังนี้:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

โค้ดนี้จะสร้างโคลนเชิงลึกของเอกสารต้นฉบับและบันทึกเป็นไฟล์ใหม่

## ขั้นตอนที่ 2: การแทรกเอกสารที่จุดแทนที่

คุณสามารถแทรกเอกสารที่จุดแทนที่เฉพาะในเอกสารอื่นได้ โดยทำได้ดังนี้:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

 ในตัวอย่างนี้เราใช้`FindReplaceOptions` วัตถุเพื่อระบุตัวจัดการการโทรกลับสำหรับการเปลี่ยน`InsertDocumentAtReplaceHandler` คลาสจัดการตรรกะการแทรก

## ขั้นตอนที่ 3: การแทรกเอกสารในบุ๊กมาร์ก

หากต้องการแทรกเอกสารที่บุ๊กมาร์กเฉพาะในเอกสารอื่น คุณสามารถใช้โค้ดดังต่อไปนี้:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

 ที่นี่เราจะค้นหาบุ๊กมาร์กตามชื่อและใช้`insertDocument` วิธีการแทรกเนื้อหาของ`subDoc` เอกสารในตำแหน่งบุ๊กมาร์ก

## ขั้นตอนที่ 4: การแทรกเอกสารระหว่างการผสานจดหมาย

คุณสามารถแทรกเอกสารระหว่างการดำเนินการผสานจดหมายใน Aspose.Words สำหรับ Java ได้ ดังต่อไปนี้:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

 ในตัวอย่างนี้ เราตั้งค่าคอลแบ็กการรวมฟิลด์โดยใช้`InsertDocumentAtMailMergeHandler` คลาสสำหรับจัดการการแทรกเอกสารที่ระบุโดยฟิลด์ "Document_1"

## บทสรุป

การโคลนและรวมเอกสารใน Aspose.Words สำหรับ Java สามารถทำได้โดยใช้เทคนิคต่างๆ ไม่ว่าคุณจะต้องโคลนเอกสาร แทรกเนื้อหาที่จุดแทนที่ คั่นหน้า หรือระหว่างการผสานจดหมาย Aspose.Words ก็มีฟีเจอร์อันทรงพลังเพื่อจัดการเอกสารได้อย่างราบรื่น

## คำถามที่พบบ่อย

### ฉันจะโคลนเอกสารใน Aspose.Words สำหรับ Java ได้อย่างไร

 คุณสามารถโคลนเอกสารใน Aspose.Words สำหรับ Java ได้โดยใช้`deepClone()` วิธีการ นี่คือตัวอย่าง:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### ฉันจะแทรกเอกสารไว้ในบุ๊กมาร์กได้อย่างไร?

 หากต้องการแทรกเอกสารที่บุ๊กมาร์กใน Aspose.Words สำหรับ Java คุณสามารถค้นหาบุ๊กมาร์กตามชื่อแล้วใช้`insertDocument` วิธีการแทรกเนื้อหา ดังตัวอย่างต่อไปนี้

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### ฉันจะแทรกเอกสารในระหว่างการผสานจดหมายใน Aspose.Words สำหรับ Java ได้อย่างไร

คุณสามารถแทรกเอกสารระหว่างการผสานจดหมายใน Aspose.Words สำหรับ Java ได้โดยตั้งค่าคอลแบ็กการผสานฟิลด์และระบุเอกสารที่จะแทรก ต่อไปนี้คือตัวอย่าง:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

 ในตัวอย่างนี้`InsertDocumentAtMailMergeHandler`คลาสจัดการตรรกะการแทรกสำหรับ "DocumentField" ในระหว่างการผสานจดหมาย
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
