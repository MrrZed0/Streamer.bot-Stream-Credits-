# 🎬 Streamer.bot Twitch End Credits Overlay

A **cinematic movie-style end credits overlay** for **OBS Studio**, powered by **Streamer.bot**.

Display your community activity as **rolling Hollywood-style credits** at the end of your stream.

---

![Image](https://github.com/MrrZed0/Streamer.bot-Stream-Credits-/blob/main/1.png?raw=true)
![Image](https://github.com/MrrZed0/Streamer.bot-Stream-Credits-/blob/main/2.png?raw=true)

# ✨ Features

* 🎬 Cinematic rolling credits (movie style)
* 👤 Profile picture + username layout
* 💬 First chatters tracking
* 💎 Bits with exact amount shown
* 🎁 Gifted subs grouped by gifter
* 👥 Recipient names displayed under gifted subs
* ❤️ Followers, subs, raids, guest stars, shared chat
* 🌈 Per-category glow colors
* 🎯 Category icons
* ⚡ Works locally in OBS (no web server required)
* 🔁 Auto-updating via `credits_data.js`

---

# 📦 Categories Supported

* First Chatters
* Cheers / Bits
* New Followers
* Gifted Subs
* Subscribers
* Raids
* Guest Stars
* Shared Chat

---

# 🧠 How It Works

Streamer.bot writes data into:

```
credits_data.js
```

Example:

```js
window.CREDITS_DATA = [
  {
    "type":"bits",
    "userName":"ViewerOne",
    "profileImage":"https://...",
    "detail":"500 Bits",
    "recipients":[]
  }
];
```

The HTML overlay loads that file and renders **scrolling credits**.

---

# 🎁 Gifted Subs (Smart Grouping)

Gifted subs are automatically grouped by the same gifter.

### Example

If:

* BigSupporter gifts UserA
* BigSupporter gifts UserB
* BigSupporter gifts UserC

It becomes:

**BigSupporter**
Gifted 3 Subs
Recipients: UserA, UserB, UserC

✔ No duplicates
✔ Automatically merged
✔ Count auto-updated

---

# 📁 Folder Setup

Recommended path:

```
C:\Program Files\OBS-Studio\Files\Sources\Ending_Stream\End_Credits_Overlay\
```

Files:

```
credits_overlay.html
credits_data.js
credits_db.txt
```

---

# 🎥 OBS Setup

Add a **Browser Source**:

```
file:///C:/Program%20Files/OBS-Studio/Files/Sources/Ending_Stream/End_Credits_Overlay/credits_overlay.html
```

### Recommended Settings

* Width: 1920
* Height: 1080
* FPS: 30
* ✔ Refresh browser when scene becomes active
* ❌ Shutdown source when not visible

---

# 🤖 Streamer.bot Setup

Use the **Add Credits C# script** for all triggers.

### Set `eventType` before running:

```
chatFirst
bits
follow
gifted
sub
raid
guestStar
sharedChat
```

---

# 💎 Bits Setup

Pass:

```
eventType = bits
targetUser
targetUserProfileImageUrl
bits OR cheerAmount
```

### Output

```
ViewerName
500 Bits
```

---

# 🎁 Gifted Subs Setup

Pass:

```
eventType = gifted
gifterUser
gifterProfileImageUrl
giftCount
recipientUsers = user1,user2,user3
```

### Output

```
BigSupporter
Gifted 3 Subs
Recipients: user1 user2 user3
```

---

# 🔄 Reset Before Each Stream

Run the reset script to clear credits:

* `credits_db.txt`
* `credits_data.js`

---

# 🧪 Example Data

```js
window.CREDITS_DATA = [
  {
    "type":"bits",
    "userName":"ViewerOne",
    "profileImage":"https://static-cdn.jtvnw.net/example1.png",
    "detail":"500 Bits",
    "recipients":[]
  },
  {
    "type":"gifted",
    "userName":"BigSupporter",
    "profileImage":"https://static-cdn.jtvnw.net/example2.png",
    "detail":"Gifted 3 Subs",
    "recipients":["UserA","UserB","UserC"]
  }
];
```

---

# 🎮 Typical Workflow

### Start of Stream

➡ Run **Reset Credits**

### During Stream

➡ Each event adds to credits

### End of Stream

➡ Show credits overlay scene

---

# ⚠️ Notes

* Works best as **local OBS browser source**
* Uses `.js` instead of `.txt` (fixes OBS fetch issues)
* Recipient names depend on Streamer.bot trigger data
* Some triggers may require custom arg mapping

---

# 🎨 Customization Ideas

* Add your logo at the top
* Change fonts (cinematic / sci-fi / neon)
* Add background video
* Adjust scroll speed
* Add music sync
* Add subscriber tiers
* Add Twitch badges

---

# 🛠 Requirements

* OBS Studio
* Streamer.bot
* Twitch triggers configured
* Local file access enabled

---

# ❤️ Credits

Built for streamers who want a **clean cinematic outro** that highlights their community.

---

# 📄 License

Free to use, modify, and customize for your stream.
