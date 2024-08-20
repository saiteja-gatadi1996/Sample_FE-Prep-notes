## Execute all the tasks in such a way that if there are no dependencies then the tasks can be started but if there are any dependencies then those tasks should execute once the dependency are completed

```js
 For eg:-
  for the below tasks Objet the output should be in the below way:-
  d done
  b done
  a done
  c done
  e done
```

```js
const tasks = {
  a: {
    job: function (finish) {
      setTimeout(() => {
        console.log("a done");
        finish();
      }, 5000);
    }
  },
  b: {
    job: function (finish) {
      setTimeout(() => {
        console.log("b done");
        finish();
      }, 2000);
    },
    dependencies: []
  },
  c: {
    job: function (finish) {
      setTimeout(() => {
        console.log("c done");
        finish();
      }, 3000);
    },
    dependencies: ["a", "b"]
  },
  d: {
    job: function (finish) {
      setTimeout(() => {
        console.log("d done");
        finish();
      }, 1000);
    },
    dependencies: []
  },
  e: {
    job: function (finish) {
      setTimeout(() => {
        console.log("e done");
        finish();
      }, 2000);
    },
    dependencies: ["a", "b"]
  },
  f: {
    job: function (finish) {
      setTimeout(() => {
        console.log("f done");
        finish();
      }, 2000);
    },
    dependencies: ["d"]
  }
};
```

## Solution:

```js
// Function to check if all elements in arr2 are included in arr1
const checkIntersection = (arr1 = [], arr2 = []) => {
  return arr2.every((e) => arr1.includes(e));
};

function runTasks(tasks) {
  // Get all task keys as a list
  const tasksList = Object.keys(tasks);

  // Filter out tasks that have no dependencies
  const inDependantTasks = tasksList.filter(
    (ele) => !tasks[ele].dependencies || !tasks[ele].dependencies.length
  );

  // Filter out tasks that do have dependencies
  const dependantTasks = tasksList.filter(
    (ele) => !inDependantTasks.includes(ele)
  );

  // Array to keep track of completed tasks
  const completedTasks = [];
  // Array to keep track of tasks currently being executed
  let inProgressTasks = [];

  // Function called when a task is completed
  const completeFunction = (taskName) => {
    // Add the completed task to the completedTasks array
    completedTasks.push(taskName);
    // Remove the completed task from inProgressTasks
    inProgressTasks = inProgressTasks.filter((ele) => ele !== taskName);

    // If not all tasks are completed yet
    if (completedTasks.length !== tasksList.length) {
      // Check which dependent tasks can now be executed
      // These three conditions together determine whether a dependent task is ready to be executed:
      const isDependenciesCompleted = dependantTasks.filter(
        (el) =>
          checkIntersection(completedTasks, tasks[el].dependencies) && //This condition checks if all the dependencies of the task el have been completed.
          !completedTasks.includes(el) && //This condition checks to make sure the task el itself has not already been completed
          !inProgressTasks.includes(el) //This condition ensures the task el is not currently in progress.
      );

      // If there are tasks that can now be executed
      if (isDependenciesCompleted?.length) {
        // Execute those tasks
        isDependenciesCompleted.forEach((ele) =>
          tasks[ele].job(() => completeFunction(ele))
        );
        // Add them to the inProgressTasks list
        inProgressTasks = [...inProgressTasks, ...isDependenciesCompleted];
      }
    } else {
      // If all tasks are completed, log it to the console
      console.log('all tasks completed');
    }
  };

  // Start all independent tasks
  inDependantTasks.forEach((ele) =>
    tasks[ele].job(() => completeFunction(ele))
  );
  // Mark them as in progress
  inProgressTasks = [...inProgressTasks, ...inDependantTasks];
}

// Start running the tasks
runTasks(tasks);
```