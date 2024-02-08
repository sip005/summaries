# [Building and deploying Next.js applications with Docker](https://www.youtube.com/watch?v=aNh8iShFXto&t=978s)

### What Next JS offers us -  
1. Static site generation
2. Server-side rendering
3. Incremental static regeneration
4. Works with TypeScript and Saas
5. Code-Splitting and bundling
6. API routes
7. Awesome developer experience

It take react and renders it in the server and sends the html product code to the client, no need for js download(hydration), good for SEO.  

# Steps - 

1. npx create-next-app@latest  .  {14}
    procced with (y)  
    no - for TypeScript  
    yes - for ESlint  
    no - for Tailwind css  
    no - for src directory  
    no - for app router (?)  
    no - for alias  

2. ` npm run dev --host` to view the project  

3. Directory Structure

```shell
.
├── README.md
├── jsconfig.json
├── next.config.mjs
├── node_modules
├── package-lock.json
├── package.json
├── pages
├── public
└── styles

```  

4. One advantage of nextjs is routes are set as files. We will make changes in the /pages/index.js

5. Add a new route vim /pages/docker.js [cat index.js > docker.js]

6. Production build `npm run build`

7. It will create a file `.next`, which will have all the production files

8. `npm start` will server the file that we just built in `.next`  

9. Now we wiil use docker, create a docker file `Dockerfile` in the root  

10. First we will take a base image for docker `nodejs alpine` will be our base image.  

11. Then in Second line we will create a working directory `WORKDIR /app`  

12. We will copy our package.json and package-lock.json to the docker file  

13. then in the docker file we will run the install for the packages  

14. Then we will add our next config js  

15. 

https://dev.to/scaabel/containerizing-a-nextjs-application-for-development-204d

```yaml
FROM node:16-alpine

WORKDIR /app

COPY package.json package-lock.json
RUN npm install

COPY next.config.js ./next.config.js
COPY public ./public
COPY styles ./styles

CMD ["npm", "run", "dev"]
```

```yaml
version: '2'

services:
  app:
    image: dcoker-nextjs-dev-test
    build: .
    ports:
      - 3000:3000
```