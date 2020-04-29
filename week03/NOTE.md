# 每周总结可以写在这里
1.convertStringToNumber
```
function convertStringToNumber (string, radix = 10) {
  if (radix > 10) {
    return
  }
  let flag = /e|E/.test(string)
  if (!flag) {
    let chars = string.split('')
    let number = 0
    let i = 0
    while (i < chars.length && chars[i] != '.') {
      number = number * radix
      number += chars[i].codePointAt(0) - '0'.codePointAt(0)
      i++
    }
    if (chars[i] === '.') {
      i++
    }
    let fraction = 1
    while (i < chars.length) {
      fraction /= radix
      number += (chars[i].codePointAt(0) - '0'.codePointAt(0)) * fraction
      i++
    }
    return number
  } else {
    let logNumber = Number(string.match(/\d+$/)[0])
    let number = string.match(/^[\d\.]+/)[0].replace(/\./, '')
    if (/e-|E-/.test(string)) {
      return Number(number.padEnd(logNumber + 1, 0))
    } else {
      return Number(number.padStart(logNumber + number.length, 0).replace(/^0/, '0.'))
    }
  }
}
```
2.convertNumberToString
```
  function convertNumberToString (number, x) {
    let integer = Math.floor(number);
    let fraction = number - integer;
    console.log('fraction', fraction);
    let string = '';
    while(integer > 0) {
      string = String(integer % x) + string;
      integer = Math.floor(integer / x);
    }
    if (fraction) {
      string = string + '.';
    }
    while(fraction > 0) {
      let flag = Math.floor(fraction * x);
      string += String(flag);
      fraction =  fraction * x - Math.floor(fraction * x);
    }
    return string;
  }
  console.log(convertNumberToString(122.121, 10));
```
