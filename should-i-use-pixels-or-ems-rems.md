## Should I use pixels or ems/rems?

use `rem`

### Unit Overview

Historically px units typically represented one device pixel. With devices having higher and higher pixel density this no longer holds for many devices, such as with Apple's Retina Display.

rem units represent the root em size. It's the font-size of whatever matches :root. In the case of HTML, it's the <html> element; for SVG, it's the <svg> element. The default font-size in every browser* is 16px.

### On Using `px`
The majority of CSS examples on the internet use px values because they were the de-facto standard. pt, in and a variety of other units could have been used in theory, but they didn't handle small values well as you'd quickly need to resort to fractions, which were longer to type, and harder to reason about.

If you wanted a thin border, with px you could use 1px, with pt you'd need to use 0.75pt for consistent results, and that's just not very convenient.

### On Using `rem`
rem's default value of 16px isn't a very strong argument for its use. Writing 0.0625rem is worse than writing 0.75pt, so why would anyone use rem?

There are two parts to rem's advantage over other units.

### User preferences are respected
  
You can change the apparent px value of rem to whatever you'd like
Respecting User Preferences
Browser zoom has changed a lot over the years. Historically many browsers would only scale up font-size, but that changed pretty rapidly when websites realized that their beautiful pixel-perfect designs were breaking any time someone zoomed in or out. At this point, browsers scale the entire page, so font-based zooming is out of the picture.

Respecting a user's wishes is not out of the picture. Just because a browser is set to 16px by default, doesn't mean any user can't change their preferences to 24px or 32px to correct for low vision or poor visibility (e.x. screen glare). If you base your units off of rem, any user at a higher font-size will see a proportionally larger site. Borders will be bigger, padding will be bigger, margins will be bigger, everything will scale up fluidly.

If you base your media queries on rem, you can also make sure that the site your users see fits their screen. A user with font-size set to 32px on a 640px wide browser, will effectively be seeing your site as shown to a user at 16px on a 320px wide browser. There's absolutely no loss for RWD in using rem.

Changing Apparent px Value
Because rem is based on the font-size of the :root node, if you want to change what 1rem represents, all you have to do is change the font-size:

```html
:root {
  font-size: 100px;
}
body {
  font-size: 1rem;
}
<p>Don't ever actually do this, please</p>  
```

Whatever you do, don't set the :root element's font-size to a px value.

If you set the font-size on html to a px value, you've blown away the user's preferences without a way to get them back.

If you want to change the apparent value of rem, use % units.

The math for this is reasonably straight-forward.

The apparent font-size of :root is 16px, but lets say we want to change it to 20px. All we need to do is multiply 16 by some value to get 20.

Set up your equation:

```css
16 * X = 20
And solve for X:

X = 20 / 16
X = 1.25
X = 125%
:root {
  font-size: 125%;
}
<p>If you're using the default font-size, I'm 20px tall.</p>
```

Doing everything in multiples of 20 isn't all that great, but a common suggestion is to make the apparent size of rem equal to 10px. The magic number for that is 10/16 which is 0.625, or 62.5%.

```css
:root {
  font-size: 62.5%;
}
<p>If you're using the default font-size, I'm 10px tall.</p>
```
  
The problem now is that your default font-size for the rest of the page is set way too small, but there's a simple fix for that: Set a font-size on body using rem:

```css
:root {
  font-size: 62.5%;
}

body {
  font-size: 1.6rem;
}
<p>I'm the default font-size</p>
```

It's important to note, with this adjustment in place, the apparent value of rem is 10px which means any value you might have written in px can be converted directly to rem by bumping a decimal place.

```css
padding: 20px;
turns into

padding: 2rem;
The apparent font-size you choose is up to you, so if you want there's no reason you can't use:

:root {
  font-size: 6.25%;
}
body {
  font-size: 16rem;
}
and have 1rem equal 1px.
```

So there you have it, a simple solution to respect user wishes while also avoiding over-complicating your CSS.

Wait, so what's the catch?
I was afraid you might ask that. As much as I'd like to pretend that rem is magic and solves-all-things, there are still some issues of note. Nothing deal-breaking in my opinion, but I'm going to call them out so you can't say I didn't warn you.

Media Queries (use em)
One of the first issues you'll run into with rem involves media queries. Consider the following code:

```css
:root {
  font-size: 1000px;
}
@media (min-width: 1rem) {
  :root {
    font-size: 1px;
  }
}
```
  
Here the value of rem changes depending on whether the media-query applies, and the media query depends on the value of rem, so what on earth is going on?

rem in media queries uses the initial value of font-size and should not (see Safari section) take into account any changes that may have happened to the font-size of the :root element. In other words, it's apparent value is always 16px.

This is a bit annoying, because it means that you have to do some fractional calculations, but I have found that most common media queries already use values that are multiples of 16.

|   px | rem |
+------+-----+
|  320 |  20 |
|  480 |  30 |
|  768 |  48 |
| 1024 |  64 |
| 1200 |  75 |
| 1600 | 100 |
Additionally if you're using a CSS preprocessor, you can use mixins or variables to manage your media queries, which will mask the issue entirely.

Safari
Unfortunately there's a known bug with Safari where changes to the :root font-size do actually change the calculated rem values for media query ranges. This can cause some very strange behavior if the font-size of the :root element is changed within a media query. Fortunately the fix is simple: use em units for media queries.

Context Switching
If you switch between projects various different projects, it's quite possible that the apparent font-size of rem will have different values. In one project, you might be using an apparent size of 10px where in another project the apparent size might be 1px. This can be confusing and cause issues.

My only recommendation here is to stick with 62.5% to convert rem to an apparent size of 10px, because that has been more common in my experience.

Shared CSS Libraries
If you're writing CSS that's going to be used on a site that you don't control, such as for an embedded widget, there's really no good way to know what apparent size rem will have. If that's the case, feel free to keep using px.

If you still want to use rem though, consider releasing a Sass or LESS version of the stylesheet with a variable to override the scaling for the apparent size of rem.
