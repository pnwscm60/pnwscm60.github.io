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
      We can expect to have a r below 1, when the peak of new infections is reached. And using this formula, we can calculate the cases in the end. In Switzerland, the peak was reached on March 26th with 13000 cases. Let's assume a r-value of 0.7, which seams reasonable from the data given by <a href="#ref2" id="rref2">Swiss National Covid-19 Science Task Force</a>, as (given a fixed r-value), the sum converges to 
        $$
        cases = \frac{g}{1-r} = \frac{13000}{0.3} = 43000 cases
        $$
        </div>
    <div class="ntext">
      Why is this important? From the data collected worldwide about Covid-19, we expect, that the number of deaths is proportional to the number of infected people. This number, the case fatality rate (CFR) differs as it depends heavily on the test capacity. In Switzerland and Germany, testing a lot, the CFR is about 5%. As the number of deaths is proportional to the cases, we can take the peak death toll as starting point g. Given r-value = 0.7 for Switzerland, the final number of deaths will be about
      $$
      deaths = \frac{g}{1-r} = \frac{700}{0.3} = 2333 deaths
      $$
    </div>
  <div class="ntext">
    Switzerland has started to loosen the restrictions and will have a soft regime by May 11th (limited access to restaurants, no mass events like concerts/football matches). Let's assume, that r will go up to 0.9 by this "opening" process. Until May 11th, we will have about 1830 deaths in total by Covid-19.
    $$
    deaths = \frac{g}{1-r} = \frac{1830}{0.1} = 7000 deaths
    $$
The death toll will be 3 times higher, if we are not able to hold r-value at about 0.7. So: We should aim to reduce the r-value as low as possible. If we look at the situation in US, this same principle let us expect, that the death toll will be much higher: We see a r-value lingering between 0.9 and 1 and have (hopefully) reached a peak at about 70000 deaths. 
    $$
    deaths = \frac{g}{1-r} = \frac{70000}{0.1} = 700000 deaths
    $$
So, let's do all we can, to lower the r-value: physical distancing and hygiene measures are key!
    </div>
    </div>
      <div id="foot" style="font-size:0.9em;margin-top:1em;font-style:italic;">
        <div style="border-top:1px solid #000000;width:100px;clear:both;height:4px;line-height:4px;">&nbsp;</div>
        <div id="ref1"><a href="#rref1">^</a> As R is the name of a statistics software widely used today, we use the term of r-value instead of R.</div>
        <div id="ref2"><a href="#rref2">^</a> <a href="https://ncs-tf.ch/de/lagebericht" target="_blank">Situation report by the Swiss National Covid-19 Science Task Force</a></div>
    
    </div>
