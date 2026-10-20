---
category: general
date: 2026-05-01
description: Sube imágenes a la nube mientras conviertes un documento Word a markdown.
  Aprende cómo extraer imágenes de docx y almacenarlas en Azure Blob storage.
draft: false
keywords:
- upload images to cloud
- convert word to markdown
- extract images from docx
- convert docx to markdown
- store images azure blob
language: es
og_description: Sube imágenes a la nube mientras conviertes un documento de Word a
  markdown. Esta guía muestra cómo extraer imágenes de un docx y almacenarlas en Azure
  Blob Storage.
og_title: Subir imágenes a la nube al convertir Word a Markdown
tags:
- Aspose.Words
- C#
- Azure Blob Storage
title: Subir imágenes a la nube al convertir Word a Markdown
url: /es/net/programming-with-markdownsaveoptions/upload-images-to-cloud-when-converting-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Subir imágenes a la nube al convertir Word a Markdown

¿Alguna vez necesitaste **subir imágenes a la nube** mientras conviertes un archivo Word a markdown? No eres el único—los desarrolladores constantemente manejan la conversión de documentos y la gestión de recursos, y hacer ambas cosas en un flujo fluido puede sentirse como perseguir un objetivo en movimiento.  

¿La buena noticia? Con Aspose.Words puedes extraer cada imagen, gráfico o diagrama de un .docx, enviarlo directamente a Azure Blob Storage y dejar que el markdown generado haga referencia a esas URL en la nube en lugar de archivos locales. En este tutorial recorreremos todo el proceso, desde cargar el documento fuente hasta obtener un archivo markdown limpio que apunte a tu contenedor de Azure.

Al final de esta guía podrás **convertir docx a markdown**, **extraer imágenes de docx** y **almacenar imágenes Azure Blob**—todo con solo unas pocas líneas de C#. Sin herramientas externas, sin copiar‑pegar manual y, por supuesto, sin enlaces de imagen rotos.

## Lo que necesitarás

- **.NET 6.0** o posterior (el código funciona también en .NET Core y .NET Framework)  
- **Aspose.Words for .NET** (paquete NuGet `Aspose.Words`)  
- Una **cuenta de Azure Storage** con un contenedor (p. ej., `images`) y una clave de acceso compartido – necesitarás la cadena de conexión para subir archivos.  
- Un conocimiento básico de C# y async/await (opcional pero útil).  

Si ya tienes estas piezas en su lugar, genial—pasemos directamente a la solución. Si no, la sección “Prerequisites” al final te indicará los pasos rápidos de configuración.

## Paso 1: Configurar el ayudante de Azure Blob (Por qué es importante)

Antes de tocar el documento Word, necesitamos un pequeño ayudante que sepa cómo enviar un arreglo de bytes a Azure Blob Storage y devolver una URL pública. Esta abstracción mantiene la lógica de conversión limpia y facilita cambiar de proveedor de almacenamiento más adelante.

```csharp
using Azure;
using Azure.Storage.Blobs;
using Azure.Storage.Blobs.Models;

/// <summary>
/// Simple wrapper around Azure Blob Storage for uploading images.
/// </summary>
public class AzureBlobUploader
{
    private readonly BlobContainerClient _container;

    public AzureBlobUploader(string connectionString, string containerName)
    {
        var service = new BlobServiceClient(connectionString);
        _container = service.GetBlobContainerClient(containerName);
        _container.CreateIfNotExists(PublicAccessType.Blob);
    }

    /// <summary>
    /// Uploads the supplied image bytes and returns a publicly accessible URL.
    /// </summary>
    public async Task<string> UploadAsync(string fileName, byte[] content)
    {
        // Ensure the file name is safe for URLs.
        var safeName = Uri.EscapeDataString(fileName);
        var blob = _container.GetBlobClient(safeName);
        using var stream = new MemoryStream(content);
        await blob.UploadAsync(stream, overwrite: true);
        return blob.Uri.ToString(); // This is the URL we’ll embed in markdown.
    }
}
```

**¿Por qué este ayudante?**  
1. **Separación de responsabilidades** – el código de conversión a markdown se mantiene enfocado en el manejo del documento, no en los detalles HTTP.  
2. **Reutilización** – puedes llamar a `UploadAsync` desde cualquier otro lugar de tu aplicación (p. ej., para imágenes subidas por usuarios).  
3. **Preparación para el futuro** – cambiar a Amazon S3 o Google Cloud Storage solo requiere una nueva implementación de la misma interfaz.

> **Consejo profesional:** Configura el nivel de acceso del contenedor a `Blob` (público) solo si estás de acuerdo con que cualquiera pueda leer las imágenes. Para escenarios privados, genera tokens SAS por carga e incrusta esas URL en su lugar.

## Paso 2: Definir una devolución de llamada de guardado de recursos (El núcleo de Subir‑mientras‑conviertes)

Aspose.Words te permite interceptar cada recurso (imagen, gráfico, etc.) que normalmente se escribiría en disco al guardar un documento como markdown. Al proporcionar un `ResourceSavingCallback`, podemos subir cada recurso a Azure Blob y reemplazar el nombre de archivo local con la URL en la nube.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Callback that uploads each extracted image to Azure Blob Storage
/// and tells Aspose.Words to use the resulting URL instead of a file.
/// </summary>
public class CloudResourceSaver : IResourceSavingCallback
{
    private readonly AzureBlobUploader _uploader;

