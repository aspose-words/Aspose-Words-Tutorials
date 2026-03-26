---
category: general
date: 2026-03-25
description: Crear modelo de IA personalizado para editar documentos Word – aprende
  cómo hacer el texto más formal, reemplazar el texto de un párrafo y reescribir un
  párrafo de Word usando Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: es
og_description: Crea un modelo de IA personalizado para editar documentos de Word.
  Aprende a hacer el texto más formal, reemplazar el contenido de los párrafos y reescribir
  un párrafo de Word usando Aspose.Words IA.
og_title: Crear modelo de IA personalizado – Editar párrafos de Word en Java
tags:
- Aspose.Words
- Java
- AI integration
title: Crear modelo de IA personalizado – Editar párrafos de Word en Java
url: /es/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear modelo de IA personalizado – Editar párrafos de Word en Java

¿Alguna vez necesitaste **crear modelo de IA personalizado** que pueda pulir un párrafo dentro de un archivo Word? Tal vez tienes un lote de contratos que suenan un poco demasiado informales, y te gustaría hacer el texto más formal con una sola línea de código. La buena noticia es que puedes hacer exactamente eso—sin servicios externos, sin SDKs pesados, solo Aspose.Words for Java y un endpoint compatible con OpenAI.

En este tutorial recorreremos cada paso necesario para **crear modelo de IA personalizado**, conectarlo a un servidor LLM local, y luego usarlo para *reemplazar el texto del párrafo* con una versión más formal. Al final tendrás un programa Java ejecutable que **edita párrafos con IA**, reescribe un párrafo de Word y guarda el resultado en disco. Sin rodeos, solo una solución práctica que puedes copiar y pegar en tu propio proyecto.

> **Lo que necesitarás**  
> • Java 17 o superior (el código compila con versiones anteriores, pero 17 es el punto óptimo)  
> • Aspose.Words for Java 23.9 (o la última versión)  
> • Un servidor LLM compatible con OpenAI en ejecución (p. ej., Ollama, LocalAI) escuchando en `http://localhost:8000/v1`  
> • Un documento Word de entrada (`input.docx`) colocado en una carpeta que controles  

Si te preguntas *por qué molestarse en crear un modelo personalizado* en lugar de llamar directamente a OpenAI, la respuesta es flexibilidad: controlas el endpoint, puedes cambiar de modelo sin modificar el código y mantienes las claves API fuera de tu repositorio de código. Vamos a sumergirnos.

---

## Crear modelo de IA personalizado – Configuración y puesta en marcha

Primero necesitamos indicar a Aspose.Words dónde reside nuestro LLM. La clase `AiModelEndpoint` contiene la URL y la clave API opcional. Como estamos usando un servidor local, la clave puede ser una cadena vacía, pero el parámetro es obligatorio.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Consejo profesional:** Si alguna vez cambias a un modelo alojado (p. ej., Azure OpenAI), solo cambia la URL y la clave—no se necesitan otros cambios de código.

---

## Cargar el documento Word

Ahora cargamos el archivo fuente en memoria. `Document` puede leer `.docx`, `.doc`, `.rtf` y muchos otros formatos, pero para este ejemplo nos quedamos con `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Asegúrate de que `YOUR_DIRECTORY` apunte a una carpeta real; de lo contrario obtendrás una `FileNotFoundException`. En una aplicación real podrías pasar la ruta como argumento de línea de comandos o leerla de un archivo de configuración.

---

## Inicializar el modelo de IA personalizado

Creamos un `AiModel` de tipo `CUSTOM` y le asignamos el endpoint que definimos antes. Esto indica a Aspose.Words que enrute todas las llamadas de IA a través de nuestro propio servidor.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Detrás de escena, Aspose.Words construye un pequeño cliente HTTP que se comunica con el LLM usando el esquema estándar de chat/completado de OpenAI. Por eso el endpoint debe ser *compatible con OpenAI*.

---

## Recuperar y reescribir el primer párrafo

Aquí es donde realmente **hacemos el texto más formal**. Obtendremos el primer párrafo, enviamos su texto sin procesar al modelo con un prompt, y recibimos la versión editada.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

El segundo argumento (`"Make it more formal"`) es la instrucción que le damos al modelo. Puedes reemplazarlo con cualquier directiva—**reemplazar texto del párrafo**, **resumir**, **traducir**, etc. El método devuelve una cadena simple, que más adelante insertaremos de nuevo en el documento.

> **Por qué funciona:** `editText` envía una carga JSON como `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. El LLM ve el párrafo original y la instrucción, y luego responde con el texto revisado.

