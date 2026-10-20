---
category: general
date: 2026-07-19
description: Aspose.Words C# kullanarak Word belgesi oluşturun ve ActiveX komut düğmesi
  eklemeyi, düğme boyutunu ayarlamayı ve düğmeyi programlı olarak eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: tr
lastmod: 2026-07-19
og_description: Aspose.Words C# ile Word belgesi oluşturun ve saniyeler içinde bir
  ActiveX komut düğmesi gömün. Düğme boyutunu ayarlamak ve düğmeyi kolayca eklemek
  için adım adım kılavuzu izleyin.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: ActiveX Düğmesiyle Word Belgesi Oluşturma – C# Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: ActiveX Düğmesiyle Word Belgesi Oluşturma – C# Rehberi
url: /tr/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ActiveX Düğmesiyle Word Belgesi Oluşturma – Tam C# Rehberi

Hiç **create word document** içeren işlevsel bir ActiveX düğmesinin nasıl oluşturulacağını merak ettiniz mi? Belki bir raporu otomatikleştiriyorsunuz ve dosyanın içinde tıklanabilir bir “Onayla” kontrolüne ihtiyacınız var. Bu öğreticide tam olarak bunu adım adım göstereceğiz—Aspose.Words for .NET kullanarak bir ActiveX komut düğmesi eklemek, boyutunu ayarlamak ve ihtiyacınız olan yere yerleştirmek.  

Eğer *how to add activex* kontrollerini Word'ü manuel olarak açmadan eklemeyi hiç düşündüyseniz, doğru yerdesiniz. Sonunda çalıştırılabilir bir örnek, her adımın net açıklaması ve yaygın sorunlarla başa çıkma ipuçlarına sahip olacaksınız.

## Öğrenecekleriniz

- C# projesinde Aspose.Words nasıl kurulur  
- ActiveX komut düğmesi gömülü **create word document** için tam kod  
- **set button size** nasıl yapılır ve başlığı ile adını özelleştirme yolları  
- Belgedeki herhangi bir konuma **insert command button** ve **how to insert button** yönteminin doğru kullanımı  
- Köşe durumları (Word sürümü, platform sınırlamaları, güvenlik uyarıları) dikkate alınması

### Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework 4.7+ üzerinde de çalışır).  
- Geçerli bir Aspose.Words for .NET lisansı (veya ücretsiz deneme anahtarı).  
- Visual Studio 2022 (veya tercih ettiğiniz herhangi bir IDE).  
- C# ve nesne yönelimli programlamaya temel aşinalık.

Başka üçüncü taraf kütüphane gerekmez.

---

## Adım 1: Word Belgesi Oluşturma – Proje Kurulumu

**insert command button** yapmadan önce, üzerinde çalışabileceğimiz boş bir Word dosyasına ihtiyacımız var. Bu adım ayrıca Aspose.Words kullanarak klasik “create word document” desenini gösterir.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Neden önemli:** `Document` tüm .docx dosyasını temsil eder, `DocumentBuilder` ise mevcut imleç konumunu izler. Sonraki tüm eklemeler (ActiveX kontrolümüz dahil) bu builder'a göre yapılır.

---

## Adım 2: ActiveX Nasıl Eklenir – CommandButton Kontrolünü Oluşturma

Belge artık mevcut olduğuna göre, **how to add activex** kısmını ele alalım. Aspose.Words, ActiveX nesneleri için `Forms2OleControl` sınıfını sunar. Burada bir komut düğmesi oluşturacağız ve özelliklerini yapılandıracağız, **set button size** gereksinimi de dahil.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro ipucu:** Boyut noktalarla ölçülür (1 nokta = 1/72 inç). Değerleri düzenlemenize göre ayarlayın; tipik bir araç çubuğu düğmesi için 120 × 30 iyi çalışır.

---

## Adım 3: Komut Düğmesi Ekleme – **Insert Command Button**'ın Özeti

