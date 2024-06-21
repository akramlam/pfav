<template>
  <div>
    <!-- Stats cards for key metrics -->
    <div class="row">
      <div class="col-md-6 col-xl-3" v-for="stats in statsCards" :key="stats.title">
        <stats-card>
          <div class="icon-big text-center" :class="`icon-${stats.type}`" slot="header">
            <i :class="stats.icon"></i>
          </div>
          <div class="numbers" slot="content">
            <p>{{ stats.title }}</p>
            {{ stats.value }}
          </div>
          <div class="stats" slot="footer">
            <i :class="stats.footerIcon"></i> {{ stats.footerText }}
          </div>
        </stats-card>
      </div>
    </div>

    <!-- Charts for user behavior and other analytics -->
    <div class="row">
      <div class="col-12">
        <chart-card title="Employee Activity Over Time" sub-title="Performance by hours" :chart-data="usersChart.data" :chart-options="usersChart.options">
          <span slot="footer">
            <i class="ti-reload"></i> Updated 3 minutes ago
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Active
            <i class="fa fa-circle text-warning"></i> Idle
          </div>
        </chart-card>
      </div>

      <div class="col-md-6 col-12">
        <chart-card title="Requests Overview" sub-title="Requests by category" :chart-data="requestsChart.data" chart-type="Bar">
          <span slot="footer">
            <i class="ti-timer"></i> Data refreshed every 5 minutes
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-success"></i> Leave
            <i class="fa fa-circle text-danger"></i> Salary Raise
            <i class="fa fa-circle text-primary"></i> Position Change
          </div>
        </chart-card>
      </div>

      <div class="col-md-6 col-12">
        <chart-card title="Complaints Resolution" sub-title="Monthly Data" :chart-data="complaintsChart.data" :chart-options="complaintsChart.options">
          <span slot="footer">
            <i class="ti-check"></i> Last updated today
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Resolved
            <i class="fa fa-circle text-danger"></i> Open
          </div>
        </chart-card>
      </div>
    </div>
  </div>
</template>

<script>
import { StatsCard, ChartCard } from "@/components/index";
import Chartist from "chartist";

export default {
  components: {
    StatsCard,
    ChartCard
  },
  data() {
    return {
      statsCards: [
        {
          type: "primary",
          icon: "ti-user",
          title: "Total Employees",
          value: "980",
          footerText: "Updated now",
          footerIcon: "ti-reload",
        },
        {
          type: "success",
          icon: "ti-check-box",
          title: "Requests Processed",
          value: "350",
          footerText: "This month",
          footerIcon: "ti-calendar",
        },
        {
          type: "danger",
          icon: "ti-alert",
          title: "Open Complaints",
          value: "15",
          footerText: "Needs attention",
          footerIcon: "ti-timer",
        },
        {
          type: "info",
          icon: "ti-stats-up",
          title: "Positions Filled",
          value: "45",
          footerText: "This year",
          footerIcon: "ti-flag",
        },
      ],
      usersChart: {
        // Configuration for the Employee Activity Chart
      },
      requestsChart: {
        // Configuration for the Requests Overview Chart
      },
      complaintsChart: {
        // Configuration for the Complaints Resolution Chart
      }
    };
  },
  methods: {
    // Define methods to fetch and update data here
  }
};
</script>

<style scoped>
/* Add your styles here */
</style>
