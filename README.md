# Vibe - frontend (React + Vite + Tailwind)

## Run it
1. Install Node.js from https://nodejs.org (the LTS version)
2. Open a terminal in this folder and run:

       npm install
       npm run dev

3. Open the address it prints (http://localhost:5173)

The backend is on Render's free plan: it "sleeps" when nobody uses it,
so the FIRST request can take up to a minute. Just wait.

## Where is everything?
- src/api.jsx           ALL backend calls (one small function per endpoint)
- src/helpers.js        tiny tools: toList(), cover pictures, genre colours
- src/PlayerContext.jsx the music player (play / pause / next / previous)
- src/pages/            one file per page (Home, Search, Explore, ...)
- src/components/       Sidebar, MusicPlayer panel, SongCard
- public/               your images

## How a page talks to the backend (the same pattern everywhere)
    useEffect(() => {
      getAllSongs().then((data) => setSongs(toList(data)));   // ask the backend
    }, []);                                                   // [] = only once
    ...
    {songs.map((song) => <p key={song.id}>{song.title}</p>)}  // show it

## Pictures
The backend's songs have an empty image_url right now, so cover pictures are
taken from /public by song title (see COVERS in src/helpers.js).
When a song gets a real image_url from the backend, that is used instead.

## Deploying (Vercel / Netlify)
The backend must allow your site's address (CORS) - ask the backend developer.
