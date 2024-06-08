If you want to use SCSS in GitHub Pages without Jekyll, you can use a workflow that involves precompiling your SCSS into CSS before deploying your site. Here's a step-by-step guide:

### Step 1: Set Up Your Project

1. **Create a new repository on GitHub**:
   - Go to GitHub, click on the "+" sign, and select "New repository."
   - Name your repository (e.g., `my-github-pages-site`).

2. **Clone the repository to your local machine**:
   ```sh
   git clone https://github.com/your-username/my-github-pages-site.git
   cd my-github-pages-site
   ```

### Step 2: Set Up Node.js and npm

1. **Install Node.js**:
   - Download and install Node.js from the [official website](https://nodejs.org/).

2. **Initialize npm in your project**:
   ```sh
   npm init -y
   ```

### Step 3: Install SCSS Compiler

1. **Install `sass` (Dart Sass)**:
   ```sh
   npm install sass --save-dev
   ```

### Step 4: Set Up Your Project Structure

1. **Create the necessary directories**:
   ```sh
   mkdir src
   mkdir src/scss
   mkdir dist
   ```

2. **Create your SCSS file**:
   - Create a file named `styles.scss` inside `src/scss/`.

3. **Create your HTML file**:
   - Create an `index.html` file in the root of your project.

### Step 5: Configure SCSS Compilation

1. **Create a script to compile SCSS**:
   - Open your `package.json` file and add the following script:
     ```json
     "scripts": {
       "build:css": "sass src/scss/styles.scss dist/styles.css"
     }
     ```

2. **Compile your SCSS**:
   ```sh
   npm run build:css
   ```

### Step 6: Link Compiled CSS in HTML

1. **Update `index.html` to link the compiled CSS**:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>My GitHub Pages Site</title>
     <link rel="stylesheet" href="dist/styles.css">
   </head>
   <body>
     <h1>Hello, World!</h1>
   </body>
   </html>
   ```

### Step 7: Automate the Build Process

You can use a build tool like `npm scripts` or `Gulp` to automate the build process. Here's an example using `npm scripts`:

1. **Install `concurrently` and `watch`**:
   ```sh
   npm install concurrently watch --save-dev
   ```

2. **Update `package.json` to automate the build process**:
   ```json
   "scripts": {
     "build:css": "sass src/scss/styles.scss dist/styles.css",
     "watch:css": "watch 'npm run build:css' src/scss",
     "start": "concurrently \"npm run watch:css\""
   }
   ```

### Step 8: Deploy to GitHub Pages

1. **Create a `.gitignore` file** to exclude `node_modules`:
   ```sh
   echo "node_modules" >> .gitignore
   ```

2. **Commit your changes**:
   ```sh
   git add .
   git commit -m "Initial commit with SCSS setup"
   ```

3. **Push to GitHub**:
   ```sh
   git push origin main
   ```

4. **Enable GitHub Pages**:
   - Go to your repository on GitHub.
   - Click on "Settings."
   - Scroll down to "GitHub Pages."
   - Select the branch you want to deploy from (`main` or `gh-pages`).

### Additional Tips

- To add more SCSS files, simply create them in the `src/scss` directory and import them in your `styles.scss` file.
- You can customize your site further by adding more HTML, CSS, and JavaScript files as needed.

By following these steps, you can set up a GitHub Pages site that uses SCSS without relying on Jekyll. This approach involves precompiling your SCSS into CSS locally and then deploying the compiled CSS to GitHub Pages.