# d3treetutorial


**Understanding Diagonals**

1. Create a canvas <br><br>
	```
		var canvas = d3.select("body").append("svg")<br>
			.attr("width", 500)<br>
			.attr("height", 500);
	```
2. Variable declaration of diagonal <br><br>
	```
		var diagonal = d3.svg.diagonal()
	```
3. Append the diagonal to the canvas and give it a few basic attributes <br><br>
	```
		canvas.append("path")<br>
			.attr("fill", "none")<br>
			.attr("stroke", "black")<br>
			.attr("d", diagonal); 
	```
4. Add source coordinates and target coordinates for the diagonal. Use D3's source and target accessor functions (typically provided in coordinated data object - d3.layout.tree will create that!) <br><br>
	```
		var diagonal = d3.svg.diagonal()<br>
			.source({x: 10, y: 10}) <br>
			.target({x: 300, y: 300})
	```

**Creating a tree layout**