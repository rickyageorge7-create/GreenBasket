# GreenBasket website: presentation and study guide

This guide explains the Group 10 website, how its pages connect, how the HTML and CSS work, and what the customer inquiry form does. It describes the version in this project folder.

## 1. What the website does

GreenBasket is a four-page farm produce website for a class project. It introduces the project, displays five products, gives sample prices for three products, explains the group and its members, and provides a way for customers to prepare an inquiry for email or WhatsApp.

The website uses HTML for page structure and content, CSS for appearance and responsive layout, images in `images/`, and a short JavaScript function in `contact.html` to prepare inquiries. It has no server or database.

## 2. How the files fit together

- `index.html` is the home page and shows five product cards.
- `about.html` explains the project and lists team members, student IDs, and roles.
- `services.html` shows a sample price table, product photographs, and services.
- `contact.html` shows contact details and the inquiry form.
- `style.css` contains shared colors, layout rules, component styles, hover effects, and mobile breakpoints.
- `images/logo.jpg` is the uploaded GreenBasket seal. CSS uses it both in the header and as a faint watermark.
- `images/cassava.jpg`, `images/plantains.jpg`, `images/palm-oil.jpg`, `images/hot-peppers.jpg`, and `images/country-rice.jpg` are the locally stored product photographs.

Keep the HTML files, `style.css`, and `images/` together. The relative paths such as `images/logo.jpg` are resolved from the HTML file’s folder.

## 3. Common HTML structure

Each page is a document with this general shape:

```html
<!doctype html>
<html lang="en">
  <head>...page information...</head>
  <body>...visible page...</body>
</html>
```

- `<!doctype html>` tells the browser to use modern HTML rules.
- `<html lang="en">` is the root element. `lang` tells browsers and assistive technology that the page is in English.
- `<head>` contains information about the page that is not the main visible content.
- `<meta charset="UTF-8">` allows the page to show a wide range of characters, including punctuation and accented letters.
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">` makes the layout use the device’s actual screen width on phones and tablets.
- `<title>` names the page in the browser tab and in bookmarks.
- `<link rel="stylesheet" href="style.css">` loads the shared stylesheet.
- `<body>` contains the content visitors see and interact with.

### Semantic page landmarks

- `<header>` contains the logo and main navigation.
- `<nav aria-label="Main navigation">` identifies the site navigation. The accessible label tells screen-reader users what the navigation is for.
- `<main>` contains the page’s primary content. There should be one main content area per page.
- `<section>` groups related content, such as the hero, products, and team.
- `<footer>` contains repeated closing details such as the project name, location, and phone number.

These tags describe the purpose of their content. They are easier to understand and navigate than using generic containers for everything.

### Containers and links

- `<div>` is a generic grouping element. Classes such as `container`, `navbar`, and `grid` let CSS arrange its contents.
- `<a href="services.html">...</a>` creates a link. A relative `href` such as `about.html` opens another local page. An external `href` opens an online address.
- The logo is an image inside a link to `index.html`, so selecting the logo returns to the home page.
- `&amp;` displays an ampersand (`&`) in HTML text. `&copy;` displays the copyright symbol.

### Headings, paragraphs, and inline elements

- `<h1>` is the main heading of a page. Use one clear page-level heading.
- `<h2>` is used for major sections; `<h3>` is used for cards or subsections inside them.
- `<p>` marks a paragraph.
- `<span>` groups a short inline piece of text for styling without starting a new line.
- `<strong>` marks text with strong importance, such as a field label.
- `<small>` is used for compact supporting text in the brand lockup.

Headings should follow a meaningful order. They are not selected just to make text a certain size; CSS controls size.

## 4. Navigation, logo, and repeated page header

The header repeats on all four pages so people can move between Home, About, Products & Services, and Contact from anywhere. Each navigation link’s `href` is the matching HTML filename.

The header uses the same `.site-header`, `.container`, `.navbar`, and `.brand` classes on each page. `images/logo.jpg` is the supplied seal; its `<img>` element has descriptive `alt` text. CSS also uses the same image with low opacity behind the page content as a watermark.

The CSS class names are not HTML tags. They are labels written in `class="..."` that let CSS target an element. One element may have multiple classes, as in `class="button button-outline"`.

## 5. Home page: `index.html`

The home page is arranged in this order:

