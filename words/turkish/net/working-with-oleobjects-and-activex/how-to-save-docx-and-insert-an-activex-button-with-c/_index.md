---
category: general
date: 2026-09-08
description: C#'ta bir ActiveX kontrolü eklerken docx dosyasını nasıl kaydedilir.
  Komut düğmesini kodla eklemek için bu adım adım kılavuzu izleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: tr
lastmod: 2026-09-08
og_description: C#'ta bir ActiveX kontrolü eklerken docx dosyasını nasıl kaydedilir?
  Bu öğretici, bir Word belgesini programlı olarak oluşturma, bir komut düğmesi ekleme
  ve dosyayı kalıcı hale getirme sürecini adım adım gösterir.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: C#'ta docx dosyasını kaydetme ve ActiveX düğmesi ekleme
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: C# ile docx dosyasını kaydetme ve bir ActiveX düğmesi ekleme
url: /tr/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile docx kaydetme ve ActiveX düğmesi ekleme

Programatik olarak bir Word belgesi oluşturup ardından interaktif bir düğme içeren docx kaydetmeniz gerekiyorsa, bu kılavuz size bunu nasıl yapacağınızı gösterir. ActiveX kontrolü eklemeyi, bir ActiveX düğmesi eklemeyi ve sonuçta oluşan .docx dosyasını C# ve Aspose.Words kütüphanesi kullanarak kaydetmeyi öğreneceksiniz.

Bu öğretici, **programatik olarak Word belgesi oluşturma**, **komut düğmesi** gömme ve dosyayı diske kalıcı olarak kaydetme adımlarını kapsar. COM nesneleriyle ilgili önceden bir deneyime sahip olmanız gerekmez, ancak temel C# bilgisine ve Visual Studio kurulu olmasına sahip olmalısınız.

## Önkoşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm  
* Visual Studio 2022 (veya herhangi bir C# IDE)  
* Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)  
* C# proje yapısının temel kavramları  

Bu öğeler, kodun derlenip ek bir yapılandırma gerektirmeden çalışmasını sağlar.

## Adım 1: Yeni bir C# konsol projesi oluşturun

Word otomasyon mantığını barındıracak bir konsol uygulaması oluşturun.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Yukarıdaki komut, **WordActiveXDemo** adlı bir klasör oluşturur, Aspose.Words referansını ekler ve projeyi derlemeye hazır hâle getirir.

## Adım 2: Programatik olarak bir Word belgesi oluşturun

Oluşturulan `Program.cs` dosyasını açın ve gerekli `using` yönergelerini ekleyin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Şimdi boş bir `Document` nesnesi örnekleyin. Bu nesne, bellek içindeki tüm Word dosyasını temsil eder.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

`Document` sınıfı, tüm Word‑işleme işlemlerinin giriş noktasıdır. Bu aşamada belge henüz sayfa içermez, ancak içerik eklediğinizde Aspose.Words otomatik olarak bir varsayılan bölüm oluşturur.

## Adım 3: ActiveX kontrolü ekleyin – activex düğmesi ekleme

