# beltariacontent-api — dépôt Maven

Ce dépôt **ne contient pas de code source**. C'est un dépôt Maven servi par
`raw.githubusercontent`, qui publie l'API de BeltariaContent pour que les autres
plugins (BeltariaGear, BeltariaCrafts, BeltariaShop, BeltariaRunes) compilent
contre elle sans construire BeltariaContent.

Les versions sont publiées par le workflow de release de BeltariaContent à chaque
tag `v*` (ou à la main, voir le README de BeltariaContent). Une version publiée ne
se réécrit jamais.

## Utiliser l'API

L'artefact `fr.beltaria:content-api` ne contient que l'interface
`fr.beltaria.content.api.ContentItems` : fabriquer un item du catalogue par son
identifiant, lire le `beltaria:id` d'un item. Ses classes sont livrées dans
`BeltariaContent.jar` : la déclarer en `compileOnly`.

**Gradle** (Kotlin DSL)

```kotlin
repositories {
    maven("https://raw.githubusercontent.com/Beltaria/beltariacontent-api/main/") {
        content { includeGroup("fr.beltaria") }
    }
}

dependencies {
    compileOnly("fr.beltaria:content-api:7.0.0")
}
```

```java
ContentItems items = ContentItems.get();      // null si BeltariaContent n'est pas actif
ItemStack orb = items.build("orbe_t3", 1);    // null pour un identifiant inconnu
```
