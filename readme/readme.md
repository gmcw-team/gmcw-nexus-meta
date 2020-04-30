# Welcome to GM Nexus

Welcome to GM Nexus, a public registry for GM packages.  GM Nexus allows developers to share and find GM packages in one place.

## Downloading packages
GM Nexus works directly with gmpm. details coming soon!  For other ways of downloading packages, see below

### Downloading manually
Click the *Download Tarball* icon to download packages from the website. The downloaded *.tar.gz* file can be opened using any archive tool, like [7-zip](https://www.7-zip.org/).

### Downloading packages using npm/yarn
GM Nexus is powered by *npm*! Add the *@gm* scope to your npm config by using `npm set @gm:registry https://nexus.gmcw.dev` you can then download packages into your *node_modules* folder using `npm install @gm/<package_name>`.

See [here for instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) on installing npm.

## Creating and Uploading a package to GM Nexus
To upload and share your package on GM Nexus, you must use *npm* (or other compatible package managers such as *yarn*), and must have a GitHub account (used for logging in).

### Setting up

1. Download and install *npm* (or compatible package manager like *yarn*) if you do not already have it. See [here for instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) on installing npm.
2. Sign up for a [GitHub](https://github.com/) account if you don't already have one.
3. Click Login in the menu to the top right, and OAuth with your GitHub account.
4. Set up your *npm* to use GM Nexus:
```
npm set @gm:registry https://nexus.gmcw.dev
npm config set //nexus.gmcw.dev/:_authToken "<your auth token>"
npm config set //nexus.gmcw.dev/:always-auth true
```
You can copy these commands from the (i) icon in the menu, which will display your own authToken. These settings will be written to your *.nprc* file in your home folder.

Your machine now set up to publish to GM Nexus. In the event that you receive 403 errors when publishing, log out of GM Nexus and log back in to receive a new token, and re-run step 4.

### Publishing a Package

Before you are able to publish, your project folder must contain the right metadata.

1. In your project folder, run `npm init` and answer the prompts, use the following format for the package name:
```
@gm/<github_username>.<package_name>
```
(See below section on Package naming for more details). This will create a *package.json* file containing package metadata.  See below section on Package naming.
2. Edit *package.json* as desired, some of these details will be listed alongside your package in the GM Nexus search results. Please remember to include a GitHub repository address where users of your package can find more information about the package! See [here for more details](https://docs.npmjs.com/files/package.json) on *package.json* metadata.
3. Ideally supply a *README.md* file in the root of your project folder describing your package and how it works.
4. Once you are ready to publish, run `npm publish`

### Updating a package

If you need to edit or update a version of your package:

1. Edit *package.json* and bump the version number or
2. Run `npm publish`

## Package naming

Package names are in the format `@gm/<username>.<package_name>` where *<username>* is your GitHub username. Only you have the permission to create and update packages that begin with `@gm/<username>.`

Packages have the `@gm` scope, this is to allow the GM Nexus to coexist with other public *npm* registries for those that use *npm* for non-GM projects.  The command `npm set @gm:registry https://nexus.gmcw.dev` mentioned in the above sections adds a configuration to use GM Nexus for the `@gm` scope, and other scopes or global scopes will continue to use the default public *npm* registries.