---
category: general
date: 2026-11-15
description: Apprenez à traduire du texte avec Google en C#. Ce tutoriel présente
  un exemple de Google Translate, la gestion de plusieurs langues et les meilleures
  pratiques.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: fr
lastmod: 2026-11-15
og_description: Comment traduire du texte avec Google en C# en utilisant un exemple
  complet de Google Translate. Suivez ce tutoriel pour traduire plusieurs langues
  en toute sécurité.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Comment traduire du texte avec l'API Google Translate en C# – tutoriel rapide
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Comment traduire du texte avec l'API Google Translate en C# – guide étape par
  étape
url: /fr/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment traduire du texte avec l'API Google Translate en C# – guide étape par étape

Si vous avez besoin de **comment traduire du texte** dans une application .NET, l'API Google Cloud Translation offre une solution fiable et indépendante de la langue. Dans ce tutoriel, vous verrez un **exemple Google Translate** qui traduit une chaîne simple, s'étend à **traduire plusieurs langues**, et suit les meilleures pratiques pour les clés API et la gestion des erreurs.

Vous repartirez avec un programme console C# prêt à l'exécution, une compréhension claire de **translate text with Google**, et la confiance nécessaire pour adapter le code à des projets plus importants.

## Ce que couvre ce tutoriel

* Configurer un projet Google Cloud et obtenir une clé API.  
* Installer le package NuGet `Google.Cloud.Translation.V2`.  
* Écrire du code propre et réutilisable qui **how to translate text** en utilisant le SDK officiel.  
* Étendre la solution pour **translate multiple languages** en un seul appel.  
* Pièges courants et conseils pour des implémentations de qualité production.

### Prérequis

* .NET 6.0 SDK ou version ultérieure (le code se compile avec .NET Core et .NET Framework).  
* Un compte Google Cloud avec l'**API Cloud Translation** activée.  
* Familiarité de base avec C# et les applications console.  

---

## Étape 1 : Installer la bibliothèque cliente Google Cloud Translation

La bibliothèque cliente officielle abstrait les appels HTTP et gère l'authentification pour vous.

```bash
dotnet add package Google.Cloud.Translation.V2
```

L'exécution de la commande ajoute le package `Google.Cloud.Translation.V2` à votre projet, vous donnant accès à la classe `TranslationClient` utilisée tout au long de ce guide.

> **Pourquoi cette étape est importante** – Utiliser le SDK évite la construction manuelle des requêtes, réduit les bugs, et garantit que vous êtes aligné avec la dernière version de l'API de Google.

## Étape 2 : Créer un assistant de traduction réutilisable

Encapsuler la logique de traduction dans une classe statique rend le code réutilisable et isole la gestion de la clé API.

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Pourquoi nous retournons un dictionnaire** – Lorsque vous devez **translate multiple languages**, organiser les résultats par code de langue simplifie le traitement en aval.

## Étape 3 : Construire l'application console qui utilise l'assistant

Ci-dessous se trouve un fichier complet `Program.cs` qui démontre à la fois une traduction d'un texte unique et une traduction par lots.

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**Sortie console attendue**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **Pourquoi les blocs try/catch ?** – Les erreurs réseau, les limites de quota ou une clé API invalide génèrent des exceptions. Les gérer gracieusement améliore l'expérience utilisateur et maintient votre application stable.

## Étape 4 : Sécuriser votre clé API

Intégrer en dur la clé API, comme montré ci-dessus, est acceptable pour une démonstration rapide mais pas pour la production. Suivez ces pratiques :

* Stocker la clé dans une variable d'environnement (`GOOGLE_API_KEY`) et la lire à l'exécution :
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Utiliser les **Google Application Default Credentials** au lieu d'une clé API lors de l'exécution sur Google Cloud (App Engine, Cloud Run, etc.).
* Restreindre la clé à l'API Translation dans la console Google Cloud et limiter son utilisation à des adresses IP ou référents spécifiques.

## Étape 5 : Étendre la solution pour des scénarios réels

### Gestion de la détection de langue

Si vous devez connaître la langue source, l'objet de réponse contient `DetectedSourceLanguage` :

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Traduction de documents volumineux

L'API prend en charge jusqu'à 30 KB par requête. Pour des textes plus longs, divisez le contenu en morceaux, traduisez chaque morceau, puis concaténez les résultats. Conservez les limites de phrases intactes pour éviter des formulations maladroites.

### Limitation du débit et quotas

Google applique des limites de requêtes par minute. Mettez en œuvre une politique de nouvelle tentative avec un back‑off exponentiel pour respecter les limites de quota et éviter les erreurs `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Questions fréquentes et cas limites

**Q : Puis-je traduire une page HTML entière ?**  
R : Oui. Utilisez le paramètre `Format` (`"text"` ou `"html"`) lors de l'appel à `TranslateText`. Le SDK expose cela via la surcharge de `TranslateText` qui accepte un `TranslateTextRequest`.

**Q : Que se passe-t-il si une langue n’est pas prise en charge ?**  
R : L'API renvoie une erreur. Validez les codes de langue par rapport à la liste renvoyée par `client.ListSupportedLanguages()` avant d'effectuer une requête.

**Q : L'API facture‑t‑elle par caractère ?**  
R : Google facture par caractère traduit. Estimez les coûts en utilisant la page de tarification et envisagez de mettre en cache les traductions fréquentes.

---

## Conclusion

Vous savez maintenant **how to translate text** en C# en utilisant l'API officielle Google Translate. Le tutoriel a couvert un **Google translate example**, a démontré **translate multiple languages**, et a mis en avant des pratiques prêtes pour la production telles que la sécurité des clés API et la gestion des erreurs. En réutilisant l'assistant `Translator`, vous pouvez intégrer la traduction dans n'importe quel service .NET, application de bureau ou microservice.

**Prochaines étapes**

- Explorez le **Google Translate tutorial** pour des fonctionnalités avancées comme les glossaires et les modèles personnalisés.  
- Combinez ce code avec ASP.NET Core pour créer une API web multilingue.  
- Expérimentez la traduction par lots de fichiers CSV pour automatiser les pipelines de localisation.

Bonne programmation, et profitez de la création d'applications accessibles mondialement !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment enregistrer un document Word traduit en C# avec Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Traduire une chaîne en espagnol en C# avec Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}