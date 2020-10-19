# ME30 website
### Tufts University, Fall 2020

### Working on the website
This site is built using Hugo. Every time you commit changes to this repository, a Github Action is triggered, which pulls a copy of the repository to our webserver, and tells the webserver to run Hugo to update the live site. It takes around 10 seconds for this to happen; after that, your changes will be live on the internet.

If you want to dig a little deeper, you can install Hugo on your local computer [with an installer](https://gohugo.io/getting-started/installing/)  
The site can then be built by running `hugo` in the top level directory. This will generate a `public/` folder.  
Inside the `public/` folder, you can run an HTTP server to view the content locally (you could do this with `python3 -m http.server`).  

### Adding new pages
All main content for this site is stored in the `content/` folder, and then organized by topic. All site pages are rendered automatically from markdown files (`.md` extension), and creating new ones will automatically integrate them into the website according to where they are located in the file structure. For a markdown cheat-sheet, check [the Markdown Guide](https://www.markdownguide.org/basic-syntax/). You might also be interested in the various features added by the [Hugo Book theme](https://github.com/alex-shpak/hugo-book) that we're using.
