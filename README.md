# 📬 Be Forward Aruba - Client Submission Form

This web form is designed for **Be Forward Aruba** to collect client information for vehicle import processing, including their personal details and an image of their identification document.

Built with modern, privacy-focused client-side tools, this form requires **no backend**, offers real-time **email delivery**, and securely uploads ID images to **ImgBB**.

---

## ✅ Features

### 📄 Client Information Collection
The form gathers:
- First Name & Last Name
- Email Address
- Phone Number
- Physical Address (City + Aruba pre-filled)
- Persoonsnummer (8-digit validated)
- ID image upload (JPG, PNG, GIF)

### 🛡️ Spam Protection
- **Honeypot Field**: A hidden field traps bots that attempt to fill it
- **Pattern Validation**: Persoonsnummer must be exactly 8 digits
- **Client-side Input Validation**: All required fields are checked in-browser

### 📷 Image Upload via ImgBB
- Files are base64-encoded and uploaded using your private ImgBB API key
- Returns a public link which is included in the email
- No server required, secure and lightweight

### ✉️ Email Notification with EmailJS
- Sends all submitted data (including ID image URL) to your email
- Powered by EmailJS v3 SDK
- Fully client-side, with no need to expose any server credentials

---

## 🧰 Technologies Used

| Feature               | Technology           |
|------------------------|----------------------|
| Form Handling         | HTML, JavaScript     |
| Spam Protection       | Honeypot Anti-Bot    |
| File Upload           | [ImgBB API](https://api.imgbb.com/) |
| Email Delivery        | [EmailJS](https://www.emailjs.com) |
| Validation            | HTML5, Regex         |
| Hosting Logo          | GitHub Pages         |

---

## 📁 Project Structure

```
be-forward-client-form/
├── client-form.html         # Main public form
├── style.css                # Optional custom styling
├── README.md                # This documentation
```

---

## 🔧 Setup Instructions

### 1. Update Your EmailJS Template
In your `template_lc1qs7d`, include the following template variables:

```html
<p><strong>Name:</strong> {{firstName}} {{lastName}}</p>
<p><strong>Email:</strong> {{email}}</p>
<p><strong>Phone Number:</strong> {{phoneNumber}}</p>
<p><strong>Address:</strong> {{address}}, {{city}}, Aruba</p>
<p><strong>Persoonsnummer:</strong> {{persoonsnummer}}</p>
<p><strong>ID Image:</strong> <a href="{{id_url}}" target="_blank">View ID</a></p>
```

---

### 2. Host the Form

You can upload this form to:
- Vercel
- Netlify
- GitHub Pages
- Any web hosting provider that serves static files

---

## 💡 Tips

- The logo is loaded from:  
  `https://beforwardaruba.github.io/webapp/logo.png`

- Ensure the browser has internet access so:
  - Imgbb uploads succeed
  - EmailJS can send emails
  - Logo loads from GitHub

---

## 🆘 Support

Need enhancements like:
- Google reCAPTCHA
- Supabase or Firebase backend
- WhatsApp or auto-confirmation emails to clients?

Let us know and we’ll help you build it.

Built with care for **Be Forward Aruba** 🇦🇼
