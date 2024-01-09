# Vue Portfolio - Static Site

This repository represents the transition of my portfolio website from a server-dependent Node.js implementation to a static website built using Vue.js and Nuxt.js.

## Overview

This Vue Portfolio repository signifies the migration of my portfolio website to a static site architecture. Previously relying on server-side operations using Node.js, this version employs Vue.js and Nuxt.js to transform the website into a static web application. This transition eliminates the need for a continuous server operation, enhancing performance and simplifying deployment.

### Key Features:

- **Static Site:** Migration from Node.js to Vue.js and Nuxt.js, enabling a static site setup for improved efficiency.
- **Retained Functionality:** Ensures the preservation of existing features, layout, and user experience from the original Node.js-based portfolio website.
- **Simplified Deployment:** Facilitates easy deployment and hosting due to the static nature of the website, eliminating the necessity for server runtime.
- **Enhanced Performance:** Optimized for faster load times and improved user interaction without relying on server-side rendering.
- **Api Integration:** Automatic content population through my [API](https://github.com/Justin0122/GitHub_API_NodeJS). This integration ensures a dynamic display of my projects and enables easy content management.

## Getting Started

### Prerequisites

Ensure you have Node.js installed on your system. If not, you can download it [here](https://nodejs.org/en/download/).

### Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/Justin0122/portfolio-vue
   cd portfolio-vue
    ```
2. **Install Dependencies:**
   ```bash
    npm install
   ```

## Usage

1. **Run the Development Server:**
   ```bash
    npm run dev
    ```
   This command will start the development server. Open your browser and visit `http://localhost:3000` to view the website locally.

2. **Build for Production:**
   ```bash
    npm run build
    ```
   Use this command to generate the production-ready build of the website.

<small>View package.json for more details regarding the available scripts.</small>


### Customize

Feel free to modify the existing pages, components, and styles to tailor the website to your preferences. Utilize Vue.js and Nuxt.js functionalities to expand features or enhance user interaction as needed.

## Built With

* [Vue.js](https://vuejs.org/) - JavaScript Framework
* [Nuxt.js](https://nuxtjs.org/) - Vue Framework for SSR and Static Sites

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

