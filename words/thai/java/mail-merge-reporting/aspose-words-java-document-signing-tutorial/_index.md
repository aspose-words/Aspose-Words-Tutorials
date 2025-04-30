---
"date": "2025-03-28"
"description": "เรียนรู้วิธีการทำให้การลงนามเอกสารเป็นแบบอัตโนมัติโดยใช้ Aspose.Words สำหรับ Java บทช่วยสอนนี้ครอบคลุมถึงการตั้งค่าสภาพแวดล้อม การสร้างข้อมูลทดสอบ การเพิ่มบรรทัดลายเซ็น และการลงนามเอกสารแบบดิจิทัล"
"title": "สร้างระบบอัตโนมัติในการลงนามเอกสารใน Java ด้วย Aspose.Words คำแนะนำที่ครอบคลุม"
"url": "/th/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# สร้างระบบอัตโนมัติในการลงนามเอกสารใน Java ด้วย Aspose.Words: คู่มือฉบับสมบูรณ์

## การแนะนำ

ในโลกธุรกิจที่เปลี่ยนแปลงอย่างรวดเร็วในปัจจุบัน การจัดการเอกสารอย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญ การทำให้การสร้างและการลงนามดิจิทัลของเอกสารเป็นแบบอัตโนมัติจะช่วยประหยัดเวลาและลดข้อผิดพลาดได้ บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับการใช้ Aspose.Words สำหรับ Java เพื่อสร้างข้อมูลทดสอบสำหรับผู้ลงนาม เพิ่มบรรทัดลายเซ็น และลงนามเอกสารแบบดิจิทัล

**สิ่งที่คุณจะได้เรียนรู้:**
- การตั้งค่า Aspose.Words ในโครงการ Java
- การสร้างข้อมูลผู้ลงนามการทดสอบด้วย Java
- การเพิ่มบรรทัดลายเซ็นลงในเอกสาร Word
- การลงนามเอกสารแบบดิจิทัลโดยใช้ใบรับรองดิจิทัล

เริ่มต้นด้วยการเตรียมสภาพแวดล้อมการพัฒนาของคุณกันก่อน!

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ โปรดตรวจสอบให้แน่ใจว่าการตั้งค่าของคุณตรงตามข้อกำหนดเหล่านี้:

- **ชุดพัฒนา Java (JDK):** เวอร์ชัน 8 ขึ้นไป.
- **สภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE):** เช่น IntelliJ IDEA หรือ Eclipse
- **Aspose.คำศัพท์สำหรับภาษา Java:** สามารถรวมไลบรารีนี้ผ่าน Maven หรือ Gradle ได้

### ข้อกำหนดเบื้องต้นของความรู้

ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม Java และความคุ้นเคยกับการจัดการไฟล์และสตรีมจะเป็นประโยชน์ หากคุณเพิ่งเริ่มใช้ Aspose ไม่ต้องกังวล เราจะอธิบายสิ่งสำคัญให้คุณฟัง

## การตั้งค่า Aspose.Words

ในการใช้ Aspose.Words สำหรับ Java ในโปรเจ็กต์ของคุณ ให้ทำตามขั้นตอนเหล่านี้:

### การพึ่งพา Maven

เพิ่มการอ้างอิงต่อไปนี้ให้กับของคุณ `pom.xml` ไฟล์:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### การอ้างอิงของ Gradle

สำหรับโครงการ Gradle ให้รวมบรรทัดนี้ไว้ใน `build.gradle` ไฟล์:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### การขอใบอนุญาต

Aspose นำเสนอตัวเลือกการออกใบอนุญาตที่แตกต่างกัน:

- **ทดลองใช้งานฟรี:** ดาวน์โหลดเวอร์ชันทดลองใช้งานฟรีเพื่อทดสอบคุณสมบัติต่างๆ
- **ใบอนุญาตชั่วคราว:** ขอใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินผล
- **ซื้อ:** หากต้องการเข้าถึงแบบเต็มรูปแบบ กรุณาซื้อใบอนุญาตจากเว็บไซต์ของ Aspose

