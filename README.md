A Small Set of Customized Tools for Merry Making

Steps:

* Discovery / Mapping:
  * Linked Resources:
    * Find inscope domains with enum-domains
    * Port scan with nmap: `nmap -sS -A -PN -p- --script=http-title dontscanme.bro`
    * via: virustotal
    * via: similarweb
    * Scan subdomains for popular services / plugins
      * curl subdomain, then cat response & grep for service strings
        * eg: facebook, wordpress, surveygizmo, aws, shopify, unbounce, fastly, heroku, github, desk, tumblr
  * Unlinked Resources:
    * `dir-buster` to brute force
      * use seclists to augment:
        * RAFT lists
        * Git digger
        * svn digger
    * Try spidering deeper:
```
acme.com - 200
acme.com/backlog/ - 404
acme.com/controlpanel/ - 401 <-- dig deeper
acme.com/controlpanel/[bruteforce here now]
```
  * Tech stack -- check for CVEs against results here:
    * Wappalyzer (chrome)
    * Builtwith (chrome)
    * [retire.js](https://retirejs.github.io/retire.js/)
  * Custom engines
    * [WPScan](https://wpscan.org/)
      * plugins are more insecure than the platform!
    * [CMSmap](https://github.com/Dionach/CMSmap)
  * OSINT:
    * Use past flaws to pivot into new flaws
      * xssed.com
      * reddit xss
      * punkspider
      * xss.cx
      * xssposed.org
      * twitter search
  * SWFs search:
    * Google dorks: `site:url.com ext:swf`
  * Login w/ Facebook connect
    * look for `redirect_uri` & open redirects
      * Links to learn, I don't understand open redirect:
        * want to get tokens / access tokens
        * http://homakov.blogspot.se/2013/02/hacking-facebook-with-oauth2-and-chrome.html 
        * http://www.breaksec.com/?p=6039 Facebook Connect
  * 3rd Party Scripts
    * look for url downloads in scripts
      * are there url query parameters used in scripts?
    * `(get)?(query|url|qs|hash)param`
    * `location\.(hash|href|search)\.match`
    * bypass Content Security Policy
      * Look at CSP domains, use those as attack vector
      * eg: `<script src="mixpanel.com?callback=alert(1)">`
