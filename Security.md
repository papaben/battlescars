# Summary

The field of security is a full time job. 

The goal of this page is to give developers a basic exposure to concepts and a starting point to learn more. 

# 1. OWASP, Start Here
> The Open Web Application Security Project (OWASP) is a 501(c)(3) worldwide not-for-profit charitable organization focused on improving the security of software. Our mission is to make software security visible, so that individuals and organizations are able to make informed decisions. https://www.owasp.org/index.php/Main_Page

OWASP has provided a really great resource for educating first time web developers, which is available on their wiki at [OWASP Education](https://www.owasp.org/index.php/OWASP_Education_Presentation). I strongly suggest viewing the first presentation `Web Application Developer Security Training (2015)`.

# 2. Categories of Security

A list of some various ways in which security plays a part in our lives at work.

## 2.1. Category: In the code
 * AuthNZ:
    * Authentication: Is a user who they say they are? E.g. username/password or API token valid?
    * Authorization: Does a user have permission to perform a certain action? E.g. Roles Based Access Control, or AWS policy documents.
* In data layer code, replace `Model.objects.get(pk=...)` requests with `Model.objects.filter(pk=..., company_id=request.user.company_id)`
* Verbose errors: do not expose unnecessary internal state to users in error messages, either in JavaScript responses or raising exceptions in Python
* SQL Injection: a bad actor sends purposefully malformed data into a form on our web app that allows them to run custom SQL statements in our database.
* Cross Site Scripting (XSS): Similar to SQL Injection, but in this case a user is able to inject malicious JavaScript through a form element and have it actually run as JavaScript when we render a web page. E.g. a `Title` name contains valid JS and that JS runs when you view that `Title`.
  * Easy solution: never use the `| safe` function in Jinja.
* Remote File Inclusion (RFI): the backend code handling the request fetches an external resource (typically a file) that is provided by or generated from user input. This could enable an attacker to cause the backend to download their malicious file, possibly executing it or processing it in some other undesirable way.

## 2.2. Category: On your laptop
 * Try as hard as possible to never type plaintext passwords anywhere except a hidden text input. This includes not typing them on the command line or chat messages.
 * If you need to type a password on the command line, you can use the shell `read -s` command line tool to save it into a variable. See https://stackoverflow.com/questions/3980668/how-to-get-a-password-from-a-shell-script-without-echoing

## 2.3. Category: Compliance
Compliance is more concerned with ensuring protections and being able to report on violations/breaches. 

Some examples,

 1. Audit trail of actions taken with various resources. E.g. Who used a key from the Key Management Service when? Who downloaded what from an S3 bucket when?
 1. Logs of requests to a service or restricted resource. This is similar to audit trails.
 1. Proper access is in place to various sensitive resources or information

## 2.4. Category: Human

In practice, the easiest and most common vector for hacks has been through people on the inside. The best security practices and conventions within the code can be meaningless if an attacker can pivot through an employee's privilege. 

## 2.4.1. Keep viruses off your computer

For starters, always use HTTPS and be very suspicious of any website that is only HTTP.

### 2.4.2. Social Engineering

Social engineering is a very real threat to security. Despite all the things listed above, well executed social engineering attacks are the common cause for many, many breaches.

Learn more: https://en.wikipedia.org/wiki/Social_engineering_(security)

#### 2.4.2.1.What can you do?

1. Don't trust anyone electronically. Always follow up in person.
1. Don't click links in emails from anyone without verifying the safety
1. Don't download files from anyone without verifying safety
1. Never give up personal information in electronic chat's
1. If you buzz someone into the office, peek down the stairs to see who it is
1. If you use your laptop outside the office, be aware of what's on your screen
1. Use a separate Chrome profile for your work life
1. Keep tabs on your Facebook (or other social media) account being not-hacked.
    1. A malicious party could hack into your account and then pretend to be you and chat with your friends to find out information about you that could be used for harm


