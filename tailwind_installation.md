# Install Postcss and plugins

    npm install –save-dev postcss postcss-cli

    npm install –save-dev cssnano

    npm install –save-dev autoprefixer

    npm install –save-dev tailwindcss

# Create a postcss.config.js file

    // postcss.config.js 
        
    module.exports = {
      plugins: [
	    require('tailwindcss'),
	    require('autoprefixer'),
	    require('cssnano')({
	    preset:  'default',
	    }),
      ],
    };

# Create a tailwind.config.js file

  On this config file you can change how tailwindss is compiled. Such
   as purge etc.
   [https://tailwindcss.com/docs/plugins](https://tailwindcss.com/docs/plugins)

Run the following to create a tailwind.config.js file

    npx tailwind init

Inside Content, define all the locations you want purge to analyses which classes are in use.

    //tailwind.config.js
   
    module.exports = {
      purge: {
        enabled: true,
        content: [&#39;./html/\*.dot.html&#39;],
      },
      //...
    };

# Create a tailwind.config.js file 

  On this config file you can change how tailwindss is compiled. Such as purge etc. https://tailwindcss.com/docs/plugins 

Run the following to  create a tailwind.config.js file

    npx tailwind init

Inside Content, define all the locations you want purge to analyses which classes are in use. 

    //tailwind.config.js
    module.exports = {
      purge: {
        enabled: true,
        content: ['./html/*.dot.html'],
      },
      // ...
    };

# Generate default tailwindcss 
### (no tailwind.config.js needed)

Run this code to generate a default version of Tailwindcss. Avg = 3.2 MB

    npx tailwindcss -o tailwind.css

# Include @tailwind or @imports to your main css file.
Use the @layer and @appy classes to modify tailwind to your liking. 

    //input.css
    @tailwind base;
    @tailwind components;
    @tailwind utilities;

    @layer components {
      .btn {
        @apply px-4 py-2 bg-blue-600 text-white rounded;
      }
    }
    @layer utilities {
      .scroll-snap-none {
        scroll-snap-type: none;
      }
      .scroll-snap-x {
        scroll-snap-type: x;
      }
      .scroll-snap-y {
        scroll-snap-type: y;
      }
    }

# Generate Custom Tailwind.css 
    npx postcss input.css > tailwind.css
Make sure you @import the final tailwind.css file after running the script

    //votestyles.css
    @import url('tailwind.css'); <-- here
    @import url('fontawesome.min.css');
    @import url('../styles/animate/animate.min.css');
# Create a script to automate before production

For convenience lets generate some scripts to run evetime before zipping for production. 

    "scripts": {
      "tailwind": "npx tailwindcss -o tailwind.css",
      "build:css": "npx postcss styles/janssen.css > styles/tailwind.css"
    },

Then we will just need to run the following script to generate our custom tailwindcss with Postcss:

    npm run build:css

 

