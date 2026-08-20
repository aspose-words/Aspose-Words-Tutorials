---
category: general
date: 2026-08-20
description: ActiveX denetimi oluşturmayı, düğme boyutunu ayarlamayı ve tam bir C#
  örneğiyle düğmeyi Word'e eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: tr
lastmod: 2026-08-20
og_description: C# ile bir Word dosyasında ActiveX kontrolü oluşturun. Bu öğreticide,
  düğme boyutunu ayarlama, düğmeyi Word’e ekleme ve tıklanabilir bir düğme oluşturma
  gösterilmektedir.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Word'de bir ActiveX kontrolü oluşturun – adım adım C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: C# kullanarak bir Word belgesinde ActiveX kontrolü nasıl oluşturulur
url: /tr/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# kullanarak bir Word belgesinde ActiveX kontrolü oluşturma

Eğer bir Microsoft Word dosyası içinde **ActiveX kontrolü oluşturmanız** gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. **Word'e düğme ekleme**, düğmenin boyutlarını ayarlama ve kontrolü tıklanabilir hâle getirme işlemlerini kısa, bağımsız bir C# programı ile göreceksiniz.

Bu öğreticide şunları öğreneceksiniz:

* Etkileşimli Word belgeleri için bir ActiveX kontrolünün neden faydalı olduğunu anlayacaksınız.  
* **Düğme boyutunu ayarlama** ve bir başlık atama için gereken kesin kodu öğreneceksiniz.  
* Daha sonra bir makroya veya harici mantığa bağlanabilecek **tıklanabilir düğme** oluşturmayı göreceksiniz.  

Adımlar Aspose.Words .NET 23.12 veya daha yeni sürümlerle çalışır ve yalnızca bir .NET geliştirme ortamı gerektirir.

> **Önkoşul** – Geçerli bir Aspose.Words lisansınız (veya değerlendirme sürümünüz) ve Visual Studio 2022 ya da herhangi bir C# IDE'si bulunmalı.

---

## Word belgesinde ActiveX kontrolü oluşturma

İlk adım, boş bir `Document` ve bir `DocumentBuilder` örneği oluşturmaktır. Builder, ActiveX kontrolleri gibi nesneleri eklemek için yüksek‑seviye API sağlar.

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
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

`InsertActiveXButton` yöntemi (aşağıda tanımlanmıştır), **düğmeyi nasıl ekleyeceğiniz** ve yapılandıracağınız mantığını içerir.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Programı çalıştırdığınızda **ActiveXButton.docx** oluşturulur. Dosyayı Word'de açtığınızda **Submit** etiketiyle bir düğme görünür. Kontrol tamamen işlevseldir—tıklamak, standart `CommandButton_Click` olayını tetikler; bunu daha sonra bir VBA makrosuna bağlayabilirsiniz.

### Bu neden çalışıyor

* `InsertForms2OleControl` Word'e **CommandButton** tipinde bir OLE nesnesi gömmesini söyler; bu klasik ActiveX düğme sınıfıdır.  
* Genişlik ve yükseklik argümanları doğrudan **düğme boyutunu ayarlar**; Word değerleri puandan (1 pt ≈ 1/72 in) dönüştürür.  
* Kontrolün adı (`Name = "btnSubmit"`) VBA içinde (`ActiveDocument.InlineShapes("btnSubmit")`) kolayca bulunmasını sağlar.  

---

## Düğme boyutunu ve başlığını ayarla

Farklı bir görünüm istiyorsanız, `InsertForms2OleControl` çağrısındaki sayısal argümanları ayarlayın. Yöntemin imzası şu şekildedir:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – ActiveX sınıfının programatik tanımlayıcısı (`"CommandButton"` standart bir düğme için).  
* **width / height** – Puan cinsinden boyut. 2 cm genişliğinde bir düğme için `width = 56.7` (2 cm ≈ 56.7 pt) kullanın.  

Eklemeden sonra başlığı da değiştirebilirsiniz:

```csharp
commandButton.Caption = "Send Request";
```

Başlığı değiştirmek boyutu etkilemez, ancak kullanıcı için görsel geri bildirimi etkiler.

### İpucu

Kare bir düğme istiyorsanız, iki boyutu da aynı değere ayarlayın:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Word'e düğme ekle ve tıklanabilir hâle getir

