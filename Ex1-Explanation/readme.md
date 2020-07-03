## BLOCK-readText

### Adding Media

When we surf on internet, the core content on a website we usually find in the form of text. Addition to text, HTML provides ways to add different type of media in the form of images, audio, video. The content from other websites also can be embedded in the form inline frames.

Apart from texts these are the different form media that we may see on websites. In this lesson we are going look at how these media can be added on a page.

#### Adding Images

After texts another type of content we mostly find on a page are the images. Images are the form of media that represents your content in pictorial form, also enhances the design of the page. To embed images we use `<img>` inline-level element. The `<img>` is a self contained element that comes with `src` and `alt` atrribute.

```html
<img src="football.jpg" alt="Two little kids are playing football together" />
```

As img is a self closing element, it comes in single tag. To bring an image on a page the `src` attribute necessary to spcify the path.

Addition to the `src` the comes with `alt` attribute, which is alternative to the image. The value of `alt` attribute must include the description of the image. It is recommned to add `alt` attribute it helps in seo also incase the image is not displayed the alternative text will be shown to the users.

**Sizing Images**

By default image will be dispalyed on a page in it's original size, however we can resize it. There are two ways to resize an image, using `width` and `height` attribute on img element and other ways is using CSS.

```html
<img
  src="football.jpg"
  alt="Two little kids are playing football together"
  width="300"
  height="300"
/>
```

Using CSS `width` and `height` properties image can resized. However, if both HTML attributes and CSS properties are used, the CSS properties will take the precedence.

```css
img {
  width: 300px;
  height: 300px;
}
```

One thing keep in mind while resizing the images that it always mentain it's aspect ratio. So specifying either `width` or `height` the will adjust the dimension of the image. If you dont want control over both `width` and height, apply either of the property, but specifying both width and height both at the same time aspect ratio will be lost and you may see a distorted image.

**Image Formats**

Images comes in various formats, most commonly supported formats are `gif`, `png`, `jpg`, `svg`. One of the most widely formats are `png` and `jpg`.

The `svg` is newly introuduced format which is a vector based image. The quality of svg format does not effect by resizing, unlike other formats. The other formats like png or jpg will lose its quality once you resize it.

> **`<img>` element Vs `background-image` property**
>
> So far we know that there are two primary ways add an image on page, using `<img>` element or `background-image` property.
> Both of the option works fine, but they have different use cases.
>
> The img element is used when the image is part of content and holds some semantic meaning on a page.
>
> The background-image property is used when the image is part of design and directly not relevant to the content of the page.

#### Adding Audio

To add an audio on a page HTML provides `<audio>` element, that comes with both opening and closing tag. Similar to `img` element the `audio` element also accepts src attribute to spcify the source URL of the audio.

```html
<audio src="roar.mp3"></audio>
```

**Audio Attributes**

Addtional to `src` attribute the `<audio>` elements accepts few other attribute also. These attributes provides better control on audio element on a page. Most popular attributes are, `autoplay`, `controls`, `loop`, and `preload`.

The `autoplay`, `controls` and `loop` are boolean attribute, if it is present on the `<audio>` element that means the value is true.

By default the `<audio>` element is not displayed on a page. If the element contains `autoplay` attribute the audio will play when page loads wihout displaying anything.

```html
<audio autoplay src="roar.mp3"></audio>
```

To display the audio element on the page the `controls` attribute is necessary. Adding controls attribute the browser will display the audio element including other controls like play pause, seek, and volume controls.

```html
<audio controls src="roar.mp3"></audio>
```

The `loop` attribute will repeat the audio continuously begining to end.

The last `prelaod` attribute will identify the information about the audio if there is any. The preload attribute attribute accepts three values: `none`, `auto` and `metadata`. The `none` value wont preload any information, `auto` value will prelaod all the information about the audio. The metadata value is in between the none and auto, because it does not preload all the information but few such as clip path's length.

When preload attribute is not present on the audio element, all the information of the audio will loaded by default.

**Audio Fallbacks**

