# Javascript pour l'analytics et le tag management

## Partie 1 : Les variables

```javascript
var myString = 'Hello world';
//Convention Javascript : le camelCase (1ère lettre en minuscule, tout attaché)
//On peut utiliser des simple ou double quotes, l'important est d'être consistant
//Toute instruction se finit par un point virgule
console.log(myString);

var myInteger = 12;

console.log('On ajoute 2 à notre Integer : ' + myInteger+2);

var myFloat = 31.43;

console.log('J\'ajoute la TVA' + myFloat*1.05)
//On pense à échapper les quotes

var myBoolean = true;

console.log('Le type de ma variable est' + typeof myInteger);
/*
On peut aussi ajouter des commentaires
sur plusieurs lignes
*/

var priceError = '32';
var myRoundedPrice = parseInt(priceError,10);

var priceError2 = '32.12' 
var myRoundedPrice = parseFloat(priceError2,10);

var priceToStringigy = 321;
var stringifiedPrice = priceToStringigy.toString();

//
```

### Exercices partie 1

Niveau facile : Déclarer une variable avec son nom, une avec son prénom, puis une troisième qui les concatène, en affichant un message "Bonjour Nom, Prénom!". Afficher cette dernière variable dans la console

Niveau difficile : Créer une variable de type string, et la transformer en Booléen. Contrainte : le booléen doit être à false.

## Partie 2 : Les conditions

```javascript
var price = 14;

if (price > 12) {
	console.log('Envoyer un pixel de retargeting');
	}

var country = 'France';

if (price > 7 && country === 'France' ){
// Les 2 conditions doivent être vérifiées
	console.log('Envoyer le tag Criteo');	
	}

var country = 'Italy';

if (country === 'France' || country === 'Italy' ){
	console.log('Envoyer le pixel Facebook');
}

var control = true;

if (control && price > 2){
	//Les variables doivent être "truthy"
	//false
	//undefined
	//null
	//0
	//NaN
	//""
}

if (price > 12){
	console.log('Envoyer le pixel Facebook générique');
}
else {
	console.log('Envoyer le pixel Facebook des promos');
}

if (price < 8){
	console.log('Envoyer le pixel de la régie 1');
}
else if (price >=8 && price <20) {
	console.log('Envoyer le pixel de la régie 2');
}
else {
	console.log('Envoyer le pixel de la régie 3');
}
//On peut faire autant de "else if" que l'on veut

if (price >50){
	console.log('trop cher!')
}
else {
	console.log('pas assez cher!');
}
//Equivalent à un ternaire =>
price > 50 ? console.log('trop cher!') : console.log('pas assez cher!');

var product = 'chaussures';

if (product === 'sac') {
	console.log('tag rmkt 1');
} 
else if (product === 'PC' ){
	console.log('tag rmkt 2');
}
else if (product === 'chaussures' ){
	console.log('tag rmkt 3');
}
else{
	console.log('tag rmkt 43');
}

//Equivalent en switch..case
switch(product){
	case 'sac' : console.log('tag rmkt 1'); break;
	case 'PC' : console.log('tag rmkt 2'); break;
	case 'sac' : console.log('tag rmkt 3'); break;
	default : console.log('....')
}
```

Intermède : les URLs : 

```javascript
var monURL = window.location.href;
//Un doute? Taper window.location. dans la console Chrome
```

### Exercices partie 2

Niveau facile : compléter le script ci-dessous

```javascript
var product = 'shoes';
var price = '12'
//Si on a un prix supérieur à 12 et le produit "shoes", on envoie le tag A, sinon on envoie le tag B
```

Niveau difficile : même exercice, mais en plus, l'URI doit *contenir* "product"

## Partie 3 : Les tableaux

