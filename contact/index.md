---
layout: page
title: Contact Me
---
<form name="contact" netlify>
    <p>
        <label>Your Name: <input type="text" name="name" required></label>   
    </p>
    <p>
        <label>Email: <input type="email" name="name" required></label>
    </p>
    <p>
        <label>Message: <textarea name="message" required></textarea></label>
    </p>
    <p>
        <div netlify-recaptcha></div>
    </p>
    <p>
        <button type="submit">Submit</button>
    </p>
</form>