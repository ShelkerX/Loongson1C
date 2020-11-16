<template>
  <div class="hello">
    <div id="container"></div>  
  </div>
</template>

<script>
import DataSet from '@antv/data-set';
import { Chart } from '@antv/g2';
import {NetData} from'./data.js'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted(){
    const chart = new Chart({
      container: 'container',
      autoFit: true,
      height: 500,
      padding: [30, 20, 70, 30]
    });

    chart.data(NetData);
    chart.scale({
      TOTAL: {
        min: 0,
        max: 30
      },
      ARP: {
        min: 0,
        max: 30
      },
      IPV4: {
        min: 0,
        max: 30
      },
      ICMP: {
        min: 0,
        max: 30
      },
      IGMP: {
        min: 0,
        max: 30
      },
      UDP: {
        min: 0,
        max: 30
      },
      TCP: {
        min: 0,
        max: 30
      }
    });

    chart.axis('ARP', false);
    chart.axis('IPV4', false);
    chart.axis('ICMP', false);
    chart.axis('IGMP', false);
    chart.axis('UDP', false);
    chart.axis('TCP', false);

    chart.legend({
      custom: true,
      items: [
        { name: 'TOTAL', value: 'TOTAL', marker: { symbol: 'line', style: { stroke: '#ff0000', lineWidth: 2 } } },
        { name: 'ARP', value: 'ARP', marker: { symbol: 'line', style: { stroke: '#ffbf00', lineWidth: 2 } } },
        { name: 'IPV4', value: 'IPV4', marker: { symbol: 'line', style: { stroke: '#ffff00', lineWidth: 2 } } },
        { name: 'ICMP', value: 'ICMP', marker: { symbol: 'line', style: { stroke: '#00ff40', lineWidth: 2 } } },
        { name: 'IGMP', value: 'IGMP', marker: { symbol: 'line', style: { stroke: '#00bfff', lineWidth: 2 } } },
        { name: 'UDP', value: 'UDP', marker: { symbol: 'line', style: { stroke: '#bf00ff', lineWidth: 2 } } },
        { name: 'TCP', value: 'TCP', marker: { symbol: 'line', style: { stroke: '#ff0080', lineWidth: 2 } } },
      ],
    });

    chart.line().position('TIME*TOTAL').color('#ff0000');
    chart.line().position('TIME*ARP').color('#ffbf00');
    chart.line().position('TIME*IPV4').color('#ffff00');
    chart.line().position('TIME*ICMP').color('#00ff40');
    chart.line().position('TIME*IGMP').color('#00bfff');
    chart.line().position('TIME*UDP').color('#bf00ff');
    chart.line().position('TIME*TCP').color('#ff0080');
    chart.removeInteraction('legend-filter'); // 自定义图例，移除默认的分类图例筛选交互
    chart.render();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
