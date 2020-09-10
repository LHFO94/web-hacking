# Webhacking 101 summary

In this doc I will briefly summarize some of the most common web hacks as listed in Web Hacking 101 by Peter Yaworski

## 2: Introduction

## 3: Background

## 4: Open redirect vulnerabilities

## 5: HTTP Parameter pollution

## 6: Cross-site Request Forgery

A cross-site request forgery, or CSRF, attack occurs when an attacker can use an HTTP request to access a user's information from another website (stored via Cookies), and use that information to act on the users behalf. Generally there are two types of CSRF attacks:

1) CSRF With GET requests
- User is on target site, distract user via social engineering away from the target to a malicious site, without logging out causing the cookies for that website (presumably with user verfication) to still be on the local user machine.
- Malicious site redirects user (with stored cookies on local machine) to target website from which it can make requests via the src attribute in an http <img> tag:
- example: <img src="https://www.bank.com/transfer?from=bob&to=joe&amount=500"> 

2) CSRF with POST requests
- Step 1 similar to GET requests 
- On the malicous website include a hidden from that makes a post request to target site to run some unwanted requests. 
- Example of such form: <iframe style="display:none" name="csrf-frame"></iframe>
<form method='POST' action='http://bank.com/transfer.php' target="csrf-frame" id\ ="csrf-form">
<input type='hidden' name='from' value='Bob'> <input type='hidden' name='to' value='Joe'> <input type='hidden' name='amount' value='500'> <input type='submit' value='submit'>
</form> <script>document.getElementById("csrf-form").submit()</script>
