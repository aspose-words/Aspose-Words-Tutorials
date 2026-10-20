---
date: 2025-12-13
description: เรียนรู้วิธีสร้างแผนภูมิคอลัมน์และจัดรูปแบบป้ายข้อมูลของแผนภูมิด้วย Aspose.Words
  for Java. สำรวจการเพิ่มหลายชุดข้อมูล, การเปลี่ยนประเภทแกน, และการซ่อนแกนของแผนภูมิ.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words สำหรับ Java
url: /th/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words สำหรับ Java

ในบทเรียนนี้คุณจะ **สร้างแผนภูมิคอลัมน์** ภายในเอกสาร Word โดยตรงด้วย Aspose.Words สำหรับ Java เราจะอธิบายการสร้างประเภทแผนภูมิต่าง ๆ การเพิ่มหลายซีรีส์ การจัดรูปแบบป้ายข้อมูลของแผนภูมิ การเปลี่ยนประเภทแกน และแม้กระทั่งการซ่อนแกนของแผนภูมิเมื่อคุณต้องการรูปลักษณ์ที่เรียบง่าย สุดท้ายคุณจะได้วิธีการที่พร้อมใช้งานในระดับผลิตภัณฑ์สำหรับฝังแผนภูมิที่มีความสมบูรณ์ในเอกสารของคุณ

## คำตอบสั้น
- **คลาสหลักที่ใช้สร้างแผนภูมิคืออะไร?** `DocumentBuilder` พร้อมเมธอด `insertChart`
- **เมธอดใดที่ใช้เพิ่มซีรีส์ใหม่?** `chart.getSeries().add(...)`
- **ฉันจะจัดรูปแบบป้ายข้อมูลของแผนภูมิได้อย่างไร?** ใช้ `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`
- **ฉันสามารถซ่อนแกนได้หรือไม่?** ได้, เรียก `setHidden(true)` บนวัตถุแกน
- **ต้องมีลิขสิทธิ์สำหรับ Aspose.Words หรือไม่?** จำเป็นต้องมีลิขสิทธิ์สำหรับการใช้งานในระดับผลิตภัณฑ์; มีรุ่นทดลองฟรีให้ใช้

## แผนภูมิคอลัมน์คืออะไรและทำไมต้องใช้?

แผนภูมิคอลัมน์แสดงข้อมูลเชิงหมวดหมู่เป็นแท่งแนวตั้ง ทำให้เหมาะสำหรับการเปรียบเทียบค่าระหว่างกลุ่ม (ยอดขายต่อภูมิภาค, ค่าใช้จ่ายรายเดือน ฯลฯ) ในแอปพลิเคชัน Java การสร้างแผนภูมิคอลัมน์ด้วย Aspose.Words ช่วยให้คุณฝังภาพเหล่านี้โดยตรงลงในไฟล์ Word / DOCX โดยไม่ต้องพึ่งพา Excel หรือเครื่องมือภายนอก

## วิธีสร้างแผนภูมิคอลัมน์

ด้านล่างเป็นตัวอย่างที่เรียบง่ายซึ่งสร้างแผนภูมิคอลัมน์พื้นฐาน โค้ดตรงกับส่วนที่ให้มาเดิม – เราเพียงเพิ่มคอมเมนต์อธิบายเพื่อให้ง่ายต่อการทำตาม

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

### เพิ่มหลายซีรีส์

คุณสามารถ **เพิ่มหลายซีรีส์** ลงในแผนภูมิคอลัมน์ได้โดยเรียก `chart.getSeries().add(...)` ซ้ำ ๆ ตามที่แสดงด้านบน แต่ละซีรีส์สามารถมีชุดหมวดหมู่และค่าของตนเอง ทำให้คุณเปรียบเทียบหลายชุดข้อมูลได้พร้อมกัน

## วิธีสร้างแผนภูมิเส้นพร้อมป้ายข้อมูลแบบกำหนดเอง

หากคุณต้องการแผนภูมิเส้นแทนแผนภูมิคอลัมน์ รูปแบบเดียวกันก็ใช้ได้ ตัวอย่างนี้ยังแสดง **การจัดรูปแบบป้ายข้อมูลของแผนภูมิ** ด้วยรูปแบบตัวเลขที่ต่างกัน

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

### เพิ่มป้ายข้อมูล

การเรียก `series1.hasDataLabels(true)` **เพิ่มป้ายข้อมูล** ให้กับซีรีส์ ส่วน `setShowValue(true)` ทำให้ค่าจริงแสดงบนแผนภูมิ

