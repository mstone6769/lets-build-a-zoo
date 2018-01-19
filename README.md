# lets-build-a-zoo
Tutorial on using the Angular CLI to build a Zoo App

See the output here:
[http://github.com/mstone6769/zoo](http://github.com/mstone6769/zoo)

See the built out app:
[https://kind-meninsky-a31df8.netlify.com/](https://kind-meninsky-a31df8.netlify.com/)


`ng new zoo`

`cd zoo`

Open Editor

Let's explore what it created

- tslint.json
- package.json
- e2e tests
- src
 - assets
 - app

`npm start`


styles.css
```css
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  margin: 0;
  background-color: rgb(245, 231, 197);

}
```

`ng g m core -m app.module.ts`

`ng g c core/header -it -m core/core.module.ts`


`ng g m home -m app.module.ts`

`ng g c home/home -it -is -m home/home.module.ts`



`ng g m shared -m app.module.ts`

`ng g c shared/page-header -it -is -m shared/shared.module.ts`

```html
<h1>
  <ng-content></ng-content>
</h1>
```



`ng g m dogs`

`ng g c dogs -is -m dogs/dogs.module.ts`

`import { RouterModule, Routes } from '@angular/router';`





`ng g s dogs/dogs -m dogs/dogs.module.ts`

```typescript
import { Injectable } from '@angular/core';
import { Http } from '@angular/http';
import { Observable } from 'rxjs/Observable';

import 'rxjs/add/operator/map';

@Injectable()
export class DogsService {

  constructor(private http: Http) { }

  getBreeds():Observable<String[]> {
    return this.http.get('https://dog.ceo/api/breeds/list')
      .map(response => response.json().message);
  }

}

```

in dogs.component
```html
  <div *ngFor="let breed of breeds | async">
    {{breed | uppercase}}
  </div>
```






