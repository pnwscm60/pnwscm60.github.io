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
  <body style="background-color:#fff;">
    
    <!-- Container for the visualization -->
    <div>Visualisierung der Durchimpfung der schweizer Bevölkerung mit einem Covid-Vakzin.<br/>Datenquelle: Bundesamt für Gesundheit, Stand 26.4.2021</div> 
<div id="vis" style="padding:1em;margin-top:1em;border-radius:5px;background-color:#fff;box-shadow:1px 1px 3px #666;"></div>

<script>
   // Assign the specification to a local variable vlSpec.
   var vlSpec = {
  
  "data": {
    "url": "https://pnwscm60.github.io/data/impfstatus.json"
  },
  "width": 400, 
  "height": 50,
  "padding": {"left": 5, "top": 20, "right": 5, "bottom": 5},
  "resolve": {"scale": {"color": "independent"}},
  "layer": [
     {"mark": "bar",
      "encoding": {
        "x": {"field": "Prozent", "type": "quantitative", "stack": "zero"},
        "y": {"field": "Impfstatus", "type": "nominal"},
        "color": {"field": "Status", "scale": {"range": ["#009933", "#ff9933", "#ff0000"]}}
     },
     {"mark": {"type": "text", "dx": -15, "dy": 5},
      "encoding": {
        "x": {"field": "Prozent", "type": "quantitative", "stack": "zero"},
        "y": {"field": "Impfstatus", "type": "nominal"},
        "color": {"Status": "site"},
        "text": { "field": "Prozent", "type": "quantitative", "format": ".1f"}}
    },
    {
        "mark": {
          "color": "#666",
          "type": "text",
          "align": "left",
          "dx": -230,
          "dy":-60,
          "fontSize": 14,
          "fontWeight": 700,
          "text": "Visualisierung der Durchimpfung der schweizer Bevölkerung mit Covid-Vakzin"
        }
      },
    {
        "mark": {
          "color": "#666",
          "type": "text",
          "align": "left",
          "dx": -230,
          "dy":80,
          "text": "Visualisierung: MvRiederberg "
        }
      }
  ]
}
// Embed the visualization in the container with id `vis`
vegaEmbed('#vis', vlSpec);
 // color old #85C5A6
</script>
<div style="margin-top:1em;"><a href="https://nocovidnow.ch/impfstatus.html" style="color:red;font-weight:300;">Covid-Impfstatus Schweiz</a></div>
