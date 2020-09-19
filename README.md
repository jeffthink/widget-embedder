# Widget Embedder

Collection of embeds for tools that offer non-url based embeddeding.

## Current Embed Options

* Dropbox - embed grid/list of files

## Getting Started

1. Clone repo
2. Install dependencies: `npm install`
3. Create `.env` file with necessary env variables
4. Start dev server: `npm run dev`

### DropBox

* Set up a Dropbox app (doesn't have to be in production) via `Create new app` [here](https://www.dropbox.com/developers/embedder).
    * Name the app / folder whatever you like.
    * Choose the domains that you'll use this on, e.g. `Notion.so`, `localhost`, `your-hosted-website.com`
    * Take the generated app key, and add it to your `.env` file (see below).
* For any given folder/file you want to embed:
    * From Dropbox UI, "create share link" for that folder/file.
    * Once shared, copy the share link via UI.
    * Once local dev server started, visit `http://localhost:3000/dropbox?share_link={my_share_link_from_last_step}`
* You should see the Dropbox embed take up the full viewport area.
* Deploy your widget-embedder to a non-local website, and visit `{my_web_url}/dropbox?share_link={my_share_link_from_last_step}` as above.
* If you see a problem, it might be that Dropbox's embed uses cookies, so you'll need to unblock any browser plugins and such that might be blocking them.

## Environment Variables

* `DROPBOX_APP_KEY` - App key when creating a Dropbox app ([see here](https://www.dropbox.com/developers/embedder))

# Deploying to Netlify

1. Set up Site in Netlify
2. Set build command: `npm run export` with publish dir: `__sapper__/export`
3. Add env variables (see above) via Netlify UI.

From: https://dev.to/sumitkharche/how-to-deploy-sapper-app-on-netlify-12en
Inspired by: https://blog.shorouk.dev/2020/06/how-to-embed-any-number-of-html-widgets-snippets-into-notion-app-for-free/