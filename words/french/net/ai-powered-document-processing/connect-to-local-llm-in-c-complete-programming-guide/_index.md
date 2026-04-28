---
category: general
date: 2026-04-28
description: Connectez‑vous à un LLM local depuis C# et invitez le grand modèle de
  langage à charger un document Word, appelez le LLM local et réécrivez le texte automatiquement.
  Code étape par étape inclus.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: fr
og_description: Connectez-vous à un LLM local depuis C# et découvrez comment interroger
  un grand modèle de langage, charger un document Word, appeler le LLM local et réécrire
  le texte automatiquement en quelques minutes.
og_title: Se connecter à un LLM local en C# – Guide complet de programmation
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Se connecter à un LLM local en C# – Guide complet de programmation
url: /fr/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Se connecter à un LLM local en C# – Guide complet de programmation

Vous avez déjà eu besoin de **connecter à un llm local** depuis une application .NET et vous vous êtes demandé comment le faire communiquer avec un fichier Word ? Vous n'êtes pas seul. Dans ce guide, nous parcourrons l’ensemble du processus — connecter à un llm local, **prompt large language model**, charger un document Word, **call local llm**, et enfin **rewrite text automatically**. À la fin, vous disposerez d’un exemple exécutable qui transforme n’importe quel paragraphe en un ton formel sans aucune clé d’API externe.

## Ce que couvre ce tutoriel

Nous commencerons par installer les packages NuGet nécessaires, puis lancerons un point de terminaison LLM local simple (pensez à Ollama sur le port 11434). Ensuite, nous chargerons un fichier `.docx` avec Aspose.Words, enverrons un paragraphe au LLM, recevrons une version réécrite, et l’écrirons de nouveau dans le même document. Vous verrez également comment gérer les pièges courants — paragraphes nuls, libération asynchrone, et particularités d’encodage — afin que le code fonctionne en production, pas seulement en démonstration.

### Prérequis

- .NET 6.0 SDK ou version ultérieure (vous pouvez également utiliser .NET 8 si vous le souhaitez)
- Visual Studio 2022 ou VS Code avec l’extension C#
- **Aspose.Words for .NET** (l’essai gratuit fonctionne bien)
- Un LLM hébergé localement qui respecte le contrat `/api/generate` (par ex., Ollama, LMStudio)
- Familiarité de base avec async/await en C#

> **Conseil pro :** Si vous n’avez pas encore installé Ollama, exécutez `ollama serve` et récupérez un modèle avec `ollama pull llama3`. Le point de terminaison HTTP par défaut sera `http://localhost:11434/api/generate`.

---

## Étape 1 : Installer les packages requis

Tout d’abord, ajoutez les packages NuGet Aspose.Words et Aspose.Words.AI à votre projet.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Ces bibliothèques nous offrent la capacité de **load word document** et un léger wrapper pour **call local llm** sans créer manuellement des requêtes HTTP.

---

## Étape 2 : Se connecter au point de terminaison LLM local

Se connecter à un modèle hébergé localement est aussi simple que d’instancier `LocalLargeLanguageModel`. Le constructeur attend l’URL complète du point de terminaison de génération.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Pourquoi envelopper le point de terminaison dans une classe ? `LocalLargeLanguageModel` gère la sérialisation JSON, les nouvelles tentatives et les réponses en streaming pour vous—vous pouvez ainsi vous concentrer sur la logique du prompt au lieu de bricoler avec `HttpClient`.

---

## Étape 3 : Charger le document Word source

Ensuite, nous chargeons le document en mémoire. Aspose.Words prend en charge pratiquement tous les formats Word, ainsi `Document` analysera `input.docx` sans nécessiter l’installation d’Office.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Si vous devez travailler avec un flux (par ex., un fichier téléchargé via ASP.NET), remplacez simplement le chemin du fichier par un `MemoryStream` et passez‑le au constructeur `Document`.

---

## Étape 4 : Extraire le texte du paragraphe actuel

Nous utiliserons `DocumentBuilder` pour naviguer dans le document. Dans cet exemple nous réécrivons **the first paragraph**, mais vous pouvez itérer sur `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` pour en traiter plusieurs.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

L’opérateur `?.` empêche une `NullReferenceException` si le document se révèle vide. C’est l’un de ces **edge cases** qui piquent les débutants.

