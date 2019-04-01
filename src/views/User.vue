<template>
  <div>
    <h1>vue-apollo example: users</h1>
    <div v-for="user in users" :key="user.id">
      <div>{{ user.id }}, {{ user.name }}, {{ user.age }}</div>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag"

const FeedQuery = gql`
{
  users {
    ...namename
  }
}
fragment namename on User {
  name
  id
  age
}
`;
export default {
  name: "User",
  data: () => ({
    users: []
  }),
  apollo: {
    // This `users` match the` users` of GraphQL `type Query {users: [User]}`.
    users: FeedQuery,
  }
};
</script>
