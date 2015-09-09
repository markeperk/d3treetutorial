# d3treetutorial


**Understanding Diagonals**

- Create a canvas 
```
	var canvas = d3.select("body").append("svg")
		.attr("width", 500)
		.attr("height", 500);
```
- Variable declaration of diagonal
```
	var diagonal = d3.svg.diagonal()
```
- Append the diagonal to the canvas and give it a few basic attributes
```
	canvas.append("path")
		.attr("fill", "none")
		.attr("stroke", "black")
		.attr("d", diagonal); 
```
- Add source coordinates and target coordinates for the diagonal. Use D3's source and target accessor functions (typically provided in coordinated data object - d3.layout.tree will create that!)
```
	var diagonal = d3.svg.diagonal()
		.source({x: 10, y: 10})
		.target({x: 300, y: 300})
```

**Creating a tree layout**

- Create (or modify) your canvas. Utilize a group element and translation transform, to push the whole g group over and down by some amount.
```
	var canvas = d3.select("body").append("svg")
		.attr("width", 1200)
		.attr("height", 1000)
		.append("g")
			.attr("transform", "translate(50, 50)");
```
- Contain your tree layout within a new variable (since layouts are both functions and objects, there are a number of things you can do to customize them like assign a size)
```
	var tree = d3.layout.tree()
		.size([1100, 900])
```
- Link a set of data to the layout. 
```
	d3.json("data.json", function(data) {
	})
```
- Remember that tree layouts are "tidy" and have 3 characteristics - labels/text, circles/nodes, and paths/links. Let's start by declaring variables for both your nodes and links and utilize their respective d3 methods with our linked data. 
```
	var nodes = tree.nodes(data); 
```
*The "nodes" variable returns an array of all of the nodes - the structure and data information needed to utilize and place each in the layout*

```
	var links = tree.links(nodes) 
```
*The "links" variable is the path between each node - expects input in the format of nodes (each link will have a source and target property)*

- Create a group element that will hold the data together. We then use it to place them on the screen according to their relative positions. Use transform to "translate" with their respective coordinates
```
	var node = canvas.selectAll(".node")
		.data(nodes)
		.enter() 
		.append("g")
			.attr("class", "node")
			.attr("transform", function(d) { return "translate(" + d.x + "," + d.y + ")"})
```
- Now we're ready to append things to each node's "g" element. Begin by giving a shape to your node.
```
	node.append("circle")
		.attr("r", 5)
		.attr("fill", "gray")
```
- Time to add labels to each node. Utilize your data object to customize each node name.
```
	node.append("text")
		.text(function(d) { return d.name; })
		.attr("font-size", 12)
```
- Don't forget to declare your diagonal variable so that you use the coordinates created in your "links" variable and connect each node.
```
	var diagonal = d3.svg.diagonal()
```
- Use paths to create linkage between each node
```
	canvas.selectAll(".link")
		.data(links)
		.enter()
		.append("path")
		.attr("class", "link")
		.attr("fill", "none")
		.attr("stroke", "gray")
		.attr("d", diagonal);
```
- Make sure that the appropriate code is within your "data" function!

**That's it!**