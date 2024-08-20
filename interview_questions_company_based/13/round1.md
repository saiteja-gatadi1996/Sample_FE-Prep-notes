1.	Arrow function and what is the difference apart from syntax?
2.	Call, apply bind (write down the code for one of them)
3.	Generator Function and write a range Generator functions
4.	Real time example of Generator Functions?
5.	ES6 features
6.	Write down the code for spread operator, rest operator and Object destructuring?
7.	Difference between forEach and map?
8.	Difference between Object.assign(), Object.create()? Which one mutates the data ?
9.	What is a Promise ?
10.	Write a function component in react which returns a lazy loaded Button Component and add the Suspense with fallback UI?
11.	What is Error Boundary, How can we write a separate Error Boundary Component?
12.	What is Redux, Why Redux , Core principles of redux?
13.	Write down a basic sum function using Typescript and how do you accept params in either string or number?

<details>
<summary>
View Answer
</summary>

```js
function sum(a: number | string, b: number | string){
  // Convert both parameters to numbers before summing them up.
  return a + b;
}

// Usage examples:
console.log(sum(1, 2)); // Outputs: 3
```
</details>

14.	What are Generics functions (inside Typescript), can you write down types ?
15.	Abstract function means ?
16.	Software Principles (DRY, KISS) how do you implemented in your codebase
17.	Git hook (pre commit, husky)
18.	SOLID Principles
19.	Write down test cases ? What does beforeEach and beforeAll do ?
20.	Difference between mock vs spy in testing?
21.	Explain Testing Pyramid? 
22.	Differences between Integration Testing vs End to End testing?
23.	Which tool you have used for above of them ?
24.	What do we mean by code coverage ? How do you measure code coverage? 
25.	What is meant by OWASP top10?
26.	What is meant by CSP, XSS (where do we set these CSP headers? In Client or Server)
27.	What is meant by CORS? (Where do we set them)
28.	DDDS ? 
29.	Explain me the various ways of Performance Optimization that you can do at any level (ex: CSS, JS, HTML)
30.	What is CRP?
31. What are memory leaks in react ? Why do they happen ?
32. Promise.all vs Promise.any vs Promise.race?
33. How do you configure typescript in your project?
34. How many ways you can create an object ?
35. What does we have in typescript .tsconfig.json? can you explain them?
36. Problem Solving 

```js
// output the longest prefix that is found in the array of arguments
function lcp(arr) {
  
}

// Test cases
console.log(lcp(['flower', 'flag', 'flutter'])); // Test Case 1 should return 'fl'
console.log(lcp(['racedog', 'car', 'racecar'])); // Test Case 2 should return ''
```
