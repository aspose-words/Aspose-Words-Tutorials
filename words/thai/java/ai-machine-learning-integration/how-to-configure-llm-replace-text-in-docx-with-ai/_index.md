---
category: general
date: 2026-03-04
description: วิธีตั้งค่า LLM สำหรับ Document AI และแทนที่ข้อความในไฟล์ DOCX ด้วย AI
  – คู่มือขั้นตอนโดยละเอียดพร้อมโค้ด Java เต็มรูปแบบ
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: th
og_description: วิธีตั้งค่า LLM สำหรับ Document AI และแทนที่ข้อความในไฟล์ DOCX ด้วย
  AI – คู่มือครบถ้วนพร้อมโค้ด Java ที่สามารถรันได้
og_title: วิธีตั้งค่า LLM – แทนที่ข้อความในไฟล์ DOCX ด้วย AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /th/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งค่า LLM – แทนที่ข้อความใน DOCX ด้วย AI

เคยสงสัย **how to configure LLM** ว่าสามารถแก้ไขไฟล์ Word ให้คุณได้หรือไม่? คุณไม่ได้เป็นคนเดียวที่เจอปัญหา นักพัฒนาจำนวนมากเจออุปสรรคเมื่อจำเป็นต้องแทนที่วลีภายในไฟล์ `.docx` โดยไม่เปิด Microsoft Word ข่าวดีคืออะไร? ด้วย LLM ที่ทำงานบนเครื่องและ Document AI wrapper เล็ก ๆ คุณสามารถสลับข้อความในไฟล์ DOCX ได้ด้วยไม่กี่บรรทัดของ Java.

ในบทแนะนำนี้ เราจะเดินผ่านกระบวนการทั้งหมด: ตั้งค่าการเชื่อมต่อ LLM, โหลด DOCX, ไปจนถึงการใช้ **Document AI** เพื่อแทนที่วลีเป้าหมาย. ในตอนท้ายคุณจะได้ตัวอย่างที่ทำงานได้อย่างอิสระและสามารถนำไปใส่ในโครงการ Maven หรือ Gradle ใดก็ได้ ไม่ต้องใช้คีย์ API ภายนอก ไม่ต้องเสียค่าใช้จ่ายบนคลาวด์—เพียงโมเดลของคุณเองที่ฟังที่ `http://localhost:8080/v1`.

> **Quick win:** ถ้าคุณมี LLM บนเครื่องแล้ว (เช่น Llama 3 หรือ Mistral) ที่เปิด endpoint ที่เข้ากันได้กับ OpenAI โค้ดด้านล่างจะทำงานได้ทันที.

---

![แผนภาพการตั้งค่า LLM สำหรับ Document AI](/images/configure-llm-diagram.png){: .center-image alt="แผนภาพการตั้งค่า llm"}

## สิ่งที่คุณต้องการ

- **Java 17** (หรือ JDK ล่าสุดใดก็ได้)  
- **local LLM** ที่เปิด endpoint แบบ OpenAI‑style `/v1` (เช่น Ollama, LMStudio)  
- **Document AI Java library** (สมมติ `com.example:document-ai:1.2.0` บน Maven Central)  
- ตัวอย่างไฟล์ DOCX (`input.docx`) ที่วางไว้ในโฟลเดอร์ที่รู้จัก  

หากคุณขาดส่วนใดส่วนหนึ่งเหล่านี้ ให้เริ่ม Ollama อย่างรวดเร็ว:

```bash
ollama serve &
ollama run llama3
```

ซึ่งจะเริ่มเซิร์ฟเวอร์ที่ `http://localhost:8080/v1` พร้อมรับคำขอ.

---

## วิธีตั้งค่า LLM สำหรับ Document AI

สิ่งแรกที่เราทำคือบอกให้ไคลเอนต์ `DocumentAi` รู้ว่าจะหาโมเดลได้จากที่ไหนและใช้โมเดลใด. นี่คือขั้นตอน **how to configure LLM** ที่บทแนะนำหลาย ๆ อย่างมักมองข้าม.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*ทำไมเรื่องนี้ถึงสำคัญ:*  
อ็อบเจ็กต์ `AiModelConfig` แยกรายละเอียด HTTP ออกไป ทำให้ `DocumentAi` สามารถมุ่งเน้นที่เนื้อหาได้ หากคุณเปลี่ยนไปใช้ผู้ให้บริการบนคลาวด์ คุณเพียงเปลี่ยน `baseUrl` และ `apiKey`—ส่วนที่เหลือของโค้ดจะไม่ต้องแก้ไข.

---

## โหลดและเตรียมเอกสาร DOCX

ต่อไปเรานำไฟล์ Word เข้าสู่หน่วยความจำ. คลาส `Document` จัดการทั้ง `.docx` และ `.pdf` ภายใน แต่ที่นี่เราสนใจเฉพาะ DOCX เท่านั้น.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Pro tip:* ใช้เส้นทางแบบ absolute ระหว่างการดีบั๊กเพื่อหลีกเลี่ยงข้อผิดพลาด “file not found”. เมื่อมั่นใจแล้วให้สลับกลับไปใช้เส้นทางแบบ relative เพื่อความพกพา.

