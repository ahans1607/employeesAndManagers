# Class Inheritance

This mini-project will apply the skills you learned in last night's inheritance
reading.

## Learning Goals

* Understand how a child class inherits from a parent class
* Know how to override a parent class's method
* Know when and how to use `super` and `extends`

## Phase 1: Define Employee and Manager classes

Create a project directory. In that project directory, set up two files for your
employee and manager classes: `Employee.js` and `Manager.js`. In the
`Employee.js` file, define an `Employee` class with a constructor that sets an
employee's name, title, salary, and boss. 

In the `manager.js` file, define another class, `Manager`, that extends
`Employee`. `Manager` should have an attribute that holds an array of all
employees assigned to the manager. Think of how to use CommonJS modules to
export the `Employee` class from the `employee.js` file into the `manager.js`
file.

Define a method, `bonus(multiplier)` in the `Employee` class. Non-manager
employees should calculate their bonus like this:

```
bonus = (employee salary) * multiplier
```

Define another method, `bonus(multiplier)` in the `Manager` class. The
`bonus(multiplier)` method defined in the `Manager` class will override the
`bonus(multiplier)` method defined in the `Employee` class. Managers should get
a bonus based on the total salary of all of their employees, as well as the
manager's employees' employees, and the employees' employees' employees, etc.
Manager employees should calculate their bonus like this:

```
bonus = (total salary of all employees) * multiplier
```

You can extract the logic of calculating the total salary of all a manager's
employees into a `totalSubsalary()` method. To do this, you can iterate through
each of a manager's employees, checking if the employee is an instance of a
`Manager` or not, and calculate the `totalSubsalary`.

> **Note**: managers might report to higher level managers.

If an employee is a `Manager`, the `totalSubsalary` will include their salary as
well as the employee's `totalSubsalary`. If an employee is **not** a `Manager`,
the `totalSubsalary` will only include their salary.

## Phase 2: Testing

Imagine you have a company structured like this:

| Name     | Salary  | Title      | Boss   |
| -------- | ------- | ---------- | ------ |
| Hobbes   | 1000000 | Founder    | null   |
| Calvin   | 130000  | Director   | Hobbes |
| Susie    | 100000  | TA Manager | Calvin |
| Lily     | 90000   | TA         | Susie  |
| Clifford | 90000   | TA         | Susie  |

Take a moment to instantiate some employees and manager. If you copy the
following statements and run your `manager.js` file with `node manager.js`, you
should have bonuses like this:

```js
console.log(hobbes.bonus(0.05)); // 70500
console.log(calvin.bonus(0.05)); // 20500
console.log(susie.bonus(0.05)); // 14000
console.log(lily.bonus(0.05)); // 4500
console.log(clifford.bonus(0.05)); // 4500
```

