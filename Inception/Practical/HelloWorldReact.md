## My first react code with CDN's:-

```html
<--index.html-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Namasthe React</title>
</head>
<body>
    <div id="root" ></div>

    <script crossorigin 
    src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script crossorigin 
    src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>    

<script>
const heading=React.createElement("h1",{},"Hello World From Yadhus REACT");
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(heading);
</script>

</body>
</html>
```

# Using js seperate

App.js:-

```javascript

const heading=React.createElement("h1",{},"Yadhus REACT");
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(heading);

```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Namasthe React</title>
</head>
<body>
    <div id="root" ></div>

    <script crossorigin 
    src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script crossorigin 
    src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>    

<script src="./App.js" ></script>

</body>
</html>
```