## วิธีเปลี่ยนประเภทแกนและปรับแต่งคุณสมบัติของแกน

การเปลี่ยนประเภทแกน (เช่น จากวันที่เป็นหมวดหมู่) ช่วยให้คุณควบคุมวิธีการวางจุดข้อมูล ตัวอย่างนี้ยังแสดงวิธี **ซ่อนแกนของแผนภูมิ** หากคุณต้องการการออกแบบที่มินิมัล

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

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### เปลี่ยนประเภทแกน

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **เปลี่ยนประเภทแกน** จากแกนที่อิงวันที่เป็นแกนประเภทหมวดหมู่ ให้คุณควบคุมตำแหน่งป้ายได้เต็มที่

## วิธีจัดรูปแบบป้ายข้อมูลของแผนภูมิ (รูปแบบตัวเลข)

คุณสามารถกำหนดรูปแบบตัวเลขให้กับแกนหรือป้ายข้อมูลโดยตรง ตัวอย่างนี้จัดรูปแบบตัวเลขของแกน Y ให้มีคั่นหลักพัน

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## การปรับแต่งแผนภูมิเพิ่มเติม

นอกเหนือจากพื้นฐานแล้ว คุณสามารถปรับขอบเขต, ตั้งค่าหน่วยระยะห่างระหว่างป้าย, ซ่อนแกนเฉพาะส่วน, และอื่น ๆ อีกมากมาย ดูเอกสาร API ของ Aspose.Words สำหรับ Java เพื่อรับรายการคุณสมบัติทั้งหมด

## คำถามที่พบบ่อย

**ถาม: ฉันจะเพิ่มหลายซีรีส์ลงในแผนภูมิได้อย่างไร?**  
ตอบ: ใช้ `chart.getSeries().add()` สำหรับแต่ละซีรีส์ที่ต้องการแสดง แต่ละการเรียกสามารถระบุชื่อ, อาเรย์หมวดหมู่, และอาเรย์ค่าได้เป็นเอกลักษณ์

**ถาม: ฉันจะจัดรูปแบบป้ายข้อมูลของแผนภูมิด้วยรูปแบบตัวเลขที่กำหนดเองได้อย่างไร?**  
ตอบ: เข้าถึงอ็อบเจกต์ `DataLabels` ของซีรีส์และเรียก `getNumberFormat().setFormatCode("รูปแบบของคุณ")` คุณยังสามารถเชื่อมโยงรูปแบบกับเซลล์ต้นทางโดยใช้ `isLinkedToSource(true)`

**ถาม: ฉันจะซ่อนแกนของแผนภูมิได้หรือไม่?**  
ตอบ: เรียก `setHidden(true)` บน `ChartAxis` ที่ต้องการซ่อน (เช่น `chart.getAxisY().setHidden(true)`)

**ถาม: วิธีที่ดีที่สุดในการเปลี่ยนประเภทแกนคืออะไร?**  
ตอบ: ใช้ `setCategoryType(AxisCategoryType.CATEGORY)` สำหรับแกนประเภทหมวดหมู่ หรือ `AxisCategoryType.DATE` สำหรับแกนประเภทวันที่

**ถาม: ฉันจะเพิ่มป้ายข้อมูลให้กับซีรีส์ได้อย่างไร?**  
ตอบ: เปิดใช้งานด้วย `series.hasDataLabels(true)` แล้วกำหนดการแสดงผลด้วย `series.getDataLabels().setShowValue(true)`

## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการเพื่อ **สร้างแผนภูมิคอลัมน์** ด้วย Aspose.Words สำหรับ Java – ตั้งแต่การแทรกแผนภูมิพื้นฐานและการเพิ่มหลายซีรีส์, การจัดรูปแบบป้ายข้อมูล, การเปลี่ยนประเภทแกน, จนถึงการซ่อนแกนเพื่อให้ได้ลุคที่สะอาดตา นำเทคนิคเหล่านี้ไปใช้ในกระบวนการสร้างรายงานหรือเอกสารอัตโนมัติของคุณ เพื่อมอบเอกสาร Word ที่เป็นมืออาชีพและขับเคลื่อนด้วยข้อมูล

---

**อัปเดตล่าสุด:** 2025-12-13  
**ทดสอบกับ:** Aspose.Words สำหรับ Java 24.12 (ล่าสุด)  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}