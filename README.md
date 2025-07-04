# 📬 Be Forward Aruba - Client Submission Form

This is a lightweight client intake web app built for **Be Forward Aruba**. It allows customers to securely submit their personal information for vehicle import processing.

---

## ✅ Features

### 🎯 Simple, User-Friendly Form
- Collects:
  - First name
  - Last name
  - Email
  - Address
  - City (Aruba is locked in)
  - Persoonsnummer (8-digit validation)

### ✉️ Instant Email Notifications
- Sends all submission details to your inbox using **Resend**
- No sensitive API keys are exposed in the frontend

### 🛡️ Spam Protection
- Honeypot field included (invisible to users, catches bots)
- Input validation on the `persoonsnummer` field (must be exactly 8 digits)

### 🔒 No Public API Keys
- The form talks only to a secured Supabase Edge Function
- No `SUPABASE_URL` or `anon key` exposed in `client-form.html`

---

## 🧰 Technologies Used

| Feature                | Technology            |
|------------------------|------------------------|
| **Frontend UI**        | HTML, CSS (custom)     |
| **Form Validation**    | Native HTML5 + JS      |
| **Spam Protection**    | Honeypot field         |
| **Email Delivery**     | [Resend](https://resend.com) (via Edge Function) |
| **Secure Backend**     | [Supabase Edge Functions](https://supabase.com/docs/guides/functions) |
| **Deployment Ready**   | Static hosting (Vercel, Netlify, etc.) |

---

## 📁 Folder Structure

```
be-forward-client-form/
├── client-form.html         # Main public-facing form (no secrets inside)
├── style.css                # Clean styling, consistent with your quote app
├── README.md                # You're reading this!
└── src/
    └── submit-client-form/
        └── index.ts         # Supabase Edge Function: handles and emails the form submission
```

---

## 🚀 How It Works

1. User fills out and submits the form
2. Form sends a `POST` request to your **Supabase Edge Function** at:

```
https://your-project.supabase.co/functions/v1/submit-client-form
```

3. The function:
   - Reads form data from the request body
   - Sends an email via Resend to notify you

---

## 🛠️ Setup Guide

### 1. Configure Supabase Edge Function

In the Supabase CLI or Dashboard, deploy the function located at:

```
src/submit-client-form/index.ts
```

Make sure to add the following secret in your **function environment variables**:

```env
RESEND_API_KEY=your_resend_api_key
```

Then deploy the function:

```bash
supabase functions deploy submit-client-form
```

---

### 2. Configure the Frontend

In `client-form.html`, ensure this fetch call matches your Supabase deployment:

```js
fetch("https://your-project.supabase.co/functions/v1/submit-client-form", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    firstName,
    lastName,
    email,
    address,
    city,
    persoonsnummer
  })
});
```

> 🔐 There is **no need** to include any public Supabase keys in this version.

---

### 3. Optional: Deploy Frontend

You can host `client-form.html` on:

- [Vercel](https://vercel.com)
- [Netlify](https://netlify.com)
- [GitHub Pages](https://pages.github.com)
- Your own web server

---

## 🧪 Sample Email Output

You’ll receive an email like:

```
📬 New Client Submission

Name: John Doe
Email: john@example.com
Address: Tanki Flip 14B, Oranjestad, Aruba
Persoonsnummer: 12345678
```

---

## 🆘 Support

Need help or want to expand this further?
- Add file attachments?
- Store submissions in Supabase?
- Add confirmation emails to clients?

Just ask. 😊
