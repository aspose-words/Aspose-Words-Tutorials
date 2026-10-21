---
category: general
date: 2026-10-13
description: Aspose.Words kullanarak bir komut düğmesini programlı olarak nasıl ekleyeceğinizi
  öğrenin. Bu kılavuz ayrıca tam C# kodu ile bir Word belgesi düğmesi oluşturmayı
  gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: tr
lastmod: 2026-10-13
og_description: Aspose.Words kullanarak bir Word belgesine programlı olarak komut
  düğmesi ekleyin. C# ile bir Word belgesi düğmesi oluşturmak için bu kapsamlı öğreticiyi
  izleyin.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Word belgesine programlı olarak bir komut düğmesi ekleyin – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Word belgesine programlı olarak bir komut düğmesi nasıl eklenir
url: /tr/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word belgesine programlı olarak bir komut düğmesi ekleme  

Eğer **komut düğmesini programlı olarak eklemeniz** gerekiyorsa, Aspose.Words .docx dosyasına doğrudan OLE form kontrolleri yerleştirmenizi sağlayan temiz bir API sunar. Bu öğretici, belge Microsoft Word’de açıldığında normal bir form düğmesi gibi davranan bir **Word belgesi düğmesi** oluşturmak için gereken tüm adımları size gösterir.  

Geliştirme ortamını nasıl kuracağınızı, düğmeyi nasıl ekleyeceğinizi, özelliklerini nasıl yapılandıracağınızı ve sonucu nasıl doğrulayacağınızı öğreneceksiniz. Harici bir araç gerektirmez—sadece bir .NET projesi ve Aspose.Words for .NET kütüphanesi yeterlidir.  

## Önkoşullar  

Başlamadan önce şunların yüklü olduğundan emin olun:  

* .NET 6.0 SDK veya daha yeni bir sürüm yüklü.  
* Aspose.Words for .NET’in güncel bir sürümü (örneklerde 23.12 kullanılmıştır, ancak 22.x+ herhangi bir sürüm de çalışır).  
* Visual Studio 2022 veya Visual Studio Code gibi bir IDE.  

Kod, Aspose.Words platform bağımsız olduğu için Windows, macOS ve Linux üzerinde çalışır.  

## Adım 1: Projeyi kurun ve Aspose.Words referansını ekleyin  

1. Yeni bir konsol projesi oluşturun:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Aspose.Words NuGet paketini ekleyin:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. **Program.cs** dosyasını açın ve içeriğini sonraki adımlarda gösterilen iskeletle değiştirin.  

Projeyi bu şekilde kurmak, form kontrolleri için gerekli olan `Aspose.Words` ve `Aspose.Words.Drawing.Forms` ad alanlarının derleyici tarafından bulunmasını sağlar.  

## Adım 2: Boş bir belge ve DocumentBuilder başlatma  

`Document` sınıfı tüm Word dosyasını temsil ederken, `DocumentBuilder` içerik eklemek için akıcı bir API sağlar.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Bu adım neden önemlidir* – `DocumentBuilder` olmadan düğmeyi sayfada tam olarak konumlandıramazsınız. Builder aynı zamanda mevcut imleç konumunu dikkate alır, böylece daha sonra birden fazla kontrol eklemek kolaylaşır.  

## Adım 3: Komut düğmesi OLE kontrolünü ekleme  

Aspose.Words, bir komut düğmesini `ControlType.CommandButton` türünde bir OLE kontrolü olarak ele alır. Konum ve boyutunu, puan cinsinden ölçülen bir `RectangleF` ile tanımlarsınız (1 puan = 1/72 inç).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Temel noktalar**  

* Dikdörtgenin başlangıç noktası (X, Y) sayfanın sol‑üst köşesine göre görecelidir.  
* `Width` veya `Height` değerini değiştirmek, düğmenin görsel boyutunu değiştirir.  
* `InsertForms2OleControl` bir `Forms2OleControl` nesnesi döndürür; bu nesneyi daha sonra yapılandırabilirsiniz.  

## Adım 4: Düğmenin adını ve başlığını yapılandırma  

**Ad**, Word’ün makro motoru tarafından kontrolü tanımlamak için kullanılır, **başlık** ise kullanıcının gördüğü metindir.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

VBA makroları eklemeyi planlıyorsanız, Word’ün makro kaydedicisinin bu özelliği referans alması nedeniyle açıklayıcı bir ad kullanın.  

