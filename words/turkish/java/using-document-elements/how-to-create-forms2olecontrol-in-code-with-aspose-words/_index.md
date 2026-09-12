---
category: general
date: 2026-09-11
description: Aspose.Words DocumentBuilder kullanarak kodda forms2olecontrol oluşturmayı
  öğrenin. Bu adım adım kılavuz, ActiveX komut düğmesi eklemesini, setOleClassName
  kullanımını ve boyutlandırmayı kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: tr
lastmod: 2026-09-11
og_description: Aspose.Words ile kodda forms2olecontrol oluşturun. Bu kılavuzu izleyerek
  bir ActiveX komut düğmesi ekleyin, sınıf adını ayarlayın ve boyutunu düzenleyin.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Kodda forms2olecontrol oluşturma – tam Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Aspose.Words ile kodda forms2olecontrol nasıl oluşturulur
url: /tr/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile kod içinde forms2olecontrol oluşturma

Kod içinde **forms2olecontrol oluşturmanız** gerekiyorsa, bu kılavuz Aspose.Words .NET API'sini kullanarak bunu tam olarak nasıl yapacağınızı gösterir. AktifX komut düğmesi gerektiren bir şablonu otomatikleştiriyor olun ya da bir Word belgesini programlı olarak zenginleştirmek istiyor olun, aşağıdaki adımlar kontrolün eklenmesinden görünümünün yapılandırılmasına kadar her şeyi kapsar.

Bu öğreticide **Aspose.Words DocumentBuilder**'ı kullanarak bir **ActiveX command button** eklemeyi, sınıfını **setOleClassName method** ile ayarlamayı ve **Forms2OleControl size**'ı düzenlemeyi öğreneceksiniz. Harici araçlara gerek yok—sadece bir .NET geliştirme ortamı ve Aspose.Words kütüphanesi.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürümünün yüklü olması (kod ayrıca .NET Framework 4.7+ ile de çalışır)
* Aspose.Words for .NET NuGet paketinin güncel bir sürümü
* C# ve Word belgelerindeki ActiveX kontrolleri kavramına temel aşinalık

Eğer bunlardan herhangi biri eksikse, NuGet paketini şu şekilde kurun:

```bash
dotnet add package Aspose.Words
```

## Bu öğreticide neler kapsanıyor

* `DocumentBuilder` örneği oluşturma
* `Forms2OleControl` ekleme (ActiveX command button için temel nesne)
* `setOleClassName` ile doğru sınıf adını atama
* **Forms2OleControl size** özelliklerini kullanarak görsel genişlik ve yüksekliği ayarlama
* Belgeyi kaydetme ve sonucu doğrulama

Kılavuzun sonunda, tıklanabilir bir düğme içeren tamamen işlevsel bir Word dosyanız olacak; bu düğmeyi daha da özelleştirebilir veya VBA makrolarına bağlayabilirsiniz.

---

## Kod içinde forms2olecontrol oluşturma – adım adım

### Adım 1: DocumentBuilder'ı Başlatma

`DocumentBuilder` sınıfı, Aspose.Words'ta çoğu belge‑oluşturma görevinin giriş noktasıdır. Metin, resim, tablo eklemek ve bu öğretici için özellikle OLE kontrolleri eklemek için yöntemler sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Neden önemlidir:**  
`DocumentBuilder` belgenin içindeki mevcut imleç konumunu tutar. Bunu erken oluşturduğunuzda, sonraki eklemelerin—örneğin **ActiveX command button**—tam istediğiniz yerde görünmesini sağlarsınız.

### Adım 2: Forms2OleControl'ı Ekleme

`insertForms2OleControl` yöntemi bir `Forms2OleControl` nesnesi döndürür. Bu nesne, Word'ün bir ActiveX düğmesi olarak render edeceği OLE kontrol yer tutucusunu temsil eder.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Neden önemlidir:**  
Bu çağrı olmadan kontrolün özelliklerini manipüle edemezsiniz. Döndürülen `Forms2OleControl`, **setOleClassName method**'a, boyut özniteliklerine ve diğer OLE‑özel ayarlara tam erişim sağlar.

### Adım 3: setOleClassName ile ActiveX sınıfını Belirtme

Word, hangi tür ActiveX kontrolünü render edeceğini bilmelidir. Standart bir komut düğmesi için sınıf adı `"Forms.CommandButton.1"`'dir.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Neden önemlidir:**  
`setOleClassName` yöntemi, genel OLE yer tutucusu ile somut **ActiveX command button** arasında bir köprüdür. Yanlış sınıf adı kullanmak, belge açıldığında boş bir nesne ya da çalışma zamanı hatasıyla sonuçlanır.

### Adım 4: Forms2OleControl boyutunu Ayarlama

Çok küçük ya da çok büyük bir düğme profesyonel görünmez. Boyutlarını `setWidth` ve `setHeight` ile kontrol edebilirsiniz.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Neden önemlidir:**  
Bu özellikler **Forms2OleControl size**'ı oluşturur. Düğmenin Word UI'da nasıl göründüğünü etkiler ve ekli makronun yeterli tıklama alanına sahip olmasını sağlar.

### Adım 5: Belgeyi Kaydet ve Test Et

Kontrolü yapılandırdıktan sonra, belgeyi istediğiniz bir konuma kaydedin.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

