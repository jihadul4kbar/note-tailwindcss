# Cara Install Tailwind CSS pada CodeIngiter 4
## Install CodeIgniter
https://codeigniter.com/user_guide/installation/installing_composer.html
1. composer create-project codeigniter4/appstarter --no-dev 
## Install Laravel Mix
* note : Versi Nodejs harus v12.14 atau lebih tinggi
https://laravel-mix.com/docs/6.0/installation 
1. npm init -y  
2. npm install laravel-mix --save-dev 
3. touch webpack.mix.js / buat file secara manual pada directori codeigniter
* //touch webpack.mix.js
* let mix = require('laravel-mix');
* mix.js('src/app.js', 'public/js');

pada direktori codeigniter buat folder 

* --src
*  --css
*    -- app.css
*  --js
*    -- app.js
4. npx mix
## Install TailwindCss
https://tailwindcss.com/docs/guides/laravel
1. npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
2. npx tailwindcss init
* // tailwind.config.js
*  module.exports = {
*   purge: [],
*   purge: [
*     './App/Views/*.php',
*     './App/Views/**/*.php',
*     './App/Views/**/**/*.php',
*     './App/Views/**/**/**/*.php',
*   ],
*    darkMode: false, // or 'media' or 'class'
*    theme: {
*      extend: {},
*    },
*    variants: {
*      extend: {},
*    },
*    plugins: [],
*  }
  
4. tambah data pada baris kode webpack.mix.js
* // webpack.mix.js
*  mix.js("src/js/app.js", "public/js")
*    .postCss("src/css/app.css", "public/css", [
*     require("tailwindcss"),
*    ]);
    
5. load css 
* /* ./src/css/app.css */
* @tailwind base;
* @tailwind components;
* @tailwind utilities; 

6. npx mix
7. load css pada halaman html 
<!doctype html>
  <head>
    <!-- ... --->
   <meta charset="UTF-8" />
   <meta name="viewport" content="width=device-width, initial-scale=1.0" />
   <link href="/css/app.css" rel="stylesheet">
  </head>
  <body>
    <div class="min-h-screen bg-gray-100 flax justify-center items-center">
      <h1 clss="text-4x1 font-medium"> Selamat Belajar Tailwind CSS </h1>
    </div>
  </body>
  <!-- ... --->
