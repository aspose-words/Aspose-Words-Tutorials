---
"description": "เรียนรู้วิธีการปรับปรุงการจัดรูปแบบเอกสารด้วย Aspose.Words สำหรับ Java สำรวจรูปแบบ ธีม และอื่นๆ ในคู่มือที่ครอบคลุมนี้พร้อมตัวอย่างโค้ดต้นฉบับ"
"linktitle": "การใช้รูปแบบและธีม"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้สไตล์และธีมใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-manipulation/using-styles-and-themes/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้สไตล์และธีมใน Aspose.Words สำหรับ Java


## การแนะนำการใช้สไตล์และธีมใน Aspose.Words สำหรับ Java

ในคู่มือนี้ เราจะมาสำรวจวิธีการทำงานกับสไตล์และธีมใน Aspose.Words สำหรับ Java เพื่อปรับปรุงการจัดรูปแบบและรูปลักษณ์ของเอกสารของคุณ เราจะครอบคลุมหัวข้อต่างๆ เช่น การดึงสไตล์ การคัดลอกสไตล์ การจัดการธีม และการแทรกตัวคั่นสไตล์ มาเริ่มกันเลย!

## การดึงข้อมูลสไตล์

ในการดึงสไตล์จากเอกสาร คุณสามารถใช้โค้ด Java ต่อไปนี้:

```java
Document doc = new Document();
String styleName = "";
// รับคอลเลกชันสไตล์จากเอกสาร
StyleCollection styles = doc.getStyles();
for (Style style : styles)
{
    if ("".equals(styleName))
    {
        styleName = style.getName();
        System.out.println(styleName);
    }
    else
    {
        styleName = styleName + ", " + style.getName();
        System.out.println(styleName);
    }
}
```

โค้ดนี้จะดึงสไตล์ที่กำหนดไว้ในเอกสารและพิมพ์ชื่อของสไตล์เหล่านั้น

## การคัดลอกสไตล์

หากต้องการคัดลอกรูปแบบจากเอกสารหนึ่งไปยังอีกเอกสารหนึ่ง คุณสามารถใช้ `copyStylesFromTemplate` วิธีการดังแสดงด้านล่างนี้:

```java
@Test
public void copyStyles() throws Exception
{
    Document doc = new Document();
    Document target = new Document("Your Directory Path" + "Rendering.docx");
    target.copyStylesFromTemplate(doc);
    doc.save("Your Directory Path" + "WorkingWithStylesAndThemes.CopyStyles.docx");
}
```

โค้ดนี้จะคัดลอกสไตล์จากเอกสารเทมเพลตไปยังเอกสารปัจจุบัน

## การจัดการธีม

ธีมเป็นสิ่งสำคัญในการกำหนดรูปลักษณ์โดยรวมของเอกสารของคุณ คุณสามารถเรียกค้นและตั้งค่าคุณสมบัติของธีมได้ตามที่แสดงในโค้ดต่อไปนี้:

```java
@Test
public void getThemeProperties() throws Exception
{
    Document doc = new Document();
    Theme theme = doc.getTheme();
    System.out.println(theme.getMajorFonts().getLatin());
    System.out.println(theme.getMinorFonts().getEastAsian());
    System.out.println(theme.getColors().getAccent1());
}

@Test
public void setThemeProperties() throws Exception
{
    Document doc = new Document();
    Theme theme = doc.getTheme();
    theme.getMinorFonts().setLatin("Times New Roman");
    theme.getColors().setHyperlink(Color.ORANGE);
}
```

สไนปเป็ตเหล่านี้สาธิตวิธีการดึงและปรับเปลี่ยนคุณสมบัติของธีม เช่น แบบอักษรและสี

## การแทรกตัวคั่นสไตล์

ตัวคั่นรูปแบบมีประโยชน์ในการใช้รูปแบบต่างๆ ในย่อหน้าเดียว ต่อไปนี้คือตัวอย่างวิธีการแทรกตัวคั่นรูปแบบ:

```java
@Test
public void insertStyleSeparator() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    Style paraStyle = builder.getDocument().getStyles().add(StyleType.PARAGRAPH, "MyParaStyle");
    paraStyle.getFont().setBold(false);
    paraStyle.getFont().setSize(8.0);
    paraStyle.getFont().setName("Arial");
    // ผนวกข้อความด้วยรูปแบบ "หัวเรื่อง 1"
    builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
    builder.write("Heading 1");
    builder.insertStyleSeparator();
    // ผนวกข้อความด้วยรูปแบบอื่น
    builder.getParagraphFormat().setStyleName(paraStyle.getName());
    builder.write("This is text with some other formatting ");
    doc.save("Your Directory Path" + "WorkingWithStylesAndThemes.InsertStyleSeparator.docx");
}
```

ในโค้ดนี้ เราจะสร้างรูปแบบย่อหน้าแบบกำหนดเองและแทรกตัวคั่นรูปแบบเพื่อสลับรูปแบบภายในย่อหน้าเดียวกัน

## บทสรุป

คู่มือนี้ครอบคลุมพื้นฐานการใช้งานสไตล์และธีมใน Aspose.Words สำหรับ Java คุณได้เรียนรู้วิธีการดึงและคัดลอกสไตล์ จัดการธีม และแทรกตัวคั่นสไตล์เพื่อสร้างเอกสารที่ดึงดูดสายตาและมีการจัดรูปแบบที่ดี ทดลองใช้เทคนิคเหล่านี้เพื่อปรับแต่งเอกสารของคุณตามความต้องการของคุณ


## คำถามที่พบบ่อย

### ฉันจะดึงคุณสมบัติธีมใน Aspose.Words สำหรับ Java ได้อย่างไร

คุณสามารถดึงคุณสมบัติธีมได้โดยการเข้าถึงวัตถุธีมและคุณสมบัติของมัน

### ฉันจะตั้งค่าคุณสมบัติของธีม เช่น แบบอักษรและสี ได้อย่างไร

คุณสามารถตั้งค่าคุณสมบัติของธีมได้โดยการแก้ไขคุณสมบัติของวัตถุธีม

### ฉันจะใช้ตัวคั่นสไตล์เพื่อสลับสไตล์ภายในย่อหน้าเดียวกันได้อย่างไร

คุณสามารถแทรกตัวคั่นรูปแบบได้โดยใช้ `insertStyleSeparator` วิธีการของ `DocumentBuilder` ระดับ.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}