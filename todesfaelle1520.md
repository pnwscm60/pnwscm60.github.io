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
</style>
  </head>
  <body>
    <h2>Test for online graphs</h2>
    <!-- Container for the visualization -->
 
<div id="vis"></div>

<script>
   // Assign the specification to a local variable vlSpec.
   var vlSpec = {
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "description": "A dual axis chart, created by setting y's scale resolution to `\"independent\"`",
  "width": 400, "height": 400,
  "layer": [{
  "data": {
    "url": "https://pnwscm60.github.io/data/wodeathch1019.csv"
  },
  "transform": [{"filter": "datum.KJ > 2014"}],
  "config": {
  "axis": {
    "grid": true,
    "gridColor": "#eaeaea",
    "font": "Open Sans Condensed"
  }
  },
  "encoding": {
    "x": {
        "field": "Endend",
        "axis": {"format": "%d.%m.%y", "tickCount": 12, "title": null},
        "type": "temporal",
        "timeUnit": "daymonthyear"
    }
  },
  "layer": [
    {
      "mark": {"opacity": 0.25, "type": "area", "color": "#85C5A6"},
      "transform": [{"filter": "datum.Alter == \"65\""}],
      "encoding": {
        "y": {
          "aggregate": "average",
          "field": "obeGrenze",
          "scale": {"domain": [0, 1700]},
          "type": "quantitative",
          "axis": {"title": "Anzahl wöchentliche Todesfälle", "tickCount":8, "titleColor": "#111","format": "3r"}
        },
        "y2": {
          "aggregate": "average",
          "field": "untGrenze"
        }
      }
    },
    {
      "mark": {"opacity": 0.25, "type": "area", "color": "#85C5A6"},
      "transform": [{"filter": "datum.Alter == \"0-64\""}],
      "encoding": {
        "y": {
          "aggregate": "average",
          "field": "obeGrenze",
          "scale": {"domain": [0, 1700]},
          "type": "quantitative"
        },
        "y2": {
          "aggregate": "average",
          "field": "untGrenze"
        }
      }
    },
    {
      "mark": {
        "stroke":"#85A9C5",  "type": "line", "strokeWidth": "1.4", "interpolate": "monotone","point": false},
      "transform": [{"filter": "datum.Alter == \"0-64\""}],
      "encoding": {
        "y": {
          "aggregate": "mean",
          "field": "Anzahl_Todesfalle",
          "type": "quantitative"
        }
      }
    },
    {
      "mark": {
        "stroke": "#85A9C5", "type": "line", "strokeWidth": "1.4", "interpolate": "monotone","point": ""},
      "transform": [{"filter": "datum.Alter == \"65\""}],
      "encoding": {
        "y": {
          "aggregate": "mean",
          "field": "Anzahl_Todesfalle",
          "type": "quantitative"
        }
      }
    },
{
      "mark": {
        "stroke": "#85A9C5", "type": "text"},
        "encoding": {
        "y": {
          "aggregate": "mean",
          "field": "Anzahl_Todesfalle",
          "type": "quantitative"
        }
      }
    }]
  }, {
      "data": {
         "values": [{}]
      },
      "encoding": {
        "y": {"datum": 1650}
      },
      "layer": [{
        "mark": { 
          "type": "rule",
        "strokeOpacity": 0}
      }, {
        "mark": {
          "color": "red",
          "type": "text",
          "align": "left",
          "dx": -225,
          "dy":30,
          "text": "Grippe"
        }
      },
      {
        "mark": {
          "color": "red",
          "type": "text",
          "align": "left",
          "dx": -65,
          "dy":30,
          "text": "Grippe"
        }
      },
      {
        "mark": {
          "color": "red",
          "type": "text",
          "align": "left",
          "dx": 130,
          "dy":-10,
          "text": "Covid-19"
        }
      }
      ]
    },
    {
      "data": {
         "values": [{}]
      },
      "encoding": {
        "y": {"datum": 850}
      },
      "layer": [{
        "mark": { 
          "type": "rule",
        "strokeOpacity": 0}
      }, {
        "mark": {
          "color": "#666",
          "type": "text",
          "align": "left",
          "dx": -240,
          "dy":5,
          "text": "Altersgruppe 65 Jahre und älter"
        }
      },
      {
        "mark": {
          "color": "#666",
          "type": "text",
          "align": "left",
          "dx": -240,
          "dy":160,
          "text": "Altersgruppe 0–64 Jahre"
        }
      }
      ]
    }]
}

// Embed the visualization in the container with id `vis`
vegaEmbed('#vis', vlSpec);
</script>