Kontrol hazır olduğunda, şimdi **insert command button**'ı belgenin builder'ın mevcut konumuna ekliyoruz. Bu yöntemi çağırmadan önce builder'ı istediğiniz yere (ör. bir paragraftan sonra) taşıyabilirsiniz.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Belirli bir yer imine **how to insert button** eklemeniz gerekiyorsa, önce builder'ı taşımanız yeterlidir:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Arka planda ne oluyor?** Aspose.Words gerekli OLE nesne akışlarını .docx paketine yazar, böylece Word ek makrolar olmadan düğmeyi görüntüleyebilir.

---

## Adım 4: Belgeyi Kaydetme – **Create Word Document** Döngüsünü Tamamlama

Son adım basittir: dosyayı diske kaydetmek. Bu, **create word document**'in, ActiveX'in gömülmesinin ve kaydetmenin tam döngüsünü tamamlar.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Oluşan dosyayı Microsoft Word'de (sadece Windows) açın. “Click Me” etiketiyle tıklanabilir bir düğme görmelisiniz. Üzerine tıklamak, CommandButton için varsayılan eylemi tetikler—VBA kodu eklemediğiniz sürece bir şey olmaz, ancak kontrol tamamen işlevseldir.

> **Beklenen çıktı:** Tek sayfalı bir .docx dosyası, ekleme noktasında ortalanmış, 120 × 30 pt boyutunda, “Click Me” başlıklı bir düğme.  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Resim alt metni:* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).  

---

## Adım 5: Kenar Durumları, Güvenlik ve En İyi Uygulamalar

### Platform Sınırlamaları
- ActiveX kontrolleri yalnızca Windows sürümündeki Word'de çalışır. İzleyicileriniz macOS veya Word Online kullanıyorsa, düğme statik bir resim olarak görünecektir.
- Bazı kurumsal ortamlar güvenlik nedeniyle ActiveX'i devre dışı bırakır; belgeyi imzalamanız veya kullanıcıları içeriği etkinleştirmeleri konusunda bilgilendirmeniz gerekebilir.

### VBA Etkileşimi (İsteğe Bağlı)
Düğmenin bir makro çalıştırmasını istiyorsanız, kaydettikten sonra belgeye bir VBA projesi eklemeniz gerekir. Aspose.Words otomatik olarak VBA kodu üretmez, ancak `Document.VbaProject` API'sini kullanarak ekleyebilirsiniz.

### İsim Çakışmaları
Her kontrole benzersiz bir `Name` verin. Aynı ismi tekrar kullanmak, Word kontrolü çözümlemeye çalışırken çalışma zamanı hatalarına yol açabilir.

### Performans İpucu
Birçok kontrol eklerken, tek bir `DocumentBuilder` örneğini yeniden kullanın ve bir döngü içinde `doc.Save` çağrısından kaçının. Eklemeleri toplu yapın ve sonunda bir kez kaydedin.

## Tam Çalışan Örnek

Her şeyi bir araya getirerek, işte tam, kopyala‑yapıştır hazır bir program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Programı çalıştırın, kaydedilen dosyayı açın ve düğmeyi builder'ın konumlandığı yerde tam olarak göreceksiniz.

## Sonuç

Sıfırdan **created word document** yaptık, `Forms2OleControl` yapılandırarak **how to add activex** öğrendik, **set button size** özelliklerini ustalaştık ve dosyanın herhangi bir noktasına **insert command button** ve **how to insert button** eklemenin doğru yolunu gösterdik.  

Tek bir kod örneğiyle artık daha zengin Word otomasyonu için sağlam bir temele sahipsiniz—etkileşimli formlarla şablonlar oluşturuyor, kullanıcı onayı gerektiren sözleşmeler üretiyor ya da bir rapor boyunca birkaç kullanışlı kontrol ekliyor olun.

### Sıradaki Adım?

- **Style the button** – yazı tiplerini, renkleri değiştirin veya bir resim arka planı ekleyin.  
- **Attach VBA macros** – düğmenin hesaplamalar yapmasını veya dış programları başlatmasını sağlayın.  
- **Combine with other controls** – onay kutuları, liste kutuları veya hatta gömülü Excel sayfaları.  

Denemekten çekinmeyin, bir sorunla karşılaşırsanız aşağıya yorum bırakın. Kodlamanın tadını çıkarın ve Aspose.Words ile Word otomasyonunun keyfini çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}