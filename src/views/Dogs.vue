<template>
  <div>
      <PetTable
        species='Dogs'
        :pets="dogs"
      />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable'
export default {
  components: {
    PetTable
  },
  name: 'Dogs',
  data () {
    return {}
  },
  computed:
    mapState([
      'dogs'
    ])

}
</script>
