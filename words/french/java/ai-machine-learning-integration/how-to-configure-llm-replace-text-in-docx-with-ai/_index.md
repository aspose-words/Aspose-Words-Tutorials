---
category: general
date: 2026-03-04
description: Comment configurer le LLM pour le Document AI et remplacer du texte dans
  un DOCX à l'aide de l'IA – guide étape par étape avec le code Java complet.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: fr
og_description: How to configure LLM for Document AI and replace text in DOCX using
  AI – complete guide with runnable Java code.
og_title: Comment configurer le LLM – Remplacer le texte d’un DOCX avec l’IA
tags:
- LLM
- Document AI
- Java
- DOCX
title: Comment configurer le LLM – Remplacer le texte dans un DOCX avec l'IA
url: /fr/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment configurer LLM – Remplacer du texte dans un DOCX avec l'IA

Vous vous êtes déjà demandé **comment configurer LLM** pour qu’il puisse modifier un fichier Word pour vous ? Vous n’êtes pas le seul. De nombreux développeurs se heurtent à un mur lorsqu’ils doivent remplacer programmétiquement une phrase dans un `.docx` sans ouvrir Microsoft Word. La bonne nouvelle ? Avec un LLM local et un petit wrapper Document AI, vous pouvez échanger du texte dans un fichier DOCX en quelques lignes de Java.

Dans ce tutoriel, nous parcourrons l’ensemble du processus : de la connexion au LLM, au chargement d’un DOCX, à l’utilisation de **Document AI** pour remplacer une phrase cible. À la fin, vous disposerez d’un exemple autonome, exécutable, que vous pourrez intégrer à n’importe quel projet Maven ou Gradle. Aucun clé d’API externe, aucun frais cloud — juste votre propre modèle écoutant sur `http://localhost:8080/v1`.

> **Gain rapide** : si vous avez déjà un LLM local (comme Llama 3 ou Mistral) exposant un endpoint compatible OpenAI, le code ci‑dessous fonctionne immédiatement.

---

![Diagramme montrant comment configurer LLM pour Document AI](/images/configure-llm-diagram.png){: .center-image alt="diagramme de configuration du llm"}

## Ce dont vous aurez besoin

- **Java 17** (ou tout JDK récent)  
- Un **LLM local** exposant un endpoint de type OpenAI `/v1` (p. ex., Ollama, LMStudio)  
- La **bibliothèque Java Document AI** (supposons `com.example:document-ai:1.2.0` sur Maven Central)  
- Un fichier DOCX d’exemple (`input.docx`) placé dans un dossier connu  

Si l’un de ces éléments vous manque, lancez rapidement Ollama :

```bash
ollama serve &
ollama run llama3
```

Cela démarrera un serveur sur `http://localhost:8080/v1` prêt à accepter les requêtes.

---

## Comment configurer LLM pour Document AI

La première chose que nous faisons est d’indiquer au client `DocumentAi` où trouver le modèle et quel modèle utiliser. C’est l’étape **comment configurer LLM** que de nombreux tutoriels négligent.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Pourquoi c’est important* :  
L’objet `AiModelConfig` abstrait les détails HTTP, permettant à `DocumentAi` de se concentrer sur le contenu. Si vous passez un jour à un fournisseur hébergé, il suffit de modifier `baseUrl` et `apiKey` — le reste de votre code reste intact.

---

## Charger et préparer le document DOCX

Ensuite, nous chargeons le fichier Word en mémoire. La classe `Document` gère à la fois les `.docx` et les `.pdf` en interne, mais ici nous ne nous intéressons qu’aux DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Astuce pro* : utilisez un chemin absolu pendant le débogage pour éviter la surprise « file not found ». Une fois que vous êtes sûr, revenez à un chemin relatif pour plus de portabilité.

---

## Remplacer du texte dans le DOCX avec l’IA

Voici le cœur du tutoriel — **comment remplacer du texte** dans un fichier DOCX avec l’aide de l’IA. La méthode `replaceText` envoie le contenu du document au LLM, lui demande d’effectuer la substitution, puis renvoie le texte révisé.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*Que se passe-t-il en coulisses ?*  
`DocumentAi` sérialise le DOCX en texte brut, construit une invite du type :

> « Dans le document suivant, remplacez chaque occurrence de « old phrase » par « new phrase » et ne renvoyez que le texte mis à jour. »

Le LLM traite la requête et renvoie le contenu modifié. Cette approche fonctionne même lorsque la phrase s’étend sur plusieurs runs ou paragraphes — ce que la simple recherche de chaîne manque souvent.

---

## Vérifier et afficher le texte révisé

Enfin, nous affichons le texte révisé par l’IA dans la console. Dans une application réelle, vous écririez probablement le résultat dans un nouveau DOCX, mais l’affichage permet de vérifier rapidement.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Sortie attendue** (en supposant que le DOCX original contenait « This is the old phrase we want to change. ») :

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Si vous voyez la nouvelle phrase apparaître, félicitations — **vous venez d’apprendre à utiliser Document AI pour remplacer une phrase avec l’IA**.

---

## Exemple complet fonctionnel

En rassemblant tout, voici une classe Java complète, prête à être exécutée. N’hésitez pas à copier‑coller dans `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Comment exécuter

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Assurez‑vous que le serveur LLM est démarré avant d’exécuter le programme ; sinon vous obtiendrez un délai d’attente de connexion.

---

## Cas limites et pièges courants

| Situation | Points d’attention | Solution suggérée |
|-----------|---------------------|-------------------|
| **Phrase non trouvée** | Le LLM renvoie le texte original inchangé. | Vérifiez l’orthographe et la sensibilité à la casse ; vous pouvez ajouter `ignoreCase:true` à l’invite si votre wrapper le supporte. |
| **Documents volumineux (>5 Mo)** | La taille de l’invite peut dépasser la limite de tokens du modèle. | Divisez le DOCX en sections, traitez chaque partie séparément, puis concaténez les résultats. |
| **Le LLM local renvoie des erreurs** | Souvent causé par un nom de modèle incorrect. | Vérifiez que le nom du modèle dans l’interface LLM (`ollama list`) correspond à `modelConfig.setModelName`. |
| **Caractères Unicode corrompus** | Problèmes d’encodage lors de la lecture du DOCX. | Assurez‑vous que votre runtime Java utilise UTF‑8 (ajoutez `-Dfile.encoding=UTF-8` aux arguments JVM). |

---

## Prochaines étapes

Maintenant que vous savez **comment remplacer du texte dans un DOCX** avec l’IA, vous pouvez explorer :

- **Comment utiliser Document AI** pour des tâches plus complexes comme l’extraction de tableaux ou la préservation du style.  
- **Remplacer une phrase avec l’IA** dans les PDF en changeant simplement l’argument du constructeur `Document`.  
- **Traitement par lots** : parcourez un répertoire de fichiers DOCX et appliquez la même substitution.  

Chacune de ces options repose sur la même base `AiModelConfig` et `DocumentAi`, vous n’aurez donc pas besoin de repartir de zéro.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}