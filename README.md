# electron-uglifier #

Copy, uglify, minify and package [Electron](http://electron.atom.io) projects.

## How It Works

1. Copies application repository to a temporary location.
2. Uglifies JavaScript and CSS files.
3. Installs npm dependencies in a temporary location.
4. Updates build version in package.json.
5. Packages the application using [electron-packager](https://github.com/electron-userland/electron-packager).

## Installation

    npm install electron-uglifier -g (make sure to install globally)

## Usage

    electron-uglifier <path-to-app>

## Options

uglifier options are read from an electron_uglifier.json file in the application's repository.

    {
        "verifyConfig": true | false, // Whether to verify configuration before starting build. (Default: true)
        "archiveOutput": true | false, // Whether to archive electron packager output for Windows and Linux. (Default: true)
        "platforms": [], // Array or platforms to compile for. Supported options: win32, linux, darwin
        "arch": "", // Architecture options Windows (also known as win32, for x86, x86_64, and arm64 architectures), macOS (also known as darwin) / Mac App Store (also known as mas)* (for x86_64 and arm64 architectures), Linux (for x86, x86_64, armv7l, arm64, and mips64el architectures).
        "uglifyList": [], // Array of paths to uglify. JavaScript and CSS files are supported (use / for directory e.g. app/).
        "ignoreList": [], // Array of files to ignore (use / for directory e.g. app/). 
        "versionString": { // Object containing electron packager settings for Windows build.
            "CompanyName": "Company",
            "FileDescription": "Application description.",
            "OriginalFilename": "Filename.exe",
            "ProductName": "Product",
            "InternalName": "Internal Name"
        }
    }

## Output

The uglifier output of each platform from electron-packager is saved to .\releases.

## Sample Structure

    |-- app //can be any custom name
        |-- //Your application code here
        |-- electron_uglifier.json
    |-- interim //The uglifier temporary files are saved to .\interim.
    |-- releases //The uglifier output of each platform from electron-packager is saved to .\releases.

## How to run

Open Command prompt or Terminal and run

    electron-uglifier app 
    //app will your application directory

## Third Party Libraries

* Packaging - [electron-packager](https://github.com/electron-userland/electron-packager)
* File system - [fs-extra](https://github.com/jprichardson/node-fs-extra)
* JSON beautifying - [js-beautify](https://github.com/beautify-web/js-beautify)
* JavaScript uglifying - [babel](https://babeljs.io/)
* CSS minifaction - [minifier](https://github.com/fizker/minifier)
* Removing empty directories - [remove-empty-directories](https://github.com/danielhusar/remove-empty-directories)
* User prompts - [prompt](https://github.com/flatiron/prompt)
* Archiving - [zip-folder](https://github.com/sole/node-zip-folder)
* Log colours - [colors](https://github.com/Marak/colors.js)
* Package info - [pkginfo](https://github.com/indexzero/node-pkginfo)