## Adım 5: (İsteğe Bağlı) Belgeyi kaydetme ve sonucu doğrulama  

Dosyayı kaydetmek, Microsoft Word’de açıp düğmenin görünüp çalıştığını onaylamanızı sağlar.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

*CommandButtonDemo.docx* dosyasını Word’de açtığınızda, sol kenar boşluğundan yaklaşık 1.4 inç, sayfanın üstünden ise 2.1 inç uzaklıkta **Submit** adlı bir düğme görmelisiniz. Varsayılan olarak düğmeye tıklamak bir şey yapmaz çünkü hiçbir makro eklenmemiştir, ancak görsel kontrol tamamen işlevseldir.  

## Adım 6: Kenar durumları ve yaygın tuzaklar  

| Durum | Dikkat edilmesi gereken | Önerilen çözüm |
|-----------|-------------------|-----------------|
| **Düğme mevcut metnin üzerine geliyor** | Dikdörtgen bir paragrafla kesişebilir ve düzen sorunlarına yol açar. | `builder.Writeln()` çağırdıktan sonra düğmeyi ekleyerek imleci yeni bir satıra taşıyın veya `Y` koordinatını ayarlayın. |
| **Belge bir uyarı ile açılıyor** | Bazı Word sürümleri, bağlı bir programı olmayan OLE kontrollerini işaretler. | Kontrol türünün `CommandButton` olduğundan emin olun; Word bunu standart bir form öğesi olarak görür ve harici bir programa ihtiyaç duymaz. |
| **Linux’da başsız ortamda çalıştırma** | UI’yı test etmek için Word başlatılamaz, ancak dosya geçerlidir. | Kontrolün özelliklerini (`commandButton.Name`, `commandButton.Caption`) okuyan bir birim testi kullanarak doğru ayarlandığını doğrulayın. |
| **Birden fazla düğme gerekiyor** | Aynı `DocumentBuilder` imleci hareket ettirilmeden tekrar kullanılırsa düğme bir öncekinin üzerine eklenir. | Her eklemeden önce `builder.MoveToDocumentEnd()` çağırın veya dikdörtgenin `Y` değerini ayarlayın. |

Bu kenar durumlarını erken ele almak, çözümü onlarca kontrol içeren tam formlara ölçeklendirirken zaman kazandırır.  

## Adım 7: Tam, çalıştırılabilir örnek  

Aşağıda, NuGet geri yüklemesi dışında hiçbir değişiklik yapmadan kopyalayıp çalıştırabileceğiniz bağımsız bir program yer almaktadır.  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Beklenen çıktı**  

Programı çalıştırdığınızda aşağıdaki gibi bir yol yazdırır:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Oluşturulan *CommandButtonDemo.docx* dosyasını açtığınızda, kodda tanımlanan koordinatlarda tek bir **Submit** düğmesi görülür. Ek bir UI öğesi bulunmaz; bu da **komut düğmesini programlı olarak ekleme** iş akışının başarılı olduğunu gösterir.  

## Sonuç  

Artık Aspose.Words kullanarak bir Word belgesine **komut düğmesini programlı olarak eklemeyi** biliyorsunuz ve daha sonra VBA makroları veya dış otomasyon araçlarıyla bağlanabilecek bir **Word belgesi düğmesi** oluşturmanın temellerini anladınız. Süreç, bir belge başlatmayı, OLE `CommandButton` kontrolünü eklemeyi, özelliklerini yapılandırmayı ve dosyayı kaydetmeyi içerir.  

Bundan sonra şunları yapabilirsiniz:  

* Farklı `ControlType` değerleriyle adım 3’ü tekrarlayarak daha fazla kontrol (onay kutuları, metin alanları) ekleyin.  
* Düğmeye VBA makroları ekleyerek form kaydetme veya e‑posta gönderme gibi işlemler gerçekleştirin.  
* Alan tanımlarının veri‑tabanlı bir koleksiyonu üzerinde döngü kurarak tüm formları dinamik olarak oluşturun.  

Dikdörtgen koordinatları ve düğme başlığını UI tasarımınıza göre ayarlamayı deneyin. Kodlamanın tadını çıkarın!  


## Sonraki Öğrenmeniz Gerekenler?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for .NET ile Word Belgesine Bir Combo Box Form Alanı Ekleme](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words for .NET ile Word Belgesine Bir Check Box Form Alanı Ekleme](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Aspose.Words ile Boş Word Belgesi Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}