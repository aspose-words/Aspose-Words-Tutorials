---
date: 2026-02-16
description: เรียนรู้วิธีเพิ่มหลายชุดข้อมูลลงในแผนภูมิใน Aspose.Words for Java, เปลี่ยนเครื่องหมายติ๊กบนแกน,
  ใช้รูปแบบตัวเลขที่กำหนดเอง, และสร้างเอกสาร Word ที่มีแผนภูมิเส้นและแผนภูมิคอลัมน์.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: เพิ่มหลายชุดข้อมูลในแผนภูมิใน Aspose.Words สำหรับ Java
url: /th/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มหลายซีรีส์ลงในแผนภูมิใน Aspose.Words for Java

## บทนำการใช้แผนภูมิใน Aspose.Words for Java

ในบทเรียนนี้คุณจะได้เรียนรู้ **วิธีการเพิ่มหลายซีรีส์** ลงในแผนภูมิด้วย Aspose.Words for Java ทำไมการปรับแต่งเครื่องหมายติ๊กบนแกนและการใช้รูปแบบตัวเลขที่กำหนดเองจึงสำคัญ และวิธีการสร้างเอกสาร Word ที่เต็มไปด้วยแผนภูมิ ไม่ว่าคุณจะต้องการแผนภูมิเส้นสำหรับข้อมูลการเงินหรือแผนภูมิคอลัมน์สำหรับตัวเลขการขาย ขั้นตอนต่อไปนี้จะช่วยคุณสร้าง สไตล์ และปรับแต่งแผนภูมิอย่างเป็นโปรแกรม

## คำตอบสั้น ๆ
- **ฉันจะเพิ่มหลายซีรีส์ได้อย่างไร?** ใช้ `chart.getSeries().add(...)` สำหรับแต่ละซีรีส์ที่คุณต้องการแสดง.  
- **ฉันสามารถเปลี่ยนเครื่องหมายติ๊กบนแกนได้หรือไม่?** ได้ – ใช้ `setMajorTickMark()` และ `setMinorTickMark()` บนวัตถุแกน.  
- **ฉันสามารถใช้รูปแบบใดกับป้ายข้อมูลได้?** รูปแบบตัวเลขที่เข้ากันได้กับ Excel ใดก็ได้ เช่น `"$"#,##0.00` หรือ `0.00%`.  
- **ประเภทแผนภูมิใดที่รองรับ?** Line, column, area, bubble, scatter และอื่น ๆ อีกมากผ่าน `ChartType`.  
- **ต้องใช้ใบอนุญาตสำหรับการผลิตหรือไม่?** จำเป็นต้องมีใบอนุญาต Aspose.Words for Java ที่ถูกต้องสำหรับการทำงานเต็มรูปแบบ.

## “เพิ่มหลายซีรีส์” ในแผนภูมิหมายถึงอะไร?
การเพิ่มหลายซีรีส์หมายถึงการใส่ชุดข้อมูลมากกว่าหนึ่งชุดลงในพื้นที่แผนภูมิเดียวกัน ทำให้คุณสามารถเปรียบเทียบหมวดหมู่หรือช่วงเวลาต่าง ๆ ข้างเคียงกันได้ แต่ละซีรีส์จะแสดงเป็นเส้น, คอลัมน์ หรือชุดเครื่องหมายของตนเอง ให้ผู้อ่านได้รับเรื่องราวภาพที่สมบูรณ์ยิ่งขึ้น

## ทำไมต้องใช้ Aspose.Words for Java เพื่อสร้างเอกสาร Word ที่มีแผนภูมิ?
- **การควบคุมเต็มรูปแบบ** บนประเภทแผนภูมิ, การจัดวาง, และสไตล์โดยไม่ต้องเปิด Word ด้วยตนเอง.  
- **การสร้างแบบโปรแกรม** เหมาะกับการทำงานอัตโนมัติในสายงานรายงาน.  
- **ข้ามแพลตฟอร์ม** – ทำงานได้บนสภาพแวดล้อมที่รองรับ Java ทุกประเภท.  
- **API ครบถ้วน** สำหรับการปรับแต่งแกน, ป้ายข้อมูล, และรูปแบบตัวเลข.

## ข้อกำหนดเบื้องต้น
- Java Development Kit (JDK) 8 หรือสูงกว่า.  
- ไลบรารี Aspose.Words for Java ที่เพิ่มเข้าในโครงการของคุณ (Maven/Gradle หรือ JAR).  
- ใบอนุญาต Aspose ที่ถูกต้องสำหรับการผลิต (ไม่บังคับสำหรับการทดลอง).

## คู่มือแบบขั้นตอน

### ขั้นตอนที่ 1: สร้างแผนภูมิเส้นและ **เพิ่มหลายซีรีส์**
โค้ดหลักด้านล่างนี้สร้างแผนภูมิเส้น, ลบซีรีส์เริ่มต้น, แล้วเพิ่มสามซีรีส์ที่มีป้ายข้อมูลกำหนดเอง

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

> **เคล็ดลับ:** เรียก `chart.getSeries().add(...)` จำนวนครั้งที่ต้องการเพื่อ **เพิ่มหลายซีรีส์** – ทุกครั้งที่เรียกจะสร้างเส้น (หรือคอลัมน์ ฯลฯ) ใหม่บนแผนภูมิเดียวกัน.

