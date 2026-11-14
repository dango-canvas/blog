#Announcement #Migration

Since its inception, Dango Canvas has been served under the `dango.ink` domain. As this domain is reaching its expiration and maintenance window, Dango is transitioning to GitHub Pages for sustainable hosting under the unified `dango-canvas` organization.

Because Dango was architected from day one as a pure client-side, local-first, zero-backend application, the impact of this domain change is minimal. This document outlines the straightforward migration steps for different use cases.

---

## 1. Updated Site URLs

All project sites are now statically hosted on GitHub Pages:

*   **Web Application**: [https://dango-canvas.github.io/dango/](https://dango-canvas.github.io/dango/)
*   **Landing Page**: [https://dango-canvas.github.io/page/](https://dango-canvas.github.io/page/)
*   **Official Blog**: [https://dango-canvas.github.io/blog/](https://dango-canvas.github.io/blog/)
*   **GitHub Organization**: [https://github.com/dango-canvas](https://github.com/dango-canvas)

---

## 2. Standard Web Users: Migrating Your Local Canvas Data

### How It Works
Dango adheres strictly to a **Local-First** model. Your canvases and nodes are stored exclusively in your browser's `localStorage` and never transmitted to remote servers.

Due to the browser's **Same-Origin Policy (SOP)**, different domains cannot access each other's local storage. When you first visit the new GitHub Pages domain, your browser starts with an empty canvas. You simply need to transfer your canvas data once.

### Migration Steps (Takes ~10 seconds)
1. Open the existing `dango.ink` web app.
2. Press `Ctrl + S` (`Cmd + S` on macOS), or open the export menu at the bottom-right and select **Export as Dango File** to save your `.dango` backup file.
3. Open the new site: [https://dango-canvas.github.io/dango/](https://dango-canvas.github.io/dango/).
4. **Drag and drop** your downloaded `.dango` file onto the new canvas (or use the import button at the bottom-right).
5. Your canvas is instantly loaded and will automatically persist in the new domain's storage.

---

## 3. Share Links & Embedded Iframes: Updating URLs

If you have embedded Dango in Notion, Obsidian, or your personal website, or saved share links:

### How It Works
Dango's sharing and embedding mechanism is completely **stateless**. The entire canvas state (nodes, links, layouts) is compressed using `lz-string` and stored in the URL `#` (Hash) fragment. No central server is required to resolve or host the content.

### Solution: Pure String URL Replacement
Since all data is embedded in the hash, you only need to swap the origin domain in your link while keeping the parameters and hash intact.

#### ① Share Links
*   Old Link:
    ```text
    https://dango.ink/#NoJgNMwAxgRAVPQPBuEN9wR2q...
    ```
*   New Link:
    ```text
    https://dango-canvas.github.io/dango/#NoJgNMwAxgRAVPQPBuEN9wR2q...
    ```

#### ② Embedded Iframe Code (Notion / Obsidian / Blogs)
*   Old Embed Code:
    ```html
    <iframe src="https://dango.ink/?embed=true#NoJgNMwAxg..." style="width: 100%; height: 500px; border: none; border-radius: 12px;" allow="clipboard-write"></iframe>
    ```
*   Updated Embed Code:
    ```html
    <iframe src="https://dango-canvas.github.io/dango/?embed=true#NoJgNMwAxg..." style="width: 100%; height: 500px; border: none; border-radius: 12px;" allow="clipboard-write"></iframe>
    ```

---

## 4. Browser Extensions & Single-File Bundles

*   **Firefox Add-on**: A maintenance update will be submitted to redirect to the new Web endpoint. Existing installations will continue working normally offline.
*   **Single-file Distribution**: If you use the standalone `dango.html` downloaded from GitHub Releases, you are completely unaffected by this migration.

---

## 5. Security & Privacy Guarantees

Moving to GitHub Pages only changes the static delivery CDN:
1. **Zero Backend**: No servers or dynamic execution environments.
2. **Zero Tracking**: Computation, compression, and rendering remain 100% on your device.
3. **Open & Transparent**: Build steps are executed publicly via GitHub Actions.

Thank you for using Dango! If you encounter any issues, please feel free to open a ticket on [GitHub Issues](https://github.com/dango-canvas/dango/issues).
