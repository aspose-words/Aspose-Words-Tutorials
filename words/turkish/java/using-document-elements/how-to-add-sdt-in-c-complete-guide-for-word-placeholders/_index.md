---
category: general
date: 2026-08-14
description: Aspose.Words ile SDT'yi hızlıca nasıl eklenir. Word yer tutucusunu oluşturmayı
  ve bir .docx dosyasına düz metin kontrolü eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: tr
lastmod: 2026-08-14
og_description: Aspose.Words kullanarak C#'de SDT nasıl eklenir. Dinamik belgeler
  için kelime yer tutucusu oluşturmak ve düz metin kontrolü eklemek için bu öğreticiyi
  izleyin.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: C#'de SDT nasıl eklenir – adım adım Word yer tutucu rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: C#'da SDT Nasıl Eklenir – Word Yer Tutucuları için Eksiksiz Rehber
url: /tr/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta SDT Nasıl Eklenir – Word Yer Tutucuları İçin Tam Kılavuz

Bir Word dosyasına **how to add sdt** eklemeniz gerekiyorsa, bu öğretici Aspose.Words for .NET kullanarak tam adımları gösterir. Kılavuzun sonunda, son kullanıcıların belgeye doğrudan yazmasını sağlayan **create word placeholder** etiketlerini oluşturabilecek ve **insert plain text control** işlemini güvenilir bir şekilde nasıl yapacağınızı anlayacaksınız.

