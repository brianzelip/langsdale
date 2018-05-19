# Proof of concept refactorings for UB Langsdale Find Materials web page

[https://brianzelip.github.io/langsdale](https://brianzelip.github.io/langsdale)

There are four solutions provided in index.html:

1.  row-based float solution
2.  column-based float solution
3.  row-based flexbox solution
4.  column-based flexbox solution

As a point of reference for what row- and column-based mean here, I consider the live Find Materials page tiles to be column-based. That is, when the viewport is narrow enough, the second column collapses under the first column to create one column.

The row-based solutions provide a better visual output in my opinion, because each horizontal pair (on larger devices) are the same height. The column-based approaches can't achieve this.

## About index.html

Each solution is contained in a `<section>` element in index.html

The CSS for each solution is included in a `<style>` block directly above the solution's markup, for streamlining the reference look up of how the CSS and HTML interact.

## About the CSS inside index.html

### Use a modern browser to view!

I prototyped these solutions as quick and dirty as possible, which means that I didn't stop to add [Autoprefixer](https://github.com/postcss/autoprefixer) to the development workflow.

Use a modern Firefox or Chrome browser to see these solutions, as the uses of flexbox may require vendor-prefixes for older browsers.

### CSS conventions

There are two types of CSS conventions on display here - BEM and atomic CSS.

While I prefer to wield atomic CSS, the [BEM method](https://en.bem.info/methodology/) is closer to the "normal way of writing CSS" that the Find Materials page uses.

I kept one solution written in atomic CSS, the fourth "Column-based flexbox method", for demonstration. Basscss is the library used herein for most of the atomic css instances. The rest are original and are contained in the `<head>`'s style block.

## About the float solutions

I included float solutions to demonstrate how to fix the wrapping bugs in the live page.

There are comments in the CSS that point to the essential parts of each solution.

The code currently in production is written in such a way that it becomes difficult to change course for the better. Some major code smells in this regard are the many uses of large amounts of padding and margin, and very particular positioning length values, for general layout. I see this happening all over the place, not just the Find Materials tiles.

Ultimately, what's missing from the live page is a rock solid method for reusable layout patterns. This is what Flexbox and CSS Grid provide. If not using these newer CSS tools, then you want to implement some kind of float-based grid system.

The float-based grid system is conceptually comprised of rows and columns.

Working with floats means you have to know how to work around the undesirable wrapping situations that happen. The general wisdom here is to incoporate a _clearfix_ and know when to use `overflow: hidden`.

## Use `<wbr>` for long strings with no spaces ('KnowledgeWorks@UB')

These solutions use [`<wbr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/wbr) to break up long strings with no spaces in them, like "KnowledgeWorks@UB". This solves:

1.  the bug of truncating such long strings on smaller devices that also have an `overflow: hidden` assigned to it (like in the case of "KnowledgeWorks@UB")
2.  the forced horizontal scroll on smaller devices due to such long strings that do not have `overflow: hidden` assigned to it.

## About index.pug

Continuing our discussion of _the developer user experience_, _automation_, and _front end tooling_, [Pug](https://pugjs.org/) is a HTML templating engine for Node.js.

I used Pug here to minimize the amount of code needed to demonstrate the solutions. I use the [pug-cli](https://github.com/pugjs/pug-cli) locally to render index.html from index.pug, before publishing index.html.

## Another argument for incorporating git into your dev workflow

One of the many benefits of git is that you can see the evolution of the project via the log of "commit messages". See [the log of commits for this project](https://github.com/brianzelip/langsdale/commits/master).

This feature is especially useful for understanding what's going on in your code long after it was written!

Also note that the log lists who is responsible for what changes to the code, and at exactly what point in time. Very handy for teams.

## Further resources

Here are some resources that I used when writing these solutions:

* https://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/
* https://stackoverflow.com/questions/27292942/2x2-grid-in-flexbox-with-fixed-width-column
* http://basscss.com/v7/docs/grid/#breakpoint-based-floats -- the docs that helped me leverage `overflow: hidden` to avoid the tile item text wrapping underneath the floated left image when the text was long enough to do so
* https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis
* http://reflexgrid.com/docs/#basic-example
