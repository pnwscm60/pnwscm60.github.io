<html>
  <head>
    <title>Realtime estimation of Rt</title>
    <meta charset="utf-8" />
    <meta http-equiv="expires" content="0">
  <style>
 /* FONTS */
 @import url("https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,700");
</style>
  </head>
  <body>
    <h2>Realtime estimation of Rt in selected European Countries</h2>
    <div style="margin-bottom:1em;">Kevin Systrom published an interesting <a href="http://systrom.com/blog/the-metric-we-need-to-manage-covid-19/" target="_blank">article</a> about realtime estimation of Rt. To know the actual Rt is of special interest now, as Swiss government has started to gradually ease the restrictions since April 27th. Austria started earlier, several other countries are discussing the same.<br/>Systrom based his publication on a Paper from <a href="https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0002185" target="_blank">Bettencourt & Ribeiro</a>, «Real Time Bayesian Estimation of the Epidemic Potential of Emerging Infectious Diseases». They used Bayesian statistics to estimate the most likely value of Rt and a credible interval for the true value of Rt. We used the method described by Systrom to estimate Rt for European Countries since the beginning of the epidemic, but we used an serial interval of 5.2 (<a href="https://ispmbern.github.io/covid-19/swiss-epidemic-model/" target="_blank">Althaus CL</a>) instead of 4 and used R instead of Python. We show the last 35 data points (about 5 weeks) for each of these countries. Smaller case numbers result as expected in wider density intervals. Data are taken from <a href="https://opendata.ecdc.europa.eu/covid19/casedistribution/csv">ECDC</a>.</div>
    <div><img src="/images/estimrteu_0405.svg" style="max-height:800px;"></div>
    <div style="font-size:1em;style:italic;">Estimated Rt for some European countries inclucing Switzerland as per May 4th. Yellow: Highest density interval (95%). Based on data from ECDC, downloaded on Mai 4th 8 pm.</div>
