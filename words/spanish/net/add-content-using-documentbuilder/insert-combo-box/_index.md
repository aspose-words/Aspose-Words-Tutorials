---
title: Agregar un campo de formulario de cuadro combinado a un documento Word con Aspose.Words for .NET
weight: 310
limit:
description: Aprenda cómo agregar un campo de formulario de cuadro combinado con elementos predefinidos a un documento Word usando Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar un campo de formulario de cuadro combinado a un documento Word con Aspose.Words
Este tutorial demuestra cómo usar DocumentBuilder de Aspose.Words for .NET para crear un nuevo documento Word e insertar un campo de formulario de cuadro combinado poblado con elementos predefinidos. Al seguir el código paso a paso, verá cómo configurar las opciones del cuadro combinado y luego guardar el documento para su uso en formularios interactivos.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ¿Qué representa la matriz `items` que se pasa a `InsertComboBox`?**
A: Define la lista de cadenas que aparecen como opciones seleccionables en el desplegable del cuadro combinado.

**Q: ¿Cómo puedo cambiar qué elemento está seleccionado por defecto cuando se abre el documento?**
A: Establezca el tercer argumento (`selectedIndex`) de `InsertComboBox` al índice basado en cero del elemento predeterminado deseado (p. ej., `2` para "Three").

**Q: ¿Es posible colocar el cuadro combinado en una ubicación específica del documento?**
A: Sí: mueva el cursor de `DocumentBuilder` al punto deseado usando métodos como `MoveToParagraph`, `InsertParagraph` o `Write` antes de llamar a `InsertComboBox`.

**Q: ¿Qué formato de archivo crea este código y puede abrirse en versiones anteriores de Word?**
A: El código guarda un archivo `.docx`, que puede abrirse con Word 2007 y versiones posteriores, así como con cualquier aplicación que admita el formato OpenXML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}