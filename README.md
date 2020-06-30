# Bike shop and repair station map
Map of Madison bike shops and repair stations for the [Madison Bikes website](https//www.madisonbikes.org/bike-shop-map), using [Leaflet](https://rstudio.github.io/leaflet/) and RMarkdown.

## Data
Bike shop info was manually compiled and entered into a Google Sheet; repair station data is imported from the [City of Madison Open Data portal](https://data-cityofmadison.opendata.arcgis.com/datasets/bike-repair-station).

## Deployment
The Madison Bikes website runs on Wordpress, which means there are some manual steps required to set up the map.[^1]

[^1]: If anyone can think of a more automated solution, let me know.

### Initial set-up
1. Set the `YAML` header to output a `html_document` and knit
1. Copy the `lib` folder into your Wordpress site root directory via `ssh` (i.e. the libraries will be `madisonbikes.org/lib`)
1. Create a new root-level page on Wordpress
1. Add an `html` block in the Wordpress editor
1. Copy all library references from the `map.html` `<head>` section into the block (starting from `<script src="lib/jquery-1.12.4/jquery.min.js"></script>` and ending at `<link href="lib/fontawesome-4.7.0/font-awesome.min.css" rel="stylesheet">`)
1. Manually adjust the paths to point to the right `lib` directory (i.e. insert `../` in front of every relative path to go up to the root directory and then into `lib`)
1. Copy all content between the `<body> ... </body>` tags into the block after the `<script>`s.

### Updates
1. Change `YAML` header to `html_fragment` and knit
1. Copy `map.html` content and paste it into the `<body>` section on Wordpress