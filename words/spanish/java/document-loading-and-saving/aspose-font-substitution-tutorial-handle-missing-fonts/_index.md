---
category: general
date: 2026-05-04
description: El tutorial de sustitución de fuentes de Aspose muestra cómo manejar
  fuentes faltantes en Java mediante callbacks de advertencia y LoadOptions para una
  carga de documentos fiable.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: es
og_description: El tutorial de sustitución de fuentes de Aspose explica cómo manejar
  fuentes faltantes en Java, capturar eventos de sustitución y mantener sus documentos
  con el aspecto correcto.
og_title: Tutorial de sustitución de fuentes Aspose – Manejar fuentes faltantes
tags:
- Aspose.Words
- Java
- Font Management
title: Tutorial de sustitución de fuentes Aspose – Manejar fuentes faltantes
url: /es/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial de sustitución de fuentes Aspose – Manejo de fuentes faltantes

¿Alguna vez necesitaste un **aspose font substitution tutorial** porque un DOCX que cargas de repente se ve mal? No estás solo—las fuentes faltantes son una fuente furtiva de errores que pueden convertir un informe perfectamente formateado en un desastre confuso. La buena noticia es que Aspose.Words te ofrece una forma limpia de **handle missing fonts** antes de que rompan tu diseño.

En esta guía recorreremos un ejemplo completo, listo‑para‑ejecutar en Java que captura advertencias de sustitución de fuentes, explica por qué cada pieza es importante y te muestra cómo verificar el resultado. Al final sabrás exactamente cómo mantener tus documentos con un aspecto impecable incluso cuando las tipografías originales no estén en la máquina.

## Lo que aprenderás

- Cómo registrar un `IWarningCallback` personalizado que escuche eventos `FONT_SUBSTITUTION`.  
- Por qué usar `LoadOptions` es el enfoque recomendado para un manejo fiable de fuentes.  
- Formas de probar la solución con un documento deliberadamente dañado.  
- Trampas comunes (p. ej., olvidar establecer el callback) y soluciones rápidas.  

**Prerequisites**: Java 8+ instalado, una licencia válida de Aspose.Words for Java (o la evaluación gratuita), y un IDE básico como IntelliJ o Eclipse. No se necesitan otras bibliotecas externas.

---

![Diagrama del tutorial de sustitución de fuentes Aspose](https://example.com/images/font-substitution-diagram.png "Aspose font substitution tutorial diagram")

## Paso 1 – Definir un Callback de Advertencia para Capturar Sustituciones  

Lo primero que hace Aspose.Words cuando no puede encontrar una fuente solicitada es disparar un evento `WarningInfo`. Implementando `IWarningCallback` puedes registrar, mostrar o incluso abortar la carga si lo prefieres.

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**Why this matters** – Sin un callback nunca sabrías que Aspose sustituyó *Arial* por *Liberation Sans* (o cualquier fuente de respaldo que eligió). Ese intercambio silencioso puede provocar desplazamientos de diseño, especialmente en tablas o diseños de varias columnas.

---

## Paso 2 – Adjuntar el Callback a `LoadOptions`

`LoadOptions` es el centro neurálgico de todo lo que influye en cómo se lee un documento. Al conectar el callback aquí garantizas que **cualquier** documento cargado con estas opciones activará tu lógica de advertencia.

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**Tip** – Si planeas cargar varios documentos en lote, reutiliza la misma instancia de `LoadOptions`. Ahorras sobrecarga de creación de objetos y mantienes tu registro consistente.

---

## Paso 3 – Cargar un Documento que Puede Necesitar Sustitución de Fuentes  

Ahora leemos realmente un archivo del que sabemos que le falta una fuente. Reemplaza `YOUR_DIRECTORY` con la carpeta que contiene tus archivos de prueba.

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

Cuando el cargador encuentra un glifo que no puede renderizar, el callback del **Paso 1** imprime un mensaje amigable en la consola. Por ejemplo:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**Edge case** – Si el documento contiene fuentes *embedded*, Aspose usará esas primero y omitirá la advertencia. Ese es el comportamiento esperado; solo ves advertencias para fuentes realmente ausentes.

---

## Paso 4 – Guardar el Documento (Ahora con Fuentes Sustituidas)

Después de que la carga termina, Aspose ya ha intercambiado internamente las fuentes faltantes. Guardar el documento preserva la sustitución, de modo que la salida se vea exactamente como lo viste en la consola.

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Abre `loaded.docx` en Word o LibreOffice y verás el diseño sin cambios, aunque la fuente original no esté instalada en tu máquina.

---

## Paso 5 – Verificar el Resultado Programáticamente (Opcional)

Si deseas estar totalmente seguro de que no se colaron sustituciones inesperadas, puedes consultar la tabla de fuentes del documento después de la carga.

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

La salida debería contener la fuente de respaldo (p. ej., *Arial*) en lugar de la que falta. Esto es útil para pipelines automatizados donde necesitas garantizar que el PDF o DOCX final cumpla con los requisitos de marca.

---

## Consejos Pro y Errores Comunes

- **Pro tip:** Establece `loadOptions.setFontSettings(new FontSettings())` si necesitas apuntar a una carpeta de fuentes personalizada antes de cargar. Esto reduce la cantidad de sustituciones.  
- **Watch out for:** Olvidar llamar a `setWarningCallback`. El código seguirá ejecutándose, pero perderás los mensajes diagnósticos cruciales.  
- **Performance note:** Cargar documentos grandes con muchas fuentes faltantes puede generar muchísimas advertencias. Considera limitar la salida o escribir a un archivo de registro en lugar de `System.out`.  
- **What if you need to abort on substitution?** Reemplaza la llamada `System.out.println` por `throw new RuntimeException(info.getDescription())` dentro del callback. Eso fuerza que la carga falle, lo cual es útil en escenarios de cumplimiento estricto.

---

## Preguntas Frecuentes

**Q: ¿Esto funciona con formatos PDF o de imagen?**  
A: El callback de advertencia es específico de la fase de carga de formatos de procesamiento de Word (`.docx`, `.doc`, `.rtf`, etc.). La renderización de PDF usa una canalización diferente, pero aún puedes capturar advertencias relacionadas con fuentes mediante `PdfLoadOptions`.

**Q: ¿Puedo sustituir una fuente específica por otra de mi elección?**  
A: Sí. Crea un objeto `FontSettings`, llama a `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")` y asígnalo a `loadOptions.setFontSettings(fontSettings)`.

**Q: ¿El callback es thread‑safe?**  
A: La implementación predeterminada no está sincronizada. Si cargas documentos en paralelo, asegúrate de que tu implementación del callback maneje el acceso concurrente (p. ej., usando `ConcurrentLinkedQueue` para el registro).

---

## Conclusión

Ahora tienes un **aspose font substitution tutorial** completo que muestra cómo **handle missing fonts** de forma elegante en Java. Definiendo un `IWarningCallback` personalizado, adjuntándolo a `LoadOptions` y guardando el documento, mantienes tu salida consistente sin importar qué fuentes estén instaladas en el equipo host.  

A partir de aquí podrías explorar:

- Tablas de sustitución de fuentes personalizadas para reemplazos compatibles con la marca.  
- Integrar el registrador de advertencias con SLF4J o Log4j para diagnósticos de nivel producción.  
- Extender el callback para recopilar estadísticas a lo largo de un lote de documentos.

Pruébalo, ajusta las fuentes de respaldo y permite que tus documentos sigan luciendo hermosos incluso cuando las tipografías originales desaparezcan. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}