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
    <h2>Todesfälle in der Schweiz 2015-2020</h2>
    <!-- Container for the visualization -->
    <div>Visualisierung der Todesfälle und der Übersterblichkeit in der Schweiz 2015–2020. Datenquelle: Bundesamt für Statistik, abgerufen 15.11.2020</div> 
<div id="vis" style="padding:1em;margin-top:1em;border-radius:5px;background-color:#fff;box-shadow:1px 1px 3px #666;"></div>

<script>
   // Assign the specification to a local variable vlSpec.
   var vlSpec = {
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "description": "Visualization of deaths in Switzerland, combined data from bfs",
  "width": 700, "height": 360,
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
          "dx": -120,
          "dy":10,
          "text": "Grippe"
        }
      },
      {
        "mark": {
          "color": "red",
          "type": "text",
          "align": "left",
          "dx": 10,
          "dy":30,
          "text": "Grippe"
        }
      },
      {
        "mark": {
          "color": "red",
          "type": "text",
          "align": "left",
          "dx": 250,
          "dy":-15,
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
          "dx": -194,
          "dy":2,
          "text": "Altersgruppe 65 Jahre und älter"
        }
      },
      {
        "mark": {
          "color": "#666",
          "type": "text",
          "align": "left",
          "dx": -194,
          "dy":120,
          "text": "Altersgruppe 0–64 Jahre"
        }
      }
      ]
    }]
}
// Embed the visualization in the container with id `vis`
vegaEmbed('#vis', vlSpec);
 // color old #85C5A6
</script>
