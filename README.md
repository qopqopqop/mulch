*Note* This project is in a very early state. It works great as-is since it's a dev tool, but we would love contributions/suggestions to make it work even better.

# Mulch

Mulch is a Gulp recipe that features Twig, LESS/SASS, JS compilation and BrowserSync. It's a great starting point for frontend projects that run on PHP backends that use Twig. (Craft CMS, Drupal 8, Symfony, HiFi, etc). It makes it easy to develop the frontend of those projects without running a whole server. Because it has BrowserSync, as soon as changes are made to your source files, those are instantly reflected in the browser without the need to click refresh!

## How to install

To install Mulch, you'll first need to install Node. Once that is installed, two simple lines get it running:

`sudo npm install`

This will install all of the dependencies. (The sudo is likely just required for the BrowserSync installation. Some assistance in removing this requirement would be awesome.)

## How to use

A single line will get you up and running.

`gulp mulch-watch`

This will compile all of the assets and launch BrowserSync. Your browser should open and display the "Hello World" page. While this is running all of your project assets will be watched and as soon as they are changed you'll see the changes in your browser!.

## Project Structure

There are two main folders in the project:

* src - This holds all of your source files. Some sample ones are in place.
* compiled - Once you execute mulch-watch this will be created and it holds all of the compiled assets and html pages. This is also where BrowserSync looks to serve content. If you need images, you'll need to put them in here.

### Twig Structure

The most interesting folder in src is "templates". This is where all the twig templates go. Inside this directory is a "urls" folder. Every template in this folder will be treated as an accessible URL by BrowserSync once things are compiled. So if you want a /about.html page, create "templates/urls/about.html". It also uses subfolders correctly so "templates/urls/about/team.html" will show up at /about/team.html.

### Data Folder

This folder can contain any number of valid json files. These will be made available to all twig templates indexed against their filename. So a file named "foo.json" would be available in the templates with {{ foo }}. This is a helpful way to inject/use some data from a project you are mocking up.

### LESS/SASS Folders

Depending on which you are using, the target file will be all.less or all.scss. This should include any other files you wish to use.

### Scripts Folder

All scripts in the scripts folder are compiled and minified. The scripts in the libs subdirectory are added first.

## Other commands

Each sub-task is available via gulp if you wish to run them independently. They are:

* browser-sync - Launches BrowserSync
* data - Compiles all json data files
* twig - Compiles twig templates _after_ data is run
* less - Compiles LESS files
* scripts - Compiles all scripts
* mulch-compile - Compiles all assets in the correct order. Useful if you're using this recipe without BrowserSync
* mulch-watch - Compiles all assets, launches BrowserSync and then watches files for changes