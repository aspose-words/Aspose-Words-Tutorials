---
"description": "Java için Aspose.Words kullanarak bir DataTable'dan tablo oluşturmayı öğrenin. Biçimlendirilmiş tablolarla profesyonel Word belgeleri zahmetsizce oluşturun."
"linktitle": "Datatable'dan Tablo Oluştur"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Datatable'dan Tablo Oluştur"
"url": "/tr/java/table-processing/generate-table-from-datatable/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Datatable'dan Tablo Oluştur

## giriiş

Veri kaynaklarından dinamik olarak tablolar oluşturmak birçok uygulamada yaygın bir görevdir. İster raporlar, ister faturalar veya veri özetleri üretiyor olun, bir tabloyu programatik olarak verilerle doldurabilmek size çok fazla zaman ve emek kazandırabilir. Bu eğitimde, Java için Aspose.Words kullanarak bir DataTable'dan bir tablonun nasıl oluşturulacağını inceleyeceğiz. Süreci yönetilebilir adımlara bölerek her bir parçayı net bir şekilde anlamanızı sağlayacağız.

## Ön koşullar

Koda dalmadan önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Java Geliştirme Kiti (JDK): Makinenizde JDK'nın yüklü olduğundan emin olun. Bunu şu adresten indirebilirsiniz: [Oracle web sitesi](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2. Java için Aspose.Words: Aspose.Words kütüphanesine ihtiyacınız olacak. En son sürümü şu adresten indirebilirsiniz: [Aspose'un sürüm sayfası](https://releases.aspose.com/words/java/).

3. IDE: IntelliJ IDEA veya Eclipse gibi bir Entegre Geliştirme Ortamı (IDE) kodlamayı kolaylaştıracaktır.

4. Temel Java Bilgisi: Java programlama kavramlarına aşinalık, kod parçacıklarını daha iyi anlamanıza yardımcı olacaktır.

5. Örnek Veriler: Bu eğitim için, bir veri kaynağını simüle etmek için "List of people.xml" adlı bir XML dosyası kullanacağız. Bu dosyayı test için örnek verilerle oluşturabilirsiniz.

## Adım 1: Yeni Bir Belge Oluşturun

Öncelikle tablomuzun bulunacağı yeni bir belge oluşturmamız gerekiyor. Bu, çalışmamızın tuvalidir.

```java
Document doc = new Document();
```

Burada yeni bir örnek oluşturuyoruz `Document` nesne. Bu, tablomuzu oluşturacağımız çalışma belgemiz olarak hizmet edecektir.

## Adım 2: DocumentBuilder'ı Başlatın

Daha sonra şunu kullanacağız: `DocumentBuilder` Belgeyi daha kolay bir şekilde düzenlememize olanak sağlayan sınıf.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

The `DocumentBuilder` nesnesi, belgeye tablo, metin ve diğer öğeleri eklemek için yöntemler sağlar.

## Adım 3: Sayfa Yönünü Ayarla

Tablomuzun geniş olmasını beklediğimizden sayfa yönünü yatay olarak ayarlayacağız.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Bu adım çok önemlidir çünkü tablomuzun sayfaya düzgün bir şekilde oturmasını ve kesilmemesini sağlar.

## Adım 4: XML'den Veri Yükle

Şimdi, verilerimizi XML dosyasından bir `DataTable`Verilerimiz buradan geliyor.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

Burada, XML dosyasını okuruz ve veri kümesinden ilk tabloyu alırız. Bu `DataTable` belgemizde görüntülemek istediğimiz verileri tutacaktır.

## Adım 5: Tabloyu DataTable'dan içe aktarın

Şimdi heyecan verici kısma geliyoruz: Verilerimizi tablo olarak belgeye aktarmak.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

Yöntemi çağırıyoruz `importTableFromDataTable`, geçerek `DocumentBuilder`, bizim `DataTable`ve sütun başlıklarının eklenip eklenmeyeceğini belirtmek için bir Boole değeri.

## Adım 6: Tabloyu Şekillendirin

Masamızı hazırladıktan sonra onu güzel gösterecek bazı düzenlemeler yapabiliriz.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Bu kod tabloya önceden tanımlanmış bir stil uygulayarak görsel çekiciliğini ve okunabilirliğini artırır.

## Adım 7: İstenmeyen Hücreleri Kaldırın

Eğer görüntülemek istemediğiniz sütunlar varsa, örneğin resim sütunu, bunları kolayca kaldırabilirsiniz.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Bu adım, tablomuzun yalnızca ilgili bilgileri göstermesini sağlar.

## Adım 8: Belgeyi Kaydedin

Son olarak oluşturulan tablonun bulunduğu belgemizi kaydediyoruz.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Bu satır, belgeyi belirtilen dizine kaydeder ve sonuçları incelemenize olanak tanır.

## importTableFromDataTable Yöntemi

Daha yakından bakalım `importTableFromDataTable` method. Bu method, tablo yapısını oluşturmaktan ve onu verilerle doldurmaktan sorumludur.

### Adım 1: Tabloyu Başlatın

Öncelikle belgede yeni bir tablo başlatmamız gerekiyor.

```java
Table table = builder.startTable();
```

Bu, belgemizde yeni bir tablo başlatır.

### Adım 2: Sütun Başlıkları Ekleyin

Sütun başlıklarını eklemek istiyorsak, şunu kontrol ederiz: `importColumnHeadings` bayrak.

```java
if (importColumnHeadings) {
    // Orijinal biçimlendirmeyi sakla
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // Başlık biçimlendirmesini ayarla
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // Sütun adlarını ekle
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // Orijinal biçimlendirmeyi geri yükle
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

Bu kod bloğu başlık satırını biçimlendirir ve sütun adlarını ekler. `DataTable`.

### Adım 3: Tabloyu Verilerle Doldurun

Şimdi, her satırda döngüye giriyoruz `DataTable` tabloya veri eklemek için.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

Bu bölümde farklı veri tiplerini ele alacağız, tarihleri uygun şekilde biçimlendireceğiz ve diğer verileri metin olarak ekleyeceğiz.

### Adım 4: Masayı Sonlandırın

Son olarak tüm veriler girildikten sonra tabloyu tamamlıyoruz.

```java
builder.endTable();
```

Bu satır tablomuzun sonunu işaret ediyor ve `DocumentBuilder` Bu bölümün bittiğini bilmek.

## Çözüm

Ve işte karşınızda! Java için Aspose.Words kullanarak bir DataTable'dan bir tablo oluşturmayı başarıyla öğrendiniz. Bu adımları izleyerek, belgelerinizde çeşitli veri kaynaklarına dayalı olarak kolayca dinamik tablolar oluşturabilirsiniz. İster raporlar ister faturalar oluşturun, bu yöntem iş akışınızı kolaylaştıracak ve belge oluşturma sürecinizi geliştirecektir.

## SSS

### Java için Aspose.Words nedir?
Aspose.Words for Java, Word belgelerini programlı olarak oluşturmak, düzenlemek ve dönüştürmek için güçlü bir kütüphanedir.

### Aspose.Words'ü ücretsiz kullanabilir miyim?
Evet, Aspose ücretsiz deneme sürümü sunuyor. Bunu şuradan indirebilirsiniz: [Burada](https://releases.aspose.com/).

### Aspose.Words'de tabloları nasıl biçimlendirebilirim?
Kütüphane tarafından sağlanan önceden tanımlanmış stil tanımlayıcılarını ve seçeneklerini kullanarak stiller uygulayabilirsiniz.

### Tablolara hangi tür verileri ekleyebilirim?
Metin, sayı ve tarih gibi çeşitli veri türlerini ekleyebilir ve bunları uygun şekilde biçimlendirebilirsiniz.

### Aspose.Words için desteği nereden alabilirim?
Destek bulabilir ve soru sorabilirsiniz. [Aspose forumu](https://forum.aspose.com/c/words/8/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}