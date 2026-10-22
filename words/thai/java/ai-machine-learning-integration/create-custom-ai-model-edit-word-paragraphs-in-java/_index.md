---
category: general
date: 2026-03-25
description: สร้างโมเดล AI แบบกำหนดเองเพื่อแก้ไขเอกสาร Word – เรียนรู้วิธีทำให้ข้อความเป็นทางการมากขึ้น,
  แทนที่ข้อความในย่อหน้า, และเขียนย่อหน้า Word ใหม่โดยใช้ Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: th
og_description: สร้างโมเดล AI แบบกำหนดเองเพื่อแก้ไขเอกสาร Word. เรียนรู้วิธีทำให้ข้อความเป็นทางการมากขึ้น,
  แทนที่ข้อความในย่อหน้า, และเขียนย่อหน้า Word ใหม่โดยใช้ Aspose.Words AI.
og_title: สร้างโมเดล AI แบบกำหนดเอง – แก้ไขย่อหน้าของ Word ใน Java
tags:
- Aspose.Words
- Java
- AI integration
title: สร้างโมเดล AI แบบกำหนดเอง – แก้ไขย่อหน้า Word ด้วย Java
url: /th/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างโมเดล AI แบบกำหนดเอง – แก้ไขย่อหน้าของ Word ใน Java

เคยต้องการ **create custom AI model** ที่สามารถปรับแต่งย่อหน้าในไฟล์ Word หรือไม่? บางทีคุณอาจมีชุดสัญญาที่ฟังดูเป็นกันเองเกินไปและต้องการทำให้ข้อความเป็นทางการมากขึ้นด้วยบรรทัดโค้ดเดียว ข่าวดีคือคุณทำได้เช่นนั้น—ไม่ต้องใช้บริการภายนอก ไม่ต้องใช้ SDK ที่หนักหน่วง เพียง Aspose.Words for Java และ OpenAI‑compatible endpoint

ในบทแนะนำนี้เราจะพาคุณผ่านทุกขั้นตอนที่จำเป็นเพื่อ **create custom AI model**, เชื่อมต่อกับเซิร์ฟเวอร์ LLM ภายในเครื่อง, แล้วใช้มันเพื่อ *replace paragraph text* ด้วยเวอร์ชันที่เป็นทางการมากขึ้น เมื่อเสร็จสิ้นคุณจะมีโปรแกรม Java ที่สามารถรันได้ซึ่ง **edit paragraph with AI**, เขียนทับย่อหน้าใน Word และบันทึกผลลัพธ์กลับไปยังดิสก์ ไม่ได้มีเนื้อหาเกินความจำเป็น เพียงโซลูชันที่ใช้งานได้จริงที่คุณสามารถคัดลอก‑วางไปใช้ในโปรเจกต์ของคุณ

> **สิ่งที่คุณต้องการ**  
> • Java 17 หรือใหม่กว่า (โค้ดสามารถคอมไพล์กับเวอร์ชันก่อนหน้าได้ แต่ 17 เป็นจุดที่เหมาะที่สุด)  
> • Aspose.Words for Java 23.9 (หรือเวอร์ชันล่าสุด)  
> • เซิร์ฟเวอร์ LLM ที่เข้ากันได้กับ OpenAI‑compatible (เช่น Ollama, LocalAI) ที่กำลังทำงานและรับฟังที่ `http://localhost:8000/v1`  
> • เอกสาร Word อินพุต (`input.docx`) ที่วางไว้ในโฟลเดอร์ที่คุณควบคุม  

หากคุณสงสัย *why bother building a custom model* แทนการเรียก OpenAI โดยตรง คำตอบคือความยืดหยุ่น: คุณควบคุม endpoint, สามารถสลับโมเดลโดยไม่ต้องเปลี่ยนโค้ด, และเก็บ API keys ไว้ไกลจากที่เก็บรหัสต้นฉบับของคุณ มาเริ่มกันเลย

---

## สร้างโมเดล AI แบบกำหนดเอง – การตั้งค่าและกำหนดค่า

ก่อนอื่นเราต้องบอก Aspose.Words ว่า LLM ของเราตั้งอยู่ที่ไหน คลาส `AiModelEndpoint` จะเก็บ URL และคีย์ API แบบเลือกได้ เนื่องจากเราใช้เซิร์ฟเวอร์ภายในเครื่อง คีย์สามารถเป็นสตริงว่างได้ แต่พารามิเตอร์นี้จำเป็นต้องระบุ

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **เคล็ดลับ:** หากคุณเปลี่ยนไปใช้โมเดลที่โฮสต์ไว้ (เช่น Azure OpenAI) เพียงเปลี่ยน URL และคีย์—ไม่ต้องแก้ไขโค้ดส่วนอื่นใด

