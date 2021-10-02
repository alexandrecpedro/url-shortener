
- initial setup
    - ran npm init
    - ran npm install typescript
    - setup mongodb on atlas
    - added tsconfig.json
    - added tslint.json
    - wrote on package.json
        - script 
            - "build:watch": "tsc -w",
            - "dev": "nodemon ./dist/index.js",
    - wrote .gitignore
        - node_modules/  
<br>


- created index.ts
    - created ./src/index.ts
    - ran npm run dev
        -failed
    - fixed package.json
        - "dev": "npx nodemon -w dist dist/index.js"
    - ran npm run dev
        - succeeded
        - change to test reload
        - reloaded
    - updated .gitignore
        - dist/
<br>

- creating test endpoint
    - import express, {Request, Response} from 'express' 
    - GET /test
        - ok
<br>

- make shortUrl
    - added dependency
        - npm i --save shortid @types/shortid
    - created controller/UrlController.ts
        -  public async shorten
    - created config/Constants.ts
    - created POST /shorten on index.ts
        - handler urlController.shorten
<br>

- made redirect method
    - created UrlController.redirect()
        - mocked return for testing
    - updated index.ts 
        - GET /:hash
            - redirects to link with hash
<br>

- connect to mongo
    - add dependency mongoose
        - npm install mongoose --save
    - created database/MonogoConnection.ts
    - updated index.ts
<br>

- persist data
    - add dependency
        - npm install @hasezoey/typegoose
    - created model/Url.ts
    - updated UrlController.shorten
    - tested POST from postman
        - data persisted on mongo 
<br>

- redirect from database
    - updated UrlController.redirect
    - tested GET with hash of data persisted previously
        - redirects to page saved before
    - tested GET with innexistent hash
        - returns not found
<br>