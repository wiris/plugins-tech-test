# Wiris Plugin technical test
---
## First practice: Editor instance
- Follow the [Quick Start Guide](https://ckeditor.com/docs/ckeditor5/latest/framework/guides/quick-start.html) to initialize a CKEditor5 editor instance on the div editable area defined in index.html
- As a result of following the previous guide, you will have an npm module ready to use.
- Upload the resultant npm module to **{user}-editor **branch.
- The editor should be initialized with the instructions below:
    ```
    git clone https://github.com/wiris/plugins-tech-proof -b {user}-editor
    npm install
    webpack --mode development
    ```
## Second practice: Create a plugin
### Create a plugin to fulfill the following user story:
```
- To understand LaTeX code
- As a CKEditor5 user
- I need to be able to transform LaTeX code into human-readable text
```

### Technical overview:
- The plugin name must be LatexAccesible
- The main class of the plugin must extend CKEditor5 [Plugin class](https://ckeditor.com/docs/ckeditor5/latest/api/module_core_plugin-Plugin.html).
- The main class of the plugin must be accessible from CKeditor5 entry point. User the export statement.
- The plugin must open a modal dialog to enter the text.
- CKEditor5 uses an MVC structure. See the [Editing Engine](https://ckeditor.com/docs/ckeditor5/latest/framework/guides/architecture/editing-engine.html) documentation to understand how to insert a text into the editing view.
- To transform LaTeX into human-readable text use the following services:
    - http://www.wiris.net/demo/editor/latex2mathml
    - Transforms LaTeX into MathML
    - Accepts the parameter "latex"
    ```
    www.wiris.net/demo/editor/latex2mathml?latex=\sqrt{2x}
    ```
    - http://www.wiris.net/demo/editor/mathml2accessible
    - Transforms MathML into accessible text
    - Accepts the parameter "mml"
    - Throws a 500 status code if the transformation fails.
    ```
    http://www.wiris.net/demo/editor/mathml2accessible?mml=%3Cmath%20xmlns=%22http://www.w3.org/1998/Math/MathML%22%3E%3Cmsqrt%3E%3Cmn%3E2%3C/mn%3E%3Cmi%3Ex%3C/mi%3E%3C/msqrt%3E%3C/math%3E
    ```
- If the mathml2accessible service fails the inserted text must be "Unable to transform LaTeX into the accessible text".
- As a result of developing the plugin, you will have an npm module ready to use.
- Upload the npm-module plugin to **{user}-plugin** branch.

## Third practice: Add LatexAccessible plugin as a dependency to the editor
- Specify the LatexAccessible package as a dependency into the editor project. Because there is none entry in npmjs database, use the repository and the {user}-plugin branch as the dependency.
- Upload the new package.json to **{user}-editor** branch.
- The plugin and the editor should be initialized following the instructions below:
    ```
    git clone https://github.com/wiris/plugins-tech-proof -b {user}-editor
    npm install
    webpack --mode development
    ```

## Technical considerations
 - Don't use var to declare variables. Use let and const properly.
 - Don't upload node_modules folder.
 - Don't forget to upload de package.json manifest of the npm modules.
 - Fill the package.json fields you consider necessary.
 - Make the code understandable. Comment it.
 - Good commit messages.
 - The code should pass eslint CKEditor5 standards.
 - Use common sense as much as possible.

## Useful documentation
- [CKEditor5 API documentation](https://ckeditor.com/docs/ckeditor5/latest/api/index.html)
- [Quick Start Guide](https://ckeditor.com/docs/ckeditor5/latest/framework/guides/quick-start.html)
- [CKEditor5 quick start guide]()
- [Create a CKEditor5 simple plugin guide](https://ckeditor.com/docs/ckeditor5/latest/framework/guides/creating-simple-plugin.html)
 - [Text service API](http://www.wiris.com/pluginwiris_engine/docs/api/com/wiris/plugin/api/TextService.html)
 - [npm-package.json](https://docs.npmjs.com/files/package.json)
 - [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json)
 - [CKEditor5 ESLint preset](https://www.npmjs.com/package/eslint-config-ckeditor5)
 - [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
