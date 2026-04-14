# My Daily Link — PWA

A personalized daily link PWA with push notifications at 9:00 AM.

## Files
- `index.html` — the member-facing PWA (what members see)
- `admin.html` — your admin dashboard to manage members & links
- `sw.js` — service worker (handles offline + push notifications)
- `manifest.json` — PWA manifest (makes it installable)
- `icons/` — add icon-192.png and icon-512.png here

## Deploy in 3 steps (free)

### 1. Add icons
Add two square PNG icons to the `icons/` folder:
- `icon-192.png` (192×192px)
- `icon-512.png` (512×512px)

### 2. Deploy to Netlify
1. Go to netlify.com → sign up free
2. Drag and drop this entire folder onto the Netlify dashboard
3. Your site goes live instantly at a URL like `https://your-app.netlify.app`

### 3. Use the admin dashboard
1. Open `https://your-app.netlify.app/admin.html`
2. Add a member name + their link
3. Copy their unique PWA URL
4. Send them that URL once (via Spruce or any method)

## How member links work
Each member gets a unique URL like:
`https://your-app.netlify.app/?member=123&link=https://their-link.com`

When you update their link in the admin panel, generate a new URL and send it once.
For truly dynamic links (update without resending the URL), you'd need a backend like Supabase — ask Claude to set that up.

## Notifications
- **Android**: Full automatic push notification prompt at first visit
- **iPhone**: User must add to home screen first (Safari → Share → Add to Home Screen), then notifications work
- Notifications fire daily at **9:00 AM** in the user's local timezone
- Message: "Your daily link is here"

## Changing notification time or message
Edit `index.html` and find:
```js
next.setHours(9, 0, 0, 0); // change 9 to your desired hour (24hr format)
```
And:
```js
body: 'Your daily link is here', // change the notification message here
```
