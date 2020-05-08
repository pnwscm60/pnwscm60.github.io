<html>
  <head>
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3.0.1/es5/tex-mml-chtml.js"></script>
    <title>Why to hold the r-value low</title>
    <meta charset="utf-8" />
    <meta http-equiv="expires" content="0">
  <style>
 /* FONTS */
 @import url("https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,700");
</style>
  </head>
  <body>
    <h2>Wieso es sich lohnt, R<span style="font-size:0.8em;font-style:italic;">e</span> so tief wie möglich zu halten</h2>
    <div class="twocol">
    <div class="ntext">
      Zu Beginn dieses Jahres war der Begriff «Reproduktionszahl» oder R<span style="sub">0</span> bzw. R<span style="sub">e</span> den wenigsten bekannt. Heute ist er in aller Munde, erscheint täglich in allen Massenmedien und in sozialen Netzwerken weiss jede und jeder darüber zu berichten. Den meisten Leuten (falls sie nicht der Fraktion der Verschwörungstheoretiker angehören) ist klar, dass R<span style="font-size:0.8em;font-style:italic;">e</span> unter 1 liegen muss, damit die Epidemie zurückgeht. Ein Wert über 1 würde bedeuten, dass wir ein exponentielles Wachstum der Infektionen haben. Nur wenigen verstehen aber, wieso es wichtig ist, R<span style="font-size:0.8em;font-style:italic;">e</span> nicht nur «unter 1», sondern «so niedrige wie möglich» zu halten. 
    </div>
    <div class="ntext">
   Was sagt uns R<span style="font-size:0.8em;font-style:italic;">e</span> genau? Die Reproduktionszahl zeigt, um wie viel grösser (oder kleiner) die nächste Generation an Infizierten sein wird. Nehmen wir an, Person 0 sei infiziert und infiziere zwei andere Personen. Dies entspricht einem R<span style="font-size:0.8em;font-style:italic;">e</span> von 2. Diese Person ist also die 1. Generation, nenne wir sie g. Sie enthält g = 1 Person. Die zweite Generation umfasst g&#183;r = 2 Personen. Da jede dieser beiden Personen wieder 2 andere infiziert, sind es in der dritten Generation g&#183;r^2 = 4 Personen, usw. Wir werden also pro Tag 1, 2, 4, 8, 16, ... Fälle haben, die Fallzahl steigt exponentiell an, solange R<span style="font-size:0.8em;font-style:italic;">e</span> 2 bleibt. Die Fallzahl wird erst sinken, wenn die Anzahl der infizierten Personen so gross ist, dass es für eine infizierte Person schwieriger wird, noch nicht infizierte Personen «zu finden». Findet sie kaum noch nicht infizierte Personen, hat man die sogenannte Herdenimmunität erreicht.
    </div>
    <div class="ntext">
      Liegt R<span style="font-size:0.8em;margin:2px 1px 0 -1px;font-style:italic;">e</span> When the r-value is above 1, the sum will go up infinitely, until it slows down by the lack of suceptible people. When the r-value is between 0 and 1, the sum converges to a sum 
      $$
      \frac{g}{1-r}
      $$
    </div>
      <div class="ntext">
      We can expect to have a r below 1, when the peak of new infections is reached. And using this formula, we can calculate the cases in the end. In Switzerland, the peak was reached on March 26th with 13000 cases. Let's assume a r-value of 0.7, which seams reasonable from the data given by <a href="#ref2" id="rref2">Swiss National Covid-19 Science Task Force</a>, as (given a fixed r-value), the sum converges to 
        $$
        cases = \frac{g}{1-r} = \frac{13000}{0.3} = 43000
        $$
        </div>
    <div class="ntext">
      Why is this important? From the data collected worldwide about Covid-19, we expect, that the number of deaths is proportional to the number of infected people. This number, the case fatality rate (CFR) differs as it depends heavily on the test capacity. In Switzerland and Germany, testing a lot, the CFR is about 5%. As the number of deaths is proportional to the cases, we can take the peak death toll as starting point g. Given r-value = 0.7 for Switzerland, the final number of deaths will be about
      $$
      deaths = \frac{g}{1-r} = \frac{700}{0.3} = 2333
      $$
    </div>
  <div class="ntext">
    Switzerland has started to loosen the restrictions and will have a soft regime by May 11th (limited access to restaurants, no mass events like concerts/football matches). If we assume a higher r-value of 0.9, this would give us 
    $$
    deaths = \frac{g}{1-r} = \frac{700}{0.1} = 7000
    $$
The death toll will be 3 times higher, if we are not able to hold r-value at about 0.7. So: We should aim to reduce the r-value as low as possible. If we look at the <a href="#ref3" id="rref3">situation in US</a>, this same principle let us expect, that the death toll will be much higher: We see a r-value lingering between 0.9 and 1 and have (hopefully) reached a peak at about 70000 deaths. 
    $$
    deaths = \frac{g}{1-r} = \frac{70000}{0.1} = 700000
    $$
So, let's do all we can, to lower the r-value: physical distancing and hygiene measures are key!
    </div>
    </div>
      <div id="foot" style="font-size:0.9em;margin-top:1em;font-style:italic;">
        <div style="border-top:1px solid #000000;width:100px;clear:both;height:4px;line-height:4px;">&nbsp;</div>
        <div id="ref1"><a href="#rref1">^</a> As R is the name of a statistics software widely used today, we use the term of r-value instead of R.</div>
        <div id="ref2"><a href="#rref2">^</a> <a href="https://ncs-tf.ch/de/lagebericht" target="_blank">Situation report by the Swiss National Covid-19 Science Task Force</a></div>
    <div id="ref2"><a href="#rref2">^</a> <a href="https://www.worldometers.info/coronavirus/" target="_blank">Worldometer</a></div>
    </div>
