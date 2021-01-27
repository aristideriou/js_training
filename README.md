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

//Dans GTM
(function(){ 
    var product = 'Barry';
    console.log('variable GTM'+product);
})();
```

## Partie 4 : Les boucles for & cie

## Les objets 

```javascript
//Je veux stocker les infos sur un client

var customerArray = ['Dupont','Jean',25,true];
//Pas pratique pour stocker des valeurs typées

var customerObject = {
	'last name' : 'Dupont',
	'first name' : 'Jean',
	'age' : 25,
	'is Client' : true
}

Array.isArray(customerObject)
//Renvoie "false"

customerObject["first name"]
//Renvoie "Jean"
```

## Partie 5 : les fonctions

L'intérêt des fonctions : faire du code réutilisable

```javascript
//Syntaxe basique d'une fonction - Écriture
function getRandom(){
	console.log(Math.random());
}

//Syntaxe basique d'une fonction - Invocation
getRandom();

//Fonction avec un argument
function getRandomUpToX(max){
	//max => Argument
	console.log(Math.random()*max);
}
```

## Partie 6 : Les dates

```javascript
//Timestamp vs type date
```

## Partie 7 : La manipulation du DOM

Rappel : les sélecteurs CSS

p => Toutes les balises <p>
.red => Toutes les balises de classe 'red'
#product-image => Toutes les balises d'ID product-image
ul .active => Sélecteur descendant direct
ul > .active => Sélecteur descendant global

```javascript
document.querySelector('#newsletter').addEventListener('focus',function(){
	console.log('Le formulaire a le focus');
	dataLayer.push({
		'event' : 'formFocus',
		'formName' : 'newsletter'
	})
})
```

## Partie 8 : Les cookies et le local storage

```javascript
//Lire un cookie

//Ecrire un cookie

//Lire un local / session storage

//Ecrire un local storage
```