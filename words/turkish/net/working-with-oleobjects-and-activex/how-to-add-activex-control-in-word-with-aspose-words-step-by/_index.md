---
category: general
date: 2026-08-07
description: C# kullanarak bir Word belgesine ActiveX kontrolü eklemeyi öğrenin. Makroyu
  bir düğme ile ilişkilendirmeyi ve tıklanabilir düğme Word örneklerini eklemeyi içerir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: tr
lastmod: 2026-08-07
og_description: Aspose.Words kullanarak bir Word belgesine ActiveX kontrolü nasıl
  eklenir. Bu kılavuzu izleyerek bir düğme ekleyin, düğmeye makro atayın ve tıklanabilir
  bir düğme kelimesi ekleyin.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: Word'de ActiveX kontrolü nasıl eklenir – tam C# öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words ile Word'e ActiveX kontrolü ekleme – adım adım rehber
url: /tr/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Aspose.Words ile ActiveX kontrolü nasıl eklenir

Programlı olarak bir Microsoft Word dosyasına **how to add activex control** eklemeniz gerekiyorsa, bu eğitim Aspose.Words for .NET kullanarak tam adımları gösterir. Bir komut düğmesi nasıl eklenir, başlığı nasıl ayarlanır ve **associate macro with button** nasıl yapılır göreceksiniz, böylece kontrol kullanıcı tıkladığında tepki verir. Sonunda tam işlevsel bir düğme içeren makro‑etkin bir `.docm` dosyanız olacak.

ActiveX düğmesi eklemek, kredi başvuruları, çalışan işe alım formları veya otomatik raporlar gibi etkileşimli şablonlar oluştururken yaygın bir gereksinimdir. Bu kılavuz, kodun her satırını adım adım inceler, **why** her adımın neden önemli olduğunu açıklar ve karşılaşabileceğiniz tipik tuzakları kapsar.

## Önkoşullar