```javascript
var myArray = ['kkjkj'],
	myOtherArray = ['aaa','bbbb',1223,32.4,true];
//Notation raccourcie pour définir plusieurs variables à la suite

myArray.push(myOtherArray);

typeof myOtherArray;
//Renvoie 'object' => ça ne va pas tellement aider

Array.isArray(myOtherArray);
//Renvoie 'true'

myOtherArray.length;
//Renvoie 5

myOtherArray[3]
// Pour récupérer une valeur en particulier

var joinedArray = myOtherArray.join('|');
// 'true|32.4|1223|bbbb'



var product = '111';
console.log('variable dèv'+product);

myArray.push('newElement')

Exercice : corriger 

```javascript
var myArray = ['Pierre','Paul]
```

Exercice

## Partie 4 : Les boucles for & cie

## Les objets 

```javascript
//Je veux stocker les infos sur un client?

var customerArray = ['Dupont','Jean',25,true];
//Pas pratique pour stocker des valeurs typées

var customerObject = {
	'last name' : 'Dupont',
	'first name' : 'Jean',
	'age' : 25,
	'is Client' : true
}
//Un "objet" est un ensemble de clés / valeurs, sans notion d'ordre

Array.isArray(customerObject)
//Renvoie "false"

customerObject["first name"]
//Renvoie "Jean"

customerObject['first name'] = 'Émilie';
//Pour changer à la volée une valeur

customerObject['salary' : 3000];
//Pour ajouter une paire clé / valeur

//parser un objet
for (var key in customerObject) {
  console.log('clé : '+key+'  value : '+ customerObject[key]);
}

```

## Partie 5 : les fonctions

L'intérêt des fonctions : faire du code réutilisable

```javascript
//Syntaxe basique d'une fonction - Écriture
function getRandom(){
	console.log(Math.random());
}
//On parle aussi de méthode (équivalent)

//Syntaxe basique d'une fonction - Invocation
getRandom();

//Fonction avec un argument
function getRandomUpToX(max){
	//max => Argument de la fonction
	console.log(Math.random()*max);
}
```

## Partie 6 : Les dates

```javascript
//Générer un timestamp
var unixTimestamp = Date.now();
//Nombre de millisecondes écoulées depuis le 1er janvier 1970

//Générer une date 
var date2 = new Date('December 17, 1995 03:24:00');

typeof date2
//Renvoie "object"

```

Exercice : créer une fonction qui prend en input une date de naissance au format AAAA-MM-JJ, et donne le nombre de jours depuis

## Partie 7 : La manipulation du DOM

Rappel : les sélecteurs CSS

```css
p /*=> Toutes les balises <p>*/
.red /*=> Toutes les balises de classe 'red'*/
#product-image /*=> Toutes les balises d'ID product-image*/
ul .active /*=> Sélecteur descendant direct*/
ul > .active /*=> Sélecteur descendant global*/
```

```javascript
document.querySelector('#newsletter').addEventListener('focus',function(){
	console.log('Le formulaire a le focus');
	dataLayer.push({
		'event' : 'formFocus',
		'formName' : 'newsletter'
	})
})

//Astuce : récupérer un sélecteur CSS depuis l'inspecteur Chrome

```

## Partie 8 : Les cookies et le local storage

```javascript
//Ecrire un cookie
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2013 12:00:00 UTC; path=/";
//Bon exercice pour chainer les conditions

//Lire un cookie
document.cookie
//Renvoie une string

// Enregistrer des données dans sessionStorage
sessionStorage.setItem('idClient', '123456789');

// Récupérer des données depuis sessionStorage
var monID = sessionStorage.getItem('idClient');

// Supprimer des données de sessionStorage
sessionStorage.removeItem('idClient');
```

Le local storage est plus moderne, mais pas compatible avec de vieux navigateurs, et sans possibilité de contrôler finement l'expiration, et le domaine

Exercice niveau 1 : créer un cookie GA 'propre' (GA1.2.1232667359.1603816516) avec un random number, le timestamp courant, et une date d'expiration à 13 mois

Exercice niveau 2 : faire une méthode qui prend un booléen en entrée, et fait une expiration à 12 ou 24 mois selon ce que renvoie ce booléen

## Partie 9 : Le bilan

A comprendre avant de passer sur GTM