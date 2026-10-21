---
category: general
date: 2026-04-04
description: Capture advertencias de sustitución de fuentes al cargar documentos Word
  con Aspose.Words para Java y detecte automáticamente las fuentes faltantes. Siga
  esta guía paso a paso.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: es
og_description: Capture advertencias de sustitución de fuentes al cargar documentos
  Word con Aspose.Words para Java y detecte fuentes faltantes en unos pocos pasos
  sencillos.
og_title: Capturar advertencias de sustitución de fuentes – Detectar fuentes faltantes
tags:
- Aspose.Words
- Java
- Document Processing
title: Capturar advertencias de sustitución de fuentes – Detectar fuentes faltantes
url: /es/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturar advertencias de sustitución de fuentes – Detectar fuentes faltantes

¿Alguna vez necesitaste **capturar advertencias de sustitución de fuentes** al abrir un archivo Word, solo para descubrir que una tipografía crucial falta? No estás solo. En muchos flujos de trabajo empresariales, una fuente faltante puede convertir un informe perfectamente formateado en un desastre confuso, y la única pista que obtienes es una advertencia silenciosa que la mayoría de los desarrolladores nunca ve.

La buena noticia es que Aspose.Words for Java te permite engancharte al proceso de carga y **detectar fuentes faltantes** antes de que te causen problemas más adelante. En este tutorial recorreremos un ejemplo completo y ejecutable que imprime cada advertencia de sustitución directamente en la consola, para que puedas decidir si incrustar la fuente correcta, reemplazarla o alertar al usuario.

Al final de esta guía sabrás cómo:

* Configurar un objeto `LoadOptions` con una devolución de llamada de advertencia personalizada.
* Filtrar la devolución de llamada para que solo reaccione a eventos de sustitución de fuentes.
* Cargar cualquier archivo `.docx` y ver las advertencias al instante.
* Ampliar la solución para registrar advertencias, lanzar excepciones o incluso instalar automáticamente fuentes faltantes.

No se requiere documentación externa, solo unas pocas líneas de Java y el JAR de Aspose.Words.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 8 o superior instalado (la última versión LTS funciona mejor).
* Aspose.Words for Java 23.11 o posterior – puedes obtener el artefacto Maven o el JAR simple desde el sitio web de Aspose.
* Un documento Word que haga referencia a una fuente que no tienes en tu máquina de desarrollo (p. ej., “MyFancyFont”).  
* Un IDE o editor de texto de tu preferencia – yo uso IntelliJ IDEA, pero Eclipse o VS Code también sirven.

Si alguno de estos te resulta desconocido, detente e instálalo primero; el resto del tutorial asume que ya están listos.

---

## Capturar advertencias de sustitución de fuentes usando Aspose.Words