ตรวจสอบให้แน่ใจว่าโครงการของคุณได้รับการกำหนดค่าด้วยการอ้างอิงที่จำเป็นและใบอนุญาตที่จำเป็นทั้งหมด การตั้งค่านี้จะช่วยให้คุณใช้ประโยชน์จากความสามารถในการจัดการเอกสารอันทรงพลังของ Aspose ได้อย่างราบรื่น

## คู่มือการใช้งาน

เราจะแนะนำคุณลักษณะแต่ละอย่างทีละขั้นตอน โดยเริ่มจากการสร้างข้อมูลผู้ลงนามทดสอบ

### คุณลักษณะที่ 1: สร้างข้อมูลการทดสอบสำหรับผู้ลงนาม

#### ภาพรวม

ฟีเจอร์นี้จะสร้างรายชื่อผู้ลงนามพร้อมรหัสประจำตัว ชื่อ ตำแหน่ง และรูปภาพเฉพาะ ซึ่งถือเป็นสิ่งสำคัญสำหรับการทดสอบสถานการณ์การลงนามเอกสารโดยไม่ใช้ข้อมูลจริง

##### ขั้นตอนที่ 1: ตั้งค่าคลาส Java ของคุณ

สร้างคลาสที่มีชื่อว่า `SignPersonCreator` และนำเข้าไลบรารีที่จำเป็น:

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### คำอธิบาย

- **รหัสประจำตัว:** สร้างตัวระบุที่ไม่ซ้ำกันสำหรับผู้ลงนามแต่ละคน
- **รับไบต์จากสตรีม:** แปลงไฟล์รูปภาพเป็นอาร์เรย์ไบต์เพื่อจัดเก็บข้อมูล

### คุณสมบัติ 2: เพิ่มบรรทัดลายเซ็นลงในเอกสาร

#### ภาพรวม

ฟีเจอร์นี้จะเพิ่มบรรทัดลายเซ็นลงในเอกสารของคุณ โดยเชื่อมโยงกับรายละเอียดของผู้ลงนาม

##### ขั้นตอนที่ 1: สร้างคลาส SignatureLineAdder

การดำเนินการตาม `SignatureLineAdder` ชั้นเรียนดังต่อไปนี้:

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### คำอธิบาย

- **ตัวเลือก SignatureLine:** กำหนดค่าชื่อและตำแหน่งของผู้ลงนาม
- **แทรกบรรทัดลายเซ็น:** แทรกบรรทัดลายเซ็นลงในเอกสารที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

### คุณสมบัติที่ 3: ลงนามเอกสารด้วยใบรับรองดิจิทัล

#### ภาพรวม

ฟีเจอร์นี้จะลงนามเอกสารแบบดิจิทัลโดยใช้ใบรับรองดิจิทัล เพื่อรับรองความถูกต้องและสมบูรณ์

##### ขั้นตอนที่ 1: สร้างคลาส DocumentSigner

การดำเนินการตาม `DocumentSigner` ระดับ:

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### คำอธิบาย

- **ผู้ถือใบรับรอง:** แสดงถึงใบรับรองดิจิทัลที่ใช้ในการลงนาม
- **เข้าสู่ระบบ:** วิธีการที่ลงนามเอกสารด้วยตัวเลือกและใบรับรองที่ระบุ

## บทสรุป

ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีการสร้างเอกสารและลงนามอัตโนมัติใน Java โดยใช้ Aspose.Words เมื่อทำตามขั้นตอนเหล่านี้ คุณจะปรับปรุงกระบวนการจัดการเอกสาร เพิ่มความปลอดภัย และรับรองความสมบูรณ์ของข้อมูล หากต้องการศึกษาเพิ่มเติม โปรดพิจารณาเจาะลึกคุณลักษณะขั้นสูงของ Aspose.Words

**ขั้นตอนต่อไป:**
- สำรวจฟีเจอร์เพิ่มเติมของ Aspose.Words เช่น การผสานจดหมายหรือการสร้างรายงาน
- ตรวจสอบเอกสาร Aspose เพื่อดูคำแนะนำโดยละเอียดและเอกสารอ้างอิง API
- ทดลองใช้รูปแบบเอกสารต่างๆ ที่รองรับโดย Aspose.Words

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}