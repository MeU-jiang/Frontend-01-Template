# 每周总结可以写在这里

-  function convertStringToNumber(str, radix = 10) {
-     let num = 0;
-     let fraction = 0;
-     let hasEx = /[eE](\d+)/g.test(str);
-     let exNum = hasEx ? +/[eE](\d+)/g.exec(str)[1] : 1;
-     let exIndex = hasEx ? /[eE](\d+)/g.exec(str).index : str.length;
-     let isFloat = str.includes('.');
-     let dotIndex = isFloat ? str.indexOf('.') : str.length;
-     function getCodePoint(s) {
-       return s.codePointAt(0);
-     }
-     for (let i = 0; i < dotIndex; i++) {
-       num *= radix;
-       num += getCodePoint(str[i]) - getCodePoint('0');
-     }
-     for (let i = dotIndex + 1; i < exIndex; i++) {
-       fraction *= radix;
-       fraction += getCodePoint(str[i]) - getCodePoint('0');
-     }
-     return [num, fraction, exNum];
-   }

-    function convertNumberToString (number, x) {
-      let integer = Math.floor(number);
-      let fraction = number - integer;
-      console.log('fraction', fraction);
-      let string = '';
-      while(integer > 0) {
-        string = String(integer % x) + string;
-        integer = Math.floor(integer / x);
-      }
-      if (fraction) {
-        string = string + '.';
-      }
-      while(fraction > 0) {
-        let flag = Math.floor(fraction * x);
-        string += String(flag);
-        fraction =  fraction * x - Math.floor(fraction * x);
-      }
-      return string;
-    }
-    console.log(convertNumberToString(122.121, 10));


```
function convertStringToNumber(str, radix = 10) {
    let num = 0;
    let fraction = 0;
    let hasEx = /[eE](\d+)/g.test(str);
    let exNum = hasEx ? +/[eE](\d+)/g.exec(str)[1] : 1;
    let exIndex = hasEx ? /[eE](\d+)/g.exec(str).index : str.length;
    let isFloat = str.includes('.');
    let dotIndex = isFloat ? str.indexOf('.') : str.length;
    function getCodePoint(s) {
      return s.codePointAt(0);
    }
    for (let i = 0; i < dotIndex; i++) {
      num *= radix;
      num += getCodePoint(str[i]) - getCodePoint('0');
    }
    for (let i = dotIndex + 1; i < exIndex; i++) {
      fraction *= radix;
      fraction += getCodePoint(str[i]) - getCodePoint('0');
    }
    return [num, fraction, exNum];
  }
  ```
