---
category: general
date: 2026-02-13
description: Convertir PNG en Base64 en C# rapidement – apprenez comment encoder une
  image en base64, intégrer une image en base64 dans du HTML, et copier un flux en
  mémoire pour les projets web.
draft: false
keywords:
- convert png to base64
- base64 encode image
- embed image html base64
- image stream to base64
- copy stream to memory
language: fr
og_description: Convertir PNG en Base64 en C# rapidement. Ce tutoriel montre comment
  encoder une image en base64, intégrer une image en base64 dans le HTML et copier
  le flux en mémoire.
og_title: Convertir PNG en Base64 en C# – Guide complet
tags:
- C#
- image-processing
- data-uri
title: Convertir PNG en Base64 en C# – Guide complet
url: /fr/net/basic-conversions/convert-png-to-base64-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert PNG to Base64 in C# – Guide complet

Vous avez déjà eu besoin de **convertir PNG en Base64** sans savoir par où commencer ? Vous n'êtes pas seul ; de nombreux développeurs rencontrent ce problème lorsqu'ils essaient d'intégrer des images directement dans du HTML ou du CSS. La bonne nouvelle, c’est que la solution est assez simple une fois que vous connaissez les bonnes étapes.

Dans ce tutoriel, nous passerons en revue un exemple complet et exécutable qui **base64 encode image** les données, vous montre comment **embed image html base64** via un data‑URI, et explique même la meilleure façon de **copy stream to memory** sans fuite de ressources. À la fin, vous disposerez d’un extrait réutilisable que vous pourrez insérer dans n’importe quel projet .NET.

## Ce que vous allez apprendre

- Comment vérifier l’extension d’un fichier de manière insensible à la casse.  
- Le modèle le plus sûr pour transformer un **image stream to base64** en utilisant `MemoryStream`.  
- Construire un data‑URI correct que les navigateurs comprennent.  
- Nettoyer le flux original afin que votre application reste légère.  

Aucune bibliothèque externe n’est requise — uniquement les classes BCL fournies avec .NET. Si vous maîtrisez les bases de C# et avez déjà un projet qui gère les téléchargements de fichiers, vous êtes prêt à partir.

---

