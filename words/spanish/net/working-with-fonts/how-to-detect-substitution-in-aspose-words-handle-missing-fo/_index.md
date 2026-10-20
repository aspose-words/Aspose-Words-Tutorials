---
category: general
date: 2026-04-24
description: Cómo detectar la sustitución de fuentes faltantes en Aspose.Words usando
  C#. Esta guía le muestra cómo manejar fuentes faltantes de manera confiable con
  advertencias de FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: es
og_description: Cómo detectar la sustitución de fuentes faltantes en Aspose.Words
  con C#. Aprende a manejar fuentes faltantes usando advertencias de FontSettings.
og_title: Cómo detectar la sustitución en Aspose.Words – Guía completa
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Cómo detectar la sustitución en Aspose.Words – Gestionar fuentes faltantes
url: /es/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo detectar sustitución en Aspose.Words – Manejar fuentes faltantes

¿Alguna vez te has preguntado **cómo detectar sustitución** cuando un documento intenta usar una fuente que no está instalada en tu servidor? Es un punto doloroso común, especialmente cuando generas PDFs o archivos Word en una canalización automatizada. La buena noticia es que Aspose.Words te brinda un gancho incorporado para detectar exactamente esa situación, y también puedes **manejar fuentes faltantes** de forma elegante.

En este tutorial recorreremos un ejemplo del mundo real que muestra **cómo detectar sustitución** a través del evento `FontSettings.Warning`, y explicaremos cómo **manejar fuentes faltantes** sin romper tu flujo de procesamiento. Al final tendrás un fragmento listo para ejecutar, una comprensión clara de por qué cada línea es importante y algunos consejos para evitar los errores típicos.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona en .NET Framework)  
- Aspose.Words for .NET (paquete NuGet `Aspose.Words`) – versión 23.11 o más reciente  
- Un documento de muestra que haga referencia a una fuente que no tienes instalada (p. ej., `MissingFont.docx`)  
- Visual Studio, VS Code o cualquier IDE de C# que prefieras  

No se requiere configuración adicional más allá de agregar el paquete NuGet.

---

## Cómo detectar sustitución con FontSettings

El núcleo de **cómo detectar sustitución** reside en el evento `FontSettings.Warning`. Cuando Aspose.Words no puede encontrar una fuente solicitada, genera una advertencia `WarningType.FontSubstitution`. Al suscribirte a este evento recibes una notificación en tiempo real, con el nombre de la fuente original y la fuente que se utilizó como alternativa.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Por qué funciona:**  
- `LoadOptions.FontSettings` indica a Aspose.Words que use el objeto `FontSettings` que acabas de crear.  
- Suscribirse a `Warning` te brinda un único lugar para monitorizar *todos* los problemas relacionados con fuentes, no solo las fuentes faltantes.  
- El filtro `WarningType.FontSubstitution` asegura que solo reaccionas al escenario exacto que te interesa – la esencia de **cómo detectar sustitución**.

### Salida esperada

Ejecutar el código anterior con un documento que haga referencia a una fuente inexistente imprimirá algo como:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Si el documento usa solo fuentes instaladas, la consola permanecerá silenciosa – una señal clara de que **cómo detectar sustitución** se completó sin falsas alarmas.

---

## Manejar fuentes faltantes de forma elegante

Detectar una sustitución es solo la mitad de la batalla; también necesitas una estrategia para **manejar fuentes faltantes** de modo que la salida final se vea como esperas. A continuación, tres enfoques prácticos que puedes combinar.

### 1. Proveer una carpeta de fuentes de respaldo

Aspose.Words puede buscar fuentes en directorios adicionales. Apuntándolo a una carpeta que contenga las fuentes más comunes que esperas, reduces la probabilidad de una sustitución por completo.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Por qué:** Cuando la fuente original falta, Aspose.Words ahora tiene un conjunto conocido de alternativas, lo que suele producir un resultado visual más predecible.

### 2. Reemplazar fuentes faltantes programáticamente

Si deseas control total, puedes reemplazar la fuente faltante con una específica después de detectarla.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Por qué:** Esto indica al motor exactamente qué fuentes probar, permitiéndote imponer la identidad corporativa o normas de accesibilidad.

