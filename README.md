# Fieldbook website

This is the public website for **Fieldbook**, an iPad app that electrical contractors' field crews use to fill in work orders on the job and send them to the office. It has two pages:

- `index.html` is the homepage. It explains the app, and its Support section (`#support`) is the App Store Support URL.
- `privacy.html` is the privacy policy. Its URL goes into App Store Connect as the Privacy Policy URL.

The site is plain HTML and CSS, written by hand. There's no build step, package manager, framework or JavaScript. To preview it, open `index.html` in a browser.

| File | What it is |
| --- | --- |
| `index.html` | Homepage |
| `privacy.html` | Privacy policy |
| `404.html` | "Page not found" page, which GitHub Pages shows for missing addresses |
| `style.css` | One stylesheet shared by every page, with light and dark mode |
| `.nojekyll` | Empty file that tells GitHub Pages to serve the files exactly as they are |
| `assets/` | Images, which you add (see "Adding the images") |

The site makes no requests to other domains: no web fonts, CDNs, analytics, cookies, embedded videos or social widgets. The privacy policy promises this, so keep it that way. Every link and asset path is relative, so the site works at a project subpath like `https://<username>.github.io/<repo>/` or on a custom domain.

## Publishing on GitHub Pages

1. Push this repository to GitHub.
2. In the repository, go to **Settings › Pages**.
3. Under **Build and deployment**, set the source to **Deploy from a branch**. Choose the `main` branch and the `/ (root)` folder, then click **Save**.
4. Within a few minutes, the site appears at `https://<username>.github.io/<repo>/`.

A custom domain is optional. You can add one on the same Settings › Pages screen.

## Before publishing

Replace `[CONTACT EMAIL]` with the email address people should use to reach you. It appears in every HTML file, both as link text and inside `mailto:` links, so replace every occurrence:

- `index.html`: the Support section and the footer
- `privacy.html`: "Your privacy rights", "Contact us" and the footer
- `404.html`: the footer

To find them all, run `grep -rn "CONTACT EMAIL" .` from the repository folder.

## When the app is live

1. In `index.html`, find the commented-out "Download on the App Store" button in the hero section.
2. Replace `[APP STORE URL]` with the app's App Store link.
3. Delete the "Coming soon to the App Store" line, and remove the comment markers around the button so it shows.

The button is plain text on purpose. If you'd rather use Apple's official "Download on the App Store" badge, get the artwork from Apple's marketing resources and use it exactly as Apple's guidelines describe. Don't redraw or change the badge. Apple's guidelines are at https://developer.apple.com/app-store/marketing/guidelines/

## Adding the images

Add these files to the `assets/` folder. The pages already point to them. Until they're added, each image shows as a tinted placeholder of the right shape, so the layout still looks fine.

| File | What to add |
| --- | --- |
| `assets/app-icon.png` | The app icon, 1024 × 1024 PNG. It's in the Xcode project at `Fieldbook/Assets.xcassets/AppIcon.appiconset/AppIcon-iOS.png`. The site rounds its corners, and also uses it as the browser tab icon, the Apple touch icon and the link-preview image. |
| `assets/screenshot-1.png` | Landscape iPad screenshot of a work order with the job details filled in from a downloaded template. |
| `assets/screenshot-2.png` | Landscape iPad screenshot of the materials catalog, showing parts and the search field. |
| `assets/screenshot-3.png` | Landscape iPad screenshot of the Gallery, with search and the Draft and Submitted filters. |

Screenshots are shown in a 4:3 frame. Landscape iPad screenshots at 4:3 (such as 2732 × 2048 or 2752 × 2064 pixels) fill it exactly. Other sizes still fit, with a thin tinted border. The alt text and caption for each screenshot in `index.html` describe the screens above. If you use different screens, update them to match.

## App Store Connect settings

- **Privacy Policy URL:** `https://<username>.github.io/<repo>/privacy.html`
- **Support URL:** `https://<username>.github.io/<repo>/#support`
- **Marketing URL (optional):** the homepage, `https://<username>.github.io/<repo>/`
- **App Privacy:** "Data Not Collected" matches this policy, as long as the app keeps working as described.

If you use a custom domain, use it in these URLs instead.

## Keeping it current

The privacy policy and the App Store privacy answers both describe how the app works today. If the app changes, update both together, and change the "Last updated" date at the top of `privacy.html`. For example, adding analytics, crash reporting, a server, user accounts or a new permission would change both.

The "This website" section of the policy says the site uses no cookies, analytics or third-party scripts and loads nothing from other websites. Adding web fonts, analytics, embedded videos or social widgets would make that untrue.

## Legal review

`privacy.html` is a draft. Have a qualified lawyer review it before the app is published. There's a note saying the same at the top of the file.

Things worth raising with them:

- The policy doesn't mention support email. If people write to `[CONTACT EMAIL]`, you'll hold their email address and whatever they send. A lawyer can advise whether to add a short section about that.
- The effective date is November 10, 2026. If you publish later, update both dates at the top of the policy.

## Other notes

- **Link previews.** The Open Graph image uses a relative path, like everything else on the site. Some apps only show a preview image when it's a full URL. Once you know the site's address, you can change `og:image` on each page to the full address, such as `https://<username>.github.io/<repo>/assets/app-icon.png`.
- **The 404 page.** GitHub Pages shows `404.html` for any missing address. Because its paths are relative, it's fully styled for a missing page at the top level, like `https://<username>.github.io/<repo>/missing.html`. For a deeper missing address, like `.../<repo>/a/b/c`, it can show without its styles. If that matters, add `<base href="https://<username>.github.io/<repo>/">` inside the `<head>` of `404.html` once the address is final.
