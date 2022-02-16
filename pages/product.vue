<template>
  <div class="container">
    <navigasi/>
    <div class="row">
      <div class="col-md-10">
        <h3>Products</h3>

        <div class="row">
          <div class="col-md-3" v-for="item in items" :key="item.id">
            <div class="card mb-2">
              <div class="card-header">
                <img :src="item.foto" alt="" width="90%">
              </div>
              <div class="card-body">
                <h4>{{ item.nama }}</h4>
                <h4>Rp{{ item.harga }}</h4>
                <a :href="item.link_eksternal" class="btn btn-success btn-block">Beli di whatsapp</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: '',
    }
  },
  mounted() {
    this.ambilData()
  },
  methods: {
    async ambilData() {
      const { data, error } = await this.$supabase
        .from('tb_produk')
        .select()

      if(data) this.items = data
      if(error) console.log(error)
    }
  }
}
</script>