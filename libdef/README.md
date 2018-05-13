# ng2-mousewheel

An Angular directive for cross-browser mousewheel support by making use of the hamster.js library.

It is built using Angular CLI 6 library support, so it may not work on Angular versions 2 through 5 (please excuse the 'ng2' moniker).

## Installation

`npm install ng2-mousewheel --save`

### angular.json:
```json
"projects": {
    "my-angular-app": {
      "architect": {
        "build": {
          "options": {
            "scripts": [
              "node_modules/@kensingtontech/hamsterjs/hamster.js"
            ]
            ...
```

### app.module.ts:
```typescript
import { Ng2MousewheelModule } from 'ng2-mousewheel';

@NgModule({
  imports: [ Ng2MousewheelModule ],
  ...
})

export class MyAppModule { }
```

## Usage

This library exposes a directive called 'kwheel', which will emit a normalised mousewheel event.  The event handler is run outside of the Angular zone, so a kwheel event will not trigger change detection.

```typescript
@Component({
  selector: 'my-component'
  template: `<div (kwheel)="onMouseWheel($event)"></div>`
})


export class MyComponent {

  public onMouseWheel(event): void {
    // your wheel handler goes here
  }

}
```

Please note that this implementation uses passive event listeners.  If you need support for traditional listeners, do let me know.

## Reference

[Hamster.js Github page](https://github.com/monospaced/hamster.js)