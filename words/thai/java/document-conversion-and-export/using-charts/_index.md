---
title: การใช้แผนภูมิใน Aspose.Words สำหรับ Java
linktitle: การใช้แผนภูมิ
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีการสร้างและปรับแต่งแผนภูมิใน Aspose.Words สำหรับ Java สำรวจประเภทแผนภูมิ การจัดรูปแบบ และคุณสมบัติของแกนสำหรับการแสดงภาพข้อมูล
weight: 12
url: /th/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การใช้แผนภูมิใน Aspose.Words สำหรับ Java


## การแนะนำการใช้แผนภูมิใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะมาเรียนรู้วิธีการทำงานกับแผนภูมิโดยใช้ Aspose.Words สำหรับ Java คุณจะได้เรียนรู้วิธีการสร้างแผนภูมิประเภทต่างๆ ปรับแต่งคุณสมบัติแกน จัดรูปแบบป้ายข้อมูล และอื่นๆ อีกมากมาย มาเริ่มกันเลย!

## การสร้างแผนภูมิเส้น

ในการสร้างแผนภูมิเส้น ให้ใช้โค้ดดังต่อไปนี้:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// ลบซีรีย์ที่สร้างขึ้นตามค่าเริ่มต้น
chart.getSeries().clear();

// การเพิ่มชุดข้อมูลและป้ายข้อมูล
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// หรือเชื่อมโยงรูปแบบโค้ดไปยังเซลล์แหล่งที่มา
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## การสร้างแผนภูมิประเภทอื่น ๆ

คุณสามารถสร้างแผนภูมิประเภทต่างๆ เช่น แผนภูมิคอลัมน์ แผนภูมิพื้นที่ แผนภูมิฟอง แผนภูมิกระจาย และอื่นๆ โดยใช้เทคนิคที่คล้ายกัน ต่อไปนี้คือตัวอย่างการแทรกแผนภูมิคอลัมน์แบบง่าย:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// ลบซีรีย์ที่สร้างขึ้นตามค่าเริ่มต้น
chart.getSeries().clear();

// การสร้างหมวดหมู่และการเพิ่มข้อมูล
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## การปรับแต่งคุณสมบัติของแกน

คุณสามารถปรับแต่งคุณสมบัติของแกนได้ เช่น การเปลี่ยนประเภทแกน การตั้งเครื่องหมาย การจัดรูปแบบป้ายกำกับ และอื่นๆ ต่อไปนี้คือตัวอย่างการกำหนดคุณสมบัติของแกน XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// ล้างซีรีย์เริ่มต้นและเพิ่มข้อมูลของคุณ

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// เปลี่ยนแกน X ให้เป็นหมวดหมู่แทนวันที่
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //วัดเป็นหน่วยแสดงผลของแกน Y (ร้อย)
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

## การจัดรูปแบบฉลากข้อมูล

คุณสามารถจัดรูปแบบป้ายข้อมูลด้วยรูปแบบตัวเลขที่แตกต่างกันได้ ต่อไปนี้คือตัวอย่าง:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// ล้างซีรีย์เริ่มต้นและเพิ่มข้อมูลของคุณ

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## การปรับแต่งแผนภูมิเพิ่มเติม

คุณสามารถปรับแต่งแผนภูมิของคุณเพิ่มเติมได้โดยการปรับขอบเขต หน่วยช่วงระหว่างป้ายกำกับ ซ่อนแกนแผนภูมิ และอื่นๆ อีกมากมาย สำรวจตัวอย่างโค้ดที่ให้มาเพื่อเรียนรู้เพิ่มเติมเกี่ยวกับตัวเลือกเหล่านี้

## บทสรุป

ในบทช่วยสอนนี้ เราได้ศึกษาวิธีการทำงานกับแผนภูมิโดยใช้ Aspose.Words สำหรับ Java คุณได้เรียนรู้วิธีการสร้างแผนภูมิประเภทต่างๆ ปรับแต่งคุณสมบัติแกน จัดรูปแบบป้ายข้อมูล และอื่นๆ อีกมากมาย Aspose.Words สำหรับ Java มอบเครื่องมืออันทรงพลังสำหรับการเพิ่มการแสดงภาพข้อมูลลงในเอกสารของคุณ เพื่อปรับปรุงวิธีการนำเสนอข้อมูลของคุณ

## คำถามที่พบบ่อย

### ฉันจะเพิ่มซีรีส์หลายชุดลงในแผนภูมิได้อย่างไร

 คุณสามารถเพิ่มซีรีส์หลายชุดลงในแผนภูมิได้โดยใช้`chart.getSeries().add()` วิธีการนี้ โปรดระบุชื่อซีรีส์ หมวดหมู่ และค่าข้อมูล

### ฉันจะจัดรูปแบบป้ายข้อมูลด้วยรูปแบบตัวเลขแบบกำหนดเองได้อย่างไร

คุณสามารถจัดรูปแบบป้ายข้อมูลโดยการเข้าถึง`DataLabels` คุณสมบัติของซีรีส์และการตั้งค่ารหัสรูปแบบที่ต้องการโดยใช้`getNumberFormat().setFormatCode()`.

### ฉันจะปรับแต่งคุณสมบัติแกนในแผนภูมิได้อย่างไร

 คุณสามารถปรับแต่งคุณสมบัติของแกน เช่น ประเภท เครื่องหมายถูก ป้ายกำกับ และอื่นๆ ได้โดยการเข้าถึง`ChartAxis` คุณสมบัติเช่น`setCategoryType()`, `setCrosses()` , และ`setMajorTickMark()`.

### ฉันจะสร้างแผนภูมิประเภทอื่น เช่น แผนภูมิกระจาย หรือแผนภูมิพื้นที่ ได้อย่างไร

 คุณสามารถสร้างแผนภูมิประเภทต่างๆ ได้โดยระบุประเภทที่เหมาะสม`ChartType` เมื่อแทรกแผนภูมิโดยใช้`builder.insertChart(ChartType.TYPE, width, height)`.

### ฉันจะซ่อนแกนแผนภูมิได้อย่างไร

 คุณสามารถซ่อนแกนแผนภูมิได้โดยการตั้งค่า`setHidden(true)` คุณสมบัติของแกน
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
