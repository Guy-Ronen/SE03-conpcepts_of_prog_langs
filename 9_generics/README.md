# Generics

Generics are a programming concept that allows types to be parameterized. They provide a way to write reusable code that can work with different types, without the need to duplicate code. 

## Generic example with TypeScript

Generics provide a way to write reusable code that can work with different types without duplicating it. They can be used in functions, classes, and interfaces, and provide compile-time type safety.

Here's an example of how generics can be used in an API response in TypeScript:

```typescript
interface ApiResponse<T> {
  success: boolean;
  message: string;
  data: T; // T is a generic type parameter which can be replaced with any type like User or User[]
}

interface User {
  id: number;
  name: string;
  email: string;
}

// A function that simulates making an API call to retrieve a user
function getUser(): ApiResponse<User> {
  const user: User = {
    id: 123,
    name: "John Doe",
    email: "johndoe@example.com",
  };

  return {
    success: true,
    message: "User retrieved successfully",
    data: user // in this case, T is replaced with User 
  };
}

// A function that simulates making an API call to retrieve a list of users
function getUsers(): ApiResponse<User[]> {
  const users: User[] = [
    { id: 1, name: "John Doe", email: "johndoe@example.com" },
    { id: 2, name: "Jane Smith", email: "janesmith@example.com" },
  ];
  return {
    success: true,
    message: "Users retrieved successfully",
    data: users // in this case, T is replaced with User[] 
  };
}

const userResponse = getUser();
console.log(userResponse.data.name); // Output: John Doe


const usersResponse = getUsers();
console.log(usersResponse.data); 
/*
Output: [ { id: 1, name: 'John Doe', email: 'johndoe@example.com' },
        { id: 2, name: 'Jane Smith', email: 'janesmith@example' } ]
*/
```

In this example, the `ApiResponse` interface is defined using a generic type parameter `T`. 
This allows the response data to be of any type, making the interface reusable for different types of API responses.

The `getUser` and `getUsers` functions both return an `ApiResponse` with different data types (`User` and `User[]`), demonstrating the flexibility of the generic type parameter.
