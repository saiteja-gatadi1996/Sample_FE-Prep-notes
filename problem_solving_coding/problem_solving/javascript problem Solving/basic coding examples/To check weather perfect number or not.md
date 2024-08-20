## To check weather perfect number or not

**Approach Taken**

1. the param you pass to verify whether the number is perfect number or not, perform a basic for loop starting from 1 to param/2 (ex: 1 to number/2)
2. if number% i===0 then store into a variable for adding (ex: temp = temp + i) Ex: 28% 1, 28%2, 28%4 becomes zero
3. so to check if your number is perfect or not, then your stored variable if(temp === number ) it is a perfect number

```js
function is_perfect(number) {
  var temp = 0;
  for (var i = 1; i <= number / 2; i++) {
    if (number % i === 0) {
      console.log(i); //1, 2, 4, 7, 14
      temp += i;
    }
  }
  if (temp === number && temp !== 0) {
    console.log('It is a perfect number.');
  } else {
    console.log('It is not a perfect number.');
  }
}
is_perfect(28);
```
