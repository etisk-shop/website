---
layout: post 	
title: Anders Holch Povlsen
date: 2021-04-30 17:01:07 +0200
categories: fy-liste personer
parent: Personer
---

<script src="https://d3js.org/d3.v6.min.js"></script>

<script>
var width = 460;
var height = 460;

document.addEventListener('DOMContentLoaded', function(e) {
var svg = d3.select("#hierarchy")
  .append("svg")
    .attr("width", width)
    .attr("height", height)
  .append("g")
    .attr("transform", "translate(40,0)");  

var data = JSON.parse('{"children":[{"name":"boss1","children":[{"name":"mister_a","colname":"level3"},{"name":"mister_b","colname":"level3"},{"name":"mister_c","colname":"level3"},{"name":"mister_d","colname":"level3"}],"colname":"level2"},{"name":"boss2","children":[{"name":"mister_e","colname":"level3"},{"name":"mister_f","colname":"level3"},{"name":"mister_g","colname":"level3"},{"name":"mister_h","colname":"level3"}],"colname":"level2"}],"name":"CEO"}');

  console.log(data);

  var cluster = d3.cluster()
    .size([height, width - 100]);

  var root = d3.hierarchy(data, function(d) {
      return d.children;
  });
  cluster(root);

  svg.selectAll('path')
    .data( root.descendants().slice(1) )
    .enter()
    .append('path')
    .attr("d", function(d) {
        return "M" + d.y + "," + d.x
                + "C" + (d.parent.y + 50) + "," + d.x
                + " " + (d.parent.y + 150) + "," + d.parent.x 
                + " " + d.parent.y + "," + d.parent.x;
              })
    .style("fill", 'none')
    .attr("stroke", '#ccc');

  svg.selectAll("g")
      .data(root.descendants())
      .enter()
      .append("g")
      .attr("transform", function(d) {
          return "translate(" + d.y + "," + d.x + ")";
      })
      .append("circle")
        .attr("r", 7)
        .style("fill", "#69b3a2")
        .attr("stroke", "black")
        .style("stroke-width", 2);
});

</script>

# Anders Holch Povlsen
## Om

## Overblik 
Hierarkisk overblik over, hvad AHP enten er ejer eller medejer af.


Hierarkiet er stadig under udvikling, vil gerne dreje det 90 grader og tilføje labels, stay tuned!
<div id="hierarchy"></div>

---

Kilder:

1. <a id="ahp-wiki"></a>[Wikipedia - Anders Holch Povlsen](https://en.wikipedia.org/wiki/Anders_Holch_Povlsen)