Different browser supports different formats of the audio. Most popular formats are ogg, mp3, and wav. So using `<audio>` element with `src` attribute is not enough for all the available browsers. Because with this approach we can provide just one format. But we need to provide fallbacks for all browsers.

To add fallback formats we will remove the `src` attribute from the audio element. We will use `<source>` element with `src` attribute inside the audio element.

```html
<audio controls>
  <source src="roar.ogg" type="audio/ogg" />
  <source src="roar.mp3" type="audio/mpeg" />
  <source src="roar.wav" type="audio/wav" />
  Please <a href="roar.mp3" download>download</a> the audio file.
</audio>
```

Different `<source>` element is nested with src attribute, adding the value of each format. Addition to `src` attribute there exist `type` attribute also to specify the type of the audio. With the presence of `type` attribute the browser will quickly recognise the audio type and rest will be ignored.

There are some old browser which do not support audio element because it is newly introduced element. For that purpose you can provide a download link. The browser which do not support audio element the anchor link will be displayed to download the file.

#### Adding Video Element

Video can be also added on a page using to `<video>` element similar to `<audio>` element. Works the same way with same attributes(`src`, `autoplay`, `controls`, `loop`, `and` `preload`).

However, without controls attribute also the video element will be displayed, but we cannot play or pause. But it can be automatically played with `autoplay` attribute, without any controls.

```html
<video src="earth.ogv" controls></video>
```

**Poster Attribute**

The `<video>` element can also accepts poster with an image URL value to show before the video is played.

```
<video src="earth.ogv" controls poster="earth-video-screenshot.jpg"></video>
```

**Video Fallbacks**

Smilar to the audio element video element also require video fallbacks. The markup is same as audio element to.

```
<video controls>
  <source src="earth.ogv" type="video/ogg">
  <source src="earth.mp4" type="video/mp4">
  Please <a href="earth.mp4" download>download</a> the video.
</video>
```

**Embeding Video**

Addtion to above way of adding a video on a page, one other way is to embed a video, using [YouTube](https://www.youtube.com/) or [Vimeo](https://vimeo.com/). These websites allow us upload our videos, and allow us to embed our video on a page using inline frame.

```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/668nUCeBHyY"
  frameborder="0"
  allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen
></iframe>
```

Embeding video from online platfrom like YouTube or Vimeo is consider as most preferrable way. Because you dont have to worry about the player and other format of the video.

#### Inline Frames

Inline frame element allow us to embed antoher HTML page within the current page. To do this `<iframe>` tag is used.

```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/668nUCeBHyY"
></iframe>
```

To add the path of the video, src attribute is used which accepts value in url, which load the page with embeded content.

Mainly the iframe element is used to embed media from external websites like YouTube, Google Maps, and others.

For Example let's add Google Map.

```html
<iframe
  src="https://www.google.com/maps/embed?pb=!1m14!1m12!1m3!1d3375.919684030991!2d76.3514099151738!3d32.20639478114809!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!5e0!3m2!1sen!2sin!4v1589823959436!5m2!1sen!2sin"
  width="600"
  height="450"
  frameborder="0"
  allowfullscreen=""
  aria-hidden="false"
  tabindex="0"
></iframe>
```

By default the iframe element comes with default styles like border, width and height. The iframe tag accepts few set of attributes such as frameborder, width, and height, that can be used to style. It can also be styled using CSS properties and value.

#### Figure & Figcaption

The `<figure>` and `<figcaption>` are newly introuduced element to semantically markup self contained content or media.

**Figure**

The `<figure>` is block-level element that can wrap self contained element specially media. The element like, images, audio, videos, diagrams, illustrations, etc can be nested inside `<figure>` tag.

```html
<figure>
  <img src="football.jpg" alt="Two little kids are playing football together" />
</figure>
```

**Figurecaption**

To add a heading or caption inside `<figure>` element `<figcaption>` tag is used. If you have `<figcaption>` inside `<figure>` element then you can avoid `alt` attribute in`img` element.

```html
<figure>
  <figcaption>Two little kids are playing football together</figcaption>
  <img src="football.jpg" />
</figure>
```



