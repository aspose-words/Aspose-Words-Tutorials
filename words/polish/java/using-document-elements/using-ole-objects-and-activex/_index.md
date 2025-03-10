---
title: Korzystanie z obiektów OLE i kontrolek ActiveX w Aspose.Words dla Java
linktitle: Korzystanie z obiektów OLE i kontrolek ActiveX
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Naucz się używać obiektów OLE i kontrolek ActiveX w Aspose.Words dla Java. Twórz interaktywne dokumenty z łatwością. Zacznij teraz!
weight: 21
url: /pl/java/using-document-elements/using-ole-objects-and-activex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Korzystanie z obiektów OLE i kontrolek ActiveX w Aspose.Words dla Java

W tym samouczku pokażemy, jak pracować z obiektami OLE (Object Linking and Embedding) i kontrolkami ActiveX w Aspose.Words for Java. Obiekty OLE i kontrolki ActiveX to potężne narzędzia, które pozwalają na ulepszanie dokumentów poprzez osadzanie lub łączenie zewnętrznej zawartości, takiej jak arkusze kalkulacyjne, pliki multimedialne lub kontrolki interaktywne. Śledź, jak zagłębiamy się w przykłady kodu i uczymy się, jak skutecznie korzystać z tych funkcji.

### Wymagania wstępne

Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:

1.  Aspose.Words dla Java: Upewnij się, że biblioteka Aspose.Words jest zainstalowana w Twoim projekcie Java. Możesz ją pobrać z[Tutaj](https://releases.aspose.com/words/java/).

2. Środowisko programistyczne Java: Na swoim systemie powinieneś mieć zainstalowane działające środowisko programistyczne Java.

### Wstawianie obiektu OLE

Zacznijmy od wstawienia obiektu OLE do dokumentu Word. Utworzymy prosty dokument Word, a następnie wstawimy obiekt OLE reprezentujący stronę internetową.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", prawda, prawda, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

W tym kodzie tworzymy nowy dokument i wstawiamy obiekt OLE, który wyświetla witrynę Aspose. Możesz zastąpić adres URL żądaną treścią.

### Wstawianie obiektu OLE za pomocą OlePackage

Następnie przyjrzyjmy się sposobowi wstawiania obiektu OLE za pomocą OlePackage. Pozwala to na osadzanie plików zewnętrznych jako obiektów OLE w dokumencie.

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

tym przykładzie wstawiamy obiekt OLE za pomocą OlePackage, co umożliwia dołączenie plików zewnętrznych jako obiektów osadzonych.

### Wstawianie obiektu OLE jako ikony

Teraz zobaczmy, jak wstawić obiekt OLE jako ikonę. Jest to przydatne, gdy chcesz wyświetlić ikonę reprezentującą osadzony plik.

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

W tym kodzie wstawiamy obiekt OLE jako ikonę, zapewniając bardziej atrakcyjną wizualnie reprezentację osadzonej zawartości.

### Odczytywanie właściwości kontrolki ActiveX

Teraz przenieśmy naszą uwagę na kontrolki ActiveX. Nauczymy się, jak odczytywać właściwości kontrolek ActiveX w dokumencie Word.

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

W tym kodzie przeglądamy kształty w dokumencie Word, identyfikujemy kontrolki ActiveX i pobieramy ich właściwości.

### Wniosek

Gratulacje! Nauczyłeś się, jak pracować z obiektami OLE i kontrolkami ActiveX w Aspose.Words for Java. Te funkcje otwierają świat możliwości tworzenia dynamicznych i interaktywnych dokumentów.

### Często zadawane pytania

### Jaki jest cel obiektów OLE w dokumencie Word? 
   - Obiekty OLE umożliwiają osadzanie lub łączenie zewnętrznej zawartości, np. plików lub stron internetowych, w dokumencie programu Word.

### Czy mogę dostosować wygląd obiektów OLE w moim dokumencie? 
   - Tak, można dostosować wygląd obiektów OLE, w tym ustawić ikony i nazwy plików.

### Czym są kontrolki ActiveX i w jaki sposób mogą ulepszyć moje dokumenty? 
   - Kontrolki ActiveX to interaktywne elementy, które mogą dodawać funkcjonalność do dokumentów programu Word, np. kontrolek formularzy lub odtwarzaczy multimedialnych.

### Czy Aspose.Words for Java nadaje się do automatyzacji dokumentów na poziomie przedsiębiorstwa? 
   - Tak, Aspose.Words for Java to potężna biblioteka umożliwiająca automatyzację generowania i manipulowania dokumentami w aplikacjach Java.

### Gdzie mogę uzyskać dostęp do Aspose.Words dla Java? 
   -  Możesz pobrać Aspose.Words dla Javy ze strony[Tutaj](https://releases.aspose.com/words/java/).

Zacznij korzystać z Aspose.Words for Java już dziś i odkryj pełen potencjał automatyzacji i personalizacji dokumentów!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
