---
category: general
date: 2026-08-07
description: Aspose.Words for .NET kullanarak dipnot ayırıcıyı alın. Dipnot ve sonnot
  ayırıcılarını nasıl çıkaracağınızı, düğüm türlerini nasıl inceleyeceğinizi ve C#'ta
  nasıl değiştireceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: tr
lastmod: 2026-08-07
og_description: Aspose.Words for .NET ile dipnot ayırıcıyı alın. Bu kılavuz, dipnot
  ve sonnot ayırıcılarını nasıl çıkaracağınızı, düğüm türlerini nasıl kontrol edeceğinizi
  ve değişiklikleri nasıl kaydedeceğinizi gösterir.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: C#'de dipnot ayırıcıyı al – adım adım Aspose.Words öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: C#'de dipnot ayırıcıyı al – eksiksiz Aspose.Words rehberi
url: /tr/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta dipnot ayırıcıyı alın – eksiksiz Aspose.Words rehberi

Bir Word belgesinden **dipnot ayırıcıyı almak** istiyorsanız, bu öğretici Aspose.Words for .NET ile bunu nasıl yapacağınızı tam olarak gösterir. Belge‑işleme hizmeti oluşturuyor ya da dipnot biçimlendirmesini temizliyorsanız, hem dipnot hem de sonnot ayırıcılarını çıkaran tam, çalıştırılabilir bir örnek göreceksiniz.

Bu rehberde bir `.docx` dosyasını nasıl yükleyeceğinizi, `FootnoteSeparator` ve `EndnoteSeparator` özelliklerini nasıl çağıracağınızı, döndürülen `Node` nesnelerini nasıl inceleyeceğinizi ve isteğe bağlı olarak ayırıcı satırını nasıl değiştireceğinizi öğreneceksiniz. Harici bir dokümantasyona gerek yok—gereken her şey aşağıda yer alıyor.

## Önkoşullar

