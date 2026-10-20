---
category: general
date: 2026-10-20
description: Aspose.Words kullanarak programlı olarak Word belgesi oluşturun ve bir
  komut düğmesi ekleyin. ActiveX kontrolü eklemeyi ve düğme başlığını ayarlamayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: tr
lastmod: 2026-10-20
og_description: Programlı olarak Word belgesi oluşturun ve bir ActiveX komut düğmesi
  gömün. Bu öğreticide, kontrolü nasıl ekleyeceğiniz ve Aspose.Words ile başlığını
  nasıl ayarlayacağınız açıklanıyor.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Word belgesini programlı olarak oluştur – ActiveX düğmesi ekle
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: ActiveX düğmesiyle programatik olarak Word belgesi oluşturma
url: /tr/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ActiveX düğmesiyle programlı olarak Word belgesi oluşturma

Aspose.Words kullanarak programlı olarak Word belgesi oluşturun ve ardından kullanıcıların tıklayabileceği bir komut düğmesi ekleyin. Bu kılavuz, bir ActiveX kontrolü eklemeyi, özelliklerini yapılandırmayı ve sonucu **.docx** dosyası olarak kaydetmeyi adım adım gösterir.

Konsol uygulamasına kopyalayabileceğiniz tam, çalıştırılabilir bir örnek göreceksiniz. Eğitim sonunda, tam işlevsel bir komut düğmesi içeren bir Word dosyası oluşturabilecek ve **add command button**, **add activex control**, **insert activex button**, ve **set button caption** işlemlerini C# kodunuzdan çıkmadan anlayacaksınız.

## Önkoşullar

* .NET 6.0 SDK veya daha yeni bir sürüm yüklü  
* Visual Studio 2022 (veya C#‑uyumlu herhangi bir IDE)  
* Aspose.Words for .NET lisans dosyası (ücretsiz deneme bu örnek için çalışır)  
* C# ve .NET proje sistemi hakkında temel bilgi  

ActiveX desteği kütüphaneye yerleşik olduğu için **Aspose.Words** dışındaki ek NuGet paketlerine gerek yoktur.

## Adım 1: Projeyi kurun ve Aspose.Words ekleyin

1. Bir terminal veya Visual Studio açın ve yeni bir konsol projesi oluşturun:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Aspose.Words paketini ekleyin:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (İsteğe bağlı) Bir lisans dosyanız varsa, proje köküne koyun ve `Program.cs` dosyasının başına aşağıdaki satırı ekleyerek değerlendirme filigranlarını kaldırın:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Adım 2: Programlı olarak Word belgesi oluşturma – belgeyi başlatma

İlk işlem **programlı olarak Word belgesi oluşturma**dır. Bunu, bir `Document` nesnesi ve belge içeriğini düzenlemenizi sağlayan bir `DocumentBuilder` örneği oluşturarak yaparsınız.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` tüm dosyayı temsil ederken, `DocumentBuilder` belge içinde istediğiniz konuma taşıyabileceğiniz bir imleç tutar. Bu ayrım API’yı temiz tutar ve daha sonra **add activex control** eklemenizi düşük‑seviye yapıların manuel yönetimi olmadan mümkün kılar.

## Adım 3: Komut düğmesi ekleme – ActiveX kontrolü ekleme

Şimdi `OleControlType.CommandButton` türünde bir ActiveX kontrolü ekleyerek **add command button** işlemini gerçekleştireceksiniz. `InsertForms2OleControl` yöntemi kontrol tipini, bir konumu (`Point`) ve bir boyutu (`Size`) gerektirir.

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Yukarıdaki çağrı, belirttiğiniz tam koordinatlarda belgeye **insert activex button** ekler. Koordinatlar puan cinsinden ölçülür (1 pt ≈ 1/72 in). Düğmeyi belirli bir paragrafta istiyorsanız, önce builder’ın imlecini hareket ettirin:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Adım 4: Düğme başlığını ayarlama – komut düğmesi metnini özelleştirme

Etiketi olmayan bir düğme kafa karıştırıcıdır, bu yüzden **set button caption** işlemiyle anlamlı bir metin belirleyeceksiniz. `Caption` özelliği düğmede gösterilecek metni tanımlar, `Name` ise kontrole programatik bir tanımlayıcı verir.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Daha sonra belgeyi makro‑etkin bir formata (`.docm`) dışa aktarırsanız, `OnClick` değeri bir VBA makro adıyla eşleşmelidir. Düz bir `.docx` için özellik saklanır ancak çalıştırılmaz; bu çoğu otomasyon senaryosu için yeterlidir.

## Adım 5: ActiveX düğmesi içeren belgeyi kaydetme

Kontrolü yapılandırdıktan sonra **save the document** işlemini gerçekleştirebilirsiniz. Yazma izniniz olan bir klasör seçin ve maksimum uyumluluk için `.docx` uzantısını kullanın.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Oluşturulan dosyayı Microsoft Word’de açtığınızda, belirttiğiniz koordinatlarda **Submit** adlı bir düğme göreceksiniz. Masaüstü istemcisinde düğmeye tıkladığınızda `SubmitForm` makrosu (varsa) çalıştırılmaya çalışılacaktır.

## Adım 6: Sonucu doğrulama ve yaygın sorunları giderme

1. `ActiveXCommandButton.docx` dosyasını Microsoft Word’de açın.  
2. Düğmenin kenarlıklarını görmek için **Design Mode** (Developer sekmesi → **Design Mode**) moduna geçin.  
3. Düğme görünmüyorsa, **Developer** sekmesinin etkin olduğundan ve Word sürümünüzün ActiveX kontrollerini desteklediğinden emin olun.  
4. Makro‑etkin dosyalar (`.docm`) için `OnClick` içindeki makro adının bir VBA rutinine eşleştiğini doğrulayın; aksi takdirde Word bir güvenlik uyarısı gösterir.

### Pro ipucu

ActiveX kontrolleri yalnızca Windows’tadır. Çapraz platform etkileşime ihtiyacınız varsa, ActiveX düğmesi yerine **Content Controls** (`RichTextContentControl`) kullanmayı düşünün.

## Tam kaynak kodu

Aşağıda tam, çalıştırılabilir program yer almaktadır. `Program.cs` dosyasına kopyalayın ve `dotnet run` komutunu çalıştırın.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Optional: apply a license to remove evaluation watermarks
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // Step 2: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a paragraph to give context
        builder.Writeln("Please click the button below to submit the form:");
        builder.MoveToDocumentEnd();

        // Step 3: Add command button – insert ActiveX control
        Point position = new Point(100, 150);
        Size size = new Size(120, 30);
        Forms2OleControl commandButton = builder.InsertForms2OleControl(


## Sonraki Öğrenmeniz Gerekenler?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [ActiveX Düğmesiyle Word Belgesi Oluşturma – C# Kılavuzu](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Aspose.Words ile Word Belgesine Komut Düğmesi Ekleme – Tam Kılavuz](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Aspose.Words ile Word Belgesi Düğmesi Oluşturma – Tam Kod Örneği](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}