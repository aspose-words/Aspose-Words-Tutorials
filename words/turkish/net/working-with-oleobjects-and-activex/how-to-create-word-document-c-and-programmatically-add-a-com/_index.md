---
category: general
date: 2026-09-11
description: Aspose.Words kullanarak birkaç basit adımda C# ile Word belgesi oluşturmayı
  ve programlı olarak bir komut düğmesi eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: tr
lastmod: 2026-09-11
og_description: C# ile Word belgesi oluşturun ve programlı olarak Aspose.Words kullanarak
  bir komut düğmesi ekleyin. Çalışan bir çözüm için bu kapsamlı rehberi izleyin.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Word belgesi oluştur C# – komut düğmesini programlı olarak ekle
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: C# ile Word belgesi nasıl oluşturulur ve programlı olarak bir komut düğmesi
  eklenir
url: /tr/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create word document c# and programmatically add a command button

Eğer **create word document c#** yapmanız ve etkileşimli bir düğme eklemeniz gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Aspose.Words kullanarak sadece birkaç satır kodla programlı bir şekilde bir komut düğmesi ekleyebilir, Word’de manuel UI çalışmasına gerek kalmaz.

Bu öğreticide şunları öğreneceksiniz:

* C# ile boş bir Word dosyası başlatma.
* Bir ActiveX **CommandButton** kontrolü ekleme.
* Düğmenin adı ve başlığı gibi özelliklerini ayarlama.
* Belgeyi kaydedip, dosya Microsoft Word’de açıldığında düğmenin görünmesini sağlama.

Aspose.Words for .NET kütüphanesi dışındaki hiçbir harici araç gerekmez ve adımlar .NET 6+ ya da .NET Framework 4.6.2 ve üzeri sürümlerle çalışır.

## Prerequisites

Başlamadan önce şunların olduğundan emin olun:

