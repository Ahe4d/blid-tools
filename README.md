# BLID Tools
A set of of tools for working with [Blockland](https://blockland.us)'s authentication system.

## Features
* Generating an authentication key
* Converting from between a key ID & BLID

## Example Usage
```js
const blidTools = require('blid-tools');

// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min; //The maximum is exclusive and the minimum is inclusive
}

function insertNthChar(string,chr,nth) {
  var output = '';
  for (var i=0; i<string.length; i++) {
    if (i>0 && i%4 == 0)
      output += chr;
    output += string.charAt(i);
  }

  return output;
}

function getNewKey() {
  let key = insertNthChar(blidTools.generateKey(),'-', 4); // will return a randomly generated key, and formatted properly
  let keyid = blidTools.BLIDToKey(getRandomInt(1, 999999));

  return keyid + `-${key}`; 
}

let myKey = getNewKey();

console.log(`My key is '${myKey}', and my ID is ${blidTools.keyToBLID(myKey.substr(0,5))}, don't tell anyone!`) // My key is 'ABLQ6-XL3T-74EM-PRZS', and my ID is 43484 don't tell anyone!
```

## Disclaimer
This package and its owner are not endorsed by Blockland, Blockland LLC or their respective owners. This package will **NOT** grant you a working key for Blockland. It is meant to help those who are interested in working with Blockland's authentication, not those looking to acquire a license to the game free of charge.