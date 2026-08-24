# Studio Aria — deployment and caching notes

## The problem this repo currently addresses

The admin page (`whonknows-xke99.html`) showed different information on a
phone than on a desktop PC.

Two separate causes were identified.

### 1. The Supabase project was paused (root cause of the reported symptom)

Supabase free-tier projects pause automatically after 7 days of inactivity.
While paused the database is offline and every API call the site makes fails.

The admin page did not report this. Instead each device displayed whatever it
still had available locally, so the desktop (with a warm cache from an earlier
working session) and the phone (with an older or empty one) disagreed. The
page looked broken on mobile when in fact the backend was down for both.

Resuming the project restored service. Pausing does not delete data — the
database is snapshotted on pause and restored on resume.

**Still outstanding:** any gift card purchased while the project was paused
was never written to the database, even though the payment processor would
have taken the payment successfully. Those payments need to be reconciled
against the gift card table, and any missing cards issued manually. The
payment processor is the authoritative record for that window, not Supabase.

**Recurrence:** this will happen again after any 7 idle days. Either keep the
project awake with a scheduled request every few days, or move to a paid plan.
For a site that takes payments, a paid plan is the safer choice — a keepalive
ping keeps the project running but gives no warning if it ever stops.

### 2. Page caching (fixed by `_headers`)

Independent of the outage, nothing instructed browsers how long to keep these
pages, so different devices could hold copies from different times. The
`_headers` file in this repo makes every page revalidate against the server,
and makes the admin page uncacheable outright.

## Deploying `_headers`

`_headers` must sit at the root of the folder uploaded to Netlify — the same
folder containing `whonknows-xke99.html`. It has no file extension and needs
no build step.

To verify after deploying:

    curl -sI https://studioaria.net/whonknows-xke99.html | grep -i cache-control

Expected: `no-store, no-cache, must-revalidate, max-age=0`

## Getting the site source into this repo

The site was built with Claude Code, so the source is on the local machine it
was run from — the folder containing `whonknows-xke99.html`. It has never been
pushed here. Until it is, the site exists only as deployed files on Netlify,
with no version history and no backup.

From that folder:

    git init
    git remote add origin https://github.com/tyrelllewisrcc-arch/businessagent
    git fetch origin
    git checkout -b claude/aria-admin-mobile-display-nod7yx origin/claude/aria-admin-mobile-display-nod7yx
    git add .
    git commit -m "Add Studio Aria site source"
    git push -u origin claude/aria-admin-mobile-display-nod7yx

Before committing, check for a `.env` file or anything holding a Stripe secret
key or a Supabase **service_role** key, and add it to `.gitignore` first.
Those must never reach a public repository. The Supabase **anon** key is safe
to commit — it is served to every visitor by design, and Row Level Security,
not secrecy of that key, is what protects the data.

## Open items, once the source is available

- **Fail visibly.** The admin page should show an explicit error when Supabase
  is unreachable, instead of silently rendering whatever it last had. This is
  what disguised a backend outage as a display bug.
- **Confirm the admin page requires a login.** If the only barrier is an
  unguessable URL, anyone who obtains that URL has full access.
- **Review Row Level Security** on the gift card tables. Without correct
  policies the public anon key can read or create gift cards directly,
  regardless of what the admin page's UI allows.