1. Header and navigation.
2. Hero introduction, project label, main heading, and two call-to-action links.
3. Five product cards.
4. Three reasons to choose GreenBasket.
5. Shared footer.

The hero’s `h1` communicates the main message. The two links styled as buttons go to the Products & Services and Contact pages. They remain ordinary links, so they work without JavaScript.

Each product is an `<article class="card">`. An article is a self-contained piece of content. Inside it:

- `<div class="product-image">` gives the photo a consistent frame.
- `<img src="images/...jpg" alt="...">` loads the photo and provides a text description for screen readers or if the image fails to load.
- `<div class="card-body">` groups the product text.
- `<span class="tag">` displays a small category label.
- `<h3>` gives the card’s product name.
- `<p>` describes how the product is used.

All five image paths should resolve to files in the local `images/` folder. The image CSS sets the same 4:3 frame and uses `object-fit: cover`; this fills each frame while cropping any extra edges proportionally.

The `Why Choose GreenBasket?` section uses `.info-card` blocks. The footer repeats the location and phone details for easy access.

## 6. About page: `about.html`

The About page explains the purpose and audience of the project, describes Ricky’s web development contribution, and lists group members. Each person’s card uses:

- `<div class="info-card team-card">` for a consistent card with a gold top edge.
- `<h3>` for the person’s name.
- `<p>` for the student ID and role summary.
- `<strong>` to make “Student ID” stand out.

The group leader card intentionally uses `[Group Leader Name]` and `[Add ID]` placeholders until those details are supplied. Member role descriptions were drafted for the project and should be checked with each person before presenting them as factual contributions.

## 7. Products & Services page: `services.html`

The page contains three main parts:

### Sample price table

- `<div class="table-wrap">` allows the table to scroll horizontally on a narrow screen.
- `<table>` holds tabular information.
- `<thead>` groups the table headings.
- `<tbody>` groups the product rows.
- `<tr>` means one table row.
- `<th>` is a heading cell; `<td>` is a regular data cell.

The price note correctly says the listed prices are fictional examples. Do not present them as verified current market prices.

### Produce photo gallery

The gallery uses the same `.grid`, `.card`, and `.product-image` styling as the home page. Each `<figure>` groups an image and its caption; `<figcaption>` identifies the pictured product. These images use local paths, so they do not depend on a remote image host.

### Services

Three `.info-card` elements describe product information, availability inquiries, and pickup or delivery inquiries.

## 8. Contact page and inquiry form

The left card lists GreenBasket’s location, email, WhatsApp number, and hours. The email address uses a `mailto:` link to start an email. The WhatsApp link uses the international-format number `231775399168`: Liberia’s country code is 231, and WhatsApp’s click-to-chat format omits the local leading zero.

The form uses these elements:

- `<form>` groups all fields and the submit action.
- `<label for="fullname">` describes the input. Its `for` must match the input’s `id` so clicking the label focuses the right field.
- `<input type="text">` collects a name.
- `<input type="tel">` collects a phone number; `tel` may show a suitable phone keyboard on a mobile device.
- `<select>` and `<option>` make a product choice and a delivery-method choice.
- `<textarea>` accepts a longer message.
- `required` asks the browser to check that the field is filled before submission.
- `name` identifies a form value so JavaScript can read it.
- `<button type="submit">` starts form submission.

The `onsubmit="return sendInquiry(event);"` calls the page’s JavaScript function. The function:

1. Stops the browser from submitting to a nonexistent server with `event.preventDefault()`.
2. Reads the entered values with `new FormData(form)` and `data.get(...)`.
3. Builds one message containing the customer’s name, phone, product, and question.
4. If Email is selected, makes a `mailto:` URL with a subject and encoded message body.
5. If WhatsApp is selected, opens a `wa.me` URL with the message encoded into the link.

This is useful on a static GitHub Pages website, but it does not silently send or save the form. The customer’s email app or WhatsApp opens with a draft; the customer must review and press Send. A real automatic web form would need a server or a trusted form-processing service.

## 9. CSS: colors, layout, and appearance

CSS follows this pattern:

```css
.card {
  background: var(--white);
  border-radius: var(--radius);
}
```

`.card` is a class selector: the dot means “select elements whose class includes card.” Braces contain declarations. Each declaration has a property, a colon, a value, and usually a semicolon.

### Color variables

