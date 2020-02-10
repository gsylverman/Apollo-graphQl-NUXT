<template>
  <div>
    <ul>
      <li v-for="character in characters.results" :key="character.id">
        Name: {{ character.name }} ID:{{ character.id }}
      </li>
    </ul>
    <div>Ch: {{ character.name }}</div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  apollo: {
    characters: gql`
      query getCharacters {
        characters {
          results {
            id
            name
            status
          }
        }
      }
    `,
    character: gql`
      query getCharacter {
        character(id: "2") {
          id
          name
        }
      }
    `
  }
}
</script>
