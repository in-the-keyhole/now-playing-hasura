# Now Playing - Hasura Demo

Based on the [Hasura TypeScript Boilerplate](https://github.com/hgiasac/hasura-typescript-boilerplate)

## Setup

Copy the `dotenv` file and rename the copy to `.env` - the default values can be left for now.

In `docker-compose.yaml`, uncomment the appropriate image for graphql-engine (`data` service).

Run `make dev` to initiate the `docker compose` script.

## Hasura Console

Install Hasura Console CLI using the instructions here: https://hasura.io/docs/latest/graphql/core/hasura-cli/install-hasura-cli.html

You can run it by navigating to the data folder and running:

```
hasura console --admin-secret hasura --endpoint http://localhost:8123
```

## Data

In the API tab of the Hasura console:

- Create a user account

```
mutation CREATE_USER {
  createUser(data: {email: "blade@runner.com", firstName: "Good", lastName: "Joe", password: "replicant", role: "user"}) {
    id
    user {
      email
      firstName
      lastName
      password
    }
  }
}

```

- Insert some movies:

```
mutation MyMutation {
  insert_movies(objects: [{title: "Blade Runner 2049"},{title: "The Fifth Element"}, {title: "Contact"}]) {
    returning {
      id
      title
    }
  }
}

```

## Querying

With the latest version of Hasura (this one - 2.0) - you can query with GraphQL - the console allows you to do this. Additionally, you can craft REST endpoints for queries. The movies listing already has one made, check out the REST tab within the API tab in the Hasura console.

If you're feeling adventurous, try creating some users with either "user" or "admin" roles - play with some permissions. Have fun!

## Hasura Features

- many features
- much wow
- TODO: blog
