---
date: '2025-11-12'
description: เรียนรู้วิธีใช้ LayoutCollector และ LayoutEnumerator ของ Aspose.Words
  for Java เพื่อวิเคราะห์การแบ่งหน้า, เดินทางผ่านการจัดวางเอกสาร, ทำงานกับ callback
  ของการจัดวาง, และรีสตาร์ทการนับหน้าในส่วนต่อเนื่อง.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: th
title: การวิเคราะห์การแบ่งหน้าใน Java ด้วยเครื่องมือ Layout ของ Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การวิเคราะห์การแบ่งหน้าใน Java ด้วยเครื่องมือ Layout ของ Aspose.Words

## Introduction  

หากคุณต้องการ **วิเคราะห์การแบ่งหน้า** หรือ **สำรวจโครงสร้างของเอกสาร** ในแอปพลิเคชัน Java, Aspose.Words for Java จะมอบ API สองตัวที่ทรงพลังให้คุณคือ **`LayoutCollector`** และ **`LayoutEnumerator`** คลาสเหล่านี้ช่วยให้คุณทราบว่าโหนดหนึ่งครอบคลุมกี่หน้า, เดินผ่านทุกเอนทิตี้ของเลเอาต์, ตอบสนองต่อเหตุการณ์ของเลเอาต์, และแม้กระทั่งรีสตาร์ทการนับหน้าในเซคชันต่อเนื่อง ในคู่มือนี้เราจะอธิบายแต่ละฟีเจอร์แบบขั้นตอน‑โดย‑ขั้นตอน, แสดงตัวอย่างโค้ดจริง, และอธิบายผลลัพธ์ที่คาดหวัง เพื่อให้คุณนำไปใช้ได้ทันที

คุณจะได้เรียนรู้วิธี:

* **ใช้ LayoutCollector** เพื่อรับหมายเลขหน้าเริ่มต้นและสิ้นสุดของโหนดใดก็ได้ (use layoutcollector page span)  
* **สำรวจโครงสร้างเอกสาร** ด้วย LayoutEnumerator (traverse document layout)  
* **ทำงานกับ callback ของเลเอาต์** เพื่อตอบสนองต่อเหตุการณ์การแบ่งหน้า (implement layout callback)  
* **รีสตาร์ทการนับหน้า** ในเซคชันต่อเนื่อง (restart page numbering sections)  

มาเริ่มกันเลย

## Prerequisites  

### Required Libraries  

| Build Tool | Dependency |
|------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Note:** หมายเลขเวอร์ชันถูกเก็บไว้เพื่อความเข้ากันได้; โค้ดทำงานกับ Aspose.Words for Java เวอร์ชันล่าสุดใดก็ได้

### Environment  

* JDK 8 หรือใหม่กว่า  
* IDE เช่น IntelliJ IDEA หรือ Eclipse  

### Knowledge  

ความรู้พื้นฐานด้าน Java และความคุ้นเคยกับ Maven/Gradle เพียงพอที่จะทำตามตัวอย่างได้

## Setting Up Aspose.Words  

ก่อนที่คุณจะเรียกใช้ API ของเลเอาต์ใด ๆ, ไลบรารีต้องได้รับการลิขสิทธิ์ (หรือใช้ในโหมดทดลอง) โค้ดตัวอย่างด้านล่างแสดงการเริ่มต้นขั้นพื้นฐานที่สุด:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*โค้ดนี้ไม่ได้แก้ไขเอกสารใด ๆ; เพียงเตรียมสภาพแวดล้อมของ Aspose*  

ตอนนี้เราพร้อมที่จะลงลึกในฟีเจอร์หลัก

## Feature 1: Using **LayoutCollector** to Analyze Pagination  

`LayoutCollector` จะแมปทุกโหนดใน `Document` ไปยังหน้าที่มันครอบคลุม นี่เป็นวิธีที่เชื่อถือได้ที่สุดในการ **use layoutcollector page span** สำหรับการวิเคราะห์การแบ่งหน้า

### Step‑by‑step implementation  

1. **สร้างเอกสารใหม่และแนบ LayoutCollector**  
2. **แทรกเนื้อหาที่บังคับให้เกิดการแบ่งหน้า** (เช่น page break, section break)  
3. **รีเฟรชเลเอาต์** ด้วย `updatePageLayout()`  
4. **สอบถาม collector** เพื่อรับหน้าเริ่มต้น, หน้าสิ้นสุด, และจำนวนหน้าที่ครอบคลุมทั้งหมด

#### 1️⃣ Initialize Document and LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Populate the Document  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Update Layout and Retrieve Metrics  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Expected output**

```
Document spans 5 pages.
```

> **Why it works:** `updatePageLayout()` ทำให้ Aspose.Words คำนวณเลเอาต์ใหม่, หลังจากนั้น `LayoutCollector` จะรายงานช่วงหน้าที่แม่นยำ

## Feature 2: Traversing Document Layout with **LayoutEnumerator**  

เมื่อคุณต้องการ **traverse document layout** (เช่น สำหรับการเรนเดอร์หรือวิเคราะห์แบบกำหนดเอง), `LayoutEnumerator` จะให้มุมมองแบบต้นไม้ของหน้า, ย่อหน้า, บรรทัด, และคำ

### Step‑by‑step implementation  