At the top of `style.css`, `:root` defines custom properties. `:root` means the document root, so its variables are available throughout the stylesheet. For example:

- `--primary-green: #316B3C` is Group 10’s main green.
- `--accent-yellow: #E9C96A` is Group 10’s yellow.
- `--cream`, `--white`, and `--tint` provide light backgrounds.
- `--dark` and `--muted` provide main and secondary text colors.
- `--border`, `--radius`, and `--shadow` provide shared edge, corner, and depth styles.

`var(--primary-green)` reads a custom property. Changing the value once updates every rule that uses it.

### Global rules and box sizing

- `*` selects every element. `box-sizing: border-box` makes an element’s declared width include its padding and border, which makes sizing easier.
- `margin: 0; padding: 0` resets browser default spacing so the page starts consistently.
- `html { scroll-behavior: smooth; }` makes in-page scrolling smooth.
- `body` sets the base font, background, text color, and line spacing.
- `img { display: block; max-width: 100%; }` removes inline-image gaps and prevents images from overflowing their containers.
- `a { color: inherit; text-decoration: none; }` makes links inherit text color and removes default underlines; hover styles provide interaction cues.
- `.container` uses a percentage width with a maximum width and automatic side margins to center content.

### Flexbox and grid

- `.navbar` uses `display: flex` to place the brand and navigation in a row. `align-items: center` aligns them vertically; `justify-content: space-between` pushes them apart; `gap` adds space between them.
- `.nav-links` is a flex row. `flex-wrap: wrap` lets links move to another line if there is not enough width.
- `.grid` uses CSS Grid. `repeat(3, 1fr)` creates three equal columns; `gap` sets the space between cards.
- In media queries, `.grid` changes to two columns and then one column on narrower screens.

### Hero, buttons, cards, and photos

- `.hero` gives the top banner its dark layered green background, white text, and generous spacing.
- `clamp(min, preferred, max)` lets heading sizes grow with the screen but stay within readable limits.
- `.button` makes links and form buttons look consistent. `:hover` applies only while the pointer is over an element.
- `.button-outline` adds the transparent secondary button style.
- `.card` and `.info-card` apply white surfaces, borders, rounded corners, and shadows.
- `.product-image { aspect-ratio: 4 / 3; overflow: hidden; }` gives product photos a consistent frame and hides image edges outside that frame.
- `.product-image img { width: 100%; height: 100%; object-fit: cover; }` fills the frame and crops excess image area without distorting it.
- `.tag` makes the small category pill.
- `nth-child(even)` selects every second table row to create alternating row shading.

### Page polish and accessibility

- `::before` and `::after` are pseudo-elements: CSS-generated decoration, not HTML content. The hero uses these for subtle rings; `body::before` displays the low-opacity logo watermark.
- `transition` animates visual changes smoothly. Hover rules lift cards and buttons and slightly zoom product photos.
- `@media (prefers-reduced-motion: reduce)` reduces animation for people who prefer less motion.
- `@media (max-width: 760px)` and `@media (max-width: 520px)` apply different layouts at smaller screen widths.
- `z-index` controls stacking order. The watermark is behind the page content; `pointer-events: none` makes it ignore clicks.
- `position: sticky; top: 0` keeps the header near the top of the viewport while scrolling.

## 10. Proofreading and presentation checks

The spelling and punctuation on the main pages are generally clear. The following content points deserve attention:

1. The group leader placeholder must be replaced with the correct name and ID before final submission.
2. The member role summaries are draft descriptions. Confirm them with the team so the presentation accurately reflects each person’s work.
3. The prices on Products & Services are labelled fictional examples; keep that explanation when presenting.
4. The product photos and watermark now use local image files. Keep `images/` alongside the HTML files when sharing or uploading the site.
5. The inquiry form opens a prefilled email or WhatsApp draft; it does not automatically send or store messages.

### Short presentation summary

“GreenBasket is a responsive four-page farm produce website. HTML provides the page structure and form controls. One shared CSS file keeps the Group 10 colors, header, cards, tables, spacing, and mobile layout consistent. The home page introduces five products, the services page presents sample units and prices, the About page explains our team, and the Contact page prepares inquiries for email or WhatsApp. The product photographs and supplied logo are stored in the images folder. The prices are classroom examples, and the inquiry form opens a message draft for the customer to send.”
