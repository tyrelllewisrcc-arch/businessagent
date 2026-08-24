# Income & expense tracker

`tracker.html` — a single file. Open it in a browser and it works. No install,
no build step, no server, no account.

## Opening it

Double-click the file, or drag it into a browser window. Bookmark the tab so
you can get back to it.

**It is not part of the website and should not be uploaded to Netlify.** It
carries a `noindex` tag as a safety net in case it ever is, but the intended
home for this file is your own machine.

## What it does

- Record income and expenses: date, amount, category, payment method, note
- Totals for this month, last month, this quarter, this year, or any custom range
- A month-by-month bar chart of money in against money out
- A breakdown showing which categories your money actually goes to
- Search and filter, edit or delete anything, undo a deletion
- Export to CSV for a spreadsheet or an accountant
- Import a CSV — including a bank export, which usually just needs a date
  column and an amount column

Set your business name by clicking the title. Categories, payment methods and
currency are all editable under **Settings**.

## Where the data lives, and what that means

Everything is stored in this browser, on this device, using its local storage.
Nothing is transmitted anywhere. There is no database to go down and no key
that could leak your figures.

The consequences of that are worth being clear about:

- **Data does not sync.** What you enter on a laptop will not appear on a phone.
- **Clearing browsing data deletes it.** So can "clear cookies and site data",
  some privacy extensions, and private browsing windows.
- **A different browser is a different set of books.** Chrome and Safari on the
  same machine do not share storage.

So: **export a backup regularly.** Settings → Download backup gives you a JSON
file that restores everything exactly. CSV is the better format to hand to
someone else. Either one, kept somewhere that is itself backed up, is what
stands between you and a lost year of records.

## If you outgrow it

The point at which this file stops being enough is usually when you want the
same figures on more than one device. That means a database behind it —
at which point the questions are who can read the data, what happens when the
database is unavailable, and who is backing it up. All three are worth settling
before moving the data, not after.