Bir **Forms2OleControl** nesnesi, bir Word paragrafı içine ActiveX kontrolü gömmenizi sağlar. Aşağıdaki kod, genişliği 150 pt ve yüksekliği 30 pt olan bir **CommandButton** ekler.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` kontrolü oluşturur ve güçlü tipli bir `Forms2OleControl` örneği döndürür; bu örneği daha da yapılandırabilirsiniz. Metot, kontrolü barındıracak yeni bir paragrafı otomatik olarak ekler, böylece paragraf nesnelerini manuel olarak yönetmeniz gerekmez.

## Adım 4: Komut düğmesini yapılandırın – komut düğmesi özelliklerini ekleme

Düğmenin **Name** ve **Caption** özelliklerini ayarlayarak çalışma zamanında tanımlanabilir ve kullanıcı arayüzünde anlaşılır hâle getirin.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

`Name` özniteliği, düğmenin tıklama olayını VBA veya bir Word makrosu aracılığıyla ele alırken faydalıdır. `Caption` ise son kullanıcının düğme yüzeyinde gördüğü metindir.

### Pro ipucu
C# tarafında tıklama işlemini otomatikleştirmeyi planlıyorsanız, `cmdSubmit` referansını içeren bir VBA makrosu ekleyin. Word, belge açıldığında makroları etkinleştirmenizi isteyecek; bu, ActiveX kontrolleri için standart güvenlik davranışıdır.

## Adım 5: docx nasıl kaydedilir

Kontrol yerleştirildikten sonra belgeyi bir .docx dosyasına kalıcı hâle getirin. `Save` metodu, dosya uzantısına göre uygun formatı otomatik olarak seçer.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Dosyanın kaydedilmesi, **docx nasıl kaydedilir** iş akışını tamamlar. Oluşan dosya Microsoft Word’de açılabilir ve ActiveX düğmesi ilk sayfada görünecektir. Düğmeye tıkladığınızda, bir makro eklenmemişse yer tutucu bir mesaj gösterilir.

## Adım 6: Programı çalıştırın ve sonucu doğrulayın

Konsol uygulamasını derleyip çalıştırın:

```bash
dotnet run
```

Program tamamlandığında `C:\Temp\CommandButton.docx` dosyasını Microsoft Word’de açın:

* Belge, üst kısımda bir **Submit** düğmesi bulunan tek bir sayfa içerir.  
* Düğmenin üzerine geldiğinizde, `cmdSubmit` adını gösteren bir araç ipucu (tooltip) görünür.  
* Hiçbir içerik kaybolmaz ve dosya boyutu standart bir boş .docx dosyasına benzer olur.

Düğme görünmüyorsa, aşağıdakileri kontrol edin:

1. Word’ün **Trust Center** ayarları ActiveX kontrollerine izin veriyor mu?  
2. Dosya `.docx` uzantısıyla kaydedildi (`.doc` değil) mi?

## Kenar durumları ve yaygın varyasyonlar

| Durum | Önerilen ayarlama |
|-----------|------------------------|
| Farklı bir düğme boyutuna ihtiyacınız var | Genişlik ve yükseklik argümanlarını `InsertForms2OleControl` içinde değiştirin. |
| Düğmeyi belirli bir sayfada istiyorsunuz | Sayfalar ekledikten sonra `builder.MoveToDocumentEnd();` kullanın veya kontrolün önüne bir sayfa sonu ekleyin. |
| Aspose.Words olmadan ortamları desteklemeniz gerekiyor | `w:object` öğesini eklemek için Open XML SDK’yı kullanın, ancak kod önemli ölçüde daha karmaşık hâle gelir. |
| Makro‑etkin belge gerekli | `.docm` uzantısıyla kaydedin (`document.Save("MyDoc.docm");`) ve `cmdSubmit_Click` olayını işleyen bir VBA modülü ekleyin. |

## Tam kaynak kodu

Aşağıda, `Program.cs` içine kopyalayıp değişiklik yapmadan (çıkış yolu dışında) çalıştırabileceğiniz tam, bağımsız program yer almaktadır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Konsolda beklenen çıktı

```
Document saved to C:\Temp\CommandButton.docx
```

Word’de dosyayı açtığınızda **Submit** etiketiyle bir düğme görüntülenir. Düğmeye tıkladığınızda, varsayılan ActiveX davranışı (makro ekli olmadığını belirten bir ileti kutusu) tetiklenir.

## Sonuç

Bu öğreticide **docx nasıl kaydedilir** sorusunu, **ActiveX kontrolü** gömerek, özellikle **add activex button** işleviyle bir komut düğmesi ekleyerek yanıtladık. Artık **programatik olarak Word belgesi oluşturma**, düğme özelliklerini yapılandırma ve dosyayı son kullanıcı etkileşimi için kalıcı hâle getirme konusunda bilgi sahibisiniz.

Bundan sonra şunları keşfedebilirsiniz:

* `cmdSubmit_Click` olayını işleyen VBA makroları ekleme.  
* Onay kutuları veya açılır kutular gibi diğer ActiveX kontrollerini ekleme.  
* Çok sayfalı belgeler oluşturup birden fazla etkileşimli öğe yerleştirme.  

Farklı kontrol türleri ve yerleşim seçenekleriyle deneyler yaparak, iş süreçlerinizi kolaylaştıran zengin, etkileşimli Word şablonları oluşturun.


## Sonraki Öğrenmeniz Gereken Konular

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece ek API özelliklerini hâkim olmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz sağlanır.

- [Aspose.Words – docx'i txt olarak kaydetme ve Word denklemlerini LaTeX olarak dışa aktarma – Tam Kılavuz](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [docx kurtarma – Bozuk Word dosyaları için C# rehberi](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [Word'ü Markdown olarak kaydetme – Tam C# Rehberi](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}