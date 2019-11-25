<template>
  <div class="hello">
    <v-layout row>
      <v-flex d-flex xs3>
        <v-card tile>
          <v-card-text>
            <v-list>
              <draggable
                v-model="relsFiltered"
                @start="drag = true"
                @end="drag = false"
                element="div"
              >
                <div
                  v-for="(el, index) in relsFiltered"
                  @click="onSelect(el)"
                  :key="el.id"
                >
                  <v-divider v-if="index === 0" />

                  <v-list-tile
                    :key="el.id"
                    ripple
                  >
                    <v-list-tile-content>
                      <v-list-tile-title>
                        {{ index }}. {{ el.name }}
                      </v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>

                  <v-divider />
                </div>
              </draggable>
            </v-list>
          </v-card-text>

          <v-card-text />
        </v-card>
      </v-flex>

      <v-flex d-flex xs9>
        <v-card tile>
          <div>{{ relsFiltered.length }}</div>
          <pre style="text-align: left;">{{ relsFiltered }}</pre>
        </v-card>
      </v-flex>
    </v-layout>
  </div>
</template>
<script>
import draggable from 'vuedraggable'

export default {
  name: 'HelloWorld',
  components: { draggable },
  data () {
    return {
      rels: [
        { id: 0, name: 'one' },
        { id: 1, name: 'two' },
        { id: 2, name: 'three' },
        { id: 3, name: 'four' }
      ]
    }
  },
  computed: {
    relsFiltered: {
      get () {
        return this.rels
      },
      set (data) {
        this.rels = data
      }
    }
  },
  methods: {
    onSelect () {}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