---

## โหลดเอกสาร Word

ตอนนี้เรานำไฟล์ต้นฉบับเข้าสู่หน่วยความจำ `Document` สามารถอ่านไฟล์ `.docx`, `.doc`, `.rtf` และรูปแบบอื่น ๆ มากมาย แต่ในตัวอย่างนี้เราจะใช้เฉพาะ `.docx`

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

ตรวจสอบให้แน่ใจว่า `YOUR_DIRECTORY` ชี้ไปยังโฟลเดอร์ที่มีอยู่จริง; หากไม่เช่นนั้นคุณจะเจอ `FileNotFoundException`. ในแอปพลิเคชันจริงคุณอาจส่งพาธเป็นอาร์กิวเมนต์ของบรรทัดคำสั่งหรืออ่านจากไฟล์คอนฟิก

---

## เริ่มต้นโมเดล AI แบบกำหนดเอง

เราสร้าง `AiModel` ประเภท `CUSTOM` และกำหนด endpoint ที่เรากำหนดไว้ก่อนหน้านี้ให้กับมัน ซึ่งบอก Aspose.Words ให้ส่งคำเรียก AI ทั้งหมดผ่านเซิร์ฟเวอร์ของเรา

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

เบื้องหลัง Aspose.Words สร้าง HTTP client ขนาดเล็กที่สื่อสารกับ LLM โดยใช้สคีมมาตรฐานของ OpenAI chat/completion นั่นคือเหตุผลที่ endpoint ต้องเป็น *OpenAI‑compatible*

---

## ดึงและเขียนทับย่อหน้าแรก

นี่คือจุดที่เราจริง ๆ **make text more formal** เราดึงย่อหน้าแรก ส่งข้อความดิบของมันไปยังโมเดลพร้อมพรอมต์ และรับเวอร์ชันที่แก้ไขแล้ว

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

อาร์กิวเมนต์ที่สอง (`"Make it more formal"`) คือคำสั่งที่เรามอบให้โมเดล คุณสามารถเปลี่ยนเป็นคำสั่งใดก็ได้—**replace paragraph text**, **summarize**, **translate**, เป็นต้น เมธอดจะคืนค่าเป็นสตริงธรรมดาซึ่งเราจะนำกลับไปแทรกในเอกสารต่อไป