---

## Reemplazar el contenido del párrafo original

Ahora **reemplazamos el texto del párrafo** dentro del modelo de objetos de Word. Eliminamos cualquier `Run` existente (las piezas de texto de bajo nivel) e insertamos un nuevo `Run` que contiene la cadena generada por IA.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Ten cuidado de no llamar a `firstParagraph.setText()`—ese método eliminaría cualquier formato. Usar `Run` preserva el estilo del párrafo (encabezado, viñeta, etc.) mientras se sustituyen los caracteres reales.

---

## Guardar el documento editado

Finalmente, escribimos el documento modificado de nuevo en disco. Puedes sobrescribir el archivo original o, como hacemos aquí, crear una copia nueva.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Cuando abras `output.docx` deberías ver que el primer párrafo suena considerablemente más formal. Si el LLM no siguió la instrucción a la perfección, puedes ajustar el prompt o probar una versión diferente del modelo.

---

## Ejemplo completo funcional

A continuación está el programa completo—cópialo en `LlmDemo.java`, ajusta las rutas y ejecútalo con `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Salida esperada:** Abre `output.docx` y verás el párrafo original transformado. Por ejemplo, una frase casual como “We’ll get the thing done soon.” podría convertirse en “We shall complete the task promptly.” La redacción exacta depende del modelo que estés usando.

---

## Preguntas comunes y casos límite

### ¿Qué pasa si mi documento tiene múltiples secciones?

El código anterior solo modifica el *primer* párrafo de la *primera* sección. Para **editar párrafos con IA** en todo el archivo, recorre `document.getSections()` y luego cada `section.getBody().getParagraphs()`. Recuerda omitir los párrafos vacíos, de lo contrario el LLM recibe una cadena vacía y no devuelve nada.

### ¿Cómo manejo párrafos grandes que superan los límites de tokens?

La mayoría de los LLM limitan la entrada a alrededor de 4 000 tokens. Si un párrafo es inusualmente largo, divídelo en fragmentos más pequeños antes de llamar a `editText`. Puedes reutilizar la misma instancia de `AiModel`; solo ten en cuenta los límites de velocidad en tu servidor local.

### ¿Puedo usar una instrucción diferente, como “summarize” o “translate to French”?

Absolutamente. El segundo argumento de `editText` es libre. Para un resumen podrías pasar `"Summarize in one sentence"`. Para traducción, `"Translate to French, keep the tone formal"` funciona igual de bien. Esta flexibilidad te permite **reemplazar el texto del párrafo** en muchos escenarios sin cambiar código.

### ¿El modelo preserva el estilo del párrafo (fuentes, colores)?

Como solo reemplazamos el `Run` dentro del mismo objeto `Paragraph`, los estilos existentes (nivel de encabezado, lista con viñetas, sangría) permanecen intactos. Si necesitas cambiar el estilo en sí, puedes manipular `Paragraph.getParagraphFormat()` después del reemplazo.

### ¿Qué pasa si mi servidor LLM requiere HTTPS con un certificado autofirmado?

`AiModelEndpoint` acepta una URL con `https://`. Si el certificado no es de confianza, deberás configurar el contexto SSL de Java para confiar en él, o ejecutar el servidor con un certificado válido. Esa configuración está fuera del alcance de este tutorial pero bien documentada en las guías de SSL para Java.

---

## Consejos para una integración lista para producción

| Tip | Why it matters |
|-----|----------------|
| **Cachear el endpoint** | Re‑crear `AiModelEndpoint` en cada solicitud añade sobrecarga. |
| **Ediciones por lotes** | Si tienes muchos párrafos, envíalos en una sola solicitud (p. ej., arreglo JSON) para reducir la latencia. |
| **Validar la salida del LLM** | Siempre verifica que la cadena devuelta no sea nula o vacía antes de insertarla. |
| **Registrar prompts y respuestas** | Útil para depuración y cumplimiento cuando estás reescribiendo texto legal. |
| **Retorno elegante** | Si el LLM está caído, recurre al párrafo original o a una reescritura heurística simple. |

---

## Conclusión

Te hemos mostrado cómo **crear modelo de IA personalizado** con Aspose.Words, conectarlo a un endpoint compatible con OpenAI, y luego **editar párrafos con IA** para **hacer el texto más formal**. Siguiendo los seis pasos—definir el endpoint, cargar el documento, inicializar el modelo,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}