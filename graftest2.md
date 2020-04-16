<html>
  <head>
    <title>Vega-Lite Bar Chart</title>
    <meta charset="utf-8" />
    <script src="https://d3js.org/d3.v5.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/vega@5.10.1"></script>
    <script src="https://cdn.jsdelivr.net/npm/vega-lite@4.10.4"></script>
    <script src="https://cdn.jsdelivr.net/npm/vega-embed@6.5.2"></script>
  <style>
 /* FONTS */
 @import url("https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,700");
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
        height: 25px;  
    }
    div.tooltip2 {
        padding: 3px;
        width: 40px;                  
        height: 26px;
        line-height:13px;
    }
    </style>
  </head>
  <body>
    <h2>Test for online graphs</h2>
    <!-- Container for the visualization -->
 
<div id="vis"></div>
<div id="vis2"></div>
<div id="vis3"></div>
<div id="vis4"></div>
<script>
      // Assign the specification to a local variable vlSpec.
      var vlSpec = {
  "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
  "data": {"url": "https://vega.github.io/vega-lite/examples/data/cars.json"},
  "encoding": {
    "x": {
      "field": "Year",
      "type": "temporal",
      "timeUnit": "year"
    }
  },
  "layer": [
    {
      "mark": {"type": "errorband", "extent": "ci"},
      "encoding": {
        "y": {
          "field": "Miles_per_Gallon",
          "type": "quantitative",
          "title": "Mean of Miles per Gallon (95% CIs)"
        }
      }
    },
    {
      "mark": "line",
      "encoding": {
        "y": {
          "aggregate": "mean",
          "field": "Miles_per_Gallon",
          "type": "quantitative"
        }
      }
    }
  ]
}
// Embed the visualization in the container with id `vis`
vegaEmbed('#vis2', vlSpec);
</script>
<script>
      // Assign the specification to a local variable vlSpec.
      var vlSpec = {
        $schema: 'https://vega.github.io/schema/vega-lite/v4.json',
        data: {
          values: [
            {a: 'C', b: 2},
            {a: 'C', b: 7},
            {a: 'C', b: 4},
            {a: 'D', b: 1},
            {a: 'D', b: 2},
            {a: 'D', b: 6},
            {a: 'E', b: 8},
            {a: 'E', b: 4},
            {a: 'E', b: 7}
          ]
        },
        mark: 'bar',
        encoding: {
          y: {field: 'a', type: 'nominal'},
          x: {
            aggregate: 'average',
            field: 'b',
            type: 'quantitative',
            axis: {
              title: 'Average of b'
            }
          }
        }
      };

      // Embed the visualization in the container with id `vis`
vegaEmbed('#vis', vlSpec);
</script>

<script>
   // Assign the specification to a local variable vlSpec.
   var vlSpec = {
  "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
  "description": "A dual axis chart, created by setting y's scale resolution to `\"independent\"`",
  "width": 300, "height": 300,
  "data": {
    "url": "data/chdeath.csv"
  }, 
  "axis": {
    "font": "Open Sans Condensed"
  },
  "encoding": {
    "x": {
        "field": "date",
        "axis": {"format": "%d.%m", "title": null},
        "type": "temporal",
        "timeUnit": "daymonth"
    }
  },
  "layer": [
    {
      "mark": {"opacity": 0.3, "type": "area", "color": "#85C5A6"},
      "transform": [{"filter": "datum.Alter == \"65\""}],
      "encoding": {
        "y": {
          "aggregate": "average",
          "field": "obeGrenze",
          "scale": {"domain": [0, 1800]},
          "type": "quantitative",
          "axis": {"title": "Anzahl wöchentliche Todesfälle", "titleColor": "#111","format": ".2r"}
        },
        "y2": {
          "aggregate": "average",
          "field": "untGrenze"
        }
      }
    },
    {
      "mark": {"opacity": 0.3, "type": "area", "color": "#85C5A6"},
      "transform": [{"filter": "datum.Alter == \"0-64\""}],
      "encoding": {
        "y": {
          "aggregate": "average",
          "field": "obeGrenze",
          "scale": {"domain": [0, 1800]},
          "type": "quantitative"
        },
        "y2": {
          "aggregate": "average",
          "field": "untGrenze"
        }
      }
    },
    {
      "mark": {"stroke": "#85A9C5", "type": "line", "interpolate": "monotone","point": true},
      "transform": [{"filter": "datum.Alter == \"0-64\""}],
      "encoding": {
        "y": {
          "aggregate": "mean",
          "field": "hochrechnung",
          "type": "quantitative",
          
          "axis": {}
        }
      }
    },
    {
      "mark": {"stroke": "#85A9C5", "type": "line", "interpolate": "monotone","point": true},
      "transform": [{"filter": "datum.Alter == \"65\""}],
      "encoding": {
        "y": {
          "aggregate": "mean",
          "field": "hochrechnung",
          "type": "quantitative",
          
          "axis": {}
        }
      }
    }
  ]
}

