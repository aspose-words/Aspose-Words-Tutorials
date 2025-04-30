---
"description": "Bu kapsamlı, adım adım kılavuzla Aspose.Words for .NET'i kullanarak belge dosya biçimlerini nasıl algılayacağınızı öğrenin."
"linktitle": "Belge Dosya Biçimini Algıla"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Belge Dosya Biçimini Algıla"
"url": "/tr/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Belge Dosya Biçimini Algıla

## giriiş

Günümüzün dijital dünyasında, farklı belge biçimlerini verimli bir şekilde yönetmek hayati önem taşır. Word, PDF, HTML veya diğer biçimleri kullanıyor olun, bu dosyaları doğru bir şekilde algılayıp işleyebilmek size çok fazla zaman ve emek kazandırabilir. Bu eğitimde, .NET için Aspose.Words kullanarak belge dosya biçimlerinin nasıl algılanacağını inceleyeceğiz. Bu kılavuz, ön koşullardan ayrıntılı adım adım kılavuza kadar bilmeniz gereken her şeyde size yol gösterecektir.

## Ön koşullar

Koda dalmadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

- Aspose.Words for .NET: Buradan indirebilirsiniz [Burada](https://releases.aspose.com/words/net/). Geçerli bir lisansınız olduğundan emin olun. Değilse, bir tane alabilirsiniz [geçici lisans](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Güncel herhangi bir sürüm sorunsuz çalışacaktır.
- .NET Framework: Doğru sürümün yüklü olduğundan emin olun.

## Ad Alanlarını İçe Aktar

Başlamak için projenize gerekli ad alanlarını içe aktarmanız gerekir:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Takip etmeyi kolaylaştırmak için örneği birden fazla adıma bölelim.

## Adım 1: Dizinleri Ayarlayın

Öncelikle dosyaların formatlarına göre sıralanacağı dizinleri ayarlamamız gerekiyor.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Eğer henüz mevcut değilse dizinleri oluşturun.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Adım 2: Dosyaların Listesini Alın

Daha sonra dizindeki dosyaların bir listesini alacağız, bozuk belgeleri hariç tutacağız.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Adım 3: Dosya Biçimlerini Algıla

Şimdi her dosyayı inceleyip Aspose.Words kullanarak formatını tespit edeceğiz.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Belge türünü görüntüle
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Çözüm

Aspose.Words for .NET kullanarak belge dosya biçimlerini algılamak basit bir işlemdir. Dizinlerinizi ayarlayarak, dosya listenizi alarak ve dosya biçimlerini algılamak için Aspose.Words'ü kullanarak belgelerinizi etkili bir şekilde düzenleyebilir ve yönetebilirsiniz. Bu yaklaşım yalnızca zamandan tasarruf sağlamakla kalmaz, aynı zamanda çeşitli belge biçimlerini doğru bir şekilde işlemenizi de sağlar.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, Word belgeleriyle programatik olarak çalışmak için güçlü bir kütüphanedir. Geliştiricilerin çeşitli formatlarda belgeler oluşturmasına, değiştirmesine ve dönüştürmesine olanak tanır.

### Aspose.Words şifrelenmiş belgeleri tespit edebilir mi?
Evet, Aspose.Words bir belgenin şifrelenip şifrelenmediğini tespit edebilir ve bu tür belgeleri buna göre işleyebilirsiniz.

### Aspose.Words hangi formatları algılayabilir?
Aspose.Words DOC, DOCX, RTF, HTML, MHTML, ODT ve daha birçok formatı algılayabilir.

### Aspose.Words için geçici lisansı nasıl alabilirim?
Geçici bir lisansı şuradan alabilirsiniz: [Aspose Satın Alma](https://purchase.aspose.com/temporary-license/) sayfa.

### Aspose.Words'ün dokümanlarını nerede bulabilirim?
Aspose.Words için belgeler şurada bulunabilir: [Burada](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}