---

## Étape 5 : Demander au LLM de réécrire le paragraphe

Nous allons maintenant réellement **prompt large language model**. Le prompt est en anglais simple ; le wrapper l’enverra sous forme de JSON au point de terminaison local.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Pourquoi formuler la requête ainsi ? Les LLM répondent mieux à des instructions claires et à tâche unique. Ajouter un saut de ligne après les deux‑points sépare l’instruction du contenu, réduisant la probabilité que le modèle renvoie le prompt.

**Résultat attendu** – Si `originalParagraph` était `"Hey, what's up?"`, le LLM pourrait renvoyer :

> “Good day, how may I assist you?”

Vous pouvez vérifier le résultat en l’affichant :

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Étape 6 : Insérer le texte réécrit dans le document

Avec le nouveau texte en main, nous remplaçons l’ancien paragraphe. `DocumentBuilder.Writeln` écrit une nouvelle ligne et avance le curseur, ce qui est parfait pour ajouter. Si vous devez *remplacer* le même paragraphe, vous pouvez utiliser `docBuilder.CurrentParagraph.RemoveAllChildren()` avant d’écrire.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Les deux approches sont présentées afin que vous puissiez choisir celle qui correspond à votre flux de travail.

---

## Étape 7 : Enregistrer le document mis à jour

Enfin, nous persistons les modifications dans un nouveau fichier. Aspose.Words choisit automatiquement le format en fonction de l’extension du fichier.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Ouvrez `output.docx` dans Word, et vous verrez que le paragraphe est maintenant rédigé sur un ton formel.

---

## Exemple complet fonctionnel

Ci‑dessous se trouve le **programme complet et autonome**. Copiez‑collez‑le dans un projet console, restaurez les packages NuGet, et exécutez‑le — aucune configuration supplémentaire n’est requise au‑delà d’un LLM local en cours d’exécution.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Ce à quoi s’attendre lors de l’exécution

1. La console affiche les paragraphes original et réécrit.  
2. `output.docx` apparaît à côté de `input.docx`.  
3. L’ouverture du fichier montre le nouveau paragraphe formel inséré après l’original (ou remplacé, si vous avez choisi le code alternatif).

---

## Gestion des cas limites courants

| Situation | Solution |
|-----------|----------|
| **Paragraphe vide ou contenant uniquement des espaces** | Vérifiez `string.IsNullOrWhiteSpace` avant de demander (voir Étape 3). |
| **Le LLM renvoie une erreur ou une chaîne vide** | Enveloppez `PromptAsync` dans un `try/catch` et revenez au texte original. |
| **Plusieurs paragraphes nécessitent une réécriture** | Bouclez sur `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` et appliquez la même logique de prompt. |
| **Les gros documents entraînent de la latence** | Regroupez les paragraphes et envoyez‑les dans une seule requête (prompt jusqu’à 4 KB par appel). |
| **Les caractères non ASCII sont corrompus** | Assurez‑vous que le point de terminaison LLM utilise UTF‑8 (la plupart des modèles modernes le font). |

---

## Prochaines étapes et sujets associés

- **Prompt large language model** avec des instructions plus riches (par ex., guides de style, limites de longueur).  
- Utilisez **call local llm** dans une API web pour exposer l’automatisation de documents en tant que service.  
- Explorez **load word document** dans des flux parallèles pour des scénarios à haut débit.  
- Combinez cette approche avec **rewrite text automatically** pour la génération massive d’e‑mails ou la standardisation de rapports.  

Si vous souhaitez approfondir, consultez la documentation d’Aspose sur **document merging** et la référence API d’Ollama pour les paramètres d’échantillonnage personnalisés.

---

## Conclusion

Nous venons de vous montrer comment **connect to local llm** depuis C#, **prompt large language model**, **load word document**, **call local llm**, et **rewrite text automatically**—le tout dans une seule application console exécutable. Le modèle est extensible : changez le prompt, itérez sur les paragraphes, ou exposez la logique via un point de terminaison ASP.NET. L’idée principale est que les modèles IA locaux peuvent être intégrés étroitement aux bibliothèques classiques de traitement de documents, vous offrant une automatisation puissante sans jamais quitter votre environnement sur site de confiance.

Des questions sur le threading,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}