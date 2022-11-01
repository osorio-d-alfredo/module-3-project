//dom 
const passwordEl = document.getElementById('password');
const lengthEl = document.getElementById('length');
const uppercaseEl = document.getElementById('uppercase');
const lowercaseEl = document.getElementById('lowercase');
const numbersEl = document.getElementById('numbers');
const symbolsEl = document.getElementById('symbols');
const generateEl = document.getElementById('generate');


const randomFunc = {
  lower: getRandomLower,
  upper: getRandomUpper,
  number: getRandomNumber,
  symbol: getRandomSymbol,
};

generateEl.addEventListener('click', () => {
  const length = +lengthEl.value;
  const hasLower = lowercaseEl.checked;
  const hasUpper = uppercaseEl.checked;
  const hasNumber = numbersEl.checked;
  const hasSymbol = symbolsEl.checked;

  passwordEl.innerText = generatePassword(
    hasLower,
    hasUpper, 
    hasNumber, 
    hasSymbol, 
    length
    );
});

function generatePassword(lower, upper, number, symbol, length) {
  // password generation
  // 1. formats the password
  // 2. in case of lower values, makes it possible to make password length of 1 without mistakes
  
  let generatedPassword= '';
  const typesCount = lower + upper + number + symbol;

  const typesArr = [{lower}, {upper}, {number}, {symbol}].filter(
    item => Object.values(item)[0]
  );

  if(typesCount===0){
    return'';
  }

  for(let i = 0; i < length; i +=typesCount){
    typesArr.forEach(type =>{
      const funcName = Object.keys(type)[0];
      generatedPassword += randomFunc[funcName]();

    });
  }

  const finalPassword = generatedPassword.slice(0, length);
  return finalPassword;
}

// // Get references to the #generate element
// https://owasp.org/www-community/password-special-characters
// https://www.w3schools.com/html/html_charset.asp

function getRandomLower() {
  return String.fromCharCode(Math.floor(Math.random()* 26) + 97)
}

function getRandomUpper() {
  return String.fromCharCode(Math.floor(Math.random()* 26) + 65)
}

function getRandomNumber() {
  return String.fromCharCode(Math.floor(Math.random()* 10) + 48)
}

function getRandomSymbol() {
  const symbols = ' !@#$%^&*(){}[]=,.<>/';
  return symbols[Math.floor(Math.random() * symbols.length)];

}
