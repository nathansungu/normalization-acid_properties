#   PRISMA
## What is prisma?
Prisma is a modern, open-source ORM (Object-Relational Mapping) tool that makes it easier for developers to work with databases.

### Set up Prisma in your project.

1. Initialize a new Node.js project:<br>
**`npm init -y`**
1. Install the Prisma as a development option by passing flag D:<br>
**`npm install prisma -D`**
1. Prisma allows for the use of many databases like Postgres, Mysql, or MongoDb. Prisma sets up your tables the same way regardless of the database you use. 
1. Lets initialize a new Prisma project and use Postgresql as our provider:<br><br>
`npx prisma init --datasource-provider sqlite` <br><br>
1. This will create a new prisma folder and a .env file for us. Inside of that folder, we will have a schema.prisma file. This is where we will define our data model. If you open the .env file, we should see the following:

## Special annotations:

1. `@id`: Marks a field as the primary key.
1. `@default`: Sets a default value, like autoincrement() for id or now() for timestamps.
1. `@relation`: Defines relationships between models (e.g., Post belongs to User).
1. `@unique`: Ensures the field’s values are unique (e.g., email in User).
1. `@map `: Maps the attribute to a particular name provided. 

1. `?`: Specify that a field is optional.(e.g., email?)


### Define a database model.
 To define a model for aparticular table we use the key word model then pass then name as below.

**contents table**

 ```sql
     model Post {
        id Int  @id @default(autoincrement()) @map("content_id")
        title     String @map("title")
        content   String? @map("titile")
        published Boolean  @default(false)@map("isPublished")
        author User @relation(fields: [authorId], references: [id])
        authorId  Int @map("author_id")
        createdAt DateTime @default(now())
}
```

**User table**
```sql
    model User {
    id Int @id @default(autoincrement()) @map("user_id")
    name String @map("user_name")
    email String @unique @map("email_address")
    posts Post[] @map("post")
}
```

After defining the models we save the changes to database by running migrations.

```sql
    npm prisma migrate dev --name "create users table and posts table"

```

The ``` --name ``` flag allows as to name our migrations. 

### Perform CRUD (Create, Read, Update, Delete) operations.

To run queries open a js file and import  PrismaClient  from '@prisma/client';

### Example
```JS
    import { PrismaClient } from '@prisma/client';
    const client =PrismaCLient
```
Now you can run any code in the file using the models we declared with prisma.

**Create** <br>
Used to insert a new record into database.
### Example
```js
    async function createUser(){
        const newUser = await client.user.create({
            data:{
                emai: "user@gmail.com",
                name: "James Maina"                 
            }
        })
    }
```

This will create a user with an auto increment id.

## Read-Find a record
 This includes methods such as:<br>
- findone
- findMany
- findAll
### Example 
```js
    async function findUser(){
        const userById = await client.user.findOne({
            where:{id: "pass here pk"}
            include: {
            posts: true,
            },
        })
    }
```
```js
    const posts = await client.post.findMany();
    console.log(posts);
```

## Update records <br>

### Example
```js
    async function updateUser(){
        const updateUser = await client.user.update({
            where:{id: "pass id"},
            data:{name: "james", email: "james@gmail.com"}
        })
    }
```

## Delete Record <br>

### Example
```js
    async function deleteUser(){
        const deleteRecord = await client.user.delete({
            where:{id: "pass id to delete"}
        })
    }
```

### Prisma studio.

It is a GUI that allows you to view and edit data in your database.

To run prisma studio use:<br>
```
    npx prisma studio
```

click on the server port provided to open in a web browser.


![alt prisma studio image](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*nNW4FkhZbCWEoWVf-30JSg.png)

