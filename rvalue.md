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
    <h2>Why to hold the r-value low</h2>
    <div class="twocol">
    <div class="ntext">
      There are probably only a few people knowing the meaning of the <a href="#ref1" id="rref1">r-value</a> 6 months ago. Today, the r-value is omnipresent in print and social media. As officials from the health agencies worldwide have repeated every day, many people know today, that the r-value should be below 1. A value above 1 would mean, that we have an exponential growth of infections. But most people do probably not understand, while it is important to hold the r-value as low as possible. We try to give a short explanation. 
    </div>
    <div>
   What does the r-value tell us exactly? Rhe r-value shows, how bigger (or smaller) the next generation will be. Let's assume, Person 0 is infected and infects two other persons, and each infected person infects two others, so r = 2. So, we start with generation zero, let's name it g = 1, the second generation will be g&#183;r = 2, the third g&#183;r^2 = 4, and so on. So we have 1, 2, 4, 8, 16, cases and this sum goes up for each generation. It will start to slow down, when the number of infected people rises, as it will take a longer time to find an non-infected person. That's the basic principle of infection.
    </div>
    <div class="ntext">
      When the r-value is above 1, the sum will go up infinitely, until it slows down by the lack of suceptible people. When the r-value is between 0 and 1, the sum converges to a sum 
      $$
      \frac{g}{1-r}
      $$
    </div>
    <div class="ntext">
      Why is this important? From the data collected worldwide about Covid-19, we expect, that the number of deaths is proportional to the number of infected people. This number, the case fatality rate (CFR) differs as it depends heavily on the test capacity. Let's take as example Switzerland, which has seen an early outbreak. 
    </div>
    </div>
      <div id="foot" style="font-size:0.9em;margin-top:1em;font-style:italic;">
        <div style="border-top:1px solid #000000;width:100px;clear:both;height:4px;line-height:4px;">&nbsp;</div>
        <div id="ref1"><a href="#rref1">^</a> As R is the name of a statistics software widely used today, we use the term of r-value instead of R.</div>
        <div id="ref2"><a href="#rref2">^</a> <a href="https://en.wikipedia.org/wiki/Constructivism_(philosophy_of_education)">https://en.wikipedia.org/wiki/Constructivism_(philosophy_of_education)</a></div>
    
    </div>
