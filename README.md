ATRF's committee on Public Transport Research
=============================================

Contact the committee members for information



[![Editing tutorial](https://github.com/atrforum/pt_research_committee/assets/7377666/884c8b30-6f64-4a29-8c4e-7dfb7dd691b4)](https://youtu.be/-8pIQiQ1Ly0)

## Developer notes

### Stack

- **Jekyll 4.x** static site (see [Gemfile](Gemfile)).
- Hosted on **GitHub Pages**, built and deployed by the workflow at [.github/workflows/jekyll.yml](.github/workflows/jekyll.yml) on every push to `main`.
- Custom domain: `ptrc.atrf.link` configured via [CNAME](CNAME).

### Local preview

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000/

### Deployment

A push to `main` triggers [.github/workflows/jekyll.yml](.github/workflows/jekyll.yml), which builds with `JEKYLL_ENV=production` and deploys directly to GitHub Pages. Build status is visible on the repository's **Actions** tab.


