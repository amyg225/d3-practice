# Intro

- just js
    - easily included in a project
- chainable methods
    - similar to jQuery
    - order matters - methods expect to receive specific information
        - `text()` expects a reference to a DOM element
- data binding
- style with css or as an svg
- can be responsive with consistent/custom scale

!

#Why use D3?

- Encourages interest in design thinking
- Engages users
- Growing community/Well supported
- FREE!

!

##Example with CSS
```
var dataset = [ 5, 10, 13, 19, 21, 25, 22, 18, 15, 13,
                11, 12, 15, 20, 18, 17, 16, 18, 23, 25 ];

d3.select("body").selectAll("div")
    .data(dataset)
    .enter()
    .append("div")
    .attr("class", "bar")
    .style("height", function(d) {
        var barHeight = d * 5;
        return barHeight + "px";
    });
```
- note syntax similar to jQuery

!

##Example with SVG

```
var svg = d3.select("body")
            .append("svg")
            .attr("width", w)
            .attr("height", h);

svg.selectAll("rect")
   .data(dataset)
   .enter()
   .append("rect")
   .attr("x", 0)
   .attr("y", 0)
   .attr("width", 20)
   .attr("height", 100);
```
!
##The HTML

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>D3 Test</title>
        <script type="text/javascript" src="d3/d3.v3.js"></script>
    </head>
    <body>
        <script type="text/javascript">
            // Your beautiful D3 code will go here
        </script>
    </body>
</html>
```
!
## data binding
### How do you `SelectAll()` when you don't have any 'p's??? WTF?
#### the magic of `.enter()`

- SelectAll is always part of a chain
- Each point of data gets mapped to an element, which does not exist yet
- Elements for each data point will be created with the methods that follow

!
## Breaking it down
source- Scott Murray, "http://alignedleft.com/tutorials/d3/binding-data"
```
d3.select("body") — Finds the body, hands a reference off to chain

.selectAll("p") — empty array that will contain any "p"s that will be created

.data(dataset) — Counts and parses our data values
 - Methods after this will be applied to each data

*****
.enter() — uses selected elements on the page, creates 'placeholders' if there are not enough
*****

.append("p") — creates a "p" element from the placeholders on the DOM. Hooray!

.text("New paragraph!") — inserts a text value to all 'p's in the selectAll array
```

!

## customizable scale
- allows for adjusting views based on screen size
- can handle changing data ranges
- more accurate than pixels or other units of measurement
* domain - possible input values
* range - possible output values

!

## style with css or as an svg

http://alignedleft.com/tutorials/d3/drawing-svgs

```
<circle cx="25" cy="25" r="20" fill="rgba(128, 0, 128, 1.0)"/>
<circle cx="50" cy="25" r="20" fill="rgba(0, 0, 255, 0.75)"/>
<circle cx="75" cy="25" r="20" fill="rgba(0, 255, 0, 0.5)"/>
<circle cx="100" cy="25" r="20" fill="rgba(255, 255, 0, 0.25)"/>
<circle cx="125" cy="25" r="20" fill="rgba(255, 0, 0, 0.1)"/>
```
!
## practice map

- [tutorial](http://bost.ocks.org/mike/map/)
- [example](http://localhost:8888/map.html)

!

##TODO:
###election info with d3
- find current shapefiles or topojson/geojson
- combine census shapefile data with population data
- publish?!

###resources
- [geojson from NYC open data](https://github.com/dwillis/nyc-maps)
- [creating svgs with geo-data](https://github.com/mbostock/d3/wiki/Geo-Paths)
- [nyc.gov shapefiles](http://www.nyc.gov/html/dcp/html/bytes/districts_download_metadata.shtml)
