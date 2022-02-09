# CSS Aspect Ratio Box

```html
<div class="container">
  <div class="aspect-box">
    <img
      src="https://images.pexels.com/photos/4932184/pexels-photo-4932184.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260"
      alt=""
    />
  </div>
  <div class="aspect-box-new">
    <img
      src="https://images.pexels.com/photos/1028225/pexels-photo-1028225.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260"
      alt=""
    />
  </div>
</div>
```

```css
.container {
  max-width: 960px;
  margin: 0 auto;
}

img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.aspect-box {
  /* Styles for browsers that don't support aspect-ratio */
  position: relative;
  width: 320px;
  background: lightcoral;
  margin-bottom: 32px;
}

.aspect-box::before {
  display: block;
  content: "";
  width: 100%;
  padding-bottom: calc(100% / (16 / 9));
}

.aspect-box > :first-child {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

@supports (aspect-ratio: 1 / 1) {
  .aspect-box-new {
    /* Styles for browsers that support aspect-ratio */
    aspect-ratio: 16/ 9;
    background: lightblue;
    width: 320px;
  }
}
```

Source: [Aspect Ratio is Great](https://css-irl.info/aspect-ratio-is-great/)