Yukarıdaki kod zaten **Word'e düğme ekliyor**. Düğmenin bir eylem gerçekleştirmesi için, `Click` olayını işleyen bir VBA makrosu yazmanız gerekir. İşte Word VBA editörüne (`Alt+F11` → Insert → Module) yapıştırabileceğiniz minimal bir makro:

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Kontrol `btnSubmit` olarak adlandırıldığı için Word, `Click` olayını otomatik olarak `btnSubmit_Click`'e eşler. Bu, harici kütüphaneler olmadan **tıklanabilir düğme** işlevselliği oluşturmanın standart yoludur.

> **Not:** Word'deki makro güvenlik ayarları ActiveX kontrollerini engelleyebilir. Belge için “Enable all macros” veya “Enable VBA macros” seçeneğinin işaretli olduğundan emin olun, ya da üretim kullanımında makroyu dijital olarak imzalayın.

---

## Sık sorulan sorular: düğmeyi nasıl eklenir ve sorun giderme

### 1. Düğme kaydedildikten sonra görünmezse ne olur?

* Aspose.Words sürümünün `InsertForms2OleControl`'ı desteklediğini doğrulayın. 22.5 öncesi sürümler bu özelliğe sahip değildir.  
* Hedef dosya formatının `.docx` veya `.doc` olduğundan emin olun. `.rtf` gibi eski formatlar ActiveX nesnelerini depolayamaz.

### 2. Düğmeyi belirli bir yer imine ekleyebilir miyim?

Evet. `InsertForms2OleControl` çağırmadan önce builder'ı yer imine taşıyın:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Metin uzunluğuna göre **düğme boyutunu** dinamik olarak nasıl ayarlarsınız?

`Graphics.MeasureString` yöntemi (`System.Drawing`'dan) ile gerekli genişliği hesaplayın ve pikseli puana dönüştürün (`points = pixels * 72 / DPI`). Ardından hesaplanan genişliği `InsertForms2OleControl`'a geçirin.

### 4. Bir döngü içinde birden fazla düğme eklemenin bir yolu var mı?

Kesinlikle. Ekleme mantığını bir `for` döngüsü içinde sarın ve her yineleme için `Left` ve `Top` özelliklerini ayarlayın:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Beklenen çıktı

Programı çalıştırıp **ActiveXButton.docx** dosyasını açtığınızda:

* İlk sayfanın sol‑üst kısmına tek bir **Submit** düğmesi görünür.  
* Düğme boyutu sağladığınız ölçülerle eşleşir (`100 pt × 30 pt`).  
* VBA makrosunu eklediyseniz, düğmeye tıkladığınızda “You clicked the Submit button!” mesaj kutusu gösterilir.

Artık **ActiveX kontrolü oluşturmayı**, **düğme boyutunu ayarlamayı**, ve **Word'e düğme eklemeyi** başarıyla yaptınız; ayrıca gelecekteki otomasyon görevleri için **düğmeyi nasıl ekleyeceğinizi** ve **tıklanabilir düğme oluşturmayı** öğrendiniz.

---

## Sonuç

Bu öğreticide C# ile bir Word belgesi içinde **ActiveX kontrolü oluşturmayı** öğrendiniz. Adımları izleyerek **düğme boyutunu ayarlayabilir**, kontrole anlamlı bir ad verebilir ve **Word'e düğme ekleyerek** VBA makrosuna bağlanan bir **tıklanabilir düğme** elde edebilirsiniz.  

Buradan şu konuları keşfedebilirsiniz:

* VBA yerine bir .NET COM eklentisine düğmeyi bağlamak.  
* `CheckBox` veya `ComboBox` gibi diğer ActiveX sınıflarını kullanmak.  
* Birden çok kontrol içeren tam formlar oluşturmayı otomatikleştirmek.

Farklı boyutlarla denemeler yapmaktan çekinmeyin


## Sonra Ne Öğrenmelisin?


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve ilgili konuları derinlemesine ele alan içeriklerdir. Her kaynak, adım‑adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [.NET'te Yüzen Görsel ile Word Belgesi Oluşturma](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Aspose.Words Kullanarak Başlık ve Altbilgi ile Word Belgesi Oluşturma](/words/english/net/header-footer-formatting/create-header-footer/)
- [Word'den Erişilebilir PDF Oluşturma – Tam Kılavuz](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}