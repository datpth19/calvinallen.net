---
layout: page
title: Contact Me
---
<form name="contact" netlify netlify-honeypot="bot-field">
    <p class="hidden">
        <label>Don’t fill this out if you're human: <input name="bot-field" /></label>
    </p>
    <p>
        <label>
            Your Name:<br/>
            <input type="text" name="name" required>
        </label>   
    </p>
    <p>
        <label>
            Email:<br/>
            <input type="email" name="name" required>
        </label>
    </p>
    <p>
        <label>
            Message:<br/>
            <textarea name="message" required></textarea>
        </label>
    </p>
    <p>
        <div netlify-recaptcha></div>
    </p>
    <p>
        <button type="submit">Submit</button>
    </p>
</form>