+++
date = 2020-09-16T06:50:00Z
tags = []
title = "Add a Static Directory to an Eleventy Project"

+++
**# Add a Static Directory to an Eleventy Project**  
Aug 17, 2020 Eleventy

Some static site generators, like Gatsby, have the concept of a static folder, in which anything you drop into that folder makes its way (unprocessed) to the build directory during the build process.  
With Eleventy, a similar feature is trivial to achieve, but not so straightforward out of the box.  
The simplest way to setup a static folder is to use the manual passthrough file copy. After reading the docs, it seems like it would be as simple as adding this code to your Eleventy config file:\`\`\`module.exports = function (eleventyConfig) { eleventyConfig.addPassthroughCopy("static")}\`\`\`But that would actually nest everything in static/ under _site/static/, assuming your output directory is _site (which is the default).  
But what we really want is to copy everything in static directly to _site. To do that we can use an option in which we change the output directory. That code looks like this:  
``.eleventy.js``

    module.exports = function (eleventyConfig) { eleventyConfig.addPassthroughCopy({ static: "/" })}

This tells Eleventy to take everything in the **\`static/\`** directory and copy it to the root of your build directory (e.g. \`static/sitemap.xml\` to \`_site/sitemap.xml\`).

<!-- <dl> <dt>Definition list</dt> <dd>Is something people use sometimes.</dd>  
<dt>Markdown in HTML</dt> <dd>Does _not_ work **very** well. Use HTML <em>tags</em>.</dd></dl> -->