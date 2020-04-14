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
 
<div id="container1" class="svg-container" style="position:relative;float:left;margin-bottom:1em;"></div>

{
  "$schema": "https://vega.github.io/schema/vega/v5.json",
  "description": "A dual axis chart, created by setting y's scale resolution to `\"independent\"`",
  "background": "white",
  "padding": 5,
  "width": 400,
  "height": 300,
  "style": "cell",
  "data": [
    {
      "name": "source_0",
      "url": "https://vega.github.io/vega-lite/examples/data/weather.csv",
      "format": {"type": "csv", "parse": {"date": "date"}, "delimiter": ","},
      "transform": [
        {"type": "filter", "expr": "datum.location == \"Seattle\""},
        {
          "field": "date",
          "type": "timeunit",
          "units": ["month"],
          "as": ["month_date", "month_date_end"]
        },
        {
          "type": "aggregate",
          "groupby": ["month_date"],
          "ops": ["average", "average", "average"],
          "fields": ["temp_max", "temp_min", "precipitation"],
          "as": [
            "average_temp_max",
            "average_temp_min",
            "average_precipitation"
          ]
        }
      ]
    }
  ],
  "marks": [
    {
      "name": "layer_0_marks",
      "type": "area",
      "style": ["area"],
      "sort": {"field": "datum[\"month_date\"]"},
      "from": {"data": "source_0"},
      "encode": {
        "update": {
          "opacity": {"value": 0.3},
          "orient": {"value": "vertical"},
          "fill": {"value": "#85C5A6"},
          "x": {"scale": "x", "field": "month_date"},
          "y": {"scale": "layer_0_y", "field": "average_temp_max"},
          "y2": {"scale": "layer_0_y", "field": "average_temp_min"},
          "defined": {
            "signal": "isValid(datum[\"month_date\"]) && isFinite(+datum[\"month_date\"]) && isValid(datum[\"average_temp_max\"]) && isFinite(+datum[\"average_temp_max\"])"
          }
        }
      }
    },
    {
      "name": "layer_1_marks",
      "type": "line",
      "style": ["line"],
      "sort": {"field": "datum[\"month_date\"]"},
      "from": {"data": "source_0"},
      "encode": {
        "update": {
          "stroke": {"value": "#85A9C5"},
          "interpolate": {"value": "monotone"},
          "x": {"scale": "x", "field": "month_date"},
          "y": {"scale": "layer_1_y", "field": "average_precipitation"},
          "defined": {
            "signal": "isValid(datum[\"month_date\"]) && isFinite(+datum[\"month_date\"]) && isValid(datum[\"average_precipitation\"]) && isFinite(+datum[\"average_precipitation\"])"
          }
        }
      }
    }
  ],
  "scales": [
    {
      "name": "x",
      "type": "time",
      "domain": {"data": "source_0", "field": "month_date"},
      "range": [0, {"signal": "width"}]
    },
    {
      "name": "layer_0_y",
      "type": "linear",
      "domain": [0, 30],
      "range": [{"signal": "height"}, 0],
      "nice": true,
      "zero": true
    },
    {
      "name": "layer_1_y",
      "type": "linear",
      "domain": {"data": "source_0", "field": "average_precipitation"},
      "range": [{"signal": "height"}, 0],
      "nice": true,
      "zero": true
    }
  ],
  "axes": [
    {
      "scale": "x",
      "orient": "bottom",
      "gridScale": "layer_0_y",
      "grid": true,
      "domain": false,
      "labels": false,
      "maxExtent": 0,
      "minExtent": 0,
      "ticks": false,
      "zindex": 0
    },
    {
      "scale": "x",
      "orient": "bottom",
      "grid": false,
      "labelFlush": true,
      "labelOverlap": true,
      "encode": {
        "labels": {
          "update": {"text": {"signal": "timeFormat(datum.value, '%b')"}}
        }
      },
      "zindex": 0
    },
    {
      "scale": "layer_0_y",
      "orient": "left",
      "grid": false,
      "title": "Avg. Temperature (°C)",
      "titleColor": "#85C5A6",
      "labelOverlap": true,
      "tickCount": {"signal": "ceil(height/40)"},
      "zindex": 0
    },
    {
      "scale": "layer_1_y",
      "orient": "right",
      "grid": false,
      "title": "Precipitation (inches)",
      "titleColor": "#85A9C5",
      "labelOverlap": true,
      "tickCount": {"signal": "ceil(height/40)"},
      "zindex": 0
    }
  ]
}

    </script> 
  </body>
