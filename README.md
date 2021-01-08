# Cheat Sheet Swift 5 (Français)

Voici un cheat sheet sur le langage Swift (pour Swift 5) avec des notions à réutiliser dans le **CodinGame**, lors de tests techniques ou lors de projets d'applications iOS (iPadOS inclus)/macOS/watchOS/tvOS avec Xcode. Idéal pour tout débutant sur le langage Swift.

Swift est un langage de programmation créé par Apple et utilisé depuis 2014, qui se veut performant et sûr (c'est un langage fortement typé). Swift est un langage multi-paradigmes et orienté objet, interopérable avec le langage Objective-C, et également [open source](https://github.com/apple/swift).

**Dernière version du langage Swift: 5.3**

![Swift logo](https://codabee.com/wp-content/uploads/2019/05/1280px-Swift_logo_with_text.svg_.png)

## Table des matières

- [Syntaxe de base](#basesyntax)
- [Variables](#variables)
    + [Types de base](#basetypes)
    + [Expression](#varexp)
    + [Inférence de type](#vartypeinf)
    + [Bonus](#varbonus)
- [Opérateurs](#operators)   
- [Contrôle de flux](#flowcontrol)
    + [Condition (if)](#if)
    + [Boucle pour (for)](#for)
    + [Boucle tant que (while/repeat-while)](#while)
- [Chaînes de caractères](#strings)
    + [Substring (sous-chaîne)](#substring)
    + [Caractères (sous-chaîne)](#character)
- [Optionnels](#optionals)

## <a name="basesyntax"></a>Syntaxe de base

Dans toute expression en Swift, **il n'y a pas besoin de mettre le point-virgule à la fin d'une expression**. Le point-virgule est utile pour plusieurs déclarations de variables en une seule ligne.

Pour un affichage de base dans la console, on utilise la fonction print()
```swift
print("Hello world !")
```

## <a name="variables"></a>Variables

Comme en JavaScript, on utilise `var`pour une variable dont son contenu est modifiable et `let` pour des constantes dont son contenu ne peut pas changer. Utilisez `let` en priorité s'il n'y a pas de modifications à faire.

### Syntaxe
```swift
let <nomVariable> = <valeur>
let <nom>: <type> = <valeur>
```

Les exemples ci-dessous dans les types.

### <a name="baseTypes"></a>Types de base

Le type `Int` pour les nombres entiers, allant jusqu'à 32 bits.

```swift
var n: Int = 1
```

Pour des nombres entiers plus grands, utilisez `Int64` allant jusqu'à 64 bits.

```swift
var bigN: Int64 = 100000000000
```

Le type `Float` pour les nombres décimaux, avec une partie après la virgule (le point représentant la virgule).

```swift
var pi: Float = 3.14
```

Le type `Double` pour les nombres décimaux avec double précision, avec une partie après la virgule (le point représentant la virgule). Il est préférable d'utiliser `Double` au lieu de `Float`.

```swift
let pi: Double = 3.14159265359
```

Le type `String` représente une chaîne de caractères, comme du texte. Vous pouvez bien évidemment utiliser dans vos chaînes de caractères tous les caractères possibles y compris les émojis,...

```swift
var message: String = "Hello World !"
var emoji: String = "😀"
```

Le type `Bool` est booléen faisant office de variable à 2 états de la table de vérité étant vrai avec `true` ou faux avec `false`. À utiliser dans les opérations logiques et notamment dans les conditions.

```swift
var estConnecté: Bool = false
var estDisponible: Bool = true
```

Dans les cas plus poussés, il y a aussi les types personnalisés avec les notions d'orienté objet.

### <a name="varexp"></a>Expressions

Avec les variables, vous pouvez donc ainsi les utiliser dans des expressions, comme ci-dessous:
```swift
let a: Int = 2
let b: Int = 3
let c: Int = a + b // 5
```

### <a name="vartypeinf"></a>Inférence de type

Comme les langages JavaScript et PHP, Swift peut inférer le type de variable, c'est-à-dire qu'il n'est pas nécessaire de préciser le type de variable lors de sa création, Swift peut donc ainsi reconnaître automatiquement le type de valeur affecté à la variable. Dans des cas spécifiques, préciser son type avant l'affectation d'une valeur devient nécessaire.
```swift
let n: 2 // Int
let message = "Salut" // String
let prix = 9.99 // Double
```

### <a name="varBonus"></a>Bonus
Grâce à Apple, et pour plus de fun, il est possible dans les noms de variables en Swift d'utiliser des caractères spéciaux qu'ils soient:
- Accentués comme dans la langue française, espagnole, portugaise, ...
- De langues étrangères avec les caractères arabes, chinois, japonais, coréens, cyrilliques, indiens, thaïlandais,... (dans le monde entier)
- Utilisant des émojis et tout autre caractère Unicode.
- Le tout en conservant la convention des autres langages: **Les symboles d'opérateurs, espaces, arobases (@), chiffres au début du nom sont interdits, le compilateur le refuse**. Swift autorise l'utilisation des mots-clés du langage seulement en entourant le mot-clé avec des apostrophes inversées (`), **À N'UTILISER QU'EN CAS DE NÉCESSITÉ ABSOLUE, À PROSCRIRE EN TEMPS NORMAL !**.

```swift
var english = "Hello"
var français = "Bonjour"
var السلام عليكم" = العربية"
var 日本人 = "こんにちは"
var 😀 = "🙋‍♂️"

// À proscrire, mais c'est autorisé par le langage Swift
var `import` = "OK"
```

**NOTE: En temps normal, on doit respecter les conventions de nommage international anglophone des variables.** Mais en tout cas, Apple ne fait pas les choses à moitié 😃. Dans une pratique professionnelle, la convention globale de nommage de variables se fait en "camel case" de ce type-là:

```swift
var camelCase = 0
```

## <a name="operators"></a>Opérateurs

Incontournables, les opérateurs permettent d'effectuer diverses opérations selon les cas d'utilisation.

### Affectation
L'opérateur d'affectation `=`va affecter le contenu à droite de l'opérande à la variable à gauche de l'opérande. **ATTENTION À NE PAS CONFONDRE AVEC L'OPÉRATEUR CONDITIONNEL D'ÉGALITÉ `==`!**
```swift
var x = 2
```

### Opérateurs mathématiques basiques (type binaire)
- `+` pour l'addition (ou la concaténation avec les chaînes de caractères) -> `a + b` (en String: `"a" + "b" -> "ab"`).
- `-` pour la soustraction -> `a - b`. Utilisé aussi pour inverser le signe d'un nombre: `-a`
- `*` pour la multiplication -> `a * b`
- `/` pour la division -> `a / b`
- `%` pour le modulo (reste de la division euclidienne) -> `a % b`

**Version condensée pour effectuer une opération sur le nombre lui-même avec un autre:**
- `+=` pour l'addition (ou la concaténation avec les chaînes de caractères) -> (`a += b` au lieu de `a = a + b`)
- `-=` pour la soustraction -> (`a -= b` au lieu de `a = a - b`)
- `*=` pour la multiplication -> (`a *= b` au lieu de `a = a * b`)
- `/=` pour la division -> (`a /= b` au lieu de `a = a / b`)

**ATTENTION: L'OPÉRATEUR D'INCRÉMENTATION DE 1 (`++`) OU DE DÉCRÉMENTATION DE 1 (`--`) EXISTANT EN C, C++, JAVA, PHP, JAVASCRIPT,... N'EXISTE PAS EN SWIFT, LE COMPILATEUR SWIFT VA RÂLER !!!**
```swift
var a = 1

// Incrémentation de 1
a++ // INTERDIT !!!
a += 1 // VALIDE: a = 2

// Décrémentation de 1
a-- // INTERDIT
a -= 1 // VALIDE: a = 0
```

**ATTENTION: le compilateur Swift râle si vous effectuez des opérations mathématiques avec des types différents l'un de l'autre !!! Il est donc interdit de faire par exemple une multiplication entre un `Int` et un `Double` !** Vous devrez donc être explicite avec des conversions de type (transtypage) pour effectuer des opérations comme ça:
```swift
let a: Int = 4
let b: Double = 5.0

let c: Int = a * b // INTERDIT !
let c: Int = 4 * Int(b) // AUTORISÉ, Swift reconnaît 2 Int pour la multiplication
```

### Opérateurs de comparaison (conditionnels)
- `==` pour vérifier l'égalité entre 2 valeurs
- `!=` pour vérifier l'inégalité entre 2 valeurs
- `>` pour vérifier si la valeur est supérieure à l'autre valeur
- `>=` pour vérifier si la valeur est supérieure ou égale à l'autre valeur
- `<` pour vérifier si la valeur est inférieure à l'autre valeur
- `<=` pour vérifier si la valeur est inférieure ou égale à l'autre valeur

### Opérateurs logique (conditionnels)
- `&&`: Expression logique "ET", où les 2 valeurs doivent être à `true` pour valoir `true`, `false` sinon.
- `||`: Expression logique "OU", où l'une des 2 valeurs doit être à `true` pour valoir `true`.
- `!`: Expression logique "NON", qui donne la valeur booléenne opposée de l'expression.
```swift
var a = true
print(!a) // false
```

### Opérateurs d'intervalles
- `..<`: Intervalle semi-ouverte (la borne supérieure est exclue de l'intervalle) (`a ..< b`)
- `...`: Intervalle fermée (la borne supérieure est incluse dans l'intervalle) (`a ... b`)

### Opérateurs d'intervalles (intervalle d'un côté)
- `[n...]`: Intervalle ouverte de l'indice n au dernier indice
- `[...n]`: Intervalle ouverte du premier indice jusqu'à l'indice n

```swift
let array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print(array[3...]) // De l'indice 3 à 9: [4, 5, 6, 7, 8, 9, 10]
print(array[...4]) // De l'indice 0 à 4: [1, 2, 3, 4, 5]
```

## <a name="controlflow"></a>Flux de contrôle

### <a name="if"></a>Conditions (if)

Les blocs conditionnels "si" (`if`) sont incontournables et s'utilisent pour exécuter des blocs spécifiques par rapport aux instructions conditionnelles (booléennes) vérifiées par le biais d'opérateurs de comparaision et d'égalité. De base, il y a 2 blocs, le bloc "si" (`if`) si la condition est vérifiée, et le bloc sinon (`else`) dans le cas contraire.
```swift
let âge = 18

if âge >= 18 {
    print("Tu es majeur")
} else {
    print("Tu es mineur")
}
```

Par rapport aux autres langages, il n'y a pas besoin de mettre les conditions entre parenthèses, c'est facultatif. Utile néanmoins pour des conditions multiples afin d'assurer une meilleure lisibilité du code.

Si on a plusieurs conditions à vérifier, alors on utilise la structure "si-sinon si-sinon" (`if`, `else if`, `else`):
```swift
let note = 15

if note > 16 {
    print("Grade A")
} else if note > 12 {
    print("Grade B")
} else if note > 9 {
    print("Grade C")
} else if note > 6 {
    print("Grade D")
} else if note > 3 {
    print("Grade E")
} else {
    print("Grade F")
}
```
On peut faire plus simple avec la structure "selon" (`switch`) avec différentes valeurs pour une variable afin d'éviter la répétition de `if`,`else if`, `else`:
```swift
let codeHttp = 200

// Il n'est pas nécessaire d'utiliser le mot-clé break comme le font les autres langages.
switch codeHttp {
    case 200:
        print("Succès")
    case 403:
        print("Erreur 403: Accès refusé")
    case 404:
        print("Erreur 404: la page n'existe pas")
    case 500:
        print("Erreur 500: Erreur serveur")
    default:
        print("Erreur inconnue")
}
```

Avec les opérateurs logiques, on peut combiner plusieurs expressions:
```swift
// De 0 à 20 par incrémentations de 2
let a = 5
let b = 7

// "ET"
if a < 10 && b < 10 {
    print("OK")
}

// "OU"
if a < 10 || b < 10 {
    print("OK")
}

// Combinaison avec "NON", les parenthèses sont utiles. !(a < 10 && b < 10) = !a <> 10 && !b < 10 = a > 10 && b > 10
if !(a < 10 && b < 10) {
    print("OK")
}
```

Pour des cas d'instructions simples par rapport à un bloc `if - else`, l'opérateur ternaire du type `a ? b : c`s'avère utile
```swift
// Le if-else de base
var a = 5

if a > 5 {
    print("OK")
} else {
    print("NOT OK")
}

// L'équivalent en ternaire
(a > 5) ? print("OK") : print("NOT OK")
```

### <a name="if"></a>Boucle pour (for)

Les boucles "pour" `for` permettent de répéter de façon itérative des instructions. Aussi, la boucle `for` est utilisée pour explorer les tableaux, les caractères des chaînes,... On sait exactement le nombre de fois que les instructions vont se répéter. En Swift, la syntaxe est différente des autres langages, on utilise la structure `for`...`in` avec une variable et l'opérateur d'intervalle `...` et `..<`.

- Cas classique avec l'intervalle d'exclusion (**la borne supérieure est exclue de l'intervalle**):
```swift
// Répéter 5 fois les instructions
for i in 0 ..< 5 {
    print("i = \(i)")
}
```

- Cas classique avec l'intervalle d'inclusion (**la borne supérieure est incluse dans l'intervalle**):
```swift
// Répéter 6 fois les instructions
for i in 0 ... 5 {
    print("i = \(i)")
}
```

- Pour faire l'intervalle dans le sens inverse, on donne l'intervalle entre parenthèse suivi de la méthode `reverse`.
```swift
// Compte à rebours de 10 à 0 au lieu de 0 à 10
for i in (0 ... 10).reverse() {
    print(i)
}
```
- Pour faire une intervalle avec une itération d'une valeur spécifique au lieu de 1 à chaque fois, on utilise `stride(from: , to: , by: )`
```swift
// De 0 à 20 par incrémentations de 2
for i in stride(from: 0, to: 20, by: 2) {
    print(i)
}

// De 20 à 0 par décrémentations de 2 (on utilise une valeur négative dans by)
for i in stride(from: 20, to: 0, by: -2) {
    print(i)
}
```

### <a name="if"></a>Boucle tant que (while / repeat-while)

La boucle "tant que" (`while`) s'utilise pour répéter des opérations de façon indéterminée jusqu'à ce que la condition passe à `false`. Si la condition est déjà à `false`, la boucle `while` sera ignorée. Les conditions s'écrivent avec des expressions logiques comme dans les conditions `if`.
```swift
var n = 5

while n < 10 {
    n += 1
}
```

La boucle "faire-tant que" (`repeat-while`) fait comme la boucle `while`, sauf qu'elle répète au moins une fois les instructions de la boucle.
```swift
var n = 5

repeat {
    n += 1
} while n < 10
```

## <a name="strings"></a>Chaînes de caractères (String)

Les chaînes de caractères (`String`) sont des incontournables dans la programmation. On les utilise en permanence, mais il faut aussi leur appliquer des traitements spécifiques comme par exemple pour le filtrage, la mise en forme,...

- Rappel de la déclaration de variable:
```swift
var message: String = "Hello World !"
var message2 = "Bonjour"
```

### Interpolation de chaîne (String interpolation)

Dans une chaîne de caractères en Swift, l'interpolation va permettre de mettre en place des contenus de variables affichables, sous format de chaîne de caractère. En gros, avec la syntaxe d'interpolation, on peut y mettre plusieurs chaînes dans une seule. C'est aussi de cette façon qu'on peut afficher le contenu d'une variable de type `Int`, `Float`, `Double`, `Bool`,... dans une chaîne (entre "").

```swift
\() // Syntaxe d'interpolation de chaîne, à mettre entre les ""

var message: String = "Hello World !"
var message2 = "Le message de base: \(message)"
// Sortie: Le message de base: Hello World

var prix: Int = 1159 // Avec un Int
var sortie = "Le prix de l'iPhone 12 Pro est de \(prix)€" // Interpolation d'un Int
```

Note: C'est de cette façon qu'on affiche le contenu d'une variable dans un `print()`:
```swift
\() // Syntaxe d'interpolation de chaîne, à mettre entre les ""
var prix: Int = 1159 // Avec un Int
print("Le prix de l'iPhone 12 Pro est de \(prix)€") // Interpolation d'un Int
// -> Affiche: Le prix de l'iPhone 12 Pro est de 1 159€
```

### Concaténation de chaînes

En Swift, les opérateurs d'addition `+`et `+=`sont utilisés pour la concaténation de chaînes, c'est à dire que les chaînes seront combinées en une seule.

```swift
// Concaténation avec +
var texte = "Hello " + "World !"

// Concaténation avec += (équivaut à texte = texte + " How are you ?")
texte += " How are you ?"
```

### Multi-lignes dans une chaîne

Pour une chaîne à plusieurs lignes, il suffit de l'entourer avec des triples guillemets `"""`.
```swift
let messageMultiligne = """
Ligne 1
Ligne 2
Ligne 3
"""
```

### Conversion de types différents en String

Swift permet avec une version dédiée de constructeurs (`init`) de convertir des valeurs en chaînes de caractères, comme par exemple avec le type `Int`:
```swift
let n = 123456789
let str = String(number) // Méthode 1
let str2 = "\(number)" // Méthode 2 avec l'interpolation
"""
```

Et il est possible de faire l'opération inverse. ATTENTION, le contenu retourne un optionnel ! Si c'est `nil` et que ce n'est pas vérifié, ça crashe ! Si vous êtes certain que le contenu est correct et existant, alors il suffira de déballer avec `!`. 
```swift
let str = "123456789"
let n = Int(number)! // ATTENTION, Int(string) retourne Int?
```

### <a name="substring"></a>Sous-chaînes (Substring)

En Swift, les sous-chaînes ont un type défini: `Substring`. Elles s'utilisent de façon temporaire avant d'être converties en `String` avec son constructeur dédié.

### <a name="character"></a>Caractères

Comme les autres langages, Swift a son propre type pour les caractères: `Character`. Une chaîne `String` est composée de caractères `Character`.
```swift
let str = "Hello"

for c in str {
    print(c) // H -> e -> l -> l -> o
}
```

Pour déclarer une variable:
```swift
let c: Character = "c"
```

Avec un tableau de `Character`, en le passant en argument du constructeur, il est possible de le transformer en `String`:
```swift
let caractères: [Character] = ["H", "e", "l", "l", "o"]
let str = String(caractères)

print(str) // "Hello"
```

**ATTENTION: VOUS NE POUVEZ PAS DIRECTEMENT UTILISER UN `Character` POUR TOUT ÉLÉMENT UTILISANT LE TYPE `String` ! VOUS DEVEZ LE CONVERTIR EN STRING:**
```swift
let c: Character = "c" // Avec let c: "c", ce sera un String. ATTENTION donc dans ce cas particulier !
let s = String(c)
```

Si la chaîne ne contient qu'un seul caractère, la conversion de `String` vers `Character` est possible
```swift
let s = "c"
let c = Character(s) // AUTORISÉ

let s1 = "cc"
let c1 = Character(s) // ERREUR !
```

Il est aussi possible de concaténer un `Character` dans un `String`:
```swift
var s = "Hello "
let c:  Character = "!"

s.append(c) // "Hello !"

s += c // INTERDIT !
```

## <a name="optionals"></a>Optionnels

Les optionnels sont des contenant de type générique qui peuvent contenir ou non une valeur. Par rapport aux autres langages où on utilise `null` pour signifier l'absence de valeur, Swift se veut sûr en s'assurant que chaque variable contienne une valeur lorsqu'elle doit être exploitée afin de réduire le plus possible le cas de crashs et de bugs. Pour déclarer un type optionnel, on écrit le nom du type suivi d'un `?`. Si l'optionnel ne contient rien, on lui affecte la valeur `nil` (équivalent à `null`), attribuée par défaut si aucune valeur est fournie.

```swift
var a: Int? // nil par défaut
var b: String? = nil // nil explicite
var c: Double? = 10.0 // Optionnel contenant une valeur

print(c) // Affiche Optional(10.0)
```

### Déballage d'un optionnel (accéder à sa valeur): déballage forcé

Dans un optionnel, pour accéder à son contenu, il faut le "déballer" (unwrap), et on utilise `!` après le nom de la variable, de l'appel du constructeur ou d'une fonction retournant une valeur optionnelle. **ATTENTION: DE CETTE FAÇON DIRECTE, VOUS DEVEZ ÊTRE ABSOLUMENT SÛR ET CERTAIN QUE L'OPTIONNEL CONTIENNE BIEN UNE VALEUR, L'APPLICATION CRASHE DANS LE CAS CONTRAIRE SI L'OPTIONNEL NE CONTIENT RIEN (`nil`) !!!**.

```swift
var a: Int? = 3 // nil par défaut
var b: String? = nil // nil explicite

print(a) // Affiche Optional(3)
print(a!) // Affiche 3

// DANGER: CRASH DE L'APPLICATION, car b vaut `nil`.
print(b!)
```

Pour plus de sûreté avec le déballage forcé, on peut utiliser une condition pour vérifier si l'optionnel contient bien une valeur:
```swift
var a: Int? = 3 // nil par défaut
var b: String? = nil // nil explicite

if a != nil {
    print(a!) // 3
}

// CRASH ÉVITÉ
if b != nil {
    print(b) // DANGER: CRASH DE L'APPLICATION, car b vaut `nil`.
}
```

### Déballage d'un optionnel de façon sûre: if let

Swift permet de déballer l'optionnel de façon sûre et pratique grâce à la condition `if let`. Par rapport aux conditions classiques, ici on utilise l'opérateur d'affectation pour vérifier que l'optionnel contienne une valeur. Ici, il n'y aura donc pas besoin de faire du déballage forcé avec "!".
```swift
var a: Int? = 3 // nil par défaut

// Équivaut à if a != nil, b = a! 
if let b = a {
    print(b) // 3
} else {
    print("Pas de valeur")
}
```

En condensé, il existe l'équivalent du `if-else` en ternaire, on utilise l'opérateur `??`
```swift
var a: Int? = 3 // nil par défaut

// Équivaut à if a != nil, b = a! 
print(a ?? "Pas de valeur")

let b = a ?? nil
```