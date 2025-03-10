---
title: Java için Aspose.Words'de İçerik Çıkarmak İçin Yardımcı Yöntemler
linktitle: İçerik Çıkarmak İçin Yardımcı Yöntemler
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java kullanarak Word belgelerinden içerikleri etkili bir şekilde nasıl çıkaracağınızı öğrenin. Bu kapsamlı kılavuzda yardımcı yöntemleri, özel biçimlendirmeyi ve daha fazlasını keşfedin.
weight: 14
url: /tr/java/document-manipulation/helper-methods-for-extracting-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de İçerik Çıkarmak İçin Yardımcı Yöntemler


## Java için Aspose.Words'de İçerik Çıkarmak İçin Yardımcı Yöntemlere Giriş

Aspose.Words for Java, geliştiricilerin Word belgeleriyle programatik olarak çalışmasına olanak tanıyan güçlü bir kütüphanedir. Word belgeleriyle çalışırken yaygın görevlerden biri de onlardan içerik çıkarmaktır. Bu makalede, Aspose.Words for Java kullanarak içeriği verimli bir şekilde çıkarmak için bazı yardımcı yöntemleri inceleyeceğiz.

## Ön koşullar

Kod örneklerine dalmadan önce, Java projenizde Aspose.Words for Java'nın yüklü ve ayarlanmış olduğundan emin olun. Bunu şuradan indirebilirsiniz:[Burada](https://releases.aspose.com/words/java/).

## Yardımcı Yöntem 1: Stile Göre Paragrafları Çıkarma

```java
public static ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    // Belirtilen stildeki paragrafları toplamak için bir dizi oluşturun.
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);

    // Belirtilen stile sahip olanları bulmak için tüm paragraflara göz atın.
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}
```

Word belgenizde belirli bir stile sahip paragrafları çıkarmak için bu yöntemi kullanabilirsiniz. Bu, başlıklar veya blok alıntılar gibi belirli bir biçimlendirmeye sahip içeriği çıkarmak istediğinizde yararlıdır.

## Yardımcı Yöntem 2: Düğümlere Göre İçerik Çıkarma

```java
public static ArrayList<Node> extractContentBetweenNodes(Node startNode, Node endNode, boolean isInclusive) {
    // Öncelikle bu metoda geçirilen düğümlerin kullanıma uygun olup olmadığı kontrol edilmelidir.
    verifyParameterNodes(startNode, endNode);
    
    // Çıkarılan düğümleri saklamak için bir liste oluşturun.
    ArrayList<Node> nodes = new ArrayList<Node>();

    // İşaretçilerden biri yorumun bir parçasıysa, yorumun kendisi de dahil olmak üzere, işaretçiyi hareket ettirmemiz gerekir
    // CommentRangeEnd düğümünden sonra bulunan Yorum Düğümüne ilet.
    if (endNode.getNodeType() == NodeType.COMMENT_RANGE_END && isInclusive) {
        Node node = findNextNode(NodeType.COMMENT, endNode.getNextSibling());
        if (node != null)
            endNode = node;
    }
    
    // Gerektiğinde işaretleyici düğümleri bölmek için bu yönteme geçirilen orijinal düğümlerin bir kaydını tutun.
    Node originalStartNode = startNode;
    Node originalEndNode = endNode;

    //Blok düzeyindeki düğümlere (paragraflar ve tablolar) dayalı içerik çıkarın. Bunları bulmak için üst düğümler arasında gezinin.
    // İşaretleyici düğümlerin satır içi olup olmamasına bağlı olarak ilk ve son düğümlerin içeriğini böleceğiz.
    startNode = getAncestorInBody(startNode);
    endNode = getAncestorInBody(endNode);
    boolean isExtracting = true;
    boolean isStartingNode = true;
    // Belgeden çıkardığımız geçerli düğüm.
    Node currNode = startNode;

    // İçeriği çıkarmaya başlayın. Tüm blok düzeyindeki düğümleri işleyin ve özellikle ilkini bölün
    // ve gerektiğinde son düğümler eklenerek paragraf biçimlendirmesinin korunması sağlanır.
    // Bu yöntem, normal bir çıkarıcıdan biraz daha karmaşıktır çünkü faktörlememiz gerekir
    // Çıkarmada satır içi düğümler, alanlar, yer imleri vb. kullanarak kullanışlı hale getirmek.
    while (isExtracting) {
        // Bir kopyasını elde etmek için geçerli düğümü ve onun alt düğümlerini klonlayın.
        Node cloneNode = currNode.deepClone(true);
        boolean isEndingNode = currNode.equals(endNode);
        if (isStartingNode || isEndingNode) {
            // Her bir işaretçiyi ayrı ayrı işlememiz gerekiyor, bu yüzden onu ayrı bir yönteme aktarıyoruz.
            // Düğüm indekslerini korumak için önce sonun işlenmesi gerekir.
            if (isEndingNode) {
                // !isStartingNode: İşaretçiler aynı düğüm ise düğümü iki kez eklemeyin.
                processMarker(cloneNode, nodes, originalEndNode, currNode, isInclusive,
                        false, !isStartingNode, false);
                isExtracting = false;
            }
            //Blok düzeyindeki başlangıç ve bitiş belirteçleri aynı düğüm olabileceğinden, koşulun ayrı olması gerekir.
            if (isStartingNode) {
                processMarker(cloneNode, nodes, originalStartNode, currNode, isInclusive,
                        true, true, false);
                isStartingNode = false;
            }
        } else
            // Düğüm bir başlangıç veya bitiş belirteci değildir, sadece kopyayı listeye ekleyin.
            nodes.add(cloneNode);

        // Sonraki düğüme geçin ve onu çıkarın. Sonraki düğüm boşsa,
        // İçeriğin geri kalanı farklı bir bölümde bulunmaktadır.
        if (currNode.getNextSibling() == null && isExtracting) {
            // Bir sonraki bölüme geçin.
            Section nextSection = (Section) currNode.getAncestor(NodeType.SECTION).getNextSibling();
            currNode = nextSection.getBody().getFirstChild();
        } else {
            // Gövdedeki bir sonraki düğüme geç.
            currNode = currNode.getNextSibling();
        }
    }

    // Satır içi yer imleri moduyla uyumluluk için bir sonraki paragrafı (boş) ekleyin.
    if (isInclusive && originalEndNode == endNode && !originalEndNode.isComposite())
        includeNextParagraph(endNode, nodes);

    // Düğüm işaretçileri arasındaki düğümleri döndür.
    return nodes;
}
```

