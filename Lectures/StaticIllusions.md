# HTML Basics

Browser display (including with jsPsych) relies on HTML, most often HTML5.
Let us see how it works.

> **To go further** The point of this lecture is to raise your understanding of HTML, CSS, JS & JsPsych enough to code your own experiments. For those who may want to go further / better understand the magic at hand, I will leave notes as the present one in the form of quotes. They are not necessary, but may answer questions you may have.

## HTML document structure overview

A HTML file contains:
- A declaration that you are using HTML5;

`<!DOCTYPE html>`

> **What happens if you remove it? - A note on browser compatibility** Most browsers will not care and behave similarly. However, you have no guarantee that it will do so: in fact, Internet Explorer will just treat this as plain text!
> In the case of an online experiment, this means you may lose some participants/data. Even worse, this means that you may have flawed data without realising it!

- A head where most webpage-level elements (e.g. title) are defined,

```
<head></head>
```

> **Tags in HTML** Here, we write "head" between chevrons. This is known as a *tag* in HTML. Tags tell information to your browser, here that this is the head of the document.
> Notice that we have two tags here, one after another. Think of them as brackets: everything that we want to define in the head will be enclosed between the tags. Accordingly, the first tag is called the *opening tag* and the other one the *closing tag*. Closing tags specifically have an additional `/` slash at the start).
> Note that a few tags do not enclose content and only use a single tag, with the slash `/` at the end (e.g. line breaks <br/>).

- A body which will contain the main elements of the page, especially what will be displayed to the user.

```
<body></body>
```

Our first document thus look like this, and is read as a blank page.

```
<!DOCTYPE html>
<head></head>
<body></body>
```

## Setting up a title

You can use the `<title>` tag in the head of the document to set a title.

```
<head>
  <title>My first page!</title>
</head>
```

# Simple shapes

## Square

### Creating divs
Rectangles are very simple shapes to draw in HTML. Although there are a variety of way, we will start by using colored 'divs'.

> **Divs** Divs are precisely HTML element with a rectangle shape. They are most often used as generic containers, but this won't interest us right now.

You may use the following body for your HTML code.

```
<body>
 <div></div>
</body>
```

As you may notice, the page is still blank. Press f12 to understand why.

> **Inspector** f12 opens your browser's inspector, which allows you to see the HTML code of the web page you are currently browsing.

Open the body tags and hover over the `<div>` element. It should show you the element on the webpage, and give you its dimensions. Notice the issue? It is simply of width 0, so of course you won't see it.
TODO IMAGE

### Setting size

Let's specify a width for our `<div>`. To do so, will add specifications to our tag, so that the browser knows how to deal with the element it marks.
Here, we will use the `style` keyword to specify a style that forces a 200px width and a 200px height.

The result is as follows:

```
<body>
 <div style = "width: 200px; height: 200px"></div>
</body>
```

Notice that the style specification has a precise syntax: `keyword: value`, with successive entries being separated by semicolumns `;`. The style won't be applied if you omit semicolumns, or use equal sign instead of columns `:`! Similarly, the value part must have a unit. Here we use pixels (`px`), but there are many others!

> **Setting size with style in HTML** Here we use style to specify the width and height of the element. There are other ways, with specific `width` and `height` tags. However, these specifications may behave unexpectedly at times, which is why we will use `style` in this lecture.

> **Size units in HTML** To set the size of an element, we have many useful units that can adapt to each screen. Here we used pixels (`px`) which are the base unit of computer screens. Since pixel size may vary between computers, we could also use centimeters (`cm`) to get a constant value. Conversely, we could want to adapt our display to the size of the window, and use viewport height (`vh`) and width (`vw`). If we want more specifically to adapt to a given container, we can use percents (`%`).

### Setting background color

If you update the page, you'll see that you in fact still don't see the div. Check again with f12; it should highlight an actual square this time. The reason why you don't see it is that, by default, elements take the background color of their parent, here `<body>`. So you are looking at a white square on a white background, which is a good reason not to see it!

To specify the color (actually background color of the square), you may use another specification in the style:

```
<body>
 <div style = "...; background-color = "red""></div>
</body>
```

> **Names with spaces** Names with spaces are always annoying when programming, since they should actually be taken as a whole by the language. To prevent this, several alternatives exist (such as CamelCase or snake_case), with each language having its usually prefered alternative. In HTML/CSS, we replace spaces ` ` with dashes `-`.

