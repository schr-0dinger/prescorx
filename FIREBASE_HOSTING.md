# Kavum Marketing Firebase Hosting

This repo deploys the public marketing/legal site to `https://kavum.in`.

## Firebase setup

Use the existing production Firebase project:

```sh
firebase use presco-f091a
firebase hosting:sites:create presco-f091a-kavum-marketing
firebase target:apply hosting marketing presco-f091a-kavum-marketing
```

The checked-in `.firebaserc` already maps the `marketing` target to the expected
site id. If the site id is changed in Firebase Console, update `.firebaserc`.

## Domains

1. In Firebase Console -> Hosting -> `presco-f091a-kavum-marketing`, add `kavum.in`.
2. Keep GitHub Pages and the current `CNAME` in place until Firebase verifies
   DNS and provisions SSL.
3. After Firebase shows the domain as connected, update DNS to Firebase's
   records and then disable GitHub Pages or remove the GitHub Pages custom
   domain.

## Deploy

Manual live deploy:

```sh
firebase deploy --only hosting:marketing
```

GitHub Actions deploys:

- Pull requests: preview channel for `marketing`.
- `main` or `master` pushes: live channel for `marketing`.

Required GitHub secret:

- `FIREBASE_SERVICE_ACCOUNT_PRESCO_F091A`

## Post-deploy checks

- `https://kavum.in/`
- `https://kavum.in/privacy.html`
- `https://kavum.in/terms.html`
- `https://kavum.in/robots.txt`
- `https://kavum.in/sitemap.xml`