### 3. Registrar y abortar (cuando la sustitución es inaceptable)

A veces una fuente faltante significa que el documento es inválido para tu caso de uso (p. ej., formularios legales). En ese escenario puedes lanzar una excepción tan pronto como ocurra una sustitución.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Por qué:** Un fallo inmediato evita errores posteriores, como tablas desalineadas o firmas rotas.

---

## Ejemplo completo – Todos los pasos combinados

A continuación tienes un programa listo para copiar y pegar que demuestra **cómo detectar sustitución** *y* varias formas de **manejar fuentes faltantes**. Siéntete libre de comentar las secciones que no necesites.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Qué esperar:**  
- Si `MissingFont.docx` hace referencia a una fuente que no está en la máquina, la consola imprimirá la advertencia de sustitución.  
- El `Processed.docx` guardado usará la fuente de respaldo que configuraste (o la predeterminada de la biblioteca).  
- No aparecerán excepciones no controladas a menos que abortes deliberadamente ante una sustitución.

---

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| *¿Qué pasa si el documento contiene muchas fuentes faltantes?* | El evento de advertencia se dispara para **cada** sustitución, por lo que verás varias líneas. Puedes agregarlas a una lista para generar un informe resumido. |
| *¿Funciona con la conversión a PDF?* | Absolutamente. Las mismas `FontSettings` se respetan cuando llamas a `doc.Save("out.pdf")`. La advertencia de sustitución sigue disparándose, permitiéndote verificar la fidelidad visual del PDF. |
| *¿Puedo detectar sustitución después de que el documento ya está cargado?* | No directamente. La advertencia se genera **durante** la carga o el guardado. Si necesitas análisis posterior a la carga, captura las advertencias en una colección durante la fase de carga. |
| *¿Qué pasa con fuentes personalizadas incrustadas en el DOCX?* | Las fuentes incrustadas se consideran presentes, por lo que no ocurre sustitución. Si la fuente incrustada está corrupta, Aspose.Words aún genera una advertencia, que puedes capturar de la misma manera. |
| *¿Hay impacto en el rendimiento?* | Mínimo. La comprobación de advertencias es ligera; el costo real está en cargar el documento. Añadir una carpeta de fuentes puede aumentar ligeramente el tiempo de búsqueda, pero solo en la primera carga. |

---

## Consejos profesionales y errores comunes a evitar

- **Consejo pro:** Siempre establece `recursive: true` al apuntar a una carpeta con muchas fuentes; de lo contrario se ignoran las subcarpetas.  
- **Cuidado con:** La sensibilidad a mayúsculas en Linux. Los nombres de fuentes no distinguen mayúsculas en Windows, pero sí en Linux, así que usa el nombre exacto o agrega ambas variantes.  
- **Recuerda:** Si ejecutas en un entorno contenedorizado, asegúrate de que la carpeta de fuentes forme parte de la imagen o esté montada en tiempo de ejecución.  
- **Tip:** Almacena las advertencias en un `List<string>` si necesitas presentar un resumen a los usuarios finales o registrarlas en un sistema de monitoreo.  

---

## Conclusión

Hemos cubierto **cómo detectar sustitución** de fuentes faltantes en Aspose.Words, te hemos mostrado varias formas de **manejar fuentes faltantes**, y te hemos proporcionado un ejemplo completo y ejecutable que puedes incorporar a cualquier proyecto .NET. Al aprovechar el evento `FontSettings.Warning` obtienes visibilidad en tiempo real de los problemas de fuentes, y con carpetas de respaldo o reglas de sustitución explícitas mantienes tu salida exactamente como esperas.

¿Listo para el siguiente paso? Prueba a extender la solución para incrustar automáticamente la fuente de respaldo en el PDF generado, o conecta el manejador de advertencias a un servicio de registro centralizado para canalizaciones de documentos a gran escala. Los patrones que discutimos hoy—detección basada en eventos, respaldo elegante y manejo explícito de errores—se aplican a muchas otras APIs de Aspose, así que ahora estás preparado para afrontar desafíos relacionados con fuentes en cualquier contexto.

¿Tienes más preguntas sobre el manejo de fuentes, la conversión a PDF o trucos de Aspose.Words? ¡Deja un comentario abajo y feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}