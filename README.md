## Hosting Static Google Fonts, optimizing and using it on a page

> "Google fonts are great, but often self-hosting them is a better choice, or if you’re in parts of Europe, it might be your only choice, so in this video I take a look at the basics of how to self-host fonts." - Kevin Powell

! important - for variable fonts the setup is a bit different

1. Head to [Google Fonts](fonts.google.com).
2. Download the font family you want to work with.
3. Unzip file.
   > TrueType fonts are the best for browser support but the file sizes are bigger than ideal.
4. Now to get a more appropriate font file size we'll convert them to webfonts using some kind of converter like [Font Squirrel's Webfont Generator](https://www.fontsquirrel.com/tools/webfont-generator) using the optimal setting.
5. We'll convert all the fonts that will be needed on the website (making sure the font we choose can be used for this purpose on its licensing) and get our fonts in .woff and .woff2 formats which are quite smaller file sizes.
   > Browser support for .woff2 is pretty good but we'll setup with both (.woff and .woff2) just to be safe
6. Drag the .woff and .woff2 files to our /assets/fonts folder.
7. Set them up on the style.css file:

```css
@font-face {
  font-family: "Unbounded"; // font-family name and font-weight can be custom to whatever we want, it's just a mapping but make sure that what it's chosen makes sense
  font-weight: 300; // 500, 600, 900
  src: url("assets/fonts/Unbounded-Light.woff2") format("woff2"), /* fallbacks after it */ url("assets/fonts/Unbounded-Light.woff") format("woff");
}

@font-face {
  font-family: "Unbounded";
  font-weight: 500;
  src: url("assets/fonts/Unbounded-Medium.woff2") format("woff2"), url("assets/fonts/Unbounded-Medium.woff") format("woff");
}

@font-face {
  font-family: "Unbounded";
  font-weight: 600;
  src: url("assets/fonts/Unbounded-SemiBold.woff2") format("woff2"), url("assets/fonts/Unbounded-SemiBold.woff") format("woff");
}

@font-face {
  font-family: "Unbounded";
  font-weight: 900;
  src: url("assets/fonts/Unbounded-Black.woff2") format("woff2"), url("assets/fonts/Unbounded-Black.woff") format("woff");
}
/* if there was an italic font all we would have to do is to add the font-style: italic; to it and also change the src file */
@font-face {
  font-family: "Unbounded";
  font-weight: 900;
  font-style: italic;
  src: url("assets/fonts/Unbounded-Black-Italic.woff2") format("woff2"), url("assets/fonts/Unbounded-Black-Italic.woff") format("woff");
}
```

8. Then we can apply them to our site

```css
body {
  font-family: "Unbounded", cursive;
}
```

9. As a bonus we can also setup a local font on the src attribute as our first choice to make sure that if the user already has the font we choose on their systems there's no need to download anything at all (making sure the filename is the one that would be on the user's system)

```css
@font-face {
  font-family: "Unbounded";
  font-weight: 500;
  src: local("Unbounded Medium"), url("assets/fonts/Unbounded-Medium.woff2") format("woff2"), url("assets/fonts/Unbounded-Medium.woff") format("woff");
}
```