> **Changing background color of the body** Like with any other elements, you can change the style of the body. Try setting it to `gray` with the `background-color` specification!

### Centering

At this point, you should finally have a square ! However, it lies sad and alone in the corner of the screen. We'll see more on the placing of elements, but for now we will stick to simple solutions.

First, we can specify the position of the left corner on the square in the style. This works similar to setting the dimensions of the square.

```
<div style = "...; top: 100px; left: 200px"></div>
```

Although we are moving the square, it is still not centered on the screen. It is pointless to use trial-and-error here, as it won't be centered anymore if you resize your browser window. To get a unit relative to the size of the window, we will use viewport height (`vh`) and width (`vw`). `1vh` correspond to 1% of the _height_ of the window. `1vw` is 1% of the _width_ of the window. Do not confuse both!

As such, we can (somewhat) center the square using the following style:

```
<div style = "...; top: 50vh; left: 50vw"></div>
```

Notice that we are still slightly off, since we actually centered the top left corner of the square. To correct this we will apply a simple translation, of half the square dimensions.

```
<div style = "...;
  top: 50vh; left: 50vw;
  transform: translate(-50%, -50%)"></div>
```

> **Percent unit** The percent unit `%` refers to the dimension of the parent container. E.g., for our `div` within the body, setting `top` and `left` to 50% would put our top left corner to the center of the body. Here, with the call to `translate`, it becomes as if self centered, and the translation is thus of 50% of the *square* size.

### ID

We can specify the id of an element using `id = "my-id"`.

> IDs are not necessary, but they come in handy for several reasons. The main reason for us now is to be able to identify component in the inspector view. It also helps identification of the element by other elements, which helps for applying a specific style (more later) or retrieving the element in JavaScript (more even later , see next session).

And voilà, we have a neat centered square! The final code can be found here: [square.py (PLACEHOLDER)].

## Circle

As said above, `<div>`s are rectangle elements, but they may also be slightly modified. As an example, their corners can be rounded, a property which we will make use of to make circles. For that we will use a `border-radius` specification within our style.

```
<div style = "...; border-radius = 50%"></div>
```

You may try and change the value of this `border-radius`, to better understand the behavior we're making use of. Notice how much we start definitely resorting to tricks here, which may (and will) be insufficient at some point. HTML proposes alternatives that are more suited to drawing shapes, such as *Scalable Vector Graphics* (SVG).

In HTML, SVGs are elements like divs, but which are designed to contain shapes. Here we will use the `<circle>` shape element. We will specify its properties (radius, center, color) with tags directly linked to the element.
```
<svg>
  <circle cx="100" cy="100" r="100" fill="red"/>
</svg>
```

> Notice that we are at the same level as style **TODO**
> Also notice that here we space things with spaces and not semicolumns.
> some attributes are specific to `<circle/>`

What is going wrong here? Well, f12 can enlighten us here again. As you may see, the circle is cut by the border of the container. In other words, our 150x300 pixels containers does not have the right shape to display the whole shape. We thus have to specify the size of the container, with the usual `style` attribute.

```
<svg style = "height = 200px; width=200px">
  <circle cx="100" cy="100" r="100" fill="red"/>
</svg>
```

## Triangle

A good reason to learn about SVGs is that you can't draw triangles with divs (or rather, you will have an extremely hard time doing so). With SVGs, doing so is much easier, as you can draw any polygon using the `<polygon/>` tag. `<polygon/>` takes a specific attribute named `points` which takes a list of integers corresponding to the coordinates of the polygon's **TODO SOMMET**. Integers in the list will be paired to create the *x* and *y* coordinates of each point.

```

```
Stroking

## Style usage

Define in head
CSS file

# Combining shapes
## Two circles

Two solutions: move the position of the squares, or the transform.
Note that it may not be super clear to just change position values -> introduce calc to show the computations, also allows to use pixels!

## Troxler

Many iterations, long file.

Note that if you don't use calc, you update positions relative to the screen... and thus you do not create a square, since your screen isn't

## Kanisza

We can't draw arcs of circle... yet. So we have to superpose images.

This is problematic to the illusion at hand, since the square is not supposed to exist in the first place! JS will help us with this.

# Combining shapes with JS
