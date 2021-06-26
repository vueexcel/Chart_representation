<template>
  <div>
    <vue-apex-charts
      type="bar"
      height="500"
      :options="apexChartData.chartOptions"
      :series="apexChartData.series"
    ></vue-apex-charts>
  </div>
</template>
<script>
import VueApexCharts from "vue-apexcharts";
export default {
  name: "Chart",
  components: {
    VueApexCharts,
  },
  data() {
    return {
      apexChartData: {
        series: [],
        chartOptions: {
          plotOptions: {
            bar: {
              horizontal: false,
              endingShape: "rounded",
              columnWidth: "80%",
            },
          },
          title: {
            text: "Website",
            margin: 0,
            floating: true,
          },
          dataLabels: {
            enabled: false,
          },
          stroke: {
            show: true,
            width: 2,
            colors: ["transparent"],
          },

          xaxis: {
            type: "category",
            labels: {
              style: {
                cssClass: "grey--text lighten-2--text fill-color",
              },
            },
          },
          yaxis: {
            title: {
              text: "",
            },
            labels: {
              style: {
                cssClass: "grey--text lighten-2--text fill-color",
              },
            },
          },
          fill: {
            opacity: 1,
          },
          grid: {
            borderColor: "rgba(0,0,0,0.1)",
          },
          tooltip: {
            theme: "dark",
          },
        },
      },
      sales: [
        471, 342, 499, 212, 341, 356, 221, 448, 298, 483, 457, 238, 447, 479,
        319, 368, 214, 300, 201, 232, 480, 243, 236, 311, 374, 437, 342, 333,
        470, 418, 455, 362, 399, 324, 386, 451, 467, 375, 500, 246, 412, 246,
        251, 333, 218, 410, 372, 438, 227, 408, 235, 499,
      ],
      revenue: [
        3660, 2256, 3587, 2589, 3477, 4900, 4538, 2824, 2516, 2287, 4496, 4903,
        3322, 2558, 2519, 3836, 4320, 3976, 3324, 3821, 4450, 3339, 2466, 3043,
        3612, 2382, 4220, 3304, 2081, 2946, 4506, 3250, 3768, 4253, 2558, 2587,
        4977, 2001, 2918, 3461, 4029, 2007, 2621, 3215, 2756, 4884, 4252, 3003,
        4567, 2762, 3807, 4181,
      ],
      cancellations: [
        26, 11, 17, 17, 18, 21, 30, 29, 18, 25, 12, 20, 18, 17, 30, 16, 23, 19,
        18, 24, 24, 27, 15, 18, 26, 30, 29, 14, 15, 23, 27, 20, 19, 23, 19, 26,
        29, 21, 21, 22, 12, 28, 26, 23, 19, 15, 19, 16, 25, 15, 11, 21,
      ],
    };
  },
  mounted() {
    let categories = [];
    for (let index = 1; index < 53; index++) {
      const category = `week ${index}`;
      categories.push(category);
    }
    this.apexChartData = {
      chartOptions: {
        xaxis: {
          categories
        },
      },
    };
    this.apexChartData.series = [
      {
        name: `Sales`,
        data: this.sales,
      },
      {
        name: `Revenue`,
        data: this.revenue,
      },
      {
        name: `Cancellations `,
        data: this.cancellations,
      },
    ];
  },
};
</script>