# HTML Basics

Browser display (including with jsPsych) relies on HTML, most often HTML5.
Let us see how it works

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
> Notice that we have two tags here, one after another. Think of them as brackets: everything that we want to define in the head will be enclosed between the tags. Accordingly, the first tag is called the *opening tag* and the other one the *closing tag*. Closing tags specifically have an additional '/' slash at the start).
> Note that a few tags do not enclose content and thus do not use opening tags (e.g. line breaks </br>).

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

## Changing background colors

```
<body style = "background-color: white">
</body>
```

# Simple shapes

## Square

Use div,
see it is of size 0 (non-visible; introduce inspector),
specify width
> we use style here. we could do otherwise but we'll stick to it.

see we can't see it with
specifiy background color of the div

### Centering


### ID

We can specify the id of an element using `id = "my-id"`.

> IDs are not necessary, but they come in handy for several reasons. The main reason for us now is to be able to identify component in the inspector view. It also helps identification of the element by other elements, which helps for applying a specific style (more later) or retrieving the element in JavaScript (more even later , see next session).

## Circle

Rounded borders

SVG variation

## Triangle

SVG

Stroking

## Style usage

Define in head
CSS file
.
