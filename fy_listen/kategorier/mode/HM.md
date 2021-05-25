---
layout: post
title: "HM"
date: 2021-05-02 19:46:00 +0200
categories: fy-liste supermarked
parent: Mode
grand_parent: Fy-listen
---

# H&M

<script src="https://d3js.org/d3.v6.min.js"></script>

<script>
var width = 440;
var height = 460;

document.addEventListener('DOMContentLoaded', function(e) {
var svg = d3.select("#hm_hierarchy")
  .append("svg")
    .attr("width", width)
    .attr("height", height)
  .append("g")
    .attr("transform", "translate(40,0)");  

var data = JSON.parse('{"children":[{"name":"H&M","children":[],"colname":"level2"},{"name":"ARKET","children":[],"colname":"level2"},{"name":"COS","children":[],"colname":"level2"},{"name":"Weekday","children":[],"colname":"level2"},{"name":"& Other Stories","children":[],"colname":"level2"},{"name":"H&M Home","children":[],"colname":"level2"},{"name":"Afound","children":[],"colname":"level2"},{"name":"Monki","children":[],"colname":"level2"}],"name":"H&M Group"}');

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
		});
});

</script>

<div id="hm_hierarchy"></div>


---

Kilder:

1. <a id="hm-brands"></a>[H&M](https://hmgroup.com/brands/)
