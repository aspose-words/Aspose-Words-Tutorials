---
date: 2026-02-22
description: Aspose.Words ile Java’da belge formatını nasıl tespit edeceğinizi öğrenin
  ve dosyaları formatına göre otomatik olarak taşıyın. DOC, DOCX ve daha fazlasını
  tanımlayın.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java kullanarak Java'da belge formatını tespit et
url: /tr/java/document-loading-and-saving/determining-document-format/
weight: 25
---

.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# detect document format java using Aspose.Words for Java

Bir dosya topluluğunda **detect document format java** yapmanız gerektiğinde, dosyaları doğru klasörlere otomatik olarak ayırabilmek saatler süren manuel işi ortadan kaldırabilir. Bu öğreticide Aspose.Words for Java’ın Word, RTF, HTML, ODT ve birçok diğer formatı nasıl kolayca tanımladığını ve ardından **move files by format** ile düzenli dizinlere nasıl taşıyabileceğinizi göstereceğiz.

## Quick Answers
- **“detect document format java” ne anlama geliyor?** Java kodu kullanarak bir dosyanın Word işlem formatını (DOC, DOCX, RTF vb.) programatik olarak tanımlama sürecidir.  
- **Bu yeteneği hangi kütüphane sağlıyor?** Aspose.Words for Java, `FileFormatUtil.detectFileFormat` API’sini sunar.  
- **Araç şifreli dosyaları da işleyebiliyor mu?** Evet – `FileFormatInfo.isEncrypted()` bayrağı, belgenin şifre korumalı olup olmadığını bildirir.  
- **Üretim ortamında lisans gerekir mi?** Değerlendirme dışı dağıtımlar için ticari bir Aspose.Words lisansı gereklidir.  
- **Algılamadan sonra dosyalar otomatik olarak taşınabilir mi?** Kesinlikle – algılama sonucunu `FileUtils.copyFile` ile birleştirerek dosyaları özel klasörlere sıralayabilirsiniz.

## What is detect document format java?
`detect document format java`, bir dosyanın ikili başlığını inceleyerek hangi Word işlem formatına (ör. DOC, DOCX, ODT) ait olduğunu belirlemek için Java kodu kullanılması anlamına gelir. Aspose.Words, belgeyi tamamen yüklemeden dosyayı okur, böylece işlem hızlı ve bellek‑verimli olur.

## Why move files by format?
Belgeleri yerel formatlarına göre düzenlemek, sonraki işlemleri basitleştirir:

- **Batch conversions** tüm DOCX dosyaları tek bir klasörde olduğunda sorunsuz gerçekleşir.  
- **Legacy support**: eski 97‑öncesi Word dosyalarını özel bir işleme ayırabilirsiniz.  
- **Security**: şifreli belgeler otomatik olarak karantinaya alınabilir.  

## Prerequisites

Başlamadan önce şunların yüklü olduğundan emin olun:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (en son sürümü indirin)  
- Java Development Kit (JDK) 8 veya üzeri  
- Java I/O ve akışları hakkında temel bilgi  

## Step 1: Set up directories for each format

İlk olarak algılanan dosyaların taşınacağı temiz bir klasör yapısı oluştururuz. Bu, iş akışını düzenli tutar ve yeni format kategorileri eklemeyi kolaylaştırır.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

> **Pro tip:** Üretim kodunda sabit yol tanımlamaktan kaçınmak için mutlak yollar kullanın veya temel dizini bir properties dosyasıyla yapılandırın.

## Step 2: Detect the document format and move files

**detect document format java** işleminin kalbi aşağıdaki döngüdedir. Her dosyayı tarar, tipini belirler ve uygun klasöre kopyalar.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

`switch` bloğu, ilgilendiğiniz tüm formatları kapsayacak şekilde genişletilebilir. Her durum, dostça bir mesaj yazdırır ve ardından dosyayı eşleşen klasöre taşır.

## Complete source code for detecting document format java

Aşağıda, klasör oluşturma ve algılama mantığını birleştiren tam, çalıştırılabilir örnek yer almaktadır. Java sınıfına yapıştırın, temel yolu ayarlayın ve karışık belgeler içeren bir klasörde çalıştırın.

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Common issues and troubleshooting

| Issue | Why it happens | How to fix |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Dosya bozuk veya Word dışı bir formatta. | Dosya uzantısını kontrol edin veya örnekteki *Unknown* klasörüne taşıma geri dönüşü ekleyin. |
| **Encrypted files throw an exception** | API, şifre kontrolünden önce içeriği okumaya çalışıyor. | `info.isEncrypted()` metodunu diğer işlemlerden önce çağırın. |
| **Directory creation fails on Linux** | Yetersiz izinler veya eksik üst klasör. | Java sürecinin yazma iznine sahip olduğundan ve temel yolun var olduğundan emin olun. |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: You can download Aspose.Words for Java from the [here](https://releases.aspose.com/words/java/) and follow the installation instructions provided.

**Q: What document formats are supported for detection?**  
A: Aspose.Words can detect DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML, and older pre‑97 formats, among others.

**Q: Can this code handle password‑protected documents?**  
A: Yes. The `FileFormatInfo.isEncrypted()` flag identifies encrypted files, allowing you to move them to a secure folder without opening them.

**Q: Is there a performance impact when scanning large folders?**  
A: Detection reads only the file header, so even thousands of files are processed quickly. For very large batches, consider parallel streams.

**Q: How can I extend the script to convert unsupported formats?**  
A: After detection, you can call `Document.save` with the desired output format for any supported source type.

## Conclusion

**detect document format java** özelliğini Aspose.Words ile kullanarak Word‑ile ilgili dosyaları otomatik olarak sıralayabilir, karantinaya alabilir veya dönüştürebilirsiniz. Örnek kod, temiz bir klasör hiyerarşisi oluşturmayı, her dosyanın formatını tanımlamayı ve buna göre taşımayı gösterir—zaman kazandırır ve manuel hataları azaltır.

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}