// Embed the visualization in the container with id `vis`
vegaEmbed('#vis3', vlSpec);
</script>

<script>
      // Assign the specification to a local variable vlSpec.
      var vlSpec = {
  "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
  "data": {"url": "data/COVID19_Fallzahlen_CH_total_v2.csv"},
  "width": 400,
  "height": 300,
  "encoding": {"x": {"field": "date", "type": "temporal"}},
  "layer": [
    {
      "encoding": {
        "color": {"field": "abbreviation_canton_and_fl", "type": "nominal"},
        "y": {"field": "ncumul_conf", "gt": 0, "type": "quantitative","axis": {"title": "Anzahl bestätigte Fälle"}},
        "x": {
      "field": "date", "type": "temporal",
      "axis": {
        "format":"%d.%m.",
        "tickCount": 10,
        "title": "Datum"
        }}
      },
      "layer": [
        {"mark": "line"},
        {"transform": [{"filter": {"selection": "hover"}}], "mark": "point"}
      ]
    },
    {
      "transform": [{"pivot": "abbreviation_canton_and_fl", "value": "ncumul_conf", "groupby": ["date"]}],
      "mark": "rule",
      "encoding": {
        "opacity": {
          "condition": {"value": 0.3, "selection": "hover"},
          "value": 0
        },
        "tooltip": [
          {"field": "AG", "type": "quantitative"},
          {"field": "AI", "type": "quantitative"},
          {"field": "AR", "type": "quantitative"},
          {"field": "BE", "type": "quantitative"},
          {"field": "BL", "type": "quantitative"},
          {"field": "BS", "type": "quantitative"},
          {"field": "FR", "type": "quantitative"},
          {"field": "GE", "type": "quantitative"},
          {"field": "GL", "type": "quantitative"},
          {"field": "GR", "type": "quantitative"},
          {"field": "JU", "type": "quantitative"},
          {"field": "LU", "type": "quantitative"},
          {"field": "NE", "type": "quantitative"},
          {"field": "NW", "type": "quantitative"},
          {"field": "OW", "type": "quantitative"},
          {"field": "SG", "type": "quantitative"},
          {"field": "SH", "type": "quantitative"},
          {"field": "SO", "type": "quantitative"},
          {"field": "SZ", "type": "quantitative"},
          {"field": "TG", "type": "quantitative"},
          {"field": "TI", "type": "quantitative"},
          {"field": "UR", "type": "quantitative"},
          {"field": "VD", "type": "quantitative"},
          {"field": "VS", "type": "quantitative"},
          {"field": "ZG", "type": "quantitative"},
          {"field": "ZH", "type": "quantitative"}
        ]
      },
      "selection": {
        "hover": {
          "type": "single",
          "fields": ["date"],
          "nearest": true,
          "on": "mouseover",
          "empty": "none",
          "clear": "mouseout"
        }
      }
    }
  ]
}

  // Embed the visualization in the container with id `vis`
vegaEmbed('#vis4', vlSpec);
</script>
