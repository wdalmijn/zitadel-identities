# zitadel-identities

`.well-known` files per domain, so each domain can point to its Zitadel issuer.

```
domains/
└── <domain>/
    └── .well-known/
        └── webfinger
```

Each `domains/<domain>/` folder is served as the web root of that domain, so
`domains/superbusy.work/.well-known/webfinger` must be reachable at
`https://superbusy.work/.well-known/webfinger`.

## WebFinger (Tailscale custom OIDC)

- `subject` is `acct:` plus the email you sign up to Tailscale with.
- The `href` must exactly match the `issuer` in your Zitadel
  `/.well-known/openid-configuration`.
- Serve it with `Content-Type: application/jrd+json` and over HTTPS.
- Check it with the lookup tool at https://webfinger.net before setting up Tailscale.

To add a domain, copy `domains/superbusy.work` to `domains/<new-domain>` and edit the values.
