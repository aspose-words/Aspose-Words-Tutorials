---
category: general
date: 2026-07-29
description: Aspose.Words kullanarak Word belgesine komut düğmesi ekleyin. ActiveX
  kontrol özelliklerini ayarlamayı ve komut düğmesi başlığını birkaç kolay adımda
  nasıl ayarlayacağınızı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: tr
lastmod: 2026-07-29
og_description: Aspose.Words ile Word belgesine komut düğmesi ekleyin. Bu öğreticide,
  ActiveX kontrol özelliklerini nasıl ayarlayacağınız ve komut düğmesi başlığını hızlı
  bir şekilde nasıl belirleyeceğiniz gösterilmektedir.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Word Belgesine Komut Düğmesi Ekle – Aspose.Words Adım Adım
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Aspose.Words ile Word Belgesine Komut Düğmesi Ekleme – Tam Rehber
url: /tr/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesine Komut Düğmesi Ekle – Tam Programlama Rehberi

Bir **komut düğmesini word belgesine eklemek** istediğinizde hangi API çağrılarını kullanacağınızdan emin olmadınız mı? Yalnız değilsiniz; birçok geliştirici ilk kez bir DOCX dosyasına etkileşimli denetimler eklemeye çalıştığında bu engelle karşılaşır. İyi haber şu ki Aspose.Words bunu şaşırtıcı derecede sorunsuz hâle getiriyor. Bu rehberde bir CommandButton ActiveX denetimi oluşturmayı, **activex denetim özelliklerini ayarlamayı** ve **komut düğmesi başlığını ayarlamayı**—hepsi temiz C# kodu ile adım adım göstereceğiz; kodu hemen kopyalayıp yapıştırabilirsiniz.

Bu öğreticinin sonunda, tıklanabilir bir “Submit” (Gönder) düğmesi içeren tamamen işlevsel bir Word dosyanız olacak ve Microsoft Word’de açılmaya hazır olacak. Harici VBA betikleri, manuel UI ayarlamaları yok—sadece saf programatik kontrol.

## Öğrenecekleriniz

* Boş bir Word belgesi ve bir `DocumentBuilder` nasıl oluşturulur.
* Aspose.Words kullanarak **komut düğmesini word belgesine eklemek** için tam metod çağrısı.
* Boyut, konum ve ad gibi **activex denetim özelliklerini ayarlama** yolları.
* **Komut düğmesi başlığını ayarlama** tekniği, böylece düğme istediğiniz metni gösterir.
* Farklı düğme tipleri, DPI ölçekleme ve Word sürüm uyumluluğu gibi kenar durumlarını ele alma ipuçları.

