# grunt-electron-app-builder

Helps build electron baed applications for mac, win and linux with grunt. It will download the prebuilt binaries for either the latest or a specific version, unpack them, and add your application source to the extracted distirbution.

## Getting Started
Install this grunt plugin with: `npm install grunt-electron-app-builder`

Then add this line to your project's gruntfile:

```javascript
grunt.loadNpmTasks('grunt-electron-app-builder');
```

### Example

```javascript
module.exports = function(grunt) {
  grunt.initConfig({
    'build-electron-app': {
        options: {
            platforms: ["darwin", "win32"]
        }
    }
  });
  grunt.loadNpmTasks('grunt-electron-app-builder');
};

```

## The "build-electron-app" task

### Options

#### options.electron_version
Type: `String`
Default value: `most recent release`
Required: `no`

The version of electron you want to use (e.g., `'v0.24.0'`). [Here is a list](https://github.com/atom/electron/releases) of available releases. If not specified, it will query github for the latest release.

#### options.build_dir
Type: `String`
Default value: `build`
Required: `no`

Where application builds should be placed. Releases will be placed into a platform specific subdirectory. '[build_dir]'/'[platform]/' 


#### options.cache_dir
Type: `String`
Default value: `cache`
Required: `no`

Where downloads of the pre-built binaries should be stored.

#### options.app_dir
Type: `String`
Default value: `app`
Required: `no`

Where application source is located. This will be copied to the app directory for each platform build.

#### options.platforms
Type: `String Array`
Default value: `[ 'HostPlatform' ]`
Required: `no`

The platforms to download and build packages for. Supported platforms are `'darwin'`, `'win32'`, `'linux32'`, and `'linux64'` (`'linux'` works as well for backwards compatibility, and maps to linux32). If ommitted, defaults to the host platform. 

Note that building `'darwin'` packages on a windows host is currently unsupported due to the format of the darwin electron zip, which includes symlinks.

#### options.app_title
Type: `String`
Default value: `<App Name>`
Required: `no`

This will be used to rename the application. This defaults to the 'name' field in your app's package.json.

#### options.app_id
Type: `String`
Default value: `com.electron.<options.app_title>`
Required: `no`

The Mac application's bundle id will be set to this value.

#### options.app_version
Type: `String`
Default value: `<App Version>`
Required: `no`

This will be used to set the version for the application. This defaults to the 'version' field in your app's package.json.


## To Do:
- Add support for further application customization (name, icon, etc)


## License
Copyright (c) 2014 Chad Fawcett
Licensed under the Apache 2.0 license.
