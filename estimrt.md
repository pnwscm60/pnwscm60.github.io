<html>
  <head>
    <title>Estimation Rt</title>
    <meta charset="utf-8" />
    <meta http-equiv="expires" content="0">
  <style>
 /* FONTS */
 @import url("https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,700");
</style>
  </head>
  <body>
    <h2>Estimation of Rt in Swiss Cantons</h2>
    <div style="margin-bottom:1em;">Kevin Systrom published an interesting <a href="http://systrom.com/blog/the-metric-we-need-to-manage-covid-19/" target="_blank">article</a> about the realtime estimation of Rt. To know the actual Rt is of special interest now, as Swiss government has started to gradually ease the restrictions since 27.4.2020.<br/> Systrom based his publication on a Paper from <a href="https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0002185" target="_blank">Bettencourt & Ribeiro</a>, «Real Time Bayesian Estimation of the Epidemic Potential of Emerging Infectious Diseases». They used Bayesian statistics to estimate the most likely value of Rt and a credible interval for the true value of Rt. We used the method described by Systrom to estimate Rt for Swiss cantons with over 750 cases since the beginning of the epidemic, but we used an serial interval of 5.2 (<a href="https://ispmbern.github.io/covid-19/swiss-epidemic-model/" target="_blank">Althaus CL</a>) instead of 4. We show the last 35 data points (about 5 weeks) for each of these cantons Smaller case numbers result as expected in wider density intervals. Data are taken from <a href="https://github.com/openZH/covid_19/">openZH</a>, thanks!</div>
    <div><img src="/images/estimate_200427.svg" style="max-height:800px;"></div>
    <div style="font-size:1em;style:italic;">Estimated Rt for Swiss cantons with over 750 cases as per April 27th. Yellow: Highest density interval (95%). Based on data from OpenZH from the Swiss cantons, downloaded on April 27th.</div>
