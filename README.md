# responsive-breakpoints-lab

Five small pages, five stylesheets, one subject: media queries. Plain HTML and
CSS, no framework and no JavaScript. The pages keep their teaching skin on
purpose, red outlines on every box and a header that turns green, red or plain
depending on the range in force, so the breakpoint being applied is visible at
a glance instead of having to be inferred.

## Breakpoints

Three ranges, and each one closes just below the next one's start, so exactly
one is ever in force:

| Range | Query |
| --- | --- |
| Phone | `max-width: 639.98px` |
| Tablet | `min-width: 640px` and `max-width: 959.98px` |
| Desktop | `min-width: 960px` |

The fraction is the point. `max-width: 640px` and `min-width: 640px` are both
true at exactly 640 px, so a page written on round numbers has two ranges live
at the boundary and depends on the order of the blocks in the file to resolve
them. Closing at 639px instead would leave a gap, since a device pixel ratio can
land the viewport on a fractional width. Verified in the browser at 639, 640,
959 and 960 px on all five pages: one range each time.

Exercise 4 uses 665 px instead of 640 px, closed the same way at 664.98 px.

## The five exercises

### 1. One centred block

![Exercise 1 at 375, 800 and 1280 pixels](preview-no1.png)

A single content block, centred with Flexbox. The rules shared by the three
ranges sit once at the top of the file, and each range declares only the header
colour that identifies it.

### 2. Two blocks, three flows

![Exercise 2 at 375, 800 and 1280 pixels](preview-no2.png)

The same two blocks stack on a phone, split the row in half on a tablet, and
become two fixed 300 px cards on a desktop. Three different mechanisms for the
same markup: `inline-block`, then Flexbox, then `inline-block` again at a fixed
width.

### 3. The same page, written mobile first

![Exercise 3 at 375, 800 and 1280 pixels](preview-no3.png)

Base rules are the phone layout, and each range above only declares what
changes. The tablet range floats the two blocks, and `main` carries
`display: flow-root` to contain them and keep the footer below.

### 4. Image, text, and a footer that leaves

![Exercise 4 at 375, 800 and 1280 pixels](preview-no4.png)

The footer is hidden below 665 px through a `no-mobile` class, the image goes
full width on a phone and floats beside the text on a tablet. `flow-root` again
on the container, so the float stays inside it.

### 5. Three panels

![Exercise 5 at 375, 800 and 1280 pixels](preview-no5.png)

Menu, content and side panel. Stacked on a phone, menu plus content on a tablet
with the side panel pushed to its own row, and three columns at 18, 64 and 18
per cent on a laptop. The panels are laid out with Flexbox, so no float is
involved in placing them.

## Markup notes

- No `X-UA-Compatible` meta. Internet Explorer was retired in June 2022 and the
  tag does nothing but sit there.
- `lang` on every `<html>`, so a screen reader does not have to guess the
  language and read the page in the wrong voice.
- `alt` on both images.
- The menu in exercise 5 is one list of three items rather than three lists of
  one, which is how it is announced.
- Containers holding floats use `display: flow-root`, so the footer stays below
  them without a clearfix element.
- Rules shared by all three ranges live once at the top of each file rather
  than inside every media query.

## Structure

```
no1.html … no5.html    the five pages
css/style1.css …       one stylesheet per page
images/                two placeholder images
```

## Running it

No build step and no dependency. Clone the repository and open any of the five
pages in a browser, or serve the folder:

```bash
python -m http.server 8000
```

Then resize the window across 640 px and 960 px and watch the header colour.

## Stack

HTML5, CSS3, media queries, Flexbox. No framework, no JavaScript, no external
asset.

## Résumé

Cinq pages consacrées aux media queries, avec la peau pédagogique d'origine:
contours rouges et en tête coloré selon le palier, pour que le palier actif se
voie du premier coup d'œil. Trois plages, chacune fermée juste sous le début de
la suivante, de sorte qu'une seule s'applique à la fois: `max-width: 640px` et
`min-width: 640px` sont tous deux vrais à exactement 640 px, et une page écrite
sur des nombres ronds dépend alors de l'ordre des blocs dans le fichier.
Vérifié dans le navigateur à 639, 640, 959 et 960 px sur les cinq pages.

## Licence

MIT. See [LICENSE](LICENSE).
