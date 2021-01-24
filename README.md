# Javascript pour l'analytics et le tag management

## Déclarer et manipuler les variables

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

//
```