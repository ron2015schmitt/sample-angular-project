# Sample Angular Project

Tools / packages

- [Angular CLI](https://github.com/angular/angular-cli) 16.2.5
- ng integrated vite / esbuild for `build` and `serve`
- nvm
- nodejs 18.18
- npm 10.2
- pnpm 8.8
- jest 29.7
- TypeScript 5.1


## install

```bash
nvm install 18.18
nvm use 18.18
npm i -g npm@10.2
npm i -g pnpm@8.8

git clone https://github.com/ron2015schmitt/sample-angular-project.git
cd sample-angular-project
pnpm install
```


## How this repo was created

### Compatibility Guides

- [Official Angular Compatibility Guide](https://angular.io/guide/versions)
- [Unofficial Angular Compatibility Guide]((https://gist.github.com/LayZeeDK/c822cc812f75bb07b7c55d07ba2719b3)


### Set up package managers: nvm, npm, pnpm

```bash
nvm install 18.18
nvm use 18.18
npm i -g npm@10.2
npm i -g pnpm@8.8
```

### Set up Angular 

The current version of the global Angular CLI determines the version of Angular to be used.  

```bash
npm install -g @angular/cli@16.25
```

### Create Angular scaffolding 

```bash
ng new sample-angular-project --minimal --skip-tests --skip-git --package-manager=pnpm
cd sample-angular-project
```

### Add TypeScript

```bash
pnpm add typescript@5.1
```

### Using integrated vite / esbuild in Angular 16

![Vite + esbuild](vite_esbuild.png)

>In ng serve we’re now using Vite for the development server, and esbuild powers both your development and production builds!
>
>We want to emphasize that Angular CLI relies on Vite exclusively as a development server. To support selector matching, the Angular compiler needs to maintain a dependency graph between your components which requires a different compilation model than Vite.

https://blog.angular.io/angular-v16-is-here-4d7a28ec680d


#### Using vite during `ng build`

In your project `angular.json`, add `-esbuild` to the following line

![Alt text](image-3.png)


#### Using vite during `ng serve`

Then (also in `angular.json`) add the text
```json
          "options": {
            "forceEsbuild": true
          },
```

in the following location

![Alt text](image-2.png)


## Jest support in Angular 16

Install jest

```bash
npm install jest --save-dev
```

Add the following to your `angular.json` in the `"architect"` section
```json
        "test": {
          "builder": "@angular-devkit/build-angular:jest",
          "options": {
            "tsConfig": "tsconfig.spec.json",
            "polyfills": ["zone.js", "zone.js/testing"]
          }
        }
```

