---
"description": "Aprenda a usar objetos OLE y controles ActiveX en Aspose.Words para Java. Cree documentos interactivos fácilmente. ¡Empiece ya!"
"linktitle": "Uso de objetos OLE y controles ActiveX"
"second_title": "API de procesamiento de documentos Java de Aspose.Words"
"title": "Uso de objetos OLE y controles ActiveX en Aspose.Words para Java"
"url": "/es/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uso de objetos OLE y controles ActiveX en Aspose.Words para Java

En este tutorial, exploraremos cómo trabajar con objetos OLE (vinculación e incrustación de objetos) y controles ActiveX en Aspose.Words para Java. Los objetos OLE y los controles ActiveX son herramientas potentes que permiten mejorar los documentos incrustando o vinculando contenido externo, como hojas de cálculo, archivos multimedia o controles interactivos. Continúe mientras profundizamos en los ejemplos de código y aprende a usar estas funciones eficazmente.

### Prerrequisitos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:

1. Aspose.Words para Java: Asegúrate de tener la biblioteca Aspose.Words instalada en tu proyecto Java. Puedes descargarla desde [aquí](https://releases.aspose.com/words/java/).

2. Entorno de desarrollo de Java: debe tener un entorno de desarrollo de Java en funcionamiento configurado en su sistema.

### Inserción de un objeto OLE

Comencemos insertando un objeto OLE en un documento de Word. Crearemos un documento de Word simple y luego insertaremos un objeto OLE que represente una página web.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "archivohtml", verdadero, verdadero, nulo);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

En este código, creamos un nuevo documento e insertamos un objeto OLE que muestra el sitio web de Aspose. Puede reemplazar la URL con el contenido deseado.

### Inserción de un objeto OLE con OlePackage

A continuación, exploraremos cómo insertar un objeto OLE mediante un OlePackage. Esto permite incrustar archivos externos como objetos OLE en el documento.

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

En este ejemplo, insertamos un objeto OLE utilizando un OlePackage, lo que le permite incluir archivos externos como objetos incrustados.

### Insertar un objeto OLE como icono

Ahora, veamos cómo insertar un objeto OLE como icono. Esto resulta útil si desea mostrar un icono que representa un archivo incrustado.

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

En este código, insertamos un objeto OLE como ícono, proporcionando una representación visualmente más atractiva del contenido incrustado.

### Lectura de las propiedades del control ActiveX

Ahora, centrémonos en los controles ActiveX. Aprenderemos a leer las propiedades de los controles ActiveX en un documento de Word.

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

En este código, iteramos a través de las formas en un documento de Word, identificamos controles ActiveX y recuperamos sus propiedades.

### Conclusión

¡Felicitaciones! Has aprendido a trabajar con objetos OLE y controles ActiveX en Aspose.Words para Java. Estas funciones abren un mundo de posibilidades para crear documentos dinámicos e interactivos.

### Preguntas frecuentes

### ¿Cuál es el propósito de los objetos OLE en un documento de Word? 
   - Los objetos OLE le permiten incrustar o vincular contenido externo, como archivos o páginas web, dentro de un documento de Word.

### ¿Puedo personalizar la apariencia de los objetos OLE en mi documento? 
   - Sí, puede personalizar la apariencia de los objetos OLE, incluida la configuración de íconos y nombres de archivos.

### ¿Qué son los controles ActiveX y cómo pueden mejorar mis documentos? 
   - Los controles ActiveX son elementos interactivos que pueden agregar funcionalidad a sus documentos de Word, como controles de formulario o reproductores multimedia.

### ¿Es Aspose.Words para Java adecuado para la automatización de documentos a nivel empresarial? 
   - Sí, Aspose.Words para Java es una potente biblioteca para automatizar la generación y manipulación de documentos en aplicaciones Java.

### ¿Dónde puedo obtener acceso a Aspose.Words para Java? 
   - Puede descargar Aspose.Words para Java desde [aquí](https://releases.aspose.com/words/java/).

¡Empiece hoy mismo a utilizar Aspose.Words para Java y descubra todo el potencial de la automatización y personalización de documentos!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}