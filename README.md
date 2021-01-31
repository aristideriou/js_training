# Javascript pour l'analytics et le tag management

## Introduction : le tooling

Installer un bon éditeur de texte : [Sublime Text](https://www.sublimetext.com/) (simple et efficace), ou [VSCode](https://code.visualstudio.com/) (plus complexe, mais aussi très complet).

Télécharger [l'archive avec le template de base](https://github.com/aristideriou/aristideriou.github.io/tree/master/js_demo_page) et le modifier tout au long de la formation.

Travailler en local

Vos 3 meilleurs amis : 
- La console de Chrome pour débugger
- La doc (W3Schools, MDN)
- Les forums (StackOverflow)

## Partie 1 : Les variables

```javascript
var myString = 'Hello world';
//Convention Javascript : le camelCase (1ère lettre en minuscule, tout attaché)
//On peut utiliser des simple ou double quotes, l'important est d'être consistant
//Toute instruction se finit par un point virgule
console.log(myString);

var myInteger = 12;

var userValue = prompt('Saisir un nombre entre 1 et 10');
//Technique rudimentaire pour créer un peu d'interaction

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
var myIntPrice = parseInt(priceError,10);

var priceError2 = '32.12' 
var myFloatPrice = parseFloat(priceError2,10);

var accuratePrice = 452.123485654;
var myRoundedPrice = Math.round(accuratePrice);

var priceToStringigy = 321;
var stringifiedPrice = priceToStringigy.toString();

//
```

### Exercices partie 1

Niveau facile : Déclarer une variable avec son nom, une avec son prénom, puis une troisième qui les concatène, en affichant un message "Bonjour Nom, Prénom!". Afficher cette dernière variable dans la console

Niveau difficile : Demander via un prompt l'âge de l'utilisateur en années, et afficher un message dans la console avec son âge (approximatif) en jours

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

Intermède : manipulation des URLs 

```javascript
var myURL = window.location.href;
//Un doute? Taper window.location. dans la console Chrome pour voir toutes les infos que l'on peut récupérer
```
![Window loc](/window_location_search.png "Logo Title Text 1")


### Exercices partie 2

Niveau facile : compléter le script ci-dessous

```javascript
var product = 'shoes';
var price = '12'
//Si on a un prix supérieur à 12 et le produit "shoes", on envoie le tag A, sinon on envoie le tag B
```

Niveau difficile : même exercice, mais en plus, l'URI doit **contenir** "product"

## Partie 3 : Les tableaux

```javascript
var myArray = ['kkjkj'],
	myOtherArray = ['aaa','bbbb',1223,32.4,true];

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

//Transformer une string en tableau
var completeURL = document.location.href;

var ArrayURL = completeURL.split('/');

var product = '111';
console.log('variable dèv'+product);

myArray.push('newElement')
```

Exercice : corriger le script suivant

```javascript
var myArray = ['Pierre','Paul]
```

Exercice niveau difficile : extraire uniquement 

## Partie 4 : La boucle for

C'est la boucle de base qui permet notamment d'itérer sur un tableau.

En JS "moderne", il existe des boucles plus optimisées / lisibles selon les cas, mais "for" permettra toujours de s'en sortir

```javascript
var cars = ['Renault','Nissan','Ford'];

for (var i = 0; i < cars.length; i++) {
  console.log(cars[i]);
}

var productTags = ['Apple','Computer','Laptop','2021 Sales'];
//Objectif : envoyer un tag d'event spécifique à GA si jamais l'article a un tag "2021 Sales"

for (var i = 0; i < productTags.length; i++) {
  if (productTags[i]==='2021 Sales'){
	  //Envoyer un tag GA ici...
  }
}

```

## Partie 5 : Les objets 

Problématique : je veux stocker les infos sur un client (nom, prénom, âge)

```javascript

var customerFirstName = 'Jean',
	customerLastName = 'Dupont',
	customerAge = 25,
	customerIsClient = true;
//Un peu redondant, non?

var customerArray = ['Dupont','Jean',25,true];
//Pas pratique pour stocker des valeurs sans savoir de quoi il s'agit 😣

var customerObject = {
	'last name' : 'Dupont',
	'first name' : 'Jean',
	'age' : 25,
	'is Client' : true
}
//Un "objet" est un ensemble de clés / valeurs, sans notion d'ordre (Dictionnary en Python). 

customerObject["first name"]
//Pour aller récupérer une valeur d'une clé en particulier => Ici, renvoie "Jean"

customerObject['first name'] = 'Émilie';
customerObject.age = 27;
//Pour changer à la volée une valeur. Les 2 écritures sont équivalentes, mais préférer la méthode avec les crochets pour les clés qui comportent des espaces & cie

customerObject['salary' : 3000];
//Pour ajouter une paire clé / valeur, autrement dit une nouvelle ligne, à notre objet

var dataLayer = [{
	'pageType' : 'editorial',
	'pageID' : 123456789,
	'loggedUser' : true,
	'userID' : 32165498
}];
//Le data layer de GTM est un array d'objets

//Comment parser un objet pour faire des trucs?
//For ne marche pas, car for n'est capable que de parser des "énumérables"
for (var key in customerObject) {
  console.log('clé : '+key+'  value : '+ customerObject[key]);
}
```

Exercice facile : ajouter la TVA (5%) à l'objet ci-dessous (nouvelle clé 'taxes')

```javascript
var transaction = {
	'id' : 6666666,
	'amount' : 26,
	'product' : 'MacBook Air 13 pouces' 
}
```

Exercice difficile : parser le data layer et le réécrire si une clé est incorrecte

## Partie 6 : les fonctions

L'intérêt des fonctions : faire du code réutilisable sans se répéter (DRY : Don't Repeat Yourself est quasiment le principe de développement le plus important)

```javascript
//Syntaxe basique d'une fonction (on parle aussi de méthode)
function getRandom(){
	var randomNumber = Math.random();
	return randomNumber;
	//return => Valeur de retour, qui sera renvoyée lorsque la fonction sera exécutée
}

//Syntaxe basique d'une fonction - Invocation
getRandom();

var myRandomNumber = getRandom();
//Affectation d'une variable via une fonction => D'où l'importance du "return" (renverrait undefined sinon)

//Fonction avec un argument
function getRandomUpToX(max){
	//max => Argument de la fonction
	return Math.random()*max;
}

//On appelle ensuite la fonction avec un argument

```

Exercice niveau facile : créer une méthode qui parse le data layer, et renvoie un boléen selon la présence d'un ID de transaction (transactionID)

Exercice niveau difficile : 

## Partie 7 : Les dates

```javascript
//Générer un timestamp
var unixTimestamp = Date.now();
//Nombre de millisecondes écoulées depuis le 1er janvier 1970

//Générer une date 
var date2 = new Date('December 17, 1995 03:24:00');

typeof date2
//Renvoie "object"

//Mettre une date au format UTC
```

Exercice : créer une fonction qui prend en input une date de naissance au format AAAA-MM-JJ (prompt), et donne le nombre de jours depuis.
Bonus : vérifier l'intégrité de la date envoyée par l'utilisateur (le format doit être correct)

## Partie 8 : La manipulation du DOM et les events listeners

Rappel : les sélecteurs CSS

```css
p /*=> Toutes les balises <p>*/
.red /*=> Toutes les balises de classe 'red'*/
#product-image /*=> Toutes les balises d'ID product-image*/
ul .active /*=> Sélecteur descendant direct*/
ul > .active /*=> Sélecteur descendant global*/
```

```javascript
var selector1 = document.querySelector('h1');

var selector2 = document.querySelectorAll('h3');

var selector3 = document.getElementById
```

Niveau 2 : modifier le DOM

Astuce : récupérer un sélecteur CSS depuis l'inspecteur Chrome

```javascript
//On travaille à l'envers : on commence par créer la fonction que l'on va "attacher" à l'événement

function pushNLEventToDL (){
	console.log('Le formulaire a le focus');
	dataLayer.push({
		'event' : 'formFocus',
		'formName' : 'newsletter'
	})
}
//On pense bien à tester la fonction "à blanc"

document.querySelector('#newsletter').addEventListener('click',pushNLEventToDL());
```

## Partie 9 : Les cookies et le local storage

```javascript
//Ecrire un cookie
document.cookie = "username=Pierre Dupont; expires=Thu, 18 Dec 2021 12:00:00 UTC; path=/";
//Bon exercice pour chainer les conditions

//Lire un cookie
document.cookie
//Renvoie une string qu'il faut ensuite parser

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

## Partie 10 : Le bilan

A comprendre avant de passer sur GTM