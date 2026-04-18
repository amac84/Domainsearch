# Vercel domain and deploy setup

This project is configured to use the **Vercel MCP server** in Cursor so you can add domains and deploy from the IDE.

## 1. Enable the Vercel MCP server

- The project has **`.cursor/mcp.json`** with the Vercel server (`https://mcp.vercel.com`).
- **Restart Cursor** (fully quit and reopen) so it picks up the new MCP server.
- On first use, the Vercel MCP will prompt for **OAuth**; sign in with your Vercel account.

If you use **global MCP settings** instead of project-level, add this in **Settings → Tools & MCP → Add new MCP server**:

- **Name:** `vercel`
- **Type:** `streamableHttp`
- **URL:** `https://mcp.vercel.com`

## 2. Create the Vercel project (if needed)

- In Cursor, ask the agent to **create a new Vercel project** or **link this repo** to Vercel (using the Vercel MCP tools after the server is connected).
- Or in the [Vercel dashboard](https://vercel.com/dashboard): **Add New → Project**, import the `Domainsearch` repo, set **Root Directory** to `domainsearch-app`, then deploy.

## 3. Add a custom domain (using the plugin)

Once the Vercel MCP server is connected and you’ve signed in:

- In the chat, ask: **“Add the domain [your-domain.com] to the domainsearch project in Vercel.”**
- The agent will use the Vercel MCP tools to add the domain and show you the required DNS records (e.g. A/CNAME) to add at your registrar.

## 4. Deploy

- **Via plugin:** Ask: **“Deploy the domainsearch-app to Vercel production.”**
- **Via CLI:** From the repo root:
  ```bash
  cd domainsearch-app
  npx vercel --prod
  ```
  Or from root with Vercel linked to `domainsearch-app`:
  ```bash
  npx vercel --prod --cwd domainsearch-app
  ```

## 5. Root directory for this repo

The app lives in **`domainsearch-app/`**. In Vercel:

- Either set **Root Directory** to **`domainsearch-app`** for the project, or  
- Run `vercel` from inside `domainsearch-app` so the project root there is used.

`domainsearch-app/vercel.json` is set up for Next.js; no extra config is required for a standard deploy.

## 6. Environment variables

Add any env vars (e.g. from `domainsearch-app/.env`) in the Vercel project:

- **Dashboard:** Project → Settings → Environment Variables  
- **Or** ask the agent: **“Add environment variable X for the domainsearch project in Vercel.”** (when using the Vercel MCP)

---

**Summary:** Restart Cursor → sign in to Vercel MCP when prompted → then use the plugin (or CLI) to add your domain and deploy.