### ขั้นตอนที่ 2: **สร้างแผนภูมิคอลัมน์** (create column chart java)
ส่วนต่อไปนี้แสดงวิธีแทรกแผนภูมิคอลัมน์ง่าย ๆ ซึ่งเหมาะสำหรับการเปรียบเทียบหมวดหมู่ข้างเคียงกัน

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### ขั้นตอนที่ 3: **เปลี่ยนเครื่องหมายติ๊กบนแกน** (change axis tick marks)
การปรับแต่งแกน X และ Y ช่วยให้อ่านง่ายขึ้น โค้ดต่อไปนี้สาธิตวิธีเปลี่ยนเครื่องหมายติ๊ก, กลับลำดับ, และกำหนดจุดตัดที่กำหนดเอง

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### ขั้นตอนที่ 4: **ใช้รูปแบบตัวเลขที่กำหนดเอง** (apply custom number format)
คุณสามารถจัดรูปแบบตัวเลขบนแกนหรือป้ายข้อมูลด้วยรูปแบบใดก็ได้ที่ Excel รองรับ ตัวอย่างสั้น ๆ ด้านล่างนี้จัดรูปแบบแกน Y ด้วยรูปแบบคั่นหลักพัน

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### ขั้นตอนที่ 5: สร้างเอกสาร Word สุดท้าย (generate chart word document)
หลังจากตั้งค่าซีรีส์, แกน, และป้ายข้อมูลแล้ว เพียงเรียก `doc.save(...)` ตามที่แสดงในโค้ดข้างต้น ไฟล์ `.docx` ที่ได้จะมีแผนภูมิทำงานเต็มรูปแบบที่สามารถเปิดและแก้ไขใน Microsoft Word

## กรณีการใช้งานทั่วไป
- **แดชบอร์ดการเงิน** – แผนภูมิเส้นหลายซีรีส์สำหรับรายได้, ค่าใช้จ่าย, และกำไร.  
- **รายงานการขาย** – แผนภูมิคอลัมน์เปรียบเทียบยอดขายไตรมาสตามภูมิภาค.  
- **การติดตามโครงการ** – แผนภูมิพื้นที่หรือกระจายแสดงความคืบหน้าตามเวลา.  

## การปรับแต่งแผนภูมิเพิ่มเติม
นอกเหนือจากพื้นฐาน คุณสามารถปรับขอบเขต, ซ่อนแกน (`axis.setHidden(true)`), เปลี่ยนสี, เพิ่มคำอธิบาย, และอื่น ๆ อีกมาก ดูเอกสารอ้างอิง API ของ Aspose.Words for Java เพื่อรับรายการตัวเลือกทั้งหมด

## สรุป
ในคู่มือนี้เราได้อธิบายวิธี **เพิ่มหลายซีรีส์** ลงในแผนภูมิ, สร้างแผนภูมิเส้นและคอลัมน์, **เปลี่ยนเครื่องหมายติ๊กบนแกน**, **ใช้รูปแบบตัวเลขที่กำหนดเอง**, และสุดท้าย **สร้างเอกสาร Word ที่เต็มไปด้วยแผนภูมิ** ด้วย Aspose.Words for Java คุณจะได้วิธีการโค้ด‑ฟอร์สต์ที่ทรงพลังเพื่อฝังการแสดงผลข้อมูลระดับมืออาชีพโดยตรงในเอกสารของคุณ

## คำถามที่พบบ่อย

**ถาม: ฉันจะเพิ่มหลายซีรีส์ลงในแผนภูมิได้อย่างไร?**  
ตอบ: เรียก `chart.getSeries().add()` สำหรับแต่ละซีรีส์ที่คุณต้องการแสดง ทุกการเรียกจะสร้างชุดข้อมูลใหม่ที่ปรากฏเป็นเส้น, คอลัมน์, หรือกลุ่มเครื่องหมายของตนเอง

**ถาม: ฉันจะจัดรูปแบบป้ายข้อมูลด้วยรูปแบบตัวเลขที่กำหนดเองได้อย่างไร?**  
ตอบ: เข้าถึงอ็อบเจ็กต์ `DataLabels` ของซีรีส์และใช้ `getNumberFormat().setFormatCode("รูปแบบของคุณ")` คุณยังสามารถเชื่อมโยงรูปแบบกับเซลล์ต้นทางด้วย `isLinkedToSource(true)`

**ถาม: ฉันจะเปลี่ยนเครื่องหมายติ๊กบนแกนได้อย่างไร?**  
ตอบ: ใช้ `setMajorTickMark()` และ `setMinorTickMark()` บน `ChartAxis` ตัวเลือกรวมถึง `CROSS`, `INSIDE`, `OUTSIDE`, และ `NONE`

**ถาม: ฉันสามารถสร้างประเภทแผนภูมิอื่น ๆ เช่น แผนภูมิกระจายหรือแผนภูมิพื้นที่ได้หรือไม่?**  
ตอบ: ได้ – ระบุ `ChartType` ที่ต้องการ (เช่น `ChartType.SCATTER`, `ChartType.AREA`) เมื่อเรียก `builder.insertChart(...)`

**ถาม: ฉันจะซ่อนแกนที่ไม่ต้องการได้อย่างไร?**  
ตอบ: เรียก `axis.setHidden(true)` บน `ChartAxis` ที่ต้องการซ่อน

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}