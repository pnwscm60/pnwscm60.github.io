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
    <div>Visualisation de la vaccination en Suisse contre la Covid-19.<br/>Data: Office de la Santé du 30.4.2021</div> 
<div id="vis" style="padding:1em;margin-top:1em;border-radius:5px;background-color:#fff;box-shadow:1px 1px 3px #666;"></div>

<script>
   // Assign the specification to a local variable vlSpec.
   var vlSpec = {
  "data": {
    "url": "https://pnwscm60.github.io/data/impfstatusf.json"
  },
  "width": 400, 
  "height": 50,
  "padding": {"left": 5, "top": 20, "right": 5, "bottom": 5},
  "resolve": {"scale": {"color": "independent"}},
  "layer": [
     {"mark": "bar",
      "encoding": {
        "x": {"field": "Pourcentage", "type": "quantitative", "stack": "zero"},
        "y": {"field": "Vaccination", "type": "nominal"},
        "color": {"field": "Status",
          "type": "nominal",
          "scale": {"range": ["green","orange","red"]}}}
     },
     {"mark": {"type": "text", "dx": -20, "dy": 0, "fontSize":15},
      "encoding": {
        "x": {"field": "Pourcentage", "type": "quantitative", "stack": "zero"},
        "y": {"field": "Vaccination", "type": "nominal"},
        "color": {"field": "Status", "type": "nominal", "scale": {"range": ["white"]}, "legend": null},
        "text": { "field": "Pourcentage", "type": "quantitative", "format": ".1f"}}
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
          "text": "Visualisation de la Vaccination en Suisse contre la Covid-19"
        }
      },
    {
        "mark": {
          "color": "#666",
          "type": "text",
          "align": "left",
          "dx": -230,
          "dy":80,
          "text": "Visualisation: MvRiederberg "
        }
      }
  ]
}
// Embed the visualization in the container with id `vis`
vegaEmbed('#vis', vlSpec);
 // color old #85C5A6
</script>
<div style="margin-top:1em;"><a href="https://nocovidnow.ch/vaccination.html" style="color:red;font-weight:300;">Situation Vaccination en Suisse</a></div>
