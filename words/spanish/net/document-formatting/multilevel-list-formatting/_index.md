---
title: Formato de lista multinivel en documento de Word
linktitle: Formato de lista multinivel en documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a dominar el formato de listas multinivel en documentos de Word con Aspose.Words para .NET con nuestra guía paso a paso. Mejore la estructura de los documentos sin esfuerzo.
weight: 10
url: /es/net/document-formatting/multilevel-list-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formato de lista multinivel en documento de Word

## Introducción

Si eres un desarrollador que busca automatizar la creación y el formato de documentos de Word, Aspose.Words para .NET es una herramienta revolucionaria. Hoy, analizaremos en profundidad cómo puedes dominar el formato de listas multinivel con esta potente biblioteca. Ya sea que estés creando documentos estructurados, describiendo informes o generando documentación técnica, las listas multinivel pueden mejorar la legibilidad y la organización de tu contenido.

## Prerrequisitos

Antes de entrar en los detalles esenciales, asegurémonos de que tienes todo lo que necesitas para seguir este tutorial.

1. Entorno de desarrollo: asegúrese de tener configurado un entorno de desarrollo. Visual Studio es una excelente opción.
2.  Aspose.Words para .NET: Descargue e instale la biblioteca Aspose.Words para .NET. Puede obtenerla[aquí](https://releases.aspose.com/words/net/).
3.  Licencia: Obtenga una licencia temporal si no tiene una completa. Consígala[aquí](https://purchase.aspose.com/temporary-license/).
4. Conocimientos básicos de C#: será beneficioso estar familiarizado con C# y el marco .NET.

## Importar espacios de nombres

Para utilizar Aspose.Words para .NET en su proyecto, deberá importar los espacios de nombres necesarios. A continuación, le indicamos cómo hacerlo:

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

## Paso 1: Inicialice su documento y generador

Lo primero es lo primero: vamos a crear un nuevo documento de Word e inicializar DocumentBuilder. La clase DocumentBuilder proporciona métodos para insertar contenido en el documento.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Aplicar numeración predeterminada

 Para comenzar con una lista numerada, utilice el`ApplyNumberDefault` método. Esto configura el formato de lista numerada predeterminado.

```csharp
builder.ListFormat.ApplyNumberDefault();
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

 En estas líneas,`ApplyNumberDefault` comienza la lista numerada, y`Writeln` añade elementos a la lista.

## Paso 3: Sangría para subniveles

 A continuación, para crear subniveles dentro de su lista, utilice el`ListIndent` método. Este método sangra el elemento de la lista, convirtiéndolo en un subnivel del elemento anterior.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.1");
builder.Writeln("Item 2.2");
```

Este fragmento de código sangra los elementos y crea una lista de segundo nivel.

## Paso 4: Más sangría para niveles más profundos

Puedes seguir aplicando sangrías para crear niveles más profundos dentro de tu lista. Aquí, crearemos un tercer nivel.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.2.1");
builder.Writeln("Item 2.2.2");
```

Ahora tienes una lista de tercer nivel bajo el “Elemento 2.2”.

## Paso 5: Eliminar sangría para volver a niveles superiores

 Para volver a un nivel superior, utilice el`ListOutdent` método. Esto mueve el elemento nuevamente al nivel de lista anterior.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 2.3");
```

Esto lleva el “Artículo 2.3” de nuevo al segundo nivel.

## Paso 6: Eliminar numeración

Una vez que haya terminado con su lista, puede eliminar la numeración para continuar con texto normal u otro tipo de formato.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 3");
builder.ListFormat.RemoveNumbers();
```

Este fragmento de código completa la lista y detiene la numeración.

## Paso 7: Guarde su documento

Por último, guarde el documento en el directorio que desee.

```csharp
doc.Save(dataDir + "DocumentFormatting.MultilevelListFormatting.docx");
```

Esto guarda su documento bellamente formateado con listas de varios niveles.

## Conclusión

¡Y ya está! Ha creado con éxito una lista de varios niveles en un documento de Word con Aspose.Words para .NET. Esta potente biblioteca le permite automatizar tareas complejas de formato de documentos con facilidad. Recuerde que dominar estas herramientas no solo le permite ahorrar tiempo, sino que también garantiza la coherencia y el profesionalismo en el proceso de generación de documentos.

## Preguntas frecuentes

### ¿Puedo personalizar el estilo de numeración de la lista?
 Sí, Aspose.Words para .NET le permite personalizar el estilo de numeración de listas utilizando el`ListTemplate` clase.

### ¿Cómo agrego viñetas en lugar de números?
 Puede aplicar viñetas utilizando el`ApplyBulletDefault` método en lugar de`ApplyNumberDefault`.

### ¿Es posible continuar numerando desde una lista anterior?
 Sí, puedes continuar numerando utilizando el`ListFormat.List` propiedad para vincular a una lista existente.

### ¿Cómo cambio el nivel de sangría dinámicamente?
 Puede cambiar dinámicamente el nivel de sangría utilizando`ListIndent` y`ListOutdent` métodos según sea necesario.

### ¿Puedo crear listas multinivel en otros formatos de documentos como PDF?
Sí, Aspose.Words permite guardar documentos en varios formatos, incluido PDF, manteniendo el formato.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
