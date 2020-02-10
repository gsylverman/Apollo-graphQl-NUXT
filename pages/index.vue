<template>
  <div>
    <ul>
      <li v-for="character in characters.results" :key="character.id">
        Name: {{ character.name }} ID:{{ character.id }}
      </li>
    </ul>
    <div>Ch: {{ character.name ? character.name : null }}</div>
    <button @click="charId++">change id</button>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      charId: 2
    }
  },
  watch: {
    charId(newVal) {
      console.log(newVal)
    }
  },
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
    character: {
      query: gql`
        query getCharacter($id: ID) {
          character(id: $id) {
            id
            name
          }
        }
      `,
      variables() {
        return { id: this.charId }
      }
    }
  }
}
</script>
