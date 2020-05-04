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
    <h2>Realtime estimation of Rt in Switzerland</h2>
    <div style="margin-bottom:0.5em;">We calculate the actual Rt using the data delivered to ECDC by the BAG at the end of each day. We will not update these data on weekends, as data quality on weekends is low. To calculate the actual Rt, we use the methods described by <a href="http://systrom.com/blog/the-metric-we-need-to-manage-covid-19/" target="_blank">Kevin Systrom</a> about realtime estimation of Rt, based on a paper by <a href="https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0002185" target="_blank">Bettencourt & Ribeiro</a>, «Real Time Bayesian Estimation of the Epidemic Potential of Emerging Infectious Diseases». We used a serial interval of 5.2 (<a href="https://ispmbern.github.io/covid-19/swiss-epidemic-model/" target="_blank">Althaus CL</a>) instead of 4 and used R instead of Python. We show the last 35 data points (about 5 weeks). Data are taken from ECDC.</div>
    <div style="margin-bottom:1em;">CAVE: Some cantons deliver data one day later only, some cantons deliver data of the day at noon. Data for the last few days are often corrected 2–3 days later, especially after weekends. This is an estimation of Rt only.</div>
    <div><img src="/images/rtch0405.svg" style="max-width:600px;"></div>
    <div style="font-size:1em;style:italic;">Estimated Rt for Switzerland per 4th of Mai. Yellow: Highest density interval (95%).</div>