> **ทำไมวิธีนี้ถึงได้ผล:** `editText` ส่ง JSON payload เช่น `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. LLM จะเห็นย่อหน้าเดิมและคำสั่ง จากนั้นตอบกลับด้วยข้อความที่แก้ไขแล้ว

---

## แทนที่เนื้อหาย่อหน้าต้นฉบับ

ตอนนี้เราจะ **replace paragraph text** ภายในโมเดลอ็อบเจกต์ของ Word เราจะล้าง `run` ที่มีอยู่ทั้งหมด (ส่วนย่อยของข้อความ) แล้วแทรก `Run` ใหม่ที่มีสตริงที่สร้างโดย AI

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

ระวังอย่าเรียก `firstParagraph.setText()`—เมธอดนี้จะลบการจัดรูปแบบทั้งหมด การใช้ `Run` จะรักษาสไตล์ของย่อหน้า (หัวข้อ, รายการหัวข้อย่อย, ฯลฯ) ขณะเปลี่ยนตัวอักษรจริง

---

## บันทึกเอกสารที่แก้ไขแล้ว

สุดท้าย เราจะเขียนเอกสารที่แก้ไขแล้วกลับไปยังดิสก์ คุณสามารถเขียนทับไฟล์ต้นฉบับหรือเช่นที่ทำในที่นี้ สร้างสำเนาใหม่

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

เมื่อคุณเปิด `output.docx` คุณควรเห็นย่อหน้าแรกมีความเป็นทางการมากขึ้นอย่างชัดเจน หาก LLM ไม่ปฏิบัติตามคำสั่งอย่างสมบูรณ์ คุณสามารถปรับพรอมต์หรือลองใช้เวอร์ชันโมเดลอื่น

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มรูปแบบ—คัดลอกไปยังไฟล์ `LlmDemo.java`, ปรับพาธให้ตรง, แล้วรันด้วย `javac` + `java`

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด `output.docx` แล้วคุณจะเห็นย่อหน้าเดิมถูกแปลง ตัวอย่างเช่น ประโยคไม่เป็นทางการอย่าง “We’ll get the thing done soon.” อาจกลายเป็น “We shall complete the task promptly.” คำที่ได้ขึ้นอยู่กับโมเดลที่คุณใช้

---

## คำถามทั่วไป & กรณีขอบ

### ถ้าเอกสารของฉันมีหลายส่วน?

โค้ดด้านบนจะทำงานกับ *first* paragraph ของ *first* section เท่านั้น เพื่อ **edit paragraph with AI** ทั่วทั้งไฟล์ ให้วนลูปผ่าน `document.getSections()` แล้วต่อด้วย `section.getBody().getParagraphs()` จำไว้ว่าต้องข้ามย่อหน้าว่าง มิฉะนั้น LLM จะได้รับสตริงว่างและไม่ตอบอะไร

### จะจัดการกับย่อหน้าขนาดใหญ่ที่เกินขีดจำกัดโทเคนอย่างไร?

ส่วนใหญ่ LLM จะจำกัดอินพุตที่ประมาณ 4 000 โทเคน หากย่อหน้าใหญ่มากเกินไป ให้แบ่งเป็นชิ้นย่อยก่อนเรียก `editText`. คุณสามารถใช้ `AiModel` ตัวเดียวกันได้; เพียงแค่ระวังขีดจำกัดอัตราการเรียกบนเซิร์ฟเวอร์ภายในของคุณ

### ฉันสามารถใช้คำสั่งอื่น เช่น “summarize” หรือ “translate to French” ได้หรือไม่?

แน่นอน. อาร์กิวเมนต์ที่สองของ `editText` เป็นข้อความอิสระ สำหรับสรุปคุณอาจส่ง `"Summarize in one sentence"` สำหรับการแปล `"Translate to French, keep the tone formal"` ก็ทำงานได้เช่นกัน ความยืดหยุ่นนี้ทำให้คุณสามารถ **replace paragraph text** ในหลายสถานการณ์โดยไม่ต้องเปลี่ยนโค้ด

### โมเดลจะรักษาการจัดรูปแบบของย่อหน้า (ฟอนต์, สี) หรือไม่?

เนื่องจากเราเพียงแทนที่ `Run` ภายในอ็อบเจกต์ `Paragraph` เดียวกัน สไตล์ที่มีอยู่ (ระดับหัวข้อ, รายการหัวข้อย่อย, การเยื้อง) จะคงอยู่ หากต้องการเปลี่ยนสไตล์เอง สามารถจัดการ `Paragraph.getParagraphFormat()` หลังการแทนที่ได้

### หากเซิร์ฟเวอร์ LLM ของฉันต้องการ HTTPS พร้อมใบรับรอง self‑signed จะทำอย่างไร?

`AiModelEndpoint` รองรับ URL ที่มี `https://`. หากใบรับรองไม่เป็นที่เชื่อถือ คุณต้องกำหนดค่า SSL context ของ Java ให้เชื่อถือ หรือรันเซิร์ฟเวอร์ด้วยใบรับรองที่ถูกต้อง การตั้งค่านี้อยู่นอกขอบเขตของบทแนะนำนี้ แต่มีเอกสารอธิบายอย่างละเอียดในคู่มือ Java SSL

## เคล็ดลับสำหรับการบูรณาการระดับ Production

| Tip | Why it matters |
|-----|----------------|
| **Cache the endpoint** | การสร้าง `AiModelEndpoint` ใหม่ในทุกคำขอจะเพิ่มภาระงาน |
| **Batch edits** | หากคุณมีหลายย่อหน้า ให้ส่งทั้งหมดในคำขอเดียว (เช่น JSON array) เพื่อลดความหน่วง |
| **Validate LLM output** | ตรวจสอบสตริงที่คืนเสมอว่ามีค่า null หรือว่างก่อนแทรก |
| **Log prompts and responses** | เป็นประโยชน์สำหรับการดีบักและการปฏิบัติตามกฎระเบียบเมื่อคุณเขียนข้อความทางกฎหมายใหม่ |
| **Graceful fallback** | หาก LLM ไม่ทำงาน ให้ใช้ย่อดั้งเดิมหรือทำการเขียนทับด้วยวิธีเชิงอรรถง่าย ๆ |

## สรุป

เราได้แสดงวิธี **create custom AI model** ด้วย Aspose.Words, เชื่อมต่อกับ OpenAI‑compatible endpoint, แล้ว **edit paragraph with AI** เพื่อ **make text more formal** โดยทำตามหกขั้นตอน—กำหนด endpoint, โหลดเอกสาร, เริ่มต้นโมเดล,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}