### Merge Results of Promises

```js
//Step 1: Create Mock APIs with the array values
function createMockApi(students) {
  return new Promise((resolve) => {
    resolve(students);
  });
}

// api1, api2 are fulfilled promises
const api1 = createMockApi([
  { name: 'ABC', marks: '98%', registrationId: '1234' },
  { name: 'DEF', marks: '88%', registrationId: '1235' },
  { name: 'GHI', marks: '78%', registrationId: '1236' },
]);

const api2 = createMockApi([
  { name: 'JKL', marks: '68%', registrationId: '1237' },
  { name: 'MNO', marks: '58%', registrationId: '1238' },
  { name: 'ABC', marks: '98%', registrationId: '1234' }, // Duplicate
]);

//Step 2: Merge and Remove Duplicates
function mergeAndRemoveDuplicates(api1Data, api2Data) {
  const uniqueStudents = new Map();

  [...api1Data, ...api2Data].forEach((student) => {
    if (!uniqueStudents.has(student.registrationId)) {
      uniqueStudents.set(student.registrationId, student);
    }
  });

  return Array.from(uniqueStudents.values());
}

//Step 3: Combine and Execute Promises
Promise.all([api1, api2])
  .then(([api1Data, api2Data]) => {
    //api1Data and api2Data are nothing but arrays
    const mergedData = mergeAndRemoveDuplicates(api1Data, api2Data);
    console.log(mergedData);
  })
  .catch((error) => console.error('An error occurred:', error));
```

```js
//Output:
[
  { name: 'ABC', marks: '98%', registrationId: '1234' },
  { name: 'DEF', marks: '88%', registrationId: '1235' },
  { name: 'GHI', marks: '78%', registrationId: '1236' },
  { name: 'JKL', marks: '68%', registrationId: '1237' },
  { name: 'MNO', marks: '58%', registrationId: '1238' },
];
```
