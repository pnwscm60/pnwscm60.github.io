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
    
    <!-- Container for the visualization -->
    <div>Visualisierung der Durchimpfung der schweizer Bevölkerung mit Covid-Vakzin. Datenquelle: Bundesamt für Gesundheit, publ. 25.4.2021</div> 
<div id="vis" style="padding:1em;margin-top:1em;border-radius:5px;background-color:#fff;box-shadow:1px 1px 3px #666;"></div>

<script>
   // Assign the specification to a local variable vlSpec.
   var vlSpec = {
  
  "data": {
    "url": "https://pnwscm60.github.io/data/impfstatus.json"
  },
  "width": 500, "height": 50,
  "resolve": {"scale": {"color": "independent"}},
  "layer": [
     {"mark": "bar",
      "encoding": {
        "x": {"aggregate": "sum", "field": "Prozent", "type": "quantitative", "stack": "zero"},
        "y": {"field": "Impfstatus", "type": "nominal"},
        "color": {"field": "Status", "type": "nominal"}}
     },
     {"mark": {"type": "text", "dx": -15, "dy": 3},
      "encoding": {
        "x": {"aggregate": "sum", "field": "Prozent", "type": "quantitative", "stack": "zero"},
        "y": {"field": "Impfstatus", "type": "nominal"},
        "color": {"field": "Status", "type": "nominal", "scale": {"range": ["white"]}, "legend": null},
        "text": { "field": "Prozent", "type": "quantitative", "format": ".1f"}}
    }
  ]
}
// Embed the visualization in the container with id `vis`
vegaEmbed('#vis', vlSpec);
 // color old #85C5A6
</script>
