---
title: Microsoft Fabric API for GraphQL editor
description: Learn about the Fabric API for GraphQL editor, including where to find the editor and what the editor screen looks like.
ms.reviewer: sngun
ms.author: sngun
author: snehagunda
ms.topic: conceptual
ms.custom:
  - build-2024
ms.search.form: GraphQL query editor
ms.date: 05/21/2024
---

# Fabric API for GraphQL editor

> [!NOTE]
> Microsoft Fabric API for GraphQL is in preview.

The Fabric API for GraphQL provides a graphical in-browser GraphQL development environment, which enables an interactive playground to compose, test, and see the live results of your GraphQL queries and mutations.

To go to the editor, open the API for GraphQL item in Fabric and select **Query** at the lower left corner of your portal screen.

:::image type="content" source="media/api-graphql-editor/query-view-button.png" alt-text="Screenshot showing where the Query option appears in the lower left corner of the Fabric screen." lightbox="media/api-graphql-editor/query-view-button.png":::

You can type and execute GraphQL queries directly on the **Query** tab. Intellisense capabilities are available with a keyboard shortcut: CTRL + Space (Windows), or Command + Space (macOS). Select **Run** to execute the query and retrieve the data accordingly from the data source.

:::image type="content" source="media/api-graphql-editor/query-editor-intellisense.png" alt-text="Screenshot of the API editor screen, which has a Query tab that is divided into Run, Query variables, and Results panes." lightbox="media/api-graphql-editor/query-editor-intellisense.png":::

## Generate code

Once you tested and prototyped the desired GraphQL operation, the API editor can generate boilerplate Python or Node.js code based on the query or mutation executed in the editor. You can run the generated code locally for testing purposes and re-use parts of it in the application development process.

> [!IMPORTANT]
> The generated code uses interactive browser credentials and should be used for testing purposes only. In production, always register an application in Microsoft Entra and use the appropriate `client_id` and scopes. You can find an end-to-end example with sample code at [Connect Applications](connect-apps-api-graphql.md).

To get started, execute a query, select the **Generate code** button and chose the language accordingly:

:::image type="content" source="media/api-graphql-editor/query-editor-generate-code.png" alt-text="Screenshot of the API editor screen after opening the generate code option." lightbox="media/api-graphql-editor/query-editor-generate-code.png":::

You can then copy the generated code and save it as a file in a local folder. Depending on the language of choice, follow simple steps to test locally:

##### Python

1. Create a virtual environment with the command `python -m venv .venv`
2. Activate the `venv` using `.venv\Scripts\activate` or `source .venv/bin/activate`
3. Install the required dependency with the command `pip install azure.identity`
4. Execute the code with `python <filename.py>`

##### Node.JS

1. In the same folder as the file you saved, create a `package.json` file with the following content:
```json
{
  "type": "module",
  "dependencies": { 
  }
}
```
2. Run `npm install --save @azure/identity` or similar command in your package manager of choice to install the latest version of the identity library.
3. Execute the code with  `node <filename>.js`

## Development of queries and mutations

Review the following short GraphQL schema, which defines a single `Post` type with queries to read a single post or list all posts. It also defines mutations to create, update, or delete posts supporting all CRUDL (create, read, update, delete, list) use cases.

```json
type Post {
  id: ID!
  title: String!
  content: String!
  author: String!
  published: Boolean
}

type Query {
  getPost(id: ID!): Post
  getAllPosts: [Post]
}

type Mutation {
  createPost(title: String!, content: String!, author: String!): Post
  updatePost(id: ID!, title: String, content: String, author: String, published: Boolean): Post
  deletePost(id: ID!): Boolean
}
```

You can read the data exposed via GraphQL using any query defined in the schema. The `getPost` query should look like the following example.

```json
query MyQuery {
  getPost(id: "1234") {
    title
    content
    author
  }
}
```

*Response:*

```json
{
  "data": {
    "getPost": {
      "title": "First Post",
      "content": "This is my first post.",
      "author": "Jane Doe"
    }
  }
}
```

Write data using mutations like `createPost` to create a post with the required parameters.

```json
mutation MyMutation {
  createPost(title: "Second post", content: "This is my second post", author: "Jane Doe", published: false) {
    id
    title
    content
    author
  }
}
```

*Response:*

```json
{
  "data": {
    "createPost": {
      "id": "5678",
      "title": "Second Post",
      "content": "This is my second post.",
      "author": "Jane Doe"
    }
  }
}
```

## Query variables

Use the **Query variables** pane on the right side of the **Query** tab to pass any parameters as variables to your queries or mutations. Variables work the same way as variables in any other programming language. Each variable needs to be declared with a name that is used to access the value stored in it. With the previous mutation example, you can modify it slightly to use query variables.

```json
mutation MyMutation ($title: String!, $content: String!, $author: String!){
  createPost(title: $title, content: $content, author: $author) {
    id
    title
    content
    author
  }
}
```

Define the variables in the pane like the following example.

```json
    {
      "id": "5678",
      "title": "Second Post",
      "content": "This is my second post.",
      "author": "Jane Doe"
    }
```

Variables make the mutation code cleaner and easier to read, test, and modify the parameters.

## Related content

- [More query and mutation examples](/azure/data-api-builder/graphql#supported-root-types)
- [Fabric API for GraphQL schema view and Schema explorer](graphql-schema-view.md)
