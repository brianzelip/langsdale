I'm trying to redo this layout[1] using flexbox. You'll notice that, right now, it doesn't gracefully realign for smaller screen sizes. Here's the progress I've made so far in implementing flexbox[2]. Now I'm struggling with how to design the layout of the icons and accompanying text. Is there a way, using flexbox, to add vertical spacing in between the stacked icons, or do I simply need to use normal CSS to add padding/margin? Also, can I use flexbox to get closer to the neatly spaced/aligned text layout from first link above, or do I just need to, again, use normal CSS get there?

[1] http://langsdale.ubalt.edu/find-materials/
[2] https://www.dropbox.com/s/qsnasul5nytdby4/flextiles.html?dl=0

See also

* https://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/
* https://stackoverflow.com/questions/27292942/2x2-grid-in-flexbox-with-fixed-width-column
* http://basscss.com/v7/docs/grid/#breakpoint-based-floats -- the article that helped me avoid the tile item text wrapping underneath the floated left image when the text was long enough to do so with out the code provided here in the basscss docs
* https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis
* http://reflexgrid.com/docs/#basic-example
* https://davidwalsh.name/flexbox-layouts

If you're not working with flexbox, then I'd suggest you use a grid (rows and columns) system when fixing legacy stuff or creating new projects.

Also - use `<wbr>`
