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
    <h2>Wieso es sich lohnt, R<sub>e</sub> so tief wie möglich zu halten</h2>
    <div class="twocol">
    <div class="ntext">
      Zu Beginn dieses Jahres war der Begriff «Reproduktionszahl» oder R<sub>0</sub> bzw. R<sub>e</sub> den wenigsten bekannt. Heute ist er in aller Munde, erscheint täglich in allen Massenmedien und in sozialen Netzwerken weiss jede und jeder darüber zu berichten. Den meisten Leuten (falls sie nicht der Fraktion der Verschwörungstheoretiker angehören) ist klar, dass R<sub>e</sub> unter 1 liegen muss, damit die Epidemie zurückgeht. Ein Wert über 1 würde bedeuten, dass wir ein exponentielles Wachstum der Infektionen haben. Nur wenigen verstehen aber, wieso es wichtig ist, R<sub>e</sub> nicht nur «unter 1», sondern «so niedrig wie möglich» zu halten. 
    </div>
    <div class="ntext">
   Was sagt R<sub>e</sub> genau aus? Die Reproduktionszahl zeigt, um wie viel grösser (oder kleiner) die nächste Generation an Infizierten während einer Epidemie sein wird. Nehmen wir an, Person 0 sei infiziert und infiziere zwei andere Personen. Dies entspricht einem R<sub>e</sub> von 2. Diese Person ist also die 1. Generation, nennen wir sie g. Sie enthält g = 1 Person. Die zweite Generation umfasst g&#183;R<sub>0</sub> = 2 Personen. Da jede dieser beiden Personen wieder 2 andere infiziert, sind es in der dritten Generation g&#183;R<sub>e</sub>^2 = 4 Personen, usw. Wir werden also pro Tag 1, 2, 4, 8, 16, ... neue Infektionsfälle haben. Mathematisch interessierten fällt sofort auf, dass es sich dabei um eine geometrische Reihe handelt. Solange R<sub>e</sub> 2 bleibt, steigt die Zahl der Infizierten exponentiell an. Die Fallzahl wird erst sinken, wenn die Anzahl der infizierten Personen so gross ist, dass es für eine infizierte Person schwieriger wird, noch nicht infizierte Personen «zu finden».
    </div>
    <div class="ntext">
      Liegt R<sub>e</sub> also über 1, steigt die Fallzahl täglich an, bis die Zunahme durch die grosse Zahl der bereits Infizierten gebremst wird. Liegt R<sub>e</sub> aber zwischen 0 und 1, konvergiert die Summe der täglichen Fallzahlen zur Summe 
      $$
      \frac{g}{1-R_e}
      $$
    </div>
      <div class="ntext">
        Bei einem einfachen eingipfeligen Verlauf können wir vermuten, dass R<sub>e</sub> unter 1 liegt, sobald die Spitze der Neuinfektionen überschritten wird. Nehmen wir ab diesem Zeitpunkt ein gleichbleibendes R<sub>e</sub> an, können wir die Gesamtsumme der Fälle abschätzen. In der Schweiz wurde der Gipfel der Neuinfektionen mit 13000 Fällen ungefähr am 26. März überschritten. Nehmen wir ab diesem Zeitpunkt ein R<sub>e</sub> von 0.7 an – dies erscheint aufgrund der Daten der <a href="#ref2" id="rref2">Swiss National Covid-19 Science Task Force</a> als vernünftig – konvergiert die Summe der Infektionsfälle zu 
        $$
        Bestätigte Infektionen = \frac{g}{1-r} = \frac{13000}{0.3} = 43000
        $$
        </div>
    <div class="ntext">
      Die Zahl der Todesfälle ist proportional zur Anzahl der bestätigten Fälle. Dies wird durch die sogenannte Case Fatality Rate (CFR) ausgedrückt (Anzahl Todesfälle pro bestätigten Fall). In der Schweiz liegt dieser Wert im Moment bei ungefähr 5 %, in Deutschland bei ungefähr 4 %. Die CFR hängt natürlich davon ab, wie viele Tests durchgeführt werden. In Schweden beispielsweise, das verhätnismässig wenig testet, lag die CFR am 8. Mai bei 12 %. Anstelle der bestätigten Fälle können wir auch die Todesfallzahl einsetzen und so die zu erwartende Summe der Todesfälle abschätzen. Unter der Annahme eines R<sub>e</sub> von 0.7 hat die Schweiz ingesamt ungefähr
      $$
      Tote = \frac{g}{1-r} = \frac{700}{0.3} = 2333
      $$
      zu erwarten.
    </div>
  <div class="ntext">
  Nehmen wir ab dem Spitzenwert ein R<sub>e</sub> von 0.9 an, wie wir es bei Lockerung der Massnahmen wohl erwarten müssen, ergäbe dies eine Summe von 
    $$
    Tote = \frac{g}{1-r} = \frac{700}{0.1} = 7000
    $$
    Die Zahl der Todesfälle liegt also drei mal höher. Diese Rechnung ist selbstverständlich eine starke Vereinfachung, das R<sub>e</sub> nicht fix ist, sondern – je nachdem, wie gut die Grundregeln von Abstand halten und Hygiene eingehalten werden – mehr oder weniger schwankt. Immerhin sollte klar sein, dass es sich lohnt, die Infektionsrate möglichst gering zu halten. In Schweden liegt R<sub>e</sub> derzeit nur knapp unter 1, in den USA und in Grossbritannien sogar darüber. Nimmt man für Schweden den aktuellen Stand der Todesfälle (8. Mai: 3175) als Ausgangswert und geht aufgrund der lockeren Regeln von einem stabilen R<sub>e</sub> von 0.9 aus, ergibt dies eine Endsumme der Todesfälle von 
    $$
    Tote = \frac{g}{1-r} = \frac{3175}{0.1} = 31750
    $$
In den USA scheint die Epidemie derzeit auf die ländlichen Gebiete überzuspringen, während offenbar in vielen Bundesstaaten Lockerungen der Massnahmen verkündet werden. Gehen wir auch hier von einem R<sub>e</sub> 0.9 (aktuell liegt der Wert über 1), so ergäben sich 
    $$
    Tote = \frac{g}{1-r} = \frac{78500}{0.1} = 785000
    $$
      </div>
      <div class="ntext">Die Pandemie ist noch lange nicht überstanden. Es wird sich lohnen, die Infektionsrate so tief wie möglich zu halten. Aus den Analysen der Auswirkungen verschiedener Massnahmen bedeutet das: <a href="#ref3" id="rref3">Abstand halten, Maske in Innenräumen, Hygiene und Verbot von Grossveranstaltungen.</div>
    </div>
    </div>
      <div id="foot" style="font-size:0.9em;margin-top:1em;font-style:italic;">
        <div style="border-top:1px solid #000000;width:100px;clear:both;height:4px;line-height:4px;">&nbsp;</div>
        <div id="ref1"><a href="#rref1">^</a> As R is the name of a statistics software widely used today, we use the term of r-value instead of R.</div>
        <div id="ref2"><a href="#rref2">^</a> <a href="https://ncs-tf.ch/de/lagebericht" target="_blank">Situation report by the Swiss National Covid-19 Science Task Force</a></div>
    <div id="ref2"><a href="#rref2">^</a> <a href="https://www.worldometers.info/coronavirus/" target="_blank">Worldometer</a></div>
        <div id="ref3"><a href="#rref3">^</a>Ich bevorzuge den Begriff «Abstand halten» oder «physical distancing». Denn es geht m. E. nicht darum, keine Kontakte mehr zu pflegen, sondern um das Einhalten der physikalischen Distanz.</div>
    </div>
