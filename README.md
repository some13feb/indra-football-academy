# 🏆 Indra Football Academy (IFA) — Website

**Live:** [https://indrafootballacademy.github.io](https://indrafootballacademy.github.io)

A modern, responsive football coaching website for Indra Football Academy, Lucknow, India.

---

## 🏗️ Architecture

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3, Bootstrap 5, JavaScript |
| Auth | Firebase Authentication (Google + Email/Password) |
| Database | Cloud Firestore |
| Storage | Firebase Storage |
| Hosting | GitHub Pages (free, unlimited) |
| Security | CSP headers, Firebase Security Rules |

---

## 📁 File Structure

```
├── index.html                 Homepage (carousel hero, programs preview)
├── 404.html                   Custom 404 page
├── pages/
│   ├── about.html             Coach profile, team, values
│   ├── admin.html             Admin panel (super/sub-admin system)
│   ├── contact.html           Contact form + 2 Google Maps
│   ├── gallery.html           Masonry grid with category filters
│   ├── profile.html           User profile (view/edit, sign out)
│   ├── programs.html          4 programs + comparison table
│   ├── register.html          3-step: Auth → Details → Program
│   ├── reset-password.html    Dedicated password reset page
│   ├── schedule.html          Weekly timetable
│   └── signin.html            Google + Email sign-in
├── css/
│   ├── style.css              Custom theme + responsive
│   └── animations.css         Effects, floating dots, gradients
├── js/
│   ├── app.js                 Navbar, counters, dark mode, validation
│   ├── hero-doodle.js         Canvas animated football doodle
│   └── firebase-config.js     [DEPRECATED — not used, kept for reference]
├── assets/images/             Hero carousel backgrounds
├── firestore.rules            Firestore security rules
├── storage.rules              Storage security rules
└── .gitignore
```

---

## 🔐 Authentication System

### Sign-In Methods
- **Google Sign-In** (popup method — instant feedback)
- **Email/Password** (with email verification)

### User Roles
| Role | Access |
|------|--------|
| Super Admin (`some13feb@gmail.com`) | Full access + User Management |
| Sub-Admin (added by Super Admin) | Content management only |
| Student (registered users) | Profile + registration |

### Admin Access Flow
1. Admin signs in with Google
2. Navbar shows "🛡️ Super Admin" dropdown
3. Dropdown includes "Modify Content" → opens admin panel
4. Admin panel has auth guard (requires Google sign-in)

---

## 🛡️ Security

### Applied Security Measures
- ✅ **Content Security Policy (CSP)** — meta tags on all pages
- ✅ **X-Frame-Options: DENY** — prevents clickjacking
- ✅ **X-Content-Type-Options: nosniff** — prevents MIME sniffing
- ✅ **Referrer-Policy: strict-origin-when-cross-origin**
- ✅ **Firebase Security Rules** — server-side data protection
- ✅ **No demo/bypass mode** — admin auth is real Firebase auth
- ✅ **HTTPS enforced** — GitHub Pages forces HTTPS
- ✅ **Popup auth** — no redirect vulnerabilities
- ✅ **Sub-admin privileges limited** — can't access User Management

### Firebase Security Rules Summary
- Users can only read/write their OWN data
- Registrations require authentication
- Only super admin can write to `settings` collection
- Contact form validates field lengths (anti-spam)
- Default deny-all on undefined paths

### Recommended Additional Steps
1. **Enable 2FA** on `some13feb@gmail.com`
2. **Restrict API key** in Google Cloud Console (HTTP referrer whitelist)
3. **Add reCAPTCHA** to contact/registration forms
4. **Add Cloudflare** for DDoS protection (see below)

---

## ☁️ Cloudflare Setup (Recommended)

### Why Cloudflare?
- Free DDoS protection
- Free SSL/CDN
- Bot protection
- Analytics
- Page Rules for URL rewrites

### Steps to Add Cloudflare:

**Step 1: Buy a domain (optional but recommended)**
- Buy `indrafa.in` from Namecheap/GoDaddy (~₹500/year)

**Step 2: Sign up for Cloudflare**
- Go to [cloudflare.com](https://www.cloudflare.com) → Sign up (Free plan)
- Add your domain → Cloudflare scans DNS

**Step 3: Update nameservers**
- At your domain registrar, change nameservers to Cloudflare's
- Cloudflare will give you 2 nameservers (e.g. `ada.ns.cloudflare.com`)

**Step 4: Configure DNS**
- Add a CNAME record: `@` → `indrafootballacademy.github.io`
- Add a CNAME record: `www` → `indrafootballacademy.github.io`

**Step 5: Enable in GitHub Pages**
- Go to repo Settings → Pages → Custom domain → enter `indrafa.in`
- Check "Enforce HTTPS"

**Step 6: Cloudflare Settings (Free tier)**
- SSL/TLS → Full (strict)
- Speed → Auto Minify (HTML, CSS, JS)
- Security → Bot Fight Mode: ON
- Security → Challenge Passage: 30 minutes
- Caching → Browser Cache TTL: 4 hours

**Step 7: Update Firebase**
- Add `indrafa.in` to Firebase Auth → Authorized domains
- Remove old domains if not needed

---

## 📱 Responsive Design

- Bootstrap 5 grid handles breakpoints
- Hero carousel: 100vh desktop, 70vh mobile
- `clamp()` for fluid typography
- Touch-friendly on iOS/Android
- Navbar collapses to hamburger below 992px

---

## 🔥 Firebase Configuration

```
Project ID: indra-football-academy
Region: asia-south1 (Mumbai)
Auth: Google + Email/Password
Firestore: Standard edition
```

### Firestore Collections
| Collection | Purpose |
|-----------|---------|
| `users` | User profiles |
| `registrations` | Student registrations |
| `contacts` | Contact form messages |
| `settings` | Admin settings (sub-admins, team) |
| `programs` | Coaching programs |
| `gallery` | Gallery images |
| `schedule` | Weekly schedule |

---

## 🏟️ Academy Details

| | |
|--|--|
| **Name** | Indra Football Academy |
| **Instagram** | @indra_football_academy |
| **Location 1** | Greenfields Sports Hub, Rajajipuram, Lucknow |
| **Location 2** | Red Hill School, Butler Colony, Lucknow |
| **Phone** | +91-8957039841 |
| **Email** | info.indrafa@gmail.com |
| **Training** | Mon–Fri, 5:00–7:00 PM |
| **Admin Email** | some13feb@gmail.com |

---

## 🚀 Deployment

```bash
# Push to deploy (auto-deploys via GitHub Pages)
git add -A
git commit -m "your message"
git push origin main
```

Site deploys automatically in ~60 seconds after push.

---

## 📋 Programs

| Program | Ages | Price | Sessions |
|---------|------|-------|----------|
| Little Strikers | 6–10 | ₹3,300/mo | 2x/week |
| Elite Development | 11–16 | ₹5,400/mo | 3x/week |
| Pro Pathway | 16+ | ₹7,500/mo | 5x/week |
| Summer Camp | All | ₹12,500/week | 1 week intensive |

---

## 👥 Social Links

- Facebook: [facebook.com/share/1H2BBqbfJo](https://www.facebook.com/share/1H2BBqbfJo/?mibextid=wwXIfr)
- Instagram: [@indra_football_academy](https://www.instagram.com/indra_football_academy/)
- YouTube: [@ifa.indrafootballacademy](https://www.youtube.com/@ifa.indrafootballacademy)
- WhatsApp: +91-8957039841