---

## แทนที่ข้อความใน DOCX ด้วย AI

ตอนนี้มาถึงหัวใจของบทแนะนำ—**how to replace text** ในไฟล์ DOCX ด้วยความช่วยเหลือของ AI. เมธอด `replaceText` จะส่งเนื้อหาเอกสารไปยัง LLM, ขอให้ทำการแทนที่, แล้วคืนข้อความที่แก้ไขแล้ว.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*อะไรที่เกิดขึ้นเบื้องหลัง?*  
`DocumentAi` ทำการแปลง DOCX เป็นข้อความธรรมดา, สร้าง prompt เช่น:

> “ในเอกสารต่อไปนี้ ให้แทนที่ทุกการปรากฏของ ‘old phrase’ ด้วย ‘new phrase’ และคืนเฉพาะข้อความที่อัปเดต”

LLM ประมวลผลคำขอและส่งกลับเนื้อหาที่แก้ไขแล้ว วิธีนี้ทำงานได้แม้เมื่อวลีกระจายหลาย run หรือหลายย่อหน้า—สิ่งที่การแทนที่ด้วยสตริงธรรมดามักพลาด.

---

## ตรวจสอบและแสดงข้อความที่อัปเดต

สุดท้ายเราจะพิมพ์ข้อความที่ AI แก้ไขแล้วออกที่คอนโซล. ในแอปจริงคุณอาจเขียนผลลัพธ์กลับไปยัง DOCX ใหม่, แต่การพิมพ์ช่วยให้คุณตรวจสอบได้อย่างรวดเร็ว.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**ผลลัพธ์ที่คาดหวัง** (สมมติว่า DOCX ดั้งเดิมมีข้อความ “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

หากคุณเห็นวลีใหม่ปรากฏขึ้น, ยินดีด้วย—**you’ve just learned how to use Document AI to replace a phrase with AI**.

---

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน, นี่คือตัวอย่างคลาส Java ที่พร้อมรัน. คัดลอกและวางลงใน `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### วิธีการรัน

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

ตรวจสอบให้แน่ใจว่าเซิร์ฟเวอร์ LLM ทำงานอยู่ก่อนรันโปรแกรม; มิฉะนั้นคุณจะได้รับข้อผิดพลาด timeout การเชื่อมต่อ.

---

## กรณีขอบและข้อผิดพลาดทั่วไป

| สถานการณ์ | สิ่งที่ควรระวัง | วิธีแก้แนะนำ |
|-----------|-------------------|---------------|
| **ไม่พบวลี** | LLM ส่งคืนข้อความต้นฉบับโดยไม่มีการเปลี่ยนแปลง. | ตรวจสอบการสะกดและความแตกต่างของตัวพิมพ์ใหญ่‑เล็กอีกครั้ง; คุณสามารถเพิ่ม `ignoreCase:true` ไปยัง prompt หาก wrapper ของคุณรองรับ. |
| **เอกสารขนาดใหญ่ (>5 MB)** | ขนาดของ prompt อาจเกินขีดจำกัด token ของโมเดล. | แยก DOCX เป็นส่วน ๆ ประมวลผลแต่ละส่วนแยกกัน แล้วต่อผลลัพธ์เข้าด้วยกัน. |
| **Local LLM คืนข้อผิดพลาด** | มักเกิดจากชื่อโมเดลที่ไม่ตรงกัน. | ตรวจสอบให้แน่ใจว่าชื่อโมเดลใน UI ของ LLM (`ollama list`) ตรงกับ `modelConfig.setModelName`. |
| **อักขระ Unicode แสดงผลผิด** | ปัญหา encoding เมื่ออ่าน DOCX. | ตรวจสอบให้แน่ใจว่า Java runtime ของคุณใช้ UTF‑8 (เพิ่ม `-Dfile.encoding=UTF-8` ไปยังอาร์กิวเมนต์ของ JVM). |

---

## ขั้นตอนต่อไป

ตอนนี้คุณรู้ **how to replace text in DOCX** ด้วย AI แล้ว, คุณอาจอยากสำรวจต่อ:

- **How to use Document AI** สำหรับงานที่ซับซ้อนมากขึ้น เช่น การสกัดตารางหรือการรักษารูปแบบสไตล์.  
- **Replace phrase with AI** ใน PDFs โดยสลับอาร์กิวเมนต์ของคอนสตรัคเตอร์ `Document`.  
- **Batch processing**: วนลูปผ่านไดเรกทอรีของไฟล์ DOCX และใช้การแทนที่เดียวกัน.  

แต่ละรายการนี้สร้างบนพื้นฐานของ `AiModelConfig` และ `DocumentAi` เดียวกัน, ดังนั้นคุณจะไม่ต้องเริ่มจากศูนย์

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}