* .NET 6 (or .NET Core 3.1 / .NET Framework 4.8) installed.
* A valid Aspose.Words for .NET license or a temporary evaluation key.
* Visual Studio 2022 (or any IDE that supports C#).
* Basic familiarity with Word macros (VBA) if you plan to write the macro that the button will trigger.

> **Pro tip:** Örneği çalıştırdığınızda, çıktıyı yazma izniniz olan bir klasöre kaydedin, aksi takdirde `doc.Save` bir istisna fırlatır.

## Aspose.Words kullanarak bir Word belgesine ActiveX kontrolü nasıl eklenir

The core of the solution is a short C# program that creates a new document, inserts an ActiveX **CommandButton** control, and saves the file as a macro‑enabled document (`.docm`). The code is complete and ready to copy‑paste.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Her satırın önemi

| Line | Purpose |
|------|---------|
| `Document doc = new Document();` | Bellekte yeni bir Word paketi oluşturur. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | ActiveX kontrolleri dahil içerik eklemek için akıcı bir API sağlar. |
| `InsertForms2OleControl` | ActiveX kontrolü oluşturan tek Aspose.Words yöntemi; kontrol tipini (`CommandButton`) ve geometrisini belirtirsiniz. |
| `commandButton.Caption = "Click Me";` | Son kullanıcının gördüğü **add clickable button word** ayarlar. Başlık olmadan düğme boş görünür. |
| `commandButton.OnAction = "MyMacro";` | **associate macro with button** – kontrol tıklandığında Word'ün çalıştıracağı VBA makrosunu belirtir. |
| `doc.Save("CommandButton.docm");` | Belgeyi makro‑etkin bir dosya olarak kaydeder; normal bir `.docx` kontrol ve makroyu kaldırır. |

> **Note:** Koordinatlar (sol, üst) nokta cinsinden ölçülür (1 pt ≈ 1/72 in). Düğmeyi sayfada istediğiniz konuma yerleştirmek için bunları ayarlayın.

## Makroyu düğmeye nasıl ilişkilendirirsiniz

`OnAction` özelliği, düğmeyi `MyMacro` adlı bir VBA makrosuna bağlar. Bu makroyu Word dosyasının içinde ya manuel olarak ya da programlı olarak VBA kodu enjekte ederek (Aspose.Words VBA kodu yazmaz) oluşturmanız gerekir. İşte Word’ün **Developer → Visual Basic** editörünü kullanarak ekleyebileceğiniz minimal bir makro:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Kullanıcı `CommandButton.docm` dosyasını açıp düğmeye tıkladığında Word `MyMacro`'yu çalıştırır ve bir ileti kutusu gösterir. Makro güvenliği **Disable all macros without notification** olarak ayarlanmışsa, düğme devre dışı görünür. Kullanıcılara belge için makroları etkinleştirmelerini veya makroyu güvenilir bir sertifika ile imzalamalarını önerin.

### Makro ilişkilendirirken yaygın tuzaklar

* **Macro security settings** – Belge, sıkı güvenlik politikalarına sahip bir makinede açılırsa makro engellenebilir. Güvenlik seviyesini düşürme veya makroyu imzalama talimatları sağlayın.  
* **Naming conflicts** – Makro adı, belgenin VBA projesi içinde benzersiz olmalıdır; aksi takdirde Word “duplicate procedure name” hatası verir.  
* **64‑bit vs 32‑bit Word** – ActiveX kontrolleri aynı şekilde çalışır, ancak VBA editörü Office sürümüne bağlı olarak farklı uyarı mesajları gösterebilir.

## Word formuna tıklanabilir düğme kelimesi nasıl eklenir

`Caption` özelliği, kullanıcıların düğmede gördüğü metindir. Bunu daha da özelleştirebilirsiniz:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Kullanıcı girdisine bağlı olarak başlığın dinamik olarak değişmesi gerekiyorsa, kontrolü Word’ün nesne modeli üzerinden daha sonra erişebilirsiniz:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Kenar durumu: Uzun başlıklar

Word, düğmenin genişliğini aşan başlıkları kırpar. Kesilmemesi için ya `InsertForms2OleControl` içindeki genişlik argümanını artırın ya da metni kısaltın. Karakter genişliği değiştiği için farklı dillerde (ör. Almanca veya Japonca) test yapmak önerilir.

## Form otomasyonu için komut düğmesi kelimesi nasıl eklenir

Görsel başlığın ötesinde, **add command button word** kavramı kontrolün programatik adını kapsar. Aspose.Words, ActiveX kontrolleri için doğrudan bir `Name` özelliği sunmaz, ancak `AltText` alanını ayarlayabilirsiniz; Word bunu kontrolün tanımlayıcısı olarak kabul eder:

```csharp
commandButton.AltText = "SubmitButton";
```

Daha sonra VBA içinde düğmeye `AltText` değeriyle başvurabilirsiniz:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Bu teknik, birden fazla düğmeniz olduğunda ve onları programatik olarak ayırt etmeniz gerektiğinde faydalıdır.

## Tam çalışan örnek

Aşağıda, bir konsol uygulaması olarak derleyip çalıştırabileceğiniz tam program yer alıyor. İsteğe bağlı stil, makro ilişkilendirme ve her adımı açıklayan bir yorum bloğu içerir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** `SubmitForm.docm` dosyasını Microsoft Word'de açtığınızda, *Submit Form* etiketiyle mavi kenarlı bir düğme görüntülenir. Düğmeye tıkladığınızda, belgeye eklediğiniz takdirde VBA makrosu `SubmitMacro` çalışır. Düğme aynı `Forms2OleControl` nesnesiyle daha da taşınabilir, yeniden boyutlandırılabilir veya stil verilebilir.

## Çözümü test etme

1. C# konsol uygulamasını derleyip çalıştırın.  
2. Oluşturulan `SubmitForm.docm` dosyasını Word'de açın.  
3. İstenirse, makroları etkinleştirin.  
4. *Submit Form* düğmesine tıklayın – `SubmitMacro` içinde tanımlı ileti kutusunu görmelisiniz.

Düğme görünüyor ama hiçbir şey yapmıyorsa, makro adının tam olarak (`SubmitMacro`) eşleştiğinden ve makro güvenliğinin çalışmayı engellemediğinden emin olun.

## Sıkça Sorulan Sorular

| Question | Answer |
|----------|--------|
| *Can I add more than one ActiveX button?* | Evet. `InsertForms2OleControl` metodunu farklı koordinatlarla birden çok kez çağırın. `OnAction` ve `AltText` değerlerini farklı tutarak ayırt edin. |
| *Is the ActiveX control visible in Word Online?* | Hayır. |

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Belge Builder Kullanarak İçerik Ekleme Aspose.Words for .NET'de](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Şekil Gölge Eğitimi – C#'ta Word Şekline Gölge Ekleme](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Word Belgesine Yeni Bölüm Ekleme | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}