El núcleo de la solución reside en una instancia de `LoadOptions`. Al asignar un `IWarningCallback` podemos interceptar cada advertencia que la biblioteca emite durante la fase de carga.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Por qué funciona esto:**  
`LoadOptions` indica a Aspose.Words cómo tratar el archivo entrante. La interfaz `IWarningCallback` es un gancho que recibe un objeto `WarningInfo` para *cada* advertencia. Al comprobar `info.getWarningType()` filtramos todo excepto `SUBSTITUTED_FONT`. La propiedad `description` contiene un mensaje legible como “Font 'MyFancyFont' was substituted with 'Arial'`.

### Salida esperada en la consola

Si el documento fuente hace referencia a una fuente que no está instalada, verás algo como:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Si el documento solo usa fuentes que existen en la máquina, la devolución de llamada permanece silenciosa y solo obtienes la línea final “Document loaded successfully.”.

---

## Detectar fuentes faltantes en tu documento

Podrías preguntarte, *“¿Una advertencia de sustitución es lo mismo que una fuente faltante?”* En la mayoría de los casos, sí—Aspose.Words sustituye una fuente faltante por una alternativa y lo informa mediante `SUBSTITUTED_FONT`. Sin embargo, existen casos límite donde la fuente está presente pero el estilo exacto (negrita‑cursiva, características específicas de OpenType) no lo está, lo que lleva a una sustitución sutil.

Para estar absolutamente seguro de que has capturado cada brecha, puedes combinar la devolución de llamada de advertencia con una inspección después de la carga:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Consejo profesional:** Si encuentras cualquier ejecución que aún haga referencia a la fuente faltante, puedes reemplazarla al vuelo:

```java
font.setName("Arial"); // fallback
```

De esa manera garantizas un resultado visual consistente, incluso si la advertencia original fue suprimida.

---

## Errores comunes y cómo evitarlos

| **Error** | **Por qué ocurre** | **Solución** |
|-----------|--------------------|--------------|
| **Olvidar establecer la devolución de llamada** | `LoadOptions` por defecto usa una devolución de llamada sin operación, por lo que las advertencias desaparecen. | Siempre llama a `loadOptions.setWarningCallback(...)` antes de cargar. |
| **Usar el tipo de advertencia incorrecto** | `WarningType.SUBSTITUTED_FONT` es el único enum que indica fuentes faltantes. | Filtra en `WarningType.SUBSTITUTED_FONT` *exactamente*; otros tipos (p. ej., `UNKNOWN_FILE_FORMAT`) no están relacionados. |
| **Codificar rutas de archivo de forma rígida** | Funciona localmente pero falla en pipelines CI/CD. | Usa una ruta relativa o pasa la ubicación del archivo como argumento de línea de comandos. |
| **Ignorar fuentes Unicode** | Algunas fuentes faltantes solo son un problema para ciertos caracteres. | Prueba con un documento que contenga el conjunto completo de caracteres que esperas soportar. |
| **Ejecutar en un servidor sin cabeza sin configuración de fuentes** | El servidor puede carecer de fuentes de respaldo, provocando sustituciones inesperadas. | Instala un conjunto mínimo de fuentes comunes (Arial, Times New Roman) en el servidor. |

---

## Ampliando la solución

Ahora que puedes **capturar advertencias de sustitución de fuentes**, quizás quieras:

* **Registrar advertencias en un archivo** – reemplaza `System.out.println` con un logger como SLF4J.
* **Lanzar una excepción** – útil en pipelines automatizados donde una fuente faltante debe hacer fallar la compilación:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Instalar automáticamente fuentes faltantes** – descarga el TTF/OTF requerido en tiempo de ejecución y añádelo al `GraphicsEnvironment` de Java. Es un escenario más avanzado, pero totalmente posible.

---

## Diagrama (opcional)

![Diagrama de flujo de captura de advertencias de sustitución de fuentes mostrando LoadOptions → WarningCallback → salida de consola](capture-font-substitution-warnings-diagram.png)

*Texto alternativo:* “Diagrama de flujo de captura de advertencias de sustitución de fuentes que ilustra cómo Aspose.Words dirige las advertencias de fuentes faltantes a una devolución de llamada personalizada.”

---

## Conclusión

Acabamos de cubrir cómo **capturar advertencias de sustitución de fuentes** y **detectar fuentes faltantes** al cargar documentos Word con Aspose.Words for Java. Configurando un objeto `LoadOptions` e implementando un pequeño `IWarningCallback`, obtienes total visibilidad del proceso de sustitución de fuentes, lo que te permite registrar, reemplazar o abortar ante tipografías faltantes.

En resumen: establece la devolución de llamada, filtra por `SUBSTITUTED_FONT`, carga el documento y maneja la salida según lo requiera tu aplicación. Desde aquí puedes expandir a frameworks de registro, verificaciones CI o incluso aprovisionamiento automático de fuentes.

¿Quieres ir más allá? Prueba:

* **Incrustar fuentes** directamente en el documento guardado (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` con `FontEmbeddingMode.EMBED_ALL`).
* **Generar un PDF** después de corregir fuentes, asegurando que la salida final se vea exactamente como se pretende.
* **Escanear una carpeta completa** de documentos en busca de fuentes faltantes y producir un informe resumido.

Eso es todo por ahora—¡feliz codificación, y que tus documentos siempre se rendericen con la tipografía correcta!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}