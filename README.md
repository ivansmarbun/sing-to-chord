# Sing to Chord

A small web app for guitarists who sing. Sing a song into your microphone and the app detects the key you're singing in, then tells you which chords to play and where to put a capo, so the chord sheet from the internet fits your voice.

Everything runs in the browser. Audio is analysed locally and never uploaded.

## How it works

1. **Sing the song.** Press the button, which turns on the microphone, and sing a verse or chorus for 20–30 seconds. While you sing, the app shows the note, how sharp or flat it is, and a pitch trace. Press again to stop and turn the microphone off. Pitch is detected with the YIN algorithm, and the notes you held are matched against the Krumhansl-Schmuckler major and minor key profiles to find your key. A match level (strong, good or weak) tells you how far to trust it.
2. **Your song.** Paste the chords from the website. The app works out their original key, or you can pick it yourself.
3. **What to play.** You get the chords moved into your key, plus the 3 easiest open-shape and capo options (for example "capo 3, play G shapes") with your chord sheet rewritten for each.

Optionally, you can also record your lowest and highest notes. If you haven't sung a song, the app uses that range to suggest a key.

## Run it

The microphone only works on `localhost` or HTTPS, so opening the file directly won't work.

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000> and allow microphone access.

## Hosting

It's a single static file (`index.html`), so any free static host works, such as GitHub Pages, Cloudflare Pages, Netlify or Vercel. They all provide HTTPS, which the microphone needs.

## Tips

- Use headphones if music is playing, and sing in a quiet room.
- If the key match is weak, sing longer or more steadily, or choose the key yourself.
- C major and A minor share the same chords, so the app can mix them up. The chords it suggests still work either way.

## Limits

- It can't know the real chords of a song from your voice alone. It finds the key you sing in and the chords that fit it, so paste the chords from the website to get the exact ones.
- There is no AI or song lookup. A song-title lookup could be added later to fill in the original key and chords.

## Files

- `index.html`: the whole app (HTML, CSS and JavaScript).
