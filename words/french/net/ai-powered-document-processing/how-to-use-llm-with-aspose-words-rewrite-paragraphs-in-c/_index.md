---
category: general
date: 2026-05-04
description: Comment utiliser les LLM pour éditer des documents avec Aspose – apprenez
  à remplacer le texte d’un paragraphe, à vous connecter à un LLM local et à réécrire
  le texte à l’aide de l’IA.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: fr
og_description: Comment utiliser un LLM pour éditer des documents avec Aspose. Ce
  guide montre comment se connecter à un LLM local, remplacer le texte d’un paragraphe
  et réécrire le texte à l’aide de l’IA.
og_title: Comment utiliser LLM avec Aspose.Words – Réécrire des paragraphes en C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Comment utiliser LLM avec Aspose.Words – Réécrire des paragraphes en C#
url: /fr/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment utiliser LLM avec Aspose.Words – Réécrire des paragraphes en C#

Vous êtes-vous déjà demandé **comment utiliser LLM** pour peaufiner un document Word sans l’ouvrir manuellement ? Vous n’êtes pas le seul. De nombreux développeurs se heurtent à un mur lorsqu’ils doivent *remplacer le texte d’un paragraphe* de façon programmatique mais ne disposent pas d’un flux de travail propre basé sur l’IA.  

Dans ce tutoriel, nous allons connecter un modèle de langage de grande taille local, lui fournir un extrait d’un fichier `.docx`, lui demander de **réécrire le texte avec l’IA**, puis enregistrer le document mis à jour — le tout avec Aspose.Words. À la fin, vous disposerez d’une application console C# prête à l’emploi qui démontre l’ensemble du pipeline.

> **Ce que vous obtiendrez :** un exemple complet et exécutable, des explications pour chaque étape, des astuces pour les cas limites, et des idées pour étendre la solution.

## Ce dont vous avez besoin

- **.NET 6+** (ou .NET Framework 4.7.2 – le code fonctionne dans les deux environnements)
- **Aspose.Words for .NET** (package NuGet `Aspose.Words`)
- Un **serveur LLM local** exposant un simple endpoint HTTP `/generate` (par ex. Ollama, LMStudio, ou un service Flask personnalisé)
- Une connaissance de base du C# et du code client HTTP  

Aucun SDK supplémentaire n’est requis ; tout le reste vit dans le code que nous écrirons ensemble.

## Étape 1 : Comment utiliser LLM pour remplacer le texte d’un paragraphe

La première chose à faire est d’identifier le paragraphe que nous voulons modifier. Aspose.Words rend cela très simple en exposant un modèle d’objets riche.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Pourquoi c’est important :**  
Sélectionner le bon nœud empêche d’écraser accidentellement des titres ou des tableaux. En utilisant l’approche **replace paragraph text**, nous conservons la structure du document tout en ne touchant que le contenu qui nous intéresse.

> **Astuce :** Si votre document comporte des sections de longueur variable, utilisez `document.GetChildNodes(NodeType.Paragraph, true)` et LINQ pour localiser un paragraphe par son texte ou son style.

## Étape 2 : Connecter à un endpoint LLM local

Maintenant que nous avons le texte, nous devons l’envoyer au LLM. L’exemple utilise une classe d’enveloppe simple `LocalLargeLanguageModel` qui masque la plomberie HTTP. Vous pouvez la remplacer par des appels `HttpClient` si vous le préférez.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Pourquoi nous nous connectons ainsi :**  
Une configuration **connect to local llm** élimine la latence, garde les données sur site et évite les coûts d’API. L’enveloppe rend également le code ultérieur plus lisible, nous permettant de nous concentrer sur la logique **rewrite text using ai**.

## Étape 3 : Réécrire le texte avec l’IA via Aspose.Words

Avec le texte du paragraphe en main et le LLM prêt, nous construisons une invite qui indique exactement au modèle ce que nous voulons — réécrire dans un ton formel. Vous pouvez ajuster l’invite pour d’autres styles (amical, technique, etc.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Pourquoi cela fonctionne :**  
Les LLM sont pilotés par des invites ; fournir des instructions explicites (“Rewrite … in a formal tone”) donne des résultats cohérents. L’étape **rewrite text using ai** est le cœur du tutoriel – elle montre comment l’IA peut être intégrée directement dans les flux de travail de documents.

## Étape 4 : Modifier le document et enregistrer les changements

Nous remplaçons maintenant les runs originaux par le nouveau contenu. Aspose.Words stocke le texte dans des objets `Run`, donc les vider d’abord évite les artefacts de formatage résiduels.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Note sur les cas limites :**  
Si le paragraphe original contenait un formatage mixte (gras, italique) vous voudrez peut‑être préserver les styles. Dans ce cas, créez un nouveau `Run`, copiez les paramètres `Font` d’origine, puis affectez son `Text` à `revisedText`.

## Exemple complet fonctionnel

Voici le programme complet que vous pouvez copier‑coller dans un projet console. N’oubliez pas d’installer le package NuGet Aspose.Words d’abord (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Résultat attendu

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Ouvrez `output.docx` – vous verrez que le troisième paragraphe affiche maintenant la version polie.

## Questions fréquentes & Pièges

| Question | Réponse |
|----------|--------|
| **Et si mon LLM renvoie du JSON avec des champs supplémentaires ?** | Ajustez `GenerateText` pour désérialiser la propriété correcte ou analysez la réponse manuellement. |
| **Puis‑je traiter plusieurs paragraphes à la fois ?** | Oui – parcourez `document.FirstSection.Body.Paragraphs` et appliquez la même logique d’invite, éventuellement en ajoutant un indice de paragraphe à l’invite pour le contexte. |
| **Mon serveur LLM utilise une authentification ?** | Ajoutez un en‑tête au `HttpClient` avant le POST : `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Le formatage est perdu après le remplacement.** | Conservez les paramètres `Run.Font` d’origine : créez un nouveau `Run`, copiez `originalRun.Font.Clone()`, puis définissez son `Text`. |
| **Le LLM renvoie parfois des chaînes vides.** | Implémentez un fallback – si `revisedText.Trim().Length == 0`, conservez le texte original ou réessayez avec une invite plus simple. |

## Étendre la solution

Maintenant que vous avez maîtrisé **how to use llm** pour un seul paragraphe, envisagez les étapes suivantes :

- **Traitement par lots :** Parcourez chaque paragraphe et réécrivez‑le dans un style choisi (par ex. “rendre tout le texte concis”).  
- **Réécriture sensible au style :** Transmettez le nom du style du paragraphe original dans l’invite afin que le LLM respecte les titres vs le corps du texte.  
- **Intégration à une pipeline CI :** Automatisez le polissage de documents dans le cadre d’un processus de génération de documentation.  
- **Invites alternatives :** Essayez “summarize this paragraph” ou “translate this paragraph to Spanish” pour explorer toute la puissance de **rewrite text using ai**.

## Conclusion

Nous avons parcouru l’ensemble du flux **how to use llm** avec Aspose.Words : charger un document, **connect to local llm**, extraire un paragraphe, **rewrite text using ai**, **replace paragraph text**, puis enregistrer le résultat. Le code est autonome, fonctionne immédiatement, et montre une façon concrète de combiner IA et automatisation de documents traditionnelle.

Essayez, ajustez les invites, et laissez

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}