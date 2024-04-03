# Converting a HTML into React
HTML:-
```html
<div id = "parent">
  <div id = "Child">
        <h1>im h1 tag</h1>
  </div>
</div>
```

React:-

```javascript
const parent = React.createElement("div",{id:"parent"},
React.createElement("div",{id:"child"},
React.createElement("h1",{},"im h1 tag")
));


const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(parent);
```
if we `console.log(parent)` its an object!!!

## If there are are lots of childs Like:-

HTML:-
```html
<div id = "parent">
  <div id = "Child">
        <h1>im h1 tag</h1>
        <h2>im h2 tag</h2>
  </div>
</div>
```
REACT:-
```javascript
const parent = React.createElement("div",{id:"parent"},
React.createElement("div",{id:"child"},
[React.createElement("h1",{},"im h1 tag"),
React.createElement("h2",{},"im h2 tag)
]
));


const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(parent);

```

Childs are creating like as inside arrays


*Also:-*

if

HTML:-
```html
<div id = "parent">
  <div id = "Child">
        <h1>im h1 tag</h1>
        <h2>im h2 tag</h2>
  </div>

  <div id = "Child2">
        <h1>im h1 tag</h1>
        <h2>im h2 tag</h2>
  </div>
</div>
```

React:-

```javascript

const parent = React.createElement("div",{id:"parent"},
[React.createElement("div",{id:"child"},
[React.createElement("h1",{},"Hi iam yadhu H1 tag"),
React.createElement("h2",{},"Hi iam yadhu H2 tag")
]
),

React.createElement("div",{id:"child2"},
[React.createElement("h1",{},"Hi iam yadhu H1 tag from child2"),
React.createElement("h2",{},"Hi iam yadhu H2 tag Child2")
]
)]
);


const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(parent);
```

### But its very complicated than HTML!!!!

Thats why we use `JSX` for react but this is (above^) the core of react
