# [NextJS Tutorial - All 12 Concepts You Need to Know](https://youtu.be/vwSlYG7hFk0?si=2rGH360RpN_ZI4Yq)  

### Steps  

1. Creating project  

```sh

npx create-next-app@latest  .
    procced with (y)  
    yes - for TypeScript  
    yes - for ESlint  
    yes - for Tailwind css  
    yes/? - for src directory  
    yes - for app router (?)  
    no - for alias  
```  

2. `npm run dev`  

3. list of Topics

```md
1. Routing and navigaion 
2. Metadata
3. styling (Tailwind CSS)
4. `<Image/>`
5. Client vs Server components 
    - data fetching (Get-requets)
6. Server actions (POST/PUT/DELETE)
7. Suspence and streaming
8. Caching
9. static and dynamic rendering
10. Middlewares
11. Production build and deploying
12.
```

4. index page source code dir of the page is `src/app/page.tsx`. delete all the boiler plate code, just keep the home function that will return the main section  

5. Clear the global css, Keep the tailwind import  

6. In the `src/app` directory we will detetmine all the routes of our application, `page.tsx` is our home page and create a folder for our `posts`, inside the posts our posts will be stored. 