![Diagramme montrant le flux d’un fichier PNG vers un data‑URI Base64 – conversion png en base64](https://example.com/convert-png-to-base64-diagram.png "exemple de conversion png en base64")

## Convert PNG to Base64 – Étape par étape

Ci‑dessous, nous décomposons le processus en cinq étapes logiques. Chaque en‑tête reflète une partie du puzzle, ce qui facilite la localisation de la section exacte dont vous avez besoin (et pour les assistants IA).

### Étape 1 : Vérifier que la ressource est un PNG (insensible à la casse)

Avant de gaspiller de la mémoire, nous confirmons que le fichier entrant est bien un PNG. Le drapeau `StringComparison.OrdinalIgnoreCase` gère toute combinaison d’extensions en majuscules ou minuscules.

```csharp
// Step 1: Verify that the resource is a PNG image (case‑insensitive)
if (args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Continue with conversion...
}
else
{
    // Not a PNG – you might log or throw here
    throw new InvalidOperationException("Only PNG files are supported.");
}
```

*Pourquoi c’est important :* Tenter d’encoder un fichier qui n’est pas une image (ou un JPEG) comme PNG pourrait corrompre le résultat et casser le data‑URI que vous intégrerez plus tard.

### Étape 2 : Copier le flux en mémoire

Le `Stream` entrant (peut‑être provenant d’un gestionnaire d’upload) doit être entièrement lu. Utiliser une instruction `using var` garantit que le tampon est automatiquement libéré, gardant le **copy stream to memory** propre.

```csharp
using var memory = new MemoryStream();
args.Stream.CopyTo(memory);
```

*Astuce :* Si vous traitez des fichiers très volumineux, envisagez `CopyToAsync` avec une taille de tampon raisonnable pour éviter de bloquer les threads.

### Étape 3 : Encoder l’image en Base64

Maintenant que les octets de l’image sont dans `memory`, nous pouvons les transformer en chaîne Base64. C’est le cœur du **base64 encode image**.

```csharp
// Step 3: Encode the buffered bytes as a Base64 string
string base64Data = Convert.ToBase64String(memory.ToArray());
```

*Que se passe‑t‑il ?* `Convert.ToBase64String` prend un tableau d’octets et renvoie la représentation textuelle que les navigateurs peuvent décoder pour retrouver les données binaires.

### Étape 4 : Construire un Data‑URI pour HTML/CSS

Un data‑URI vous permet d’intégrer l’image directement dans le balisage, éliminant les requêtes HTTP supplémentaires. Le format est `data:[<mediatype>][;base64],<data>`.

```csharp
// Step 4: Build a data‑URI that embeds the PNG directly in HTML/CSS
args.ResourceFilePath = $"data:image/png;base64,{base64Data}";
```

Lorsque vous afficherez plus tard `args.ResourceFilePath` à l’intérieur d’une balise `<img src="...">`, le navigateur affichera le PNG instantanément.

### Étape 5 : Libérer le flux original

Comme l’image est maintenant représentée par le data‑URI, le `Stream` original n’est plus nécessaire. Le mettre à `null` aide le ramasse‑miettes à récupérer le socket ou le handle de fichier sous‑jacent.

```csharp
// Step 5: Release the original stream because the resource is now embedded
args.Stream = null;
```

*Cas particulier :* Si vous avez besoin du fichier original plus tard (par ex. pour le stocker sur disque), sautez cette étape et conservez une référence ailleurs.

---

## Exemple complet fonctionnel

Assembler toutes les pièces donne une méthode compacte que vous pouvez coller dans n’importe quelle classe qui traite des ressources téléchargées.

```csharp
using System;
using System.IO;

public class ResourceProcessor
{
    public void ProcessPng(ResourceArgs args)
    {
        // Verify extension (primary check)
        if (!args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
        {
            throw new InvalidOperationException("Only PNG files can be converted to Base64.");
        }

        // Copy the incoming stream into a memory buffer (copy stream to memory)
        using var memory = new MemoryStream();
        args.Stream.CopyTo(memory);

        // Encode the buffered bytes as a Base64 string (base64 encode image)
        string base64Data = Convert.ToBase64String(memory.ToArray());

        // Build a data‑URI that embeds the PNG directly in HTML/CSS (embed image html base64)
        args.ResourceFilePath = $"data:image/png;base64,{base64Data}";

        // Release the original stream because the resource is now embedded (image stream to base64)
        args.Stream = null;
    }
}

// Helper class to mimic incoming arguments
public class ResourceArgs
{
    public string ResourceFileExtension { get; set; }   // e.g., ".png"
    public Stream Stream { get; set; }                 // original file stream
    public string ResourceFilePath { get; set; }       // will hold the data‑URI
}
```

**Résultat attendu :** Après l’exécution de `ProcessPng`, `args.ResourceFilePath` contient une chaîne qui ressemble à :

```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Vous pouvez maintenant insérer cette chaîne directement dans une balise `<img>` :

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." alt="Converted PNG">
```

L’image apparaît immédiatement, sans aucun trafic réseau supplémentaire.

---

## Questions fréquentes & cas particuliers

### Et si le PNG est très volumineux ?

Les grandes images peuvent exploser l’utilisation de la mémoire parce que le fichier entier vit dans un `MemoryStream`. Pour des fichiers de plusieurs mégaoctets, envisagez de convertir le Base64 par morceaux ou de redimensionner l’image avant l’encodage.

### Puis‑je rendre cela asynchrone ?

Absolument. Remplacez `CopyTo` par `CopyToAsync` et marquez la méthode `async Task`. Cela libère le thread de requête ASP.NET pendant que l’I/O s’effectue.

```csharp
await args.Stream.CopyToAsync(memory);
```

### Cela fonctionne‑t‑il avec d’autres formats d’image ?

Le code est indépendant du format ; il suffit d’ajuster le type MIME dans le data‑URI (`image/jpeg`, `image/gif`, etc.) et de modifier la vérification d’extension en conséquence.

### Comment gérer les erreurs proprement ?

Enveloppez l’ensemble du bloc dans un `try/catch` et consignez l’exception. Si vous êtes dans une API web, renvoyez un 400 Bad Request avec un message explicite.

---

## Conclusion

Vous savez maintenant comment **convertir PNG en Base64** en C# du début à la fin. Le tutoriel a couvert la vérification du type de fichier, la copie sécurisée du flux en mémoire, l’exécution d’un **base64 encode image**, la construction d’un **embed image html base64** data‑URI correct, et le nettoyage des ressources.  

À partir d’ici, vous pouvez explorer le redimensionnement d’image à la volée, la mise en cache des data‑URIs générés, ou même la génération de placeholders SVG. Quelle que soit la direction que vous choisissez, le modèle présenté ci‑dessus constitue une base solide pour tout scénario où vous devez transformer un **image stream to base64** et l’intégrer directement dans le balisage.

Vous avez une variante de ce flux de travail ? Peut‑être travaillez‑vous avec WebAssembly ou Blazor — n’hésitez pas à partager vos expériences dans les commentaires. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}