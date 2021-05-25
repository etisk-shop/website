---
layout: post 	
title: "AHP"
date: 2021-04-30 17:01:07 +0200
categories: fy-liste personer
parent: Personer
grand_parent: Fy-listen
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

var data = JSON.parse('{"children":[{"name":"Bestseller","children":[{"name":"Vero Moda","colname":"level3"},{"name":"Jack & Jones","colname":"level3"},{"name":"Vila","colname":"level3"},{"name":"Junarose","colname":"level3"},{"name":"Only","colname":"level3"},{"name":"Only & Sons","colname":"level3"},{"name":"Kids Only","colname":"level3"},{"name":"Only Play","colname":"level3"},{"name":"Only Carmakoma","colname":"level3"},{"name":"Jaqueline de Young","colname":"level3"},{"name":"Selected Femme/Homme","colname":"level3"},{"name":"Name it","colname":"level3"},{"name":"LMTD","colname":"level3"},{"name":"Noisy May","colname":"level3"},{"name":".Object","colname":"level3"},{"name":"Pieces","colname":"level3"},{"name":"Yas","colname":"level3"},{"name":"mamalicious","colname":"level3"}],"colname":"level2"},{"name":"Bestseller Fashion Group China","children":[],"colname":"level2"},{"name":"Normal","children":[],"colname":"level2"},{"name":"Nemlig","children":[],"colname":"level2"},{"name":"ASOS","children":[{"name":"Top Shop","colname":"level3"},{"name":"Topman","colname":"level3"},{"name":"Miss Selfridge","colname":"level3"}],"colname":"level2"},{"name":"Zalando","children":[{"name":"Anna Field","colname":"level3"},{"name":"Even&Odd","colname":"level3"},{"name":"Friboo","colname":"level3"},{"name":"FullStop","colname":"level3"},{"name":"Kiomi","colname":"level3"},{"name":"Mint&Berry","colname":"level3"},{"name":"Pier One","colname":"level3"},{"name":"Twin tip","colname":"level3"},{"name":"Yourturn","colname":"level3"},{"name":"Zalando Essentials","colname":"level3"},{"name":"Zign","colname":"level3"}],"colname":"level2"},{"name":"Klarna","children":[],"colname":"level2"},{"name":"J. Lindeberg","children":[],"colname":"level2"},{"name":"Bianco Footwear","children":[],"colname":"level2"}],"name":"AHP"}');

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

# Anders Holch Povlsen
## Om

## Overblik 
Hierarkisk overblik over, hvad AHP enten er ejer eller medejer af.

<div id="hierarchy"></div>

### Brand informationer
* Bestseller
  * Alle brands under Bestseller kan også ses på [deres egen hjemmeside](https://about.bestseller.com/our-brands). 
  * Brands relateret til Bestseller kan ses [her](https://about.bestseller.com/about-us/related-companies/related-companies-overview).
  * [Bestseller Fashion Group China](https://about.bestseller.com/about-us/related-companies/fashion-group-china)
* Information om ejerskab i [Normal](https://dagligvarehandlen.dk/bestseller-ejer-koeber-op-i-normal-14/12-2016?fbclid=IwAR3JLujf9K0p-oyl15kn2_RpVYDIGOwSg9oY4OzruXRCXNEfx-8G5NCv5J4)
* Zalando
  * [Pressemeddelelse](https://corporate.zalando.com/en/newsroom/en/press-releases/zalando-introduces-anders-holch-povlsen-new-shareholder)
  * Zalando
    * [aktieoversigt](https://ww.fashionnetwork.com/news/Bestseller-ceo-buys-more-shares-in-zalando,1078304.html)
	* [zLabels (brands under Zalando)](https://zlabels.com/brands.html) 
* ASOS
  * [ASOS-owned brands](https://www.tatler.com/article/anders-povlsen-uks-largest-private-landowner-scotland-rewilding-interview)
* Nemlig
  * [Efter arbejdsforholdsskandalen](https://piopio.dk/mange-milliardaer-staar-bag-nemligcom)
* Klarna
  * [Pressemeddelelse](https://www.klarna.com/international/press/global-klarna-announces-strategic-equity-investment-by-brightfolk-as/)
* [J. Lindeberg](https://en.wikipedia.org/wiki/J.Lindeberg)
* Generelt
  * [Forbes](https://www.forbes.com/profile/anders-holch-povlsen/)

Hierarkiet er stadig under udvikling.
---

Kilder:

1. <a id="ahp-wiki"></a>[Wikipedia - Anders Holch Povlsen](https://en.wikipedia.org/wiki/Anders_Holch_Povlsen)
