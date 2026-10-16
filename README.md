ATRF Public Transport Research Committee (ATRF-PTRC)
===================================================

Source for the website of the Public Transport Research Committee, a standing group of the
[Australasian Transport Research Forum (ATRF)](https://australasiantransportresearchforum.org.au/).

[![Editing tutorial](https://github.com/atrforum/pt_research_committee/assets/7377666/884c8b30-6f64-4a29-8c4e-7dfb7dd691b4)](https://youtu.be/-8pIQiQ1Ly0)


## Developer notes

### Stack

- **Jekyll 4.x** static site (see [Gemfile](Gemfile)).
- **[Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes)** theme, pinned to `4.26.2` and pulled in via `jekyll-remote-theme` rather than vendored — see `remote_theme:` in [_config.yml](_config.yml). The theme's source files are *not* in this repo; only the overrides we need.
- Hosted on **GitHub Pages**, built and deployed by the workflow at [.github/workflows/jekyll.yml](.github/workflows/jekyll.yml) on every push to `main`. There's no GitHub Pages branch — the action builds with full Jekyll (so plugins like `jekyll-remote-theme` work) and uploads the `_site/` artifact directly.

### Repo layout

| Path | What's there |
| --- | --- |
| [_config.yml](_config.yml) | Site-wide settings: title, baseurl, theme, plugins, footer/social links, Sass config. |
| [_data/](_data/) | Structured content driving the page sections — `people.yml`, `leadership.yml`, `events.yml`, `resources.yml`, `research_needs.yml`, `navigation.yml`. Editing these is the day-to-day way the site changes. |
| [index.md](index.md) | The single landing page. Front matter sets the splash hero; the body just `{% include %}`s the section partials in display order. |
| [_includes/sections/](_includes/sections/) | One HTML partial per page section (`about`, `research-needs`, `resources`, `events`, `team`). These are local — they're not part of Minimal Mistakes. |
| [_includes/masthead.html](_includes/masthead.html), [_includes/head/custom.html](_includes/head/custom.html) | **Local overrides** of theme partials. The masthead override exists for the dual-logo layout; `head/custom.html` is MM's extension point for favicons/meta tags. |
| [assets/css/main.scss](assets/css/main.scss) | The site's compiled stylesheet. Imports the theme's skin and base styles, then layers brand-colour and component overrides on top. |
| [img/team/](img/team/) | Headshot JPGs. Filenames must match the `pic:` field in `_data/people.yml` / `_data/leadership.yml` (without the extension). `placeholder.jpg` is the default. |
| [assets/](assets/) | Presentation slides (PDFs / ZIPs) referenced from past-event entries in `_data/events.yml`. |

### Local preview

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000/

### Deployment

A push to `main` triggers [.github/workflows/jekyll.yml](.github/workflows/jekyll.yml), which builds with `JEKYLL_ENV=production` and deploys to GitHub Pages. Build status is visible on the repo's **Actions** tab.
