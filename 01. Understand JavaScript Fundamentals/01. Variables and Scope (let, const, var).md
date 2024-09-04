In JavaScript, variables are used to store values, and how they behave depends on how they are declared. There are three main ways to declare variables: `var`, `let`, and `const`. These declarations have different scoping rules, behavior, and usage, particularly in the context of block scope, function scope, and global scope.

### 1. `var`
- **Scope**: `var` is function-scoped or globally scoped, meaning it is available throughout the entire function or globally if declared outside any function.
- **Hoisting**: Variables declared with `var` are **hoisted** to the top of their scope. This means that a `var` variable can be referenced before it is declared, though it will be `undefined` until it is initialized.
- **Redeclaration**: `var` allows redeclaration of the same variable in the same scope without errors.
  
  Example:
  ```javascript
  console.log(a); // undefined (due to hoisting)
  var a = 10;
  console.log(a); // 10

  var a = 20; // Redeclaration is allowed
  console.log(a); // 20
  ```

### 2. `let`
- **Scope**: `let` is block-scoped, which means the variable is only accessible within the block (enclosed by `{}`) in which it is defined. This includes loops and `if` blocks.
- **Hoisting**: Variables declared with `let` are also hoisted, but unlike `var`, they are not initialized until they are assigned a value, leading to a **Temporal Dead Zone** where they cannot be accessed before declaration.
- **Redeclaration**: `let` does not allow redeclaration of the same variable in the same scope.

  Example:
  ```javascript
  {
    let b = 10;
    console.log(b); // 10
  }
  // console.log(b); // Error: b is not defined (block scope)

  let c = 5;
  let c = 10; // Error: Identifier 'c' has already been declared
  ```

### 3. `const`
- **Scope**: Like `let`, `const` is also block-scoped.
- **Hoisting**: `const` is hoisted, but it also cannot be accessed before declaration, similar to `let`, due to the Temporal Dead Zone.
- **Immutability**: Variables declared with `const` must be initialized at the time of declaration, and the value cannot be reassigned. However, for objects or arrays, the properties or elements can be changed (mutated).
- **Redeclaration**: `const` does not allow redeclaration of the same variable in the same scope.

  Example:
  ```javascript
  const x = 100;
  // x = 200; // Error: Assignment to constant variable

  const arr = [1, 2, 3];
  arr.push(4); // This is allowed as the array is mutable
  console.log(arr); // [1, 2, 3, 4]

  const y; // Error: Missing initializer in const declaration
  ```

### Key Differences

| Feature             | `var`                         | `let`                         | `const`                       |
|---------------------|-------------------------------|-------------------------------|-------------------------------|
| **Scope**           | Function or global scope       | Block scope                   | Block scope                   |
| **Hoisting**        | Hoisted, initialized as `undefined` | Hoisted but not initialized   | Hoisted but not initialized   |
| **Redeclaration**   | Allowed                       | Not allowed                   | Not allowed                   |
| **Reassignment**    | Allowed                       | Allowed                       | Not allowed (for primitives)  |
| **Temporal Dead Zone** | No                           | Yes                           | Yes                           |

### Best Practices:
- Use `const` by default unless you know the variable’s value will change.
- Use `let` if the value will change.
- Avoid using `var` because its scoping rules can lead to bugs that are hard to track down.

These rules help make JavaScript code more predictable and easier to understand.