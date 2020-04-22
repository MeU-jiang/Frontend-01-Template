# 每周总结可以写在这里





- 作业：
- 匹配number直接量
- /（^-？\d*\。？\d+$)|(^[01]+$)|（^[0-7]+$)|((^0[XX][一-为fA-F0-9]{1，2}$)|(^[一- 为fA-F0-9]{1，2}$))/;
- 匹配utf-8的函数
- function encodeUtf8(utf) {
- const code = encodeURIComponent(utf);
- const bytes = [];
- for (var i = 0; i < code.length; i++) {
  - const c = code.charAt(i);
  - if (c === '%') {
    - const hex = code.charAt(i + 1) + code.charAt(i + 2);
    - const hexVal = parseInt(hex, 16);
    - bytes.push(hexVal);
    - i += 2;
  - } else bytes.push(c.charCodeAt(0));
- }
- return bytes;
- }
- 写一个正则表达式，匹配所有的字符串直接量，单引号和双引号
- "(?:[^"\n\\\r\u2028\u2029]|\\(?:['"\\bfnrtv\n\r\u2028\u2029]|\r\n)|\\x[0-9a-fA-F]{2}|\\u[0-9a-fA-F]{4}|\\[^0-9ux'"\\bfnrtv\n\\\r\u2028\u2029])*"
