> This repository is for demonstration purposes of how it can be implemented in Angular and is not maintaned. Please fork and maintain your own version of this repository.

# ngx-dropdown

Simple dropdown for your angular2 applications using bootstrap3. Does not depend of jquery.
If you don't want to use it without bootstrap - simply create proper css classes. 
Please star a project if you liked it, or create an issue if you have problems with it.

## Installation

1. Install npm module:
    
    `npm install ngx-dropdown --save`

2. If you are using system.js you may want to add this into `map` and `package` config:
    
    ```json
    {
        "map": {
            "ngx-dropdown": "node_modules/ngx-dropdown"
        },
        "packages": {
            "ngx-dropdown": { "main": "index.js", "defaultExtension": "js" }
        }
    }
    ```

## Usage

```html
<div class="dropdown" dropdown [dropdownToggle]="false" (onOpen)="doSomeActionOnOpen()" (onClose)="doSomeActionOnClose()">
    <button class="btn btn-primary" dropdown-open>My Heroes</button>
    <ul class="dropdown-menu">
        <li><a>Badman</a></li>
        <li><a>Sadman</a></li>
        <li><a>Lieman</a></li>
    </ul>
</div>
```

* `dropdown` directive is used to specify where your dropdown starts
    * `dropdownToggle` Indicates if dropdown should be closed when user double-clicks the dropdown opening button. Default is **true**.
    * `(onOpen)` in dropdown is called when dropdown is opened
    * `(onClose)` in dropdown is called when dropdown is closed
* `dropdown-open` is used on `a`, `button` or any other clickable element to open a dropdown on its click
* `dropdown-not-closable-zone` (not used in the example above, however is used in the examples below) is used
    to prevent closing dropdown when you click on its elements. Its highly usable when you want to create
    interactive dropdowns.

## Sample

```typescript
import {Component} from "@angular/core";
import {DropdownModule} from "ngx-dropdown";

@Component({
    selector: "app",
    template: `
<div class="container">

    <!-- a-style dropdown -->
    <div class="dropdown" dropdown>
        <a dropdown-open>My Heroes</a>
        <ul class="dropdown-menu">
            <li><a href="#">Badman</a></li>
            <li><a href="#">Sadman</a></li>
            <li><a href="#">Lieman</a></li>
        </ul>
    </div>
    <br/>

    <!-- button dropdown -->
    <div class="dropdown" dropdown>
        <button class="btn btn-primary" dropdown-open>My Heroes</button>
        <ul class="dropdown-menu">
            <li><a href="#">Badman</a></li>
            <li><a href="#">Sadman</a></li>
            <li><a href="#">Lieman</a></li>
        </ul>
    </div>
    <br/>

    <!-- dropdown with items that are not closing dropdown when you click on them -->
    <div class="dropdown" dropdown>
        <button class="btn btn-primary" dropdown-open>Not closable on items click</button>
        <ul class="dropdown-menu" dropdown-not-closable-zone>
            <li><a href="#">This dropdown will</a></li>
            <li><a href="#">not be closed when you</a></li>
            <li><a href="#">select any its items</a></li>
            <li><a href="#">this allows you to put</a></li>
            <li><a href="#">dynamic content into it</a></li>
        </ul>
    </div>

</div>
`
})
export class AppComponent {

}

@NgModule({
    imports: [
        BrowserModule,
        DropdownModule
    ],
    declarations: [
        AppComponent
    ],
    bootstrap: [
        AppComponent
    ]
})
export class AppModule {

}

platformBrowserDynamic().bootstrapModule(AppModule);
```

Take a look on samples in [./sample](https://github.com/pleerock/ngx-dropdown/tree/master/sample) for more examples of
usages.
