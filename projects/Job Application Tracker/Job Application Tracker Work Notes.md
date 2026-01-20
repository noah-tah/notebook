# 9:03 PM 1/19/2026
- Moved our work notes from notepad over to Obsidian, syncing across windows and Linux.
- Next is to finish the front end of the Job Application Tracker

# 10:07 PM 1/19/2026
- Began displaying the date different potentially based on the brower's time zone, requires a helper function to do so
- Following is an example code snippet of how to do so:
```ts
const formatDateOnly = (value: string | null | undefined) => {
  if (!value) return '—';
  const d = new Date(value);
  if (Number.isNaN(d.getTime())) return value; // fallback if parsing fails

  return new Intl.DateTimeFormat(undefined, {
    year: 'numeric',
    month: 'short',
    day: '2-digit',
  }).format(d);
};
```

# 8:42 AM 1/20/2026
```js
const date = Intl.DateTimeFormat(undefined, {
	year: 'numeric',
	month: 'short',
	day: '2-digit',
}).format(d);
```
- `Intl` is a JavaScript helper object that stands for Internalization.
- Here we are using it as a way to help make sure our date and time is in a proper format depending on the user's browser
	- "Lets you format things in a way that matches user's locale conventions"
```js
Intl.DateTimeFormat(locales, options)
```
- Takes a locales argument