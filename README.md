# Node Projects

## REST API with Node JS

### Basic Commands

- `npm init -y`
  initialize a project and also do basic setup of the package.json file.

- `npm i --save express`
  To install express.

- `npm i --save -dev nodemon`
  prevent every time reload and serve everytime.

## HTTP Methods

- GET : `/users` find all users
- POST : `/users` create a user
- GET : `/users/:id` finds user details
- DELETE : `/users/:id` delete a user
- PATCH : `/users/:id` Update a user (Partial Update)
- PUT : `/users/:id/` Completely update a user (Completely overwrite existing)

### Get all Users

`let users = [];`

`router.get("/", getUsers);`

```
export const getUsers = (req, res) => {
  res.send(users);
};
```

### Create a new User

`router.post("/", createUser);`

```export const createUser = (req, res) => {
  const user = req.body;

  users.push({
    ...user,
    id: uuidv4(),
  });
  res.send(`User with the name ${user.firstName} added to the database`);
};
```

### Get specific User

`router.get("/:id", getUser);`

```
export const getUser = (req, res) => {
  const { id } = req.params;
  const foundUser = users.find((user) => user.id === id);

  res.send(foundUser);
};
```

### Delete specific user

`router.delete("/:id", deleteUser);`

```
export const deleteUser = (req, res) => {
  const { id } = req.params;
  users = users.filter((user) => user.id !== id);

  res.send(`User with the id ${id} was deleted from the database`);
};
```

### Edit Details of specific user

`router.patch("/:id", updateUser);`

```
export const updateUser = (req, res) => {
  const { id } = req.params;
  const { firstName, lastName, age } = req.body;

  const user = users.find((user) => user.id === id);

  firstName && (user.firstName = firstName);
  lastName && (user.lastName = lastName);
  age && (user.age = age);

  res.send(`User with the id ${id} has been updated.`);
};
```