1. โหลดเอกสารที่มีเอนทิตี้ของเลเอาต์อยู่แล้ว  
2. สร้างอินสแตนซ์ของ `LayoutEnumerator`  
3. ย้ายไปยังเอนทิตี้ระดับราก `PAGE`  
4. เดินผ่านเลเอาต์ไปข้างหน้าและถอยหลังโดยใช้เมธอดช่วยเหลือแบบเรียกซ้ำ

#### 1️⃣ Load Document and Create Enumerator  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Position on the Page Level  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Forward Traversal (Depth‑First)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Backward Traversal  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Helper methods** (`traverseLayoutForward` / `traverseLayoutBackward`) ถูกเขียนแบบเรียกซ้ำเพื่อเยี่ยมชมทุกเอนทิตี้ลูกและพิมพ์ประเภทพร้อมดัชนีหน้า คุณสามารถปรับให้เก็บสถิติ, เรนเดอร์กราฟิก, หรือแก้ไขคุณสมบัติของเลเอาต์ได้ตามต้องการ

## Feature 3: Implementing **Layout Callbacks**  

บางครั้งคุณต้องการตอบสนองเมื่อ Aspose.Words เสร็จสิ้นการจัดเลเอาต์ส่วนหนึ่งของเอกสาร การทำ `IPageLayoutCallback` จะทำให้คุณ **implement layout callback** เช่น การบันทึกแต่ละหน้าเป็นรูปภาพ

### Step‑by‑step implementation  

1. กำหนดอินสแตนซ์ callback ให้กับ `LayoutOptions` ของเอกสาร  
2. ภายใน callback, จัดการเหตุการณ์ `PART_REFLOW_FINISHED` และ `CONVERSION_FINISHED`  
3. เรนเดอร์หน้าปัจจุบันเป็น PNG ด้วย `ImageSaveOptions`

#### 1️⃣ Register the Callback  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Callback Class  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**What happens:** ทุกครั้งที่ส่วนของเลเอาต์เสร็จสิ้นการ reflow, callback จะเรนเดอร์หน้านั้นเป็นไฟล์ PNG, ให้คุณเห็นกระบวนการแบ่งหน้าตามภาพ

## Feature 4: Restarting Page Numbering in **Continuous Sections**  

เมื่อเอกสารมีเซคชันต่อเนื่อง, คุณอาจต้องการให้การนับหน้าตั้งค่าใหม่เฉพาะเมื่อเริ่มหน้าใหม่ทางกายภาพ การทำเช่นนี้ทำได้ด้วยการตั้งค่า `ContinuousSectionRestart`

### Step‑by‑step implementation  

1. โหลดเอกสารเป้าหมาย  
2. เปลี่ยนตัวเลือก `ContinuousSectionPageNumberingRestart`  
3. เรียก `updatePageLayout()` อีกครั้งเพื่อให้การเปลี่ยนแปลงมีผล

#### 1️⃣ Load Document  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

#### 2️⃣ Configure Restart Behavior  

```java
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();            // Apply the new numbering rule
```

**Result:** ตอนนี้หมายเลขหน้าจะรีสตาร์ทเฉพาะเมื่อเริ่มหน้าใหม่ทางกายภาพ, ทำให้รายงานหรือหนังสือดูเป็นมืออาชีพมากขึ้น

## Practical Applications  

| Scenario | Which API Helps | Benefit |
|----------|----------------|---------|
| **Audit long contracts** | `LayoutCollector` | ค้นหาได้อย่างรวดเร็วว่าข้อความใดครอบคลุมหลายหน้า |
| **Custom PDF rendering** | `LayoutEnumerator` | เดินผ่านต้นไม้ของเลเอาต์เพื่อส่งออกแต่ละบรรทัดเป็นกราฟิกเวกเตอร์ |
| **Live document preview** | Layout callbacks | สร้างภาพหน้าตามเวลาจริงขณะผู้ใช้แก้ไขเนื้อหา |
| **Multi‑section reports** | Continuous section restart | รักษาการนับหน้าให้เป็นตรรกะโดยไม่ต้องปรับด้วยตนเอง |

## Performance Tips  

* **Trim unused nodes** ก่อนเรียก `updatePageLayout()` – จำนวนองค์ประกอบที่น้อยลงทำให้การแบ่งหน้าเร็วขึ้น  
* **Reuse a single LayoutCollector** สำหรับหลายการสอบถามแทนการสร้างใหม่ทุกครั้ง  
* **Limit traversal depth** เมื่อใช้ LayoutEnumerator หากคุณต้องการข้อมูลระดับหน้าเท่านั้น  
* **Dispose of streams** (ตามตัวอย่างใน callback) เพื่อป้องกันการรั่วของหน่วยความจำกับเอกสารขนาดใหญ่

## Conclusion  

ด้วยการเชี่ยวชาญ `LayoutCollector`, `LayoutEnumerator`, layout callbacks, และการรีสตาร์ทการนับหน้าในเซคชันต่อเนื่อง, คุณจะมีเครื่องมือครบวงจรสำหรับ **analyze pagination java**, **traverse document layout**, และ **restart page numbering sections** API เหล่านี้ช่วยให้คุณสร้าง pipeline การประมวลผลข้อความที่มีประสิทธิภาพสูงและให้ผลลัพธ์ระดับมืออาชีพทุกครั้ง

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}