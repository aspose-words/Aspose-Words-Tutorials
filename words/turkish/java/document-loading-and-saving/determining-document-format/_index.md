---
date: 2025-12-20
description: Aspose.Words ile Java’da dosyaları türe göre nasıl düzenleyeceğinizi
  ve belge formatlarını nasıl tespit edeceğinizi öğrenin. DOC, DOCX, RTF ve daha fazlasını
  destekler.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java Kullanarak Dosyaları Türlerine Göre Düzenle
url: /tr/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java Kullanarak Dosyaları Türlerine Göre Düzenleme

Java uygulamanızda **dosyaları türlerine göre düzenlemeniz** gerektiğinde, ilk adım her belgenin formatını güvenilir bir şekilde belirlemektir. Aspose.Words for Java bu süreci basitleştirir; DOC, DOCX, RTF, HTML, ODT ve daha birçok formatı – hatta şifreli veya bilinmeyen dosyaları – tespit etmenizi sağlar. Bu rehberde klasörleri oluşturma, dosya formatlarını tespit etme ve dosyalarınızı otomatik olarak sıralama adımlarını göstereceğiz.

## Hızlı Yanıtlar
- **“Dosyaları türlerine göre düzenleme” ne anlama gelir?**  Bu, belgeleri tespit edilen formatlarına göre (ör. DOCX, PDF, RTF) otomatik olarak klasörlere taşıma anlamına gelir.  
- **Java'da dosya formatını tespit etmeye yardımcı olan kütüphane hangisidir?** Aspose.Words for Java, `FileFormatUtil.detectFileFormat()` metodunu sunar.  
- **API bilinmeyen dosya türlerini tanımlayabilir mi?** Evet – desteklenmeyen veya tanınamayan dosyalar için `LoadFormat.UNKNOWN` döndürür.  
- **Şifreli belge tespiti destekleniyor mu?** Kesinlikle; `FileFormatInfo.isEncrypted()` bayrağı dosyanın şifre korumalı olup olmadığını gösterir.  
- **Üretim ortamında lisans gerekir mi?** Ticari dağıtımlar için geçerli bir Aspose.Words lisansı gereklidir.

## Giriş: Aspose.Words for Java ile Dosyaları Türlerine Göre Düzenleme

Java’da belge işleme yaparken, elinizdeki dosyaların formatını belirlemek çok önemlidir. Aspose.Words for Java, **detect file format java** için güçlü özellikler sunar ve dosyalarınızı verimli bir şekilde düzenlemenize yardımcı olur.

## Önkoşullar

Başlamadan önce aşağıdaki önkoşulları karşıladığınızdan emin olun:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Sisteminizde kurulu Java Development Kit (JDK)
- Java programlama hakkında temel bilgi

## Adım 1: Dizin Kurulumu

İlk olarak dosyalarımızı etkili bir şekilde düzenlemek için gerekli dizinleri oluşturmamız gerekiyor. Farklı belge türleri için klasörler oluşturacağız.

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

Desteklenen, bilinmeyen, şifreli ve pre‑97 belge türleri için dizinler oluşturduk.

## Adım 2: Belge Formatını Tespit Etme

Şimdi dizinlerimizdeki belgelerin formatını tespit edelim. Bunu gerçekleştirmek için Aspose.Words for Java’yı kullanacağız.

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

Bu kod parçacığında dosyalar üzerinde döngü yapıyor, **detect file format java**, ve onları uygun klasörlere yerleştiriyoruz.

## Aspose.Words for Java'da Belge Formatını Belirlemek İçin Tam Kaynak Kodu

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

## Java'da Dosya Formatını Nasıl Tespit Edebilirsiniz

`FileFormatUtil.detectFileFormat()` metodu dosya başlığını inceler ve bir `FileFormatInfo` nesnesi döndürür. Bu nesne **yükleme formatını**, dosyanın şifreli olup olmadığını ve diğer yararlı meta verileri size bildirir. Bu bilgileri kullanarak **bilinmeyen dosya türlerini** programatik olarak tanımlayabilir ve her birine nasıl işlem yapılacağına karar verebilirsiniz.

## Bilinmeyen Dosya Türlerini Tanımlama

API `LoadFormat.UNKNOWN` döndürdüğünde, dosya ya bozuk ya da Aspose.Words tarafından desteklenmeyen bir formattadır. Örnek kodumuzda bu dosyaları **Unknown** klasörüne taşıyarak daha sonra incelemenizi sağlıyoruz.

## Yaygın Sorunlar ve Çözümleri

| Sorun | Sebep | Çözüm |
|-------|--------|-----|
| Dosyalar her zaman *Supported* klasörüne yerleştiriliyor | `FileFormatUtil` başlığı okuyamıyor (ör. dosya boş) | Doğru dosya yolunu gönderdiğinizden ve dosyanın sıfır bayt olmadığından emin olun. |
| Şifreli dosyalar bir istisna fırlatıyor | Şifreleme işlenmeden okunmaya çalışılıyor | `info.isEncrypted()` kontrolünü, kodda gösterildiği gibi, daha fazla işleme başlamadan önce kullanın. |
| Pre‑97 Word belgeleri tespit edilmiyor | Eski formatlar `DOC_PRE_WORD_60` durumuna ihtiyaç duyar | `case LoadFormat.DOC_PRE_WORD_60` bloğunu tutun, böylece *Pre97* klasörüne yönlendirilir. |

## Sık Sorulan Sorular

### Aspose.Words for Java nasıl kurulur?

Aspose.Words for Java’yı [buradan](https://releases.aspose.com/words/java/) indirebilir ve sağlanan kurulum talimatlarını izleyebilirsiniz.

### Desteklenen belge formatları nelerdir?

Aspose.Words for Java, DOC, DOCX, RTF, HTML, ODT ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler. Tam liste için resmi dokümantasyona bakın.

### Aspose.Words for Java kullanarak şifreli belgeleri nasıl tespit edebilirim?

`FileFormatUtil.detectFileFormat()` metodunu kullanın; dönen `FileFormatInfo.isEncrypted()` bayrağı şifrelemeyi gösterir; bu rehberdeki örnek kodda olduğu gibi.

### Eski belge formatlarıyla çalışırken herhangi bir sınırlama var mı?

MS Word 6 veya Word 95 gibi eski formatlar modern özelliklerden yoksun olabilir ve uyumluluk sorunları yaşayabilir. Mümkün olduğunda bu belgeleri daha yeni formatlara dönüştürmeyi düşünün.

### Java uygulamamda belge formatı tespitini otomatikleştirebilir miyim?

Evet, sağlanan kodu uygulamanızın iş akışına entegre edin. Böylece tespit edilen formatlara göre otomatik sıralama ve işleme gerçekleştirebilirsiniz.

**Son Güncelleme:** 2025-12-20  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12 (latest)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}