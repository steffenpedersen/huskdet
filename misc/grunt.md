# Grunt

Well, Grunt is a task runner. Grunt can do all of those things for you.

Install the Grunt CLI \(command line interface\). That’s what makes the grunt command in the terminal work.

```
$ npm install -g grunt-cli
```

Go to the project.

```
$ npm init
```

Make the file `package.json`.

Create `Gruntfile.js`.

### Concatenate files

```
$ npm install grunt-contrib-concat --save-dev
```

```
module.exports = function(grunt) {

    // 1. All configuration goes here 
    grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),

        concat: {  // Concatenate
            dist: {
                src: [
                    'js/libs/*.js', // All JS in the libs folder
                    'js/global.js'  // This specific file
                ],
                dest: 'js/build/production.js',
            }
        }
        
    });

    // 3. Where we tell Grunt we plan to use this plug-in.
    grunt.loadNpmTasks('grunt-contrib-concat');

    // 4. Where we tell Grunt what to do when we type "grunt" into the terminal.
    grunt.registerTask('default', ['concat']);

};
```

### Minify JavaScript

```
$ npm install grunt-contrib-uglify --save-dev
```

Then we alter our_Gruntfile.js_to load the plug-in:

```
grunt.loadNpmTasks('grunt-contrib-uglify');
```

Then we configure it:

```
uglify: {
    build: {
        src: 'js/build/production.js',
        dest: 'js/build/production.min.js'
    }
}
```

Let’s update that`default`task to also run minification:

```
grunt.registerTask('default', ['concat', 'uglify']);
```

Run `grunt` at the terminal and you’ll get some deliciously minified JavaScript.

### Watch

```
$ npm install grunt-contrib-watch --save-dev
```

```
grunt.loadNpmTasks('grunt-contrib-watch');
```

```
watch: {
    scripts: {
        files: ['js/*.js'],
        tasks: ['concat', 'uglify'],
        options: {
            spawn: false,
        },
    } 
}
```

Just run `grunt watch` at the terminal.

### Preprocessing

```
$ npm install grunt-contrib-sass --save-dev
```

```
grunt.loadNpmTasks('grunt-contrib-sass');
```

```
sass: {
    dist: {
        options: {
            style: 'compressed'
        },
        files: {
            'css/build/global.css': 'css/global.scss'
        }
    } 
}
```

Just run `grunt sass` at the terminal.

... or add to `watch`configuration:

```
css: {
    files: ['css/*.scss'],
    tasks: ['sass'],
    options: {
        spawn: false,
    }
}

```

### LiveReload

Go to [link](https://24ways.org/2013/grunt-is-not-weird-and-hard/).

