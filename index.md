## Welcome to my GitHub Page

Information about projects that i am working on.

## StaffLocation
Project that I use for research on Integration Platform / API Management tool and / JS Frontend.
All components in project are Open Source except Microsoft SQL server Express that is used for database.

Project source is not public or intended as open source, so repository is not visible on my GitHub profile.

### Description
Front end client that displays statistics about how much time / distance a given workplace would earn or lose on single workday if the workplace was located elsewhere.
The client can also compare time from given point on map to (a) current workplace and (b) propose workplace.
The client shows calculations based on driving, walking and cycling profiles provided by used routing machine.

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
[The archtectual decision log for the project is made public here.](/docs/adr/index)

## My Blog
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
