# React Deployment

Please follow one of the following metbods.

## Vitejs Deployment: Github Pages using the gh-pages CLI tool

Navigate into your project via a CLI tool (ubuntu/ terminal)\
Go through gitflow and save your current code.&#x20;

```
git add
git commit -m 'commit-message'
git push 
```

Next, run the following command:&#x20;

`npm run build`

You can check to see if your build worked by running the command:&#x20;

`npm run preview`

\
You should be able to see your application within your browser at [`http://localhost:4173`](http://localhost:4173/)

After validating that this works, we will install the required packages:\
Run the command: `npm install gh-pages --save-dev`

Now we will setup the package.json:\
Add these scripts into scrips:

```
"predeploy": "npm run build",
"deploy": "gh-pages -d dist",
```

Now we will configure the vite.config.js:\
We need to add a key value pair for gh-pages:

The key will be base, the value should be ‘/name-of-your-repo’\
The configure should look something like:

```
export default defineConfig({
  plugins: [react()],
  base: "/ftbc14_vitejs/",
});
```

Now you should be able to run the command: `npm run deploy`

\#==========================================================#

## Vitejs Deployment: Github Pages through git push

Navigate into your project via a CLI tool (ubuntu/ terminal)

Go through gitflow and save your current code.&#x20;

```
git add
git commit -m 'commit-message'
git push 
```

Run the following command:&#x20;

`git checkout -b gh-pages`

Next, run the following command:&#x20;

`npm run build`

You can check to see if your build worked by running the command:&#x20;

`npm run preview`

\
You should be able to see your application within your browser at [`http://localhost:4173`](http://localhost:4173/)

Now we will configure the vite.config.js:\
We need to add a key value pair for deployment:

The key will be base, the value should be ‘/name-of-your-repo’\
The configure should look something like:

```
export default defineConfig({
  plugins: [react()],
  base: "/ftbc14_vitejs/",
});
```

Within your local machine we need to make a new github workflow within a yml file.

\
Create a new folder named `.github`\
Within the newly created directory create a workflows folder\
In the workflows folder create a new file named: `jekyll-gh-pages.yml`

Paste in this file:

```
# Simple workflow for deploying static content to GitHub Pages
name: Deploy static content to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches: ["gh-pages"]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets the GITHUB_TOKEN permissions to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow one concurrent deployment
concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  # Single deploy job since we're just deploying
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Node.js environment
        uses: actions/setup-node@v4.0.0
        with:
          node-version: lts/*
          cache: 'npm'
      - name: Install dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Setup Pages
        uses: actions/configure-pages@v3
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v2
        with:
          # Upload entire repository
          path: './dist'
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2
```

In your GitHub, repo goto pages and then choose source as GitHub actions, not deploy from branch. Now you should be able to deploy when you push to this branch, before this will work we need to go through git flow (add commit and push)\
Then run the command:&#x20;

`git push origin gh-pages`
