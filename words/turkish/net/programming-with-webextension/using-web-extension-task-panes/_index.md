---
"description": "Bu ayrıntılı, adım adım eğitimde Aspose.Words for .NET kullanarak Word belgelerine Web Uzantısı Görev Bölmeleri'nin nasıl ekleneceğini ve yapılandırılacağını öğrenin."
"linktitle": "Web Uzantısı Görev Bölmelerini Kullanma"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Web Uzantısı Görev Bölmelerini Kullanma"
"url": "/tr/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Web Uzantısı Görev Bölmelerini Kullanma

## giriiş

Aspose.Words for .NET kullanarak bir Word belgesinde Web Uzantısı Görev Bölmeleri'ni kullanma konusunda bu derinlemesine eğitime hoş geldiniz. Word belgelerinizi etkileşimli görev bölmeleriyle geliştirmek istediyseniz, doğru yerdesiniz. Bu kılavuz, bunu sorunsuz bir şekilde başarmanız için her adımda size yol gösterecektir.

## Ön koşullar

Başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

- Aspose.Words for .NET: İndirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
- .NET Geliştirme Ortamı: Visual Studio veya tercih ettiğiniz herhangi bir IDE.
- Temel C# Bilgisi: Bu, kod örneklerini takip etmenize yardımcı olacaktır.
- Aspose.Words için lisans: Bir tane satın alabilirsiniz [Burada](https://purchase.aspose.com/buy) veya geçici bir lisans alın [Burada](https://purchase.aspose.com/temporary-license/).

## Ad Alanlarını İçe Aktar

Kodlamaya başlamadan önce, projenize aşağıdaki ad alanlarının aktarıldığından emin olun:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Adım Adım Kılavuz

Şimdi süreci kolay takip edilebilir adımlara bölelim.

### Adım 1: Belge Dizininizi Ayarlama

İlk önce, belgeler dizininize giden yolu ayarlamamız gerekiyor. Word belgeniz buraya kaydedilecek.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` Belgelerinizin bulunduğu klasöre giden gerçek yol ile.

### Adım 2: Yeni Bir Belge Oluşturma

Şimdi Aspose.Words kullanarak yeni bir Word belgesi oluşturacağız.

```csharp
Document doc = new Document();
```

Bu satır, yeni bir örneğini başlatır `Document` Word belgesini temsil eden sınıf.

### Adım 3: Görev Bölmesi Ekleme

Şimdi, belgemize bir Görev Bölmesi ekleyeceğiz. Görev Bölmeleri, bir Word belgesi içinde ek işlevler ve araçlar sağlamak için kullanışlıdır.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

Burada yeni bir tane yaratıyoruz `TaskPane` nesneyi seçin ve belgenin `WebExtensionTaskPanes` koleksiyon.

### Adım 4: Görev Bölmesini Yapılandırma

Görev Bölmemizi görünür hale getirmek ve özelliklerini ayarlamak için aşağıdaki kodu kullanıyoruz:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` Görev Bölmesinin nerede görüneceğini ayarlar. Bu durumda, sağ taraftadır.
- `IsVisible` Görev Bölmesinin görünür olmasını sağlar.
- `Width` Görev Bölmesinin genişliğini ayarlar.

### Adım 5: Web Uzantısı Referansını Ayarlama

Daha sonra ID, versiyon, depolama türü ve depolama bilgilerini içeren Web Uzantısı Referansını ayarlıyoruz.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` web uzantısı için benzersiz bir tanımlayıcıdır.
- `Version` uzantının sürümünü belirtir.
- `StoreType` mağazanın türünü belirtir (bu durumda OMEX).
- `Store` Mağazanın dil/kültür kodunu belirtir.

### Adım 6: Web Uzantısına Özellikler Ekleme

Web uzantınıza davranışını veya içeriğini tanımlamak için özellikler ekleyebilirsiniz.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

Burada, adında bir özellik ekliyoruz `mailchimpCampaign`.

### Adım 7: Web Uzantısını Bağlama

Son olarak web uzantımıza bağlamalar ekliyoruz. Bağlamalar, uzantıyı belgenin belirli bölümlerine bağlamanıza olanak tanır.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` Bağlamanın adıdır.
- `WebExtensionBindingType.Text` Bağlamanın metin türünde olduğunu gösterir.
- `194740422` uzantının bağlı olduğu belgenin parçasının kimliğidir.

### Adım 8: Belgeyi Kaydetme

Her şeyi ayarladıktan sonra belgenizi kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Bu satır, belgeyi belirtilen dizine, belirtilen dosya adıyla kaydeder.

### Adım 9: Görev Bölmesi Bilgilerinin Yüklenmesi ve Görüntülenmesi

Görev bölmesi bilgilerini doğrulamak ve görüntülemek için belgeyi yükleyip görev bölmeleri arasında yineleme yapıyoruz.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Bu kod belgeyi yükler ve konsoldaki her görev bölmesinin sağlayıcısını, sürümünü ve katalog tanımlayıcısını yazdırır.

## Çözüm

Ve işte bu kadar! Aspose.Words for .NET kullanarak bir Word belgesine Web Uzantısı Görev Bölmesi'ni başarıyla eklediniz ve yapılandırdınız. Bu güçlü özellik, doğrudan belge içinde ek işlevler sağlayarak Word belgelerinizi önemli ölçüde geliştirebilir. 

## SSS

### Word'de Görev Bölmesi Nedir?
Görev Bölmesi, Word belgesi içerisinde ek araçlar ve işlevler sağlayan, kullanıcı etkileşimini ve üretkenliği artıran bir arayüz öğesidir.

### Görev Bölmesinin görünümünü özelleştirebilir miyim?
Evet, Görev Bölmesinin görünümünü şu gibi özellikleri ayarlayarak özelleştirebilirsiniz: `DockState`, `IsVisible`, Ve `Width`.

### Web Uzantı Özellikleri Nelerdir?
Web Uzantısı Özellikleri, bir web uzantısının davranışını veya içeriğini tanımlamak için ekleyebileceğiniz özel özelliklerdir.

### Bir Web Uzantısını belgenin bir bölümüne nasıl bağlarım?
Bir Web Uzantısını, kullanarak belgenin bir bölümüne bağlayabilirsiniz. `WebExtensionBinding` Bağlayıcı türünü ve hedef kimliğini belirten sınıf.

### Aspose.Words for .NET hakkında daha fazla bilgiyi nerede bulabilirim?
Ayrıntılı dokümanları bulabilirsiniz [Burada](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}