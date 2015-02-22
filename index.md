---
title       : A Shiny Application of Population Density Map
subtitle    : An appliation that displays population density data on a googleVis map
author      : Jijie Wang
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---.class #slide1

## Introduction

<B>Purpose of the application:</B> This application is to display population density (people per sq. km of land area) by country from 2010 to 2013.
<br>
<br>
<B>Source of the data:</B> The data source is from World Bank Website (http://data.worldbank.org/indicator/EN.POP.DNST).
<br>
<br>
<B>How to use:</B> 
When you select a year from the textbox from the left pane of the web page, a map will appear in the right pane to display the world population density data of the year selected. If you mouse over the map, it will display year and population density information.

---.class #slide2 

## User Interface

On the left pane of the web page, the user can select a year. The following codes in ui.R will display a select box for the user.


```r
library(shiny)
  
    selectInput("yearInput", 
                label = "Please select a year.",
                choices = c("2010", "2011",
                            "2012", "2013"),
                selected = "2010"
                )
```

<!--html_preserve--><div class="form-group shiny-input-container">
<label class="control-label" for="yearInput">Please select a year.</label>
<div>
<select id="yearInput"><option value="2010" selected>2010</option>
<option value="2011">2011</option>
<option value="2012">2012</option>
<option value="2013">2013</option></select>
<script type="application/json" data-for="yearInput" data-nonempty="">{}</script>
</div>
</div><!--/html_preserve-->

---.class #slide3

## Server Side Coding

On the server side, R codes will take the user input, retrieve data from a data file, and then display a map according to the inputs. The codes are as follows.

```r
  myYear <- reactive({
    input$yearInput
  })
  output$yearTextOutput <- renderText({
    myYearColumn<-paste("year", myYear())
    paste("Your have selected year", myYear())
  })
  output$gvisOutput <- renderGvis({    
     myYearColumn<-paste("year", myYear(),sep="")
     gvisGeoChart(country_data, locationvar="country", colorvar=myYearColumn, 
                  hovervar="country",options=list(width=600, height=400, dataMode='regions'))
  })
```

---.class #slide4
## Output
Assuming the user selects year 2010, the following map will be displayed.<br>

<!-- GeoChart generated in R 3.1.2 by googleVis 0.5.8 package -->
<!-- Thu Feb 19 21:21:54 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataGeoChartID3b783563bf9 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Afghanistan",
"Afghanistan",
100 
],
[
 "Albania",
"Albania",
11 
],
[
 "Algeria",
"Algeria",
38 
],
[
 "American Samoa",
"American Samoa",
68 
],
[
 "Andorra",
"Andorra",
40 
],
[
 "Angola",
"Angola",
38 
],
[
 "Antigua and Barbuda",
"Antigua and Barbuda",
53 
],
[
 "Argentina",
"Argentina",
35 
],
[
 "Armenia",
"Armenia",
11 
],
[
 "Aruba",
"Aruba",
113 
],
[
 "Australia",
"Australia",
73 
],
[
 "Austria",
"Austria",
10 
],
[
 "Azerbaijan",
"Azerbaijan",
15 
],
[
 "Bahamas, The",
"Bahamas, The",
88 
],
[
 "Bahrain",
"Bahrain",
8 
],
[
 "Bangladesh",
"Bangladesh",
5 
],
[
 "Barbados",
"Barbados",
121 
],
[
 "Belarus",
"Belarus",
103 
],
[
 "Belgium",
"Belgium",
90 
],
[
 "Belize",
"Belize",
30 
],
[
 "Benin",
"Benin",
138 
],
[
 "Bermuda",
"Bermuda",
7 
],
[
 "Bhutan",
"Bhutan",
49 
],
[
 "Bolivia",
"Bolivia",
142 
],
[
 "Bosnia and Herzegovina",
"Bosnia and Herzegovina",
131 
],
[
 "Botswana",
"Botswana",
73 
],
[
 "Brazil",
"Brazil",
61 
],
[
 "Brunei Darussalam",
"Brunei Darussalam",
132 
],
[
 "Bulgaria",
"Bulgaria",
124 
],
[
 "Burkina Faso",
"Burkina Faso",
114 
],
[
 "Burundi",
"Burundi",
89 
],
[
 "Cabo Verde",
"Cabo Verde",
21 
],
[
 "Cambodia",
"Cambodia",
136 
],
[
 "Cameroon",
"Cameroon",
100 
],
[
 "Canada",
"Canada",
92 
],
[
 "Cayman Islands",
"Cayman Islands",
62 
],
[
 "Central African Republic",
"Central African Republic",
126 
],
[
 "Chad",
"Chad",
142 
],
[
 "Chile",
"Chile",
61 
],
[
 "China",
"China",
31 
],
[
 "Colombia",
"Colombia",
95 
],
[
 "Comoros",
"Comoros",
91 
],
[
 "Congo, Dem. Rep.",
"Congo, Dem. Rep.",
67 
],
[
 "Congo, Rep.",
"Congo, Rep.",
20 
],
[
 "Costa Rica",
"Costa Rica",
143 
],
[
 "Cote d'Ivoire",
"Cote d'Ivoire",
117 
],
[
 "Croatia",
"Croatia",
134 
],
[
 "Cuba",
"Cuba",
12 
],
[
 "Curacao",
"Curacao",
83 
],
[
 "Cyprus",
"Cyprus",
19 
],
[
 "Czech Republic",
"Czech Republic",
29 
],
[
 "Denmark",
"Denmark",
26 
],
[
 "Djibouti",
"Djibouti",
88 
],
[
 "Dominica",
"Dominica",
146 
],
[
 "Dominican Republic",
"Dominican Republic",
58 
],
[
 "Ecuador",
"Ecuador",
117 
],
[
 "Egypt, Arab Rep.",
"Egypt, Arab Rep.",
133 
],
[
 "El Salvador",
"El Salvador",
75 
],
[
 "Equatorial Guinea",
"Equatorial Guinea",
65 
],
[
 "Eritrea",
"Eritrea",
114 
],
[
 "Estonia",
"Estonia",
78 
],
[
 "Ethiopia",
"Ethiopia",
140 
],
[
 "Faeroe Islands",
"Faeroe Islands",
88 
],
[
 "Fiji",
"Fiji",
103 
],
[
 "Finland",
"Finland",
45 
],
[
 "France",
"France",
19 
],
[
 "French Polynesia",
"French Polynesia",
130 
],
[
 "Gabon",
"Gabon",
115 
],
[
 "Gambia, The",
"Gambia, The",
40 
],
[
 "Georgia",
"Georgia",
133 
],
[
 "Germany",
"Germany",
63 
],
[
 "Ghana",
"Ghana",
13 
],
[
 "Greece",
"Greece",
140 
],
[
 "Greenland",
"Greenland",
2 
],
[
 "Grenada",
"Grenada",
77 
],
[
 "Guam",
"Guam",
72 
],
[
 "Guatemala",
"Guatemala",
28 
],
[
 "Guinea",
"Guinea",
100 
],
[
 "Guinea-Bissau",
"Guinea-Bissau",
112 
],
[
 "Guyana",
"Guyana",
92 
],
[
 "Haiti",
"Haiti",
87 
],
[
 "Honduras",
"Honduras",
124 
],
[
 "Hong Kong SAR, China",
"Hong Kong SAR, China",
116 
],
[
 "Hungary",
"Hungary",
15 
],
[
 "Iceland",
"Iceland",
73 
],
[
 "India",
"India",
93 
],
[
 "Indonesia",
"Indonesia",
27 
],
[
 "Iran, Islamic Rep.",
"Iran, Islamic Rep.",
102 
],
[
 "Iraq",
"Iraq",
128 
],
[
 "Ireland",
"Ireland",
122 
],
[
 "Isle of Man",
"Isle of Man",
33 
],
[
 "Israel",
"Israel",
86 
],
[
 "Italy",
"Italy",
56 
],
[
 "Jamaica",
"Jamaica",
64 
],
[
 "Japan",
"Japan",
85 
],
[
 "Jordan",
"Jordan",
124 
],
[
 "Kazakhstan",
"Kazakhstan",
115 
],
[
 "Kenya",
"Kenya",
129 
],
[
 "Kiribati",
"Kiribati",
21 
],
[
 "Korea, Dem. Rep.",
"Korea, Dem. Rep.",
57 
],
[
 "Korea, Rep.",
"Korea, Rep.",
107 
],
[
 "Kosovo",
"Kosovo",
39 
],
[
 "Kuwait",
"Kuwait",
41 
],
[
 "Kyrgyz Republic",
"Kyrgyz Republic",
69 
],
[
 "Lao PDR",
"Lao PDR",
69 
],
[
 "Latvia",
"Latvia",
84 
],
[
 "Lebanon",
"Lebanon",
97 
],
[
 "Lesotho",
"Lesotho",
122 
],
[
 "Liberia",
"Liberia",
94 
],
[
 "Libya",
"Libya",
73 
],
[
 "Liechtenstein",
"Liechtenstein",
60 
],
[
 "Lithuania",
"Lithuania",
105 
],
[
 "Luxembourg",
"Luxembourg",
52 
],
[
 "Macao SAR, China",
"Macao SAR, China",
50 
],
[
 "Macedonia, FYR",
"Macedonia, FYR",
137 
],
[
 "Madagascar",
"Madagascar",
88 
],
[
 "Malawi",
"Malawi",
37 
],
[
 "Malaysia",
"Malaysia",
139 
],
[
 "Maldives",
"Maldives",
3 
],
[
 "Mali",
"Mali",
14 
],
[
 "Malta",
"Malta",
6 
],
[
 "Marshall Islands",
"Marshall Islands",
71 
],
[
 "Mauritania",
"Mauritania",
92 
],
[
 "Mauritius",
"Mauritius",
119 
],
[
 "Mexico",
"Mexico",
118 
],
[
 "Micronesia, Fed. Sts.",
"Micronesia, Fed. Sts.",
34 
],
[
 "Moldova",
"Moldova",
22 
],
[
 "Monaco",
"Monaco",
46 
],
[
 "Mongolia",
"Mongolia",
54 
],
[
 "Montenegro",
"Montenegro",
102 
],
[
 "Morocco",
"Morocco",
128 
],
[
 "Mozambique",
"Mozambique",
74 
],
[
 "Myanmar",
"Myanmar",
134 
],
[
 "Namibia",
"Namibia",
73 
],
[
 "Nepal",
"Nepal",
48 
],
[
 "Netherlands",
"Netherlands",
106 
],
[
 "New Caledonia",
"New Caledonia",
30 
],
[
 "New Zealand",
"New Zealand",
42 
],
[
 "Nicaragua",
"Nicaragua",
104 
],
[
 "Niger",
"Niger",
24 
],
[
 "Nigeria",
"Nigeria",
44 
],
[
 "Northern Mariana Islands",
"Northern Mariana Islands",
18 
],
[
 "Norway",
"Norway",
38 
],
[
 "Oman",
"Oman",
142 
],
[
 "Pakistan",
"Pakistan",
59 
],
[
 "Palau",
"Palau",
101 
],
[
 "Panama",
"Panama",
105 
],
[
 "Papua New Guinea",
"Papua New Guinea",
35 
],
[
 "Paraguay",
"Paraguay",
38 
],
[
 "Peru",
"Peru",
61 
],
[
 "Philippines",
"Philippines",
79 
],
[
 "Poland",
"Poland",
23 
],
[
 "Portugal",
"Portugal",
17 
],
[
 "Puerto Rico",
"Puerto Rico",
96 
],
[
 "Qatar",
"Qatar",
36 
],
[
 "Romania",
"Romania",
141 
],
[
 "Russian Federation",
"Russian Federation",
142 
],
[
 "Rwanda",
"Rwanda",
99 
],
[
 "Samoa",
"Samoa",
122 
],
[
 "San Marino",
"San Marino",
109 
],
[
 "Sao Tome and Principe",
"Sao Tome and Principe",
47 
],
[
 "Saudi Arabia",
"Saudi Arabia",
24 
],
[
 "Senegal",
"Senegal",
123 
],
[
 "Serbia",
"Serbia",
137 
],
[
 "Seychelles",
"Seychelles",
51 
],
[
 "Sierra Leone",
"Sierra Leone",
135 
],
[
 "Singapore",
"Singapore",
127 
],
[
 "Sint Maarten (Dutch part)",
"Sint Maarten (Dutch part)",
4 
],
[
 "Slovak Republic",
"Slovak Republic",
16 
],
[
 "Slovenia",
"Slovenia",
10 
],
[
 "Solomon Islands",
"Solomon Islands",
49 
],
[
 "Somalia",
"Somalia",
35 
],
[
 "South Africa",
"South Africa",
95 
],
[
 "South Sudan",
"South Sudan",
1 
],
[
 "Spain",
"Spain",
144 
],
[
 "Sri Lanka",
"Sri Lanka",
81 
],
[
 "St. Kitts and Nevis",
"St. Kitts and Nevis",
55 
],
[
 "St. Lucia",
"St. Lucia",
71 
],
[
 "St. Martin (French part)",
"St. Martin (French part)",
111 
],
[
 "St. Vincent and the Grenadines",
"St. Vincent and the Grenadines",
70 
],
[
 "Sudan",
"Sudan",
49 
],
[
 "Suriname",
"Suriname",
73 
],
[
 "Swaziland",
"Swaziland",
125 
],
[
 "Sweden",
"Sweden",
61 
],
[
 "Switzerland",
"Switzerland",
52 
],
[
 "Syrian Arab Republic",
"Syrian Arab Republic",
18 
],
[
 "Tajikistan",
"Tajikistan",
110 
],
[
 "Tanzania",
"Tanzania",
108 
],
[
 "Thailand",
"Thailand",
25 
],
[
 "Timor-Leste",
"Timor-Leste",
129 
],
[
 "Togo",
"Togo",
17 
],
[
 "Tonga",
"Tonga",
32 
],
[
 "Trinidad and Tobago",
"Trinidad and Tobago",
66 
],
[
 "Tunisia",
"Tunisia",
124 
],
[
 "Turkey",
"Turkey",
145 
],
[
 "Turkmenistan",
"Turkmenistan",
14 
],
[
 "Turks and Caicos Islands",
"Turks and Caicos Islands",
82 
],
[
 "Tuvalu",
"Tuvalu",
80 
],
[
 "Uganda",
"Uganda",
43 
],
[
 "Ukraine",
"Ukraine",
134 
],
[
 "United Arab Emirates",
"United Arab Emirates",
9 
],
[
 "United Kingdom",
"United Kingdom",
66 
],
[
 "United States",
"United States",
84 
],
[
 "Uruguay",
"Uruguay",
49 
],
[
 "Uzbekistan",
"Uzbekistan",
123 
],
[
 "Vanuatu",
"Vanuatu",
49 
],
[
 "Venezuela, RB",
"Venezuela, RB",
82 
],
[
 "Vietnam",
"Vietnam",
70 
],
[
 "Virgin Islands (U.S.)",
"Virgin Islands (U.S.)",
76 
],
[
 "West Bank and Gaza",
"West Bank and Gaza",
120 
],
[
 "Yemen, Rep.",
"Yemen, Rep.",
98 
],
[
 "Zambia",
"Zambia",
45 
],
[
 "Zimbabwe",
"Zimbabwe",
84 
] 
];
data.addColumn('string','country');
data.addColumn('string','country.1');
data.addColumn('number','year2010');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartGeoChartID3b783563bf9() {
var data = gvisDataGeoChartID3b783563bf9();
var options = {};
options["width"] =    650;
options["height"] =    450;
options["dataMode"] = "regions";

    var chart = new google.visualization.GeoChart(
    document.getElementById('GeoChartID3b783563bf9')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "geochart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartGeoChartID3b783563bf9);
})();
function displayChartGeoChartID3b783563bf9() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartGeoChartID3b783563bf9"></script>
 
<!-- divChart -->
  
<div id="GeoChartID3b783563bf9" 
  style="width: 650; height: 450;">
</div>
