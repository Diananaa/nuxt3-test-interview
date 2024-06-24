<template>
    <section id="chart" class="my-2 w-fit md:my-6 lg:my-10   flex justify-center">
        <div class="flex flex-col justify-center items-center  sm:px-4 md:px-8 lg:w-[1000px]">
          <highstock :options="chartOptions" class="w-[100vw] sm:w-full" />
        </div>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        rumahSakit: []
      };
    },
    computed: {
      chartOptions() {
        return {
          chart: {
            type: "column",
            
          },
          title: {
            align: 'left',
            text: 'Jumlah Pasien COVID-19 di Rumah Sakit'
          },
          accessibility: {
            announceNewData: {
              enabled: true
            }
          },
          xAxis: {
            type: 'category'
          },
          yAxis: {
            title: {
              text: 'Jumlah Pasien COVID-19'
            }
          },
          legend: {
            enabled: false
          },
          plotOptions: {
            series: {
              borderWidth: 0,
              dataLabels: {
                enabled: true,
                format: '{point.y}'
              }
            }
          },
          tooltip: {
            headerFormat: '<span style="font-size:11px">{series.name}</span><br>',
            pointFormat: '<span style="color:{point.color}">{point.name}</span>: ' +
              '<b>{point.y}</b> pasien<br/>'
          },
          series: [
            {
              name: 'Rumah Sakit',
              colorByPoint: true,
              data: this.rumahSakit.map(rs => ({
                name: rs.nama_rs,
                y: rs.jumlah_pasien_covid
              }))
            }
          ]
        };
      }
    },
    mounted() {
      this.fetchData();
    },
    methods: {
      async fetchData() {
        const response = await fetch("/covid.json");
        const data = await response.json();
        this.rumahSakit = data;
      }
    }
  };
  </script>
  