</html>

{
  "$schema": "https://vega.github.io/schema/vega/v5.json",
  "description": "A dual axis chart, created by setting y's scale resolution to `\"independent\"`",
  "background": "white",
  "padding": 5,
  "width": 400,
  "height": 300,
  "style": "cell",
  "data": [
    {
      "name": "source_0",
      "url": "https://vega.github.io/vega-lite/examples/data/weather.csv",
      "format": {"type": "csv", "parse": {"date": "date"}, "delimiter": ","},
      "transform": [
        {"type": "filter", "expr": "datum.location == \"Seattle\""},
        {
          "field": "date",
          "type": "timeunit",
          "units": ["month"],
          "as": ["month_date", "month_date_end"]
        },
        {
          "type": "aggregate",
          "groupby": ["month_date"],
          "ops": ["average", "average", "average"],
          "fields": ["temp_max", "temp_min", "precipitation"],
          "as": [
            "average_temp_max",
            "average_temp_min",
            "average_precipitation"
          ]
        }
      ]
    }
  ],
  "marks": [
    {
      "name": "layer_0_marks",
      "type": "area",
      "style": ["area"],
      "sort": {"field": "datum[\"month_date\"]"},
      "from": {"data": "source_0"},
      "encode": {
        "update": {
          "opacity": {"value": 0.3},
          "orient": {"value": "vertical"},
          "fill": {"value": "#85C5A6"},
          "x": {"scale": "x", "field": "month_date"},
          "y": {"scale": "layer_0_y", "field": "average_temp_max"},
          "y2": {"scale": "layer_0_y", "field": "average_temp_min"},
          "defined": {
            "signal": "isValid(datum[\"month_date\"]) && isFinite(+datum[\"month_date\"]) && isValid(datum[\"average_temp_max\"]) && isFinite(+datum[\"average_temp_max\"])"
          }
        }
      }
    },
    {
      "name": "layer_1_marks",
      "type": "line",
      "style": ["line"],
      "sort": {"field": "datum[\"month_date\"]"},
      "from": {"data": "source_0"},
      "encode": {
        "update": {
          "stroke": {"value": "#85A9C5"},
          "interpolate": {"value": "monotone"},
          "x": {"scale": "x", "field": "month_date"},
          "y": {"scale": "layer_1_y", "field": "average_precipitation"},
          "defined": {
            "signal": "isValid(datum[\"month_date\"]) && isFinite(+datum[\"month_date\"]) && isValid(datum[\"average_precipitation\"]) && isFinite(+datum[\"average_precipitation\"])"
          }
        }
      }
    }
  ],
  "scales": [
    {
      "name": "x",
      "type": "time",
      "domain": {"data": "source_0", "field": "month_date"},
      "range": [0, {"signal": "width"}]
    },
    {
      "name": "layer_0_y",
      "type": "linear",
      "domain": [0, 30],
      "range": [{"signal": "height"}, 0],
      "nice": true,
      "zero": true
    },
    {
      "name": "layer_1_y",
      "type": "linear",
      "domain": {"data": "source_0", "field": "average_precipitation"},
      "range": [{"signal": "height"}, 0],
      "nice": true,
      "zero": true
    }
  ],
  "axes": [
    {
      "scale": "x",
      "orient": "bottom",
      "gridScale": "layer_0_y",
      "grid": true,
      "domain": false,
      "labels": false,
      "maxExtent": 0,
      "minExtent": 0,
      "ticks": false,
      "zindex": 0
    },
    {
      "scale": "x",
      "orient": "bottom",
      "grid": false,
      "labelFlush": true,
      "labelOverlap": true,
      "encode": {
        "labels": {
          "update": {"text": {"signal": "timeFormat(datum.value, '%b')"}}
        }
      },
      "zindex": 0
    },
    {
      "scale": "layer_0_y",
      "orient": "left",
      "grid": false,
      "title": "Avg. Temperature (°C)",
      "titleColor": "#85C5A6",
      "labelOverlap": true,
      "tickCount": {"signal": "ceil(height/40)"},
      "zindex": 0
    },
    {
      "scale": "layer_1_y",
      "orient": "right",
      "grid": false,
      "title": "Precipitation (inches)",
      "titleColor": "#85A9C5",
      "labelOverlap": true,
      "tickCount": {"signal": "ceil(height/40)"},
      "zindex": 0
    }
  ]
}
