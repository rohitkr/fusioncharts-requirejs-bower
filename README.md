# Example of using FusionCharts with Bower and require.js to load FusionCharts

Bower is a package manager for the Web. In this example we are using bower to download FusionCharts from the command line. And also this example shows one way to load FusionCharts with require.js

### Project structure

bower_components/fusioncharts/
- fusioncharts.js
- fusioncharts.charts.js
- fusioncharts.widgets.js
- fusioncharts.powercharts.js
- fusioncharts.maps.js
- fusioncharts.gantt.js
- fusioncharts.zoomscatter.js
- fusioncharts.treemap.js

bower_components/requirejs/
- require.js

bower_components/jquery/dist
- jquery.js

index.html

The boilerplate index.html looks as below.
```sh
<!DOCTYPE html>
<html>
    <head>
        <title>FusionCharts sample with bower and require</title>
        <script  src="bower_components/requirejs/require.js"></script>

        <script type="text/javascript">
        	
			require.config({
				//By default load any module IDs from bower_components
				baseUrl: 'bower_components',
                paths: {
	                jquery: 'jquery/dist/jquery',
	                fusioncharts: 'fusioncharts/fusioncharts',
	                fusionthemes: 'fusioncharts/themes/fusioncharts.theme.fint'
			    },
			 	shim: {
				    'fusionthemes': {
				    	deps: ['fusioncharts']
				    }
				}
			});

			require(['fusioncharts', 'fusionthemes', 'jquery'], function() {
				// Render FusionCharts here...
			    FusionCharts.ready(function() {
					var chart = new FusionCharts({
						type: "Column2D",
						width: "600",
						height: "350",
						renderAt: "chartContainer",
						dataFormat: "json",
						dataSource: {
						    "chart": {
						        "caption": "Revenue",
						        "animation": "0"
						    },
						    "data": [
						        {
						            "label": "2013",
						            "value": "420000"
						        },
						        {
						            "label": "2014",
						            "value": "910000"
						        },
						        {
						            "label": "2015",
						            "value": "720000"
						        }
						    ]
						}
					})
					.render();
				});
			});

        </script>
    </head>
    <body>
        <div id='chartContainer'> FusionCharts will render here... </div>
    </body>
</html>
```

### Use the below steps to render the FusionCharts
1. Download or clone this repository
2. Install the dependencies listed in bower.json file using the `$ bower install` command (Note: If you get an error that the bower command is not found, check out [Bower's installation instructions].)
3. Open index.html in the browser
 
[Bower's installation instructions]: <http://bower.io/#install-bower>