* .NET 6.0 veya daha yeni (kod .NET Framework 4.7.2'de de çalışır)
* Aspose.Words for .NET NuGet paketi (sürüm 24.9 veya daha yeni)
* Dipnot ve/veya sonnot içeren bir Word belgesi (ör. `Footnotes.docx`)

Aspose.Words paketini aşağıdaki CLI komutuyla ekleyebilirsiniz:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

Yeni bir konsol projesi oluşturun veya kodu mevcut bir projeye ekleyin. Gerekli `using` yönergeleri aşağıda listelenmiştir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Bu ad alanları, **dipnot ayırıcıyı almak** işlemleri için gereken `Document` sınıfına, `Node` hiyerarşisine ve `NodeType` enumarasyonuna erişim sağlar.

## Adım 2: Dipnot ve sonnot içeren belgeyi yükleyin

Herhangi bir Aspose.Words iş akışındaki ilk işlem, kaynak dosyayı yüklemektir. Yer tutucu yolu, `.docx` dosyanızın gerçek konumuyla değiştirin.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Dosyanın yüklenmesi, iç node ağacını hazırlar; bu, ayırıcı node'ları bu ağacın içinde bulunduğu için **dipnot ayırıcıyı almak** açısından önemlidir.

## Adım 3: Dipnot ayırıcı node'unu alın

Artık `Document` nesnesinin `FootnoteSeparator` özelliğine erişerek **dipnot ayırıcıyı alabilirsiniz**. Bu node, dipnotları ana metinden ayıran satırı temsil eder.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

`NodeType`, standart bir ayırıcı satırı için `Paragraph` olacaktır. Node tipini bilmek, ayırıcıyı değiştirmeniz mi yoksa tamamen değiştirmeniz mi gerektiğine karar vermenize yardımcı olur.

## Adım 4: Sonnot ayırıcı node'unu alın

Benzer şekilde, `EndnoteSeparator` özelliğini kullanarak **sonnot ayırıcıyı alabilirsiniz**. Bu node, sonnotları ana içerikten ayırır.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Her iki ayırıcı node da çoğu belgede aynı `NodeType` (`Paragraph`) değerini paylaşır, ancak bağımsız olarak özelleştirilebilirler.

## Adım 5: Ayırıcı içeriğini inceleyin veya değiştirin (isteğe bağlı)

Ayırıcıyı görsel olarak değiştirmek isterseniz—örneğin bir tire satırını ince bir çizgiyle değiştirmek gibi—`Paragraph` node'unu doğrudan düzenleyebilirsiniz. Aşağıda, varsayılan ayırıcı metnini özel bir dizeyle değiştiren bir örnek bulunmaktadır.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Node'ları düzenledikten sonra, değişikliklerin Word'te yansıtıldığını görmek için belgeyi kaydedebilirsiniz.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Beklenen konsol çıktısı

Programı orijinal `Footnotes.docx` ile çalıştırdığınızda, aşağıdakine benzer bir çıktı görmelisiniz:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

`Footnotes_Updated.docx` dosyasını Microsoft Word'de açarsanız, dipnot ve sonnot ayırıcıları eklediğiniz özel metni gösterecektir.

## Yaygın sorular ve uç durumlar

**Belgede dipnot yoksa ne olur?**  
`FootnoteSeparator` özelliği, Word her zaman bir ayırıcı yer tutucu eklediği için yine bir `Paragraph` node'u döndürür. Node boş olacaktır, bu yüzden güvenle içerik ekleyebilir veya olduğu gibi bırakabilirsiniz.

**Belirli bir bölüm için ayırıcıyı alabilir miyim?**  
Dipnot ve sonnot ayırıcıları belge-genelindedir, bölüm-spesifik değildir. Bölüm düzeyinde kontrol gerekiyorsa, global ayırıcı node'ları yerine `Section.FootnoteOptions` ve `Section.EndnoteOptions` ile çalışmalısınız.

**Bu .NET Core ile çalışır mı?**  
Evet. Aspose.Words for .NET çapraz-platformdur ve aynı kod Windows, Linux ve macOS'ta .NET 6+ ile çalışır.

**Hangi node tipini beklemeliyim?**  
`FootnoteSeparator` ve `EndnoteSeparator` her ikisi de bir `Paragraph` node'u (`NodeType.Paragraph`) döndürür. Farklı bir tip ile karşılaşırsanız, belge bozulmuş olabilir ve kaynak dosyayı yeniden yüklemeli veya doğrulamalısınız.

## Hızlı kopyala‑yapıştır için tam kaynak kodu

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Kodu bir `Program.cs` dosyasına kopyalayın, dosya yollarını ayarlayın ve `dotnet run` komutunu çalıştırın. Program, belgeyi yüklemekten değişiklikleri kalıcı hale getirmeye kadar tam **dipnot ayırıcıyı alma** iş akışını gösterir.

## Sonuç

Artık Aspose.Words for .NET kullanarak **dipnot ayırıcıyı alma** ve **sonnot ayırıcıyı alma** işlemlerini nasıl yapacağınızı, `document node type`'larını nasıl inceleyeceğinizi ve isteğe bağlı olarak içeriklerini nasıl değiştireceğinizi biliyorsunuz. Bu teknik, dipnot biçimlendirmesini otomatikleştirmenize, özel ayırıcı satırları oluşturmanıza veya herhangi bir C# uygulamasında belge yapısını doğrulamanıza olanak tanır.

Sonraki adımda, bireysel dipnot metinleri için **C# dipnot çıkarımı** gibi ilgili konuları keşfedebilir veya `FootnoteOptions` kullanarak **dipnot referans işaretlerini değiştirmeyi** öğrenebilirsiniz. Her iki kavram da burada ele alınan node‑ağacı temelleri üzerine doğrudan inşa edilir.

Kodlamaktan keyif alın ve projenizin markasına uygun farklı ayırıcı stillerini denemekten çekinmeyin!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen teknikler üzerine inşa edilen yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalarla birlikte tam çalışan kod örnekleri içerir.

- [Ayaknot ve Sonnot ile Kelime İşleme](/words/english/net/working-with-footnote-and-endnote/)
- [Aspose.Words for .NET'te Document Builder Kullanarak İçerik Ekleme](/words/english/net/add-content-using-document-builder/)
- [Ayaknot ve Sonnot ile Çalışma](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}