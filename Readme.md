# Nepalese Student Association (NSA) Website @ MSU

Welcome to the official website source code for the **Nepalese Student Association at Mississippi State University**. This website serves as a portal for current students, alumni, and newcomers to stay informed, engaged, and connected with NSA activities and resources.

---

## 🌐 Website Features

| Section | Description |
|--------|-------------|
| `index.html` | **Homepage** featuring carousel of NSA images, animated welcome text, "About NSA" section, dynamic "Current Team" area loaded from a JSON file, and upcoming events with Google Calendar embed. Also includes a special popup alert system (NSA announcement alert). |
| `connect.html` | **Contact page** with animated carousel background, blurred overlay content, links to Cowbell Connect, social media, and a Google Form for user queries. |
| `alumni.html` | **Alumni page** showing a searchable and paginated table of past NSA members with department, batch, and contact info (loaded dynamically from `alumni_data.json`). |
| `more-info.html` | **Welcome guide** with animated sections offering info on airports, housing, events, and how to stay connected for new/incoming students. |
| `discussion.html` | (Planned or under construction) Placeholder for future community discussions or bulletin board. |
| `funding.html` | (Planned or under construction) Likely to include information on NSA event funding, budgeting, and sponsorships. |

---

## 📁 Folder Structure Overview

```bash
NSA_WEBSITE_MAIN/
│
├── data/
│   └── alumni_data.json            # JSON file storing alumni details for dynamic pagination
│
├── img/
│   ├── team-images/                # Profile images of team members
│   │   ├── adarsha-lamichanne.jpeg
│   │   ├── bikal-ghimire.jpg
│   │   ├── saphal-upreti.jpeg
│   │   ├── simran-pandey.jpeg
│   │   └── ...
│   ├── dashain-2023.jpg            # Images used in homepage and carousel
│   ├── dashain-2024.jpg
│   ├── Holi-2023.jpg
│   ├── good_nsa_bg.jpg
│   ├── msstate-image.jpg
│   ├── nsa_extra.jpg
│   └── nsa-logo.jpeg
│
├── index.html                     # Homepage (Main Landing Page)
├── connect.html                   # Contact and connect form
├── discussion.html                # (Optional future content)
├── funding.html                   # (Optional future content)
├── header.html                    # Navbar content (included via jQuery in every page)
├── footer.html                    # Footer content (included via jQuery in every page)
├── alumni.html                    # Alumni list page
├── more-info.html                 # Onboarding/Welcome guide
├── index copy.html                # Backup copy of index.html (optional)
└── Readme.md                      # This file
```

---

## 🔔 NSA Alert Popup Feature (Smart Announcements)

A dynamic popup shows special NSA alerts using Google Sheets + Apps Script backend.

### 🧹 How It Works
- A Google Sheet stores the current announcement, link, type (`info`, `warning`, `urgent`), and expiry date.
- A deployed Apps Script Web App reads this data and returns a JSON response.
- On `index.html`, a fetch request on page load pulls this data and displays a styled popup based on alert `type`.

### 🎨 Type-Based Styling
| Type | Visual | Style |
|------|--------|-------|
| `info` | ℹ️ | Teal border + light blue background |
| `warning` | ⚠️ | Yellow border + light yellow background |
| `urgent` | ❗ | Red border + light red background |

### 🛠️ To Edit or Add an Alert
1. Open the Google Sheet configured in the script
2. Update row 2 with:
   - `enabled = TRUE`
   - `valid_till = MM-DD-YYYY` (as string)
   - `message`, `type`, and optional `link`
3. Save — the change will automatically reflect on the website

### 🔐 Security Note
- The Google Sheet **does NOT need to be public**.
- The Apps Script runs as the owner's account and can access the sheet privately.
- Only the deployed script URL is public and returns read-only JSON.

---

## 🔧 What to Edit

### ✅ Navbar and Footer
- **header.html** and **footer.html** are loaded on all pages using jQuery:
  ```js
  $("#header-placeholder").load("header.html");
  $("#footer-placeholder").load("footer.html");
  ```
- ✏️ To update site-wide navigation or footer links, edit these two files.

### ✅ Homepage (`index.html`)
- ✨ Uses `Typed.js`, `AOS`, and CSS animations.
- Team members section is designed to be **dynamically generated** from a JSON file (planned enhancement).
- Carousel at the top rotates images from `/img/` folder.
- NSA announcement popup is loaded on page load.

#### Change Team Members:
1. Update JSON file: `data/team-members-details.json` (to be created).
2. Update team member images in `img/team-images/`.
3. JavaScript will read and inject new entries dynamically (make sure the script is present).

### ✅ Alumni Page (`alumni.html`)
- Loads data from: `data/alumni_data.json`
- Features:
  - Paginated results
  - Real-time search bar
  - Uses Bootstrap styling

#### Add or Edit Alumni:
- Update `alumni_data.json` with:
  ```json
  {
    "name": "Full Name",
    "department": "Dept. of X",
    "batch": "2021",
    "organization": "Current Workplace",
    "contact": "https://linkedin.com/in/example",
    "contactType": "LinkedIn"
  }
  ```

### ✅ More Info Page (`more-info.html`)
- Helpful for newly admitted students
- Includes:
  - Travel info with airport options
  - Popular apartments near MSU
  - Community group invitation

### ✅ Connect Page (`connect.html`)
- Background image carousel + blurred overlay
- Includes:
  - Cowbell Connect button
  - Social media icons
  - Embedded Google Form

---

## 📌 Libraries Used

- **Bootstrap 4.5**
- **jQuery**
- **AOS (Animate On Scroll)**
- **Animate.css**
- **Typed.js** (typewriter animation)
- **Bootstrap Icons**

---

## 🧐 Future Improvements
- Fully dynamic `team-members` section powered by JSON
- CMS-like admin panel for adding team, events, and alumni
- Login for members
- Event gallery with modal previews

---

## 👨‍💻 Developer Tips

- All dynamic content is added inside:
  ```html
  <div class="team-scroll" id="team-container"></div>
  ```
- Use `data-aos` and `animate__` classes to add entry animations.
- All carousel images are stored in `/img/` and updated via:
  ```html
  <div class="carousel-item"><img src="img/dashain-2023.jpg" ... /></div>
  ```

---


## 📄 License

This project is licensed under the **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License**.


🔗 Full License Text: [View Here](https://creativecommons.org/licenses/by-nc-nd/4.0/)  

---




## 🤝 Contributing

If you're contributing:
- Use proper naming convention for new images
- Keep HTML clean and formatted
- Make sure new pages load header/footer via jQuery

---

## 📩 Contact

Have questions or want to contribute?  
Visit the [Connect With Us](connect.html) page to reach out or submit updates.

---

🎓 **Built by [Sushant Gautam](https://github.com/sushant097)**. Contact for any assistance.

---

