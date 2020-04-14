<html>
  <head>
    <title>Vega-Lite Bar Chart</title>
    <meta charset="utf-8" />
    <script src="https://d3js.org/d3.v5.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/vega@5.10.1"></script>
    <script src="https://cdn.jsdelivr.net/npm/vega-lite@4.10.4"></script>
    <script src="https://cdn.jsdelivr.net/npm/vega-embed@6.5.2"></script>

    <style media="screen">
      /* Add space between Vega-Embed links  */
      .vega-actions a {
        margin-right: 5px;
      }
    </style>
  </head>
  <body>
    <h2>Test for online graphs</h2>
    <!-- Container for the visualization -->
 <style>
    /* AXES */
/* ticks */
.axis line{
stroke: #706f6f;
stroke-width: 0.5;
shape-rendering: crispEdges;
}

/* axis contour */
.axis path {
stroke: #706f6f;
stroke-width: 0.7;
shape-rendering: crispEdges;
}

/* axis text */
.axis text, .xtext {
fill: #2b2929;
font-family: "Open Sans Condensed";
font-size: 100%;
}
.grid line {
stroke: lightgrey;
stroke-opacity: 0.7;
shape-rendering: crispEdges;
}
.grid path {
stroke-width: 0;
}
/* label text */
.label {
font-family: "Open Sans Condensed";
font-size: 65%;
}
.bund {
font-family: "Open Sans Condensed";
font-size: 10%;
fill:#ffffff;
}
/* LINE CHART */
.line,.li0,.li1,.li2,.li3,.li4,.li5,.li6,.li7,.li8,.li9,.li10,.li11,.li12,.li13,.li14,.li15,.li16,.li17,.li18,.li19,.li20,.li21,.li22,.li23,.li24,.li25, .line {
stroke-width: 1.5; fill:none;
    }
