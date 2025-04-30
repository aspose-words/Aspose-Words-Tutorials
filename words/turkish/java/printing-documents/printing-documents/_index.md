---
"description": "Java için Aspose.Words'ü kullanarak belgeleri nasıl yazdıracağınızı öğrenin. Java uygulamalarınızda sorunsuz yazdırma için adım adım kılavuz."
"linktitle": "Belgeleri Yazdırma"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belgeleri Yazdırma"
"url": "/tr/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belgeleri Yazdırma


Aspose.Words for Java kullanarak belgeleri yazdırmak istiyorsanız doğru yerdesiniz. Bu adım adım kılavuzda, sağlanan kaynak kodunu kullanarak Aspose.Words for Java ile belgeleri yazdırma sürecinde size yol göstereceğiz.

## giriiş

Belgeleri yazdırmak birçok uygulamada yaygın bir görevdir. Aspose.Words for Java, Word belgeleriyle çalışmak için güçlü bir API sağlar ve bunları yazdırma olanağı da sunar. Bu eğitimde, bir Word belgesini adım adım yazdırma sürecinde size rehberlik edeceğiz.

## Ortamınızı Kurma

Koda dalmadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

- Java Geliştirme Kiti (JDK) yüklendi
- Aspose.Words for Java kütüphanesi indirildi ve projenize eklendi

## Belgeyi Yükleme

Başlamak için, yazdırmak istediğiniz Word belgesini yüklemeniz gerekir. Değiştir `"Your Document Directory"` belgenize giden yol ve `"Your Output Directory"` İstenilen çıktı dizini ile.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Bir Yazdırma İşi Oluşturma

Sonra, yüklenen belgemizi yazdırmak için bir yazdırma işi oluşturacağız. Aşağıdaki kod parçacığı bir yazdırma işini başlatır ve istenen yazıcı ayarlarını belirler.

```java
// Belgemizi yazdırmak için bir yazdırma işi oluşturun.
PrinterJob pj = PrinterJob.getPrinterJob();
// Belgedeki sayfa sayısıyla bir öznitelik kümesi başlatın.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Yazıcı ayarlarını diğer parametrelerle birlikte yazdırma belgesine aktarın.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Belgeyi Yazdırma

Artık yazdırma işimizi ayarladığımıza göre, belgeyi yazdırma zamanı geldi. Aşağıdaki kod parçacığı belgeyi yazdırma işiyle ilişkilendirir ve yazdırma sürecini başlatır.

```java
// Yazdırılacak belgeyi yazdırma işini kullanarak geçirin.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Tam Kaynak Kodu
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Belgemizi yazdırmak için bir yazdırma işi oluşturun.
PrinterJob pj = PrinterJob.getPrinterJob();
// Belgedeki sayfa sayısıyla bir öznitelik kümesi başlatın.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Yazıcı ayarlarını diğer parametrelerle birlikte yazdırma belgesine aktarın.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Yazdırılacak belgeyi yazdırma işini kullanarak geçirin.
pj.setPrintable(awPrintDoc);
pj.print();
```
MultipagePrintDocument'ın kaynak kodu
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <özet>
    /// Özel PrintDocument sınıfının oluşturucusu.
    /// </özet> 
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        // Öznitelik kümesinde tanımlanan sayfa başlangıç ve bitiş dizinleri.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Sırada hangi sayfanın indeksinin oluşturulacağını hesaplayın.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Sayfa dizini toplam sayfa aralığından fazlaysa hiçbir şey yoktur
        // daha fazlasını sunmak için.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Her küçük resim yer tutucusunun boyutunu puan olarak hesaplayın.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Bu kağıda basılacak ilk sayfanın numarasını hesaplayın.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Bu kağıt parçasına yazdırılacak son sayfanın numarasını seçin.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Hesaplanana kadar saklanan geçerli sayfadan seçili sayfalar arasında döngü yapın
        // Son sayfa.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Sütun ve satır indekslerini hesaplayın.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Küçük resmin konumunu dünya koordinatlarında (bu durumda noktalarda) tanımlayın.
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Sol ve üst başlangıç pozisyonlarını hesaplayın.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Hesaplanan koordinatları kullanarak belge sayfasını Graphics nesnesine işleyin
                // ve küçük resim yer tutucu boyutu.
                // Yararlı dönüş değeri, sayfanın işlendiği ölçektir.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // Sayfa kenarlıklarını çizin (sayfa küçük resmi küçük resimden daha küçük olabilir)
                // yer tutucu boyutu).
                if (mPrintPageBorders) {
                    // Sayfanın gerçek %100 boyutunu puan olarak alın.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Bilinen ölçek faktörünü kullanarak ölçeklenen sayfanın etrafına kenarlık çizin.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Küçük resim yer tutucusunun etrafına kenarlık çizin.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Eğer render sırasında herhangi bir hata oluşursa hiçbir şey yapmayın.
                // Eğer oluşturma sırasında herhangi bir hata olursa boş bir sayfa çizilecektir.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Sayfadaki sütun ve satır sayısını tanımlayın
        // Manzara odaklı kağıt.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // Kağıt Dikey yönde ise genişliği ve yüksekliği değiştirin.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Çözüm

Tebrikler! Java için Aspose.Words kullanarak bir Word belgesini başarıyla yazdırdınız. Bu adım adım kılavuz, belge yazdırmayı Java uygulamalarınıza sorunsuz bir şekilde entegre etmenize yardımcı olacaktır.

## SSS

### S1: Aspose.Words for Java kullanarak bir belgenin belirli sayfalarını yazdırabilir miyim?

Evet, bir belgeyi yazdırırken sayfa aralığını belirtebilirsiniz. Kod örneğinde, şunu kullandık: `attributes.add(new PageRanges(1, doc.getPageCount()))` tüm sayfaları yazdırmak için. Sayfa aralığını ihtiyacınıza göre ayarlayabilirsiniz.

### S2: Aspose.Words for Java toplu yazdırma için uygun mudur?

Kesinlikle! Aspose.Words for Java toplu yazdırma görevleri için oldukça uygundur. Benzer kod kullanarak bir belge listesinde gezinebilir ve bunları tek tek yazdırabilirsiniz.

### S3: Baskı hatalarını veya istisnaları nasıl işleyebilirim?

Yazdırma işlemi sırasında oluşabilecek olası istisnaları ele almalısınız. İstisnaları ele alma hakkında bilgi için Aspose.Words for Java belgelerine bakın.

### S4: Yazdırma ayarlarını daha fazla özelleştirebilir miyim?

Evet, yazdırma ayarlarını özel gereksinimlerinizi karşılayacak şekilde özelleştirebilirsiniz. Kullanılabilir yazdırma seçenekleri hakkında daha fazla bilgi edinmek için Aspose.Words for Java belgelerini inceleyin.

### S5: Aspose.Words for Java için daha fazla yardım ve desteği nereden alabilirim?

Ek destek ve yardım için şu adresi ziyaret edebilirsiniz: [Aspose.Words for Java forumu](https://forum.aspose.com/).

---

Artık Aspose.Words for Java kullanarak belgeleri nasıl yazdıracağınızı başarıyla öğrendiğinize göre, bu işlevselliği Java uygulamalarınızda uygulamaya başlayabilirsiniz. İyi kodlamalar!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}