---
category: general
date: 2026-04-21
description: Stilize bir dikdörtgen ve gölge içeren Word belgesi oluşturun. C#'ta
  gölge eklemeyi, dikdörtgen şekli eklemeyi, gölge rengini ayarlamayı ve daha fazlasını
  öğrenin.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: tr
og_description: Word belgesi oluşturun ve C#'ta gölgeli bir dikdörtgen şekli ekleyin.
  Gölge rengini, bulanıklığını ve ofsetleri kolayca ayarlamak için bu kılavuzu izleyin.
og_title: Gölgelendirilmiş Dikdörtgenli Word Belgesi Oluştur – Adım Adım
tags:
- Aspose.Words
- C#
- Document Automation
title: Gölgelendirilmiş Dikdörtgenli Word Belgesi Oluşturma – Tam Rehber
url: /tr/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gölgelendirilmiş Dikdörtgen ile Word Belgesi Oluşturma – Tam Kılavuz

Hiç **Word belgesi oluşturma** ihtiyacınız oldu mu ve düz bir metin sayfasından daha şık bir görünüm istediğiniz oldu mu? Belki bir rapor şablonu ya da bir broşür hazırlıyorsunuz ve basit bir dikdörtgen ile hafif bir gölge işinizi görür. Bu öğreticide tam olarak bunu yapacağız—dikdörtgen şekli ekleme, gölgeyi etkinleştirme ve rengini, bulanıklığını ve ofsetlerini özelleştirme—hepsi C# ve Aspose.Words ile.

Ayrıca **gölge ekleme** konusunu da ele alacağız; bu yöntem Word 2016, 2019 ya da en yeni Office 365 sürümüne hedeflense de çalışır. Sonunda gölgeli bir dikdörtgen gösteren, kaydedilebilir bir *.docx* dosyanız olacak ve ayarladığınız her özelliğin “neden”ini anlayacaksınız.

## Gereksinimler

- .NET 6 (veya herhangi bir güncel .NET Framework sürümü)  
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)  
- C# sözdizimine temel aşinalık  
- Visual Studio gibi bir IDE (herhangi bir editör de iş görür)

Ek bir kütüphane gerekmez; diğer her şey Aspose.Words içinde bulunur.

## 1. Adım – Belgeyi ve Builder’ı Başlatma (Word Belgesi Oluşturma)

Programatik olarak **Word belgesi oluşturmak** için `Document` sınıfı ile başlarsınız. `DocumentBuilder` ise fırçanızdır; metin, şekil ve diğer öğeleri eklemenizi sağlar.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Neden önemli?* `Document` nesnesi tüm .docx dosyasını temsil eder. Onsuz dikdörtgeni ya da gölgesini ekleyecek bir yeriniz olmaz.

## 2. Adım – Dikdörtgen Şekli Ekleme (Insert Rectangle Shape)

Şimdi gerçekten **dikdörtgen şekli ekliyoruz**. `InsertShape` metodu bir `ShapeType` enum’u ve genişlik‑yükseklik değerlerini (puan cinsinden) alır.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*İpucu:* 1 puan ≈ 1/72 inç, yani 200 pt yaklaşık 2.78 inç genişliğindedir. Düzeninize göre bu değerleri ayarlayın.

## 3. Adım – Gölgeyi Etkinleştirme (How to Add Shadow)

Gölge varsayılan olarak kapalıdır. `Visible` bayrağını `true` yaparak açın.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Ne oluyor?* `Visible` true olduğunda Word, bir sonraki adımda ayarladığınız diğer özelliklere göre bir drop‑shadow çizer.

## 4. Adım – Gölge Görünümünü Özelleştirme (Set Shadow Color, Blur, Offsets)

Burada **gölge rengini**, bulanıklık yarıçapını ve X/Y ofsetlerini **ayarlarız**. Denemekten çekinmeyin—farklı değerler yumuşak bir parıltı, derin bir düşüş ya da “yüzen” bir etki yaratabilir.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Bu sayılar neden?* 5 pt bulanıklık yumuşak, tüy gibi bir kenar verir; 4 pt ofset gölgeyi sağ‑aşağı kaydırarak üst‑sol köşeden gelen bir ışık kaynağını taklit eder. Daha güçlü bir kontrast için `Color` değerini `Color.Black` yapın, yarı saydam bir siyah için `Color.FromArgb(128, 0, 0, 0)` kullanın.

### Kenar Durumları ve Varyasyonlar

