# Grunt: Styleguide <sup>v1.2.0</sup>

Chrometoaster's KSS Styleguide generator.

__Please note: this plugin is optimised for internal Chrometoaster use. YMMV.__

## Terminology

* KSS - Knyle Style Sheets; if you're unfamiliar with KSS, please read our [docs](https://github.com/chrometoasters/ct-grunt-styleguide/blob/master/docs/kss/README.md)
* NPM - the Node Package Manager, installed with NodeJS

## Setup and Usage

### A. One-time setup, for all projects

Open Terminal

#### 1. Install KSS

1. `npm list kss -g`, to check whether you have the kss NPM package installed [[src](http://stackoverflow.com/questions/10972176/find-the-version-of-an-installed-npm-package)]
1. If KSS is `(empty)`:
    1. In Terminal: `sudo npm install -g kss`, to instruct NPM to install the KSS binary so that is available globally

#### 2. Install KSS-Node and its dependencies

This project uses the NodeJS implementation of KSS, so you will also need to install `kss-node` from Github:

1. TODO: `???`, to check whether you have this installed
1. If not:
    1. `cd /path/to/github-clones`, to change to the directory where you store Git repositories that you clone
    1. `git clone https://github.com/chrometoasters/kss-node.git`, to clone our copy of `kss-node`
    1. `cd kss-node`, to change into the directory you just created
    1. `sudo npm install -g` - to instruct NPM to install the `kss-node` dependencies listed in `package.json`. The `-g` ('global') flag instructs OS X to copy the files to `/usr/local/lib/node_modules/kss/`

#### 3. Install Grunt and its dependencies

1. If you haven't used Grunt before, please read [Set up Grunt dependencies](https://github.com/chrometoasters/frontend-grunt-boilerplate#set-up-grunt-dependencies).

#### 4. Install Bower

1. `npm list bower -g`, to check whether you have the Bower NPM package installed [[src](http://stackoverflow.com/questions/10972176/find-the-version-of-an-installed-npm-package)]
1. If Bower is `(empty)`:
    1. `sudo npm install -g bower`, to install Bower

### B. Every time you set up a new project

Open Terminal

#### 1. Navigate to your project directory

1. `cd /PATH/TO/PROJECT-THEME-FOLDER`, to change to your project's theme folder

Note: If you wish to customise where Bower puts installed components, you may add a `.bowerrc` file into your project directory:

        {
            "directory" : "PATH/TO/COMPONENTS"
        }

This `README` makes the assumption that you have used the default Bower install path of `bower_components`.

#### 2. Install the KSS Grunt Task and its dependencies

1. `bower install https://github.com/chrometoasters/ct-grunt-styleguide.git`, to install this Grunt task
1. `cp bower_components/ct-grunt-styleguide/package.json package.json`, to copy `package.json` into your project's theme folder
1. `npm install`, to install the dependencies listed in `package.json`
1. SVN/Git ignore the generated folder: `node_modules`

#### 3. Set up the KSS Grunt Task and customise for your project

1. `cp bower_components/ct-grunt-styleguide/Gruntfile.js Gruntfile.js`, to copy `Gruntfile.js` into your project's theme folder
1. `cp -Ri bower_components/ct-grunt-styleguide/grunt-tasks grunt-tasks`, to copy `grunt-tasks` into your project's theme folder; if this folder already exists you will need to manually merge the files contained within the `options` folder
1. `nano package.json` to open `package.json`
1. Edit the paths to suit your project; note that the `styleguide.src` folder must exist already, but the `styleguide.dest` folder will be created
1. `Control + X` (exit) -> `y` (yes) -> `Enter`
1. Create a project template (eg `styleguide-page.php`) to import the Styleguide page, at the path you specified in `styleguide.page`

        // styleguide.php
        <!-- header code here -->
        <?php
            // START KSS STYLEGUIDE
            include( $_SERVER['DOCUMENT_ROOT'] . '/PATH/TO/PROJECT-THEME-FOLDER/STYLEGUIDE-DEST/index.php' );
            // END KSS STYLEGUIDE
        ?>
        <!-- footer code here -->

Note that the styleguide requires jQuery be present at the top of the page, so if your project `<head>` does not include this already you will need to add it.

#### 4. Run the Grunt

1. `grunt styleguide`, to run the Grunt task

### C. Occasional maintenance

#### 1. To update the styleguide template to the latest version

1. Perform step B1
2. Perform step B2.1
