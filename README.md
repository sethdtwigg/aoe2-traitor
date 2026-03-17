# AoE2 Secret Traitor Generator

> A zero-backend, single-file web app for Age of Empires II that randomly assigns teams and secret traitors using URL-hash state management. Designed for 4v4 Discord sessions.

---

## The Concept
In a standard **4v4**, the app randomly splits 8 players into two teams. It secretly assigns one player on each team to be a **Traitor** working for the opposition. To win, a Traitor must ensure their assigned team loses while completing a randomly generated sabotage mission.

## Technical Highlights
* **Zero-Backend:** No database or server-side logic. All state is generated on-the-fly.
* **URL-Hash State:** Uses Base64 encoded JSON payloads in the URL fragment (`#`) to distribute roles.
* **Zero-Knowledge Distribution:** The Dealer generates unique links for each player. Because roles are hidden in the hash, the Dealer can copy-paste links into Discord without spoiling the secrets.
* **Portable:** A single `index.html` file containing all CSS, JS, and Assets.

## How it Works
1.  **Input:** Paste 8 Discord usernames into the generator.
2.  **Shuffle:** The app uses a Fisher-Yates shuffle to determine teams and traitors.
3.  **Encapsulation:** Data is bundled into a JSON object containing name, team, role, and mission.
4.  **Encoding:** The object is stringified, converted to Base64, and appended as a URL hash.
5.  **The Reveal:** When a player opens their unique link, the app parses the hash and renders the parchment-themed view.

## Aesthetic
The UI is designed with an **Age of Empires II** theme, featuring:
* **MedievalSharp** typography.
* Parchment-texture reveal boxes.
* Blue and Red team color coding.
* Custom sabotage missions such as *The False Wall*, *The Lost Scout*, and *Market Sabotage*.

## Deployment
This project is a static site. It can be hosted on **Cloudflare Pages**, **GitHub Pages**, or **Vercel** by uploading the `index.html` file.

### Quick Deploy to Cloudflare
1.  Log in to **Cloudflare**.
2.  Navigate to **Workers and Pages**, select **Create application**, then **Upload assets**.
3.  Drag and drop the `index.html` file.
4.  Deploy the site.

## Rules of Engagement
* **Discord Etiquette:** Players join the Discord voice channel for the team assigned by the app. Traitors stay in their assigned team's channel to act as spies.
* **The Code of Sabotage:** No "instant suicide," such as deleting Town Centers in the Dark Age. Sabotage must be subtle and psychological.
* **The Reveal:** Once the game ends, Traitors must immediately switch to the other team's voice channel to reveal their true allegiance.