Structured Document Tags (SDT'ler) ile çalışmak, manuel form alanlarına olan ihtiyacı ortadan kaldırır ve dinamik sözleşmeler, raporlar veya mektuplar oluşturmak için temiz, programatik bir yol sunar. Aşağıdaki örnek, proje kurulumundan son .docx dosyasının kaydedilmesine kadar her şeyi kapsar, böylece kodu kendi çözümünüze eksiksiz bir şekilde kopyalayıp yapıştırabilirsiniz.

## Önkoşullar

- .NET 6.0 veya daha yeni (kod .NET Framework 4.6+ ile de çalışır)
- Visual Studio 2022 veya tercih ettiğiniz herhangi bir C# IDE'si
- Aspose.Words for .NET lisansı (test için ücretsiz geçici bir lisans yeterlidir)
- C# sözdizimi ve SDT kavramına temel aşinalık

> **Pro tip:** Oluşturulan belgeleri dağıtmayı planlıyorsanız, değerlendirme filigranını önlemek için bir lisans dosyası ekleyin.

## Adım 1: Projeyi kurun ve Aspose.Words'ü içe aktarın

Yeni bir konsol uygulaması oluşturun ve Aspose.Words NuGet paketini ekleyin:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Bu `using` yönergeleri, **insert plain text control** işlemleri için gerekli olan `Document`, `DocumentBuilder` ve `StructuredDocumentTag` sınıflarına erişim sağlar.

## Adım 2: Belgeyi ve builder'ı başlatın

İlk kod bloğu boş bir Word belgesi ve içine içerik yazmanıza olanak tanıyan bir `DocumentBuilder` oluşturur.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` bir imleç gibi çalışır; sonraki her çağrı içeriği mevcut konuma ekler. Belgeyi başlatmak, **how to add sdt** senaryolarının temeli olur çünkü SDT, canlı bir `Document` örneğine ait olmalıdır.

## Adım 3: Düz metin Structured Document Tag (SDT) ekleyin

Şimdi, bir kullanıcının ad, tarih veya herhangi bir özel değer yazabileceği bir yer tutucu olarak **insert plain text control** ekliyoruz.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText`, Aspose.Words'e basit bir metin alanı oluşturmasını söyler.
- `SdtAppearanceTags.Default`, etikete standart Word görsel stilini verir (belge Word'de açıldığında gölgeli bir kutu).

## Adım 4: SDT'yi bir başlık ve yer tutucu metinle yapılandırın

İyi adlandırılmış bir SDT, belgeyi son kullanıcılar için kendini açıklayıcı hâle getirir. Burada **create word placeholder** meta verisini oluşturuyor ve alan içinde görünen ipucunu ayarlıyoruz.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title`, değeri programlı olarak çıkartırken veya güncellerken daha sonra kullanabileceğiniz iç tanımlayıcıdır.
- `PlaceholderName`, Word'de gösterilen gri ipucu olup, kullanıcıya ne yazması gerektiğini bildirir.

## Adım 5: Çevresel içeriği ekleyin

Bir belge nadiren tek bir SDT'den oluşur. Genellikle yer tutucunun öncesinde ve sonrasında normal paragraflara ihtiyaç duyarsınız. Statik metin eklemek için builder'ın `WriteLine` metodunu kullanın.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

`InsertNode` çağrısı, önceden oluşturulan SDT'yi tam olarak ihtiyacınız olan yere yerleştirir ve çevresindeki metin akışını korur.

## Adım 6: Belgeyi bir .docx dosyasına kaydedin

Son olarak, belgeyi diske kalıcı olarak kaydedin. Yol, proje klasörüne göre mutlak ya da göreli olabilir.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`SDT.docx` dosyasını Microsoft Word'de açtığınızda, **Enter name here** yazan gri bir yer tutucu görünür. Kullanıcılar alana tıklayıp bir değer yazabilir ve belge tekrar kaydedildiğinde bu değer korunur.

## Tam, çalıştırılabilir örnek

Tüm parçaları bir araya getirerek anında çalıştırabileceğiniz bağımsız bir program elde edersiniz:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Programı çalıştırdığınızda **Beklenen çıktı**:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Oluşturulan `SDT.docx` dosyasını açtığınızda şunlar görülür:

```
Dear [Enter name here],
After the SDT
```

Köşeli parantez içindeki metin, kullanıcıların değiştirebileceği **insert plain text control** yer tutucusudur.

## Yaygın varyasyonlar ve uç durumlar

| Durum | Kodu nasıl uyarlarsınız |
|-----------|-----------------------|
| **Birden fazla yer tutucu** | `InsertStructuredDocumentTag` metodunu tekrarlayarak çağırın ve her etikete benzersiz bir `Title` verin. |
| **Rich‑text SDT** | `PlainText` yerine `StructuredDocumentTagType.RichText` kullanın. |
| **Yer tutucuyu kilitle** | Kullanıcıların alanı silmesini önlemek için `plainTextTag.LockContentControl = true;` ayarlayın. |
| **Değerle ön‑doldur** | Kaydetmeden önce `plainTextTag.Text = "John Doe";` atayın. |
| **Koşullu görünüm** | Onay kutusu kontrolü için `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` kullanın. |

Bu varyasyonlar, neredeyse her form benzeri senaryoya uyan **create word placeholder** yapıları oluşturmanıza olanak tanır.

## Sorun giderme ipuçları

- **Placeholder not visible** – Dosyayı Microsoft Word (veya uyumlu bir görüntüleyici) içinde açtığınızdan emin olun. Bazı hafif editörler SDT'leri gizler.
- **License warning** – Değerlendirme filigranı görürseniz, lisans dosyanızın doğru yüklendiğini doğrulayın (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Bir SDT ekledikten sonra, builder'ın imleci etiketin *sonunda* kalır. Metni *etiket içinde* eklemeniz gerekiyorsa, yazmadan önce `builder.MoveTo(plainTextTag);` kullanın.

## Sonuç

Artık Aspose.Words for .NET kullanarak bir Word belgesine **how to add sdt** eklemeyi, **create word placeholder** etiketlerini oluşturmayı ve kullanıcıların Word içinde doğrudan düzenleyebileceği **insert plain text control** eklemeyi biliyorsunuz. Tam örnek, başlatmayı, etiket eklemeyi, yapılandırmayı, çevresel içeriği ve kaydetmeyi tek bir çalıştırılabilir programda gösterir.

Sonra, **insert rich text control**, **populate SDTs from a database** veya **convert the final document to PDF** gibi ilgili konuları keşfedin. Bunların tümü burada ele alınan aynı temeller üzerine kuruludur, böylece otomasyon hattınızı güvenle genişletebilirsiniz.

Kodlamaktan keyif alın ve belge otomasyon ihtiyaçlarınıza uygun farklı SDT türleriyle denemeler yapmaktan çekinmeyin!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java kullanarak Salt Okunur Belgelerde Düzenlenebilir Aralıklar Oluşturma](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Aspose.Words for Java ile Word Yer İmleri Ekleme – Ekle, Güncelle, Sil](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}