- **Bulanıklık yok:** `Blur = 0` yaparak keskin, sert kenarlı bir gölge elde edin.  
- **Negatif ofsetler:** `OffsetX = -4` ile gölgeyi sola itin.  
- **Farklı şekiller:** Aynı gölge özellikleri daire, üçgen ya da serbest çizim şekilleri için de çalışır—sadece 2. adımdaki `ShapeType`ı değiştirin.  
- **Uyumluluk:** Aspose.Words gölge verisini Office Open XML formatında yazar; bu, Word 2010‑2021 ve Office 365 arasında sorunsuz çalışır.

## 5. Adım – Belgeyi Kaydetme (Word Belgesi Oluşturma)

Son olarak dosyayı diske yazın. İstediğiniz herhangi bir desteklenen formatı (`.docx`, `.pdf`, `.odt`, …) seçebilirsiniz; bu kılavuzda klasik Word formatını kullanacağız.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

**ShadowRectangle.docx** dosyasını Microsoft Word’de açtığınızda, alt‑sağa hafifçe kaydırılmış, bulanık bir gölgeye sahip gri bir dikdörtgen göreceksiniz—tam da kodladığımız gibi.

### Beklenen Çıktı

- Tek sayfalık bir *.docx* dosyası.  
- `InsertShape` çağrıldığında imlecin bulunduğu yerde, 200 pt × 100 pt boyutlarında merkezlenmiş bir dikdörtgen.  
- 4 pt sağ ve 4 pt aşağı kaydırılmış, 5 pt bulanıklıkta gri bir gölge.

Şekil merkezden kaymış gibi görünürse, eklemeden önce `builder.MoveTo` ile imleci taşıyabilir ya da ekledikten sonra şeklin `Left` ve `Top` özelliklerini ayarlayabilirsiniz.

## Sık Sorulan Sorular & Sorun Giderme

**S: Gölge Word’de görünmüyor.**  
C: `ShadowFormat.Visible` değerinin `true` olduğundan emin olun. Ayrıca Aspose.Words’ün gölge özelliği 20.3 sürümünde eklendi; güncel bir sürüm kullandığınızdan emin olun.

**S: Gölgeye bir degrade (gradient) uygulayabilir miyim?**  
C: `ShadowFormat` üzerinden doğrudan mümkün değildir. Word arayüzü degrade gölgeleri destekler, ancak Aspose.Words’ün izlediği Open XML şeması yalnızca **düz renk** gölgeleri sunar. Bunun için temel XML’i manuel olarak düzenlemeniz gerekir; bu daha ileri bir senaryodur.

**S: Sadece gölgesi olan şeffaf bir dikdörtgene ihtiyacım var ise?**  
C: Ekleme sonrası `rectangle.FillColor = Color.Transparent;` satırını ekleyin. Gölge, dolgu renginden bağımsız olarak hâlâ renderlanır.

## Üretim Kodu İçin Pro İpuçları

- **Builder’ı yeniden kullanın:** Birden fazla şekil ekliyorsanız aynı `DocumentBuilder` örneğini tutun; her şekil için yeni bir builder oluşturmak gereksiz yük getirir.  
- **Toplu kaydetme:** Tüm değişikliklerden sonra tek sefer kaydedin; sık I/O büyük belge üretiminde yavaşlamaya neden olur.  
- **Hata yönetimi:** Tüm bloğu bir `try / catch` içine alın ve `Aspose.Words` istisnalarını **loglayın**; belge şablonu bozulmuşsa genellikle yardımcı satır numaraları içerirler.

## Sonraki Adımlar (İlgili Konular)

- **Gölge ekleme** resimlere veya metin kutularına (benzer `ShadowFormat` kullanımı).  
- **Dikdörtgen şekli ekleme** tablo hücresi içinde özel hücre stillendirmesi için.  
- **Word’te dikdörtgen oluşturma** Word’ün yerel XML’iyle (ham Open XML’i tercih edenler için).  
- **Gölge rengini ayarlama** kullanıcı girişi ya da tema renklerine göre dinamik olarak.

Farklı renkler, bulanıklık yarıçapları ve ofsetlerle deneyler yapın—belki kurumsal bir rapor için yumuşak mavi bir parıltı, ya da çarpıcı bir broşür için derin siyah bir gölge. Olanaklar sınırsız, kod değişiklikleri ise minimal.

---

### Hızlı Özet

- Sıfırdan **Word belgesi oluşturduk**.  
- **Dikdörtgen şekli ekledik** ve gölgesini açtık.  
- **Gölge rengini**, bulanıklığını ve ofsetlerini ayarlayarak profesyonel bir görünüm elde ettik.  
- Dosyayı kaydettik, dağıtıma hazır hale getirdik.

Artık herhangi bir Word otomasyon projesine görsel bir dokunuş katmak için sağlam bir temele sahipsiniz. Başka fikirleriniz mi var? Yorum bırakın, sohbeti sürdürelim. Mutlu kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}