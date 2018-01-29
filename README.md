# wBitmask [![Build Status](https://travis-ci.org/Wandalen/wBitmask.svg?branch=master)](https://travis-ci.org/Wandalen/wBitmask)
The module in JavaScript provides an easy way to manage boolean maps.

## Bitmask
Bitmask is a sequence of bits that we can use to store different data in a single value.
For example, we can store boolean options flags from map in a single integer.
[More](https://en.wikipedia.org/wiki/Mask_(computing)) about bitmask.

By using bitwise operations we can easily get needed bit(s) and set to or compare with value of our variable. For example, by using shift operators and bitwise AND we can get boolean value of our flag masked in a number and set it to our property in a map.
[More](https://en.wikipedia.org/wiki/Bitwise_operation) about bitwise operations.

## Installation
```terminal
npm install wBitmask
```
## Usage
```javascript

var _ = wTools;

/*define array of possible names and bit values, that can vary*/
var defaultFieldsArray =
[

  { hidden : false },
  { system : false },
  { terminal : true },
  { directory : false },
  { link : true },

];

/*create new instance of wBitmask by passing options object with array( defaultFieldsArray ) to the constructor*/
var bitmask = wBitmask
({
  defaultFieldsArray : defaultFieldsArray
});

console.log( 'bitmask' )
console.log( bitmask.toStr() );
/*
bitmask
{
  hidden : false,
  system : false,
  terminal : true,
  directory : false,
  link : true
}
*/

/*define our boolean map*/
var originalMap =
{
  hidden : 1,
  terminal : 0,
  directory : 1,
}

console.log( 'originalMap :\n' + _.toStr( originalMap ) );
/*originalMap :
{ hidden : 1, terminal : 0, directory : 1 }*/

/*Convert boolean map into  32-bit number bitmask*/
var word = bitmask.mapToWord( originalMap );

console.log( 'word : ' + word );
/*word : 25*/

/*Convert 32-bit number bitmask into boolean map */
var restoredMap = bitmask.wordToMap( word );

console.log( 'restoredMap :\n' + _.toStr( restoredMap ) );
/*restoredMap :
{
  hidden : true,
  system : false,
  terminal : false,
  directory : true,
  link : true
}*/
```






