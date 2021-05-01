---
layout: post 	
title: Anders Holch Povlsen
date: 2021-04-30 17:01:07 +0200
categories: fy-liste personer
parent: Personer
---

<script src="https://d3js.org/d3.v6.min.js"></script>

<script>
var width = 440;
var height = 460;

document.addEventListener('DOMContentLoaded', function(e) {
var svg = d3.select("#hierarchy")
  .append("svg")
    .attr("width", width)
    .attr("height", height)
  .append("g")
    .attr("transform", "translate(40,0)");  

var data = JSON.parse('{"children":[{"name":"Bestseller","children":[{"name":"Vero Moda","colname":"level3"},{"name":"Jack & Jones","colname":"level3"},{"name":"Vila","colname":"level3"},{"name":"Junarose","colname":"level3"},{"name":"Only","colname":"level3"},{"name":"Only & Sons","colname":"level3"},{"name":"Kids Only","colname":"level3"},{"name":"Only Play","colname":"level3"},{"name":"Only Carmakoma","colname":"level3"},{"name":"Jaqueline de Young","colname":"level3"},{"name":"Selected Femme/Homme","colname":"level3"},{"name":"Name it","colname":"level3"},{"name":"LMTD","colname":"level3"},{"name":"Noisy May","colname":"level3"},{"name":".Object","colname":"level3"},{"name":"Pieces","colname":"level3"},{"name":"Yas","colname":"level3"},{"name":"mamalicious","colname":"level3"}],"colname":"level2"},{"name":"Normal","children":[],"colname":"level2"},{"name":"Nemlig","children":[],"colname":"level2"},{"name":"ASOS","children":[],"colname":"level2"}],"name":"AHP"}');

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
        return "M" + (d.y-30) + "," + d.x
                + "C" + (d.parent.y + 50) + "," + d.x
                + " " + (d.parent.y + 120) + "," + d.parent.x 
                + " " + d.parent.y + "," + d.parent.x;
              })
    .style("fill", 'none')
    .attr("stroke", '#ccc');

  svg.selectAll("g")
      .data(root.descendants())
      .enter()
      .append("g")
      .attr("transform", function(d) {
          return "translate(" + (d.y-30) + "," + d.x + ")";
      })
      .append("circle")
        .attr("r", 7)
        .style("fill", "#69b3a2")
        .attr("stroke", "black")
        .style("stroke-width", 2);
	
	svg.selectAll("g")
	  .append("text")
		.attr("dx", 12)
		.attr("dy", ".35em")
		.style("font-size", 12)
		.text(function(d) { 
			return d.data.name;
		})
});

</script>

# Anders Holch Povlsen
## Om

## Overblik 
Hierarkisk overblik over, hvad AHP enten er ejer eller medejer af.

<div id="hierarchy"></div>

Alle brands under Bestseller kan også ses på [deres egen hjemmeside](https://about.bestseller.com/our-brands).

Hierarkiet er stadig under udvikling.


---

Kilder:

1. <a id="ahp-wiki"></a>[Wikipedia - Anders Holch Povlsen](https://en.wikipedia.org/wiki/Anders_Holch_Povlsen)
