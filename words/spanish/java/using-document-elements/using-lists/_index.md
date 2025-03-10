---
title: Uso de listas en Aspose.Words para Java
linktitle: Uso de listas
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a utilizar listas en Aspose.Words para Java con este tutorial paso a paso. Organice y formatee sus documentos de manera eficaz.
weight: 18
url: /es/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uso de listas en Aspose.Words para Java


En este completo tutorial, exploraremos cómo usar listas de manera eficaz en Aspose.Words para Java, una potente API para trabajar con documentos de Microsoft Word de manera programática. Las listas son esenciales para estructurar y organizar el contenido de sus documentos. Cubriremos dos aspectos clave del trabajo con listas: reiniciar listas en cada sección y especificar niveles de lista. ¡Vamos a profundizar!

## Introducción a Aspose.Words para Java

Antes de comenzar a trabajar con listas, familiaricémonos con Aspose.Words para Java. Esta API proporciona a los desarrolladores las herramientas para crear, modificar y manipular documentos de Word en un entorno Java. Es una solución versátil para tareas que van desde la generación simple de documentos hasta el formato complejo y la gestión de contenido.

### Configuración de su entorno

 Para comenzar, asegúrese de tener Aspose.Words para Java instalado y configurado en su entorno de desarrollo. Puede descargarlo[aquí](https://releases.aspose.com/words/java/). 

## Reinicio de listas en cada sección

En muchos casos, es posible que necesite reiniciar las listas en cada sección del documento. Esto puede resultar útil para crear documentos estructurados con varias secciones, como informes, manuales o artículos académicos.

Aquí tienes una guía paso a paso sobre cómo lograrlo usando Aspose.Words para Java:

### Inicializar su documento: 
Comience creando un nuevo objeto de documento.

```java
Document doc = new Document();
```

### Agregar una lista numerada: 
Agregue una lista numerada a su documento. Usaremos el estilo de numeración predeterminado.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Configurar ajustes de lista: 
\Habilite la lista para reiniciarse en cada sección.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Configuración de DocumentBuilder: 
Cree un DocumentBuilder para agregar contenido a su documento.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Agregar elementos a la lista: 
Utilice un bucle para agregar elementos de lista a su documento. Insertaremos un salto de sección después del elemento número 15.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Guarde su documento: 
Guarde el documento con las opciones deseadas.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Siguiendo estos pasos podrás crear documentos con listas que se reinician en cada sección, manteniendo una estructura de contenido clara y organizada.

## Especificación de niveles de lista

Aspose.Words para Java le permite especificar niveles de lista, lo que resulta especialmente útil cuando necesita distintos formatos de lista dentro de su documento. Veamos cómo hacerlo:

### Inicializar su documento: 
Crear un nuevo objeto de documento.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Crear una lista numerada: 
Aplicar una plantilla de lista numerada de Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Especificar niveles de lista: 
Iterar a través de diferentes niveles de lista y agregar contenido.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Crear una lista con viñetas: 
Ahora, vamos a crear una lista con viñetas.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Especificar niveles de lista con viñetas: 
De manera similar a la lista numerada, especifique niveles y agregue contenido.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Formato de lista de detención: 
Para detener el formato de la lista, establezca la lista como nula.

```java
builder.getListFormat().setList(null);
```

### Guarde su documento: 
Guardar el documento.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Siguiendo estos pasos, puede crear documentos con niveles de lista personalizados, lo que le permitirá controlar el formato de las listas en sus documentos.

## Código fuente completo
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection se escribirá solo si el cumplimiento es mayor que OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Cree una lista numerada basada en una de las plantillas de lista de Microsoft Word
        // aplicarlo al párrafo actual del generador de documentos.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Hay nueve niveles en esta lista, probémoslos todos.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Cree una lista con viñetas basada en una de las plantillas de lista de Microsoft Word
        // aplicarlo al párrafo actual del generador de documentos.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Esta es una forma de detener el formato de lista.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Crea una lista basada en una plantilla.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Para reutilizar la primera lista, necesitamos reiniciar la numeración creando una copia del formato de la lista original.
        List list2 = doc.getLists().addCopy(list1);
        // Podemos modificar la nueva lista de cualquier manera, incluso establecer un nuevo número de inicio.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Conclusión

¡Felicitaciones! Aprendió a trabajar con listas en Aspose.Words para Java de manera eficaz. Las listas son fundamentales para organizar y presentar el contenido de sus documentos. Ya sea que necesite reiniciar listas en cada sección o especificar niveles de listas, Aspose.Words para Java le brinda las herramientas que necesita para crear documentos de apariencia profesional.

Ahora puede utilizar estas funciones con confianza para mejorar sus tareas de generación y formato de documentos. Si tiene alguna pregunta o necesita más ayuda, no dude en comunicarse con nosotros.[Foro de la comunidad Aspose](https://forum.aspose.com/) para soporte.

## Preguntas frecuentes

### ¿Cómo instalo Aspose.Words para Java?
 Puede descargar Aspose.Words para Java desde[aquí](https://releases.aspose.com/words/java/) y siga las instrucciones de instalación en la documentación.

### ¿Puedo personalizar el formato de numeración de las listas?
Sí, Aspose.Words para Java ofrece amplias opciones para personalizar los formatos de numeración de listas. Puede consultar la documentación de la API para obtener más detalles.

### ¿Aspose.Words para Java es compatible con los últimos estándares de documentos de Word?
Sí, puede configurar Aspose.Words para Java para cumplir con varios estándares de documentos de Word, incluido ISO 29500.

### ¿Puedo generar documentos complejos con tablas e imágenes usando Aspose.Words para Java?
¡Por supuesto! Aspose.Words para Java admite formatos de documentos avanzados, incluidas tablas, imágenes y más. Consulte la documentación para ver ejemplos.

### ¿Dónde puedo obtener una licencia temporal de Aspose.Words para Java?
Puede obtener una licencia temporal[aquí](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