> **Önkoşul:** Aspose.Words for .NET yüklü (NuGet paketi `Aspose.Words`) bir Visual Studio (veya herhangi bir C# IDE). Önceden ActiveX deneyimi gerekmez.

---

## Adım 1: Projeyi Kurun ve Namespace’leri İçe Aktarın

**Komut düğmesini word belgesine eklemek** için önce Aspose.Words’e referans veren bir C# projesine ihtiyacımız var. Yeni bir .NET konsol uygulaması oluşturun, ardından NuGet paketini ekleyin:

```bash
dotnet add package Aspose.Words
```

Şimdi gerekli namespace’leri kaynak dosyanıza getirin:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Bu üç `using` yönergesi, `Document`, `DocumentBuilder` ve ActiveX eklemeyi sağlayan `Forms2OleControl` sınıflarına erişim sağlar.

*İpucu:* Visual Studio kullanıyorsanız, IDE sınıf adlarını yazdığınızda bunları otomatik olarak eklemenizi önerir.

---

## Adım 2: Boş Bir Belge ve Builder Oluşturun

Yeni bir `Document` nesnesi boş bir Word dosyasını temsil eder. `DocumentBuilder` ise çizim, metin ekleme ve — kritik olarak — ActiveX denetimlerini yerleştirmemizi sağlayan kullanışlı “kalem”imizdir.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Bu aşamada belge sadece boş bir tuvaldir; komut düğmenizi bekleyen temiz bir kağıt gibi düşünün.

---

## Adım 3: CommandButton ActiveX Denetimini Ekleyin

Şimdi nihayet **komut düğmesini word belgesine ekliyoruz**. Aspose.Words, denetim tipini ve boyutlarını kabul eden `InsertForms2OleControl` metodunu sunar. `Forms2OleControlType.CommandButton` kullanacağız ve genişliği 150 puan, yüksekliği 30 puan olarak ayarlayacağız.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Metod, bir `Forms2OleControl` örneği döndürür; bu örnek bir sonraki adımda **activex denetim özelliklerini ayarlamak** için kullanılacak.

---

## Adım 4: Denetimi Yapılandırın – İsim, Başlık ve Konum

### Başlığı Ayarlama

Başlık, düğmenin üzerinde görünen metindir. **Komut düğmesi başlığını ayarlamak** için `Caption` özelliğine bir dize atamanız yeterlidir:

```csharp
commandButton.Caption = "Submit";
```

`"Submit"` ifadesini istediğiniz herhangi bir şeyle değiştirebilirsiniz — “Save”, “Export”, “Launch” vb. — ve Word tam olarak bu metni gösterecektir.

### Denetime İsim Verme

Denetime anlamlı bir isim vermek, daha sonra (örneğin Word makrolarını otomatikleştirirken) ona referans vermeyi kolaylaştırır. `Name` özelliğini ayarlayacağız:

```csharp
commandButton.Name = "btnSubmit";
```

### Sayfada Konumlandırma

Word, yerleşim için puan (inçin 1/72) kullanır. `Left` ve `Top` özelliklerini ayarlayarak düğmeyi istediğiniz yere yerleştirin:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Düğmeyi bir paragrafla hizalamanız gerekiyorsa, önce builder’ın imlecini hareket ettirin, ardından denetimi ekleyin; koordinatlar o konuma göre hesaplanır.

*Kenar durumu:* Yüksek DPI’lı monitörlerde görsel boyut Word’de biraz farklı görünebilir. Düğmenin fiziksel boyutunun cihazlar arasında tutarlı kalması için hedef DPI’ye (genellikle Word için 96 DPI) göre puanları hesaplayabilirsiniz.

---

## Adım 5: Belgeyi Kaydedin

Düğme tamamen yapılandırıldıktan sonra dosyayı kaydetmek tek satır bir komuttur:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Ortaya çıkan `CommandButton.docx` dosyası tam işlevli bir ActiveX düğmesi içerir. Microsoft Word’de açın; “Submit” düğmesini tam olarak yerleştirdiğiniz konumda göreceksiniz.

### Beklenen Sonuç

1. Word belgesi tek bir sayfa olarak açılır.
2. Belirttiğiniz koordinatlarda **Submit** etiketiyle bir dikdörtgen düğme görünür.
3. Düğmeye sağ‑tıklayıp **Properties** (Özellikler) seçtiğinizde `btnSubmit` ismini ve ayarladığınız diğer özellikleri görürsünüz.

---

## Adım 6: İleri Düzey Varyasyonlar ve Yaygın Tuzaklar

### Diğer ActiveX Türlerini Eklemek

`InsertForms2OleControl` metodu sadece komut düğmeleriyle sınırlı değildir. Onay kutuları, seçenek düğmeleri veya özel ActiveX nesneleri de gömebilirsiniz:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Aynı **activex denetim özelliklerini ayarlama** deseni geçerlidir — sadece tip enum’unu değiştirin.

### Word Sürümlerini Ele Alma

Eski Word sürümleri (2007 öncesi) ikili `.doc` formatını kullanır ve ActiveX denetimlerini farklı şekilde depolar. Aspose.Words, `.doc` olarak kaydettiğinizde denetimi otomatik olarak dönüştürür, ancak bazı özellikler (örneğin kesin konumlandırma) kayabilir. Eski formatları hedefliyorsanız, çıktıyı ilgili Word sürümünde test edin.

### Güvenlik Ayarları

Word, sıkı makro güvenliği olan makinelerde ActiveX denetimlerini devre dışı bırakabilir. “Security Warning” (Güvenlik Uyarısı) iletişimini önlemek için şunları düşünebilirsiniz:

* Belgeyi güvenilir bir sertifika ile imzalamak.
* Kullanıcıları bu dosya konumu için ActiveX içeriğini etkinleştirmeye yönlendirmek.
* Güvenlik bir endişe ise makro‑sız bir alternatif (ör. düz içerik denetimleri) kullanmak.

---

## Adım 7: Tam Çalışan Örnek

Aşağıda, tartıştığımız tüm adımları içeren, doğrudan çalıştırılabilir program yer alıyor. `Program.cs` dosyanıza kopyalayın, çıktı yolunu gerektiği gibi ayarlayın ve **Run** (Çalıştır) tuşuna basın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Bu kodun yaptığı:**

* Yeni bir belgeyle başlar.
* Bir komut düğmesi ekler, **activex denetim özelliklerini ayarlar** ve **komut düğmesi başlığını ayarlar**.
* Kısa bir açıklama paragrafı ekler.
* Dosyayı `CommandButton.docx` olarak kaydeder.

Programı çalıştırın, oluşturulan dosyayı açın; açıklama metninin altında düğmenin yer aldığını göreceksiniz.

---

## Sonuç

Aspose.Words kullanarak **komut düğmesini word belgesine eklemeyi**, **activex denetim özelliklerini ayarlamayı** ve **komut düğmesi başlığını ayarlamayı** kısa, üretim‑hazır bir C# snippet’iyle gösterdik. Yaklaşım ölçeklenebilir: denetim tipini değiştirin, boyutları ayarlayın veya veri kaynağını döngüye alarak onlarca düğmeyi otomatik olarak gömün.

Daha ileri gitmek ister misiniz? Şunları deneyin:

* Düğmeyi bir veri dışa aktarımını tetikleyen bir makroya bağlamak.
* `Picture` özelliğini kullanarak düğmenin içine resim veya özel simge eklemek.
* Birden fazla ActiveX denetimi (metin kutuları, açılır kutular vb.) içeren tam bir form oluşturmak.

Deneyim, Word otomasyonunda uzmanlaşmanın en iyi yoludur. Bir sorunla karşılaşırsanız DPI hesaplamalarınızı ve Word güvenlik ayarlarınızı tekrar kontrol etmeyi unutmayın. Kodlamanın tadını çıkarın ve belgelerinizin her zaman daha etkileşimli olmasını sağlayın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}