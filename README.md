# Javascript pour l'analytics et le tag management

## Les variables

```javascript
var myString = 'Hello world';
//Convention Javascript : le camelCase (1ère lettre en minuscule, tout attaché)
//On peut utiliser des simple ou double quotes, l'important est d'être consistant
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

var priceError = '32' 
var myRoundedPrice = parseInt(priceError,10);

var priceError2 = '32.12' 
var myRoundedPrice = parseFloat(priceError2,10);

var priceToStringigy = 321;
var stringifiedPrice = priceToStringigy.toString();

//
```

### Exercices partie 1

Niveau facile : Déclarer une variable avec son nom, une avec son prénom, puis une troisième qui les concatène, en affichant un message "Bonjour Nom, Prénom!". Afficher cette dernière variable dans la console

Niveau difficile : Créer une variable de type string, et la transformer en Booléen. Contrainte : le booléen doit être à false

## Les boucles

```javascript
var priceDL = 12,
	url = document.location.href;

if (url === 'https://www.chomette.fr/' || priceDL > 10){
// === signifie que le type doit être le même
	console.log('tag remarketing');
} 


var priceDL = 9;

priceDL > 10 ? console.log('tag remarketing 1') : console.log('tag remarketing 2');


//Equivalent à
if (priceDL > 10){
	console.log('tag remarketing 1');
} 
else{
	console.log('tag remarketing 2');
}


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


//Equivalent
switch(product){
	case 'sac' : console.log('tag rmkt 1'); break;
	case 'PC' : console.log('tag rmkt 1'); break;
	case 'sac' : console.log('tag rmkt 1'); break;
	default : console.log('....')
}

```

## Les tableaux

```javascript
var myArray = ['kkjkj'],
	myOtherArray = ['aaa','bbbb',1223,32.4,true];

myArray.push(myOtherArray);

Array.isArray(myOtherArray);
//Renvoie 'true'

myOtherArray.length;
//Renvoie 5

myOtherArray[3]
// Pour récupérer une valeur en particulier

var joinedArray = myOtherArray.join('|');
// "true|32.4|1223|bbbb"

var product = '111';
console.log('variable dèv'+product);


//Dans GTM
(function(){ 
    var product = 'Barry';
    console.log('variable GTM'+product);
})();
```

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

## Les dates

```javascript
//Timestamp vs type date
```

## La manipulation du DOM

```javascript
document.querySelector('#newsletter').addEventListener('focus',function(){
	console.log('Le formulaire a le focus');
	dataLayer.push({
		'event' : 'formFocus',
		'formName' : 'newsletter'
	})
})
```

## Les cookies et le local storage

```javascript
//Lire un cookie
```