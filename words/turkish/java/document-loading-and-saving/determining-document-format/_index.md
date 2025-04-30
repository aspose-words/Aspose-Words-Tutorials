---
"description": "Aspose.Words ile Java'da belge biçimlerini nasıl algılayacağınızı öğrenin. DOC, DOCX ve daha fazlasını tanımlayın. Dosyaları verimli bir şekilde düzenleyin."
"linktitle": "Belge Formatının Belirlenmesi"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belge Biçimini Belirleme"
"url": "/tr/java/document-loading-and-saving/determining-document-format/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belge Biçimini Belirleme


## Java için Aspose.Words'de Belge Biçimini Belirlemeye Giriş

Java'da belge işlemeyle çalışırken, uğraştığınız dosyaların biçimini belirlemek çok önemlidir. Java için Aspose.Words, belge biçimlerini tanımlamak için güçlü özellikler sunar ve bu süreçte size yol göstereceğiz.

## Ön koşullar

Başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:

- [Java için Aspose.Words](https://releases.aspose.com/words/java/)
- Sisteminizde yüklü Java Geliştirme Kiti (JDK)
- Java programlamanın temel bilgisi

## Adım 1: Dizin Kurulumu

Öncelikle dosyalarımızı etkili bir şekilde organize etmek için gerekli dizinleri kurmamız gerekiyor. Farklı belge türleri için dizinler oluşturacağız.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Eğer henüz mevcut değilse dizinleri oluşturun.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Desteklenen, bilinmeyen, şifrelenmiş ve 97 öncesi belge türleri için dizinler oluşturduk.

## Adım 2: Belge Biçimini Algılama

Şimdi dizinlerimizdeki belgelerin formatını tespit edelim. Bunu başarmak için Java için Aspose.Words kullanacağız.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Belge türünü görüntüle
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Gerektiğinde diğer belge biçimleri için durumlar ekleyin
    }

    // Şifrelenmiş belgeleri yönetin
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Diğer belge türlerini yönetin
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

Bu kod parçacığında dosyalar arasında geziniyoruz, biçimlerini tespit ediyoruz ve bunları ilgili dizinlere düzenliyoruz.

## Java için Aspose.Words'de Belge Formatını Belirlemeye Yönelik Tam Kaynak Kodu

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Eğer henüz mevcut değilse dizinleri oluşturun.
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
            // Belge türünü görüntüle
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

## Çözüm

Java için Aspose.Words'de belge biçimlerini belirlemek, verimli belge işleme için önemlidir. Bu kılavuzda özetlenen adımlarla, belge türlerini belirleyebilir ve bunları Java uygulamalarınızda uygun şekilde işleyebilirsiniz.

## SSS

### Java için Aspose.Words'ü nasıl yüklerim?

Java için Aspose.Words'ü şu adresten indirebilirsiniz: [Burada](https://releases.aspose.com/words/java/) ve verilen kurulum talimatlarını izleyin.

### Desteklenen belge biçimleri nelerdir?

Aspose.Words for Java, DOC, DOCX, RTF, HTML ve daha fazlası dahil olmak üzere çeşitli belge biçimlerini destekler. Tam liste için belgelere başvurabilirsiniz.

### Aspose.Words for Java kullanarak şifrelenmiş belgeleri nasıl tespit edebilirim?

Kullanabilirsiniz `FileFormatUtil.detectFileFormat()` Bu kılavuzda gösterildiği gibi şifrelenmiş belgeleri tespit etme yöntemi.

### Eski belge formatlarıyla çalışırken herhangi bir sınırlama var mı?

MS Word 6 veya Word 95 gibi eski belge biçimleri, özellikler ve modern uygulamalarla uyumluluk açısından sınırlamalara sahip olabilir. Gerektiğinde bu belgeleri yükseltmeyi veya dönüştürmeyi düşünün.

### Java uygulamamda belge biçimi algılamayı otomatikleştirebilir miyim?

Evet, sağlanan kodu Java uygulamanıza entegre ederek belge biçimi algılamayı otomatikleştirebilirsiniz. Bu, belgeleri algılanan biçimlerine göre işlemenize olanak tanır.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}