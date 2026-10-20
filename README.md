# Gather — Seasonal Planner

A static, responsive seasonal planner with a Supabase account and cloud-save starter. Deploys directly to Netlify from GitHub; no build command is needed.

## What works in this starter

- Seasonal/event chooser and planner sections: calendar, ideas, recipes, shopping, party/invites, moodboard, budget, decorations, and cards.
- Supabase email/password account creation and sign-in.
- Saves the main planner lists and settings as a per-user JSON document in Supabase, protected by row-level security.
- Netlify-ready static hosting.

## Important current limitations

- Configure Supabase before account creation or cloud sync will work.
- Moodboard uploads are currently browser-side prototype interactions; they are not yet uploaded to Supabase Storage, and imported Instagram recipes are not connected to a server-side extraction service.
- This starter stores planner state as one JSON document. For larger production use, split data into separate tables and store images in Supabase Storage.
- Supabase may require email confirmation depending on your Auth settings. Configure the Site URL and Redirect URLs after you have a Netlify URL.

## 1. Create Supabase project

1. Create a project at https://supabase.com/dashboard.
2. Open **Project Settings → API** (or API Keys) and copy the **Project URL** and **publishable/anon key**. Never use the `service_role` key in browser code.
3. Open `config.js` and replace the two placeholder values with those values.
4. Open **SQL Editor → New query**, paste `supabase/schema.sql`, and run it.
5. In **Authentication → URL Configuration**, set the Site URL to your future Netlify URL and add that URL to Redirect URLs. During local testing, add `http://localhost:8000`.

## 2. Put it on GitHub

1. Create a new empty repository named `gather-seasonal-planner` at https://github.com/new.
2. Upload the contents of this folder (the files inside the folder, not the enclosing zip) to the repository root, or use Git:

```bash
git init
git add .
git commit -m "Initial Gather seasonal planner"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/gather-seasonal-planner.git
git push -u origin main
```

## 3. Deploy on Netlify

1. Sign in at https://app.netlify.com and choose **Add new site → Import an existing project**.
2. Connect GitHub and select `gather-seasonal-planner`.
3. Set the **publish directory** to `.` and leave the build command blank.
4. Deploy. Netlify will give you a public URL.
5. Add that URL to Supabase **Authentication → URL Configuration** as the Site URL and Redirect URL, then redeploy if you changed any files.

## Local preview

Run a local static server from this folder:

```bash
python -m http.server 8000
```

Then open http://localhost:8000. Open `config.js` first if you want to test Supabase sign-in and cloud saving.
