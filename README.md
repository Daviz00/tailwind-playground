# tailwind-playground

Instructions to get up and running:

1. npm init -y

2. npm install tailwindcss postcss autoprefixer postcss-cli cssnano onchange

3. npx tailwindcss init -p

4. Go and add this to the *purge* section under tailwind.config.js

   purge: {
    mode: 'layers',
    content: ['./public/**/*.html/'],
  },

5. Go and change the postcss.config.js file contents to

  const cssnano = require('cssnano');
  module.exports = {
    plugins: [
     require('tailwindcss'),
     cssnano({
      preset: 'default',
     }),
     require('autoprefixer'),
  ]
};

6. mkdir src

7. mkdir src/css

8. touch src/css/tailwind.css

9. Now add the following to the tailwind.css file under src/css


  @tailwind base;
  @tailwind components;
  @tailwind utilities;

10. Now go to the package.json file and under scripts tab, remove eveything and add the following

  "tw:build": "tailwindcss build ./src/css/tailwind.css -o ./public/css/tailwind.css"


11. npm run tw:build

12. Now add the follwing under tw:build

  "tw:watch": "onchange 'tailwind.config.js' 'src/\**/\*.css' -- npm run tw:build"

13. npm run tw:watch

14. touch public/index.html

15. link css/tailwind.css in the index.html file head
