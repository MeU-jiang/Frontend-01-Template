# 每周总结可以写在这里

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
