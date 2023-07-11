# Description

DivDraw is a JS library that uses pure HTML elements like `<div>` for drawing on a canvas.
I was inspired by [Chart.js](https://github.com/chartjs/Chart.js) and [P5.js](https://github.com/processing/p5.js/).
So I decided to write my own "chart" library.

# Usage

### Start by adding the Script in the `<head>` Element:

```html
<script src="DivDraw/divdraw.js"></script>
```

### Create a `<div>` Element with the `id="myChart"`:
This is going to be your canvas.

```html
<div id="myChart"></div>
```

### Add a script right above the closing <body> Element/Tag:

```html
<script>
  let width = 800;
  let height = 800;
  
  var elem = document.getElementById("myChart");
  var canvas = new DivDraw(elem, width, height);
</script>
```

### You can now add different Objects to your canvas:

```html
<script>
  canvas.rect(300, 400, 10, 20, '#000');
  
  canvas.ellipse(500, 550, 10, 20, 'limegreen');
  canvas.ellipse(100, 200, 10);
  
  canvas.line(300, 400, 500, 550, 'blue', 3);
  canvas.line(200, 200, 400, 400);
  
  canvas.triangle(700, 600, 30, 50, 1, 'red');
  var returned_triangle = canvas.triangle(700, 600, 30, 50, -1, '#525252', true);
  
  canvas.text(200, 200, 'Hello there');
  canvas.text(600, 300, 'General Kenobi', 'fit-content', 20, 'orange', true);
  
  canvas.clear();
</script>
```

### Cou can add a circle/rect which displays some information when hovered:
You just need to give them the same id.

```html
<script>
  canvas.ellipse(100, 100, 10, 10, 'rgba(0,0,0,.5)', 'id-1');
  canvas.rect(200, 100, 10, 10, 'red', 'rect-id');

  canvas.label(100, 100, 'Visits', 'Visitors: 100', 'id-1', 'rgba(0,0,0,.5)');
  canvas.label(200, 100, 'Visits', 'Visitors: 200', 'rect-id', 'red');
</script>
```

### But you can also create Charts (Bar & Line):

```html
<script>
  let description = '{"type": "line","label": "Coffees per day","color": "rgb(0, 173, 255)","stroke": 8,"lineColor": "rgb(0, 173, 255)","lineStroke": 2,"fill": "rgba(0, 173, 255, .1)","labels": ["22.05", "23.05", "24.05", "25.05", "26.05", "27.05", "28.05", "29.05"], "data": [8, 4, 5.5, 7, 9, 2, 2, 5],"dataLabels": ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"]}';
  let description2 = '{"type": "bar","label": "Litres of water per day","color": "blue","labels": ["22.05", "23.05", "24.05", "25.05", "26.05", "27.05", "28.05", "29.05"], "data": [2.5, 3, 2.4, 2.1, 1.9, 2.5, 2.8, 3.4],"dataLabels": ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"]}';               

  canvas.graph(description, description2);
</script>
```
