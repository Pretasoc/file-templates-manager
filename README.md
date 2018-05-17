# File Templates Manager for VSCode

This extension allows to manage your file templates and create files from them.

![Explorer][explorer]

## Features

File Template Manager is powerful extension with following features that improve your productivity and do routine work for you.

### Manage file template

![Template Picker][template-picker]

### Interactive integrated template engine

* `{{ }}` - evaluation
* `{{= }}` - interpolation
* `{{! }}` - interpolation with encoding
* `{{# }}` - compile-time evaluation/includes and partials
* `{{## #}}` - compile-time defines
* `{{? }}` - conditionals
* `{{~ }}` - array iteration

---

Evaluation and interpolation example for `HTML` file

```html
{{ for(let i = 0; i < 10; i++ ) }}
<div>Item {{=i}}</div>
```

result is

```html
<div>Item 0</div>
<div>Item 1</div>
<div>Item 2</div>
<div>Item 3</div>
<div>Item 4</div>
<div>Item 5</div>
<div>Item 6</div>
<div>Item 7</div>
<div>Item 8</div>
<div>Item 9</div>
```

---

Select prompt example for `C#` language file

```cs
using System;

{{#def.select('TYPE', 'Select file type', ['class','interface','struct','enum'])}}
/*
  {{=$.NAME}} {{=$.TYPE}}
 */
public {{=$.TYPE}} {{=$.NAME}}
{

}
```

you will see a prompt

![Select value][type-selector]

and get result for `class` type

```cs
using System;

/*
  CSharp class 
 */
public class CSharp {
  
}
```

---

`tsconfig.json` example file

```json
{{#def.select('MODULE', 'Specify module code generation', ['none','commonjs','amd','system','umd','es6','es2015','esnext'])}}
{{#def.select('TARGET', 'Specify ECMAScript target version', ['es3','es6','es2016','es2017','esnext'])}}
{{#def.confirm('SOURCE_MAP', 'Should generate corresponding .map file?')}}
{
  "compilerOptions": {
      "module": "{{=$.MODULE}}",
      "target": "{{=$.TARGET}}",
      "sourceMap": {{=$.SOURCE_MAP}}
  },
  "exclude": [
      "node_modules"
  ]
}
```

## Extension Settings

This extension contributes the following settings:

* `templates.showExplorer`: enable/disable explorer
* `templates.customVars`: define custom variables

### 0.1.0

Initial release of Code Templates

[logo]: docs/Logo128.png 'File Templates Manager'
[explorer]: docs/explorer.png 'File Templates Manager Explorer'
[template-picker]: docs/template-picker.png 'File Templates Manager Picker'
[type-selector]: docs/select-type.png 'File Templates Manager Selector'