    public CloudResourceSaver(AzureBlobUploader uploader) => _uploader = uploader;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // args.ResourceFileName contains the default file name (e.g., image001.png)
        // args.ResourceStream gives us the raw bytes.
        var fileName = args.ResourceFileName;

        // Convert the stream to a byte[] for uploading.
        using var ms = new MemoryStream();
        args.ResourceStream.CopyTo(ms);
        var bytes = ms.ToArray();

        // NOTE: Aspose.Words calls this synchronously, so we block on the async upload.
        // In a real‑world service you might use .GetAwaiter().GetResult() or redesign.
        var uploadTask = _uploader.UploadAsync(fileName, bytes);
        var url = uploadTask.GetAwaiter().GetResult();

        // Tell Aspose.Words to use the cloud URL.
        args.ResourceFileName = url;

        // Prevent Aspose.Words from creating a local copy.
        args.AlreadyExists = true;
    }
}
```

**¿Qué está ocurriendo aquí?**  

- **Extract** – Aspose.Words nos da un stream para cada imagen.  
- **Upload** – Pasamos ese stream a `AzureBlobUploader`.  
- **Replace** – El escritor de markdown recibe la URL pública y la escribe en la sintaxis de imagen markdown (`![](https://…)`).  

Como establecemos `args.AlreadyExists = true`, no quedan archivos temporales que ensucien el sistema de archivos—una operación limpia y sin estado, perfecta para funciones serverless.

## Paso 3: Configurar las opciones de guardado de Markdown (Unir todo)

Ahora integramos la devolución de llamada en `MarkdownSaveOptions` de Aspose.Words. Los indicadores cruciales son `ExportImagesAsBase64 = false` (para obtener enlaces externos) y `ResourceSavingCallback = new CloudResourceSaver(uploader)`.

```csharp
using System;
using System.Threading.Tasks;
using Aspose.Words;
using Aspose.Words.Saving;

public class DocxToMarkdownConverter
{
    private readonly AzureBlobUploader _uploader;

    public DocxToMarkdownConverter(AzureBlobUploader uploader) => _uploader = uploader;

    /// <summary>
    /// Converts a .docx to markdown and uploads all images to Azure Blob.
    /// Returns the path to the generated markdown file.
    /// </summary>
    public async Task<string> ConvertAsync(string inputDocxPath, string outputMarkdownPath)
    {
        // Load the source document (convert word to markdown step starts here).
        var doc = new Document(inputDocxPath);

        // Set up the callback that will upload each image.
        var resourceSaver = new CloudResourceSaver(_uploader);

        // Configure markdown options.
        var mdOptions = new MarkdownSaveOptions
        {
            ExportImagesAsBase64 = false,           // Keep images as external links.
            ResourceSavingCallback = resourceSaver, // Hook that uploads to Azure.
            // Optional: you can tweak heading levels, code block fences, etc.
        };

        // Save the markdown file – Aspose.Words will invoke the callback for each image.
        doc.Save(outputMarkdownPath, mdOptions);

        // The method is synchronous because Aspose.Words API is sync.
        // Wrap in Task.Run if you need true async behavior.
        await Task.CompletedTask;
        return outputMarkdownPath;
    }
}
```

**¿Por qué desactivamos Base64?**  
Cuando `ExportImagesAsBase64` es true, Aspose incrusta cada imagen directamente en el markdown como un data URI. Eso anula el propósito de **subir imágenes a la nube** porque el archivo markdown se inflama y las imágenes permanecen ocultas al CDN. Al desactivarlo obtenemos enlaces externos limpios que apuntan a Azure Blob—exactamente lo que espera un generador de sitios estáticos moderno.

## Paso 4: Juntar todo – Una aplicación de consola mínima

A continuación tienes un programa de consola completo y listo para ejecutar. Reemplaza los marcadores de posición con tu cadena de conexión de Azure y el nombre del contenedor.

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    // 👉 Replace these with your own Azure storage details.
    private const string AzureConnectionString = "DefaultEndpointsProtocol=https;AccountName=YOUR_ACCOUNT;AccountKey=YOUR_KEY;EndpointSuffix=core.windows.net";
    private const string ContainerName = "images";

    static async Task Main(string[] args)
    {
        // Simple argument validation.
        if (args.Length != 2)
        {
            Console.WriteLine("Usage: dotnet run <input.docx> <output.md>");
            return;
        }

        var inputPath = args[0];
        var outputPath = args[1];

        // 1️⃣ Initialise the uploader.
        var uploader = new AzureBlobUploader(AzureConnectionString, ContainerName);

        // 2️⃣ Create the converter that knows how to upload while converting.
        var converter = new DocxToMarkdownConverter(uploader);

        // 3️⃣ Run the conversion.
        await converter.ConvertAsync(inputPath, outputPath);

        Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
        Console.WriteLine("🖼️  Images have been uploaded to Azure Blob and linked in the markdown.");
    }
}
```

### Salida esperada

Ejecutar el programa con `sample.docx` que contiene dos imágenes producirá:

- `output.md` que contiene sintaxis de imagen markdown como:

  ```markdown
  ![Image 1](https://myaccount.blob.core.windows.net/images/image001.png)
  ![Image 2

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}