# Welcome to my GitHub Page

Information about projects that i am working on.

## StaffLocation
Project that used for research on Integration Platform / API Management tool / JS Frontend.
All components in used in project are Open Source except Microsoft SQL server Express that is used for database.

Project source is not public or intended as open source, so repository is not visible on my GitHub profile. Intrested parties can send request for further information.

### Description and purpose
Front end client that displays statistics about how much time/distance a given workplace employees would earn/lose on single workday, given that the workplace was located elsewhere in the neigbourhood.

The front end client can also compare time from given point on map to (a) current workplace and (b) propose workplace.
The client shows all calculations based on driving, walking and cycling profiles provided by used routing machine.

The thought is that all things are optimized for minimal cost but not necessary for employees. Why not try to optimize location of business to save employees valuable time in transportation. Optimal location can also save a lot of Co2 emission in employee car usage.
If business location does not require a walk in office for customers, this should of course be considered when deciding location.

### Components used
* Vue JS
* Vuetify 
* Openstreetmap
* Leaflet JS
* OSRM routing machine
* WSO2 Data Service Server
* WSO2 API Management Server
* Microsoft SQL Express Database

### Architecural Decision Log
[The archtectual decision log for the project is made public here.](/docs/adr/index.md)

## Usage of Azure Integration Services

[test](/Azure%20Logic%20Apps%20Pilot%20Project/README.md)

## My Blog
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

<hr>

Copyright © 2020 Þorleifur Bjarnason, All Rights Reserved.
