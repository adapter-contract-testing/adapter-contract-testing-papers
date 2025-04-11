🧪 Adapter Contract Testing & Simulateurs
====

➡️ Pour des tests applicatifs plus fiables, plus simples, sans mocks fragiles.

----

### 🐛 Un bug en prod malgré vos tests ?

Vous avez tout testé… mais un comportement inattendu se produit en production.
La cause ? Souvent, **un mock** qui ne simule pas fidèlement le service ou la base de données.<br>
Et si vous changiez d’approche ?

### 🎭 Simulateurs à la place des mocks

Plutôt que de mocker à l’aveugle avec un framework, on peut **coder à la main un simulateur**. <br>
Un composant simple, maintenu dans le projet, qui simule **juste ce dont l'application a besoin**.

**💡 Pourquoi c’est mieux ?**

 - Le simulateur se comporte comme un vrai service, avec de vraies règles métier.
 - Il est plus expressif qu’un mock : on peut simuler des erreurs spécifiques, des séquences d’échanges, des états internes.
 - Il rend les tests métier **plus faciles à écrire** et **beaucoup plus fiables**, car l’environnement de test est proche du réel.

**🛠️ Exemples :**

 - Pour un service tiers : le simulateur peut générer des réponses réalistes, des erreurs précises, ou simuler une séquence de requêtes typique de la prod.
 - Pour une base de données : on implémente une version in-memory, capable de gérer les insertions, les requêtes, et les règles de filtrage.

Un simulateur bien conçu devient un outil précieux dans tous les tests applicatifs. Et surtout : **il remplace tous les mocks** pour cette dépendance.

---

### 🔁 Adapter Contract Testing : le lien entre le vrai et le simulé

Mais comment garantir que ce simulateur se comporte **comme le vrai service** ?<br>
➡️ C’est là qu’intervient l’**Adapter Contract Testing**.

L’idée :
 1. On écrit un test d’intégration **contre le vrai service externe** (ou une base réelle, ou toute dépendance non maîtrisée).
 2. Ce test devient le **contrat de comportement** attendu.
 3. On utilise ce même test pour valider notre simulateur.

🎯 Résultat : **un seul test** garantit à la fois :

 - L’intégration avec le service externe fonctionne, sans surprise
 - Le simulateur reproduit fidèlement ce comportement.
 - La cohérence dans le temps entre la réalité et la simulation

C’est puissant, car on évite la dérive entre ce qu’on teste et ce qui se passe en prod. On détecte aussi les régressions dues aux évolutions du partenaire

--- 

### 🧩 Simplifier l’interface = simplifier le test

Mais pour que cette approche fonctionne bien, encore faut-il que l’interface entre l’application et sa dépendance 
soit **claire et stable**.


| Ce n'est pas parce que la dépendance fait tout cela             | Que l'on veut plus que ceci                                   |
|-----------------------------------------------------------------|---------------------------------------------------------------|
| <img src="swiss-knife-complex.png" alt="complex" height="220"/> | <img src="swiss-knife-simple.png" alt="simple" height="220"/> |

👉 Moins on expose les détails techniques de la dépendance, plus il est facile de : 
 - écrire un contrat simple,
 - développer un simulateur fidèle,
 - et maintenir l’ensemble dans le temps.

📐 **Domain Driven Design** et **architecture hexagonale** sont deux excellentes sources d’inspiration ici : <br>
Ils poussent à concevoir des interfaces métier **centrées sur l’usage réel** de la dépendance, et non sur sa complexité interne.

En d’autres termes : **en maîtrisant la dépendance**, on rend le test bien plus simple et robuste.

---

### ✅ En résumé

<br> 🧩 On simplifie l’interface vers nos dépendances.
<br> 🧪 On écrit un test d’intégration qui définit un contrat de comportement.
<br> 🎭 On développe un simulateur qui respecte ce contrat.
<br> 🔁 Ce simulateur remplace tous les mocks dans nos tests applicatifs.
<br> ⚙️ Les tests deviennent plus simples, plus fiables, et plus proches de la réalité.

📚 Pour voir des exemples concrets :
 - Slides : https://adapter-contract-testing.github.io/presentation
 - Kata : https://github.com/adapter-contract-testing/snail-race-kata

