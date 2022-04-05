# NextJS
[Interactive Tutorial](https://nextjs.org/learn/foundations/about-nextjs)

key difference between using vanilla JS and React is that React allows us to program declaratively instead of imperatively: i.e. we don't need to know the specifics of __how__ we should manipulate the DOM to get what we want, just that we want a particular resulting state.
```javascript
// declarative (React) code
<script type="text/jsx">
  const app = document.getElementById("app")
  ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app)
</script>

// imperative code ...
<script type="text/javascript">
  const app = document.getElementById('app')
  const header = document.createElement('h1')
  const headerContent = document.createTextNode('Develop. Preview. Ship. 🚀')
  header.appendChild(headerContent)
  app.appendChild(header)
</script>
```

## Some React Refreshers
[Steps to React Rendering](https://beta.reactjs.org/learn/render-and-commit): trigger, recursively call the components, commit to the DOM

[React Refs](https://beta.reactjs.org/learn/referencing-values-with-refs): sort of like state except they don't trigger re-renders when they change and are only useful when the value being updated isn't displayed

 ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fsecond-jeff%2F4VuC_Rpl26.27.16%20AM.png?alt=media&token=3d06d470-8c06-48df-9301-f3b8154de6c4)
    
[Using Context to Pass Deeply Nested Data](https://beta.reactjs.org/learn/passing-data-deeply-with-context): when you need a prop passed down to many children consider making it "context" that children just inherit and can use

## React -> NextJS
NextJS is like [Gatsby](https://www.gatsbyjs.com/) - it takes UI primitives that a library like React expose and gives us an easy framework that stitches those building blocks to make a fully-fledged application

### Core Framework Utilities:
**Compiling**: Take dev-readable code and translate it into machine-readable code
**Minifying**: Optimize app by removing/stripping non-essential code (keeping functionality)
**Bundling**: Interpret web dependencies and modularize the app
**Code-Splitting**: Optimize initial load time by only loading the code that's needed per entry point

### Different Types of Rendering
**(Pre-Rendering) Server-Side Rendering**: HTML/JS code is generated server-side, then sent to the client, which initially only shows a fast, but non-interactive page. The process of going from static to dynamic (server-side) data is called hydration.

**(Pre-Rendering) Static Site Generation**: content is generated at build time, stored in a CDN and fetched in it's entirety by the client when the page is fetched. No server calls needed.
**Client-Side Rendering**: rendering is entirely done on a user's device within the browser at runtime

# Apollo + GraphQL
[Apollo + GraphQL Interactive Course (Odyssey)](https://odyssey.apollographql.com/?utm_source=apollo_docs&utm_medium=referral&_gl=1*1om4x9e*_ga*MTg5MjEyNzY3NS4xNjQ2NzU1MjM4*_ga_0BGG5V2W2K*MTY0Njc1NTIzOC4xLjEuMTY0Njc1NTQwNy4w)

## Building a GraphQL schema
Similar to most API layers, defining our schema is much like outlining the data contract we need in a way that makes sense for our app needs. Unlike a other API standards though, we aren't really thinking of things by their specific endpoints and instead we think purely in our data objects, relationships and defining **Query types** alongside them. Example: 

```javascript
type Query {
  "Get tracks array for homepage grid"
  tracksForHome: [Track!]!
}

"A track is a group of Modules that teaches about a specific topic"
type Track {
  id: ID!
  "The track's title"
  title: String!
  "The track's main author"
  author: Author!
  "The track's main illustration to display in track card or track page detail"
  thumbnail: String
  "The track's approximate length to complete, in minutes"
  length: Int
  "The number of modules this track contains"
  modulesCount: Int
}

"Author of a complete Track"
type Author {
  id: ID!
  "Author's first and last name"
  name: String!
  "Author's profile picture url"
  photo: String
}
```

## Apollo Client/Server
pretty straightforward, apollo acts as our graphQL server - sort of sitting in between our actual data source (DB) and our app. So we start a new server instantiated with our schema type defs

 ```javascript
const { ApolloServer } = require('apollo-server');
const typeDefs = require('./schema');

const server = new ApolloServer({ typeDefs });
```

**NOTE**: you can also include a `mocks` field in the apollo server to add some fake data right out the gate

Instantiating an Apollo client is pretty straightforward too, but it comes with some nice configurability out of the box

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import GlobalStyles from './styles';
import Pages from './pages';
import { ApolloProvider, ApolloClient, InMemoryCache } from '@apollo/client';

const client = new ApolloClient({
  uri: 'http://localhost:4000',
  cache: new InMemoryCache(),
});

ReactDOM.render(
  <ApolloProvider client={client}>
    <GlobalStyles />
    <Pages />
  </ApolloProvider>,
  document.getElementById('root')
);```

`ApolloProvider` makes all the fancy client functionality available throughout the entire component tree

 `ApolloClient` is the configured client that talks to the running server
    
`InMemoryCache` is exactly what it sounds like -- it's an in-memory normalized caching layer. which is pretty neat

## Lifecycle of A GraphQL Query
![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fsecond-jeff%2Fy_p6Ovksf9.png?alt=media&token=e8909ba7-2c2e-4797-a2ad-f1b4d8bd9f8c)

# Prisma
[NextJS + Prisma Primer](https://www.prisma.io/nextjs)

