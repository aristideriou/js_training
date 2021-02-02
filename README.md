# Javascript pour l'analytics et le tag management

## Introduction : le tooling

Installer un bon éditeur de texte : [Sublime Text](https://www.sublimetext.com/) (simple et efficace), ou [VSCode](https://code.visualstudio.com/) (plus complexe, mais très customisable).

Télécharger l'archive avec le template de base (lien envoyé avant la formation) et le modifier tout au long de la formation.

Votre setup durant la formation : 
- Ce repo ouvert (cheat sheet)
- Sublime
- Page en local / débuggueur Chrome
- Zoom avec mon partage d'écran
(Double écran fortement conseillé)

Le rythme de la formation : alternance entre des phases de démo / tuto, et des exercices. Chaque partie comporte un exercice facile, que vous devez absolument comprendre, et un exercice difficile, qui vous pousse en général à chercher au delà du tuto

Vos meilleurs amis : 
- Google, déjà
- La documentation (W3Schools, MDN)
- Les forums (StackOverflow mais pas que)

## Partie 1 : Les variables

```javascript
var myString = 'Hello world';
console.log(myString);
//Convention Javascript : le camelCase (1ère lettre en minuscule, tout attaché)
//On peut utiliser des simple ou double quotes, l'important est d'être consistant
//Toute instruction JS se finit par un point virgule

var myInteger = 12;

var userValue = prompt('Saisir un nombre entre 1 et 10');
//Technique rudimentaire pour créer un peu d'interaction et récupérer dans une variable une valeur saisie par l'utilisateur

console.log('On ajoute 2 à notre Integer : ' + myInteger+2);
//+ sert à la fois à concaténer des variables, et à incrémenter des integers

var myFloat = 31.43;

console.log('J\'ajoute la TVA' + myFloat*1.05)
//On pense à échapper les quotes avec un backslash

var myBoolean = true;

console.log('Le type de ma variable est' + typeof myInteger);
/*
On peut aussi ajouter des commentaires
sur plusieurs lignes
*/

var priceError = '32';
var myIntPrice = parseInt(priceError,10);
//Attention : la méthode parseInt prend toujours en 2nd paramètre la "base"

var priceError2 = '32.12' 
var myFloatPrice = parseFloat(priceError2);
//Un seul paramètre pour parseFloat

var accuratePrice = 452.123485654;
var myRoundedPrice = Math.round(accuratePrice);

var priceToStringify = 321;
var stringifiedPrice = priceToStringify.toString();
```

### Exercices partie 1

Niveau facile : Déclarer une variable avec son nom, une avec son prénom, puis une troisième qui les concatène, en affichant un message "Bonjour Nom, Prénom!". Afficher cette dernière variable dans la console

```javascript
var userLastName = ;
var userFirstName = ;
//A compléter
```

Niveau difficile : Demander via un prompt l'âge de l'utilisateur en années, et afficher un message dans la console avec son âge (approximatif) en jours

```javascript
var userAge = ;//Rentrer l'âge de l'utilisateur dans cette variable en lui demandant via un "prompt"
var ageInDays = ;//Compléter cette variable pour avoir l'âge en jours
console.log('vous avez...jours');//A compléter pour afficher dynamiquement l'âge

//A compléter
```

## Partie 2 : Les conditions

```javascript
var price = 14;
if (price > 12) {
	console.log('Envoyer un pixel de retargeting');
	}
//La condition dans le "if" doit être vérifiée. 
//Autrement dit, elle doit être évaluée à "true"

var country = 'France';
if (price > 7 && country === 'France' ){
// Les 2 conditions doivent être vérifiées
	console.log('Envoyer le tag Criteo');	
	}

var country = 'Italy';
if (country === 'France' || country === 'Italy' ){
// Une seule des 2 conditions doit être vérifiée
	console.log('Envoyer le pixel Facebook');
}

//Différence entre === et ==
12 == '12' //renvoie 'true' => JS fait une conversion de type à la volée
12 === '12' //renvoie 'false'
//Dans la mesure du possible, utiliser la triple égalité, plus stricte, pour éviter les mauvaises surprises

var control = true;

if (control && price > 2){
	//Les variables doivent être "truthy", c'est à dire aucun des cas suivants :
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
//Attention : le ternaire est une technique synthétique, mais qui peut parfois ne pas être très lisible

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
![Window loc](https://github.com/aristideriou/js_training/blob/main/window_location_search.png "Logo Title Text 1")

 
### Exercices partie 2

Niveau facile : compléter le script ci-dessous

```javascript
var product = 'shoes';
var price = '12'
//Si on a un prix supérieur à 12 et le produit "shoes", on envoie le tag A, sinon on envoie le tag B
```

Niveau difficile : même exercice, mais en plus, l'URI doit **contenir** "product" (vous allez devoir chercher un peu!)

## Partie 3 : Les tableaux

Pour l'instant, on ne stocke que des infos disparates. On aimerait bien avoir des informations de façon un peu plus structurée

```javascript
var mySites = ['google.com','bing.com','yandex.ru'],
	myOtherArray = ['aaa','bbbb',1223,32.4,true];

myArray.push('this is another item');

myOtherArray.length;
//Renvoie 5

myOtherArray[3]
// Pour récupérer une valeur en particulier

var joinedArray = myOtherArray.join('|');
// 'true|32.4|1223|bbbb'

typeof myOtherArray;
//Renvoie 'object' => ça ne va pas tellement aider

Array.isArray(myOtherArray);
//Renvoie 'true'

//Transformer une string en tableau
var completeURL = document.location.href;

var ArrayURL = completeURL.split('/');

var product = '111';
console.log('variable dèv : '+product);

myArray.push('newElement')
```

Apparté : les Regex

```javascript
var myURL = 'www.monsupersite.fr';
var regex = '(www)\.(.+)\.(fr|com)';

myURL.match(regex);
//Renvoie true ou false si la string matche la regex
```

Exercice : dans l'array suivant, ajouter Jacques, uniquement si le 2ème élément est "Pierre" :

```javascript
var myArray = ['Pierre','Paul]
```

Exercice niveau difficile : modifier le script précédent => Si le 2ème élément est 'Paul', retirer le 1er élément, puis ajouter Pierre (vous allez devoir chercher un peu!)

## Partie 4 : La boucle for

C'est la boucle de base qui permet notamment d'itérer sur un tableau.

```javascript
var cars = ['Renault','Nissan','Ford'];

for (var i = 0; i < cars.length; i++) {
	console.log(cars[i]);
}

for (var i = 0; i < cars.length; i++) {
	console.log(typeof cars[i]);
	//Pour changer
}

var productTags = ['Apple','Computer','Laptop','2021 Sales'];
//Objectif : envoyer un tag d'event spécifique à GA si jamais l'article a un tag "2021 Sales"

for (var i = 0; i < productTags.length; i++) {
	if (productTags[i]==='2021 Sales'){
		console.log('Envoyer le tag Bing Ads');
  }
}
```

En JS "moderne", il existe des boucles plus optimisées / lisibles selon les cas, mais "for" permettra toujours de s'en sortir

Exercice niveau facile : TBC

Exercice niveau difficile : TBC

## Partie 5 : Les objets 

Problématique : je veux stocker les infos sur un client (nom, prénom, âge)

```javascript

var customerFirstName = 'Jean',
	customerLastName = 'Dupont',
	customerAge = 25,
	customerIsClient = true;
//Un peu redondant, non? Beaucoup de variables similaires, sans lien entre elles.

//Et si on essayait plutôt avec un tableau?
var customerArray = ['Dupont','Jean',25,true];
//Pas pratique pour stocker des valeurs sans savoir de quoi il s'agit 😣

var customerObject = {
	'last name' : 'Dupont',
	'first name' : 'Jean',
	'age' : 25,
	'isClient' : true
}
//Un "objet" est un ensemble de clés / valeurs, sans notion d'ordre (Dictionnary en Python). 

customerObject["first name"]
//Pour aller récupérer une valeur d'une clé en particulier => Ici, renvoie "Jean"

customerObject['first name'] = 'Émilie';
customerObject.age = 27;
//Pour réécrite à la volée une valeur. Les 2 écritures sont équivalentes, mais préférer la méthode avec les crochets pour les clés qui comportent des espaces & cie

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
//On peut mettre 'key', 'cle', 'toto'... C'est une variable de boucle
  console.log('clé : '+key+'  value : '+ customerObject[key]);
}
```

Exercice facile : ajouter la TVA (5%) à l'objet ci-dessous (nouvelle clé 'taxes'), sur la base de la clé "amount" :

```javascript
var transaction = {
	'id' : 6666666,
	'amount' : 26,
	'product' : 'MacBook Air 13 pouces' 
}
```

Exercice difficile : parser le data layer et le réécrire si une clé est incorrecte

## Partie 6 : les fonctions

L'intérêt des fonctions : faire du code réutilisable sans se répéter (DRY : Don't Repeat Yourself - est quasiment le principe de développement le plus important)

```javascript
//Syntaxe basique d'une fonction (on parle aussi de méthode)
function getRandom(){
	var randomNumber = Math.random();
	return randomNumber;
	//return => Valeur de retour, qui sera renvoyée lorsque la fonction sera exécutée
}

//Syntaxe basique d'une fonction - Invocation
getRandom();
//Ne pas oublier les parenthèses, pour l'instant vides

var myRandomNumber = getRandom();
//Affectation d'une variable via une fonction => D'où l'importance du "return" (renverrait undefined sinon)

//Fonction avec un argument
function getRandomUpToX(max){
	//max => Argument de la fonction
	return Math.random()*max;
}

//On appelle ensuite la fonction avec un argument
getRandomUpToX(21);

var myRandom = getRandomUpToX(18);

```

Exercice : créer une méthode qui parse le data layer suivant, et renvoie un boléen selon la présence d'un ID de transaction (transactionID)

```javascript
var dataLayer = [{
	'pageType' : 'ecommerce',
	'productID' : 321654,
	'transactionID' : 123456
}];

function hasTransaction(){
	//A compléter
	return xxxx;
}
```

## Partie 7 : Les dates

```javascript
//Générer un timestamp
var unixTimestamp = Date.now();
//Nombre de millisecondes écoulées depuis le 1er janvier 1970. 
//C'est la méthode universelle, dans à peu près n'importe quel language, pour récupérer une date

//Générer une date "explicite"
var date2 = new Date('December 17, 1995 03:24:00');

//Récupérer le mois, jour, etc...courant
date2.getDate();
date2.getMonth(); //Attention, janvier = 0, donc décembre = 11
date2.getYear();

//Mettre une date au format UTC à partir d'un jour, mois, etc...
var myUTCDate = new Date(Date.UTC(96, 1, 2, 3, 4, 5));
```

Exercice : créer une fonction qui prend en input une date de naissance au format AAAA-MM-JJ (prompt), et donne le nombre de jours depuis.

```javascript
function daysSinceBirthDate(){
	//A compléter
	return 6593;
}
```

Bonus : vérifier l'intégrité de la date envoyée par l'utilisateur (le format doit être correct) => Chercher du côté des Regex!

## Partie 8 : La manipulation du DOM et les events listeners

Rappel : les sélecteurs CSS

```css
p /*=> Toutes les balises <p>*/
.red /*=> Toutes les balises de classe 'red'*/
#product-image /*=> Toutes les balises d'ID product-image*/
ul .active /*=> Sélecteur descendant direct*/

ul > .active /*=> Sélecteur descendant global*/
	{color : 'blue';}
```

```javascript
var selector1 = document.querySelector('ul');

selector1.insertAdjacentHTML('beforeend', '<li>List item 4</li>');

var selector2 = document.querySelectorAll('h2');

var selector3 = document.getElementById('header');

selector3.style.display = 'none';
//Faire disparaître

selector3.style.display = '';
//Faire apparaître
```

Ces compétences sont cruciales pour un "vrai" dèv JS front, mais pas tant que ça côté GTM (on ne bougera pas le DOM).

A partir du moment où on comprend comment fonctionne un sélecteur CSS, GTM gère très correctement l'abstraction

Astuce : récupérer un sélecteur CSS depuis l'inspecteur Chrome

### Point déterminant : les events listeners

Tout JS (y compris GTM) fonctionne sur la base d'event listeners. Même si on n'en fera pas souvent de façon directe dans GTM, il est crucial de comprendre le principe

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

var myNewsletter = document.querySelector('#newsletter');
//équivalent var myNewsletter = document.getElementByID('newsletter');

myNewsletter.addEventListener('click',pushNLEventToDL());
```

Exercice difficile : améliorer la méthode pushNLEventToDL en passant une autre clé "buttonText" qui renvoie dynamiquement le texte de la div cliquée

## Partie 9 : Les cookies et le local storage

```javascript
//Ecrire un cookie
document.cookie = 'username=PierreDupont; expires=Thu, 18 Dec 2021 12:00:00 UTC; path=/';
//Il faut tout passer sous forme d'une string. Pas simple!
//Bon exercice pour chainer les conditions

//Lire un cookie
var allCookies = document.cookie;
//Renvoie une string qu'il faut ensuite parser ==> Bon exercice pour travailler les boucles 😀

// Enregistrer des données dans sessionStorage
localStorage.setItem('idClient', '123456789');

// Récupérer des données depuis sessionStorage
var monID = localStorage.getItem('idClient');

// Supprimer des données de sessionStorage
localStorage.removeItem('idClient');

// Le local / session storage est plus moderne, mais pas compatible avec de vieux navigateurs, et sans possibilité de contrôler finement l'expiration, et le domaine
```

Exercice niveau 1 : créer un cookie GA 'propre' (GA1.2.1232667359.1603816516) avec un random number, le timestamp courant, et une date d'expiration à 13 mois à partir du moment où il est créé.

Exercice niveau 2 : créer une méthode "gaConsent" qui prend un booléen en entrée, et fait une expiration à 12 ou 24 mois selon ce que renvoie ce booléen, en renvoyant une string utilisable pour pouvoir créer un cookie

```javascript
function gaConsent(bol){
//A vous de jouer!
}

//On doit pouvoir faire du document.cookie = gaConsent(false)
```

## Partie 10 : avant de passer sur GTM

Dans GTM, dés qu'on peut s'abstraire du JS, on le fait, mais :
- Il faut bien comprendre ce qu'il y a derrière les choses "templatisées"
- Il faut tout de même souvent faire du JS "sans filet", autant bien le faire
- Certains concepts de dèv (DRY, branches...) doivent être appliqués, même sans faire de JS à proprement parler