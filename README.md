# Semiconductor-manufacturers-in-the-world
Interactive visualization of semiconductor manufacturing plants in the world

Objective: To scrape the list of semiconductor manufacturing plants in the world and other relevant information from wikipedia webpage and visualize them interactively.

Note: Attached code needs a bing maps API key to get latitude and longitude from bing maps. I have removed the personal API key to access bing maps.

Process:

1.	Webscraping:
1(a). List of semicondcutor manufacturing plants and the other relevant information are webscraped from wikipedia webpage: https://en.wikipedia.org/wiki/List_of_semiconductor_fabrication_plants. This page has links to most of the company's wikipedia webpage (eg. for intel: https://en.wikipedia.org/wiki/Intel) which was also scraped.
1(b). Borders of the world countries were webscraped from https://rawgit.com/johan/world.geo.json/master/countries.geo.json, where the data is present in python dictionary format. The webpage contains the shape of every country in the world along with it's latitude and longitude.
Library used: requests, BeautifulSoup, pandas

2.	Data Munging:
2(a). Semiconductor manufacturing plants: Webscraped data (table in wikipedia page) was converted to pandas dataframe for efficent data wrangling. Empty cells in dataframe was filled with empty string ''.
2(b). Borders of world countries: Webscraped JSON data were parsed to obtain a list of countries and their latitude and longitude. Coding from https://teamtreehouse.com/library/plotting-the-world was used.
Library used: pandas, numpy

3.	Geographical co-ordinates of semiconductor plant location:
The georgraphical co-ordinates (latitude and longitude) of all the semiconductor manufactruing plant were obtained from the library geopy via the plant's country (and city) name. API key was created from my personal account and used.
Library used: GeoPy (geolocation service: Bing maps). Note: Geopy Nominatim gives incorrect co-ordinates for some location and it is not used. (Malta, NY, USA is shown to be in Stockholm, Sweden). Opened an issue in openstreetmaps nominatim github page: https://github.com/openstreetmap/Nominatim/issues/1068

4.	Visualizing semiconductor manufactring plants in world map:
World countries and their co-orindates were plotted in bokeh via bokeh patches and semiconductor plants were plotted on the world map via bokeh circle glyph. Hovertool was added for interactive visualization to display the company and plant name when hovered over the location.
Library used: Bokeh