Bu yöntem, paragraflar, tablolar veya diğer blok düzeyindeki öğeler olsun, belirtilen iki düğüm arasındaki içeriği çıkarmanıza olanak tanır. Satır içi işaretleyiciler, alanlar ve yer imleri dahil olmak üzere çeşitli senaryoları işler.

## Yardımcı Yöntem 3: Yeni Bir Belge Oluşturma

```java
public static Document generateDocument(Document srcDoc, ArrayList<Node> nodes) throws Exception {
    Document dstDoc = new Document();
    
    // Boş belgeden ilk paragrafı kaldırın.
    dstDoc.getFirstSection().getBody().removeAllChildren();
    
    // Listedeki her düğümü yeni belgeye aktarın. Düğümün orijinal biçimlendirmesini koruyun.
    NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
    for (Node node : nodes) {
        Node importNode = importer.importNode(node, true);
        dstDoc.getFirstSection().getBody().appendChild(importNode);
    }
    
    return dstDoc;
}
```

Bu yöntem, kaynak belgeden bir düğüm listesi içe aktararak yeni bir belge oluşturmanıza olanak tanır. Düğümlerin orijinal biçimlendirmesini koruyarak belirli içeriklere sahip yeni belgeler oluşturmak için kullanışlı hale getirir.

## Çözüm

Word belgelerinden içerik çıkarmak birçok belge işleme görevinin önemli bir parçası olabilir. Aspose.Words for Java, bu süreci basitleştiren güçlü yardımcı yöntemler sunar. İster stile göre paragrafları, düğümler arasındaki içeriği çıkarmanız veya yeni belgeler oluşturmanız gereksin, bu yöntemler Java uygulamalarınızda Word belgeleriyle verimli bir şekilde çalışmanıza yardımcı olacaktır.

## SSS

### Java için Aspose.Words'ü nasıl kurabilirim?

 Aspose.Words for Java'yı yüklemek için Aspose web sitesinden indirebilirsiniz. Ziyaret edin[Burada](https://releases.aspose.com/words/java/) En son sürümü edinmek için.

### Word belgesinin belirli bölümlerinden içerik çıkarabilir miyim?

Evet, bu makalede belirtilen yöntemleri kullanarak bir Word belgesinin belirli bölümlerinden içerik çıkarabilirsiniz. Çıkarmak istediğiniz bölümü tanımlayan başlangıç ve bitiş düğümlerini belirtmeniz yeterlidir.

### Aspose.Words for Java, Java 11 ile uyumlu mu?

Evet, Aspose.Words for Java, Java 11 ve üzeri sürümlerle uyumludur. Java uygulamalarınızda herhangi bir sorun yaşamadan kullanabilirsiniz.

### Çıkarılan içeriğin biçimlendirmesini özelleştirebilir miyim?

Evet, oluşturulan belgedeki içe aktarılan düğümleri değiştirerek çıkarılan içeriğin biçimlendirmesini özelleştirebilirsiniz. Aspose.Words for Java, ihtiyaçlarınızı karşılamak için kapsamlı biçimlendirme seçenekleri sunar.

### Aspose.Words for Java için daha fazla doküman ve örneği nerede bulabilirim?

 Aspose.Words for Java için kapsamlı dokümanları ve örnekleri Aspose web sitesinde bulabilirsiniz. Ziyaret edin[https://reference.aspose.com/words/java/](https://reference.aspose.com/words/java/) Ayrıntılı dokümantasyon ve kaynaklar için.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
