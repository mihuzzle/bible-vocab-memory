# FI ↔ EN Bible Vocab Match (GitHub Pages)

A single-file, mobile-friendly matching game for practicing Biblical vocabulary translations from Finnish to English.

Live site: https://mihuzzle.github.io/bible-vocab-memory/

## What changed in this build

- Replaced the public GitHub Issues feedback flow with support for an embedded Google Form.
- The **Give feedback** button opens a full-screen overlay over the game.
- The overlay includes a **Close** button and an **Open in new tab** fallback.
- The Google Form loads only when the user opens the feedback view.
- Kept the optional Umami Cloud integration hook for anonymous daily and monthly visitor counts.
- Embedded vocabulary:
  - 1,661 Finnish-English pairs
  - 45 Finnish category labels

## Deploy

1. Rename `index_performance_feedback.html` to `index.html`.
2. Replace the repository-root `index.html`.
3. Commit and push.
4. GitHub Pages will publish the update.

## Create the Google Form

Create a short form with these questions:

1. **Feedback theme** — Multiple choice, required
   - Modify/add words
   - Modify/add phrases
   - Open feedback
2. **Your feedback** — Paragraph, required
3. **Email address (optional)** — Short answer, optional

Recommended confirmation message:

> Thank you! Your feedback has been sent. You can now close this form and return to the game.

For anonymous use:

- Publish the form so anyone with the link can respond.
- Do not enable **Limit to 1 response**.
- Do not collect verified email addresses.
- Do not use a file-upload question.
- Keep **View results summary** disabled.
- Keep the linked response spreadsheet private.

## Connect the form to the game

1. Open the Google Form.
2. Choose **Send** or the sharing/publishing controls.
3. Choose the embed option (`<>`).
4. Copy the URL inside the generated iframe's `src="..."` value. It normally looks like:

```text
https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true
```

5. Open `index.html` and find:

```js
googleFormEmbedUrl:''
```

6. Paste the URL between the quotation marks:

```js
googleFormEmbedUrl:'https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true'
```

7. Save, commit, and push the file.

Until a valid Google Forms URL is added, the feedback overlay displays a setup notice instead of an empty frame.

## Where responses appear

Responses are visible in the private **Responses** section of your Google Form. You can optionally link the form to a private Google Sheet and enable email notifications for new responses.

## Visitor counts

The file contains an optional Umami Cloud hook. It is disabled until you add your own Umami Website ID.

1. Create an Umami Cloud account.
2. Add the website `mihuzzle.github.io`.
3. Copy the site's Website ID.
4. In `index.html`, find:

```js
umamiWebsiteId:''
```

5. Paste the Website ID and deploy the updated file.

The integration records one page visit for the game. It does not track game actions, categories, answers, scores, or feedback.

## Existing gameplay rules

- Scrolling is allowed in the matching view.
- Each round uses five pairs.
- Finnish is always on the left and English on the right.
- Card text wraps and remains fully visible.
- Sessions use a shuffled deck with no repeats until eligible pairs are consumed.

## Intermittent performance feedback

The results screen now sometimes shows a lighthearted performance note based on:

- Current-round accuracy and mistakes
- Completion time compared with the selected difficulty target
- The previous three rounds
- Overall session performance

Feedback is intentionally intermittent:

- It is not shown after the first round unless that round also ends the session.
- Beginning with round 2, even-numbered rounds have a 50% chance of showing a note.
- A note is always shown after the final round of a session.
- The same message is not repeated within a session.
- The strongest translator-themed messages require consistently excellent recent performance, rather than one unusually fast round.

The message pools and thresholds are embedded in `index_performance_feedback.html` and can be edited in the `PERFORMANCE_MESSAGES`, `classifyPerformance`, and `shouldShowPerformanceFeedback` sections.

## Finnish pronunciation

The matching view now includes a small **🔊** button on each Finnish card. Tapping it reads the Finnish word or phrase aloud without selecting the card or attempting a match.

A **Finnish pronunciation** On/Off control is available in Settings and defaults to On. Pronunciation is independent of the correct-match ding.

The feature uses the browser's built-in Web Speech API and requests a `fi-FI` voice at a slightly reduced rate. No audio files, paid speech service, API key, or additional hosting are required. The exact voice quality depends on the Finnish voices installed or provided by the user's device and browser.

If the device exposes voices but has no Finnish voice, the game does not substitute an English voice; it displays a short availability message instead. Browsers without speech-synthesis support automatically disable the pronunciation setting.

### Interaction

- Tap a Finnish card: select it for matching.
- Tap **🔊**: hear the Finnish pronunciation without selecting the card.
- Starting another pronunciation stops the previous one.
- Leaving the game view or completing the round stops any active speech.