`ActiveXButton.docx` dosyasını Microsoft Word'de açın. “CommandButton1” (varsayılan başlık) etiketli bir düğme görmelisiniz. Bir VBA makrosu eklemediğiniz sürece tıklamak bir şey yapmaz, ancak kontrol kendisi tamamen işlevseldir.

**Beklenen çıktı:**  

![Eklemiş ActiveX komut düğmesi içeren Word belgesi](/images/activeX-button.png "Kod ile eklenmiş yeni oluşturulmuş bir ActiveX komut düğmesini gösteren Word belgesinin ekran görüntüsü")

*Görselin alt metni, erişilebilirlik ve SEO için anahtar kelimeyi içerir.*

---

## ActiveX Forms2OleControl sınıfını anlama

`Forms2OleControl` sınıfı, Word'ün ActiveX öğeleri için kullandığı düşük seviyeli OLE altyapısını kapsar. `Shape` sınıfından türetilir, bu da gerektiğinde tipik şekil biçimlendirmelerini (ör. kenarlıklar, döndürme) uygulayabileceğiniz anlamına gelir.

* **ActiveX command button** – En yaygın kullanım durumu; Word'ün geliştirici araçlarıyla bir makroya bağlayabilirsiniz.
* **setOleClassName method** – Word'ün yüklediği COM sınıfını belirler; diğer geçerli değerler `"Forms.TextBox.1"` ve `"Forms.ComboBox.1"` içerir.
* **Forms2OleControl size** – `SetWidth`/`SetHeight` ile kontrol edilir. Bu yöntemler puan (1 pt = 1/72 in) birimini kabul eder.

### Forms2OleControl ile İçerik Kontrolleri ne zaman kullanılmalı

Sadece basit veri girişi (ör. düz metin alanı) gerekiyorsa, Word'ün yerleşik içerik kontrolleri daha hafiftir. Olay işleme veya özel VBA etkileşimi gibi tam ActiveX işlevselliği gerektiğinde `Forms2OleControl` kullanın.

---

## Ek özellikleri ayarlama (isteğe bağlı)

Temel adımlar **kod içinde forms2olecontrol oluşturmak** için yeterli olsa da, genellikle düğmenin görünümünü veya davranışını ince ayar yapmak istersiniz.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Neden önemlidir:**  
`SetOleData`, OLE akışına doğrudan isteğe bağlı özellik değerleri yazmanıza olanak tanır. Bu, VBA'ya başvurmadan bir **ActiveX command button**'ı özelleştirmenin en esnek yoludur.

---

## Yaygın sorunlar ve sorun giderme

| Semptom | Muhtemel neden | Çözüm |
|--------|--------------|-----|
| Düğme gri bir kutu olarak görünür | `setOleClassName`'e yanlış sınıf adı gönderildi | Dizgenin tam olarak `"Forms.CommandButton.1"` olduğundan emin olun (büyük/küçük harfe duyarlı) |
| Boyut değişmez | Kontrol eklenmeden önce Width/Height ayarlandı | `SetWidth`/`SetHeight`'i her zaman `InsertForms2OleControl` **sonra** çağırın |
| Belge açıldığında “OLE object not found” hatası verir | Aspose.Words lisansı eksik (değerlendirme sürümü OLE'yi kısıtlayabilir) | Geçerli bir lisans uygulayın veya tam OLE desteğiyle ücretsiz deneme sürümünü kullanın |
| Düğme başlığı “CommandButton1” olarak kalır | `SetOleData` kullanılmadı veya makro özelliği okumuyor | `"Caption"` özelliğini okumak için bir VBA makrosu kullanın veya başlığı Word UI üzerinden ayarlayın |

---

## Tam, çalıştırılabilir örnek

Aşağıda, kopyalayıp yapıştırıp çalıştırabileceğiniz tam bir konsol uygulaması bulunmaktadır. Bu, öğreticide kapsanan her şeyi gösterir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Her bölümün açıklaması**

* **Using directives** – `Document`, `DocumentBuilder` ve `Forms2OleControl` için gereken Aspose.Words ad alanını getirir.
* **Document creation** – Boş bir Word dosyası oluşturur.
* **InsertForms2OleControl** – OLE kontrolünü builder'ın mevcut imlecine yerleştirir.
* **SetOleClassName** – Word'e kontrolün bir **ActiveX command button** olduğunu söyler.
* **SetWidth / SetHeight** – Profesyonel bir görünüm için **Forms2OleControl size**'ı ayarlar.
* **SetOleData (optional)** – Başlık gibi ek özelliklerin nasıl yazılacağını gösterir.
* **Save** – Son `.docx` dosyasını diske yazar.

Programı (`dotnet run`) çalıştırın ve `ActiveXButton.docx` dosyasını açın. Daha sonra bir makroya bağlayabileceğiniz bir düğme görmelisiniz.

---

## Sonuç

Artık Aspose.Words kullanarak **kod içinde forms2olecontrol oluşturmayı**, `DocumentBuilder`'ı başlatmaktan **ActiveX command button**'ı `setOleClassName` ile yapılandırmaya ve **Forms2OleControl size**'ı kontrol etmeye kadar biliyorsunuz. Bu yaklaşım, karmaşık Word belgelerini otomatikleştirmenizi, etkileşimli UI öğeleri eklemenizi ve tüm mantığı içinde tutmanızı sağlar

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [.NET için Aspose.Words kullanarak Word belgesinde Grup Şekli oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words ile Word'de dikdörtgen şekil oluşturma – Adım adım rehber](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}