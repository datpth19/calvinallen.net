---
layout: page
title: Contact Me
---
<form name="contact" action="thank-you" netlify-honeypot="bot-field" netlify>
    <p class="hidden">
        <label>Don't fill this out if you're human: <input name="bot-field"></label>
    </p>
    <p>
        <label>Your Name: <input type="text" name="name" required></label>   
    </p>
    <p>
        <label>Email: <input type="email" name="name" required></label>
    </p>
    <p>
        <label>Message: <textarea name="message" required></textarea></label>
    </p>
    <div netlify-recaptcha>
    </div>
    <p>
        <button type="submit">Submit</button>
    </p>
</form>