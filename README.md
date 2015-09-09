# d3treetutorial


**Understanding Diagonals**

1. Create a canvas
	```
		var canvas = d3.select("body").append("svg")
			.attr("width", 500)
			.attr("height", 500);
	```
2. Variable declaration of diagonal
	```
		var diagonal = d3.svg.diagonal()
	```
3. Append the diagonal to the canvas and give it a few basic attributes
	```
		canvas.append("path")
			.attr("fill", "none")
			.attr("stroke", "black")
			.attr("d", diagonal); 
	```
4. Add source coordinates and target coordinates for the diagonal. Use D3's source and target accessor functions (typically provided in coordinated data object - d3.layout.tree will create that!)
	```
		var diagonal = d3.svg.diagonal()
			.source({x: 10, y: 10}) 
			.target({x: 300, y: 300})
	```

**Creating a tree layout**