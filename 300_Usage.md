# Usage

## Basic Usage

Once configured, the plugin will compare the file modified dates of a `.less` file and it's companion `.css`.  The less file is compiled if the css is newer.  

Basic Examples:
````
/templates/{$template}/less/template.less 
compiles into 
/templates/{$template}/css/template.css

/templates/{$template}/css/editor.less 
compiles into 
/templates/{$template}/css/editor.css
````

When a `.less` file is located within a folder named `less`, then the compiler will look for and place generated `.css` files into a companion `css` folder.

## Ignoring Files

The less compiler will ignore files starting with an underscore like `_variables.less`

## File Inheritance / Dependecies

To save processor time the less compiler does not read less files for dependencies.  To instruct the processor of LESS dependences the `.lessrc` instruction files are used.  A `.lessrc` file can be a single file defining rules for the entire folder, or a separate file to accompany each less file in the folder.

In the following example, the `template.less` file depends on `_variables.less`, and the `template.lessrc` file is used to define that dependency.

````
templates/example/less/_variables.less

    @fontColor: black;

templates/example/less/template.less

    @import "_variables.less";
    body {
      color: @fontColor;
    }

templates/example/less/template.lessrc

    {
      "import": [
        "_variables.less"
      ]
    }
````    

Alternatively each folder may contain a single `.lessrc` file that defines rules for the entire folder.  In rules for an entire folder the `*` wildcard can be used to specify that all files depend on another.  

In this example we see that all files in the folder depend on `_variables.less`, while `editor.less` also depends on `../system/less/_variables.less`.

````
templates/example/less/.lessrc

    {
      "files": [
        {
          "file": "*",
      },
        {
          "file": "editor.less",
          "import": "../system/less/_variables.less"
      },
      ],
      "import": [
        "_variables.less"
      ]
    }

````
