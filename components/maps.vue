<template >
    <section id="maps" class="z-0 flex justify-center">
    <div class="w-full h-[60vh]">
        <LMap ref="map" :zoom="5" :center="[0.3686169, 119.0321325]">
            <LTileLayer url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
                attribution="&amp;copy; <a href=&quot;https://www.openstreetmap.org/&quot;>OpenStreetMap</a> contributors"
                layer-type="base" name="OpenStreetMap" />
                <LMarker v-for="rs in rumahSakit" :key="rs.id" :lat-lng="[rs.latitude, rs.longitude]">
                  <LPopup>
                    <div>
                      <h3>{{ rs.nama_rs }}</h3>
                      <p>{{ rs.kota }}, {{ rs.provinsi }}</p>
                      <p>Jumlah Pasien COVID: {{ rs.jumlah_pasien_covid }}</p>
                    </div>
                  </LPopup>
              </LMarker>
        </LMap>
    </div>
    </section>
</template>

<script >
export default {
  data() {
    return {
      rumahSakit: []
    };
  },
  mounted() {
    this.fetchData()
  },
  methods:{
    async fetchData() {
      const response = await fetch("/covid.json")
      const data = await response.json();
      this.rumahSakit = data;
  }
  }
};
</script>