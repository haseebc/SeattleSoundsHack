# Recon

## Getting started
Download the vulnerable VM from https://www.vulnhub.com/entry/seattle-v03,145/
Simply start up the virtual machine using Virtual Box! The root user account has a password of PASSWORD

## Check the network
Main points:
- looking mostly for common-ish vulns
- not competing with others
- racing vs. time

'netdiscover 192.168.0.0/24'

'nmap -p 80 192.168.0.24'

## Tips / Notes:

- 1st party bug bounties = Google Paypal, etc
- 2nd party bug bounties = Bugcrowd, H1, Synack, etc

Because competition is introduced; when working in a bug bounty it is essential to have templates set up for your "most found" classes of vulnerabilities. Obviously custom vulnerabilities will always be custom writeups, but having a template for ones that come up often is essential. **Protip:** always remember to change the URLS and domains in the templates. Nothing will get a bug invalidated faster than stating the wrong domain or URLs in a report.

When desigining these templates there are two really great resources to read:

- https://blog.bugcrowd.com/advice-for-writing-a-great-vulnerability-report/
- https://forum.bugcrowd.com/t/writing-a-bug-report-attack-scenario-and-impact-are-key/640