| Requirement | Reason |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | C# projesi için çalışma zamanını sağlar. |
| Visual Studio 2022 (or any C# IDE) | Kodu yazmayı, derlemeyi ve çalıştırmayı kolaylaştırır. |
| Aspose.Words for .NET NuGet package | Örnekte kullanılan `Document`, `DocumentBuilder` ve `Forms2OleControl` sınıflarını sağlar. |
| Basic knowledge of C# syntax | Ek bir öğrenme eğrisi olmadan kodu takip etmenizi sağlar. |

Aspose.Words paketini NuGet konsolundan şu şekilde ekleyebilirsiniz:

```powershell
Install-Package Aspose.Words
```

## Step 1: Set up a new C# console project

Word dosyasını oluşturacak bir konsol uygulaması oluşturun. Bir terminal açın ve şu komutu çalıştırın:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Oluşturulan `Program.cs` dosyası sonraki adımlarda gösterilen kodu barındıracaktır.

## Step 2: Create a blank document and a DocumentBuilder

İlk işlem, boş bir `.docx` dosyasını temsil eden bir `Document` nesnesi ve belgenin içeriğini düzenlemenizi sağlayan bir `DocumentBuilder` örneği oluşturmaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`Document` tüm Word öğelerinin (paragraflar, tablolar, kontroller) konteyneridir. `DocumentBuilder` ise düşük seviyeli düğüm koleksiyonlarıyla uğraşmadan mevcut imleç konumuna nesneler eklemenizi sağlayan akıcı bir API sunar.

## Step 3: Insert an ActiveX CommandButton control

Aspose.Words, `InsertForms2OleControl` yöntemi aracılığıyla eski tip ActiveX kontrollerinin eklenmesini destekler. Yöntem, kontrol tipini ve istenen boyutu (point cinsinden) alır.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**What happens under the hood:**  
Word, bir ActiveX kontrolünü OLE (Object Linking and Embedding) nesnesi olarak değerlendirir. `Forms2OleControl` sınıfı OLE verisini sarar ve `Name` ve `Caption` gibi özellikleri ortaya çıkarır.

## Step 4: Configure the button’s name and caption

Kontrol yerleştirildikten sonra çalışma zamanı özelliklerini özelleştirebilirsiniz. Anlamlı bir `Name` ayarlamak, düğmeyi daha sonra tanımlamanıza yardımcı olur; `Caption` ise düğmede gösterilecek metni belirler.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Pro tip:**  
Düğmenin tıklama olayını VBA ile ele almayı planlıyorsanız, `Name` başvurduğunuz makro adı haline gelir; ör. `Sub btnSubmit_Click()`.

## Step 5: Save the document to disk

Son olarak belgeyi bir `.docx` dosyasına yazın. Yazma izniniz olan bir klasör seçin; örnek, proje çıktısı dizinine çözümlenen bir göreli yol kullanır.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Programı çalıştırdığınızda `CommandButton.docx` oluşturulur. Dosyayı Microsoft Word’de açtığınızda tıklanabilir bir **Submit** düğmesi görünür:

![Word document with a Submit command button](/images/command-button.png "C# ile oluşturulmuş Submit komut düğmesi içeren bir Word belgesinin ekran görüntüsü")

*Image alt text (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## Verifying the result

1. Word’u başlatın ve `CommandButton.docx` dosyasını açın.  
2. Belge gövdesinde **Submit** etiketiyle bir düğme görmelisiniz.  
3. Düğmenin üzerine geldiğinizde **Properties** bölmesinde (Developer sekmesi → Properties) `btnSubmit` adını göreceksiniz.  

Düğme görünmüyorsa, Word’de **Developer** sekmesinin etkin olduğundan emin olun (File → Options → Customize Ribbon → *Developer* işaretleyin). Developer sekmesi devre dışı olduğunda ActiveX kontrolleri gizlenir.

## Handling common variations and edge cases

| Situation | Recommended adjustment |
|-----------|------------------------|
| **Different button size** | `InsertForms2OleControl` içindeki genişlik ve yükseklik argümanlarını değiştirin. Örneğin, `150, 40` daha büyük bir düğme oluşturur. |
| **Multiple buttons** | `InsertForms2OleControl` metodunu tekrar tekrar çağırın, çağrılar arasında builder’ın imlecini hareket ettirin (`builder.Writeln();`). |
| **Button without ActiveX** | Eski Word sürümlerinde ActiveX engellendiğinde uyumluluk için `InsertFormField` kullanarak bir eski form alanı (ör. onay kutusu) ekleyin. |
| **Cross‑platform usage** | ActiveX kontrolleri yalnızca Windows Word sürümlerinde çalışır. Mac ya da web‑tabanlı görüntüleyiciler için düğme görünümü veren bir hiperlink eklemeyi düşünün. |
| **Security warnings** | ActiveX içeren bir belgeyi açtığınızda Word bir güvenlik uyarısı gösterebilir. Güvenilir bir sertifika ile belgeyi imzalamak bu sürtünmeyi azaltır. |

## Full, runnable example

Aşağıda `Program.cs` içine kopyalayıp yapıştırabileceğiniz tam program yer almaktadır. Aspose.Words NuGet paketini ekledikten sonra değişiklik yapmadan derlenip çalıştırılabilir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output in the console:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Oluşturulan dosyayı açtığınızda **Submit** düğmesi etkileşim için hazırdır.

## Conclusion

Artık **create word document c#** ve Aspose.Words kullanarak **programmatically add command button** kontrollerini nasıl ekleyeceğinizi biliyorsunuz. Süreç, bir `Document` başlatmak, bir `Forms2OleControl` eklemek, özelliklerini yapılandırmak ve dosyayı kaydetmekten ibarettir. Bundan sonra şunları yapabilirsiniz:

* `ControlType` değerini değiştirerek daha fazla kontrol (ör. onay kutuları, metin alanları) ekleyin.  
* Düğmeye özel mantık eklemek için VBA makroları bağlayın.  
* Bu tekniği mail merge veya şablon doldurma gibi diğer Aspose.Words özellikleriyle birleştirin.

Farklı boyutlar, başlıklar ve çoklu düğmelerle deneyler yaparak otomasyon senaryonuza en uygun çözümü bulun. İyi kodlamalar!

## What Should You Learn Next?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece API özelliklerini daha iyi öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}