.li0 { stroke:#936037; } .te0 {fill: #936037;}
.li1 { stroke:#be1622; } .te1 {fill: #be1622;}
.li2 { stroke:#e71d73; } .te2 {fill: #e71d73;}
.li3 { stroke:#e94e1b; } .te3 {fill: #e94e1b;}
.li4 { stroke:#f39200; } .te4 {fill: #f39200;}
.li5 { stroke:#95c11f; } .te5 {fill: #95c11f;}
.li6 { stroke:#008d36; } .te6 {fill: #008d36;}
.li7 { stroke:#006633; } .te7 {fill: #006633;}
.li8 { stroke:#00a19a; } .te8 {fill: #00a19a;}
.li9 { stroke:#36a9e1; } .te9 {fill: #36a9e1;}
.li10 { stroke:#1d71b8; } .te10 {fill: #1d71b8;}
.li11 { stroke:#29235c; } .te11 {fill: #29235c;}
.li12 { stroke:#951b81; } .te12 {fill: #951b81;}
.li13 { stroke:#a3195b; } .te13 {fill: #a3195b;}
    
    .sygrid {
    stroke-opacity: 0.7;
    shape-rendering: crispEdges;
    stroke-width:1px;
    stroke-dasharray: 10,3;
    }

div.tooltip, div.tooltip2 {   
  position: absolute;           
  text-align: center;                          
    padding:0 2px 5px 2px;           
  font: 13px "Open Sans Condensed";
    font-weight:300;
    color:#fff;
  background-color: #777; 
  border: 2px #fff solid;      
  border-radius: 2px;           
  pointer-events: none;         
}
    div.tooltip {
        width: 40px;                  
        height: 15px;  
    }
    div.tooltip2 {
        padding: 3px;
        width: 40px;                  
        height: 26px;
        line-height:13px;
    }
    </style>
<div id="container5" class="svg-container" style="position:relative;float:left;margin-bottom:1em;"></div>
<div id="container1" class="svg-container" style="position:relative;float:left;margin-bottom:1em;"></div>


<!-------------- GRAFIK 5 EFFECT OF MITIGATION ------------------>
<script>
//*** PREPARE ***//
// set the dimensions and margins of the graph
var margin = {top: 40, right: 5, bottom: 35, left: 50},
    width = 350 - margin.left - margin.right,
    height = 300 - margin.top - margin.bottom;
var viewbox="0 0 350 280"
//-----------------------------DATA------------------------------//
// parse the date / time
var parseTime = d3.timeParse("%d.%m.%y");
d3.dsv(";","data/covid_cumch.csv").then(function(data) {

  // format the data
  data.forEach(function(d) {
      d.date = parseTime(d.date);
      d.F = +d.F;
  });
//-------------------SCALES ----------------//    
// set the ranges
var x = d3.scaleTime().range([0, width]);
var y = d3.scaleLinear().range([height, 0]);
    
// Scale the range of the data
x.domain(d3.extent(data, function(d) { return d.date; }));
y.domain([1, 1.65]); //d3.max(data, function(d) { return d.F; })

//-------------------LINES-----------------//
// define the 1stline

var valueline = d3.line()
    .curve(d3.curveBasis)
    .defined(function(d) { return d.F!=0; })
    .x(function(d) { return x(d.date); })
    .y(function(d) { return y(d.F); });

//-----------------AXES---------------//
formValue = d3.format("");
const yaxis = d3.axisLeft()
    .tickFormat(function(d) { return formValue(d)})
    .scale(y);
   
const xaxis = d3.axisBottom()
    .ticks(5)
    .tickFormat(d3.timeFormat('%d.%m'))
    .scale(x);
// gridlines in x axis function
function make_x_gridlines() {
return d3.axisBottom(x)
.ticks(5)
}
// gridlines in y axis function
function make_y_gridlines() {
return d3.axisLeft(y)
.ticks(5)
}
// append the svg obgect to the body of the page
// appends a 'group' element to 'svg'
// moves the 'group' element to the top left margin
var svg = d3.select("div#container5").append("svg")
    .attr("position", "absolute")
    .attr("viewbox", viewbox)
    .attr("width", width + margin.left + margin.right)
    .attr("height", height + margin.top + margin.bottom)
  .append("g")
    .attr("transform",
          "translate(" + margin.left + "," + margin.top + ")");
//--------------TOOLTIP--------------//
// Add a tooltip div. Here I define the general feature of the tooltip: stuff that do not depend on the data point.
  // Its opacity is set to 0: we don't see it by default.
  var tooltip = d3.select("div#container5")
    .append("div")
    .style("opacity", 0)
    .attr("class", "tooltip")
    
//--------------MOUSEOVER-FUNKTIONEN-------------//
// A function that change this tooltip when the user hover a point.
  // Its opacity is set to 1: we can now see it. Plus it set the text and position of tooltip depending on the datapoint (d)
  var mouseover = function(d) {
    tooltip
      .style("opacity", 1)
  }
  var mousemoveC = function(d) {
    tooltip
      .html(d.F)
      .style("left", (d3.mouse(this)[0]+20) + "px") // It is important to put the +90: other wise the tooltip is exactly where the point is an it creates a weird effect
      .style("top", (d3.mouse(this)[1]+10) + "px")
      .style("background-color", "#e94e1b")
  }
    
  // A function that change this tooltip when the leaves a point: just need to set opacity to 0 again
  var mouseleave = function(d) {
    tooltip
      .transition()
      .duration(200)
      .style("opacity", 0)
  }
// ------------------------- DRAWING-----------------------------//  
//-----------------------------AXES------------------------------//
// gridlines first
  svg.append("g")
.attr("class", "grid")
.attr("transform", "translate(0," + height + ")")
.call(make_x_gridlines()
.tickSize(-height)
.tickFormat("")
)
// add the Y gridlines
svg.append("g")
.attr("class", "grid")
.call(make_y_gridlines()
.tickSize(-width)
.tickFormat("")) 
    
svg.append("g")
    .attr("class", "axis")
    .attr("transform", "translate(0," + height + ")")
    .call(xaxis)
    .selectAll("text")  
     .style("text-anchor", "end")
     .attr("dx", "-1em")
     .attr("dy", "-.5em")
     .attr("transform", "rotate(-90)");

svg.append("g")
    .attr("class", "axis")
    .call(yaxis);
svg.append("text")
        .attr("transform", "rotate(-90)")
        .attr("dy", "+1em")
        .attr("y", 6)
        .style("text-anchor", "end")
        .attr("class", "xtext")
        .text("Wachstumsrate");        
    
//--------------------LINES-----------------//    
  // Add the valueline path.
  svg.append("path")
      .data([data])
      .attr("class", "li3")
      .attr("d", valueline)
var reg1 = 1;
var reg2 = 38;
var reg1y = x(data[reg1].date);
var reg2y = x(data[reg2].date);              
  
svg.append("line")
        .attr("class", "li6")
        .attr("x1",reg1y)
        .attr("y1",88)
        .attr("x2",reg2y)
        .attr("y2",88);

//---------------------POINTS-----------------//
    // Add the scatterplot
    var path = svg.selectAll("dot")
     .data(data)
     .enter().append("circle")
     .attr("r", 3)
     .attr("cx", function (d) {
           return x(d.date);
     })
     .attr("cy", function (d) {
          return y(d.F);
     })
    .attr("class", "li3") 
     .style("stroke-width", 1.3)
     .style("fill", "#fff")
     .on("mouseover", mouseover )
    .on("mousemove", mousemoveC )
    .on("mouseleave", mouseleave );
    
//----------------ZUSAETZLICHES-------------//
//----------------Massnahmen ----------------//
svg.append("circle")
    .attr("r", 9)
    .attr("cx",x(data[3].date))
    .attr("cy",210)
    .attr("class","te10");
svg.append("line")
        .attr("class", "li10 sygrid")
        .attr("x1",x(data[3].date))
        .attr("y1",77)
        .attr("x2",x(data[3].date))
        .attr("y2",218);
svg.append("text")
    .attr("fill", "#fff")
    .attr("x", x(data[3].date))
    .attr("y",215)
    .attr("text-anchor", "middle")
    .style("font-family", "Open Sans Condensed")
    .text("1");
svg.append("circle")
    .attr("r", 9)
    .attr("cx",x(data[10].date))
    .attr("cy",210)
    .attr("class","te10");
svg.append("line")
        .attr("class", "li10 sygrid")
        .attr("x1",x(data[10].date))
        .attr("y1",0)
        .attr("x2",x(data[10].date))
        .attr("y2",218);
svg.append("text")
    .attr("fill", "#fff")
    .attr("x", x(data[10].date))
    .attr("y",215)
    .attr("text-anchor", "middle")
    .style("font-family", "Open Sans Condensed")
    .text("2");
svg.append("circle")
    .attr("r", 9)
    .attr("cx",x(data[17].date))
    .attr("cy",210)
    .attr("class","te10");
svg.append("line")
        .attr("class", "li10 sygrid")
        .attr("x1",x(data[17].date))
        .attr("y1",0)
        .attr("x2",x(data[17].date))
        .attr("y2",218);
svg.append("text")
    .attr("fill", "#fff")
    .attr("x", x(data[17].date))
    .attr("y",215)
    .attr("text-anchor", "middle")
    .style("font-family", "Open Sans Condensed")
    .text("3");
svg.append("circle")
    .attr("r", 9)
    .attr("cx",x(data[20].date))
    .attr("cy",210)
    .attr("class","te10");
svg.append("line")
        .attr("class", "li10 sygrid")
        .attr("x1",x(data[20].date))
        .attr("y1",0)
        .attr("x2",x(data[20].date))
        .attr("y2",218);
svg.append("text")
    .attr("fill", "#fff")
    .attr("x", x(data[20].date))
    .attr("y",215)
    .attr("text-anchor", "middle")
    .style("font-family", "Open Sans Condensed")
    .text("4");
svg.append("circle")
    .attr("r", 9)
    .attr("cx",x(data[24].date))
    .attr("cy",210)
    .attr("class","te10");
svg.append("line")
        .attr("class", "li10 sygrid")
        .attr("x1",x(data[24].date))
        .attr("y1",0)
        .attr("x2",x(data[24].date))
        .attr("y2",218);
svg.append("text")
    .attr("fill", "#fff")
    .attr("x", x(data[24].date))
    .attr("y",215)
    .attr("text-anchor", "middle")
    .style("font-family", "Open Sans Condensed")
    .text("5");
//------------------ TITLE -----------------//
svg.append("text")
.attr("x", (width / 2))
.attr("y", 0 - (margin.top / 2))
.attr("text-anchor", "middle")
.style("font-size", "20px")
.style("font-family", "Open Sans Condensed")
.style("font-weight", "300")
.text("Wachstumsrate bestÃ¤tigte FÃ¤lle");
    });
    </script> 
  </body>
</html>
