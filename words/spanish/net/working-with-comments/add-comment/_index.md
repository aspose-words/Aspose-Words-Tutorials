---
title: Insertar un Comment en un párrafo específico de un documento Word usando Aspose.Words for .NET
weight: 210
limit:
description: Guía paso a paso para añadir un comentario de autor a un párrafo seleccionado en un documento Word y guardarlo como DOCX usando Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Guía paso a paso para añadir un comentario de autor a un párrafo seleccionado
    en un documento Word y guardarlo como DOCX usando Aspose.Words for .NET.
  headline: Insertar un Comment en un párrafo específico de un documento Word usando
    Aspose.Words for .NET
  type: TechArticle
- description: Guía paso a paso para añadir un comentario de autor a un párrafo seleccionado
    en un documento Word y guardarlo como DOCX usando Aspose.Words for .NET.
  name: Insertar un Comment en un párrafo específico de un documento Word usando Aspose.Words
    for .NET
  steps:
  - name: Instancie un nuevo Document y un DocumentBuilder para comenzar a construir
      el archivo Word.
    text: Instancie un nuevo Document y un DocumentBuilder para comenzar a construir
      el archivo Word.
  - name: Utilice DocumentBuilder.Writeln para agregar tres párrafos de texto separados
      al documento.
    text: Utilice DocumentBuilder.Writeln para agregar tres párrafos de texto separados
      al documento.
  - name: Recupere de forma segura el segundo párrafo, recurriendo al primero si el
      documento tiene menos de dos párrafos.
    text: Recupere de forma segura el segundo párrafo, recurriendo al primero si el
      documento tiene menos de dos párrafos.
  - name: Cree un Comment con los datos del autor, establezca su texto y adjúntelo
      al párrafo seleccionado.
    text: Cree un Comment con los datos del autor, establezca su texto y adjúntelo
      al párrafo seleccionado.
  - name: Guarde el documento modificado como un archivo DOCX llamado 'sample.docx'
      en la carpeta actual.
    text: Guarde el documento modificado como un archivo DOCX llamado 'sample.docx'
      en la carpeta actual.
  type: HowTo
- questions:
  - answer: El bloque `if` recurre al primer párrafo (`paraList[0]`) cuando `paraList.Count`
      es menor que 2, por lo que el comentario se adjuntará a ese único párrafo en
      lugar del segundo que falta.
    question: ¿Qué hace el código si el documento contiene solo un párrafo?
  - answer: Se pasan al constructor `Comment` como el segundo y tercer argumento –
      `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – donde "Jordan" es
      el nombre del autor y "JH" son las iniciales.
    question: ¿Cómo se establecen el nombre del autor del comentario y sus iniciales
      en este ejemplo?
  - answer: En este fragmento el comentario está vinculado a todo el `Paragraph` mediante
      `AppendChild`, pero para comentar un rango de texto necesitaría crear un `CommentRangeStart`
      y un `CommentRangeEnd` alrededor de los nodos `Run` deseados y luego agregar
      el nodo `Comment` entre ellos.
    question: ¿Puedo adjuntar un comentario a una parte específica del texto en lugar
      de todo el párrafo?
  - answer: '`AppendChild` agrega el nodo `Comment` a la colección de hijos del párrafo,
      y Aspose.Words genera automáticamente los marcadores de inicio y fin de comentario
      necesarios cuando se guarda el documento.'
    question: ¿Necesito insertar manualmente los marcadores de comentario, o `AppendChild`
      se encarga de eso?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Insertar un comentario en un párrafo Word
og_description: Agregar un comentario de autor a un párrafo específico y exportar el archivo como DOCX con Aspose.Words.
og_image_alt: Guía que muestra cómo agregar un comentario a un párrafo en un documento Word usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar un Comment en un párrafo específico de un documento Word usando Aspose.Words
Con Aspose.Words for .NET puede agregar comentarios a archivos Word de forma programática. Este tutorial recorre la creación de un nuevo documento, la inserción de tres párrafos, la localización del segundo párrafo y la adjunción de un comentario que incluye la información del autor y la fecha. Finalmente, el documento se guarda como un archivo DOCX preservando el comentario.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ¿Qué hace el código si el documento contiene solo un párrafo?**  
A: El bloque `if` recurre al primer párrafo (`paraList[0]`) cuando `paraList.Count` es menor que 2, por lo que el comentario se adjuntará a ese único párrafo en lugar del segundo que falta.

**Q: ¿Cómo se establecen el nombre del autor del comentario y sus iniciales en este ejemplo?**  
A: Se pasan al constructor `Comment` como el segundo y tercer argumento – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – donde "Jordan" es el nombre del autor y "JH" son las iniciales.

**Q: ¿Puedo adjuntar un comentario a una parte específica del texto en lugar de todo el párrafo?**  
A: En este fragmento el comentario está vinculado a todo el `Paragraph` mediante `AppendChild`, pero para comentar un rango de texto necesitaría crear un `CommentRangeStart` y un `CommentRangeEnd` alrededor de los nodos `Run` deseados y luego agregar el nodo `Comment` entre ellos.

**Q: ¿Necesito insertar manualmente los marcadores de comentario, o `AppendChild` se encarga de eso?**  
A: `AppendChild` agrega el nodo `Comment` a la colección de hijos del párrafo, y Aspose.Words genera automáticamente los marcadores de inicio y fin de comentario necesarios cuando se guarda el documento.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}